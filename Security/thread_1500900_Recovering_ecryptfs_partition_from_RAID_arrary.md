---
title: "Recovering ecryptfs partition from RAID arrary"
date: 2010-06-03
forum: Security
---

### Post by tehschulman on 2010-06-03
After a disastrous upgrade to 10.04 I am at my wits end trying to recover my /home partition from my unbootable system. The /home partition is part of a RAID5 array across 4 disks and I've been trying to use some disk imaging tools from Ultimate Boot CD to recover it with, but none of the utilities seem to recognize or will let me work with my multi-disk device.

Currently I've been booting up with a Live CD in attempts to mount the encrypted partition then copy all the files to an external device I bought, but the mounting process has presented me with some problems. The partition in encrypted with ecryptfs and I have both the disk's passphrase as well as an FNEK signature to work with. Attempting the following:

```

sudo mount -t ecryptfs /dev/md1 /media/md0/home

```

Prompts me for the passphrase and FNEK fine, but after entering the values the mount returns "[-2] No such file or directory". Attempting to mount the /.Private directory from my /home partition returns the same.

Another small issue is the cipher I used. I don't remember which kind of encryption the disk is encrypted with (80% sure it's aes though). I assume figuring out which cipher I used will be more like a guessing game through the ecryptfs mount prompt, but I'm wondering if this would affect the error message I get.

I'm looking for some advice on what steps I can take to diagnose this as well as someone who can help me troubleshoot this so I can recover my work and photographs. If there are any alternative methods for getting the data off these disks too I'm all ears.

---

### Post by bodhi.zazen on 2010-06-03
See if this tutorial helps :

[http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html](http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html)

---

### Post by tehschulman on 2010-06-03
I wish it was that simple. I had tried chrooting into my install before but at the command 'ecryptfs-mount-private' I got the message: 

```

ERROR: Encrypted private directory is not setup properly

```

I had attempted to reinstall my system with the hopes of booting in to it and recovering my files locally but due to booting issues (stupidly had my /boot partition on the same RAID) device as my / partition) I was unable to do this. I'm hesitant to try 'ecryptfs-setup-private' on my new /home directory for fear of locking myself out of my old /home even more but that's the one ecryptfs-utils command I haven't tried playing with yet.

ecryptfs-stat returns:
```
dmschulman@ubuntu:/$ sudo ecryptfs-stat /dev/md127 
ecryptfs_parse_stat: Magic eCryptfs marker not found in header.
Valid eCryptfs metadata information not found in [/dev/md127]

```

THe device should be /dev/md1 but some utility I used under Ultimate Boot CD ended up renaming the device to md127 *shrugs*.

UPDATE: Just tried chrooting into the system and mounting the ecryptfs partition again. If something wrote changes to my /dev/md127 disk I'm going to be very upset, but now when I attempt to mount my disk I get the following:
```

dmschulman@ubuntu:/media$ sudo mount -t ecryptfs /dev/md127 /media/home/

Unable to get the version number of the kernel
module. Please make sure that you have the eCryptfs
kernel module loaded, you have sysfs mounted, and
the sysfs mount point is in /etc/mtab. This is
necessary so that the mount helper knows which 
kernel options are supported.

Make sure that your system is set up to auto-load
your filesystem kernel module on mount.

Enabling passphrase-mode only for now.

Passphrase: 
Select cipher: 
 1) aes: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 2) blowfish: blocksize = 16; min keysize = 16; max keysize = 56 (not loaded)
 3) des3_ede: blocksize = 8; min keysize = 24; max keysize = 24 (not loaded)
 4) twofish: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 5) cast6: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 6) cast5: blocksize = 8; min keysize = 5; max keysize = 16 (not loaded)
Selection [aes]: 
Select key bytes: 
 1) 16
 2) 32
 3) 24
Selection [16]: 
Error attempting to evaluate mount options: [-22] Invalid argument
Check your system logs for details on why this happened.
Try updating your ecryptfs-utils package, and/or
submit a bug report on https://launchpad.net/ecryptfs

```

