---
title: "HP PSC as network scanner"
date: 2009-12-28
forum: Server Platforms
---

### Post by Karl Norway on 2009-12-28
Hi 
I got my HP PSC 2400 series connected as a shared printer. I want the scanner fuction to work if possible over the network or directly to PDF.  Is this possible?

---

### Post by beniwtv on 2009-12-28
Yep, it is.

I have a PSC 1110 and it works nicely as a printer and network scanner.

First, make sure your printer and scanner works on your local machine (the machine acting as server). Install sane if you don't have it already.

Next, configure the sane server to listen on the network (good reference: [https://help.ubuntu.com/community/ScanningHowTo](https://help.ubuntu.com/community/ScanningHowTo))

On the clients, if they are linux edit /etc/sane.d/net.conf and instert the hostname or IP of your server. On Windows clients, you can use SaneTwain (works really well).

Cheers,

---

### Post by Karl Norway on 2009-12-28
I think Im having troubble setting up the server. (havent tried it on localhost)...

I did set up sane as on a linux sane page.

*Edit*I see on the Ubuntu Help site taht i havent done it correct (I think). I have to check tomorrow....
I hope it works cous my psc i placed in the garage and im in the house (most of the time)

---

### Post by beniwtv on 2009-12-28
If you have any error messages / or more information on where you get stuck that would really help us to troubleshoot the issue.

---

### Post by Karl Norway on 2009-12-28
The one thing I know is that i cant get acces from my Windows machine.

(i have used this thing to help me [http://www.linux.com/archive/articles/57798](http://www.linux.com/archive/articles/57798))

Im not shure i did the step where Im supposed to setup the sane deamon to listen on my subnet.

---

### Post by Karl Norway on 2009-12-30
Here is what Im having troubble with.

It comes when i try to

```

sudo invoke-rc.d saned start

```

I get tis in return
```

Starting SANE network scanner server: invoke-rc.d: initscript saned, action "start" failed.

```

Whats wrong? I have done everything accordign to the howto link a bit further up.

---

### Post by Karl Norway on 2009-12-31
When I type in 
```

scanimage -L

```

I get this response

```

WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect
device `hpaio:/usb/psc_2400_series?serial=HU44LKF0986T' is a Hewlett-Packard psc_2400_series all-in-one

```

Am i missing a driver or is the scanner not "open" to all users?

---

### Post by Karl Norway on 2010-01-04
Does Xsane need to run the server?

---

### Post by beniwtv on 2010-01-08
The Sane daemon seems to not start up. That's why the message:

```
Starting SANE network scanner server: invoke-rc.d: initscript saned, action "start" failed.

```

You should first see why the Sane daemon doesn't start, because that is most likely the problem. See if you can find anything on the logs in /var/log/ and/or try to start the sane daemon manually (see the init script on how to do this).

---

