---
title: "How can I mount the truecrypt flashdrive file system as read/write?"
date: 2013-04-27
forum: Security
---

### Post by scruffyeagle on 2013-04-27
I find it very frustrating, that the only time I can write & modify files on a truecrypt flashdrive volume, is right after I make it. The very next time it gets plugged in, it's READ-ONLY!!! Take it anywhere, and it will only mount read-only! This sucks.

I've been searching for the past hour, and can't find an answer for this. The results from the search engine are almost entirely how to make a flashdrive formatted w/ truecrypt. (DUH! You can do that? Thanks for telling me over & over!) But, I did find one page (at [http://justbored.wordpress.com/2007/12/26/how-to-mount-a-truecrypt-volume-in-linuxubuntu/]("http://justbored.wordpress.com/2007/12/26/how-to-mount-a-truecrypt-volume-in-linuxubuntu/") with a topic of making a truecrypt flashdrive read-only file system become read/write. Unfortunately, it's not very clear, as if the writer skipped specifying steps & conditions necessary for doing it.

I have more than one Ubuntu machine, and I want to be able to read, write to, & delete from the encrypted flashdrive regardless of which machine I'm currently plugging it into; i.e., using the volume the way I'd use any normal truecrypt volume on a hard drive. (Isn't the purpose of a flashdrive to create portability for files?) If I can't write files to the drive, it can't fulfill its function!

Any gurus out there with an answer for how to fix this problem?

---

### Post by clearski on 2013-04-27
I've just finished backing up some files from an internal hdd to an encrypted TrueCrypt containter on a removable media.

Here's how I mount and access my drive. First of all make sure you have a directory in your /media which you can point to when you mount the external device.

Ex:

```

mkdir /media/stick #or name it whatever you like

```

Then

```
sudo fdisk -l #I got the device ID, in my case is /dev/sdb1
sudo mount /dev/sdb1 /media/stick -o gid=1000,uid=1000,utf8 #this mounts the drive with regular user permissions, not restrictive

```

After that, my removable media is mounted in /media/stick, so I'm using TrueCrypt to access the container in that location (the container was created as a regular user, so it has 755 permissions). After providing password/keys etc, it mounts the container in /media/truecrypt5 and I do all my backups there. After that, I close the container, quit Truecrypt, unmount & eject the removable media.

```
sudo umount /dev/sdb1
sudo eject /dev/sdb1
```

Hope this helps.

---

### Post by scruffyeagle on 2013-04-29
Thank you, clearski! That seems very detailed & straight-forward. I'll try to put your instructions into use, the next chance I get.

I'll come back here for at least one more visit to this thread, regardless of the outcome. If it works as we hope, I'll be marking the thread "solved". If it doesn't, well, I'll be posting that fact and requesting help to discover what went wrong.

---

### Post by scruffyeagle on 2013-06-21
Well, I finally got back to this.  I did as instructed, and created a new directory named "/media/flashdrive". With a flashdrive inserted, it becomes "sdc" on my Ubuntu v10.04 OS. I entered the command:

```
sudo mount /dev/sdc /media/flashdrive -o gid=1000,uid=1000,utf8
```

The system replied:
"mount: you must specify the filesystem type"

I'm not sure what to try next.  The drive I'm trying to mount was encrypted as an entire drive, not as a file container stored in some partition's filing system like ext4, etc.  (I'm also fairly sure that I formatted it as NTFS, so I could also access it in Windows systems.  Replacing "utf8" w/ "ntfs" &/or "NTFS" produced the same result.)  When I tried via mounting it into TrueCrypt first, the terminal response told me it couldn't do it because the drive was already mounted.

Any suggestions re. what to try next?

---

### Post by zacktu on 2013-06-21
Dunno what I did differently at setup, but it didn't require any use of the command line.  I would 1) insert the flashdrive; 2) start truecrypt; 3) select a slot (say 5); 4) select "Auto-Mount Devices"; and 5) enter the TrueCrypt password.  My recollection is that the flashdrive would then be mounted as /media/truecrypt5.  When finished I would select Dismount All and Exit.

---

