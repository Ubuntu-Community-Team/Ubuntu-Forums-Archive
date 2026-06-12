---
title: "opensource tools for writers?"
date: 2008-04-23
forum: The Cafe
---

### Post by Piggah on 2008-04-23
Particularly college level.. 

I'm not looking for any tool in particular, just wondering if anyone has suggestions for any open source programs for writers. I know there have to be some writers on this board. :p

thanks

---

### Post by Kingsley on 2008-04-23
I'm guessing OO.o isn't what you had in mind...

---

### Post by delfick on 2008-04-23
OO.o is very powerful once you start extensively using styles.....

---

### Post by GMU_DodgyHodgy on 2008-04-23
Open Office is good and is a comprehensive office suite.  However AbiWord has become my favorite Word Processor.  It is elegant - fast and light and has almost all the features you will need.  

It is a very suite application.

---

### Post by Piggah on 2008-04-23
Yeah, I use AbiWord for my word processing. It's a lot quicker to load and easier on resources. The formatting options are more than enough for me atm. 

I'm basically looking for anything but a basic word processor..

---

### Post by SunnyRabbiera on 2008-04-23
Open office is the tool for you to be sure, you can even get a grammar check for it (though the one in MS office is still better as it supports more then just english)

---

### Post by mrgnash on 2008-04-23
> **Piggah said:**
> Yeah, I use AbiWord for my word processing. It's a lot quicker to load and easier on resources. The formatting options are more than enough for me atm. 

I'm basically looking for anything but a basic word processor..

LaTeX is THE tool for serious writing of any sort, but particularly academic writing. The easiest way to start with it is through something like Lyx, and then move on to Kile, Emacs, or use the Gedit LaTeX plugin.

---

### Post by SunnyRabbiera on 2008-04-23
Yeh though LaTeX is a bit old fashioned...

---

### Post by mrgnash on 2008-04-23
> **SunnyRabbiera said:**
> Yeh though LaTeX is a bit old fashioned...

If by old-fashioned you mean 'not familiar to those who are only used to doing things the MS Word way', then yeah it's 'old-fashioned.' But it's much like Linux itself, in that once you get over the initial learning curve, you find that the MS way ain't necessarily the best way, it's just the familiar way.

---

### Post by SunnyRabbiera on 2008-04-23
True, but I would not shove LaTeX on a newcommer.

---

### Post by Piggah on 2008-04-23
i'll try latex out i suppose :p

---

### Post by Iandefor on 2008-04-23
> **SunnyRabbiera said:**
> True, but I would not shove LaTeX on a newcommer.What's so difficult about LaTeX? It just needs a bit of openmindedness is all.

---

### Post by dada1958 on 2008-04-24
> **SunnyRabbiera said:**
> Yeh though LaTeX is a bit old fashioned...
But still unbeaten if you want superior text quality ...

---

### Post by SoulinEther on 2008-04-24
> **dada1958 said:**
> But still unbeaten if you want superior text quality ...

In order to progress this thread (and to satisfy my desire for more information :)), how is LaTeX better, in a nutshell?

I'll be pretty free this summer so maybe I would like to then give it a try.

---

### Post by dada1958 on 2008-04-24
> **SunnyRabbiera said:**
> True, but I would not shove LaTeX on a newcommer.
Why not? I've been a newcomer too. Installation of TexLive on Ubuntu is a breeze, it is in the repositories. So is rubber, so you can install the [Gedit LaTeX plug-in]("http://live.gnome.org/Gedit/LaTeXPlugin").
Get a copy of [The Not So Short Introduction to LaTeX 2&#949;]("http://tobi.oetiker.ch/lshort/lshort.pdf") and there you go :cool:

---

### Post by sloggerkhan on 2008-04-24
not sure what you meant by tools for writers...
Page layout, there's scribus.
However, I've seen some things in the repos that say stuff like "mindmapping" and such... maybe good for brainstorming?

---

### Post by dada1958 on 2008-04-24
> **SoulinEther said:**
> In order to progress this thread (and to satisfy my desire for more information :)), how is LaTeX better, in a nutshell?

I'll be pretty free this summer so maybe I would like to then give it a try.
Just have a look at [The Not So Short Introduction to LaTeX 2&#949;]("http://tobi.oetiker.ch/lshort/lshort.pdf"), it's written with LaTeX.

---

### Post by SoulinEther on 2008-04-24
> **dada1958 said:**
> Just have a look at [The Not So Short Introduction to LaTeX 2&#949;]("http://tobi.oetiker.ch/lshort/lshort.pdf"), it's written with LaTeX.

The name worries me, lengthwise, but I'll have a look. Thanks!

---

### Post by persofi on 2008-04-24
In my opinion for ,,normal" people, LaTeX is not better.
However if you are geeky enough to install Ubuntu (I mean it positive) then LaTeX is great.
It is like a programming language for word processing. You can tweak it to a point where it is totally brilliant.
For example:

1) You can use JabRef to get the information like title, edition, publisher etc... of certain books via university library websites and then automatically compile it for your paper as a literary reference.

2) If I need to make a footnote: "Miller in: Journal of American Law, P.334, §167", I simple type \fc[P.334, §167]{mill}
Then it is automatically put into the literary reference as well...
For a totally perfect looking Table of Contents 
A.bla,
  I.ble 
       1. bli
       2. blu
  II. blo
