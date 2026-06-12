---
title: "What is Latex?"
date: 2005-12-09
forum: The Cafe
---

### Post by Orporg on 2005-12-09
I know it has a funny way of writing it but I don't remember how.  I didn't know what thread to stick this in, so I figured here was as good as any.

I read about the Latex/Tex software on Wikipedia.  I saw a sample of the output and was impressed.  It looked extremely professional, just like a printed book.  I was thinking that would be a nifty way to distribute written materials, as it's always easy to see the difference between a document that was made in a word processor and that made with desktop publishing.

However, it looked like I'd have to learn an entirely new markup language which I'm not keen on doing.  Especially if I want to write a story or book or something.  In a word processor, all you have to do is just pound away on the keyboard with occasional reach for bold or italics.  With HTML, at least as long as it's done in a text editor, you have to pause to insert codes in constantly.  I think that disrupts the flow of the writing process.  So I like word processors for the input part but I think this TeX thing might be cool for output?

I was thinking an ideal situation would be a program that you lets you convert betweeen word processed documents and TeX.  Essentially, you do the writing in Word or Open Office or Appleworks or whatever and then you convert the look and layout into a more professional looking TeX document.  And it would be even better if there was a GUI based tool for editing the layout in a TeX document.  So you could use the mouse to move something here, change something there.  And, of course, get a look at the actual TeX code if you like.  I imagine font translation would be an enormous pain in the ass but I bet it could be done.

Does such software exist, especially on a GUI basis?  If not, is it technically possible?  Am I out of my mind?

---

### Post by [Rui] on 2005-12-09
Why don't you try lyx-qt?

apt-get install lyx-qt

---

### Post by ow50 on 2005-12-09
[QUOTE=Orporg]In a word processor, all you have to do is just pound away on the keyboard with occasional reach for bold or italics.  With HTML, at least as long as it's done in a text editor, you have to pause to insert codes in constantly.  I think that disrupts the flow of the writing process.[/quote]
If you're just writing a text book (no formulas, pictures, tables, etc.) you don't need to learn much markup. Depending on your text editor you might even get Control+I to insert the italic markup and so on. Either way, your fingers will never need to leave the keyboard. Much easier than with a word processor.

---

### Post by jrib on 2005-12-09
I think the best way is for you to try it for a couple of weeks.  You can't just try it once, because during your first couple of times you will feel unsure of how to do things and have to refer some kind of documentation (usually your intuition is correct though).  Try googling "The not so short guide to LaTeX" for a nice doc on LaTeX.  LaTeX is like anything else, it takes some getting used to.  But once you are used to it, the results will be well worth it.

And as ow50 said, if you are just typing text, it isn't going to require much markup.    Basically, instead of taking your hands off the keyboard in a word processor to do something you just type some simple markup-- this will be much faster and more efficient.  One thing you want have to do is make sure you center your title or format bibliographies manually.  LaTeX is going to do all the formatting for you.  If you suddenly want to use a different style, you just change the style package  (one word in your document) and the whole document is reformatted.  I don't know how many times I've said this in my short post already but... LaTeX is great :D

I use vim with vim-latexsuite.  There is also support in emacs if you prefer that.  I'm sure there are plenty more editors to try.  I've heard some good things about lyx too but haven't gotten around to trying it.

---

### Post by Orporg on 2005-12-09
I'm afraid I can't get packages right now, because my wireless card isn't cooperating with Ubuntu.  Some nice folks are trying to give me a hand with it but so far no dice.

I don't know much about the Latex markup language, but if it's like HTML don't you have to type something like <br> or <p> just to get new lines?  Maybe I'm too lazy, but just hitting "Return" seems faster and easier to me.  

I guess what I'm looking for is something that combines the ease of a word processor with the nifty output and layout of Latex/PDF/whatever.

Plus, isn't Latex an open standard?  I'm not an open source/free software fanatic but I've heard a little about the Opendoc format and I like the idea.  It's aggravating as hell to have to worry about whether the person you're sending a MS Word file to can open it or not.  Especially when Microsoft keeps changing the file format.  It plays hell with trying to get older programs and things for the Mac to open and edit stuff.  I like Word, but I'd prefer a platform/application independent file format.

---

### Post by benplaut on 2005-12-09
to me, it seems more confusing than a WYSIWYG word processor...

-Not a coder

---

### Post by jrib on 2005-12-09
[QUOTE=Orporg]I'm afraid I can't get packages right now, because my wireless card isn't cooperating with Ubuntu.  Some nice folks are trying to give me a hand with it but so far no dice.

