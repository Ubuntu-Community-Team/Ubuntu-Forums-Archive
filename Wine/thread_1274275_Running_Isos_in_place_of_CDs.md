---
title: "Running Isos in place of CDs"
date: 2009-09-24
forum: Wine
---

### Post by Affrikka on 2009-09-24
Hey everyone,

I wanted to make an iso of my copy of Reason from Propellerhead so that I could use it on my box at home and have the cd to take with me. I successfully made an iso, and also mounted it, and installed it, but when I want to run it it says "waiting for disk"

SO, this is what I've done:


- I've tried to configure wine so that the D:/ drive is linked to a folder with JUST the .iso image in it, and nothing else

- I've tried the same thing, but linked it instead to the folder that contains all the mounted iso stuff in it, like the setup.exe and all that jazz

- I've tried creating a new drive, E:/ and saying its a CD-ROM, and did both of the steps I tried above (except that its linked to the E drive not D)


And nothing is working. So how can I tell wine (and/or reason) that it needs to run off the .iso or the mounted folder and NOT a cd?


thanks!


Mathieu
__________________

---

### Post by mister_playboy on 2009-09-24
Did you install from the mounted image?  Often, this will solve the "no CD found" problem.

---

### Post by u235sentinel on 2009-09-24
> **mister_playboy said:**
> Did you install from the mounted image?  Often, this will solve the "no CD found" problem.

good question.  It usually has worked for me with other games like Oblivion (for example).

mount -o loop cdromimage.iso /mount_point

Give it a try.  Usually works unless there is some freaky protection on the disk.

---

### Post by Affrikka on 2009-09-24
(sorry but i'm a linux newb kinda)

You all mean like... mounting the ISO into a file, right? in which case I have, I install gmount-iso and created a file on my desktop called "Reason" and I mounted the iso into that folder, in which is a bunch of stuff like setup.exe and autorun.exe etc.

---

### Post by u235sentinel on 2009-09-25
> **Affrikka said:**
> (sorry but i'm a linux newb kinda)

You all mean like... mounting the ISO into a file, right? in which case I have, I install gmount-iso and created a file on my desktop called "Reason" and I mounted the iso into that folder, in which is a bunch of stuff like setup.exe and autorun.exe etc.

mounting the iso file itself into a directory.  By using the -o loop option in the mount command you can mount iso images to a mount point and interact with it as if it's a cdrom. 

I'm doing that now automagically for my kids with oblivion.  It needs a  cd to play but I don't let them have the  cd's.  I've seen them destroy to many to count.  So I use dd to create the iso immage, save it to an isos directory then use /etc/fstab to mount it on startup.  Yeah I have a few isos and directories.  They all load at startup but it's working so far :-)

---

### Post by Affrikka on 2009-09-25
hmmm...

well I did run mount -o loop, and it gave me the various options to which I can run the mount command, and the one that looked like it would work was "mount -t Reason 4.iso /Desktop/Reason ISO"

So I typed that in, and the terminal just sat there, and when I went to close out it said "ther terminal is in the middle of a process, kill it?" so I just killed it, because after looking around and trying to run it nothing had changed.

---

### Post by Affrikka on 2009-09-27
hello? anyone else know what to do?

---

### Post by u235sentinel on 2009-09-28
> **Affrikka said:**
> hmmm...

well I did run mount -o loop, and it gave me the various options to which I can run the mount command, and the one that looked like it would work was "mount -t Reason 4.iso /Desktop/Reason ISO"

So I typed that in, and the terminal just sat there, and when I went to close out it said "ther terminal is in the middle of a process, kill it?" so I just killed it, because after looking around and trying to run it nothing had changed.

Not sure about what the above is doing.  Looks a little strange to me.  Here's what I do

mount -o loop cdromimage.iso /mnt


/mnt is a mount point that should work for most flavors.

---

