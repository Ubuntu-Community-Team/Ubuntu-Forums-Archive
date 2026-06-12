---
title: "Avast w Chron as sudo?"
date: 2009-06-08
forum: Security
---

### Post by RMOP on 2009-06-08
[Thanks for avoiding discussion of the pros/cons of AV tools and/or Ubuntu/Windows relative merits]

One of the machines on my home network runs ONLY Ubuntu, but connects to multiple other machines, some of which belong to my home network and run Windows XP.

I'd like to setup the Ubuntu-only machine to run Avast automatically as a privileged (sudo) user. Ideally, I'd like Avast to run a full command-line scan of all all local ext3 partitions AND all mounted SMB shares.

As the user will NOT have administrative rights, this Avast business will have to be launched from a configuration file which confers sudo rights on the Avast session each time it runs.

Finally, I'd like to be notified if Avast actually finds anything of interest. Preferably, w/o manually scanning an Avast log file!

Now, I suspect this task is easier to accomplish with the Server Version of Avast, but I've got the (no-cost) home version, which I want to use. I know enough about Ubuntu to think it can be done with Chron and some other tools presently obscure to me. Obviously, I don't know enough to do the job. Hence, this post.

Any help here? Many thanks.

---

### Post by rookcifer on 2009-06-08
If you know the command for running a virus scan, then just put that command into crontab.

To set that up, run the following from the terminal:

```
sudo crontab -e
```

I recommend you select the "nano" editor as its much more intuitive.  Once done editing, then hit CTRL-X to save.

To understand the syntax of the crontab file (it's easy), then Google will have a lot of tutorials.  In fact, I found an old thread from these forums on crontab [here.]("http://ubuntuforums.org/showthread.php?t=102626&highlight=cron")

---

