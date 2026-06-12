---
title: "LaTeX"
date: 2005-09-16
forum: The Cafe
---

### Post by natman on 2005-09-16
does anyone know does LaTeX come free with Ubuntu? and if so does it also come with the drawing package called Xfig ?

Thank You:

---

### Post by Manny C on 2005-09-16
Latex is free. You need to install the tetex packages and an editor (perhaps kile). Then install xfig separately.

---

### Post by Arktis on 2005-09-16
I have no idea what it is, but a quick search in synaptec gave me 35 results which in the descriptions were all spelled in the same funky cases you used. ("LaTeX")
xfig is also present in the repos.

So, yeah.

---

### Post by majikstreet on 2005-09-16
[QUOTE=Arktis]I have no idea what it is, but a quick search in synaptec gave me 35 results which in the descriptions were all spelled in the same funky cases you used. ("LaTeX")
xfig is also present in the repos.

So, yeah.[/QUOTE]
 I believe LaTeX is a type of text editing... (@ Arktis)



 It never made sense to me why you would code a text document... Please explain what is so good about it (@ the topic starter)

---

### Post by Ampersand on 2005-09-16
It's useful for things like typing equations from what I understand.

---

### Post by parktownprawn on 2005-09-16
to install latex type ```
sudo apt-get install tetex-bin tetex-base
```

you may want to also install the extra packages
```
sudo apt-get install tetex-extra
```

xfig is in the universe repository - after enabling  the universe repositories type ```
sudo apt-get install xfig 
```

to have some idea of all the latex related packages in ubuntu check out 

