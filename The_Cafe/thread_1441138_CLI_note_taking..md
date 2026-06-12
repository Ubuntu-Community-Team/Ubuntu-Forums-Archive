---
title: "CLI note taking."
date: 2010-03-28
forum: The Cafe
---

### Post by km0r3 on 2010-03-28
Hey guys,

I'm quite living in my terminal, so I decided making notes, maybe mostly short, 1-2 lines, notes a day to write things down.

Does anyone from you does that? If yes, how and what do you use?

A friend of mine actually just creates an alias `memo` for his notes, which is just a file called *memo* in his $HOME, which he edits with Vim. He appends all his notes to the bottom; like that:
```
memo() { ${EDITOR:-vim} ~/memo "$@"; }
```

*Now, I like that idea*, but I think that gets quite messy when you do that for years. OK, maybe you could give each note tags/keywords and find them this way as Vim's RE find quite everything I can imagine myself.

But maybe you know any better approach?

---

### Post by Psumi on 2010-03-28
I'd use nano instead of vim for note taking to be honest.

vim is too... how do I put it... slow for me. I want my text to appear as soon as I start typing when the program comes up.

I also used to have a terminal-only computer just for note taking. It was a Zenith 386, had dos on it.

I saved files for each class session in the documents folder, and that was that.

---

### Post by Xbehave on 2010-03-28
```
cat > notes/$subject
```

I keep all my notes in separate files in my notes dir

read__:  cat notes/$subject
append:  cat >> notes/$subject
edit__:  nano notes/$subject
delete:  rm notes/$subject

---

### Post by rabidbadger on 2010-03-28
You can find a few ideas [in this post]("http://kmandla.wordpress.com/2009/11/10/tnote-simple-is-good/"), and the responses. Disclaimer: I don't use any of the suggestions ;-)

---

### Post by kevCast on 2010-03-28
[http://orgmode.org/](http://orgmode.org/)

One of the things that brought me to emacs.

---

### Post by mobilediesel on 2010-03-28
I use [todo.txt]("http://ginatrapani.github.com/todo.txt-cli/"). It's set up primarily to be a todo list management tool but it works for quick notes. You can tag entries with different context or project tags for quickly searching for just the note(s) you want.

It's written in bash and is known to run on Linux, OSX and Cygwin in Windows.

---

### Post by jomiolto on 2010-03-28
Personally I just use a text editor with a bunch of files (quite a lot of files actually), but I've also used [hnb]("http://hnb.sourceforge.net/") in the past and I thought it was a nice little program for short notes. It allows you to organize the notes in simple hierarchies.

---

### Post by km0r3 on 2010-03-28
I've noted that most of you just pointed me to To-Do applications.
I don't like most of them; some of them just appear to be crap.
That's not quite what I wanted.

Maybe I was just unclear; I want to keep notes, short notes. Like things I want to recall in 20 years (for example), sort of a diary and a blog and a notebook.

The simpler the better.

An interesting approach was [tnote]("http://tnote.sourceforge.net/"). This looks simple and does just what it has to do.

Thanks for all the answers and I look forward to hear some other responses! :)

EDIT:
Nano is definitely no alternative for me. I simply prefer Vim, having actually tried/used Emacs and Nano (and jedit). There are not a lot of better (if any) alternatives in my humble opinion.

---

### Post by K.Mandla on 2010-03-28
> **rabidbadger said:**
> You can find a few ideas [in this post]("http://kmandla.wordpress.com/2009/11/10/tnote-simple-is-good/"), and the responses. Disclaimer: I don't use any of the suggestions ;-)
There are some more at [http://kmandla.wordpress.com/2010/01/02/task-managers-for-the-console/](http://kmandla.wordpress.com/2010/01/02/task-managers-for-the-console/)

I use [hnb]("http://kmandla.wordpress.com/software#hnb") and [wyrd]("http://kmandla.wordpress.com/software#wyrd") on a daily basis; beyond that something like vimwiki is useful. One day I'll get around to converting [doneyet]("http://code.google.com/p/doneyet/") to Crux. That could be very useful for large, complicated projects. ...

---

### Post by km0r3 on 2010-03-28
> **K.Mandla said:**
> There are some more at [http://kmandla.wordpress.com/2010/01/02/task-managers-for-the-console/](http://kmandla.wordpress.com/2010/01/02/task-managers-for-the-console/)

I use [hnb]("http://kmandla.wordpress.com/software#hnb") and [wyrd]("http://kmandla.wordpress.com/software#wyrd") on a daily basis; beyond that something like vimwiki is useful. One day I'll get around to converting [doneyet]("http://code.google.com/p/doneyet/") to Crux. That could be very useful for large, complicated projects. ...

vimwiki looks really great! That's *not exactly* what I searched for, but it's really cool.

Also hnb looks quite good.

Thanks for your reply

---

### Post by sgosnell on 2010-03-28
What's wrong with Tomboy?  It's always there, searchable, and handy.  Works for me, but you're not me.

---

