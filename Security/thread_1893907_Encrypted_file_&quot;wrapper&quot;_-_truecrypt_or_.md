---
title: "Encrypted file &quot;wrapper&quot; - truecrypt or alternative?"
date: 2011-12-11
forum: Security
---

### Post by jlparsons on 2011-12-11
Hi folks, I'm setting up a backup RAID1 NAS server on my home/business network.  I'll be using deja-dup to backup my working directories but I'd also like to have a separate encrypted file system on the server for storage and manual backups.  I therefore need a software solution to create an encrypted "wrapper" file I can store on the NAS server and mount to my filesystem.  The obvious choice would be to use truecrypt which will do all of the above, nice and easy.

Are there any other options I could consider?  Perhaps some more integrated than truecrypt, or that do not use a fixed-size file?  I particularly like the way the "disk utility" on gnome/ubuntu/linux can encrypt a usb disk/stick and remember the password, mounting the drive/stick as soon as its connected.  As my PC is an encrypted drive I'm happy that this would be secure.  I'd love for an encrypted "container" file to exist on my server (a la truecrypt) and my pc just mount it at login.  Anyone know how this might be done?

---

### Post by c.cobb on 2011-12-11
You mean so that the TC volume gets mounted without entering a password, right? 

It might be possible by using a combination of a keyfile, the TC "favorites" list, and TC's auto-mount feature. I've not used keyfiles as, if you lose the file(s), you don't ever access your data again. So not sure if you can use only a keyfile without also using a password.

---

### Post by HermanAB on 2011-12-13
LUKS, encrypted Zip files, EncFS, rsync piped through gpg... The possibilities are endless.

---

### Post by jlparsons on 2011-12-14
> **HermanAB said:**
> LUKS, encrypted Zip files, EncFS, rsync piped through gpg... The possibilities are endless.

All good options, I guess I should be more specific with my question;

What I need is an encrypted volume on my NAS drive which mounts (seemlessly) whenever I'm in range of my wifi connection.  Truecrypt would do it but would require manual mounting.  I'm already using rsync with gpg for my incremental backups on the same NAS.  Zip or rar encrypted files would work but again would need manual accessing of the specific file, so wouldn't be very "on the fly".

EncFS looks like it might do what I need - but could it be made to auto-mount when logged onto the network?  And will it work over FTP...?

Any help would be gratefully received. :)

---

### Post by JustinR on 2011-12-17
> **jlparsons said:**
> All good options, I guess I should be more specific with my question;

What I need is an encrypted volume on my NAS drive which mounts (seemlessly) whenever I'm in range of my wifi connection.  Truecrypt would do it but would require manual mounting.  I'm already using rsync with gpg for my incremental backups on the same NAS.  Zip or rar encrypted files would work but again would need manual accessing of the specific file, so wouldn't be very "on the fly".

EncFS looks like it might do what I need - but could it be made to auto-mount when logged onto the network?  And will it work over FTP...?

Any help would be gratefully received. :)

What kind of NAS do you have? Some NAS' have Linux installed - which can be [used to encrypt/decrypt data on the NAS itself]("http://mybookworld.wikidot.com/encrypted-filesystem") without you having to use your own computer to encrypt/decrypt data, namely Western Digital nas'.

---

