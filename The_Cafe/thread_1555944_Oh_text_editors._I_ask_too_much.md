---
title: "Oh text editors. I ask too much"
date: 2010-08-18
forum: The Cafe
---

### Post by ghostandmachine on 2010-08-18
I'm looking at text editors. I know there are a ton of choices and I've tried about 60% of them. I'm a writer: short stories, novels, poetry. etc. And I'm looking for something that'll be lightweight (console) but still get the job done.

Basically what I'm looking for is a console editor with "writer"-like features. Such as: word count, word wrap, placing headers and footers, spell check. Printing line numbers would also be nice but I'm not picky.

Any ideas? or am I stuck with bloated gui editors with tons of features I'll never use?

Thanks in advance

---

### Post by Austin25 on 2010-08-18
It's gui, but it isn't very bloated: abiword. The most powerful cli editor I know is emacs.

---

### Post by TriBlox6432 on 2010-08-18
Vim

---

### Post by Zorgoth on 2010-08-18
If you are looking for a console text editor, emacs is probably the most powerful, and is light, extensible, customizable, and probably given any common command you want to perform you can do using nothing but a few keystrokes.  Search and replace is so easy that I often use search even for navigating within one line.  However, emacs has a learning curve, probably of 2 weeks to a month of frequent use.

Nano is probably the easiest editor, but is not as powerful as emacs.

And vi is for if you are brain-damaged :P

---

### Post by Zorgoth on 2010-08-18
Here is an emacs how-to, courtesy of me:

[http://ubuntuforums.org/showthread.php?t=1542042](http://ubuntuforums.org/showthread.php?t=1542042)

Note: You can run emacs in a console with emacs -nw.

It is theoretically lighter, but you probably won't notice the difference.  Either emacs will be much faster than you are.  I would recommend the X version of emacs because you can select with the mouse and middle click to paste, and other handy things like that.  Although as a writer that particular trick might be less useful than as a programmer.

---

### Post by Queue29 on 2010-08-18
> **ghostandmachine said:**
> 

Basically what I'm looking for is a console editor with "writer"-like features. Such as: word count, word wrap, placing headers and footers, spell check. Printing line numbers would also be nice but I'm not picky.

Any ideas? or am I stuck with bloated gui editors with tons of features I'll never use?

Thanks in advance


I'm not sure how you're going to make stuff like headers and footers, fonts, and all that "bloated stuff" work without a GUI.

---

### Post by Zorgoth on 2010-08-18
> **Queue29 said:**
> I'm not sure how you're going to make stuff like headers and footers, fonts, and all that "bloated stuff" work without a GUI.

Fonts will not work in a console, period.  'tis truth - but a fullscreen gui emacs is basically just a version of console emacs allowing mouse interaction, and you can fullscreen it and split it into frames.  You can still control it completely from the keyboard if you wish.

Now I don't know how emacs will handle all those word processing features you are talking about.  Fonts you can certainly get, although the way I do fonts is LaTeX, which is probably not what you want.  Headers, footers, spell-check - those features probably exist, but my guess is you would have to scrounge the web for them.

I would probably really recommend a word processor over a text editor if you want word processor functionality, come to think of it.  Abiword was previously suggested and is good.

---

### Post by Queue29 on 2010-08-18
I guess he could just go all in and use LaTeX, but a full install of all the tools to make that work is in the neighborhood of 600 MB, so you may as well just use abiword.

---

### Post by p.s. on 2010-08-18
This prob isn't what you're looking for, and who knows who'll jump on me because it's not console or not emacs or etc, but after doing a lot of searching for the "perfect" text editor for actual writing I found that the answer for me is actually openoffice.

After tweaking a little bit so it wasn't so gd slow (and getting rid of every feature that I don't use for editing purposes) I just write in full screen with nothing else there, and then switch back to standard view for editing.

---

### Post by Zorgoth on 2010-08-18
Except that no matter how many tools you add onto it, emacs will always be faster than Abiword.  I don't know too much about Abiword so I don't know how keyboard-driven you can make it, but emacs will certainly be more keyboard-driven, if that is what the OP wants.

However, LaTeX is really designed for mathematical and scientific papers, so while it will support all his headers and footers and fonts (and maybe even spell-check - I don't know about that one, but certainly emacs could do it if someone programmed it), it might not be the ideal way to do it.

---

### Post by Tibuda on 2010-08-18
> **Austin25 said:**
> The most powerful [s]cli editor[/s] **operating system** I know is emacs.
> **Austin25 said:**
> The most powerful cli editor I know is [s]emacs[/s] **vim**.
:)

---

### Post by juancarlospaco on 2010-08-18
**[size="5"]ed[/size]**

---

### Post by blur xc on 2010-08-18
> **Zorgoth said:**
> And vi is for if you are brain-damaged :P

That's why we use vim...  

vim is also highly customizable - I've got mine set up as a python ide, which also works pretty well for bash scripts.  I'm sure if you googled it you'd find ways to customize it to be a good writing tool.

I tried emacs, and it's just overwhelming for a text editor, just does way too much, and found vim to be easier to learn.

BM

edit: googled it- [http://www.google.com/search?client=ubuntu&channel=fs&q=using+vim+as+a+word+processor&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=using+vim+as+a+word+processor&ie=utf-8&oe=utf-8)

---

### Post by matthew.ball on 2010-08-18
I'm a philosophy student who writes a lot of essays. I have a relatively severe case of OCD, and my main problem with GNU/Linux GUI software is a lack of consistency in appearance (yes, I am that specific), so I'll basically forfeit using any GUI tools if I can find an equivalent at the CLI-level. So far, I have found everything I need.

I use emacs23-nox with texLive for writing, and type-setting my documents. I've actually received a number of comments from my philosophy lecturers in regards to how professional it appears - I have even had one ask me to typeset his lecture notes for a course!

Everything you're after is available with emacs and a LaTeX distribution (word count is achieved by executing a shell command over a selected area of text [i.e. [FONT="Courier New"]wc -w[/FONT]], spell-check is achieved through an emacs LaTeX mode, and obviously LaTeX will prepare documents accordingly). If you're interested, send me an email and I can take you through what you need to know.

---

### Post by Legendary_Bibo on 2010-08-18
> **Queue29 said:**
> I guess he could just go all in and use LaTeX, but a full install of all the tools to make that work is in the neighborhood of 600 MB, so you may as well just use abiword.

How is that bloat? That's just space on his hard drive. Unless you're using a computer from beyond the last decade, there is no such thing as a bloated text editor.

---

### Post by Legendary_Bibo on 2010-08-18
> **blur xc said:**
> That's why we use vim...  

vim is also highly customizable - I've got mine set up as a python ide, which also works pretty well for bash scripts.  I'm sure if you googled it you'd find ways to customize it to be a good writing tool.

I tried emacs, and it's just overwhelming for a text editor, just does way too much, and found vim to be easier to learn.

BM

edit: googled it- [http://www.google.com/search?client=ubuntu&channel=fs&q=using+vim+as+a+word+processor&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=using+vim+as+a+word+processor&ie=utf-8&oe=utf-8)

I only use emacs to play tetris. :D

---

### Post by Zorgoth on 2010-08-18
Learning emacs is just hitting <tab><tab> a lot.

And after you run the command, it will often tell you the keyboard shortcut.

---

### Post by Zorgoth on 2010-08-18
A major benefit of using emacs in X rather than vim in CLI is that you can actually use in as a WYSIWYG word processor if you are writing in LaTeX, because it is capable of rendering the LaTeX as you type it using auctex/preview-latex.  A terminal is incapable of that kind of graphics.

---

