#
# "$Id: Makefile 8195 2011-01-05 23:00:33Z AlbrechtS $"
#
# Documentation makefile for the Fast Light Tool Kit (NTK).
#
# Copyright 1998-2010 by Bill Spitzak and others.
#
# This library is free software; you can redistribute it and/or
# modify it under the terms of the GNU Library General Public
# License as published by the Free Software Foundation; either
# version 2 of the License, or (at your option) any later version.
#
# This library is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
# Library General Public License for more details.
#
# You should have received a copy of the GNU Library General Public
# License along with this library; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307
# USA.
#
# Please report all bugs and problems on the following page:
#
#      http://www.ntk.org/str.php
#

# Get configuration stuff...
include ../makeinclude

# make sure that all docs are (re-)created independent of missing deps
.PHONY: pdf html refman.pdf

SRC_DOCDIR      = 	./src

# These are the HTML "source" files...
HTMLFILES	= 	 \
			 $(SRC_DOCDIR)/index.dox \
                         $(SRC_DOCDIR)/preface.dox \
                         $(SRC_DOCDIR)/intro.dox \
                         $(SRC_DOCDIR)/basics.dox \
                         $(SRC_DOCDIR)/common.dox \
                         $(SRC_DOCDIR)/editor.dox \
                         $(SRC_DOCDIR)/drawing.dox \
                         $(SRC_DOCDIR)/events.dox \
                         $(SRC_DOCDIR)/subclassing.dox \
                         $(SRC_DOCDIR)/opengl.dox \
                         $(SRC_DOCDIR)/fluid.dox \
                         $(SRC_DOCDIR)/advanced.dox \
                         $(SRC_DOCDIR)/unicode.dox \
                         $(SRC_DOCDIR)/enumerations.dox \
                         $(SRC_DOCDIR)/glut.dox \
                         $(SRC_DOCDIR)/forms.dox \
                         $(SRC_DOCDIR)/osissues.dox \
                         $(SRC_DOCDIR)/migration_1_1.dox \
                         $(SRC_DOCDIR)/migration_1_3.dox \
                         $(SRC_DOCDIR)/development.dox \
                         $(SRC_DOCDIR)/license.dox \
                         $(SRC_DOCDIR)/examples.dox

MANPAGES =	$(SRC_DOCDIR)/ntk.$(CAT3EXT) $(SRC_DOCDIR)/ntk-config.$(CAT1EXT) \
		$(SRC_DOCDIR)/fluid.$(CAT1EXT) $(SRC_DOCDIR)/blocks.$(CAT6EXT) \
		$(SRC_DOCDIR)/checkers.$(CAT6EXT) $(SRC_DOCDIR)/sudoku.$(CAT6EXT)

all:	$(MANPAGES)

# use make dist to create all docs for distribution files
# you need an installed version of doxygen for this
dist:	all html pdf

# synonym for dist
alldocs: dist

