---
title: "Sync directory to remote nfs share. What tool?"
date: 2011-07-21
forum: Server Platforms
---

### Post by phillips321 on 2011-07-21
Guys,

I have a folder on my workstation and I currently have an identical copy on my nas mounted via ifs (I'll be using this as my backup). The folder contains many virtual machines that are usually powered off. I like to think of the copy on my nas as a backup. The benefit of having two copies of my vms is that if I boot up too many on my workstation and the drive starts to cause a bottle neck I can simply boot the vms from the nas instead. (gigabit ethernet)

I would like changes I make to my local copy to be reflected on the nas.

I want this to happen In the background, I.e. If I turn off my machine it shouldnt cause a problem, the next time I boot up it just re checks the files and continues syncing the 2 directories.

What is the best tool for the job? Rsync?

I've never really used it before so a few pointers to get me going would be great, or obviously other recommendations if there are any.

Thanks in advance

---

### Post by papibe on 2011-07-21
rsync will do the job just fine. If you don't feel comfortable writing scripts and using the command line, there are a few options. I would recommend taking a look at [Unison]("http://www.cis.upenn.edu/~bcpierce/unison/"). It is in the repositories (Software Center).

Here's a [video]("http://www.youtube.com/watch?v=fOxTh6um1p0") tutorial that accomplish the same thing you need: backup from your desktop/laptop to a NAS. It is done on a Mac client and a FreeNAS server, but it should point you in the right direction.

Hope it helps.

Regards.

---

