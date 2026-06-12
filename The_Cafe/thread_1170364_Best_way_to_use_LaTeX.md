---
title: "Best way to use LaTeX"
date: 2009-05-26
forum: The Cafe
---

### Post by infestor on 2009-05-26
What is the best way to begin writing LaTeX documents (i really cant deal with word processors anymore)? 
should i start using Lyx? or complicated editors like EMACS and dive directly into coding?

My aim is to start writing scientific articles like this: [URL="http://www.tflmezunlari.com/wearing.pdf"]http://www.tflmezunlari.com/wearing.pdf
[/URL]

---

### Post by squaregoldfish on 2009-05-26
I'd suggest you get into coding as quickly as possible - you'll get to learn how LaTeX works, and you'll be using it in the way it was intended.

You don't need a complex editor to code LaTeX. There's endless discussions on here about which editor to use, so you can try a few and see what you like. I've recently switched to gedit with the LaTeX plugin, and I'm liking it a lot.

Steve.

---

### Post by infestor on 2009-05-26
> **squaregoldfish said:**
> I'd suggest you get into coding as quickly as possible - you'll get to learn how LaTeX works, and you'll be using it in the way it was intended.

You don't need a complex editor to code LaTeX. There's endless discussions on here about which editor to use, so you can try a few and see what you like. I've recently switched to gedit with the LaTeX plugin, and I'm liking it a lot.

Steve.


what about the code help? let's say, i would like to add a citation and i dont know the code for it. is there a quick function search in latex plug-in's help section or i have to search the web for it?

---

### Post by Rubicon_82 on 2009-05-26
At the very least, you'll want something with syntax highlighting such as Vim, Emacs, Kate (or a Gnome app which supports this).  

I would recommend Kile, the LaTeX IDE for KDE, which includes standard IDE tools such as autocomplete, automatic multi-step compile etc.  I would avoid LyX if you want to learn LaTeX (LyX tries to hide the underlying LaTeX markup, going so far as labeling it Evil Red Text).

---

### Post by hessiess on 2009-05-26
Just start up your favate editor(vertually enything on Linux has support for TeX/LaTeX hilighing, personally I use Vim) and start wrighting. [The not so short introduction to LaTeX ]("http://tobi.oetiker.ch/lshort/lshort.pdf")introduces the language and syntax pritty well.

> 
what about the code help? let's say, i would like to add a citation and i dont know the code for it. is there a quick function search in latex plug-in's help section or i have to search the web for it?


A quick google can normally show you how to do something in a minute or two.

---

### Post by Twallaroo on 2009-05-26
I prefer winefish.
Very nice LaTeX editor.

---

### Post by swoll1980 on 2009-05-26
Insert "Best way to use latex joke" here______________________________

---

### Post by sujoy on 2009-05-26
stop wasting time at the forums. pick up any editor you like and get set go. :P

---

### Post by pwnst*r on 2009-05-26
> **swoll1980 said:**
> Insert "Best way to use latex joke" here______________________________

must. resist...

---

### Post by ssam on 2009-05-26
any text editor with syntax highlighting and spell checking. gedit is good if you like graphical, or kate for kde, if you know or want to learn a hardcore text editor vim or emacs.

