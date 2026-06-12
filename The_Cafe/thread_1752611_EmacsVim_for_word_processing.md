---
title: "Emacs/Vim for word processing?"
date: 2011-05-08
forum: The Cafe
---

### Post by krapp on 2011-05-08
Anybody use these super stable text editing programs for word processing?

---

### Post by Oxwivi on 2011-05-08
And here we go again...

---

### Post by krapp on 2011-05-08
Please note **word processing.** Not programming or whatever the self-identified partisans do. I'm not trying to start a flame war. I'm looking for an alternative to slow, crash-prone WYSIWYG word processing that is not strictly LaTeX, though I'd be open to emphatic recommendations to go in that direction.

---

### Post by NovaAesa on 2011-05-08
I used to use emacs/latex for word processing, I now use gedit/latex for word processing.

---

### Post by sanderd17 on 2011-05-08
I have tried vim/LaTeX, but for me, Kile/LaTeX works better. Kile has a basic vim-editing-mode if you need that. 

Kile is better in things like project management and keeping track of lables, references, chapters ...

---

### Post by Irihapeti on 2011-05-08
If you want something that is in between word processing and straight-out LaTeX-with-text-editor, you could try LyX. It's a front-end to LaTeX which, for basic documents anyway, doesn't need you to learn the commands.

I could see it being useful for a long, uncomplicated document such as a full-length book. I played with it for a while and still have it installed, but recently have ended up using LaTeX-with-text-editor.

Best way to decide if it's for you is to try it. It's in the repos.

---

### Post by FreeTheBee on 2011-05-08
I switched to Vim with the vim-latex plugin about 1.5 year ago, coming from Kile and Winedt(windows). The main reason was that I wanted a cross platform solution, so I did not need to use different editors at home and the office. I tried several but stuck with Vim. After learning how to use it is more efficient for me than any editor I used before. Emacs with auctex and preview-latex seems to be an excellent solution as well, but I really like the concept of a modal editor.

---

### Post by sanderd17 on 2011-05-08
> **FreeTheBee said:**
> I switched to Vim with the vim-latex plugin about 1.5 year ago, coming from Kile and Winedt(windows). The main reason was that I wanted a cross platform solution, so I did not need to use different editors at home and the office. I tried several but stuck with Vim. After learning how to use it is more efficient for me than any editor I used before. Emacs with auctex and preview-latex seems to be an excellent solution as well, but I really like the concept of a modal editor.

I know vim is better for typing, but how do you handle the references, projects or maybe even reverse search? I didn't try too long with vim, so maybe it's possible but I just didn't find it.

---

### Post by aG93IGRvIGkgdWJ1bnR1Pw== on 2011-05-08
You're using the "word processing == document" fallacy. It's text, there's no need to package it as a document file, be it .doc, .odt or .pdf. Using anything but plaintext for word processing is redundant.

That said, I use emacs for word processing, programming, note taking, reading news and email, browsing irc, doing rpn calculations, playing with my pet LISP projects, organising my workflow and reading books.

---

### Post by matthew.ball on 2011-05-08
Yeah, I use emacs with LaTeX.