clean:
	$(RM) ntk.pdf refman.pdf
	$(RMDIR) html latex
	$(RM) *~ *.bck *.bak *.log
	$(RM) $(MANPAGES) $(SRC_DOCDIR)/*.0

depend:

install: $(MANPAGES)
	echo "Installing documentation files in $(DESTDIR)$(docdir) ..."
	-$(INSTALL_DIR) $(DESTDIR)$(docdir)
	if test -f html/index.html ; then \
	  for file in html/* ; do \
		$(INSTALL_DATA) $$file $(DESTDIR)$(docdir); \
	  done \
	fi
	if test -f ntk.pdf ; then \
	  echo "Installing ntk.pdf in $(DESTDIR)$(docdir) ..."; \
	  $(INSTALL_DATA) ntk.pdf $(DESTDIR)$(docdir); \
	fi
	echo "Installing man pages in $(DESTDIR)$(mandir) ..."
	-$(INSTALL_DIR) $(DESTDIR)$(mandir)/cat1
	$(INSTALL_MAN) $(SRC_DOCDIR)/fluid.$(CAT1EXT) $(DESTDIR)$(mandir)/cat1
	$(INSTALL_MAN) $(SRC_DOCDIR)/ntk-config.$(CAT1EXT) $(DESTDIR)$(mandir)/cat1
	-$(INSTALL_DIR) $(DESTDIR)$(mandir)/cat3
	$(INSTALL_MAN) $(SRC_DOCDIR)/ntk.$(CAT3EXT) $(DESTDIR)$(mandir)/cat3
	-$(INSTALL_DIR) $(DESTDIR)$(mandir)/man1
	$(INSTALL_MAN) $(SRC_DOCDIR)/fluid.man $(DESTDIR)$(mandir)/man1/fluid.1
	$(INSTALL_MAN) $(SRC_DOCDIR)/ntk-config.man $(DESTDIR)$(mandir)/man1/ntk-config.1
	-$(INSTALL_DIR) $(DESTDIR)$(mandir)/man3
	$(INSTALL_MAN) $(SRC_DOCDIR)/ntk.man $(DESTDIR)$(mandir)/man3/ntk.3

install-linux install-osx:
	-$(INSTALL_DIR) $(DESTDIR)$(mandir)/cat6
	$(INSTALL_MAN) $(SRC_DOCDIR)/blocks.$(CAT6EXT) $(DESTDIR)$(mandir)/cat6
	$(INSTALL_MAN) $(SRC_DOCDIR)/checkers.$(CAT6EXT) $(DESTDIR)$(mandir)/cat6
	$(INSTALL_MAN) $(SRC_DOCDIR)/sudoku.$(CAT6EXT) $(DESTDIR)$(mandir)/cat6
	-$(INSTALL_DIR) $(DESTDIR)$(mandir)/man6
	$(INSTALL_MAN) $(SRC_DOCDIR)/blocks.man $(DESTDIR)$(mandir)/man6/blocks.6
	$(INSTALL_MAN) $(SRC_DOCDIR)/checkers.man $(DESTDIR)$(mandir)/man6/checkers.6
	$(INSTALL_MAN) $(SRC_DOCDIR)/sudoku.man $(DESTDIR)$(mandir)/man6/sudoku.6


uninstall:
	$(RMDIR) $(DESTDIR)$(docdir)
	$(RM) $(DESTDIR)$(mandir)/cat1/fluid.$(CAT1EXT)
	$(RM) $(DESTDIR)$(mandir)/man1/fluid.1
	$(RM) $(DESTDIR)$(mandir)/cat1/ntk-config.$(CAT1EXT)
	$(RM) $(DESTDIR)$(mandir)/man1/ntk-config.1
	$(RM) $(DESTDIR)$(mandir)/cat3/ntk.$(CAT3EXT)
	$(RM) $(DESTDIR)$(mandir)/man3/ntk.3

uninstall-linux uninstall-osx:
	$(RM) $(DESTDIR)$(mandir)/cat6/blocks.$(CAT6EXT)
	$(RM) $(DESTDIR)$(mandir)/cat6/checkers.$(CAT6EXT)
	$(RM) $(DESTDIR)$(mandir)/cat6/sudoku.$(CAT6EXT)
	$(RM) $(DESTDIR)$(mandir)/man6/blocks.6
	$(RM) $(DESTDIR)$(mandir)/man6/checkers.6
	$(RM) $(DESTDIR)$(mandir)/man6/sudoku.6

# The HTML files are now generated using doxygen, and this needs
# an installed doxygen version and may take some time, so this target
# is not made by default.
# Use `make html' or `make dist' to create the html docs

html:	$(HTMLFILES) Doxyfile
	echo "Generating HTML documentation..."
	-$(RMDIR) html
	-$(INSTALL_DIR) html
	-$(DOXYDOC)
	if test "x$(DOXYDOC)" = "x" ; then \
	  echo "Sorry - doxygen not found. Please install doxygen and run configure."; \
	fi
	test -d html && cp src/tiny.png html/

# this is only used to minimize subversion updates of the online docs
html-online: html
	echo "*** Warning: re-create HTML files if you want to build distribution files."
	echo "*** Warning: Use 'make html' to re-create the correct HTML files."
	echo "Stripping HTML files for online documentation upload..."
	./strip_tags

pdf:	refman.pdf
	cp -f latex/refman.pdf ntk.pdf

refman.pdf: $(HTMLFILES) Doxybook
	-$(RMDIR) latex
	echo "Generating PDF documentation ..."
	$(DOXYDOC) Doxybook ;\
	(cd latex ;\
	pdflatex --interaction=nonstopmode refman.tex ;\
	makeindex refman.idx ;\
	pdflatex --interaction=nonstopmode refman.tex ;\
	latex_count=5;\
	while egrep -s 'Rerun (LaTeX|to get cross-references right)' refman.log \
		&& [ $$latex_count -gt 0 ] ;\
	    do \
	      echo "Rerunning latex ..." ;\
	      pdflatex --interaction=nonstopmode refman.tex ;\
	      latex_count=`expr $$latex_count - 1` ;\
	    done ; \
	cd ..) > pdfall.log 2>&1

#
# End of "$Id: Makefile 8195 2011-01-05 23:00:33Z AlbrechtS $".
#
