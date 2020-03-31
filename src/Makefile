force:
	yes R |make all

all: rasm_fr.pdf rasm_en.pdf rasm_fr.html rasm_en.html cp

cp:
	mv -f *.png *.html *.css ../html/
	mv -f *.pdf ../pdf/



rasm_fr.pdf: clean
	latex -file-line-error -halt-on-error rasm_fr.tex
	makeindex rasm_fr.idx
	latex rasm_fr.tex >/dev/null
	makeindex rasm_fr.idx
	pdflatex rasm_fr.tex >/dev/null
	make clean

rasm_en.pdf: clean
	latex -file-line-error -halt-on-error rasm_en.tex
	makeindex rasm_en.idx
	latex rasm_en.tex >/dev/null
	makeindex rasm_en.idx
	pdflatex rasm_en.tex
	make clean

rasm_en.html: clean
	htlatex rasm_en.tex
	htlatex rasm_en.tex
	cat rasm_css.txt >> rasm_en.css
	make clean
	cat rasm_en.html |sed s/'auto<\/span'/'<\/span'/g >Rasm_en.html
	rm rasm_en.html
	mv Rasm_en.html rasm_en.html



rasm_fr.html: clean
	htlatex rasm_fr.tex
	htlatex rasm_fr.tex
	cat rasm_css.txt >> rasm_fr.css
	make clean
	cat rasm_fr.html |sed s/'auto<\/span'/'<\/span'/g >Rasm_fr.html
	rm rasm_fr.html
	mv Rasm_fr.html rasm_fr.html

clean:
	rm -rf *.aux *.dvi *~ main *.log *.toc *.out *.cut *.tmp *.4ct *.4tc *.lg *.xref *.idv *.ind *.idx *.tks *.ilg


mrproper: clean
	rm *.pdf *.html *.css *.png
