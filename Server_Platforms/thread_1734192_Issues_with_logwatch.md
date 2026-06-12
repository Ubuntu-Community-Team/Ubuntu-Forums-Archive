---
title: "Issues with logwatch"
date: 2011-04-20
forum: Server Platforms
---

### Post by DrkMachine on 2011-04-20
Relatively new to Ubuntu and this is my first post so bare with me.

I have an installation of Ubuntu server 10.10 and followed the directions here [http://ubuntuforums.org/showthread.php?t=1268015](http://ubuntuforums.org/showthread.php?t=1268015) to set up logwatch. Every time logwatch runs in my cron.daily it fails to complete and leaves a logwatch.kljKJl867 (or something with a similar extension) directory in my /tmp directory. This is what I find in my syslog

```
Apr 19 06:54:45 CRON[5639]: (CRON) error (grandchild #5641 failed with exit status 1)
Apr 19 06:54:45 postfix/sendmail[6140]: fatal: open /etc/postfix/main.cf: No such file or directory
Apr 19 06:54:45 CRON[5639]: (root) MAIL (mailed 1 byte of output; but got status 0x004b, #012)
```

Any ideas would be appreciated.
Mike

---

### Post by falko on 2011-04-20
Can you post the output of ```
ls -la /etc/postfix/
```? Maybe it is just a permissions problem.

---

### Post by DrkMachine on 2011-04-20
Thank you for the response falko, Not sure what happened but I rebooted the server last night and behold my logs were in my email this morning. Now to figure out why the UFW logs are not among those reported...lol

---

