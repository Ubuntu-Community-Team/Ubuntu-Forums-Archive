---
title: "LaTeX"
date: 2007-11-18
forum: The Cafe
---

### Post by Lostincyberspace on 2007-11-18
Does anyone know of another GUI front end for LaTeX like lyx. :)

---

### Post by perce on 2007-11-19
I don't exactly know what you mean. If you want something which allows you to input symbols from a menu you could try kyle (a KDE application, but it suns under Gnome too). If you want to see the dvi file in real time  when you are typing you can try (x)emacs + whizzytex. 

I personally use XEmacs with an extension called x-symbols. X-symbols put some symbols in place of the command in the XEmacs buffer, and also allows you to choose the symbol from a menu if you don't remember the command. Unfortunately x-symbols is no longer maintained, and you have to download it from Debian's historical archive, but it's still working.

---

### Post by Miguel on 2007-11-19
You also have TeXmaker, but it's also a Qt app. I must admit I don't know what GTk2 app I could use to edit LaTeX files, apart from gvim running the vim-latexsuite plugin (which is what I actually do).

Isn't there a list in "The not so short introduction to LaTeX2e" (A must read if you are new to LaTeX)???. Also, I'd browse synaptic and google.

---

### Post by MaximusTG on 2007-11-19
I use winefish, it's in the repositories.

sudo apt-get install winefish

---

### Post by Kimm on 2007-11-19
I use GEdit with spellchecking and a script in Thunar to turn it into a PDF file :popcorn:

---

### Post by conehead77 on 2007-11-19
> **MaximusTG said:**
> I use winefish, it's in the repositories.

sudo apt-get install winefish

I just tried winefish, but got a error when i wanted to make a "Hello, world" pdf.

```
! LaTeX Error: File `ifpdf.sty' not found.
```
Im a complete LaTeX noob, so it might be trivial... any idea to fix this?
I found the ifpdf.sty file with google, but dont know what to do with it, lol

Edit: Already solved after i removed all /usepackage lines. I think adding packages will be described somewhen later in my tutorial ;)

---

### Post by mannheim on 2007-11-19
> **conehead77 said:**
> I just tried winefish, but got a error when i wanted to make a "Hello, world" pdf.

```
! LaTeX Error: File `ifpdf.sty' not found.
```


If you are using Gutsy, you should install the package texlive-latex-recommended:
```
sudo apt-get install texlive-latex-recommended
```
(or use synaptic to install it). This will give you ifpdf.sty

---

### Post by conehead77 on 2007-11-19
> **mannheim said:**
> If you are using Gutsy, you should install the package texlive-latex-recommended:
```
sudo apt-get install texlive-latex-recommended
```
(or use synaptic to install it). This will give you ifpdf.sty

Ah, thank you, now it all works :)

---

### Post by Lostincyberspace on 2007-11-19
What I was looking for is a wysiwyg type editor like lyx is, but better, more abilitys like being able to center text, that is hard to do lyx. I use Texmaker righ now but it takes to long to edit problems in the content.

---

### Post by perce on 2007-11-20
> **Lostincyberspace said:**
> more abilitys like being able to center text, that is hard to do lyx. 

To center in LaTeX:

\begin{center}

the text you whant to center

\end{center}

You don't need a wysiwyg editor for something that easy.

---

### Post by firefoxdl on 2007-11-20
i'm using winefish:popcorn:

---

### Post by hugmenot on 2007-11-20
Gedit with LaTeX-Plugin: [http://live.gnome.org/Gedit/LaTeXPlugin](http://live.gnome.org/Gedit/LaTeXPlugin)

---

### Post by mustang on 2007-11-20
sudo apt-get install kile

---

### Post by Lostincyberspace on 2007-11-20
I have decide I need to learn how to code well enough to make my own that is good. I like Kiles auto complete feature, I like the setup of texmaker, but I really want a whysiwhyg interface with a more advanced set of options than lyx.

---

### Post by jpkotta on 2007-11-21
[x]emacs and AUCTeX.

---

### Post by mustang on 2007-11-25
> **mannheim said:**
> If you are using Gutsy, you should install the package texlive-latex-recommended:
```
sudo apt-get install texlive-latex-recommended
```
(or use synaptic to install it). This will give you ifpdf.sty

Thanks :)

---

