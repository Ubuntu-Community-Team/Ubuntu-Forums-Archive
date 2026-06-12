---
title: "Tricking ubuntu into thinking you have root privledges"
date: 2010-01-19
forum: Security
---

### Post by KinKiac on 2010-01-19
Ok, So i ran into this a while ago and I have no clue if this was a known issue and or if it works in newer versions of ubuntu or not, but here is the situation:  

At my work(I work in a small IT dept) we have a few ubuntu boxes that are set up as terminals for employees to view a limited number of websites including our insurance info, corporate website, etc etc.  The boxes run ubuntu hardy server edition, but have the XFCE desktop environment installed.  I wont go into the details of how they are configured, I didnt set them up and really dont know all of the restrictions that have been added to them.  All I know is that everything is locked down.  There is a password just to get into a terminal, and there is a separate root password.  As well, most if not all keyboard shortcuts are disabled.  USB and floppy drives are disabled.  Basically they are set up so that they can access only a handful of sites, and so that you cant get to a terminal or to the desktop even, without the password(someone has figured out how to hack it, other than me, but I wont get into that).

So, one day im out making a change on one of the terminals, and just for s&g i decided to see if "I" could hack it, using a thumb drive installation.  I have a 16gig thumb drive with a full installation on it(9.04), none of this persistent live cd crap. lol.(I know it will wear out at some point but its got a lifetime warranty with the manufacturer and the retailer will replace it for free within 3 years)  Anyway, I booted to my thumb drive, BIOS was not locked down, cool.  I could get to my desktop, had all my files and really could use the PC to do whatever I wanted for the most part(didnt have network access without a valid user id and pass, but whatever).  I then mounted the other filesystem's HDD by clicking on it in the places menu( I love my gui's and Im a noob, lol:P.)  After mounting it I ran "sudo nautlius" from a terminal and entered in MY sudo password.  After doing so I could open ANY file on the HDD and make changes as if I was root, even though i didnt actually have root access on the filesystem i was accessing.  Just as a test I edited the menu.lst file to show grub at startup and also re-enabled USB support by editing the server.conf file.  I then rebooted and sure enough, grub menu came up and it recognized my USB drive when I inserted it after the desktop and everything came up.  

Soooo, basically by using another installation's sudo password, I was able to access another totally different filesystem, as if I had root privileges.  

Anyone else out there know of this?  Anyone know if this has been corrected in newer versions or was anyone even aware of this?  Im just curious as our network guy had no clue about this until I told him and he's pretty good with linux.

---

### Post by CharlesA on 2010-01-19
Physical access > security.

Also: you are not "tricking" ubuntu by using another install's root password. You mount it under root and you have root access.

Same thing goes if you boot into a recovery shell.

---

### Post by FuturePilot on 2010-01-19
> **CharlesA said:**
> Physical access > security.

Also: you are not "tricking" ubuntu by using another install's root password. You mount it under root and you have root access.

Same thing goes if you boot into a recovery shell.

Exactly.

If you have physical access you can do just about anything.

---

### Post by charliehorse55 on 2010-01-19
If you really want a computer where Physical Access < Security

You'll have to use  encyption, and if you lose your password... it's history for that data.

---

### Post by CharlesA on 2010-01-19
> **charliehorse55 said:**
> If you really want a computer where Physical Access < Security

You'll have to use  encyption, and if you lose your password... it's history for that data.

That's pretty much it. I mean, you could password protect the BIOS and lock it down. password protect GRUB, but it won't do a whole hell of a lot of good, since they are fairly easy to bypass.

---

### Post by KinKiac on 2010-01-19
> **CharlesA said:**
> Physical access > security.

Also: you are not "tricking" ubuntu by using another install's root password. You mount it under root and you have root access.

Same thing goes if you boot into a recovery shell.

Ok so this is normal then.  I wasnt sure, I thought you needed separate permission to read another root system.  Also, with regards to the root shell, you can lock that down as the boxes at my work are.  I tried booting into the recovery option and then going into the root shell but it asked me for root's password before it would let me do anything.  However, on a normal install, that is not the case as Ive hacked into another box that way.  One of my co-workers had a standard install of ubuntu hardy for testing purposes and I was learning ubuntu and wanted to get into it to play around and I didnt have his pass, so I just went into recovery mode and then created a new account for myself.

---

### Post by rookcifer on 2010-01-20
As was said, physical access to a machine = pwnage.  All you have to do is pop a liveCD or USB in the machine and it's game over.  This is true for Windows (the Linux liveCD's can read/write NTFS partitions too) as well as all *nixes and other OS's.  There are 3 ways to combat this:

1) BIOS password.  Not foolproof but it might stop kiddies.

2) Put the machine in a room and lock it up -- only give others access to a keyboard, mouse and monitor.  If these are terminal clients, there is no reason the employees need physical access to the computer case itself anyway.

3) Hope your employees are trustworthy.

Encryption can also stop this, but it doesn't help while the machine is turned on.  It only works when it's off.

---

### Post by iponeverything on 2010-01-20
> **rookcifer said:**
> As was said, physical access to a machine = pwnage.  All you have to do is pop a liveCD or USB in the machine and it's game over.  This is true for Windows (the Linux liveCD's can read/write NTFS partitions too) as well as all *nixes and other OS's.  There are 3 ways to combat this:

1) BIOS password.  Not foolproof but it might stop kiddies.

2) Put the machine in a room and lock it up -- only give others access to a keyboard, mouse and monitor.  If these are terminal clients, there is no reason the employees need physical access to the computer case itself anyway.

3) Hope your employees are trustworthy.

Encryption can also stop this, but it doesn't help while the machine is turned on.  It only works when it's off.

All of these suggestions seem perfectly adequate measures against casual misuse. As for 3), you don't have to hope - just make it known that they will be fired and that there are a number of state and federal laws that they could possibility prosecuted under as well..

---

### Post by cdenley on 2010-01-20
> **KinKiac said:**
> Ok so this is normal then.  I wasnt sure, I thought you needed separate permission to read another root system.  Also, with regards to the root shell, you can lock that down as the boxes at my work are.  I tried booting into the recovery option and then going into the root shell but it asked me for root's password before it would let me do anything.  However, on a normal install, that is not the case as Ive hacked into another box that way.  One of my co-workers had a standard install of ubuntu hardy for testing purposes and I was learning ubuntu and wanted to get into it to play around and I didnt have his pass, so I just went into recovery mode and then created a new account for myself.

If the root password is not set, then you can get a root shell in recovery mode. If a root password is set, then you will be required to enter it. Of course, you can always reset it with a livecd. I don't recommend setting a root password.

---

