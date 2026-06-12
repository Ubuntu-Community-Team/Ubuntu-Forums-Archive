---
title: "Running python scripts at startup on VPS"
date: 2012-04-26
forum: Server Platforms
---

### Post by izacboy_123 on 2012-04-26
Hey,

I've got three Python applications I want to be started upon boot; they are all started using the following three commands:

nohup python /home/b1/s1.pyc &
nohup python /home/b2/s2.pyc &
nohup python /home/b3/s3.pyc

How can I make the server run these commands each time I boot or reboot the VPS?

Thanks guys.

Ubuntu 11.04

---

### Post by azzamite on 2012-04-26
Have you tried putting those lines in /etc/rc.local?

Also, most of the scripts in /etc/init.d/ have a function that looks like:
```
start_<service> () {
   # commands and scripts
}
```

Make a backup of the stuff first

---

### Post by papibe on 2012-04-26
Hi izacboy_123.

The simplest method I can think of, without messing the init scripts is to use cronbtab. There's an special tag called '@reboot' designed to run things at startup.

For instance:
```
# m h  dom mon dow   command
@reboot   /path/to/myscript.sh
```

I hope that points you in the right direction. Tell us how it goes.
Regards.

---

### Post by izacboy_123 on 2012-04-27
Thanks for the replies!

I'm a bit new to this, I'm not sure how to go about either methods :')

---

### Post by papibe on 2012-04-27
Take a look at this crontab [tutorial]("https://help.ubuntu.com/community/CronHowto"), and let us know if you have any questions.

Regards.

---

