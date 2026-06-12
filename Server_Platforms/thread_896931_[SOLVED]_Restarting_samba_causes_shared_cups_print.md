---
title: "[SOLVED] Restarting samba causes shared cups printers to disappear."
date: 2008-08-21
forum: Server Platforms
---

### Post by kevmitch on 2008-08-21
This is driving me crazy.

After a reboot, samba automatically detects all of my cups printers such that they are correctly listed with the command. 

```
rpcclient  -c enumprinters localhost
```

Of course, they also show up if I browse them with a windows machine.

However, if for whatever reason, I restart samba, the result of the above command becomes

```

Password:
No printers returned.

```

And windows machines can no longer see any of the printers. I am of course entering the same valid samba password that got me the list of printers before restarting samba. 

I also notice that even if samba is seeing my printers, adding a new one to cups also requires a full reboot before samba can see it. 

I've tried restarting both cups and samba to no avail. I can't figure out what magic is happening when I reboot. Does anyone have any ideas or has anyone else noticed this?

---

### Post by tech9 on 2008-08-21
> **kevmitch said:**
> This is driving me crazy.

After a reboot, samba automatically detects all of my cups printers such that they are correctly listed with the command. 

```
rpcclient  -c enumprinters localhost
```Of course, they also show up if I browse them with a windows machine.

However, if for whatever reason, I restart samba, the result of the above command becomes

```

Password:
No printers returned.

```And windows machines can no longer see any of the printers. I am of course entering the same valid samba password that got me the list of printers before restarting samba. 

I also notice that even if samba is seeing my printers, adding a new one to cups also requires a full reboot before samba can see it. 

I've tried restarting both cups and samba to no avail. I can't figure out what magic is happening when I reboot. Does anyone have any ideas or has anyone else noticed this?

try this my friend...

```
sudo /etc/init.d/cupsys restart
```

then check to see if your printers show up again

---

### Post by kevmitch on 2008-08-21
> **tech9 said:**
> try this my friend...

```
sudo /etc/init.d/cupsys restart
```

then check to see if your printers show up again

Nope, doesn't do it. As I said, I've tried restarting both cups and samba to no avail. I will confess I'm on a Debian system where /etc/init.d/cupsys has been renamed to /etc/init.d/cups.

---

### Post by kevmitch on 2008-08-22
Well I figured out the problem, but I still don't know why a reboot ever helped. 
Along with finding the following in /var/log/cups/error_log

```

E [22/Aug/2008:02:51:12 -0700] Unsupported character set "iso-8859-1"!
E [22/Aug/2008:02:56:40 -0700] Unsupported character set "iso-8859-1"!
E [22/Aug/2008:02:56:40 -0700] Unsupported character set "iso-8859-1"!
E [22/Aug/2008:02:56:40 -0700] Unsupported character set "iso-8859-1"!
E [22/Aug/2008:02:56:40 -0700] Unsupported character set "iso-8859-1"!

```

I stumbled upon the following link:
[http://daniel.mateos.cc/2008/05/14/sambacups-charset-problems-in-debian-etch/]("http://daniel.mateos.cc/2008/05/14/sambacups-charset-problems-in-debian-etch/")

Now I don't necessarily agree with the solution there. Mostly because I don't think you should have a UTF locale as the system wide default because you can't expect everything to support IT (e.g. aterm).

So instead I dug around the samba man page and found that the following in the [global] section of my /etc/samba/smb.conf file did the trick:
```

   display charset = UTF8

```

---

### Post by djotaku on 2008-09-29
thank you SOO SOO much for that display charset - I've been troubleshooting this for about 5 hours over the past two days!!

Oh, I owe you one!

---

### Post by matludlam on 2011-06-09
Thanks for the fix.  I have Ubuntu 10.04.2 LTS which still has the same problem.

This fix nailed it though.

---

### Post by Vladimir Hidalgo on 2011-11-22
This is still a problem for 11.04, is there any bug filled about this?

---

