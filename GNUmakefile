
FIND= find
PNAME=writeat

all: ${PNAME}.tex ${PNAME}.pdf

EPS_FILES = $(shell ${FIND} img -name *.eps 2>/dev/null)
PDF_TARGETS = $(addsuffix .pdf, $(basename $(notdir $(EPS_FILES))))

${PNAME}.tex:
	pod6slide  ${PNAME}.pod6 >$@
${PNAME}.pdf: ${PNAME}.tex $(PDF_TARGETS)
	pdflatex -halt-on-error ${PNAME}.tex; touch $@

#${PNAME}.pdfx: ${PNAME}.tex $(PDF_TARGETS)
#	latex ${PNAME}.tex && dvipdf ${PNAME}.dvi


$(PDF_TARGETS): BASE = $(basename $(notdir $@))
$(PDF_TARGETS): ORIG = $(filter %/${BASE}.eps,${EPS_FILES})
$(PDF_TARGETS):
	@echo CONVERT ${ORIG} to $@;\
	epstopdf ${ORIG}  -o=$@
	
clean:
	-rm -f *.tex *.pdf *.log *.snm *.aux *.nav *.out *.toc *.dvi *.vrb