[http://packages.ubuntu.com/hoary/tex/](http://packages.ubuntu.com/hoary/tex/)

more info at 
[http://wiki.ubuntu.com/LaTeX](http://wiki.ubuntu.com/LaTeX)

if you use latex you may also be a researcher and interested in

[https://wiki.ubuntu.com/UbuntuScientists](https://wiki.ubuntu.com/UbuntuScientists)

---

### Post by macgyver2 on 2005-09-16
[QUOTE=majikstreet]I believe LaTeX is a type of text editing... (@ Arktis)



 It never made sense to me why you would code a text document... Please explain what is so good about it (@ the topic starter)[/QUOTE]
If I may jump in...

LaTeX isn't text editing...it's document formatting.  As to why I personally use it...well first, I had to learn because it's pretty much the only way most astronomy-related publications will accept stuff.  Second, I use it for a lot of other things I write now because I think it looks a lot nicer--with less effort--than something that comes out of AbiWord or OpenOffice or Word or whatever other program like that.  Less effort once you learn it, of course...like Linux, it's one of those steeper initial learning curve, easier later on type things, IMO.  And, a couple of times I've actually benefitted from the fact that you don't need a GUI to prepare a document from start to finish with LaTeX.

---

### Post by Leif on 2005-09-16
[QUOTE=majikstreet] It never made sense to me why you would code a text document... Please explain what is so good about it (@ the topic starter)[/QUOTE]

Because it allows you to write a paper without fiddling with the formatting the whole time. Because it handles long documents, with all the indexing etc., very well (last time I used Word for a long document it sucked, but this was a way back, so maybe this is not such a great advantage anymore). And finally, because documents produced with it just look better and more professional.

---

### Post by majikstreet on 2005-09-16
Alrighty makes sense... If I install it using the above instructions, how do I use it?

---

### Post by Paulus on 2005-09-16
yeah latex is an amazing program.  If you have to submit mathematics papers, this is where it's at!    It is quite hard to learn, but once you've learn't how to use it, anything written on it looks as professional as it gets.

---

### Post by Leif on 2005-09-16
[QUOTE=majikstreet]Alrighty makes sense... If I install it using the above instructions, how do I use it?[/QUOTE]

[http://www-h.eng.cam.ac.uk/help/tpl/textprocessing/](http://www-h.eng.cam.ac.uk/help/tpl/textprocessing/)

Have fun !

---

### Post by GeneralZod on 2005-09-16
[QUOTE=Leif]Because it allows you to write a paper without fiddling with the formatting the whole time. Because it handles long documents, with all the indexing etc., very well (last time I used Word for a long document it sucked, but this was a way back, so maybe this is not such a great advantage anymore). And finally, because documents produced with it just look better and more professional.[/QUOTE]

Also, it's cross-platform, *stunningly* flexible (it is, after all, a programming language unto itself!) and all files are plain-text, so you can edit them with whatever tools you prefer.

It has a very steep learning curve, however.

LyX and Texmacs are GUI front-ends; I've no idea whether these force a trade-off between flexibility and ease-of-use, though, as I've never used them (I use Kile).

---

### Post by Leif on 2005-09-16
[QUOTE=GeneralZod]LyX and Texmacs are GUI front-ends; I've no idea whether these force a trade-off between flexibility and ease-of-use, though, as I've never used them (I use Kile).[/QUOTE]

I think LyX is a bit more than a front-end Although it can import/export latex files, it has its own internal format. Never used it much, so I may be wrong about this.

And yes, latex has a steep learning curve, but getting a first document done is quite easy, especially if you have someone else's to look at :)

---

### Post by macgyver2 on 2005-09-16
[QUOTE=Leif]I think LyX is a bit more than a front-end Although it can import/export latex files, it has its own internal format. Never used it much, so I may be wrong about this.[/QUOTE]
LyX is good, though not perfect.  I tried it for a few papers...though that was about a year-and-a-half ago.  I don't know what's changed since then.  

If it hasn't changed (which I don't think it has much...current version is 1.3.6 and I think I tried 1.3.3), I can see where there might be hiccups for someone totally unfamiliar with LaTeX because there were times when LyX couldn't handle something and to get it to look right I had to use LyX's option of just inserting the code myself.

---

### Post by sumadartson on 2005-09-16
I've been using LaTeX for a somewhat mathematically oriented master thesis and so far it's been amazing.

The comparison to Linux is dead on for me. Yes, it has a relatively steep learning curve and, yes, some things are a tad more complicated then you'd expect (changing fonts and inserting graphics anyone?). But, things that seem complicated at first will quickly become second nature and the steep learning curve pays off in the end.

Areas where it shines are bibliography management (consistent references across your entire document), math formatting and handling large documents. O, and you can define custom commands and "environments", which means that you never have to do repetitive formatting work. Yay!

---

### Post by Lux Perpetua on 2005-09-16
Read through "lshort.pdf" or at least the first few chapters to get a feel for LaTeX. That's a nice, friendly introduction to the language ("The Not So Short Introduction to LaTeX2e" by Tobias Oetiker). It's also a usable reference for everyday tasks. It's on CTAN. I don't have the link right now, but it'll be at the top of a Google search. 

I've been using LaTeX for a few years now. A document written in LaTeX looks professional by default. In the typesetting of mathematical formulas, TeX/LaTeX probably has no equal. 

That said, I don't really care for the language itself; I've always found it rather awkward. Also, it can be very frustrating when it doesn't do what you think it should or you want it to do something unusual. I've found LaTeX to be like a cookie cutter sometimes, but that *could* just be my lack of experience (I'm not saying it is, but I don't know that it isn't).

---

### Post by Manny C on 2005-09-16
The english version of the Not So Short ... is found [here](http://ctan.unsw.edu.au/info/lshort/english/)

---

### Post by Manny C on 2005-09-16
Oh, and to use latex, that is to say, to code a document, you need an editor. A really good editor is kile:

```
sudo apt-get install kile
``` 

However, you can also install [emacs](http://www.emacswiki.org/cgi-bin/wiki)  with [auctex](http://www.gnu.org/software/auctex/)  and other packages:

```
sudo apt-get install emacs auctex preview-latex whizzytex advi
```

The latter two allow you to see what you are texing while you type. To activate whizzytex mode in emacs while texing a document:

```
Meta-x whizzytex-mode
``` and advi should automatically open and display your tex document.

Further, if you want to see what a tex document looks like see the attached screenshot. This show kile editing a latex document. Oh, it is really really important that you read the Not-So Short guide. It is the beginners bible to latex.

---

### Post by kleeman on 2005-09-16
Lyx is a very user friendly latex frontend (see my avator). It has it own file syntax (*.lyx) files but exports a pretty good latex product. Typically I write a paper with lyx because I can't remember enough latex and usually export it to latex for final (text) editing before submission. Usually with lyx you can get most of the math and typesetting you need done but often journals have very particular typesetting requirements that lyx cannot handle. This doesn't take much to sort out in the exported latex file. They have a good wiki here:

 [http://wiki.lyx.org/LyX/LyX](http://wiki.lyx.org/LyX/LyX)

and a good mailing list here:

[http://www.mail-archive.com/lyx-users@lists.lyx.org/](http://www.mail-archive.com/lyx-users@lists.lyx.org/)

the mailing list is high level (many developers) and friendly. I have got useful help there often.

---

### Post by nebula on 2005-09-20
Ok, so I tried tetex (without extra I believe) but I often use the fancy header package, which tetex doesn't know. In windows I use miktex, maye me m$ but miktex has the nice extra that it installs missing packages on the fly. Is there a linux version of LaTeT wich does the same thing?

---

### Post by sumadartson on 2005-09-20
Good question. I have as yet to install Lyx* on my Ubuntu box at home, but that package manager from Miktex is heaven. I'm not aware of any Linux equivalent.

There's a small [LaTeX entry in the wiki](https://wiki.ubuntu.com/LaTeX?highlight=%28latex%29)  though. It also mentions where to get packages.


* Kyle had a *very* short lifespan on my pc.

---

### Post by parktownprawn on 2005-09-21
[QUOTE=nebula]Ok, so I tried tetex (without extra I believe) but I often use the fancy header package, which tetex doesn't know. In windows I use miktex, maye me m$ but miktex has the nice extra that it installs missing packages on the fly. Is there a linux version of LaTeT wich does the same thing?[/QUOTE]

there is no such auto-install program for linux but it wouldn't be too hard to write one....

the styles  fancyhdr and fancyheadings are in tetex-extra which probably has most of what you want. there are gazillions of latex related debian packages - just search for them in synaptic or go to [http://packages.ubuntu.com/warty/tex/](http://packages.ubuntu.com/warty/tex/). 

Even relatively specialized packages are only an apt-get away (eg ethiop for typesetting Ethiopian texts).

---

### Post by AndrewStout on 2005-09-21
[QUOTE=GeneralZod]LyX and Texmacs are GUI front-ends; I've no idea whether these force a trade-off between flexibility and ease-of-use, though, as I've never used them (I use Kile).[/QUOTE]

I took a quick look at Kile...it looks nice, but it looks like it depends on KDE.
1. Is there an equivalent that doesn't require KDE?  or can one run Kile without running KDE?
2. Wouldn't it make more sense to write a LaTeX "ILE" that can be used more widely, i.e. doesn't depend on KDE?

--Andrew

---

### Post by kleeman on 2005-09-22
You're looking for TexMaker I suspect.

[http://www.ubuntuforums.org/showthread.php?t=9986&highlight=texmaker](http://www.ubuntuforums.org/showthread.php?t=9986&highlight=texmaker)

It loads a lot faster than kile too.

---

### Post by GeneralZod on 2005-09-22
[QUOTE=AndrewStout]I took a quick look at Kile...it looks nice, but it looks like it depends on KDE.
1. Is there an equivalent that doesn't require KDE?  or can one run Kile without running KDE?
2. Wouldn't it make more sense to write a LaTeX "ILE" that can be used more widely, i.e. doesn't depend on KDE?

--Andrew[/QUOTE]

You'll need KDE installed, but can obviously run Kile under GNOME.  You'll take a slight hit in memory usage as it will require some KDE libs to be loaded into memory, but this shouldn't really be noticeable.

All GUI apps depend on some toolkit or other (unless - *shudder* - they include their own!), so #2 is not really tenable - if it doesn't depend on KDE/Qt, then it will probably depend on GNOME/GTK, and then we KDE lovers would be complaining! ;)

Of course, you could always be a masochist and use emacs! :D

---

### Post by parktownprawn on 2005-09-22
[QUOTE=kleeman]You're looking for TexMaker I suspect.

[http://www.ubuntuforums.org/showthread.php?t=9986&highlight=texmaker](http://www.ubuntuforums.org/showthread.php?t=9986&highlight=texmaker)

It loads a lot faster than kile too.[/QUOTE]

yup i just tried out texmaker and although it uses Qt it doesn't depend on all the kde gumf so it loads a lot faster if you are running gnome.

on the downside it doesn't seem to have the cool backward search feature that i got working under kile.

---

### Post by petr on 2005-09-22
Yea I'm a LaTeX and xfig fan.
 - LateX separates content from format - which means it is quicker to write stuff because I don't fiddle with format.
 - It uses an ascii (txt) file (xxx.tex) as input which means I can edit a document with notepad or indeed vi.
 - a default output is ps, but pdf is easy and systematic.
 - many publishers (esp Springer) provide style files for you.  I usually allocate about one hour to format a paper appropriately, and it usually takes under half that.  My word using coleagues seem to need a day to format something.

both xfig and latex are from the days when a megabyte required a tape drive and so they are light weight and robust.

Aparently MSword has templates, but I have only seen one person using them correctly and he couldn't tell his student how it was done.

If only antiword produced pdf output, and there was a anti-powerpoint ...

Petr

---

