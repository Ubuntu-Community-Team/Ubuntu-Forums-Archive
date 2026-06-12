---
title: "Backup program to create encrypted backups?"
date: 2007-02-26
forum: The Cafe
---

### Post by bash on 2007-02-26
As you can read [here](http://ubuntuforums.org/showthread.php?t=370906) I accidently managed to remove acces to all my files. I had to reinstall Ubuntu now and all my data is lost. Now IF I had a backup (as I intended) this wouldn't have been to much trouble. But my issues is the following:

Im storing the backups on an external Harddrive. And this is just for the reason that the thing that happened to me showed. If I store the backups on the same harddrive, there is no real point in creating them, since most probably if your normal data is screwed so are your backups. So I wanted to store them on an external drive. But now comes in the fact that I can't find a program that encrypts the backup and password protects them. Since the backups are on an external drive, someone would just need to plug that drive to his comp and get all the access to your files he wanted, even more he could restore the system to the exact point you had it. 

The best I found so far is Simple Backup. Its actually does everything I need expect creating encrypted backups, There is even some discussion about some neat inclusion into Ubuntu of such a program ([http://wiki.ubuntu.com/HomeUserBackup](http://wiki.ubuntu.com/HomeUserBackup) | [http://wiki.ubuntu.com/UbuntuHomeBackup](http://wiki.ubuntu.com/UbuntuHomeBackup)) but seems like work on that has stopped. And even there encryption is not part of the basic features.

So please someone help as Im quite frustrated at the moment. Im not running of to Windows right ahead, since theres to much in Ubuntu I like, but I have to say there were capable and easy to use applications that did exactly that what im describing and asking for (Acronis Products, Norton Products, ...)

---

### Post by PatrickMay16 on 2007-02-26
Now, rar has an option to encrypt archives. You can make your backups, and then put them in a rar archive which is encrypted. Would that be good enough?

You'll need to install rar. The syntax for the command is well explained by the output of the "rar" command with no options.

For example, here's the rar command that will make an encrypted archive:

rar a -hp nutloader.rar *files*

---

### Post by Falcorian on 2007-03-01
I'm looking for something similar. My roommates and I have a common server that I'd like to make backups to, but then all my files would be public (and permissions are not an option, because we have multiple roots).

rar doesn't seem like the best option, as I'd like to be able to do something like rsync. Maybe rsync, then use something to encrypt the directory? Any ideas?

---

### Post by doobit on 2007-03-01
Check this out: [http://www.saout.de/misc/dm-crypt/](http://www.saout.de/misc/dm-crypt/)

dynebolic uses this to encrypt your backup information on a USB drive. You might be able to use it in Ubuntu as well.

---

### Post by bash on 2007-03-02
Well I thougth about just storing the normal backups on an encrypted partition. Might be an option. Although a backup program that can just encrpyt the backups would be prefered.

---

