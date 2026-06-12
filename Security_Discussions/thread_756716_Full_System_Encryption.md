---
title: "Full System Encryption"
date: 2008-04-16
forum: Security Discussions
---

### Post by nami on 2008-04-16
Apparently Ubuntu 7.10 has allows users to setup an encrypted hard drive:

[https://wiki.ubuntu.com/EncryptedFilesystemsInstaller](https://wiki.ubuntu.com/EncryptedFilesystemsInstaller)

Does that mean that attempts like:

[http://nomi.ibnmasud.com/blog/reset-your-lost-ubuntu-password/](http://nomi.ibnmasud.com/blog/reset-your-lost-ubuntu-password/)

Will no longer work?

---

### Post by hyper_ch on 2008-04-16
this will still work - as long as you remember the encryption password... that one is different from user passwords.

---

### Post by tact on 2008-04-16
Correct.  That method of getting root access to your HDD (without a password) will not work if you have an encrypted HDD.

edit:  added "(without a password)" to the line above for clarity - so it does not appear that hyper_ch and I are saying conflicting things

---

### Post by tact on 2008-04-16
With an unencrypted HDD ... you dont even need to follow that guide and edit lines in grub to get passwordless root HDD access.  

Just boot from a liveCD and you get root access to an unencrypted HDD.

Neither of these approaches will give an attacker passwordless root access to your HDD.  

As hyper_ch noted..  you just gotta have that HDD password.  :)

On the other side...  If you have a fully encrypted EXTERNAL HDD in a USB enclosure...  and you plug it into your PC's USB port guess what?

The system (in ubuntu at least) is clever enough to realise the attached drive is encrypted and a sweet dialog box pops up to tell you so and ask for the passphrase.  

But wait...  there's MORE!   hehehe
I have a USB HDD with one partition unencrypted and one partition encrypted.   When I plug it into my laptop the unencrypted partition is mounted immediately AND that sweet dialog box pops up telling me about the encrypted partition and inviting me to enter the passphrase.     Cool!

---

### Post by nami on 2008-04-16
Interesting stuff.

That guide above tells you how to get root access.  is it possible to reset the password of an encrypted hdd?

I just want my laptop to be secure, i.e. i want to stop people from getting the data out, by removing the hdd, or my resetting the password, or by using a livecd to access to hdd.

---

### Post by hyper_ch on 2008-04-16
it is possible to reset the password... by issuing the password to access it or by using a keyfile... if you don't remember the password and don't have (anymore) a keyfile... then you can only brute-force it... but that will take years....

The conent of the harddisk will be encrypted except for /boot and you can't get access to the data inside without unlocking the drive first. That's how this is supposed to work.

So if you start encrypting your full disk, you should also have somewhere a backup copy. Because if the harddisk will have a defect you may not gain access either to that data.

---

### Post by nami on 2008-04-16
That is perfect!  If the only solution of getting into a encrypted installation: [https://wiki.ubuntu.com/EncryptedFilesystemsInstaller](https://wiki.ubuntu.com/EncryptedFilesystemsInstaller) is by brute force, then that is secure enough in my world.

Thanks for the help!

I'm assuming this file system encryption option will be available in the standard graphical installer of ubuntu 8.04 coming out in a few days?

---

### Post by hyper_ch on 2008-04-16
no, alternate install cd...

Edit: Well, as you pointed out on brainstorm with reference to the wiki it sounds like encryption from DesktopCD is now also possible... but then, I haven't used a desktopcd for a long time.


as said, when you encrypt the data... make sure you have also a backup somewhere (also encrypted if you're paranoid) because hardware failures can happen...

---

### Post by nami on 2008-04-16
> **hyper_ch said:**
> no, alternate install cd...

Edit: Well, as you pointed out on brainstorm with reference to the wiki it sounds like encryption from DesktopCD is now also possible... but then, I haven't used a desktopcd for a long time.


as said, when you encrypt the data... make sure you have also a backup somewhere (also encrypted if you're paranoid) because hardware failures can happen...

the keywords being "sounds like", which is why i wanted to confirm.  Thanks for the backup tips.  Will keep all those in mind when installing 8.04.

---

### Post by hyper_ch on 2008-04-16
Backups are always recommended... but if the initalizing vector of the container gets damaged, you can't recover any data... at least I think you can't....

---

### Post by ukripper on 2008-04-16
you might also want to secure your grub incase you wish to - [http://ubuntuforums.org/showthread.php?t=715630](http://ubuntuforums.org/showthread.php?t=715630)

---

### Post by hyper_ch on 2008-04-16
how would securing grub help with a fully-encrypted system?

---

### Post by nami on 2008-04-17
> **hyper_ch said:**
> Backups are always recommended... but if the initalizing vector of the container gets damaged, you can't recover any data... at least I think you can't....

Thanks, I will be doing backups.   Probably to backup my truecrypt files with rdiff-backup :KS

---

### Post by nami on 2008-04-17
> **hyper_ch said:**
> no, alternate install cd...

Edit: Well, as you pointed out on brainstorm with reference to the wiki it sounds like encryption from DesktopCD is now also possible... but then, I haven't used a desktopcd for a long time.


as said, when you encrypt the data... make sure you have also a backup somewhere (also encrypted if you're paranoid) because hardware failures can happen...

Loops like it is still only available in the text installer...

---

### Post by hyper_ch on 2008-04-17
> **nami said:**
> Loops like it is still only available in the text installer...

Which is recommended for installation anyway ;9

---

### Post by ukripper on 2008-04-17
> **hyper_ch said:**
> how would securing grub help with a fully-encrypted system?

Well i have secured grub before encrypting my system. So that answered your question!

---

### Post by hyper_ch on 2008-04-17
I don't understand what you mean to say.

---

### Post by mojorising on 2008-04-17
I did not do a fresh install of hardy on my laptop. I upgraded from Gutsy but I would still like to encrypt my drive. 

Is there any way to set up full drive encryption, post-install?

Thanks, 
Mike

---

### Post by mojorising on 2008-04-17
Ah! never mind. I checked the wiki ([https://wiki.ubuntu.com/EncryptedFilesystemsInstaller](https://wiki.ubuntu.com/EncryptedFilesystemsInstaller)) on this again and it has been updated with more info on the topic, specifically, 

"Migration
Since an on-the-fly migration to encrypted partition is not reliable and always needs a backup, we will currently not offer a migration tool. The currently recommended way is to backup your data and reinstall from scratch. (This might get easier in the future, see "Outstanding Issues"). "

So that pretty much answers it. Looks like the developers are working on bringing the functionality I'm looking for in the future. 


Mike

---

