---
title: "Cron Backup of a folder."
date: 2007-06-28
forum: Server Platforms
---

### Post by Gruelius on 2007-06-28
Hey guys n gals,
ATM my server just has a basic raid and a hard disk. I would like to have a setup where every  12 hours my website directory is put into a tarball then zipped up in the format (webbackup*DATE*.tar.gz) and placed into a folder. Ive forgotten how to use the command but i rememberd it was something like tar *folder* | gzip *name of file*, if someone could help me out and explain to me the command that would be great.

And yeah id need to know how to put it into cron aswell :P Also apache tells me about not  being able to determine the domain name correctly or something, how do i stop it from bugging me?

Thanks Everyone, i really do appriciate the help. Oh btw i converted my nan to linux :D

---

### Post by thornomad on 2007-06-28
I have a hard time remembering the correct options and whatnot for command line tools as well ... if you run a:

man tar -or- man gzip

You will be able to read the manuals in there with examples.  I think it goes something like:

tar -cvf filename.tar.gz /dir/to/compress

But I could be wrong.  Would have to do a man tar myself to find out (am on windows -- *shudders*).  As for cron, you can edit our "crontab" ...

```
$ crontab -e
```

That's your user's crontab ... can enter the command there.

---

### Post by crazyjx23 on 2007-06-28
Use amanda.

---

