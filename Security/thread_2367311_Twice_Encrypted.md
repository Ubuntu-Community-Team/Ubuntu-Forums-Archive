---
title: "Twice Encrypted"
date: 2017-07-28
forum: Security
---

### Post by Mark_in_Hollywood on 2017-07-28
I installed 16.04.2 on a bare silicon ssd. I selected the stock (standard) encryption method at boot time. At the time of installation, I had an unencrypted backup of /home from on an external sata hdd. (I used Ubuntu's "Backups" for backup. The only password is the power up time password).

After rebooting the clean install, I tried to restore the /home. Something went amiss. To safeguard the data I powered off the external drive. In trying to fix the problem, I bricked the ssd. 

Upon re-installing a new bare silicon ssd, and then re-installing 16.04.2 and selecting the same encryption scheme as before, I now find that I cannot unlock (unwrap is it?) the /home on the external device. 

My guess is that it is now twice encrypted. I have both 32 character wide passphrases. The Access Private Data icon on the external device runs, but does not unencrypt.

At various times I have received the following terminal messages:
---
ERROR: Encrypted private directory is not setup properly

Passphrase: 
Inserted auth tok with sig [de0357543abe6969] into the user session keyring
Inserted auth tok with sig [8a0b80df2b4e58a7] into the user session keyring

Enter your login passphrase:
Inserted auth tok with sig [de0357543abe6969] into the user session keyring
fopen: No such file or directory

Error attempting to find auth tok for fnek sig
---

In LiveISO I've not been able to do much with the external drive. Dustin Kirkland's [How To]("http://blog.dustinkirkland.com/2011/04/introducing-ecryptfs-recover-private.html") on Recovery won't work in my LiveISO of 16.04.2.

Is there a way to fix this? Is it possible to make a copy of what is on the external drive so as to make a safe copy, even if it's encrypted? I looked at Clonezilla's. LiveISO but the language they were using made me nervous. I know that Clonezilla will use the *dd[I]* command and the clone would go from a 2T to a 1T drive. A no-go.

Resources Consulted: 

[https://superuser.com/questions/227713/ecryptfs-how-to-mount-a-backup-of-an-encrypted-home-dir](https://superuser.com/questions/227713/ecryptfs-how-to-mount-a-backup-of-an-encrypted-home-dir)

[http://deferred.io/posts/2013/01/06/recovering-ecryptfs-home-dir.html](http://deferred.io/posts/2013/01/06/recovering-ecryptfs-home-dir.html)

[https://askubuntu.com/questions/39753/recovering-from-a-move-of-home-when-its-encrypted-ecryptfs?rq=1](https://askubuntu.com/questions/39753/recovering-from-a-move-of-home-when-its-encrypted-ecryptfs?rq=1)

---

### Post by deadflowr on 2017-07-29
To clarify everything, only home is encrypted and not home and full disk encryption?
Just to make sure that full disk encryption isn't involved.
Which would add another level of complexity to it all if full disk encryption was used.

---

### Post by Mark_in_Hollywood on 2017-07-30
"Full disk encryption"? I don't know. What I did, was at the installation of 16.04.2 choose 

"Encrypt the new Ubuntu installation for security" 

a sample screenshot is attached. It shows a different method used.

I chose the second method from the top in the screenshot.

Thank you.

---

### Post by sudodus on 2017-07-30
If you tick the box for 'Encrypt the new Ubuntu installation for security' you install with 'LVM with encryption' alias 'encrypted disk' which is another method than 'encrypted home'. (You can use both methods in the same system if you wish.)

---

### Post by Mark_in_Hollywood on 2017-07-30
sudodus, please see post #1, above.

---

### Post by sudodus on 2017-07-31
I am not sure what you mean by

> I selected the stock (standard) encryption method at boot time.

Was this selected by ticking the box for 'Encrypt the new Ubuntu installation for security' during installation?

Is this the only way you selected encryption? In this case it is 'LVM with encryption' alias 'encrypted disk', and I cannot see why there would be double encryption.

It should be possible to 'open' by entering the passphrase and even change the passphrase, if you boot from another drive, for example a live Ubuntu system, and use **Disks** alias **gnome-disks**. Select the encrypted partition and right-click ...

---

### Post by Mark_in_Hollywood on 2017-07-31
"Was this selected by ticking the box for 'Encrypt the new Ubuntu installation for security' during installation?" **YES**.

No other method was used. Not during the installation nor after. The backup (using Ubuntu's "Backups") is encrypted on an external hard drive.

On the external drive holding the backup of /home, the icon in the drive does not unwrap. The passphrase once entered manually does not seem to unlock, as the files continue to show as encrypted. That is because the drive's files were part of an earlier encrypted OS (still 16.04.2), but a different drive. Once the first "Backups" became encrypted, the drive with 16.04.2 failed and when I replaced it, I added encryption. I call this problem, double encryption. I know no name for it.

I will say that I am noobie enough at this to not know whether files with names like ENCRYPTFS_FNEK are or are not still encrypted, but if they are unencrypted, do I run the "Restore" from Ubuntu's "Backups" to restore /home, as it requires my system password, not the encryption passphrase?

---

### Post by deadflowr on 2017-07-31
Okay, then this is a full disk encryption then.
Take a quick look at this:
[https://alvinabad.wordpress.com/2012/09/22/how-to-recover-a-luks-encrypted-disk/]("https://alvinabad.wordpress.com/2012/09/22/how-to-recover-a-luks-encrypted-disk/")
see if that gets you anywhere.

---

### Post by Mark_in_Hollywood on 2017-08-03
I read the post you supplied and am still researching. Please bear with me. I'm going slow to trying to get it all lined up properly before running commands.

1 - is the encryption used by Ubuntu: LUKS, dm-crypt, others? I wouldn't need to ask this but for the fact that there seem to be multiple partition schemes for encryption and as yet, I cannot know the right keywords to search to find similar problems as mine.

To recap:

2 - my /home is on an external drive. I think it's a partition, which due to what I blew up (1st ssd) is seen by 2nd ssd as encrypted. Does the unencryption unwrap on an external drive? That is, is this even possible? How did the data (or partition as it appears in fdisk -l get encrypted? I understand that the boot device (/dev/sda1) is encrypted.

3 - Can the encryption on the 2nd ssd be removed and will that help to recover the data on the external sata? 

4 - If the /sdc1 does not show as encrypted why? Nautilus shows a .encryptfs. Since I see /sdb as "crypt" how do I know what to do to unwrap (unlock) the /sdc (which is an external sata drive).

```
mark@Lexington:/$ sudo lsblk
[sudo] password for mark: 
NAME   MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sdb      8:16   0 232.9G  0 disk  
&#9500;&#9472;sdb2   8:18   0     1K  0 part  
&#9500;&#9472;sdb5   8:21   0   7.5G  0 part  
&#9474; &#9492;&#9472;cryptswap1
&#9474;      253:0    0   7.5G  0 crypt [SWAP]
&#9500;&#9472;sdb3   8:19   0 215.2G  0 part  
&#9492;&#9472;sdb1   8:17   0  10.2G  0 part  /
sr0     11:0    1  1024M  0 rom   
sdc      8:32   0   1.8T  0 disk  
&#9492;&#9472;sdc1   8:33   0   1.8T  0 part  
sda      8:0    1   7.5G  0 disk  
&#9492;&#9472;sda1   8:1    1   7.5G  0 part  /media/mark/cb49282a-b3f8-4f20-8f78-caccac9ae5
```

Please forgive my ignorance and fear of harming that data as it's 10 years worth of /home.

Resources consulted:

[Encrypted external drive with LUKS]("https://www.loganmarchione.com/2015/05/encrypted-external-drive-with-luks/")

---

### Post by Mark_in_Hollywood on 2017-08-07
Per: [Recover a LUKS Encrypted Disk Alvin Abad]("https://alvinabad.wordpress.com/2012/09/22/how-to-recover-a-luks-encrypted-disk/")


```
mark@Lexington:~$ sudo fdisk -l

Disk /dev/sdc: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 0C16BB68-9E62-466E-8BEB-E2655D8EE7AF


mark@Lexington:/$ cryptsetup -v luksDump /dev/sda5
Device /dev/sda5 doesn't exist or access denied.
Command failed with code 15: Device /dev/sda5 doesn't exist or access denied.
```

The remainder of the commands at the How to Recover a LUKS Encrypted Disk also show nothing.

I tried [Mount LVM encrypted partition on external HDD - Device /dev/sdc5 is not a valid LUKS device]("https://askubuntu.com/questions/309124/mount-lvm-encrypted-partition-on-external-hdd-device-dev-sdc5-is-not-a-valid")

but ```
root@Lexington:/# modprobe dm-mod
``` returned nothing.

==========

[Trying to mount old encrypted home]("https://askubuntu.com/questions/36573/trying-to-mount-old-encrypted-home")

mark@Lexington:/$ sudo ecryptfs-add-passphrase --fnek
[sudo] password for mark: 
Passphrase: 
Inserted auth tok with sig [de0357543abe6969] into the user session keyring
Inserted auth tok with sig [8a0b80df2b4e58a7] into the user session keyring

when I go further following the above:

" There, I remember bbbbbbbbbbbbbbbb and proceed with mounting the associated .Private directory:

sudo mount -t ecryptfs /mnt/oldhome/.ecryptfs/me/.Private /mnt/oldme "


but I'm trying to recover a backup of /home that was on an earlier luks-encrypted device. I next see:

```
 mark@Lexington:/$ sudo mount -t ecryptfs /mnt/oldhome/.ecryptfs/me/.Private /mnt/oldme
Passphrase: 
Select cipher: 
 1) aes: blocksize = 16; min keysize = 16; max keysize = 32
 2) blowfish: blocksize = 8; min keysize = 16; max keysize = 56
 3) des3_ede: blocksize = 8; min keysize = 24; max keysize = 24
 4) twofish: blocksize = 16; min keysize = 16; max keysize = 32
 5) cast6: blocksize = 16; min keysize = 16; max keysize = 32
 6) cast5: blocksize = 8; min keysize = 5; max keysize = 16
```

so I have no idea of what-is-what here. My goal is to unwrap (unlock?) the data and keep it that way so that using Ubuntu's "Backups" the files can be 
"Restored" to a /home (/dev/sdaX).

---

