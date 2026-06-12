---
title: "HOWTO: Automatically unlock LUKS encrypted drives with a keyfile"
date: 2008-06-22
forum: Tutorials
---

### Post by hyper_ch on 2008-06-22
[SIZE="6"]HOWTO: Automatically unlock LUKS encrypted drives with a keyfile[/SIZE]

[SIZE="5"]Introduction[/SIZE]

Well, I have written so far two tutorials with LUKS/dm_crypt involved. First one was how to enable encryption on Feisty Fawn (wasn't included back then by default) and the other one was how to reboot/unlock through a remote connection.

This howto was then written because of a question in the second howto. The problem there was how to unlock multiple devices in the intial ramdisk remotely. I suggested instead to use a keyfile for automatic unlocking. The keyfile should be stored in the normally encrypted root partition - so you still have to unlock that one. During boot process it will then be used to unlock all the other devices.

Of course one could also use an encrypted LVM so that all space is encrypted but only one password is required. I have not seen a usage for LVM so far and it seems, that others do not also but prefer to have individual encrypted devices. That way you could easily move an encrypted harddisk to another computer. I'm not sure if that works with LVM encrypted drives also because I have no experience with it.

One might ask how secure is this setup? I'd say pretty safe. During this howto the keyfile will be made read-only to root. So, if someone can access the keyfile you have more serious problems anyway on your computer.

[SIZE="5"]Step 1: Create a random keyfile[/SIZE]

```

sudo dd if=/dev/urandom of=/root/keyfile bs=1024 count=4

```
This will create a file with random content with the size of 4096 bits (better than a 20/30 character password....). You can use any file to act as keyfile but I think a 4kb file with random content is good suited.

[SIZE="5"]Step 2: Make the keyfile read-only to root[/SIZE]

```

sudo chmod 0400 /root/keyfile

```
That will make the keyfile readable only by root. If someone get access to this keyfile, then you have a bigger problem on your computer anyway. 

Alternatively chown your desired keyfile to root:root and move it into the /root folder.

[SIZE="5"]Step 3: Add the keyfile to LUKS[/SIZE]

LUKS/dm_crypt enabled devices may hold up to 10 different keyfiles/passwords. So, next to having the already setup password we're going to add this keyfile as additional authorization method.

```

sudo cryptsetup luksAddKey /dev/sdX /root/keyfile

```

sdX is of course your LUKS device.

First you'll be prompted to enter an (existing) password to unlock the drive. If everything works well, you should get an output like this:
> 
Enter any LUKS passphrase:
key slot 0 unlocked.
Command successful. 


[SIZE="5"]Step 4: Create a mapper[/SIZE]

LUKS devices need to create a mapper that can then be referenced in the fstab. Open /etc/crypttab

```

sudo nano /etc/crypttab

```

and add then a line like this (or replace the existing one for that partition)

```

sdX_crypt      /dev/sdX  /root/keyfile  luks

```

or you can use the UUID of the device

```

sdX_crypt      /dev/disk/by-uuid/247ad289-dbe5-4419-9965-e3cd30f0b080  /root/keyfile  luks

```

sdX_crypt is the name of the mapper that is being created. You can use here any name e.g. "music" or "movies" or "sfdsfawe" ....

Save and close the file by issuing ctrl-x, enter, enter. Ctrl-x closes nano but first it asks to save the file [yes = enter] and what the name shall be [same name = enter].

What we have done there actually is telling that /root/keyfile shall be used instead of password entry to unlock the drive.

[SIZE="5"]Step 5: Mount the device in fstab[/SIZE]

Now, we have an unlocked device (well, not yet but when the system is being booted up) and we just need to mount it now. Open /etc/fstab

```

sudo nano /etc/fstab

```

and add a new entry like

```

/dev/mapper/sdX_crypt  /media/sdX     ext3    defaults        0       2

```

Make sure you have the correct mapper name that you added in step 4. Also make sure that the mount point/folder exists. After having added it, save again the file and close it (ctrl-x, enter, enter).

[SIZE="5"]Step 6: Reboot or remount[/SIZE]

That's it. Now you can reboot and the additional devices should be auto-unlocked and mounted. You can also test it by remounting all devices

```

sudo mount -a

```

---

### Post by sirlancelot on 2009-04-28
This is an awesome walkthrough. I'm curious about one thing though.

I want to be able to store the key on a USB drive. I use a USB drive as my /boot partition so I can just remove it and take it with me when I don't want anyone to boot my computer (It also makes backing up that much easier).

My first thought was to place the key in the /boot folder so that it would travel safely with me. However, during the boot process, I guess /boot isn't mounted and so crypttab is pointing to a key file that doesn't exist.

Is there any way I can achieve this setup?

I would like to have the key file stored a USB drive that I can take with me.

Thanks.

---

### Post by WilliamThrilliam on 2009-06-16
OOOK, So I'm trying to do this for my SWAP and Home directory, while the key file is loaded on a USB drive.  It no worky.  I think it may be the order in which my fstab is setup?  I also read somewhere that I might have to run a script so that it will wait for my USB drive to mount before it tries to retrieve the key?  Anyone?

---

### Post by WilliamThrilliam on 2009-06-16
> **WilliamThrilliam said:**
> OOOK, So I'm trying to do this for my SWAP and Home directory, while the key file is loaded on a USB drive.  It no worky.  I think it may be the order in which my fstab is setup?  I also read somewhere that I might have to run a script so that it will wait for my USB drive to mount before it tries to retrieve the key?  Anyone?


Neve mind, found My answer here: [http://www.debianhelp.org/node/6797]("http://www.debianhelp.org/node/6797")

Seems like I needed to direct /etc/default/cryptdisks to my usb drive.

---

### Post by lucmv on 2009-08-27
Hello. Is anyone still reading this thread? I just followed the instructions and they didn't work for me. Here is a copy of my crypttab file:

# <target name>	<source device>	<key file>	<options>
swap_crypt	/dev/sda4	none		swap
home_crypt	/dev/sda5	none		luks
extra_crypt	/dev/sdb1	/home/luc/keyfile	luks

Relevant lines in my fstab:

/dev/mapper/swap_crypt   swap    swap    defaults    0  0
/dev/mapper/home_crypt   /home   ext3    defaults    1  2
/dev/mapper/extra_crypt  /extra ext3    defaults    1  2

During boot, I am prompted to enter a password... for the swap partition! Why??? I just hit Enter and it works fine, but that extra password prompt is annoying.

Then I am prompted to enter the password for my home partition. That's expected, because the key file is in my home partition.

Then the whole system halts and offers me the choice to enter root password to "fix" the problem or hit CTRL-D to bail out. Scrolling up, I can see messages complaining that the key file could not be found, so extra_crypt can't be decrypted. But it's there. The system probably doesn't have time to mount the /home partition before luks attempts to decrypt the other partition.

Can anyone help me out here? TIA.

---

### Post by lucmv on 2009-08-28
OK, I have solved it:

# <target name> <source device>     <key file>  <options>
swap_crypt   /dev/sda4       /dev/random         swap
home_crypt   /dev/sda5       none                luks
extra_crypt  /dev/sdb1       /home/luc/keyfile   luks

Also, I had forgotten to run luksAddKey to add the keyfile. Shame on me.  :-(

---

### Post by iq00 on 2009-11-13
hey!  this how-to works for me! thx to the author!  i've got one more question: is there any solution to put the keyfile in /home? in my case, /root is plain and NOT crypted, so its vulnerable. /home is being mounted by passphrase only!  i'd like to mount /home at first and THEN mount my other crypted partitions like /var and /tmp by reading the key from the mounted /home.  the problem is: luks seems trying to mount all partitions at once.   thx 4 ur help!

---

### Post by sirlancelot on 2009-11-16
> **iq00 said:**
> i'd like to mount /home at first and THEN mount my other crypted partitions like /var and /tmp by reading the key from the mounted /home.  the problem is: luks seems trying to mount all partitions at once.   thx 4 ur help!

Open up `/etc/default/cryptdisks` and on the `CRYPTDISKS_MOUNT=""` line, put this:

```
CRYPTDISKS_MOUNT="/home"
```

---

### Post by iq00 on 2009-11-18
hey! thanks for your help! i tried that but it doesn't work here. the boot process doesn't continue at all when it has to read the keyfile from /home.  maybe there's another issue according to some karmic problems by mounting cryptsetup-devices.  i even can't find anything in the syslog that might give any hint to what's really broken.  any further tips 4 me? :-\

---

### Post by foxterrier24 on 2009-11-22
hello, 
I would like to ask another question.  
one of my pc has all partition (exept /boot) crypte.  Then, at boot time, passphrase is asked immediatly, after 1 or 2 second.
My problem is the following : i would like to remove temporary this password (auto answer to passphrase).
i know, it's a big security hole, but this pc is remote and random reboot. then, in waiting to find a solution, i prefer auto passphrase (with key file ?) than each time move to this pc (3 hours).
Any idea to help me ? 
thanks !

---

### Post by sirlancelot on 2009-11-23
> **iq00 said:**
> hey! thanks for your help! i tried that but it doesn't work here. the boot process doesn't continue at all when it has to read the keyfile from /home.  maybe there's another issue according to some karmic problems by mounting cryptsetup-devices.  i even can't find anything in the syslog that might give any hint to what's really broken.  any further tips 4 me? :-\

iq00, what does your [FONT="Courier New"]/etc/crypttab[/FONT] file look like?

---

### Post by iq00 on 2009-12-05
hey! thanks for your attention, but i solved solved the issue by reinstalling ubuntu. now, i have crypted the whole lvm, so the password hast to be entered only once at boot.  bye

---

### Post by tertore on 2012-07-10
> **foxterrier24 said:**
> hello, 
I would like to ask another question.  
one of my pc has all partition (exept /boot) crypte.  Then, at boot time, passphrase is asked immediatly, after 1 or 2 second.
My problem is the following : i would like to remove temporary this password (auto answer to passphrase).
i know, it's a big security hole, but this pc is remote and random reboot. then, in waiting to find a solution, i prefer auto passphrase (with key file ?) than each time move to this pc (3 hours).
Any idea to help me ? 
thanks !

Hello dears, I have the same enquiry...
It is very important for me to be able to remote reboot the system, without insert the passphrase. In the same time, I would to preserve my datas in case of my hard disk is stolen.
It is possible?
Foxterrier24, have you found any solution?

thanks, Andrea

---

