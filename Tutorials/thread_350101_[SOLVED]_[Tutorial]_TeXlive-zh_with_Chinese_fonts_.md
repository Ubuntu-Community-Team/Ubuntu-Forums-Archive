---
title: "[SOLVED] [Tutorial] TeXlive-zh with Chinese fonts already installed"
date: 2007-01-31
forum: Tutorials
---

### Post by pabix on 2007-01-31
Hello!

This is a translation of [this thread]("http://forum.ubuntu-fr.org/viewtopic.php?id=92901") on the French forums.

Have you ever tried to install Chinese fonts on your LaTeX distribution, and, like me, failed to do so? This topic introduces a way to install a LaTeX distribution with *already installed* Chinese fonts. This method will work with any Linux distribution, not only Ubuntu. Executables are compiled for i386 systems only.

**Warnings***

TeXlive-zh is a *non-official* distibution and contains *non-commercial* licensed fonts. For a commercial use of the fonts bsmi and gbsn, please ask &#20013;&#26131; [www.china-e.com.cn]("http://www.china-e.com.cn") et &#26041;&#27491; [www.foundertech.com]("http://www.foundertech.com")

There are no Japanese, Korean, Tamil or Thai fonts here. 

Most commands here require high user privileges. They are preceeded by a # symbol, and other commands with a $ symbol. # instructions must be executed as root or with *sudo*.

**Source of this tutorial**
Instructions in Chinese are here: [http://forum.ubuntu.org.cn/about28455.html&sid=f6a06858f003aec6b5bc6e9f410a8b7c]("http://forum.ubuntu.org.cn/about28455.html&sid=f6a06858f003aec6b5bc6e9f410a8b7c")

**1. Try it, or install it**
**1.1 First method (more efficient, but longer to download)**
[LIST]
[*]Download the ISO file linked to the Chinese tutorial. You can make a coffee or so during the download
[*]Mount that ISO file on /mnt:
```
# mount -o loop texlive.iso /mnt
```
[*]Mount the SquashFS on /usr/local/texlive:
```
# mount -t squashfs -o loop,ro /mnt/texlive.squashfs /usr/local/texlive
```
[*]&#8317;¹&#8318; Add it to the PATH:
```
$ export PATH=/usr/local/texlive/2005/bin/i386-linux/:$PATH
```
[/LIST]

Done! If you want to install it, create (#) a directory, eG /usr/local/texlive-zh, and run
```
# cp -a /usr/local/texlive /usr/local/texlive-zh
```
then, add /usr/local/texlive-zh to the PATH variable in /etc/environment, for example editing it (#) with nano. You can then unmount /mnt/texlive.squashfs, the iso file, and remove that iso file.

**1.2. Alternate method (quicker)**
[LIST]
[*]Install 7-zip (package for ubuntu may be named p7zip)
[*]Download this file [here]("http://morceauxchoisis.free.fr/texlive-zh/CTeXLive20051018.iso.7z") (server in France) or [there]("http://thinfilm.ustc.edu.cn/~liangzi/software/CTeXlive/CTeXLive20051018.iso.7z") (server in China). Size should be 577MB, md5sum is f87201d93a3752b283fe19ad1f483f00.
[*]Uncompress that file (and then remove it if you want):
```
$ 7zr e CTeXLive20051018.iso.7z
```
(note: the command may be 7z instead of 7zr on some distributions)
[*]Mount the ISO file that has been extracted:
```
# mount -o loop CTeXLive20051018.iso /usr/local/texlive
```
[*]Go to the &#8317;¹&#8318; mark in method 1.
[/LIST]

**2. Sample LaTeX Document**
**2.1 LaTeX Source**
```
\documentclass{article}
\usepackage{CJKutf8}
\begin{document}
\begin{CJK*}{UTF8}{song}
&#36825;&#26159;&#19968;&#20010;&#27979;&#35797;
\end{CJK*} (this is a test)
\end{document}
```
song font can be replaced with gbsn, or bsmi for traditional characters set.
**2.2 Compiling**
If you want it, you can use my Makefile: just type «*make*» without arguments, and your LaTeX files in the working directory will be pdfLaTeXed. Available [here]("http://morceauxchoisis.free.fr/code/Makefile.gz").

**Thanks and feedback**
I hope you will enjoy it. Thanks to Yule Wang, and the creators of that distribution. If you have problems, contact me for example, or leave a MemoServ note for pabix on irc.freenode.net.

---

### Post by ziphi on 2009-09-10
You just made my day! I know this thread is fairly old, but I still want to express my gratitude!

Your fix works fine for me, although the "song" font is troublesome for some reason: See the attached logfile. Maybe someone could help me with this? I assume I just have to install the font correctly, just don't know where to edit which file...
It worked flawlessly using the gbsn font, though!

Thanks!

---

### Post by waldherrvonbirnbaum on 2013-02-22
Old thread, but for people who are interested:

I installed

latex-cjk-chinese
latex-cjk-common

via [https://apps.ubuntu.com/cat/applications/latex-cjk-chinese/](https://apps.ubuntu.com/cat/applications/latex-cjk-chinese/)

the software-center couldn't find  it by itself.

The LaTeX-code i used is:
```
 
\documentclass[11pt,ngerman]{article}
\usepackage[utf8]{inputenc}
\usepackage{graphicx}
\usepackage{tipa}
\usepackage{CJK}
\usepackage[ngerman]{babel}


(\begin{CJK}{UTF8}{gbsn}
&#35841;
\end{CJK}

```The terminal gives no errors with pdflatex and it works.
thx to [http://blog.philippklaus.de/2009/08/chinese-input-in-latex/](http://blog.philippklaus.de/2009/08/chinese-input-in-latex/)

---

