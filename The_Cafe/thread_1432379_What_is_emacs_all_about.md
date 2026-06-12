---
title: "What is emacs all about?"
date: 2010-03-17
forum: The Cafe
---

### Post by dragos240 on 2010-03-17
From what I know, it was originally made by RMS, and that it is a text editor, but not much else. What's so good about it?

---

### Post by undecim on 2010-03-17
Topics about religion are not allowed in the Community Cafe.

---

### Post by Phrea on 2010-03-17
> **undecim said:**
> Topics about religion are not allowed in the Community Cafe.

:popcorn:

---

### Post by dragos240 on 2010-03-17
> **undecim said:**
> Topics about religion are not allowed in the Community Cafe.

Lol. I've heard it's more than just a text editor, and I wanted to know exactly what it was.

---

### Post by Name change on 2010-03-17
Just an idea: install it read man and see for yourself...
AFAIK it's a editor which uses weird keyboard combos to do anything, and I mean anything.

---

### Post by skierkyles on 2010-03-17
> **undecim said:**
> Topics about religion are not allowed in the Community Cafe.

Thank you, I just spit all over my monitor I laughed so hard :D

---

### Post by Sam on 2010-03-17
[[IMG]http://imgs.xkcd.com/comics/real_programmers.png[/IMG]](http://xkcd.com/378/)

---

### Post by Tibuda on 2010-03-17
Alt+x
term
vim

and you are fine.

---

### Post by Oldskool Slacker on 2010-03-17
> **Primož Papi&#269 said:**
> ... weird keyboard combos ...

Hence the nickname "Esc-Meta-Alt-Ctrl-Shift" ;)

---

### Post by JDShu on 2010-03-17
> **undecim said:**
> Topics about religion are not allowed in the Community Cafe.

I actually LOL'd IRL.

---

### Post by kevCast on 2010-03-17
"GNU Emacs is an extensible, customizable text editor—and more. At its core is an interpreter for Emacs Lisp, a dialect of the Lisp programming language with extensions to support text editing."

[http://www.gnu.org/software/emacs/]("http://www.gnu.org/software/emacs/")

I use emacs, and I like it.

---

### Post by dragos240 on 2010-03-17
Hmm..... "has anyone here used it, and what do you think of it?" may have been a better question.

---

### Post by JDShu on 2010-03-17
In all seriousness, I use it and its pretty awesome.

---

### Post by kevCast on 2010-03-17
I actually wrote about this a little while back:

> I use two editors: ed and emacs. When I need a minimal editor, I use ed. When I need every feature under the sun, I use emacs.

I live in emacs. I play music, read mail, browse the web, get on irc, play tetris, and edit text. To vi/vim users, this sounds insanely stupid and convoluted.

However, doing this gives you a common environment. All of the programs in emacs are just elisp wrappers around various GNU tools: diff, grep, git, getmail, etc. I don't have to remember keybindings for vim, ncmpcpp, lynx, irssi, etc. All of my emacs keybindings work in erc. All of them work in emms. They all work when I edit text.

That, and emacs is incredibly portable. I can have the same setup on GNU/Linux, BSD, Windows, and MAC OSX. Because of it's low resource requirements in comparison to other software of the day, it's very light. Platforms are irrelevant. My computer is an emacs machine.

Emacs was made to be programmable from day one. Elisp is an incredibly powerful tool. You can bend emacs to your will with it. In contrast, vi was not meant to be added onto. Various Vim features are bolted on, and enabling too many plugins in Vim causes toe stepping between the various plugins.

Then there's all the editting features of emacs: major modes, minor modes, C-h i for all documentation, C-h t for the tutorial, macros, full unicode support, etc.

I've been happily using emacs, and I can't imagine computing without it. That being said, this is a subjective topic, but considering the vi/vim majority, I thought I'd add my two cents.

There's also the [EmacsWiki]("http://www.emacswiki.org/"), [http://emacs-fu.blogspot.com/]("http://emacs-fu.blogspot.com/"), [emacs subreddit]("http://www.reddit.com/r/emacs"), #emacs on freenode, etc.

---

### Post by DoktorSeven on 2010-03-17
"Emacs is a decent OS but its text editor is horrible."

:)

