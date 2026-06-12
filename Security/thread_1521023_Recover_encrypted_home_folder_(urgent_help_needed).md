---
title: "Recover encrypted home folder (urgent help needed)"
date: 2010-06-30
forum: Security
---

### Post by cra1g321 on 2010-06-30
hey i need help recovering a encrypted home folder from a ubuntu 10.04 partition. i am unable to boot the ubuntu partition :( so i will be using a linux mint live cd to try and recover the folder. Really need this recovered as it contains all my files (photos, videos, documents) and me being a noob i 4got to make any backups  :x 
i remember the username and password and have recorded the passphrase as well on a usb drive. I want to recover the home folder then copy/move it onto a external hard drive. 
ive tried a few tutorials but no luck so far.

---

### Post by cra1g321 on 2010-06-30
hey i need help recovering a encrypted home folder from a ubuntu 10.04  partition. i am unable to boot the ubuntu partition [IMG]http://forums.linuxmint.com/images/smilies/icon_sad.gif[/IMG] so i will be using a linux mint live cd to try and recover  the folder. Really need this recovered as it contains all my files  (photos, videos, documents) and me being a noob i 4got to make any  backups  [IMG]http://forums.linuxmint.com/images/smilies/icon_mad.gif[/IMG] 
i remeber the username and password and have recorded  the passphrase as well on a usb drive. I want to recover the home folder  then copy/move it onto a external hard drive. 
ive tried a few  tutorials but no luck so far.

---

### Post by Bachstelze on 2010-06-30
This worked for me just a couple days ago:

[https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering%20Your%20Data%20Manually](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering%20Your%20Data%20Manually)

Have you tried it? If so, which step didn't work?

---

### Post by cra1g321 on 2010-06-30
kk i will try them on within the live cd.

---

### Post by dino99 on 2010-06-30
[https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)

[http://www.kaijanmaki.net/2009/10/26/recovering-files-from-ecryptfs-encrypted-home/](http://www.kaijanmaki.net/2009/10/26/recovering-files-from-ecryptfs-encrypted-home/)

follow this example to chroot from a live cd

[http://ubuntuforums.org/showthread.php?t=1263030&page=2](http://ubuntuforums.org/showthread.php?t=1263030&page=2)

---

### Post by cra1g321 on 2010-06-30
I tried this but get an error. heres a complete copy of the terminal if it gives you a easier understanding. the Home fodler in on sda1 so maybe i need to mount it or something im thinking.

mint@mint ~ $ sudo ecryptfs-add-passphrase --fnek
Passphrase: 
Inserted auth tok with sig [9c8e941b757f9f5a] into the user session keyring
Inserted auth tok with sig [28ad40928bf45d59] into the user session keyring
mint@mint ~ $ sudo mount -t ecryptfs /home/cra1g321/.Private /home/cra1g321/Private
Passphrase: 
Select cipher: 
 1) aes: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 2) blowfish: blocksize = 16; min keysize = 16; max keysize = 56 (not loaded)
 3) des3_ede: blocksize = 8; min keysize = 24; max keysize = 24 (not loaded)
 4) twofish: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 5) cast6: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 6) cast5: blocksize = 8; min keysize = 5; max keysize = 16 (not loaded)
Selection [aes]: 1
Select key bytes: 
 1) 16
 2) 32
 3) 24
Selection [16]: 1
Enable plaintext passthrough (y/n) [n]: n
Enable filename encryption (y/n) [n]: y
Filename Encryption Key (FNEK) Signature [9c8e941b757f9f5a]: 28ad40928bf45d59
Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_fnek_sig=28ad40928bf45d59
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=9c8e941b757f9f5a
WARNING: Based on the contents of [/root/.ecryptfs/sig-cache.txt],
it looks like you have never mounted with this key 
before. This could mean that you have typed your 
passphrase wrong.

