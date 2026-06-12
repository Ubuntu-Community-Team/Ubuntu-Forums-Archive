---
title: "how to use Wipe 0.21-3 for secure deletion of files?"
date: 2010-10-16
forum: Security
---

### Post by jadu on 2010-10-16
Hello, 
I was just recommended Wipe as an equivalent to Eraser in Windows-- a program to securely delete files. I learned this in a computer security workshop.
I already have Bleachbit for cleaning empty space on the disk.

I can't figure out how to use Wipe. I installed it from the Software Center. But I don't know where to go from here. It's not in the applications menu, and I don't see it in the System-Administration menus either.

There are only two posts in the forum with "wipe 0.21" and neither one explains. I got the idea that it needs to be used from terminal, but I don't know how.

I'd like to figure this out to tell the other people in my workshop.

This is the site for Wipe for Lucid (my distribution):
[http://packages.ubuntu.com/lucid/wipe](http://packages.ubuntu.com/lucid/wipe)
Doesn't have any information, as far as I could see. The website I found doesn't work.

Any ideas?
I am pretty much a beginner, or a late beginner, so please, if you are kind enough to explain, I won't be at all offended if you talk down to me and explain obvious things!

thanks

---

### Post by cariboo on 2010-10-16
Wipe is a command line program, open a terminal and type:

```
wipe -h
```

for command line options.

---

### Post by jadu on 2010-10-16
thank you, I looked at that. But I don't see an explanation of how exactly it works. I could guess it might be, for example for a quick wipe,

wipe-q {file path and name}

would that be right?
do I have to get root priveleges to run it?

I found the wipe website- but no explanation there either.
[http://wipe.sourceforge.net/](http://wipe.sourceforge.net/)

---

### Post by cariboo on 2010-10-16
Almost all Linux/Unix utilities have man pages, to see the man page for wipe, in a terminal type:

```
man wipe
```

or the man page on the web is [here]("http://abaababa.ouvaton.org/wipe/wipe.1.html").

---

### Post by jadu on 2010-10-17
Thanks a lot, I think I should be able to take it from there. I'll keep it in mind for future problems with other programs.

---

### Post by rookcifer on 2010-10-17
Just use shred.  It's already built in.

```
shred --help  
```

---

### Post by jadu on 2010-10-18
Thanks a lot, I looked at the shred, it's good to know about another option.

---

### Post by Andrew.Z on 2010-10-22
> **jadu said:**
> Hello, 
I was just recommended Wipe as an equivalent to Eraser in Windows-- a program to securely delete files. I learned this in a computer security workshop.
I already have Bleachbit for cleaning empty space on the disk.


In the BleachBit GUI menu is an option for shredding arbitrary files such as that confidential spreadsheet on your desktop.  Also the new [BleachBit 0.8.2 has improvements to file shredding and cleaning empty disk space](http://bleachbit.sourceforge.net/news/test-bleachbit-082-beta).

---

### Post by johnkills on 2010-10-22
I think deleting encrypted files that look like random data more secure than deleting normal files. You go and do that. :)

---

### Post by jadu on 2010-10-22
Hi, I use BleachBit (thank you for making it!)
But I had never noticed the shred files option in the file menu!
That is what I was looking for, something with a graphic interface. I'll tell other people I know with bleach bit about that function, I think they don't know either. 
thanks again

---