The mount won't even go past asking for the cipher now??

---

### Post by tehschulman on 2010-06-04
Bump. These errors I'm getting I've never seen before.

---

### Post by bodhi.zazen on 2010-06-04
In the chroot, did you mount /dev , /dev/shm , /proc , /sys as advised ?

---

### Post by tehschulman on 2010-06-04
Yes all those directories are mounted in the chroot environment. Attempting the mount outside of the chroot environment works, but gives me the same No directory found error:

```

ubuntu@ubuntu:/media$ sudo mount -t ecryptfs /dev/md127 /media/private/
Passphrase: 
Select cipher: 
 1) aes: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 2) blowfish: blocksize = 16; min keysize = 16; max keysize = 56 (not loaded)
 3) des3_ede: blocksize = 8; min keysize = 24; max keysize = 24 (not loaded)
 4) twofish: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 5) cast6: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 6) cast5: blocksize = 8; min keysize = 5; max keysize = 16 (not loaded)
Selection [aes]: 
Select key bytes: 
 1) 16
 2) 32
 3) 24
Selection [16]: 
Enable plaintext passthrough (y/n) [n]: 
Enable filename encryption (y/n) [n]: y
Filename Encryption Key (FNEK) Signature [fd617cb3c8d38d99]: a66576095a6e5736
Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_fnek_sig=a66576095a6e5736
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=fd617cb3c8d38d99
WARNING: Based on the contents of [/root/.ecryptfs/sig-cache.txt],
it looks like you have never mounted with this key 
before. This could mean that you have typed your 
passphrase wrong.

Would you like to proceed with the mount (yes/no)? : yes
Would you like to append sig [fd617cb3c8d38d99] to
[/root/.ecryptfs/sig-cache.txt] 
in order to avoid this warning in the future (yes/no)? : yes
Successfully appended new sig to user sig cache file
Error mounting eCryptfs: [-2] No such file or directory
Check your system logs; visit <http://launchpad.net/ecryptfs>

```

Perhaps this message when I begin my mount in the chroot environment is important:

```

dmschulman@ubuntu:/media$ sudo mount -t ecryptfs /dev/md127/ /media/private/

Unable to get the version number of the kernel
module. Please make sure that you have the eCryptfs
kernel module loaded, you have sysfs mounted, and
the sysfs mount point is in /etc/mtab. This is
necessary so that the mount helper knows which 
kernel options are supported.

Make sure that your system is set up to auto-load
your filesystem kernel module on mount.

Enabling passphrase-mode only for now.

Passphrase: 
Select cipher: 

```

---

### Post by bodhi.zazen on 2010-06-04
Your posts are confusing and the likely source of you problems is that you are not following directions.

1. Mount your partition, does not matter where, /mnt is fine.

2. mount those directories in the chroot.

3. chroot into the chroot

4. su to your log in user

5. use ecryptfs-mount-private 

The instructions are laid out, in detail, step by step on the blog, but you are not following them and asking why it is not working.

> ubuntu@ubuntu$ sudo mount /dev/sda1 /mnt[FONT=monospace]
[/FONT]ubuntu@ubuntu$ sudo mount -o bind /dev /mnt/dev
ubuntu@ubuntu$ sudo mount -o bind /dev/shm /mnt/dev/shm[FONT=monospace]
[/FONT]ubuntu@ubuntu$ sudo mount -o bind /proc /mnt/proc[FONT=monospace]
[/FONT]ubuntu@ubuntu$ sudo mount -o bind /sys /mnt/sys[FONT=monospace]
[/FONT]ubuntu@ubuntu$ **sudo chroot /mnt[FONT=monospace]**
[/FONT]root@ubuntu$ **su - kirkland**[FONT=monospace]
[/FONT]kirkland@ubuntu$ **ecryptfs-mount-private**[FONT=monospace]
[/FONT]Enter your login passphrase:[FONT=monospace]
[/FONT]Warning: Using default salt value (undefined in ~/.ecryptfsrc)[FONT=monospace]
[/FONT]Inserted auth tok with sig [xxx] into the user session keyring[FONT=monospace]
[/FONT]kirkland@ubuntu$ cd $HOME[FONT=monospace]
[/FONT]kirkland@ubuntu$ ls -alF[FONT=monospace]
[/FONT]...[FONT=monospace]
[/FONT]kirkland@ubuntu$ cat .profile

