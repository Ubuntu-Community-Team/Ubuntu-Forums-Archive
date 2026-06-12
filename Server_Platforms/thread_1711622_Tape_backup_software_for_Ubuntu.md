---
title: "Tape backup software for Ubuntu"
date: 2011-03-21
forum: Server Platforms
---

### Post by Superdust on 2011-03-21
Hi

I have just installed Ubuntu on a server at work.
Now I need a easy to set up (preferable GUI) backup program witch support tape drives, and can send e-mail reports.
Is there any in the repertories?

Appreciate any help :)

---

### Post by Vegan on 2011-03-21
tar is the tape archive tool and once you have an archive you can cp the tar to the tape

tape is easy with Linux

---

### Post by Superdust on 2011-03-21
Thank you.

I seem to have tar installed.
But where is control panel for setting up rotation, e-mail confirmation etc?

---

### Post by hkphooey on 2011-03-24
Hi,

Perhaps there wasn't enough information in the original answer. tar stands for Tape ARchive, and was originally meant for copying files to tape. 

The key to understanding it is that in Linux, a tape drive appears as a device, usually /dev/st0. To backup your home directory, you'd just use something like this:

```
tar -cf /dev/st0 /home
```

Then you'd rewind and eject the tape with the mt command (Magnetic Tape):

```
mt -f /dev/st0 rewind
mt -f /dev/st0 eject
```

As all this is command-line stuff, you can put this together into a script, and use cron to fire it off at regular intervals. 

There are many more options to tar and mt of course, so its a good idea to read the man pages for both these commands. 

If you search around the internet you'll find many backup scripts, which you can adapt to your own needs. There's one here for example -- just the first one I found. 

[http://www.cyberciti.biz/faq/linux-tape-backup-with-mt-and-tar-command-howto/](http://www.cyberciti.biz/faq/linux-tape-backup-with-mt-and-tar-command-howto/)

---

### Post by HermanAB on 2011-03-24
Howdy,

Read up on Bacula, Amanda and Zmanda.

---

