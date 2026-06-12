---
title: "virtual box problems"
date: 2012-03-04
forum: Virtualisation
---

### Post by carusoswi on 2012-03-04
I installed Virtual box (don't remember from where it came).  It seems to run fine, but when trying to install FreeBSD, the install disc spins for a while, then stops.  No activity on the screen.

I've done a bit of poking around on the forum, and thought that I should uninstall the version I have installed (I thought it came from the repositories), and install another version recommended in one of the threads.

However, when I go to the software center, the only virtual box offerings listed do not seem to be installed on my machine (so I cannot mark them for uninstallation).

Any suggestions on how I might:

1) Get FreeBSD to install in my current VB.
2) Remove the current version of VB and install another.

I am running Ubuntu 11.10 as a dual boot on a laptop with Win 7 professional.

I would give you information about VB, but I do not see any 'about' drop down box.

Thanks for any help you can give.

I am only looking to try out the FreeBSD, this is not a burning problem, just something I would like to try.

Tried Windows 7 Virtual PC, but, apparently that only works with Win OS's (thanks, MS).

Caruso

---

### Post by carusoswi on 2012-03-04
Ok, if this helps, the verion of VirtualBox that I have intalled is 4.1.8.
Caruso

---

### Post by howefield on 2012-03-04
That is the latest version.

To rule out the issue being with virtualbox, have you tried creating another virtual machine ?

eg, do you have an iso hanging around or live cd that you can use to test the virtualbox install, you don't need to create the hard disk for it, just point it to the iso, see if it can boot from it.

---

### Post by carusoswi on 2012-03-04
Thanks for the reply.  I will try your suggestion.
Caruso

---

### Post by carusoswi on 2012-03-04
So, I was able to install XP, so, obviously, there is a probelm with the two dvd's on which I burned the iso for Free BSD.

I can open those discs in ubuntu and view all the files.

What do you think could be the problem?

The first disc was burned as an image file from Brassereo, the second using Windows 7 default burner.

Also, if I did want to unintsall VB, how would I go about it?

Caruso

---

### Post by CharlesA on 2012-03-04
You can remove virtualbox like so:

```
sudo apt-get purge virtualbox-4.1
```

---