Emphasis added my myself.

Where in those comands is there a "sudo mount -t ecryptfs /dev/md127/ /media/private/" ?

---

### Post by tehschulman on 2010-06-04
Using the command 'ecryptfs-mount-private' is not an option for me as I described in my first reply. The system I'm chrooting in to is a fresh install of 10.04, not the initial install where the /home directory was created and encrypted through. Because I can't perform the simple mount operation with 'ecryptfs-mount-private' I am trying to troubleshoot mounting and accessing this drive which would explain my deviating from the tutorial you kindly posted. Again, to be clear:

```

ubuntu@ubuntu:~$ sudo chroot /media/md0
root@ubuntu:/# su - dmschulman
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

dmschulman@ubuntu:/$ ecryptfs-mount-private
ERROR: Encrypted private directory is not setup properly

```

Now then, other tutorials and forum posts I've come across have instructed me to try mounting the /home partition using the traditional mount command specifying the filesystem type as ecryptfs:

```

sudo mount -t ecryptfs /dev/md127/ /media/private/

```

Outside the chroot the command executes fine, but I'm unable to successfully mount and get that "Directory not found" error. When chrooted in the system I get the "Insufficient argument" error which I've never encountered before (I've been able to successfully mount the ~/.Private directory with the above command before, but the file names were all FNEK gibberish which made me assume I wasn't choosing the right cipher). 

The tutorial I've found most helpful so far is at: [http://www.kaijanmaki.net/2009/10/26/recovering-files-from-ecryptfs-encrypted-home/](http://www.kaijanmaki.net/2009/10/26/recovering-files-from-ecryptfs-encrypted-home/) but goes beyond the initial tutorial you've linked me. 

If there's some piece of information I'm missing to make 'ecryptfs-mount-private' work properly then I apologize and hope to figure it out. I do appreciate your help though bodhi.zazen and hope you can help me crack this nut. Thank you, I hope I've explained the situation properly.

---

### Post by FuturePilot on 2010-06-04
AFAIK there's no need to specify -t ecryptfs. This could be the problem. Try mounting it normally.

---

### Post by tehschulman on 2010-06-04
Well, I can mount the drive as a block device using the mount command without specifying the filesystem type, but when I try to access the mounted directory I am locked out. Same goes for sudo, and oddly enough I tried launching nautilus as sudo in the mounted directory and nautilus crashed with the error:

```

(nautilus:12716): Eel-WARNING **: GConf error:
  Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-Sl5bCuuqHm: Connection refused)

```

Mounting the disk and subsequently using 'ecryptfs-mount-private' returns the same error as before for obvious reasons. How else could I go about accessing the encrypted directory if I've mounted the disk as you described?

---

### Post by Mister.Vash on 2010-06-04
The error that jumps out at me is the:

**"Error mounting eCryptfs: [-2] No such file or directory"**

which was generated from the code
```
sudo mount -t ecryptfs /dev/md127 /media/private/
```

can you make sure that both the /dev/md127 and /media/private folder exist?
if the /media/private doesn't exist, create it as that is the destination, should be no harm doing that.   If the /dev/m127 doesn't exist it might be still listed as the /dev/md1 - if 'you don't find either, you'll have to figure out what the source is listed as.