I have never used AUCTeX - I just wrote my own elisp to do some of the functionality I wanted (which wasn't available in the default latex-mode). I'm not a programmer (if that makes any difference), but I found elisp pretty intuitive and easy to use.

Emacs with RefTeX is pretty amazing. I'm currently writing a thesis and it handles the bibliography (and navigation of over 300+ pages split into 9 files) very well.

Just like aG93IGRvIGkgdWJ1bnR1Pw==, I basically use emacs for everything these days; in particular email, note-taking and managing workflow and tasks.

---

### Post by FreeTheBee on 2011-05-08
The vim-latex plugin takes care of references and labels. Starting to write \cite{ and then hitting <F9> opens the list of references and <enter>, after selecting one, inserts it. The same works for \ref{..
A project can be setup by putting a projectname.latexmain file in the same folder as the projectname.tex file. Vimlatex will then call the master file for compilation, when compiling one of the subfiles. I tend to use single files with folding more often than projects though.
I have no idea if reverse search is possible, I've never looked for it.

The last stable release of vimlatex is quite old, but there are snapshots released fairly regularly. Synaptic seems to have one from last year.

[vim-latex.sourceforge.net]("http://vim-latex.sourceforge.net/")

---

### Post by Random_Dude on 2011-05-24
I normally use TexMakerX for LaTeX, but lately I've tried a bit of Emacs and Vim.
I must say that I'm very impressed with Vim for LaTeX. Most people seem to recommend Emacs for LaTeX but Vim has some cool features, especially the F9 key for completing citations and references. :D

Cheers :cool:

---

### Post by danbuter on 2011-05-24
> **Oxwivi said:**
> And here we go again...

Thanks for trolling!

For the OP, I think either emacs or vim would work fine. Do all your writing there, and then worry about formatting.

---

### Post by MBybee on 2011-05-24
I use a typewriter (seriously) for writing.
If I'm creating documentation for digital distribution, I use Vim/Gedit/Kate or Writely (Google Docs).

I seriously find that I can't write if there is too much going on, I'll obsess endlessly about fonts, formatting, etc.

---

### Post by Random_Dude on 2011-05-24
> **MBybee said:**
> I use a typewriter (seriously) for writing.

Typewriters are too bloated. I use a pen..

---

### Post by RiceMonster on 2011-05-24
I use echo to write my documents.

---

### Post by keithpeter on 2011-05-24
> **krapp said:**
> I'm looking for an alternative to slow, crash-prone WYSIWYG word processing that is not strictly LaTeX, though I'd be open to emphatic recommendations to go in that direction.

Others have provided the emphatic recommendations :)

I'll chuck pandoc into the mix. 

Any text editor you like together with a basic markup format (called 'markdown' but with pandoc extensions). Can output direct to html, rtf and odt for later messing about with, so one source document produces print or web.

PS: an Olivetti Lettra 22 comes in handy for earthing those flames :twisted:

Cheers

---

### Post by Irihapeti on 2011-05-24
> **Random_Dude said:**
> Typewriters are too bloated. I use a pen..

Why use that? What's wrong with the good old marble tablet and chisel? :)

---

### Post by handy on 2011-05-24
Cream gives vim the GUI touch for those that prefer to use a mouse to give commands.

---

### Post by Random_Dude on 2011-05-25
> **Irihapeti said:**
> Why use that? What's wrong with the good old marble tablet and chisel? :)

The chisel's keybindings cause carpal tunnel.


> **handy said:**
> Cream gives vim the GUI touch for those that prefer to use a mouse to give commands.

And also uses the more common keybindings: Ctrl-c, Ctrl-v, Ctrl-x, etc. 
It's a very cool program for anyone who wants to use vim commands but doesn't want to get used to change between modes.

Cheers :cool:

---

### Post by MBybee on 2011-05-25
> **Irihapeti said:**
> Why use that? What's wrong with the good old marble tablet and chisel? :)

Nah, that's too much like Pico 

:popcorn:

---

### Post by krapp on 2011-05-25
Thanks for the replies everyone! I can see the sense of using Vim for writing as the switching between modes is not unlike the rhythms of writing/editing. But Org-mode in Emacs for note-taking and outlining has me enthralled at the moment, so I may stick with Emacs for word processing more generally.

[QUOTE=^!&^%^67152781219==]You're using the "word processing == document" fallacy. It's text,  there's no need to package it as a document file, be it .doc, .odt or  .pdf. Using anything but plaintext for word processing is redundant.[/QUOTE]

:) It may be a fallacy but it's one of the more prominent and widely held assumptions of computing. At any rate, I'm on your side! I know it's a fallacy and seek to not reinforce it.

[QUOTE=keithpeter]Others have provided the emphatic recommendations :smile:

I'll chuck pandoc into the mix. 

Any text editor you like together with a basic markup format (called  'markdown' but with pandoc extensions). Can output direct to html, rtf  and odt for later messing about with, so one source document produces  print or web.[/QUOTE]

This sounds great, thanks. I'll definitely have a look as well.

---

### Post by idoitprone on 2011-05-26
> **Irihapeti said:**
> Why use that? What's wrong with the good old marble tablet and chisel? :)

its really expensive. Do you know how much marble cost these days. And chipping them is not any easier 
 As random_dude mentions
> **Random_Dude said:**
> The chisel's keybindings cause carpal tunnel.

I use bark and chisel. Easier accessible and semi durable

---

### Post by BrokenKingpin on 2011-05-26
Nope. I used VIM for all c++ development in college, but I wouldn't consider using it for word processing. For my word processing needs I always turn to LibreOffice.

---

### Post by lykwydchykyn on 2011-05-26
I write documents in Emacs using RST (ReStructuredText) markup.  There's a moderately decent RST mode out there for Emacs, as well as a collection of snippets if you use yasnippet.

I tried to learn Latex but it seemed to verbose and overkill for my purposes.  I wanted something that was easy to type (no.angle.brackets!!!!), stayed out of the way, but still let me define structure for my document. It came down to markdown or RST, and I went with RST because it had a few things markdown lacked.

---

