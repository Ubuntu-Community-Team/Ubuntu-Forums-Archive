---
title: "Elementary OS black screen on boot"
date: 2015-07-23
forum: Ubuntu/Debian BASED
---

### Post by alex428 on 2015-07-23
Not much more can be said, this came out of the blue. See [this]("https://www.youtube.com/watch?v=fALabWGCLhE&feature=youtu.be") video to see the problem.

Currently running Elementary OS on a HP EliteBook 8440p with 2GB's of RAM. No recent changes have occurred aside from my routine "sudo apt-get dist-upgrade" which is probably the culprit. Sorry for the lack of info but there really isn't much else to tell.

Any ideas? I've found nothing.

---

### Post by alex428 on 2015-07-23
After hours of wonderful fun I have achieved,
**nothing**

I have resorted to throwing any command I can find at the terminal in hope that it will work if the stars align right but I'm yet to have any luck in this endeavour. However from this I've found that most of them respond with a phrase like "cannot open display" which doesn't sound very good *(sorry can't remember which command responded with this just believe me that multiple commands have)*. Also one attempted to mountall which caused "Plymouth command failed" along with "Disconnected from Plymouth".

That's it out of ideas, someone for the love of god save me from this, this is soul-destroying](*,).

[B]Edit:
[/B]
Managed to get the same response with the command:
glxinfo | grep -C 4 renderer

Using this I received this: **"Error: unable to open display :0.0"**
*Does this open up any possibilities?*

**Edit 2:**

Also get a similar response **"[GTK] cannot open display :0.0"** when using the command:
pantheon-terminal . ~/.bashrc

*Now time to sleep in the hope that Torvalds Claus comes down the chimney and fixes my pc.*

---

### Post by alex428 on 2015-07-28
Anyone?
Sorry to bump but I'm really stumped with this and ultimately left without a laptop.

---

### Post by howefield on 2015-07-28
If it happened with a recent (kernel) update, have you tried booting into the previous kernel ?

And yes, you might want to fix the disk error that comes up, can't read it properly so not completely sure what it says.

---

### Post by alex428 on 2015-07-28
I have now but unfortunately I've done something stupid while trying to frantically find a fix. Somehow instead of loading up my desktop environment (just the default for eOS, Pantheon) I've made it so I now boot into just a command line screen from which I can login and run commands as normal but that's about it. I can't find any commands to manually kickstart the Pantheon desktop into action. So I can't really tell if the older kernel versions are improving anything at all.

Also just a word of warning in case you haven't noticed I'm a total noob when it comes to Linux but I'm improving, slowly.

---

### Post by alex428 on 2015-08-11
So I've been continuing on my quest to actually have a functioning laptop for when I go back to college. I've found that surprisingly it seems that I haven't caused the problem with it booting solely into command line as it seems there are a few people having similar issues lately. Also even the oldest record on the "Previous Linux Versions" list (recovery boot or not) does the exact same thing it just prompts me to login (which does work and I can download and install applications using apt-get install).

---

### Post by howefield on 2015-08-12
Much as I dislike the reinstall answer, there are times when it is simply more efficient to bite the bullet and install something that works with your hardware. 2 weeks fighting this issue versus 30 minutes to install and configure (and backup) a working reinstall.

---

### Post by alex428 on 2015-08-12
> **howefield said:**
> Much as I dislike the reinstall answer, there are times when it is simply more efficient to bite the bullet and install something that works with your hardware. 2 weeks fighting this issue versus 30 minutes to install and configure (and backup) a working reinstall.

It's looking like I'm going to verge that way, man as much as I love it Linux always seems to break for me, thank god my work is backed up on Dropbox. But first I'm going to see if I can find a way to utterly purge my Intel graphics driver (as a last resort), reboot, reinstall lightdm + elementary-desktop and see if it responds at all. If not I'll nuke the drive from orbit. I know how to reinstall all the eOS stuff just no idea how to purge my graphics driver.

Edit: Also helps if you have your wireless adapter turned on whilst using apt-get :P

---