then have this open on a one of your desktops
[http://tobi.oetiker.ch/lshort/lshort.pdf](http://tobi.oetiker.ch/lshort/lshort.pdf)

and search for any other questions. there are lot of resources, and tip pages online, so google can usually find an answer.

beware of really old info. eg there is really any reason to do .tex -> .dvi -> .ps -> .pdf. just use the pdflatex command to get pdf straight away.

---

### Post by jsmidt on 2009-05-26
I think Kyle and Texmaker are the best.  They are very user friendly.

---

### Post by mihai.ile on 2009-06-01
I just use gEdit with gedit-latex-plugin from [http://live.gnome.org/Gedit/LaTeXPlugin](http://live.gnome.org/Gedit/LaTeXPlugin)

So after a year I finally put myself together and created a patch for this gedit-latex-plugin and integrated my Split View module.
With it you can do your LaTeX coding while you preview the generated PDF without doing ALT-TAB to another window every time you need to see how it looks like so far.
I submitted the patch to the author, let's hope he is quick in integrating it, if you are curious about what i'm talking about just look at [http://openmindedbrain.info/gedit-latex-plugin-live-preview](http://openmindedbrain.info/gedit-latex-plugin-live-preview)

---

### Post by kkkkdddd on 2009-06-01
Kile is simply the best.

I have written in it my Masters' Thesis (90 pages of pdf) and it worked very well.

Only one click to generate .pdf and another one to view it. It also includes spell checking (Tools->Spelling).

On the other hand, I liked 1.9 (KDE 3.5) better than 2.1 (KDE 4.2). 

WARNING: Do not use Kile with Compiz enabled. For some reason such combination cause my computer (C2D 2.4 GHz) to work very slowly. I can type faster than letters can appear on the screen.

---

### Post by mihai.ile on 2009-06-01
> **kkkkdddd said:**
> Kile is simply the best.

I have written in it my Masters' Thesis (90 pages of pdf) and it worked very well.

Only one click to generate .pdf and another one to view it. It also includes spell checking (Tools->Spelling).

On the other hand, I liked 1.9 (KDE 3.5) better than 2.1 (KDE 4.2). 

WARNING: Do not use Kile with Compiz enabled. For some reason such combination cause my computer (C2D 2.4 GHz) to work very slowly. I can type faster than letters can appear on the screen.

Did you actually saw hor gedit with latex plugin looks like bfore saying kile it's "the best"?

[IMG]http://openmindedbrain.info/sites/default/files/images/latex-preview.preview.png[/IMG]

It also has spell check (default from gedit), quick buttons to generate pdf and other formats, tables, insert images, has code assist...
I would call Kile very good for LaTeX but calling it the best in my opinion it's a personal preference, not everyone likes/uses KDE...

---

### Post by lethalfang on 2009-06-01
I like Kile, but I'd go get the Kile 2.0 from the Intrepid repo.
I have installed the default Kile 2.1 (actually 2.0.8) that comes with Jaunty in three different computers, and it has severe crashing problems in all three.

I tried LyX for about a couple of days and gave up on it. It's not LaTeX at all. The .lyx file is nothing like a .tex file.

---

### Post by infestor on 2009-06-02
I decided to start with gedit+latex plugin. a simple editor for my needs. since i am not familiar with emacs or vim, trying to learn to use one of them would be like smashing a fly with a sledgehammer.

---

### Post by piousp on 2009-06-02
I use winefish at work, Kyle at home and gedit with my netbook (UNR)

---

### Post by LookTJ on 2009-06-02
All I can say the best way is not to use LyX, it is a pain to use.  It doesn't give you complete control of LaTeX

---

### Post by orlox on 2009-06-03
How can I get gedit with that preview of the file on the side???

---

### Post by zika on 2009-06-03
> **orlox said:**
> How can I get gedit with that preview of the file on the side???
[http://ubuntuforums.org/showthread.php?t=1176257](http://ubuntuforums.org/showthread.php?t=1176257)

---

### Post by [h2o] on 2009-06-03
> **mihai007 said:**
> I just use gEdit with gedit-latex-plugin from [http://live.gnome.org/Gedit/LaTeXPlugin](http://live.gnome.org/Gedit/LaTeXPlugin)

So after a year I finally put myself together and created a patch for this gedit-latex-plugin and integrated my Split View module.
With it you can do your LaTeX coding while you preview the generated PDF without doing ALT-TAB to another window every time you need to see how it looks like so far.
I submitted the patch to the author, let's hope he is quick in integrating it, if you are curious about what i'm talking about just look at [http://openmindedbrain.info/gedit-latex-plugin-live-preview](http://openmindedbrain.info/gedit-latex-plugin-live-preview)

Wow! This plugin is really good! I wish I had known about it before writing three reports using only gedit earlier this semester. This will probably  make writing my master's thesis a lot easier :)

---

### Post by orlox on 2009-06-03
Ooooo, ill certainly be trying this soon. I use kile a lot, but from all the features it has I only use little of them when writing long reports...so the simplicity of gedit is perfect for me!

Besides, this allows me to be using pure gtk apps that fit nicely with my theme, instead of those qt windows that contrast horribly with my dark theme :p

---

### Post by zika on 2009-06-29
It seems it does not work now in Karmic ... ?

---

### Post by zika on 2009-06-29
Isn't that the case with any kind of stuff worth mentioning ... :)
TeX, Ubuntu, ... pick any ... :)

---

