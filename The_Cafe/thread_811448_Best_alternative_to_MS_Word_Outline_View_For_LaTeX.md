---
title: "Best alternative to MS Word Outline View? For LaTeX?"
date: 2008-05-29
forum: The Cafe
---

### Post by Mander on 2008-05-29
I'm in the process of switching from Word 03 on XP to LaTeX on Ubuntu for my PhD thesis.  So far so good, but I really miss some of the features of Word's Outline View, specifically two things:

- automatic folding of different heading levels (e.g. section, subsection, paragraph in LaTeX) by clicking on the plus/minus sign, or selecting the level of detail you wish to view in the view menu or toolbar

- the ability to automatically select an entire section or sub-section by clicking on the appropriate place in the document map or selecting a folded section, and dragging it to a new location.  

As far as I can tell, nothing I have tried so far will do this (Kile, LyX, OpenOffice, TeXMaker, Emacs with AUCTeX). Is there another program that I should try, or something that I'm missing?

---

### Post by dvase on 2008-05-30
> **Mander said:**
> 
- the ability to automatically select an entire section or sub-section by clicking on the appropriate place in the document map or selecting a folded section, and dragging it to a new location.  


This functionality is on the [Kile wishlist ]("http://bugs.kde.org/show_bug.cgi?id=60305").  Its status is "assigned", however it is also quite old.  You could vote for it at the above link and maybe encourage the developers to give it a higher priority.

---

### Post by bufsabre666 on 2008-05-30
office 2003 works pretty much perfectly under wine

---

### Post by vrangforestillinger on 2008-05-30
I thought this worked in TeXMakers structure-toolbox. But you are right, it doesn't. It would have been a good feature. 

But: I know the programming IDE Eclipse has these features. Eclipse was originally intended for Java, but there are now numerous plugins for other languages. Including LaTeX: [texlipse]("http://texlipse.sourceforge.net/"). I haven't tried this plugin myself though, but it might be worth checking out.

Eclipse is in the repos, there are install instructions on the texlipse-site.

> **bufsabre666 said:**
> office 2003 works pretty much perfectly under wine

But would one really want to write a PhD in Word? In LaTeX, one can focus on content and structure, letting the "professionals" (the LaTeX-compiler) take care of the layout.


BTW: There is an Education & Science-forum (edit: a section in Ubuntuforums) for these kind of questions.

---

### Post by Mander on 2008-06-06
Hey, thanks for the tip.  I'll check it out.

The main reason why I don't want to use Word anymore is because of its uncanny ability to crash and/or start doing weird things at critical moments, like right before a deadline.  I like the ability to easily customize things in Word, but I'm getting used to LaTeX.

---

### Post by hugmenot on 2008-06-06
You could do all that when editing in Vim (code folding of sections and figures, fold levels, yank+put of folded sections). But Vim is the opposite of a GUI tool.

---

### Post by vrangforestillinger on 2008-06-06
> **Mander said:**
> 
The main reason why I don't want to use Word anymore is because of its uncanny ability to crash and/or start doing weird things at critical moments, like right before a deadline.

Jupp, I remember the days when I used Word/OpenOffice under Windows 9x, constantly saving after every sentence after some very bad experiences.

> I like the ability to easily customize things in Word, but I'm getting used to LaTeX.

Ah, LaTeX: Its like moving in with your girlfriend. You can tell you want this over there, but LaTeX ultimately decides where the figure should go..

> **hugmenot said:**
> You could do all that when editing in Vim.

Oh. I did not know that. But Im somehow not surprised...

:wq

---

