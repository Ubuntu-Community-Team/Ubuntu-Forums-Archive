---
title: "Multiple domain sparc xorg"
date: 2007-05-29
forum: Sun Sparc Users
---

### Post by didijeeeke on 2007-05-29
Hey ,

After long google search i am stil nowhere.

I try to get X working on my sun ultra 80.

I found out Xorg wil not scan or support pci cards on the seconds domain.

with multiple domains i mean :

00001:00:01.0
00000:00:10.0

mayby there is a way to get xorg use the secondary domain.

i saw on the changelog of xorg 7.2 (the version i use) that support for multiple domain was added.
Mayby the ubuntu package team removed this support or mayby there is a problem but when i use:


X -scanpci 

it still shows me the fisrt domain 00000 only.

I gave up the domain part so i did put my pci card in the 66 pci slot ( the first domain)

But no luck .. i configured the xserver to use glint driver it detects the card but it can't get it to work.

Resource conficts is all i get.
And some errors i tipe in google but looks like i am the first one to get them :D

My card is a pgx32 permedia 2.

My question is how do i get this card to work or how do i get xorg to use the secondary domain.

I want to use the secondary domain so i can use my other pci video cards that don't fit in the 66 slot.

Thanks, and please help i don't like solaris and would love to use gnome on my sun.

---

### Post by jon124 on 2007-05-30
I am having the exact same problem, and would love an answer to this. I've been trying to get ubuntu on the machine for a while now and I'm about to give up and just put solaris on the damn thing.

---

### Post by jon124 on 2007-05-30
Just tried to put solaris on it, hardware error! who wants this enterprise 250 before I throw it out the window lol!

---

### Post by didijeeeke on 2007-06-03
i also installed solaris 10.

And it worked but i like ubuntu

i don't have a mouse so i would like to use synergy.

In ubuntu a 3 seconds command line job but in solaris i don't even know where to start.

i found on the internet older Xfree versions do work can anyone confirm this ?

---

### Post by vikrant on 2007-07-11
> **didijeeeke said:**
> 

i found on the internet older Xfree versions do work can anyone confirm this ?


Yes,  I have installed Debian on my E250 with the same video card and it works with Xfree86.

Check out this thread if you have not already.

[http://ubuntuforums.org/showthread.php?t=169782]("http://ubuntuforums.org/showthread.php?t=169782")

I pretty much gave up on getting X to work.  However, your posts have sparked a renewed interest in the matter.  I will post if I figure anything out. 

-Vik

---

