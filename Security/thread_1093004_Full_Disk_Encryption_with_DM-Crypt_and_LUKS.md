---
title: "Full Disk Encryption with DM-Crypt and LUKS"
date: 2009-03-11
forum: Security
---

### Post by FiberOptix on 2009-03-11
Hello,

After making use of Truecrypt for full disk encryption on my Windows machine I was a little dissapointed to learn that the same feature was not available for linux. After doing a bit of research it seems that dmcrypt & LUKS is the best bet for a linux setup. I've found several tutorials out there describing how to set this up but all the ones I've seen assume the reader is starting from scratch, so I'm trying to flesh things out before I get started.

I think the way this should work will be to:

1) Make an image of my hard disk
2) Do a clean install 
3) Install dmcrypt and LUKS
4) Transfer all settings/files from my hd image

Have I got this right? I don't have any experience doing this kind of file/settings transfer and I'd appreciate some recommendations on what tools to use/how to go about it. Step #2 also seems like it may be tricky since I'll have to wipe everything cleanly.

Suggestions/comments would be very helpful.

---

### Post by hyper_ch on 2009-03-11
you don't need to image, just make a backup of your files, especially your home folder.

Get the ALTERNATE install cd. With that one, you can directly encrypt the syste during installation.

Here's a step-by-step guide on how to encrypt (Hardy) during installation:
[http://www.howtoforge.com/encrypting-the-system-manually-upon-installation-ubuntu8.04](http://www.howtoforge.com/encrypting-the-system-manually-upon-installation-ubuntu8.04)

Here's an example of a fully encrypted raid-1 lvm system (lenny):
[http://www.howtoforge.com/set-up-a-fully-encrypted-raid1-lvm-system](http://www.howtoforge.com/set-up-a-fully-encrypted-raid1-lvm-system)

Notice: The swap-random-key-bug has been solved in 9.04

---

### Post by Tubes6al4v on 2009-03-11
Good descussion on restoring backups:
[http://ubuntuforums.org/showthread.php?t=1012103&highlight=encrypted+restore](http://ubuntuforums.org/showthread.php?t=1012103&highlight=encrypted+restore)

Here is a little guide on it, but no comments as to if it works or not from others:
[http://ubuntuforums.org/showthread.php?t=1062082&highlight=encrypted+backup](http://ubuntuforums.org/showthread.php?t=1062082&highlight=encrypted+backup)


Note: I have not tried either of these, so you are kind of on your own.

---

### Post by FiberOptix on 2009-03-11
> **hyper_ch said:**
> you don't need to image, just make a backup of your files, especially your home folder.

Get the ALTERNATE install cd. With that one, you can directly encrypt the syste during installation.

Here's a step-by-step guide on how to encrypt (Hardy) during installation:
[http://www.howtoforge.com/encrypting-the-system-manually-upon-installation-ubuntu8.04](http://www.howtoforge.com/encrypting-the-system-manually-upon-installation-ubuntu8.04)

Here's an example of a fully encrypted raid-1 lvm system (lenny):
[http://www.howtoforge.com/set-up-a-fully-encrypted-raid1-lvm-system](http://www.howtoforge.com/set-up-a-fully-encrypted-raid1-lvm-system)

Notice: The swap-random-key-bug has been solved in 9.04

Let me see if I understand you correctly.

By using the alternate installer with encryption support the disk will be formatted and I'll have a fresh install featuring full disk encryption, then I just restore my files from the backup? What about settings and all that? I suppose if I make a full backup then overwriting the new files with my backed up ones will result in all my configurations restored?

Do I have that right?

Thanks very much for your help.

---

### Post by FiberOptix on 2009-03-11
> **Tubes6al4v said:**
> Good descussion on restoring backups:
[http://ubuntuforums.org/showthread.php?t=1012103&highlight=encrypted+restore](http://ubuntuforums.org/showthread.php?t=1012103&highlight=encrypted+restore)

Here is a little guide on it, but no comments as to if it works or not from others:
[http://ubuntuforums.org/showthread.php?t=1062082&highlight=encrypted+backup](http://ubuntuforums.org/showthread.php?t=1062082&highlight=encrypted+backup)


Note: I have not tried either of these, so you are kind of on your own.

These are great! Thanks very much!

---

### Post by hyper_ch on 2009-03-11
> **FiberOptix said:**
> By using the alternate installer with encryption support the disk will be formatted and I'll have a fresh install featuring full disk encryption, then I just restore my files from the backup? What about settings and all that? I suppose if I make a full backup then overwriting the new files with my backed up ones will result in all my configurations restored?

That's pretty much it. You also might want first to make a list of the installed packages so you can easily fetch and re-install tehm again.

---

