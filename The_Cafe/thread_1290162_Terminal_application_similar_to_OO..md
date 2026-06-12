---
title: "Terminal application similar to OO."
date: 2009-10-13
forum: The Cafe
---

### Post by dragos240 on 2009-10-13
Does anyone have an application that acts like openoffice, you know, can open .doc, can open other formats. Of course, I could learn XML and stuff, but.... are there any word processors for the humble terminal?

---

### Post by dominiquec on 2009-10-13
For word processing on the command line, I normally go with joe or pico / nano.  

Since DOC formats have plenty of WYSIWYG markup, I'm not sure how well they translate in the terminal.

---

### Post by anaconda on 2009-10-13
I think there is a terminal program, that can convert a .doc file to .txt file.

Then that .txt file could be edited with any text editor.

But you would lose all formatting.

---

### Post by K.Mandla on 2009-10-13
You have a couple of options. The best is probably Wordgrinder. 

[http://wordgrinder.sourceforge.net](http://wordgrinder.sourceforge.net)

Wordgrinder behaves like a word processor and is a great tool for writing. There's a package in the repos.

I don't think it necessarily will convert from .doc files, but antiword will translate to txt, which Wordgrinder can handle.

You can also arrange both emacs and vim to do word wrapping, which in my book makes them almost as good as word processors. 

[http://kmandla.wordpress.com/2009/07/27/proper-word-wrapping-in-vim](http://kmandla.wordpress.com/2009/07/27/proper-word-wrapping-in-vim)
[http://kmandla.wordpress.com/2009/02/17/still-looking-for/](http://kmandla.wordpress.com/2009/02/17/still-looking-for/)

Depending on which you prefer, you can set either up to at least perform in a fashion similar to a word processor. By the way, I use vim with the wrapping settings for blogging through Charm.

---

### Post by matthew.ball on 2009-10-13
Could always look into LaTeX + Emacs.

---

### Post by Xbehave on 2009-10-13
WHY? a word processor is a graphical application, you make text look nice in a word processor, how can you do that without knowing what it actually looks like?

You may be able to get something, but if your serious about producing well formatted documents form the command line, then its probably worth it to learn latex and just use a text editor + latex. Then convert it to other formats using the relevant tools.

---

### Post by koleoptero on 2009-10-13
> **K.Mandla said:**
> You have a couple of options. The best is probably Wordgrinder. 

[http://wordgrinder.sourceforge.net](http://wordgrinder.sourceforge.net)

Wordgrinder behaves like a word processor and is a great tool for writing. There's a package in the repos.

I don't think it necessarily will convert from .doc files, but antiword will translate to txt, which Wordgrinder can handle.

You can also arrange both emacs and vim to do word wrapping, which in my book makes them almost as good as word processors. 

[http://kmandla.wordpress.com/2009/07/27/proper-word-wrapping-in-vim](http://kmandla.wordpress.com/2009/07/27/proper-word-wrapping-in-vim)
[http://kmandla.wordpress.com/2009/02/17/still-looking-for/](http://kmandla.wordpress.com/2009/02/17/still-looking-for/)

Depending on which you prefer, you can set either up to at least perform in a fashion similar to a word processor. By the way, I use vim with the wrapping settings for blogging through Charm.

You are a living encyclopedia for terminal apps! That wordgrinder looks very interesting. Thank you! :KS

---

### Post by p_quarles on 2009-10-13
> **Xbehave said:**
> WHY? a word processor is a graphical application, you make text look nice in a word processor, how can you do that without knowing what it actually looks like?

You may be able to get something, but if your serious about producing well formatted documents form the command line, then its probably worth it to learn latex and just use a text editor + latex. Then convert it to other formats using the relevant tools.
Word processors started out as text-based applications, without WYSIWYG functionality. Both Wordstar and Wordperfect were very successful applications from a business standpoint, though obviously the market for software was much, much smaller then than it is now.

---

### Post by hessiess on 2009-10-13
Use LaTeX, produces better looking typography anyway.

---

### Post by Xbehave on 2009-10-13
> **p_quarles said:**
> Word processors started out as text-based applications, without WYSIWYG functionality. Both Wordstar and Wordperfect were very successful applications from a business standpoint, though obviously the market for software was much, much smaller then than it is now.
But that was what passed for word processing back then, does using them now offers a significant advantage over just using a text editor? or better yet using latex?

---

### Post by ynnhoj on 2009-10-13
if you're up for learning a typesetting system, as others have mentioned LaTeX is nice. but if you're not interested in the big download, lout might be worth a try. it's easy to learn and has a good manual available, and much smaller than LaTeX. or you could use troff/groff.. they're probably on your system to begin with. (heirloom project's version of troff (or plan9's) would be a bit better though, i think.)

---

### Post by K.Mandla on 2009-10-15
> **koleoptero said:**
> You are a living encyclopedia for terminal apps! That wordgrinder looks very interesting. Thank you! :KS
You're welcome. You might also be interested in ...

[http://kmandla.wordpress.com/software#Terminal](http://kmandla.wordpress.com/software#Terminal)

There are quite a few other lists of console applications out there; keep your eyes open. :P

---

### Post by HNS-I on 2009-10-15
You can use rtf2latex to convert a .doc and you can use pdflatex to convert latex to pdf. I don't know if you are willing to learn a new markup but from experience I can tell you that latex can be very helpfull and make you more productive. It's advisable to get a book about it though.

---