Would you like to proceed with the mount (yes/no)? : no
Aborting mount.
mint@mint ~ $ sudo mount -t ecryptfs /home/cra1g321/.Private /home/cra1g321/Private
Passphrase: 
Select cipher: 
 1) aes: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 2) blowfish: blocksize = 16; min keysize = 16; max keysize = 56 (not loaded)
 3) des3_ede: blocksize = 8; min keysize = 24; max keysize = 24 (not loaded)
 4) twofish: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 5) cast6: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 6) cast5: blocksize = 8; min keysize = 5; max keysize = 16 (not loaded)
Selection [aes]: 1
Select key bytes: 
 1) 16
 2) 32
 3) 24
Selection [16]: 1
Enable plaintext passthrough (y/n) [n]: n
Enable filename encryption (y/n) [n]: y
Filename Encryption Key (FNEK) Signature [9c8e941b757f9f5a]: 28ad40928bf45d59
Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_fnek_sig=28ad40928bf45d59
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=9c8e941b757f9f5a
WARNING: Based on the contents of [/root/.ecryptfs/sig-cache.txt],
it looks like you have never mounted with this key 
before. This could mean that you have typed your 
passphrase wrong.

Would you like to proceed with the mount (yes/no)? : yes
Would you like to append sig [9c8e941b757f9f5a] to
[/root/.ecryptfs/sig-cache.txt] 
in order to avoid this warning in the future (yes/no)? : no
Not adding sig to user sig cache file; continuing with mount.
Error mounting eCryptfs: [-2] No such file or directory
Check your system logs; visit <http://launchpad.net/ecryptfs>
mint@mint ~ $ cd /home/cra1g321/private
bash: cd: /home/cra1g321/private: No such file or directory

---

### Post by cra1g321 on 2010-06-30
tried those links before but still nuthin. il try them again or sumthin :(

im using a live cd and the home folder is on my ubuntu parition (sda1) so im thinking thats why that tutorial on the 2nd link didnt work.

When i go and locate the folder using nautilus on the live cd and click "access your encrypted data" the screen flickers then this is shown in the terminal 

"(gnome-terminal:11748): Gtk-CRITICAL **: gtk_accel_map_unlock_path: assertion `entry != NULL && entry->lock_count > 0' failed"

---

### Post by dino99 on 2010-06-30
have you done something special to loose it ? or is it only hidden ?

[http://www.linux-mag.com/id/7568/2/](http://www.linux-mag.com/id/7568/2/)

---

### Post by cra1g321 on 2010-06-30
no its hiden using the option during the installation of ubuntu "require my password to login and decrypt my home folder" 

I thoguht i could run my ubuntu parition in recovery mode but i wad reading the menu duing boot is now hidden.

---

### Post by dino99 on 2010-06-30
you can remove "quiet splash" on the boot line to see comments when booting

---

### Post by cra1g321 on 2010-06-30
il do that now then try boot ubuntu

---

### Post by cra1g321 on 2010-06-30
edited out quiest splash from the grub file but didnt change anything. when the splash screen or watever of ubuntu is showing, when i hit enter this errors appears over alot 

/bin/sh/ cant open /proc/self/fd/8
init: mountall-shell main process (426)

I was expecting the process of recovering a encrypted home folder to be rather easy. Was expecting to just double-click on that "access your encrypted data" it would ask for the passphrase, i would enter it then my 140gb of files and folders would show. Seems a few other people where expecting this too.

i really hope i can resolve this and that if i dont i hope i dont go back to windows, but sadly windows is looking like a option. Or maybe i shouldnt of deleted my backup (thinking ubuntu would be fine for a day or day or so)

---

### Post by dino99 on 2010-06-30
*** /bin/sh/ cant open /proc/self/fd/8 ***

nice to know that: fd is the floppy reader, so into bios diseable it and remove it from /etc/fstab too

---

### Post by cra1g321 on 2010-06-30
went into the BIOS and diabled every floppy related thing i could find. 

also edited etc/fstab using sudo gedit in a terminal . but stil comes up with that error when loading ubuntu. im thinkin i maybe to tell ubuntu to use the new edited fstab you know like what you would do if you edited grub or something.

here a complete copy of the terminal when i try do use the instructions on that 1st link

mint@mint ~ $ sudo ecryptfs-add-passphrase --fnek
Passphrase: 
Inserted auth tok with sig [9c8e941b757f9f5a] into the user session  keyring
Inserted auth tok with sig [28ad40928bf45d59] into the user session  keyring
mint@mint ~ $ sudo mount -t ecryptfs /home/cra1g321/.Private  /home/cra1g321/Private
Passphrase: 
Select cipher: 
 1) aes: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 2) blowfish: blocksize = 16; min keysize = 16; max keysize = 56 (not  loaded)
 3) des3_ede: blocksize = 8; min keysize = 24; max keysize = 24 (not  loaded)
 4) twofish: blocksize = 16; min keysize = 16; max keysize = 32 (not  loaded)
 5) cast6: blocksize = 16; min keysize = 16; max keysize = 32 (not  loaded)
 6) cast5: blocksize = 8; min keysize = 5; max keysize = 16 (not loaded)
