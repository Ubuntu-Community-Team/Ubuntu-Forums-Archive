---
title: "Is there a way to auto-backup my server?"
date: 2013-03-22
forum: Server Platforms
---

### Post by TheGuyWithTheFace on 2013-03-22
Hello World!

I have been using Ubuntu for my desktop OS for almost a year, and love it, and now I'd like to use Ubuntu Server Edition on a old laptop I have lying around. I've been using it as a Minecraft server, but since I'm not too experienced with the command line, I just had a lubuntu installation, and backed it up with Dropbox. I feel like there's a better way of doing this... The only thing is, is there something like dropbox for the command line that I can use?

---

### Post by CharlesA on 2013-03-23
It depends on what you want to backup to.

I have an external drive hooked up to my server and run a rsync script to backup to it daily. I also have CrashPlan installed, so I have offsite backups.

Technically, I could use crashplan for both local and offsite backups, but since I've had rsync setup for a few years already, I feel it works fine for local backups (and it can do remote backups too via SSH if you so desire).

---

### Post by TheGuyWithTheFace on 2013-03-23
I'd prefer an offsite backup in case of fire or anything, but if nothing else, an external drive backup is better than nothing. I'll look into crashplan, but I'd really prefer something free... at the very least, I'll check out rsync. Thanks!

Other suggestions?

---

### Post by CharlesA on 2013-03-23
You can use Crashplan to store your data at a friend's place for free, but I opted just to store it on their servers since it was encrypted.

It looks like you can use Dropbox from a terminal via a Python script:
[https://www.dropbox.com/install?os=lnx](https://www.dropbox.com/install?os=lnx)

---

### Post by thnewguy on 2013-03-23
Since you already use Dropbox, I would probably just continue to Dropbox in the command-line form. The Dropbox website can walk you through setting up the client software on your server.

---

### Post by TheGuyWithTheFace on 2013-03-23
oh! I didn't know there was a command line option for dropbox, that's good to know! Thank you for pointing that out, that should do the trick.

---

### Post by TheGuyWithTheFace on 2013-03-23
Does anyone know how I can mark this thread as solved? It seems since the interface has changed, it's no longer in thread tools...

---

### Post by CharlesA on 2013-03-23
> **TheGuyWithTheFace said:**
> Does anyone know how I can mark this thread as solved? It seems since the interface has changed, it's no longer in thread tools...

You can edit the thread title.

---

### Post by TheGuyWithTheFace on 2013-03-23
Thank you.

---

