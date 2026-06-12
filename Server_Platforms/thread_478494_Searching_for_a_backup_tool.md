---
title: "Searching for a backup tool"
date: 2007-06-19
forum: Server Platforms
---

### Post by chrishoeppner on 2007-06-19
Hi there!

I was just wondering what you guys tend to use for regular backups. I've been reading about amanda, mondo, mindi, and all the list up to rsync, tar, dump, and the like.

While some seem absolutely overkill (I'm not getting a tape drive to backup my home folder every other day), other seemed a bit out of my range (My shell scripting skills are... eh... did really I say "skills"?).

I need to get a proper backup solution into place, since I'm going to be in charge of some lan servers. And so far, I'm feeling a bit off.

What should I use? I do not have the time to learn them all, test them all, and then choose. Any suggestions? 

Thanks everyone!
Chris Hoeppner
[www.pixware.org](www.pixware.org)

---

### Post by newlinux on 2007-06-19
It maybe too simplistic for your needs (what features are you looking for?) but I currently use sbackup. Used to use rsync (grsync) but sbackup fits my needs.

---

### Post by eentonig on 2007-06-20
sbackup is easy to set up.

But rsync is just as easy.

If you want, I provide you with a tailored rsync commandline in a script. And an explanation on how to automate it.

---

### Post by falcon15500 on 2007-06-20
I use rsnapshot.  Works a treat.

---

