---
title: "Help! CANNOT USE COMPUTER following attempt to make jackd work in Ubuntu Studio 10.04"
date: 2010-05-30
forum: Ubuntu Studio
---

### Post by hreichgott on 2010-05-30
I have been using jackd to stream audio from my computer.

After the upgrade to 10.04, I tried to start jackd, and it crashed with a "Bus error."  Before crashing, it warned that in etc/limits.conf, memlock should not be set to unlimited.  I was confused because in my limits.conf file, memlock is not set to unlimited.  I consulted the forums and learned that limits.conf is now neither in /etc nor in /etc/security but in /etc/security/limits.d/audio.conf.  I saw warnings that it should not be edited by hand, but could only learn how to set or remove realtime priority using dpkg, not how to change memlock settings.  I edited it by hand anyway to change memlock from unlimited to 375000. (I have 500 mb of memory.)  After a reboot all was still normal.  Tried to start jackd, didn't get the warning message this time, but still got a crash with a bus error.

Then I saw advice that existing limits.conf files could cause conflicts with audio.conf and jackd, so I removed /etc/security/limits.conf.

Now I cannot log in to my computer at all!

The login screen comes up, I enter my password, and I get "Unable to open session."

I know it is not a password/caps lock issue or anything, because entering anything other than my actual password gives me "Authentication failure."  I have tried logging in to another account and also get "Unable to open session" when I use the correct password.

Help!  I want to use my computer again!  What's going on?

---

### Post by hreichgott on 2010-05-30
More information:
CTRL+ALT+F1 from the login screen gives me a text only terminal.  Attempting to log in there (using either account) gives me:

Welcome to Ubuntu!
(blah blah blah)

Error in service module

Ubuntu 10.04 LTS [computer name] tty1

[computer name] login:

...and the same thing happens again if I try to log in.
help?

---

### Post by psy-man on 2010-05-30
you will have to restore /etc/security/limits.conf and to do that you will need to boot your system with a live cd or from another partition or by booting the single user recovery kernel. Can you log into a shell? press "ctrl+alt+f1" .If you can type sudo nano /etc/security/limits.conf  nano is a command line file editor so you type in a few #hashes and press "ctrl+o" to write the file and then "ctrl+x" to exit.
 I too am have jack problems so I sympathise.
 I can tell you that my copy of /etc/security/limits.conf is entirely commented out apart from those lines at the bottom for the audio group so it seems likely that the system looks for and checks the file for relevant entries, if so a blank file should do.

---

### Post by psy-man on 2010-05-30
ok your answering my question before I get it typed thats good.
So how about booting the single user recovery kernel? do you get any options when grub starts up?
I run multiple OSs so I see options but I think grub hides them if you only have one os on the system so you have to hit a key as grub loads thing is I dont know what ,try shift as the machine boots, a quick google tells me you have to hold shift and then press escape to get grub 2s menu up then you can select the single user kernel, I dont know if this is going to work yet,

---

### Post by hreichgott on 2010-05-30
How do I get into single user recovery mode?

I have another computer downloading the 10.04 iso to burn on a cd in the hopes that I can run it from the cd long enough to put back limits.conf.  But a single user recovery mode would be much easier!

By the way, I did back up limits.conf, so all I have to do is remove the ~ from limits.conf~

---

### Post by hreichgott on 2010-05-30
On my computer, Shift gets into the BIOS, then Escape exits BIOS.  I don't see any options related to the operating system, recovery mode etc. in BIOS.

---

### Post by psy-man on 2010-05-30
backed up the file before deleting, excellent,
 can you get your grub options menu up
 it should show at least two kernel options and memtest the single user kernel is the second one down the list, you should get the list up by pressing shift as soon as grub starts and then escape.
by the way the ubuntu studio DVD is not a live cd it is an installer you will have to use a special boot parameter to get a recovery shell with it other wise you will be reinstalling the whole OS , This often fixes problems like buying a new car saves changing the oil in your old one. A straight ubuntu live cd is a very useful tool for fixing messed up systems.

---

### Post by hreichgott on 2010-05-30
Holding down Shift gives a message that says "Stuck key / press F1".
Pressing F1 gives me the BIOS menu.
Nothing about grub or operating systems.
(I only have Ubuntu on that machine.)

The boot options in BIOS are only about whether to boot from USB, CD, etc. and in what order.

---

### Post by psy-man on 2010-05-30
you have to press shift after the bios has finnished and passed on to grub, or so it says in the grub2 wiki

---

### Post by bildr on 2010-05-30
while booting you are asked to select which kernel to boot. at this screen do not wait, hit some arrow keys so the timer stops, then e to edit kernel params and give it single or runlevel = 1 or 1 or something.  frankly i don't know why this keeps changing.

---

### Post by hreichgott on 2010-05-30
I don't get that screen.  I just get the "ubuntu studio" splash screen followed by the logon screen.

---

### Post by hreichgott on 2010-05-30
No luck getting the grub menu to come up.  But I created a bootable Ubuntu CD, booted from CD, had to mount the existing filesystem into ubuntu's little sandbox directory, then fixed limits.conf and can now boot.  Phew!  Thanks.  Now I return to fighting with jackd...

---

### Post by psy-man on 2010-05-30
jack is buggy in lucid there is an unofficial patch available but even that needs testing I'm trying it out now and at least I have a close button that works when jack crashes, cant find the post but the repository for the patch is here [https://launchpad.net/~slavender/+archive/lucid   ]("https://launchpad.net/%7Eslavender/+archive/lucid")
Scott only updated his patch for qjackctl 9 hours ago.

---

### Post by sgx on 2010-05-30
> **hreichgott said:**
> Holding down Shift gives a message that says "Stuck key / press F1".
Pressing F1 gives me the BIOS menu.
Nothing about grub or operating systems.
(I only have Ubuntu on that machine.)

The boot options in BIOS are only about whether to boot from USB, CD, etc. and in what order.

If the download of 10.04 is hours from completion, any mini-distro
has an editor you can use to fix the file you backed up

DSL linux is less than 50 meg, the iso images are in the archive folder of each mirror.

[http://www.damnsmalllinux.org/download.html](http://www.damnsmalllinux.org/download.html)

If you can get to a root shell prompt, by a command like
telinit 1  or just init 1

you can use nano, vim, emacs type of editors to fix the file.

[http://linux.about.com/library/cmd/blcmdl8_telinit.htm](http://linux.about.com/library/cmd/blcmdl8_telinit.htm)

telinit 6 should reboot the system.

Cheers

---

### Post by hreichgott on 2010-05-30
great, thanks for the suggestions psy-man and sgx.
Will check out Scott Lavender's PPA too.

---

