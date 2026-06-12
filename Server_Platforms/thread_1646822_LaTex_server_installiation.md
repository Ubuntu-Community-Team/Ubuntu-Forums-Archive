---
title: "LaTex server installiation"
date: 2010-12-16
forum: Server Platforms
---

### Post by Rapademic on 2010-12-16
I have installed LaTex onto my Ubuntu 10.02.1 LTS server using sudo apt-get install texlive-full.  When I am logged onto the server, LaTex works fine.  I exported the server /usr directory to my Ubunut Desktop 10.04 machine so that I could have assess to the servers installed version of LaTex.  The mount point on the Desktop is: /serverName/usr.  When I LaTex a file while logged onto the Destop machine, I get the following error:
latex letter.tex
warning: kpathsea: configuration file texmf.cnf not found in these directories: /usr/share/texmf/web2c:/usr/share/texmf-texlive/web2c:/usr/local/share/texmf/web2c.
This is pdfTeX, Version 3.1415926-1.40.10 (TeX Live 2009/Debian)

kpathsea: Running mktexfmt latex.fmt
.: 972: Can't open /usr/share/texlive-bin/debianize-fmtutil
I can't find the format file `latex.fmt'!

It looks like LaTex is looking at a compiled in directory structure and cannot find what it needs.
Can anyone tell me how to export the servers version of LaTex so that I only need to install LaTex once on the server but can use it from any of our Desktop machines?  Thanks.

---