B. bla

I just need to type
\toc{bla}
\sub{ble}
\sub{bli}
\toc{blu}
\levelup
\toc{blo}
\levelup
\toc{bla}



3) You can give it rules like to always make a space hinter a . or , like
, test;  Or always make an .  at the end of a footnote. 
This doesnt sound impressive, but in my experience, every student has to adhere to some formal rules which he totally hates. With LaTeX you look at them once, write them into code, and never worry about them again.

4) It seems to have almost no bugs. I worked with it for 1,5 years and it never did anything it wasnt supposed to do. 

5) The content is totally seperated from the style. You can type only worrying about what you write, because you will deal with how it looks at a later date. Because it is compiled it is possible to do stuff that I do not believe to be possible in WYSIWYG editors. For example in my last 80 pages work, which had Parts A,B,C,D with various subparts etc... I decided that some parts under C would be better under B, and some of the parts in B would be better under D.
You need to understand, at this point the paper was complete with footnotes, formating, references, everything.

How long did it take me to implement these huge changes?
- 15 seconds, but only because I was eating a pizza while at it.

6) It just produces beautiful text. In my opinion, if you want to create such beautiful text in Word, OpenOffice etc... you would need to spend as much time learning it. However LaTeX has a great community, which you can always ask for help.

---

### Post by Dixon Bainbridge on 2008-04-24
The best writing app i've used is Scrivener. Unfortunately its Mac only at the moment which is a real shame. Its not free, but its very cheap and for serious writers, fiction and research, there is nothing better on any platform. A Scrivener alike for linux would be sweet.

---

### Post by SoulinEther on 2008-04-24
> **persofi said:**
> ..if you are geeky enough to install Ubuntu (I mean it positive) then LaTeX is great.
It is like a programming language for word processing. You can tweak it to a point where it is totally brilliant.


You had me at hello, hehe.

I started reading that book/booklet, and along with what you're discussing, it sounds really sweet, and something I had better look into getting familiar with for my college years right ahead of me.

---

### Post by SunnyRabbiera on 2008-04-24
> **dada1958 said:**
> Why not? I've been a newcomer too. Installation of TexLive on Ubuntu is a breeze, it is in the repositories. So is rubber, so you can install the [Gedit LaTeX plug-in]("http://live.gnome.org/Gedit/LaTeXPlugin").
Get a copy of [The Not So Short Introduction to LaTeX 2&#949;]("http://tobi.oetiker.ch/lshort/lshort.pdf") and there you go :cool:

well for one its primary format is not readable to MS office, sure you can export it to text but still I find it a bit quirky.
Plus LaTeX is a terminal app, newcommers would be a bit weirded out

---

### Post by urukrama on 2008-04-24
I do a lot of writing. Here are a few applications I find very useful:

[LIST]Notecase: a very handy app to keep your notes for a particular project organised. I use it extensively while writing.
[/LIST]
[LIST]
StarDict: A dictionary app. You can download several dictionaries from its website; a simple thesaurus is available.[/LIST]
[LIST]
Pybliographer: a bibliography app. I've only recently started using it (I used EndNote before that); this might become a keeper. It looks promising, though I have to give it a little more time.[/LIST]

For the actual writing, I use OpenOffice.

---

### Post by jw5801 on 2008-04-24
> **SunnyRabbiera said:**
> well for one its primary format is not readable to MS office, sure you can export it to text but still I find it a bit quirky.
Plus LaTeX is a terminal app, newcommers would be a bit weirded out

I use `texmaker' basically a text editor designed specifically for LaTeX, integrates shortcut keys to compile the document in either .dvi or .pdf. It's a really cool app, holds your hand a bit during that initial learning curve, and doesn't get in the way at all of more advanced users.

---

### Post by bailout on 2008-04-24
Never used it but saw this, although it isn't free.

[http://www.writerscafe.co.uk/](http://www.writerscafe.co.uk/)

---

### Post by amar on 2008-04-24
I wish I had heard about LaTeX before coming to uni (or even in first year) I learnt it over the cource of the last semester and am glad. If you have engineering/ math reports with lots of formula - this typsets them beutifuly.

I am able to keep up with my lecutrers writing notes on the board exept when they finnish, it gets rubbed off. When I finnish I have a textbook :)

as for command line - Not if you use lyx or kyle. 2 of my clasmates use lyx and love it, 'same as word but produces nicer reports' and I use kyle cos it suits my needs (i like seeing the code of what I have written - i'll look at the output later)

In both cases the command line is irrelevent

---

### Post by dada1958 on 2008-04-24
> **SunnyRabbiera said:**
> Plus LaTeX is a terminal app, newcommers would be a bit weirded out
Not with Gedit + LaTeX Plugin as front end editor :wink:

---

