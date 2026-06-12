---
title: "Can't access LUKS /home &quot;No key available with this passphrase&quot;"
date: 2008-10-30
forum: Security
---

### Post by durruti36 on 2008-10-30
OK folks, I'm in trouble, big trouble and if anyone has any advice I would really appreciate it.

**Situation**
I've had an encrypted /home partition since gutsy and was able to successfully upgrade to hardy some months ago. This morning when I enter my passphrase I get the error message "Command failed: No key available for this passphrase". I know that the passphrase is correct as it has been my primary machine for the last year. The only notable since the last successful login was an update of gvfs through update manager (from proposed - which I know might be a bad idea), I don't know if this is related.

**What I have tried so far**
[LIST=1]
[*]Booted from a liveCD (intrepid RC) and run the following:
```

sudo su  
apt-get install lvm2 cryptsetup
mkdir /media/test
modprobe dm-crypt
cryptsetup luksOpen /dev/sda3 test

```
[*]Checked it's not a keyboard problem using gedit and also copying and pasting.
[/LIST]

**Complicating factors**
[LIST=1]
[*]I have previously setup "Boot up manager (bum)" to show grub options for 0 seconds, pressing esc or down-arrow on bootup doesn't give me access to grub menu. Therefore I am not able to try it with an older kernel (although as I say we have not had an update for a while and it was functioning perfectly till this morning.
[*]The server I was using to do my backup's has had a problem with mounting usb drives, that I had not noticed. i.e I HAVE NO BACKUP! I know this is my own fault, as I've lectured a thousand clients but it does make it even more important for me to find a solution if one exists.
[/LIST]

Could it be a disk issue? Is there any point running something like spinrite on the disk? Should I try doing a "repair existing system" from a live CD? Any opinions or suggests very gratefully received! 

My virtual life is in your hands!

**UPDATE**
Not sure if this is any use (I can't make much use of it), but when I run the following command on the 8.04.1 live disk: 
```
cryptsetup luksDump /dev/sda3
```
I get the the following response
```
root@ubuntu:/home/ubuntu# cryptsetup luksDump /dev/sda3
LUKS header information for /dev/sda3

Version:       	1
Cipher name:   	aes
Cipher mode:   	cbc-essiv:sha256
Hash spec:     	sha1
Payload offset:	1032
MK bits:       	128
MK digest:     	05 9e a4 82 6c 5d c4 48 72 9a 35 bf b0 26 5f 2b d7 c0 48 d4 
MK salt:       	be ae 73 a0 18 fa 34 02 11 ef df aa 75 8f e7 15 
               	9a 7c 31 67 a5 16 86 ef 99 ad 2e c2 de e8 90 1c 
MK iterations: 	10
UUID:          	d91087a9-8f41-4411-b395-7b1a02e318ce

Key Slot 0: ENABLED
	Iterations:         	124301
	Salt:               	2c 4c 4e 1c fd c4 42 1b d6 d3 8a 2a 12 22 98 26 
	                      	80 f3 fe 1d 1f 26 3b 6a 39 4e 3e 3a ab 5d bd 42 
	Key material offset:	8
	AF stripes:            	4000
Key Slot 1: DISABLED
Key Slot 2: DISABLED
Key Slot 3: DISABLED
Key Slot 4: DISABLED
Key Slot 5: DISABLED
Key Slot 6: DISABLED
Key Slot 7: DISABLED

```

---

### Post by Gamma746 on 2008-10-30
> **durruti36 said:**
> [LIST=1]
[*]I have previously setup "Boot up manager (bum)" to show grub options for 0 seconds, pressing esc or down-arrow on bootup doesn't give me access to grub menu. Therefore I am not able to try it with an older kernel (although as I say we have not had an update for a while and it was functioning perfectly till this morning.
[/LIST]

Boot off a CD, mount your / or /boot partition, edit /boot/grub/grub.conf and set timeout to 30.  Then try an older kernel.

> **durruti36 said:**
> Could it be a disk issue? Is there any point running something like spinrite on the disk? Should I try doing a "repair existing system" from a live CD? Any opinions or suggests very gratefully received! 

From a CD, run ```
 cat /dev/foo > /dev/null
```(Replace foo with your drive (e.g. /dev/sda))  If you see any errors, then your drive is broken and your data is probably gone forever.

And if you do manage to recover your data, I hope you'll start taking backups! ;)

---

### Post by hyper_ch on 2008-10-30
LVM encrypted drives are somewhat a pain.

Maybe this gives some help:  [http://www.howtoforge.com/encrypted-root-lvm](http://www.howtoforge.com/encrypted-root-lvm)

---

### Post by Hutongs79 on 2008-10-31
bump the thread up.cheap wow power leveling (World of warcraft Power Leveling):**buy [WoW Power Leveling](http://www.igsstar.com),  cheap [world of warcraft power leveling](http://www.igsstar.com/wow-powerleveling-us/) , 1-80 level [wow Power Leveling](http://www.wowgoldweb.com),[maple story mesos](http://www.buymsmesos.com),       [wedding invitations](http://www.vponsale.com/invitations/)**

---

### Post by ekh on 2008-11-01
Having no backup on a disk with important data currently not accessible, I would start getting an identical hard disk and do a verbatim copy with dd.

If some recovery procedure fails on the copy and destroys the data, just make a new copy of the original, and hopefully you eventually get everything right and recover your data.

Experimenting with the original, you have to do everything right the first time.

---

### Post by hyper_ch on 2008-11-02
> **ekh said:**
> Having no backup on a disk

That should never be the case - regardless of what you do.

---