I don't know much about the Latex markup language, but if it's like HTML don't you have to type something like <br> or <p> just to get new lines?  Maybe I'm too lazy, but just hitting "Return" seems faster and easier to me.  

I guess what I'm looking for is something that combines the ease of a word processor with the nifty output and layout of Latex/PDF/whatever.

Plus, isn't Latex an open standard?  I'm not an open source/free software fanatic but I've heard a little about the Opendoc format and I like the idea.  It's aggravating as hell to have to worry about whether the person you're sending a MS Word file to can open it or not.  Especially when Microsoft keeps changing the file format.  It plays hell with trying to get older programs and things for the Mac to open and edit stuff.  I like Word, but I'd prefer a platform/application independent file format.[/QUOTE]

if you want to start a new paragraph you just press enter twice (so you get blank lines seperating paragraphs in your .tex file).  No <br /> required :)

---

### Post by majikstreet on 2005-12-09
[QUOTE=benplaut]to me, it seems more confusing than a WYSIWYG word processor...

-Not a coder[/QUOTE]
yeah..

---

### Post by ow50 on 2005-12-09
Here's an example of a simple LaTeX file
```
\documentclass[a4paper,oneside,12pt]{article}

\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[english]{babel}

\begin{document}

I'm afraid I can't get packages right now, because my wireless card isn't
cooperating with Ubuntu. Some nice folks are trying to give me a hand with it
but so far no dice.

I don't know much about the Latex markup language, but if it's like HTML don't
you have to type something like <br> or <p> just to get new lines? Maybe I'm
too lazy, but just hitting ``Return'' seems faster and easier to me.

I guess what I'm looking for is something that combines the ease of a word
processor with the nifty output and layout of Latex/PDF/whatever.

Plus, isn't Latex an open standard? I'm not an open source/free software
fanatic but I've heard a little about the Opendoc format and I like the idea.
It's aggravating as hell to have to worry about whether the person you're
sending a MS Word file to can open it or not. Especially when Microsoft keeps
changing the file format. It plays hell with trying to get older programs and
things for the Mac to open and edit stuff. I like Word, but I'd prefer a
platform/application independent file format.

\end{document}

```

Note that the only change to the text required was that the normal quotation mark is an inch mark in LaTeX, thus the `` and ´´ for fancy left and right quotes.

---

### Post by poptones on 2005-12-09
Orporg, how old are you? If you are young enough to be entering college I think you would benefit from learning latex if it is your goal to enter a technical field. I have a few friends who are academics and they use latex daily in their publications. latex is one of the oldest markup languages (I can remember seeing ads for tex tools in Dr Dobb's at least two decades ago - back when most home computers were still 8 bit!). 

Familiarity with this tool would be an asset for any young person.

---

### Post by Lux Perpetua on 2005-12-09
[QUOTE=Orporg]I guess what I'm looking for is something that combines the ease of a word processor with the nifty output and layout of Latex/PDF/whatever.[/quote]Sounds like you're looking for lyx (see first reply to your topic). 
[quote=Orporg]
Plus, isn't Latex an open standard?  I'm not an open source/free software fanatic but I've heard a little about the Opendoc format and I like the idea.  It's aggravating as hell to have to worry about whether the person you're sending a MS Word file to can open it or not.  Especially when Microsoft keeps changing the file format.  It plays hell with trying to get older programs and things for the Mac to open and edit stuff.  I like Word, but I'd prefer a platform/application independent file format.[/QUOTE]Yes, LaTeX and TeX are both open standards and are documented completely.

---

### Post by Orporg on 2005-12-09
I just graduated.  And I'm not going into a technical field.  Far from it, in fact.  I imagine I'll never publish a paper in an academic journal in my life.  I like computer stuff but I'm not a programmer nor do I want to be one.

However, LaTeX sounds like an interesting thingamajig and if I ever end up wanting to publish something (extremely doubtful) I'd like to have the quality that it creates.  My only concern would be with the size of the files it generates.  PDF files look nice but they are huge and all sorts of zooming in and out is required to get anything readable.  

What is Lyx?  Can someone give me a description of it?

---

### Post by silent82 on 2005-12-12
How about Gnu TeXmacs?

apt-get install texmacs

---

### Post by akniss on 2005-12-12
[http://www.ubuntuforums.org/showthread.php?t=98120](http://www.ubuntuforums.org/showthread.php?t=98120)

This thread has some discussion about advantages and disadvantages of TeX vs Word Processing.  May be beneficial.

---

