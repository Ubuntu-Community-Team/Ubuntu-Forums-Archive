---
title: "The first thing a new user should see when Ubuntu boots"
date: 2009-09-23
forum: The Cafe
---

### Post by ade234uk on 2009-09-23
Should there be a small welcome screen for new users.
The welcome screen runs through a small list of recommendations

How do I install codecs
How do I install flash
How do I activate video card
Where are my documents stored
How do I burn CDs

Just something really basic but gets to the point.

I am probably going over old ground here, but when a new user boots ubuntu for the first time, what is the first thing they do?
For me, was finding out what software did what.

---

### Post by scragar on 2009-09-23
After a few boots I got used to the procedure and the first thing I always did was change my sources to include all repo's then install libdvdread, flash, checkgmail and VLC, then I uninstalled totem, soundjuicer and evolution. After that I installed updates, java, geany, khexedit, comix, unrar....

After a while I actually wrote myself a bash script to do it all for me :p. It basicly worked on a text file, when I wanted to install something I'd do:
```
aptwrap + **package**
```Which would record the package name to a text file, when I removed the package with```
aptwrap - **packagename**
```It would remove the line from the text file(and if it wasn't in the text file I'd recieve an option to mark it to remove on clean installs or leave it.), if I ever had to install it all again I could just run:```
/path/to/script/aptwrap sync
```

PS: I don't have this code anymore, I abandoned it when I moved to arch, same as the apt-fetch thing I was working on.

---

### Post by t0p on 2009-09-23
I think the first thing onscreen the new user sees is the **Ouroboros**, the serpent that swallows its own tail.  Maybe like this fancy one here.

[IMG]http://www.lightworks.net/blog/wp-content/uploads/2009/01/ouroboros.gif[/IMG]
It would slowly shrink as it sucks its tail down its throat, until it's gone.  Woooh!

---

### Post by 3rdalbum on 2009-09-23
> **ade234uk said:**
> Should there be a small welcome screen for new users.
The welcome screen runs through a small list of recommendations

How do I install codecs
How do I install flash
How do I activate video card
Where are my documents stored
How do I burn CDs

Just something really basic but gets to the point.

True. The new Ubiquity installer in Karmic is a start in the right direction, but it's too basic ("Look at this preinstalled program, this is what it does"). Just something like "This is what the Hardware Drivers manager does" or "This is Add/Remove Applications" would be fantastic.

The Learning starts now!

---

### Post by ade234uk on 2009-09-23
Exactly, its the small things that will get a new user up and running. Let's be honest all they want to be able to do is get codecs installed, make sure graphics card is working, flash and fonts. 

Only afterwards will they care about the tech side of things, i.e terminal and other stuff.

First impressions count.

---

### Post by t0p on 2009-09-23
> **ade234uk said:**
> Should there be a small welcome screen for new users.
The welcome screen runs through a small list of recommendations

How do I install codecs
How do I install flash
How do I activate video card
Where are my documents stored
How do I burn CDs

Just something really basic but gets to the point.

I am probably going over old ground here, but when a new user boots ubuntu for the first time, what is the first thing they do?
For me, was finding out what software did what.

Problem is, every different user wants/needs to know different things.  So what you going to do, tell the new user how to do *everything*?

Also, instructions on how to install codecs or flash would be problematic for ubuntu, which is a Free operating system with Free software principles.  Telling the new user how to install proprietary codecs does not fit with those principles.  If it's going to do that, ubuntu-restricted-extras might as well be preinstalled and not called "extras" anymore.

---

### Post by wojox on 2009-09-23
That little question mark icon or System > Help and support answer all those questions. Where do you think I get half my answers to reply to posts from. :lolflag:

---

### Post by ChrT on 2009-09-23
The instructions on how to use man pages, and a clear warning not to use the forums/irc as a lazy man's replacement of man pages and other documentation.

---

### Post by handy on 2009-09-23
A flashing image that says the following:

*Your are the lucky 1 millionth person to log on to the Ubuntu repositories with a new installation, therefore you will (after filling out the linked to form) receive 1 million euro's to do with as you will. :)*

The only thing we'd rather see would have a larger number than 1 million euro's in it...

---

