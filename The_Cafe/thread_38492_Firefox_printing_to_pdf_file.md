---
title: "Firefox printing to pdf file"
date: 2005-05-31
forum: The Cafe
---

### Post by macewan on 2005-05-31
](*,) 
Guess I'm a bit of a Google retard this afternoon because I can't seem to find information on having Firefox print to pdf instead of to printer or ps.

Can someone point me in the right direction?  ;-)  And if you used Google could you also provide the search phrase?  :roll:

---

### Post by wmcbrine on 2005-05-31
Just print to PS, then use ps2pdf.

---

### Post by brickbat on 2005-05-31
Hi,

The print to ps and then ps2pdf is not so good for me.  Often when i look at the final result, the text is missing.  It was such a problem that I installed KDE and now I can run Konqueror within gnome and it has a print to pdf function.

Perhaps that is an option for you.

ciao
bb

---

### Post by macewan on 2005-05-31
[QUOTE=wmcbrine]Just print to PS, then use ps2pdf.[/QUOTE]

That's what I had considered doing.

---

### Post by asimon on 2005-06-01
What I do is selecting in Firefox's printing dialog "Properties" and replace the print command line "lpr ..." with "kprinter", thus using KDE's printing framework, which in my opition is the best one available on Linux. There I can choose pdf output, poster print, whatever.

But that doesn't change that Mozilla/Firefox doesn't know pdf, only ps. Thus kprinter transforms Firefox's ps outout to pdf, and if that fails on your command line chances are that it will fail with kprinter as well.

---

### Post by macewan on 2005-06-01
[QUOTE=asimon]What I do is selecting in Firefox's printing dialog "Properties" and replace the print command line "lpr ..." with "kprinter", thus using KDE's printing framework, which in my opition is the best one available on Linux. There I can choose pdf output, poster print, whatever.

But that doesn't change that Mozilla/Firefox doesn't know pdf, only ps. Thus kprinter transforms Firefox's ps outout to pdf, and if that fails on your command line chances are that it will fail with kprinter as well.[/QUOTE]


I'll give it a try. Thanks

---

### Post by doans on 2005-06-01
I have been trying to come up with a solution to the same problem.  And, what I have been doing lately is using a ps2pdf script file placed in gnome-scripts folder.  This way I right click on the ps file that firefox generated and with the click of a mouse I have a pdf file with the same name.

Doesn't really "solve" the problem, but it definitely makes it simpler. Since I generate a lot of pdf files throughout the day doing research.

The only thing I don't know how to do is have the ps file automatically deleted after being converted to pdf.  Maybe someone can help me with this.  Hope this helps you.

Here is the script file: Which I save in the gnome-script folder (/user/name/.gnome2/nautilus-scripts) as p2pdf and give execute permission.

#!/bin/sh
# PS2PDF converts a PostScript file to PDF, using GhostScript.

OPTIONS=""

while true
do
  case "$1" in
  -*) OPTIONS="$OPTIONS $1" ;;
  *)  break ;;
  esac
  shift
done

if [ $# -lt 1 -o $# -gt 2 ]; then
  echo "Usage: `basename $0` [options...] input.ps [output.pdf]" 1>&2
  exit 1
fi

infile=$1;

if [ $# -eq 1 ]
then
  case "${infile}" in
    *.ps) base=`basename ${infile} .ps` ;;
    *) base=`basename ${infile}` ;;
  esac
  outfile=${base}.pdf
else
  outfile=$2
fi
#
#  Doing an initial 'save' helps keep fonts from being flushed between pages.
#
#  Replace "/home/ghost/bin/axp/gs510" by the correct path for GhostScript.
#
exec /usr/bin/gs -q -dNOPAUSE -dBATCH -sDEVICE=pdfwrite \
  -sOutputFile=$outfile $OPTIONS -c save pop -f $infile

---

### Post by az on 2005-06-01
Holy moley!


Just install cups-pdf!

Package: cups-pdf (1.6.3-3) [universe]
PDF Writer backend for CUPS

CUPS-PDF provides a PDF Writer backend to CUPS. It can be used to provide a virtual printer to a paperless network or to perform testing on CUPS.

---

### Post by kiddyfurby on 2005-06-08
hi there
I installed cups-pdf
but its not showing up in firefox
I saw it in print dialog of gedit though

---

### Post by brickbat on 2005-06-08
Losing the text also happens using kprinter from Firefox but it is a good idea anyway.  When I print it from konqueror to kpinter it works perfectamundo!

ciao
bb

---

### Post by rwabel on 2005-08-09
[QUOTE=azz]Holy moley!


Just install cups-pdf!

Package: cups-pdf (1.6.3-3) [universe]
PDF Writer backend for CUPS

CUPS-PDF provides a PDF Writer backend to CUPS. It can be used to provide a virtual printer to a paperless network or to perform testing on CUPS.[/QUOTE]

are u talking about kprinter? When I setup a pdf printer I still only get ps files. I've cups-pdf installed and gnome-print detects PDF Printer

---

### Post by Franko30 on 2005-08-23
The problem is that Firefox seems to produce invalid Postscript output to begin with.

That's what I found out searching the forum and when printing to *.ps files from within Firefox - Ghostview can't open the resulting files...

So if already Firefox's postscript output is faulty, everything after this (Cups-PDF or gtklp or kprinter) can't produce any usable result.

I'm using Ubuntu 5.04 Hoary, all the latest updates installed (thus using Firefox 1.0.6).

---

### Post by rwabel on 2005-08-23
[QUOTE=Franko30]The problem is that Firefox seems to produce invalid Postscript output to begin with.

That's what I found out searching the forum and when printing to *.ps files from within Firefox - Ghostview can't open the resulting files...

So if already Firefox's postscript output is faulty, everything after this (Cups-PDF or gtklp or kprinter) can't produce any usable result.

I'm using Ubuntu 5.04 Hoary, all the latest updates installed (thus using Firefox 1.0.6).[/QUOTE]
 within opera it's not much better!

---

### Post by MorayJ on 2007-09-24
This seems to be something of an old discussion, so there may be a solution already well known.

I've just come across the problem and what I'm doing (having installed the pdf -cups) is printing to postscript from mozilla and then printing to the pdf printer from evince.

Haven't done much testing - one page - but if it continues to work,  that should do for me for the time being.

---