(Calm down, tongue planted firmly in cheek, Emacs is decent enough though I prefer the all-powerful vim!!!!!11one)

---

### Post by KiwiNZ on 2010-03-17
> **dragos240 said:**
> From what I know, it was originally made by RMS, and that it is a text editor, but not much else. What's so good about it?

They actually predate GNU Emacs by RMS. Called Teco at MIT . This was later developed into Emacs by RMS

---

### Post by MaxIBoy on 2010-03-17
It is wrong to think of Emacs as a text editor. It's a combination programming language (Emacs Lisp,) API, and toolkit. Together, the package forms a very robust framework for development of command-line or text-based applications, and it is intended essentially as a desktop environment. 

It comes with a few default applications, including some games (Dunnet, Tetris, Blackbox, Pong,) a terminal emulator, VCS frontends, a GDB frontend, a PDF/PostScript viewer, a Newsgroup reader, miscellaneous knick-knacks and utilities, and, of course, a plaintext editor. However, you can easily install more. In addition, you can modify the Emacs Lisp source code to any of these if you like. Actually, I think there are several different implementations of the Vi/Vim editors written as Emacs modes.

Historically, the original EMACS stood for "Editor Macros," and it was a package of customizations and macros for the horrible TECO editor (which practically turned it into a whole new editor.) These were gathered from a bunch of people who were at MIT, and collected into one package by RMS. Later on, when an editor was needed for the GNU project, Emacs was popular enough that it made sense to rewrite it as a standalone program. So that's what RMS did.

---

### Post by jpkotta on 2010-03-19
> **MaxIBoy said:**
> It is wrong to think of Emacs as a text editor. It's a combination programming language (Emacs Lisp,) API, and toolkit. Together, the package forms a very robust framework for development of command-line or text-based applications, and it is intended essentially as a desktop environment. 

Exactly, it's like editor toolkit.  

I like it because I see some feature that another editor has, and more often than not someone has implemented that feature in Emacs.  If there's something that almost works the way I want, it's relatively easy to figure out how to make it work completely how I want.  The main downside is that it's slow due to how much stuff I have running in the background.  But by default it's very fast.

---

### Post by kaldor on 2010-03-19
I prefer Vim by far. Emacs just feels overcomplicated for me; I don't use a CLI editor unless I am doing something like editing a configuration file on my server. I like the way Vim works. 

If I had a good reason to use a text editor extensively, I'd probably learn how to use Emacs.

---

### Post by unknownPoster on 2010-03-19
It is possible to install Emacs as an operating system, over a Linux kernel. 

[http://www.informatimago.com/linux/emacs-on-user-mode-linux.html](http://www.informatimago.com/linux/emacs-on-user-mode-linux.html)

However, I really only use it for the occasional times I play around with Lisp.

---

### Post by lykwydchykyn on 2010-03-20
> **MaxIBoy said:**
> It is wrong to think of Emacs as a text editor. It's a combination programming language (Emacs Lisp,) API, and toolkit. Together, the package forms a very robust framework for development of command-line or text-based applications, and it is intended essentially as a desktop environment. 

Couldn't have said it better.  Calling Emacs a text editor is like calling KDE a window manager.

Most IDEs have a text editor widget, possibly with bells and whistles like code completion, spellcheck, or whatnot, but otherwise it behaves the same no matter what you're editing.  Emacs buffers change their behavior depending on what you're editing.  You can load and unload different features depending on what you're working on.

I mostly edit python, php/html/css, or rich text documents in Emacs, but lately I'm figuring out org mode.  In a way Emacs reminds me of the early days of learning about Linux; lots of "oh wow, it can do that too? I gotta try that!" moments.  

I should point out, every Emacs thread on UF must contain the following, which this one has fortunately met:

 - the "Emacs is a great operating system..." joke
 - the XKCD about "real programmers use..."
 - One or more Vim users piping up about how great Vim is.

:D

---

### Post by juancarlospaco on 2010-03-20
*Emacs its a great operating system and can run inside Linux too.*

---