Here is the item from the ecryptfs faq about that error [http://ecryptfs.sourceforge.net/ecryptfs-faq.html#baddir](http://ecryptfs.sourceforge.net/ecryptfs-faq.html#baddir)

Check that out, let us know, and report any other errors after that.

---

### Post by tehschulman on 2010-06-06
After running mdadm:

```

sudo mdadm --assemble --scan

```

mdadm reports the following exist:
/dev/md0
/dev/md1
/dev/md127

When I first get into the Live CD environment I use 'sudo mkdir' to create a couple of different directories in /media as various mounting points:
/media/md0/
/media/md1/
/media/md127/
/media/home/
/media/private/

Trying to use the destination as any one of these in the LiveCD environment gives me the "Error mounting eCryptfs: [-2] No such file or directory" despite me having "created" them in the / directory of the LiveCD.

After stopping the RAID devices and remounting them in Nautilus (just having Nautilus recognizing them as devices mind you) the /dev/md127 device seemed to go away, /dev/ containing only /dev/md0 and /dev/md1 now.

**A little bit of minor success.** Instead of getting "Error mounting eCryptfs: [-2] No such file or directory" now when attempting to mount the device,
```

ubuntu@ubuntu:~$ sudo mount -t ecryptfs /dev/md1/ /media/md1/
Passphrase: 
Select cipher: 
 1) aes: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 2) blowfish: blocksize = 16; min keysize = 16; max keysize = 56 (not loaded)
 3) des3_ede: blocksize = 8; min keysize = 24; max keysize = 24 (not loaded)
 4) twofish: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 5) cast6: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 6) cast5: blocksize = 8; min keysize = 5; max keysize = 16 (not loaded)
Selection [aes]: 
Select key bytes: 
 1) 16
 2) 32
 3) 24
Selection [16]: 3
Enable plaintext passthrough (y/n) [n]: 
Enable filename encryption (y/n) [n]: y
Filename Encryption Key (FNEK) Signature [fd617cb3c8d38d99]: a66576095a6e5736
Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_fnek_sig=a66576095a6e5736
  ecryptfs_key_bytes=24
  ecryptfs_cipher=aes
  ecryptfs_sig=fd617cb3c8d38d99
Error mounting eCryptfs: [-20] Not a directory
Check your system logs; visit <http://launchpad.net/ecryptfs>
ubuntu@ubuntu:~$

```

I was forgetting to run 'ecryptfs-add-passphrase --fnek' to add my keyring to the LiveCD environment, needs to be there every time you reboot despite never changing since it's based off your passphrase. After looking through 'dmesg' I saw the keys were not being recognized by the mount. Now the error to contend with is **"Error mounting eCryptfs: [-20] Not a directory"** which sounds a little more ominous to me.

dmesg output after attempting the mount:
```

[11379.811834] ecryptfs_read_super: path_lookup() failed
[11379.811842] Reading sb failed; rc = [-20]

```

"Not a directory" suggests to me that there are problems with the partition now, but having never formatted the disks on /dev/md1 or written/overwritten data to the partitions (when reinstalling the system or otherwise) I have faith things are still recoverable. Is this the case?

---

### Post by tehschulman on 2010-06-08
Bump, very close to diagnosing this!

---

### Post by tehschulman on 2010-06-09
Ok well it looks like I need to use some of the fsck tools to recover/rebuild/delete the superblock on my disks or diagnose it to the point where the disks can be mounted properly. Can someone advise me on how to go about rebuilding my superblock on the ecryptfs partition properly? I assume I just need to run this command on each of the disks in the multi-disk device and I should be good.

---

### Post by bodhi.zazen on 2010-06-09
Honestly, I have no idea what you are trying to accomplish.

In your first post you seemed to be attempting to recover old encrypted data from an old installation :

> ... trying to recover my /home partition from my unbootable system ...

But later you state it is a fresh install 

> The system I'm chrooting in to is a fresh install of 10.04 ...

There is no data to recover in a fresh install.

You would need to chroot into the old installation.

---

### Post by tehschulman on 2010-06-09
I am trying to recover the information on the device /dev/md1 which is encrypted with ecryptfs and has a bad superblock. Everything I've tried and have been doing with this has been in an effort to mount the disk and recover the data from /dev/md1.

I am keeping a log of the research and progress I'm making with my error messages on this thread so that when people in a similar situation google these errors and possible come across this thread they will have some direction to follow with fixing their problems.

Should I just make a new thread or can you assist me with understanding how I can fix the superblock error? Thanks.

---

