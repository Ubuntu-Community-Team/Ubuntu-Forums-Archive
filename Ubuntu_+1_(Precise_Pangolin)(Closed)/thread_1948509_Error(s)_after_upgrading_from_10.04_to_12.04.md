---
title: "Error(s) after upgrading from 10.04 to 12.04"
date: 2012-03-28
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Tiganjero on 2012-03-28
Yes, I know it was a stupid idea, I knew that before I've done it. Anyhow, while booting Ubuntu threw an error regarding HP .rules files in */etc/udev/rules.d/*, so I moved those to a different folder thus fixing that error. I had to execute *mount -o remount ,rw /* before I could do anything since the partition was mounted as read-only. Although that is now fixed, I'm getting a different error now and am completely clueless about it. ```
** (plymouthd :364) : WARNING **: Command line 'dbus-launch --autolaunch=9c6a84f6594013f84b94c6374f566b4e --binary-syntax --close-stderr' exited with non-zero exit status 1 : Autolaunch error : X11 initialization failed.\n
udevd[405]: specified group 'colord' unknown

The disk drive for / is not ready yet or not present.
Continue to wait, or Press S to skip mounting or M for manual recovery
```
What seems to be the problem here and is there a way to fix it? I guess I could back up the whole home folder and install a fresh copy, but that would be really time consuming since I'd have to re-install all of the applications too.

Cheers,
George

---

### Post by The Cog on 2012-03-28
Moved to Ubuntu+1

---

### Post by dino99 on 2012-03-28
Get the uuid(s) to compare with your error : autolaunch= ....


sudo blkid

about plymouth, via synaptic, purge then reinstall it (all the related packages)

---

### Post by Tiganjero on 2012-03-28
> **dino99 said:**
> Get the uuid(s) to compare with your error : autolaunch= ....

sudo blkid

about plymouth, via synaptic, purge then reinstall it (all the related packages)

Thanks for a quick response. *blkid* returns
```
/dev/sda1: LABEL="Transcend 720GB" UUID="441402B11402A5D0" TYPE="ntfs"
/dev/sda3: UUID="1ef44926-701d-481d-a46b-56a1bab9cec8" TYPE="ext4"
/dev/sda5: UUID="b40d20a3-3f02-43c4-82b2-191d68f7f722" TYPE="swap"
```
However, the only apt-get command I can run is moo. Still quite clueless.

Cheers,
George

---

### Post by Gremlyn1 on 2012-04-06
I just ran into this exact same error while attempting the 10.04 to 12.04 beta2 upgrade. I am currently booting from a live disk to see if I can find anything awry, and failing that I will do a fresh install. 

My uuids all match as expected, and I was also seeing a udev problem that I 'fixed' by simply moving the offending rules file to .bak (my problem fil was 51-android.rules).

---

### Post by Gremlyn1 on 2012-04-06
I just tried to fix the install by running the Live USB 12.04, mounting my drive, and using chroot, but all it kept telling me was dpkg stopped due to too many errors. I ran apt-get update/apt-get upgrade/apt-get -f install/apt-get upgrade-dist, nothing would work. Time to partition /home and reinstall. Seems like a good excuse to switch up to 64-bit anyway.

---

### Post by platypeanArccow on 2012-04-08
I don't understand -- how is this "solved"?  The solution is to abandon everything and reinstall?  Is there no hope of a more elegant solution?

---

