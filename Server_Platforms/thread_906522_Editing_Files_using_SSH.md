---
title: "Editing Files using SSH"
date: 2008-08-31
forum: Server Platforms
---

### Post by unsoc on 2008-08-31
I have installed the vi test editor and when I try to edit files using SSH  the only thing I see in the files at the beginning of each line is ~

Is there a way to correct this or a better text editor for SSH?

Thank You

---

### Post by tubezninja on 2008-08-31
Yeah, that's vi.  People who've learned it swear by it.  Others can barely comprehend it. :)

You may want to start out with nano as your text editor and work your way up to vi.

```
sudo apt-get install nano
```

Nano is about as simple as it gets.

EDIT: There's also emacs, which is somewhat more complex.

---

### Post by Oldsoldier2003 on 2008-08-31
> **scaredpoet said:**
> Yeah, that's vi.  People who've learned it swear by it.  Others can barely comprehend it. :)

You may want to start out with nano as your text editor and work your way up to vi.

```
sudo apt-get install nano
```

Nano is about as simple as it gets.

EDIT: There's also emacs, which is somewhat more complex.

+1 for simple file editing I always suggest nano. More experienced users may prefer emacs or vi/vim, but its hard to go wrong with nano.

---

### Post by inphektion on 2008-08-31
vi is simple if you know the commands... which is as easy as a google search.  Start out with the basics and anytime you want to do something like search and replace or edit 5 lines in a row with the same repeating pattern than google that and soon you'll pick up on more advanced commands.

---

### Post by unsoc on 2008-09-01
I haven't messed with commands in a few years. I have been using Xampp for all my home server needs and decided I wanted to expand my knowledge with servers. Being a Kubuntu user I figured what better server to try than Ubuntu Server.

Anyhow, I got nano installed and everything is working out well so far. Apache is up and running, Mysql is running and SSH. I've changed all the ports to make it a bit more secure. Now time to start reading some more.


Thanks for the help guys!

---

### Post by igb on 2008-09-02
I love Emacs, but it does have a steep learning curve. However, it does have one very useful mode called "tramp mode". This allows you to run your local copy of emacs, with all its customizations and edit files remote via ssh.

You can also run emacs remotely via an ssh terminal if you wish.

Ian.

---