Selection [aes]: 1
Select key bytes: 
 1) 16
 2) 32
 3) 24
Selection [16]: 1
Enable plaintext passthrough (y/n) [n]: n
Enable filename encryption (y/n) [n]: y
Filename Encryption Key (FNEK) Signature [9c8e941b757f9f5a]:  28ad40928bf45d59
Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_fnek_sig=28ad40928bf45d59
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=9c8e941b757f9f5a
WARNING: Based on the contents of [/root/.ecryptfs/sig-cache.txt],
it looks like you have never mounted with this key 
before. This could mean that you have typed your 
passphrase wrong.

Would you like to proceed with the mount (yes/no)? : no
Aborting mount.
mint@mint ~ $ sudo mount -t ecryptfs /home/cra1g321/.Private  /home/cra1g321/Private
Passphrase: 
Select cipher: 
 1) aes: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 2) blowfish: blocksize = 16; min keysize = 16; max keysize = 56 (not  loaded)
 3) des3_ede: blocksize = 8; min keysize = 24; max keysize = 24 (not  loaded)
 4) twofish: blocksize = 16; min keysize = 16; max keysize = 32 (not  loaded)
 5) cast6: blocksize = 16; min keysize = 16; max keysize = 32 (not  loaded)
 6) cast5: blocksize = 8; min keysize = 5; max keysize = 16 (not loaded)
Selection [aes]: 1
Select key bytes: 
 1) 16
 2) 32
 3) 24
Selection [16]: 1
Enable plaintext passthrough (y/n) [n]: n
Enable filename encryption (y/n) [n]: y
Filename Encryption Key (FNEK) Signature [9c8e941b757f9f5a]:  28ad40928bf45d59
Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_fnek_sig=28ad40928bf45d59
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=9c8e941b757f9f5a
WARNING: Based on the contents of [/root/.ecryptfs/sig-cache.txt],
it looks like you have never mounted with this key 
before. This could mean that you have typed your 
passphrase wrong.

Would you like to proceed with the mount (yes/no)? : yes
Would you like to append sig [9c8e941b757f9f5a] to
[/root/.ecryptfs/sig-cache.txt] 
in order to avoid this warning in the future (yes/no)? : no
Not adding sig to user sig cache file; continuing with mount.
Error mounting eCryptfs: [-2] No such file or directory
Check your system logs; visit <http://launchpad.net/ecryptfs>

---

### Post by cra1g321 on 2010-06-30
Windows 7 is back on the pc. still have the ubuntu partition

---

### Post by acegik on 2010-06-30
I have the same problem!
I am unable to login with ubuntu on my first partition (sda1) so I installed windows 7 on my second partition (sda2) and then ubuntu thinking I could access my old documents file. I can navigate through my partition but I'm not able to find my documents :confused: HELP!!!

---

