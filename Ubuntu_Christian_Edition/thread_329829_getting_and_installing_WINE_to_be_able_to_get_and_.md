---
title: "getting and installing WINE to be able to get and install E-Sword and other programs"
date: 2007-01-02
forum: Ubuntu Christian Edition
---

### Post by Scott A on 2007-01-02
Hello all, 
I am new to Ubuntu but have mangaged to install it and get on the internet. Major accomplishment for me. 

A year ago I tried another version of Linux, could NOT make heads or tails of it and gave up after a couple of months of frustration. 

I went to download.com hoping to find a linux version of E-sword, but no luck. (Did I miss it?)

I am trying to get and install WINE to be able to get and install E-Sword and other programs

Is wine the best way to run window programs on Linux? (only if I can't find a linux version of a program!)

Thanks in advance for any help. 

Scott A
[email]jasa711@yahoo.com[/email]

---

### Post by Spin Doctor on 2007-01-02
Hi Scott,

There is GnomeSword that you can use on your Ubuntu system. If you are running edgy, you probably want to check out the following thread:

[http://www.ubuntuforums.org/showthread.php?p=1682605#post1682605](http://www.ubuntuforums.org/showthread.php?p=1682605#post1682605)


Oh yeah, and a tip for you. Never display your emailaddress in plain view on a forum (or any websites for that matter). There are robots surfing around the internet just hoping to find an emailaddress they can send spam to... Do something like this instead:  jasa711 at yahoo dot com

---

### Post by mhancoc7 on 2007-01-02
> **Scott A said:**
> Hello all, 
I am new to Ubuntu but have mangaged to install it and get on the internet. Major accomplishment for me. 

A year ago I tried another version of Linux, could NOT make heads or tails of it and gave up after a couple of months of frustration. 

I went to download.com hoping to find a linux version of E-sword, but no luck. (Did I miss it?)

I am trying to get and install WINE to be able to get and install E-Sword and other programs

Is wine the best way to run window programs on Linux? (only if I can't find a linux version of a program!)

Thanks in advance for any help. 

Scott A
[EMAIL="jasa711@yahoo.com"]jasa711@yahoo.com[/EMAIL]

If you are using Ubuntu CE you can install WINE using Automatix.

Applications>System Tools>Automatix

Here is another E-sword post that might help as well.
[http://www.ubuntuforums.org/showthread.php?t=324792](http://www.ubuntuforums.org/showthread.php?t=324792)

God Bless, Jereme

---

### Post by Scott A on 2007-01-02
Spin Doctor, 
thanks for the advice about how to safely display my email address. 
I am afraid I do not know what "edgy" is. I take it it is not too much coffee? 
Is it like WINE? 
Sorry for the ignorance.
Scott A

---

### Post by Spin Doctor on 2007-01-02
No problem Scott...

Edgy is the version name of the latest Ubuntu distribution; Ubuntu Edgy 6.10.

---

### Post by Scott A on 2007-01-02
Hi Jereme, 
thanks for the link to another e-sword thread(?) post(?) Sorry - I don't know the terms yet. 
I went to Applications>
but there is no "System Tools" there. 
I found "System tools" under "Add and remove programs" but there was no ">Automatix"
Should I have those things?

---

### Post by Scott A on 2007-01-02
The CD case says it is "Ubuntu version 6.06 lts for your PC" 
-Scott 
By the way, I noticed that the penguin seems to be the mascot or symbol for linux. Is the coffee bean the symbol of mascot for ubuntu?

---

### Post by mysticrider92 on 2007-01-02
Are you using regular Ubuntu or CE? Automatix is not installed by default in Ubuntu, only CE. You can install Automatix and Wine using either Synaptic (System>Administration>Synaptic) or apt-get (from a terminal). Also, if you are using the regular Ubuntu, you can convert to CE using the Convert_me script [here]("http://www.whatwouldjesusdownload.com/christianubuntu/2006/11/ubuntu-ce-v151-dapper-downloads.html") (for version 6.06).

[Tux]("http://en.wikipedia.org/wiki/Tux") the penguin is the Linux mascot, and I think the three people holding hands (see [here]("https://wiki.ubuntu.com/Artwork/Official?action=AttachFile&do=get&target=UbuntuLogo.svg")) is Ubuntu's symbol.

---

### Post by Scott A on 2007-01-04
Hi Misticrider, 
in your post you said:  	Are you using regular Ubuntu or CE? Automatix is not installed by default in Ubuntu, only CE. You can install Automatix and Wine using either Synaptic (System>Administration>Synaptic) or apt-get (from a terminal). Also, if you are using the regular Ubuntu, you can convert to CE using the Convert_me script here (for version 6.06).

I clicked on the Convert to CE, but I don't know what do do with it after I download it. I tried right-clicking, opening it, extracting it, and a few other things, but nothing seems to work. 

Also, after I install WINE (I think I did) where do I go to look for it? Would it be under "Applications"? Would Automatix should up there too? 

I have tried synaptic a couple of times, but I don't know what to do with it. Are there instructions for how it works? Sorry, I am clueless. 

Thanks again for all the help.
Scott A

---

### Post by runkidrun on 2007-01-05
I just installed WINE through Automatix. Here are some steps to reaching the directory to which it was installed:

1.Click Places, then select "Computer"
2.Once a window pops up select "File System"
3.The you will see lots of folders...select "usr"
4.Then you will see more folers...select "bin"
5. Then you will have a ton of files and folders in this directory....scroll down until you see "winecfg"...then double click it and select run.
6. this configures wine.
7. then click "winefile" and select run.
8. from there you can navigate to the directory you have the file stored....
**Tip**: you might want to create a shortcut on the desktop to make it easier (right click create launcher) then browse to the directory that was shown above..

---

