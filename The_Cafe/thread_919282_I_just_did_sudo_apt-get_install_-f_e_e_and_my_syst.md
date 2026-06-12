---
title: "I just did sudo apt-get install -f e_e and my system doesn't work"
date: 2008-09-13
forum: The Cafe
---

### Post by Lord Xeb on 2008-09-13
so I had to do a reinstall. Or would it have harmed anything?

---

### Post by zmjjmz on 2008-09-13
What?
```
apt-cache search e_e
libxml-encoding-perl - Perl module for parsing encoding map XML files
lft - layer-four traceroute
libapache2-mod-line-edit - search-and-replace line editor module for apache 2
libapache2-mod-mime-xattr - Apache2 module to get MIME info from filesystem extended attributes
devscripts - Scripts to make the life of a Debian Package maintainer easier

```

---

### Post by Lord Xeb on 2008-09-13
it started to remove everything on my machine e_e

---

### Post by LaRoza on 2008-09-13
> **Lord Xeb said:**
> it started to remove everything on my machine e_e

First, -f fixes broken packages and I see no package e_e

---

### Post by zmjjmz on 2008-09-13
No comment.

---

### Post by voteforpedro36 on 2008-09-13
Well, seeing as how the command to remove is actually apt-get remove, and e_e isn't even a package (unless you meant e*e, which I guess would fix/install any packages the have two e's in the name), you're not the brightest bulb in the box.

---

### Post by smartboyathome on 2008-09-13
I think the e_e is a smiley. He just ran sudo apt-get install -f, with nothing else after it. Reference: last post of Xeb's in this thread.

---

### Post by zmjjmz on 2008-09-13
> **smartboyathome said:**
> I think the e_e is a smiley.

Doesn't look very smiley to me.

---

### Post by smartboyathome on 2008-09-13
> **zmjjmz said:**
> Doesn't look very smiley to me.

> **Lord Xeb said:**
> it started to remove everything on my machine **e_e**

In this post its used as a smiley, so I assume it is one in the topic as well. Even if it doesn't look like one.

---

### Post by voteforpedro36 on 2008-09-13
> **zmjjmz said:**
> Doesn't look very smiley to me.

Exactly. But yeah, you're right. Either way, doesn't the fact that you're running apt-get **install** give anybody a clue? How is installing going to REMOVE your packages? Sorry but that's common sense. Sorry if I sound rude or anything, but...

So what does the option fix actually do? I would guess reinstall, which means it would remove broken packages, but why would it remove all packages?

---

### Post by Giant Speck on 2008-09-13
It's a smiley.

What he's saying is that he typed **sudo apt-get install -f** into his terminal and pressed enter and now everything is screwed up.

Which doesn't make any sense to me.  I actually used it the other day and it didn't delete all of my programs.

If you seriously cannot log into GUI, you could try logging into command prompt and typing **sudo apt-get install ubuntu-desktop** (I think that's the package name for it.  I don't really know, because I use Kubuntu), and it should reinstall all of your programs.  Then, when it's done you can simply type **gdm** in order to get to the GUI login screen.

---

### Post by zmjjmz on 2008-09-13
> **Giant Speck said:**
> It's a smiley.
But, aren't smileys supposed to, you know, smile?

---

### Post by LaRoza on 2008-09-13
> **zmjjmz said:**
> But, aren't smileys supposed to, you know, smile?

emoticons are very diverse (that is probably the eastern style: [http://en.wikipedia.org/](http://en.wikipedia.org/))

Either way, they shouldn't be used with commands as commands are case sensitive and require precision.

---

### Post by Giant Speck on 2008-09-13
> **zmjjmz said:**
> But, aren't smileys supposed to, you know, smile?

I guess so, but smiley seems to encompass all of such "text pictures"

[noparse]:)[/noparse]
[noparse]:([/noparse]
[noparse];)[/noparse]
[noparse]:o[/noparse]
^_^
o.O
O_O
>.>
<.<

They're all smileys.

---

### Post by init1 on 2008-09-13
> **zmjjmz said:**
> Doesn't look very smiley to me.
Well he uses it after nearly all posts he makes

> **voteforpedro36 said:**
> Exactly. But yeah, you're right. Either way, doesn't the fact that you're running apt-get **install** give anybody a clue? How is installing going to REMOVE your packages? Sorry but that's common sense. Sorry if I sound rude or anything, but...

So what does the option fix actually do? I would guess reinstall, which means it would remove broken packages, but why would it remove all packages?
apt-get install -f fixes broken packages. So if he tried to install something that conflicted with something major, such as ubuntu-desktop, apt-get install -f would remove everything in ubuntu-desktop.

---

### Post by Riffer on 2008-09-13
I think he uses the "@" to represent dimples.

---

### Post by LaRoza on 2008-09-13
> **Riffer said:**
> I think he uses the "@" to represent dimples.

Interesting, by they weren't used here ;)

---

### Post by Lord Xeb on 2008-09-14
e_e means leering But yeah, things started to be removed. I have no idea why.... I think there was a * in the command but I do not remember

---

### Post by chris4585 on 2008-09-14
I had a friend on debian who tried installing compiz and for some reason it completely removed gnome, he had to manually reinstall those packages, the lesson is apt-get isn't perfect, or none of that would happen maybe send a bug report?

---

### Post by fmartinez on 2008-09-14
I think the real question is why did he try to use the command in the first place. 
- Did he try to install something that conflicted with another package? 
- Did he try to install something and stop the installation mid way? 
These actions may cause broken dependencies and you have to use the "sudo apt-get -f" to fix these. 
If this is the case; whatever he tried to install previously is what really caused the issue.

---

