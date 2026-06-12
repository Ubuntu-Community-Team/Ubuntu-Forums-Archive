---
title: "[SOLVED] Dovecot (localhost) &amp;amp; Thunderbird - Thunderbird can't authenticate (goes"
date: 2007-04-09
forum: Server Platforms
---

### Post by Incie83 on 2007-04-09
Hello there,

I'm trying to set up an e-mail archive in a Maildir format (you know, the whole fetchmail/procmail/dovecot thing) and I have a problem running dovecot and getting Thunderbird to connect to localhost through the IMAP protocol.

After Thunderbird prompts me for a password, I enter it and click 'OK', Thunderbird doesn't connect properly: it just rotates the 'connecting to..', 'authenticating...' and 'opening folders' messages in its statusbar. Needless to say, I can't do anything with the folders in Thunderbird. 

I suspect its something to do with imap-login. I have about 8 instances of it running at the moment, and every time I restart the dovecot server 2 new imap-login processes start. What's my mistake?

---

### Post by shufla on 2007-04-24
Hello,

Check what is saying /var/log/mail.log file while you are authenticating with Thunderbird. Paste it here for further analysis.

Bye,
Shufla

---

### Post by Incie83 on 2007-04-24
Thanks for replying, Shufla. Here's my mail.log:

```
11:49:06 user-desktop dovecot: IMAP(user): link(/media/data/Mail/.temp.user-desktop.7326.d7fbbe9d6c02f4e0, /media/data/Mail/dovecot.index.log.newlock) failed: Operation not permitted
Apr 24 11:49:06 user-desktop dovecot: IMAP(user): file_dotlock_open() failed with file /media/data/Mail/dovecot.index.log: Operation not permitted
Apr 24 11:49:06 user-desktop dovecot: child 7326 (imap) killed with signal 11
```

I think I have to change group ownership to "mail" for the "/media/data/Mail" folder, is that correct? How can I do this, Nautilus (run as root) won't let me change this setting. It stays on "plugdev", probably because the data disk is a mounted partition.

Any ideas?

---

### Post by darrenm on 2007-04-24
Try ```
sudo chown root:mail /media/data/Mail
``` But it looks like you haven't got the mailbox locations setup correctly in dovecot.conf anyway.

Don't know if this may help? [http://ubuntuforums.org/showthread.php?t=398866](http://ubuntuforums.org/showthread.php?t=398866)

---

### Post by Incie83 on 2007-04-24
Cheers, Darren. When I set my Maildir to a folder in my home dir, it works. However, I would like to use my dovecot mailbox as an e-mail archive. Therefore, I don't want the data stored on my Ubuntu partition, but on a separate data partition. I've now gotten to the actual problem: automounting my "/media/data" partition as a user, not root (since root-owned directories seem to cause my authentication problem).

I don't know how to do this, fstab doesn't seem to work for me, it just gives me errors when I try to set the "o" option. Can anybody offer me some advice on how to automount and set ownership to a user? I'll even go the udev way, if that's what it takes. ;)

---

### Post by darrenm on 2007-04-24
try editing /etc/fstab to make the mount ```
 -o user,rw,uid=1000,gid=1000
``` making the uid and gid the correct ones for the who you want to mount it as.

---

### Post by Incie83 on 2007-07-15
Hmm, after some time off and installing Feisty I'm trying this again, and it still doesn't work.

Internal server error, according to Thunderbird. This is what mail.log says:

> Jul 15 16:27:16 jeroen-desktop dovecot: imap-login: Login: user=<jeroen>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Jul 15 16:27:16 jeroen-desktop dovecot: IMAP(jeroen): link(/media/sdb2/Mail/.temp.jeroen-desktop.12466.2497c31c32ef3b09, /media/sdb2/Mail/dovecot.index.log.newlock) failed: Operation not permitted
Jul 15 16:27:16 jeroen-desktop dovecot: IMAP(jeroen): file_dotlock_open() failed with file /media/sdb2/Mail/dovecot.index.log: Operation not permitted

Something to do with permissions, again? The main user account ('jeroen') owns the mounted drive, I've mounted the drive with 'users' and 'umask=0000', so it is a complete mystery to me why I keep getting permission errors. Also, the 'mail' group (as darrenm suggested above) doesn't exist, so it seems.

EDIT: I tried setting ownership to the 'mail' group (and both user 'jeroen' and 'dovecot'), but that didn't help either

I hope anybody can't help. Surely, somebody else must have the same setup (mail archive on a FAT32 disk), what am I doing wrong?

---

### Post by Incie83 on 2007-07-29
Well, I finally got it to work. The solution: re-formatting part of my data drive as EXT3, using this partition as a /home directory, making sure it is big enough for my mail archive.

Moral o/t Story: don't set the Dovecot mail_location to a directory on a FAT32 drive, I suspect it's something to do with how FAT32 handles permissions (well, actually, it doesn't know what permissions are).

---

