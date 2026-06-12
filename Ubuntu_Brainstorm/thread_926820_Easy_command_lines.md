---
title: "Easy command lines"
date: 2008-09-22
forum: Ubuntu Brainstorm
---

### Post by Bablefish on 2008-09-22
I speak for every novice person here when I say this. Somewhere in the vast database Ubuntu seems to have there has got to be a directory of command lines, and I include those to get this program or that. Why can't copy come with the OS?  Just check out the forum and see how many people are looking to get this program or that.

---

### Post by cdenley on 2008-09-22
> **Bablefish said:**
> I speak for every novice person here when I say this. Somewhere in the vast database Ubuntu seems to have there has got to be a directory of command lines, and I include those to get this program or that. Why can't copy come with the OS?  Just check out the forum and see how many people are looking to get this program or that.

Are you saying that ubuntu should come with a database which matches commands to packages? It does. It's called "command-not-found". When you try to run a command which isn't installed but is listed in the database, you get a message like
> 
The program 'mycommand' is currently not installed.  You can install it by typing:
sudo apt-get install mypackage

> 
Why can't copy come with the OS?

What's "copy"? Are you looking for the command to copy files?
```

man cp

```

---

### Post by Bablefish on 2008-09-22
What I mean is an actual list you can copy and paste from and get what you need

---

### Post by lukjad on 2008-09-22
Well, that is somewhat impractical. There are thousands of commands that each have a slight variation. If you want to learn what a command does there is:
```
man [command]
```
that really shows you how to run a program or command and what it does. Is this what you were looking for?

---

### Post by Whiffle on 2008-09-22
Not to mention, a list of copy and paste commands would do nobody a favor when it comes to learning whats going on. Running commands you don't understand is the fastest way to screw something up.

---

### Post by lukjad on 2008-09-22
> **Whiffle said:**
> Not to mention, a list of copy and paste commands would do nobody a favor when it comes to learning whats going on. Running commands you don't understand is the fastest way to screw something up.
+1
True.

---

### Post by snova on 2008-09-22
I can see the value in this for some things. A number of things can only be done from the command line, and if the syntax for doing so is not particularly evident, a reference would be handy. As for simply pointing people to the man page, those aren't always very clear, and many are very long.

But not for everything. Reserve this for more complicated things; there's little point in adding an entry for every little program, as it would get to unmanageable size quickly.

Not to mention the risks- if this were editable Wiki-style, it would be far too easy to add something malicious to the list. "Run this as an administrator to configure your graphics card"...

---

### Post by wildman4god on 2008-09-30
I stumbled upon a website yesterday that has a complete list of bash commands and their usage and definitions, I like it because the man (command) command is no good when you don't know the command in the first place, I like to look it up in a list. I don't have the site off hand but I will try and find it again for you.

---

### Post by lukjad on 2008-09-30
That would be very useful.

---

### Post by Caremon on 2008-09-30
i useally use apropos command if i dont now the exactly command. Like this:

```
caremon@salmiakki:~$ apropos samba
Crypt::SmbHash (3pm) - Perl-only implementation of lanman and nt md4 hash functions, for use in Samba style smbpasswd entries
cupsaddsmb (8)       - export printers to samba for windows clients
lmhosts (5)          - The Samba NetBIOS hosts file

```

When i did start to use linux i google "usesual command" and found good list of commands.

---

### Post by wildman4god on 2008-10-01
[http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)
this is a site that teaches the linux commands.
[http://www.ss64.com/bash/](http://www.ss64.com/bash/)
this is a a-z index of commands and what they do.

Enjoy.:D

---

### Post by lukjad on 2008-10-01
Thanks! I'm adding this to my list of useful links.

---

### Post by MilesTeg on 2008-10-03
I still think "google this, google that"  is the wrong direction.

Such tutorials and infos should be at the fingertips of every new user (=integrated in the distro). How should someone google a command when he's trying to fix his network connection?

---

### Post by lukjad on 2008-10-03
Not that I think saying Google This is a good approach, but:
Network command fix
May do the trick.

---

### Post by lukjad on 2008-10-03
Not that I think saying Google This is a good approach, but:
Network command fix
May do the trick.

---

### Post by Whiffle on 2008-10-03
> **MilesTeg said:**
> I still think "google this, google that"  is the wrong direction.

Such tutorials and infos should be at the fingertips of every new user (=integrated in the distro). How should someone google a command when he's trying to fix his network connection?

I suggest it because thats how I learned it.  For me, having everything laid out for me does nothing for me learning what to use.  I have to think about it if I'm going to learn anything, and googling and then studying what commands do does that.

---

### Post by cdenley on 2008-10-03
I would prefer developers work on creating tools to help me do things easier than creating and maintaining guides to do the same task a more difficult way. Anything you write a guide for, you can also write a script to automate.

If someone is having problems using their internet connection, you don't improve the OS by including a better manual for commands you can use to fix it, you fix the network configuration tool so the user doesn't need commands.

---

### Post by cardinals_fan on 2008-10-03
> **Whiffle said:**
> I suggest it because thats how I learned it.  For me, having everything laid out for me does nothing for me learning what to use.  I have to think about it if I'm going to learn anything, and googling and then studying what commands do does that.
+1

I very rarely post support requests on almost any forum.  I prefer to solve problems myself and learn.

---

### Post by tomsa on 2008-10-08
I have to disagree about "google it" always being the right direction.  The reason I say so is that my laptop carries the dreaded RTL8187b wireless card, which has been sketchy at best, and has improved as I've learned more, and should no longer be an issue as 8.10 autoetects it for me.  "Googling it"  only works when you have a working internet connection.  I made my own reference materials for when I didn't have internet available- but not everyone will think of that before it's too late (I didn't think of it until after it happened once).  Another good thing to have is a command line based browser in case X breaks and you have no GUI so you can still "google it" (been there too) if you have internet.  These things have saved my butt a few times, and only become more useful once you learn to use man, apropos, and --help.  Making it easier for end users is always better, even if the end user is the occasional n00b.

---

### Post by kdorf on 2008-10-09
> **tomsa said:**
> I have to disagree about "google it" always being the right direction.

You must've missed the earlier post in the thread that mentioned "apropos" (I use man -k as it's easier to remember and does the same thing).

---