### Post by cdenley on 2010-06-30
> **cra1g321 said:**
> 
mint@mint ~ $ sudo mount -t ecryptfs /home/cra1g321/.**Private** /home/cra1g321/**Private**
...
mint@mint ~ $ cd /home/cra1g321/**private**
bash: cd: /home/cra1g321/**private**: No such file or directory

Is it "Private" or "private"?

---

### Post by cariboo on 2010-06-30
Please don't create multiple threads on the same subject, I have merged two and closed one.

---

### Post by cra1g321 on 2010-06-30
my apologies for making a couple of threads. Unfortunatily i couldnt resolve this problem and i now have a FULL install of Windows 7. 
I am rather disappointed by ubuntu as this should of been easy. I had recorded the passphrase and was expecting to run that "Acces your private data" thing that is shown in the home folder and it would ask for the passphrase and i would enter it and then my files would be shown. Instead the thing does absolutly nothing. (great feature) 
I really like using linux espeically ubuntu and linux mint but this as rather fried my head. Guess you can kinda blame me for not maknig backups but backing up over 140gb of stuff takes a bit too long. So im sticking with windows 7 for a while, till this feature is improved or something is changed. A user shouldnt have to enter a bunch of commands into a terminal becuase a tool/feature that is added into the OS doesnt work, the tool should work or at least open in the 1st place.
If i was a linux programmer i would love to help sort this out but im not so i really hope some linux guru looks into making this easier for people. Providng a simple way of encrypting data but not providing a simple of restoring that data seems abit stupid. I know its not meant 2 be easy for someone to access the files but surely if someone has the passphrase it should be a simple process.

Any way i can try notify some ubuntu main guys about suggesting improving this issue??, as ive seen on a few forums that other people have the same problem.

---

### Post by cra1g321 on 2010-06-30
Should i give ubuntu one more chance??? this is 1st time ive ever had major problem with linux and im just thinking of all the BSOD windows has giving me over the years. maybe i should learn and improve ubuntu rather than divert away from  the problem.

Fk it im going bk on ubuntu. This time il NOT use the encrpytion option during install !!!

Thanks anyway guys for trying to help me solve this problem. This forum is really gr8

---

### Post by sinner99 on 2010-07-11
ya....something with ubuntu broke. i simply moved a couple of non related drives...content drives...to different controllers, suddenly the ICEAuthority error cant login, etc. they make that encryption choice so appealing on initial installation. what a mistake
thousands and thousands of dollars ill miss out on, should have backed it up I guess. Tried every passphrase I would have made, as an administrator, im quite used to knowing what I would use. we're all human though I guess. there has to be some way to hack through my own dam encryption, my entire profile....lost. i can see the 'encrypted profile' as a private file booted up to knoppix. bout as close as i get, any thoughts or ideas? man I have some bank server installations to do today and I have everything there... ugh ubuntu should really leave that encryption idea to someone that has to hunt it out...and painfully find the way to enable it, not simply hit ok yep i want all private! jesus. sry this sucks alot.

---

### Post by The Bright Side on 2010-10-01
Strange. This morning, some updates (probably the latest kernel) fried my 10.04 system, so I booted with a live CD, ran "sudo nautilus", accessed my Home folder and was able to see all files on it (looked into a couple folders, including "Documents", all visible).

And I'm pretty sure my Home folder is encrypted, too. I have it on its own partition. I was a bit surprised that just running Nautilus with admin rights from the Live CD would make it fully accessible, but hey.

I hooked up my USB hard disk, started copying everything over, watched it for about 10 minutes, no error messages, and went to work.

I really hope that I'm not in for a bad surprise when I come home later today. I really need those files. Last backup is 2 weeks old...

I only skimmed through this thread, but were you able to even see the contents of your home folder when trying to access it from the Live CD?

---

### Post by jmate24 on 2010-10-03
I am having the same problem and i am unable to access the files even though the terminal says that they are in /mnt/OldHome. i cannot seem to be able to access the files...

---

