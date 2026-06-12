---
title: "Encrypt home folder after installation"
date: 2010-02-11
forum: Security
---

### Post by golfer91 on 2010-02-11
Hi.

I have just installed Ubuntu Jaunty (I do not like Karmic, please don't try to make me upgrade) and after installing all my programs I realized I did not encrypt my home directory.

I know it's very simple to do this during the installation but I can't seem to find an option to do it after it.

Is there a way to do this?

Thanks in advance.

---

### Post by FuturePilot on 2010-02-11
Yes you can still do it without reinstalling. 

(carefully) follow these instructions
[http://blog.dustinkirkland.com/2009/06/migrating-to-encrypted-home-directory.html]("http://blog.dustinkirkland.com/2009/06/migrating-to-encrypted-home-directory.html")

---

### Post by shankhs on 2011-11-25
It seems ecryptfs needs free space 2.5X the size of home folder :( This means that the tool is of no use when you have ubuntu installed for a long time or your ubuntu partition is small. Is there any encrypt tool which need far less free space than that of ecryptfs?

---

### Post by FuturePilot on 2011-11-28
> **shankhs said:**
> It seems ecryptfs needs free space 2.5X the size of home folder :( This means that the tool is of no use when you have ubuntu installed for a long time or your ubuntu partition is small. Is there any encrypt tool which need far less free space than that of ecryptfs?

No it doesn't. Where are you getting that information from?

---

### Post by strange_cathect on 2012-01-06
I'm trying to use the command 'encryptfs-migrate-home -u -USER' to encrypt the /home partition of a ubunut 11.10 laptop.

But I get error messages: 'cannot access /home/user .gvfs Permission denied'

What is happening here?

---

### Post by sblandford on 2012-06-14
> **shankhs said:**
> It seems ecryptfs needs free space 2.5X the size of home folder :( This means that the tool is of no use when you have ubuntu installed for a long time or your ubuntu partition is small. Is there any encrypt tool which need far less free space than that of ecryptfs?

This is because the instructions copy the data (with rsync) from your existing home directory instead of moving it. This is safer, but obviously resulting in double the required disk space.

You can get around this you can do the following...


[LIST=1]
[*]Backup important large data to an external device (or two external devices to be safe) e.g. from your Documents, Videos, Music,  .thunderbird and .mozilla directories.
[*]Delete the large data on your local drive
[*]Follow the instructions to set up the encrypted home directory
[*]Copy the large data back from your backup device to your new encrypted directory.
[*]Secure delete the data from your backup device(s), since there is probably a reason you wanted to encrypt the home directory!
[/LIST]
The "wipe" command can be used for secure delete. In fact, this should probably be used in place of the "rm" in the instructions too.

---

