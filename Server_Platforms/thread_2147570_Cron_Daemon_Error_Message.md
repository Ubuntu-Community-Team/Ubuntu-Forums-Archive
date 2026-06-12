---
title: "Cron Daemon Error Message"
date: 2013-05-22
forum: Server Platforms
---

### Post by bullet333 on 2013-05-22
Ubuntu 12.10
Squid3 3.1
Dansguardian 2.10.1.1
Postfix 2.9.6
Webmin 1.620

I keep getting these error messages everyday in the 'nobody' mailbox:

```

/etc/squid3/bannerfilter/update.sh: 116: [: 1: unexpected operator

```

Line 116 of update.sh is:

```

115 # Send all instances of redirector.pl a signal to reload the data files
116 if [ $RELOAD == 1 ] && [ $CHANGED == 1 ]; then
117   killall -HUP redirector.pl
118 fi
119

```
The redirector is located in /etc/squid3/bannerfilter/redirector.pl
I've also attached the script to this post in case you want to examine it yourself!

Now I'm not very good at scripting and not exactly sure what this one does but it appears to clean up temp files and whatnot.  I've tried researching this but to no avail.  Can someone please help me out?  

Thanks

---

### Post by SeijiSensei on 2013-05-22
Try this syntax instead:

```
if [ $RELOAD = 1  -a $CHANGED = 1 ]; then
```

Use "man bash" to see the Bash manual page then search for "test expr" for details on conditional expressions.

---

