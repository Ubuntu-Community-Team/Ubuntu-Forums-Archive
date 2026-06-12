---
title: "Massive /var/tmp contents"
date: 2007-12-05
forum: Server Platforms
---

### Post by MatthewMetzger on 2007-12-05
Hello,

I have an Ubuntu Server 6.06.1 LTS that I'm using as a TWiki server, along with squid and squidguard services. It has been running without any problems for a couple months (uptime is 85 days).

However, I noticed that the /var/tmp directory is filling up extremely rapidly. There are 99 GB of data that has appeared there and I'm not sure where it came from. There are hundreds of files that begin with BDB (BDB22453).

Is squid generating these files? Can they safely be removed?

thanks for any help you can give me.

Matthew

---

### Post by p_quarles on 2007-12-05
Yes, they can be safely removed. If you were to restart the box, they would actually be automatically deleted, along with any other files in */tmp directories. Nothing essential will ever be automatically stored in those directories. 

Given how fast this directory is building up, I would suggest setting up a cron job to clean it out.

---

### Post by MatthewMetzger on 2007-12-06
Thanks p_quarles,

I manually removed the files and will be watching to see if they come back. I'd like to know what is causing them to appear.

I'll write a removal script if the files start accumulating again.

-Matthew

---

### Post by Cato2 on 2007-12-06
Try using this to see which process has the file open:

```
lsof /tmp/BDBxxxxx 
```

And then use 'ps' to find out which processes have the files open.  You might need to use 'ls -t | head | xargs lsof' or similar to only do this for a few recent files.  Also 'man lsof' may have some tips.

This only works if the process that generates the files is quite long running. 

Another idea is to do 'strings /tmp/BDBxxx | less' which will rip out any strings from the file, even if a binary, and give a clue as to what generates it.  Also, try 'file foobar' on the files.

See [http://www.debianadmin.com/basic-linux-commands-with-man-pages.html](http://www.debianadmin.com/basic-linux-commands-with-man-pages.html) for some other handy commands.

---

