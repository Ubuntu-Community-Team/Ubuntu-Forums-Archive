---
title: "LaTeX and graphing software"
date: 2007-02-26
forum: Windows
---

### Post by Thumper322 on 2007-02-26
Hello all,

Under Ubuntu I can use TeTeX (an apt-get install tetex-* does the job) as a LaTeX compiler. The output looks quite nice, and I'd like to be able to use LaTeX on my Windows machine; is MiKTeX any good, and will it be compatible with the .tex files I've already created? I also heard that you could use "gnuplot" or other software along with LaTeX to make good-looking graphs. Is this possible under Windows, and if so, how do I do it?

Thanks for any pointers...

~T22

---

### Post by vayde on 2007-02-27
TeX is TeX  and LaTeX is LaTeX. - or so I've been told.

You shouldn't have any problems running any TeX/LaTeX code anywhere.  Only hitch might be what packages are installed by default under MikTeX.

Can't say about the graphing software.

---

### Post by Xierxes on 2007-02-27
Hi Thumper,

I have been using MikTex, TexnicCenter (a decent Win IDE) and gnuplot for about the last 7 months (I am about 2/3 of the way through my masters at the moment - lots of experiments). Although I have just switched to Ubuntu, I found that this setup worked fantastically for all my LaTex needs. The project option in Texnic Center was great, and I am now starting to look for an IDE that will provide me the same functionality in Ubuntu. 

Of note, though that is if you want to use gnuplot, and want the abiliity to resize graphics in LaTex, use the eps terminal.  This will require you Latex-dvi-pdf (rather than just pdflatex), but again Texnic Center lets you build profiles to make that a one keystroke/mousebutton push.

Hope this helps,

Cheers
Rob

---

### Post by Thumper322 on 2007-03-05
> **Xierxes said:**
> Hi Thumper,

I have been using MikTex, TexnicCenter (a decent Win IDE) and gnuplot for about the last 7 months (I am about 2/3 of the way through my masters at the moment - lots of experiments). Although I have just switched to Ubuntu, I found that this setup worked fantastically for all my LaTex needs. The project option in Texnic Center was great, and I am now starting to look for an IDE that will provide me the same functionality in Ubuntu. 

Of note, though that is if you want to use gnuplot, and want the abiliity to resize graphics in LaTex, use the eps terminal.  This will require you Latex-dvi-pdf (rather than just pdflatex), but again Texnic Center lets you build profiles to make that a one keystroke/mousebutton push.

Hope this helps,

Cheers
Rob

Thanks Rob,

I've managed to get MiKTeX and TeXnicCenter set up, and I have gnuplot sitting on my desktop; it seems to work reasonably well, but I really miss **gedit**... One of the plugins (perhaps in the **gedit-plugins** package) enabled the use of "Snippets"--so, for example, I'd type:
```
itd<TAB>
```
and it would insert:
```
\item[**number**] **text**
```
The nice thing about this, though, is that if I tap TAB, it cycles through the two bolded items. Came quite in handy when doing repetitive stuff, and I would love this functionality under Windows--in any editor!

Lifehacker Code's [Texter]("http://lifehacker.com/software/texter/lifehacker-code-texter-windows-238306.php") utility might be relevant here, but it doesn't seem to support the tabbing; unfortunately, I don't know how to modify the script to include it.

TeXNicCenter also includes autocomplete in the form of Ctrl-Space, as I have discovered, but it doesn't support tabbing either, and doesn't include many items I use. I haven't figured out how to customize autocompletion, so I can't add the things I need.

On another note, is there a tutorial I could reference about using gnuplot with TeXNicCenter automatically?

Thanks for any advice...

Thumper322

---

