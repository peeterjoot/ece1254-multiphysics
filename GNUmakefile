THISDIR := ece1254-multiphysics
THISBOOK := ece1254

include ../latex/make.bookvars

INCOMPLETE += multiphysicsProblemSet1Problem1.tex
INCOMPLETE += multiphysicsProblemSet1Problem2.tex
INCOMPLETE += multiphysicsProblemSet1Problem3.tex
INCOMPLETE += multiphysicsProblemSet2aProblem1.tex
INCOMPLETE += multiphysicsProblemSet2bProblem1.tex
INCOMPLETE += multiphysicsProblemSet2bProblem2.tex

#ONCEFLAGS := -justonce

SOURCE_DIRS += appendix
# FIXME:
# 1) including this incorrectly adds figures/*pdf to the ./.gitignore file
# 2) also not seeing this result in figure dependencies. touch figures/etalonFig1.pdf
FIGURES := ../../figures/$(THISBOOK)
SOURCE_DIRS += $(FIGURES)

# also toggle redacted classicthesis-config.tex
# FIXME: changing this flag should be a dependency of matlab.tex 
#REDACTED := -redacted

GENERATED_SOURCES += matlab.tex 
GENERATED_SOURCES += mathematica.tex 
GENERATED_SOURCES += ps3amatlab.tex
GENERATED_SOURCES += ps3bmatlab.tex
GENERATED_SOURCES += projmatlab.tex

#EPS_FILES := $(wildcard $(FIGURES)/report/*.eps)
#PDFS_FROM_EPS := $(subst eps,pdf,$(EPS_FILES))

THISBOOK_DEPS += $(PDFS_FROM_EPS)
THISBOOK_DEPS += kbordermatrix.sty

include ../latex/make.rules

#all :: proj
proj :: ece1254projectReport.pdf
#HarmonicBalance.pdf : hbFigure.sty ../ece1254/HarmonicBalanceAbstract.tex ../ece1254/HarmonicBalanceText.tex

#ece1254projectReport.pdf :: $(PDFS_FROM_EPS)

#epsconv : $(PDFS_FROM_EPS)

projmatlab.tex : ../METADATA ../../matlab/METADATA
	(cd .. ; ./METADATA -matlab -latex -ece1254 -filter ece1254/proj ) > $@

ps3bmatlab.tex : ../METADATA ../../matlab/METADATA
	(cd .. ; ./METADATA -matlab -latex -ece1254 -filter ece1254/ps3b/ ) > $@

ps3amatlab.tex : ../METADATA ../../matlab/METADATA
	(cd .. ; ./METADATA -matlab -latex -ece1254 -filter ece1254/ps3a/ ) > $@

multiphysicsProblemSet3a.pdf : multiphysicsProblemSet3aProblem1.tex
multiphysicsProblemSet3a.pdf : ps3amatlab.tex

multiphysicsProblemSet3b.pdf : multiphysicsProblemSet3bProblem1.tex
multiphysicsProblemSet3b.pdf : ps3bmatlab.tex

ece1254projectReport.pdf :: projmatlab.tex
ece1254projectReport.pdf :: ece1254projectReport.tex ../ece1254/HarmonicBalanceAbstract.tex ../ece1254/HarmonicBalanceText.tex
ece1254projectReport.pdf :: ./peeters_macros.sty ./peeters_layout.sty ./peeters_layout_exercise.sty ./macros_bm.sty 

copy: 
	cp ece1254.pdf ece1254projectReport.pdf ../blogit/HarmonicBalance.pdf proj/

multiphysicsProblemSet1.pdf :: $(PDF_DEPS)
multiphysicsProblemSet1.pdf :: multiphysicsProblemSet1Problem1.tex
multiphysicsProblemSet1.pdf :: multiphysicsProblemSet1Problem2.tex
multiphysicsProblemSet1.pdf :: multiphysicsProblemSet1Problem3.tex

multiphysicsProblemSet2a.pdf :: $(PDF_DEPS)
multiphysicsProblemSet2a.pdf :: multiphysicsProblemSet2aProblem1.tex
multiphysicsProblemSet2a.pdf :: ../ece1254/conjugateGradientAlgorithm.tex
multiphysicsProblemSet2a.pdf :: ../ece1254/simpleNortonEquivalents.tex

multiphysicsProblemSet2b.pdf :: $(PDF_DEPS)
multiphysicsProblemSet2b.pdf :: multiphysicsProblemSet2bProblem1.tex
multiphysicsProblemSet2b.pdf :: multiphysicsProblemSet2bProblem2.tex

clean ::
	rm -f ece1254projectReport.pdf
