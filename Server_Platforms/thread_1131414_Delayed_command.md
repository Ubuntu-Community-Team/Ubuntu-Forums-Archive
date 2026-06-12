---
title: "Delayed command?"
date: 2009-04-20
forum: Server Platforms
---

### Post by wubrgamer on 2009-04-20
I'd like to (on my dreamhost shared debian server):

run a delayed command, I would like make a file available for download, but only for a short amount of time (say 48 hours) and then after that, remove the file. without having to manually removing the file? (as I have been doing through an FTP client.)

is there a way to do this?

I could put into my crontab "rm /home/USERNAME/SITE/file.ext" for the date and time that I would like to remove it from my server.

But how do I do this?

What would you do?

thanks for your help!

basically, what I'm trying to do is auto-prune these files.

based on time.

---

### Post by HalPomeranz on 2009-04-20
You could put an entry like this in root's crontab:

```

0 0 * * * find /home/USERNAME/SITE -type f -mtime +2 -exec rm {} \;

```

That would run at midnight and remove any files under /home/USERNAME/SITE that are older than two days.  Be careful that there are not files under /home/USERNAME/SITE that you want to keep around for longer than that, however, because the above command will not discriminate.

To add this command to root's crontab, just run "sudo crontab -e" and cut and paste the above line into the editor window that opens up.

---

### Post by OmegaBLK on 2009-04-20
If you are only going to do this once, then take a look at the **at** command which is similar to cron, but useful for if you only need to run a delayed command once.

---

### Post by wubrgamer on 2009-04-20
thank you!

"at" is the command I was looking for exactly!

could you please help me find a good place to start to learn how to use it?

---

### Post by OmegaBLK on 2009-04-20
It's pretty much similar to cron.  Check out these links:

[http://manpages.ubuntu.com/manpages/intrepid/en/man1/at.1.html](http://manpages.ubuntu.com/manpages/intrepid/en/man1/at.1.html)
[http://www.ibm.com/developerworks/linux/library/l-job-scheduling.html#N10181](http://www.ibm.com/developerworks/linux/library/l-job-scheduling.html#N10181)
[http://www.brunolinux.com/02-The_Terminal/The_at_Command.html](http://www.brunolinux.com/02-The_Terminal/The_at_Command.html)

---

### Post by BkkBonanza on 2009-04-21
**man at**
tells you pretty much all about it.

---

