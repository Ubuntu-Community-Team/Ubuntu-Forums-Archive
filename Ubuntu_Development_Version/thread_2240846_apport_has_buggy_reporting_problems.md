---
title: "apport has buggy reporting problems"
date: 2014-08-22
forum: Ubuntu Development Version
---

### Post by ventrical on 2014-08-22
apport is acting up again . It is requesting me to send bugs reports and then telling me that they are invalid, then, just booting up a few minutes ago, I tried to ignore then and close them and it left a relic on my screen, when , upon clicking, it closed.

anybody else noticing bogus apport pop-ups ?

---

### Post by Cavsfan on 2014-08-22
I booted with systemd and immediately got a popup box saying an error had occurred and asking if I want to report it. I just left it and opened up terminal and got a bunch of updates including the new kernel.
Then another box saying the same thing opened up. I just rebooted thinking that it was because my software was not up to date.

However it would not shutdown. It just listed the systemd messages that it listed when I booted up. I tried Alt+Cntl+F1 to see if I could reboot that way but could not enter anything.

So I pressed the reset button. Booted back up with systemd and it got another error. It said it was an error with Upstart. 
I was under the impression that booting with systemd and Upstart (init) were 2 different things so I didn't understand that one since I never touched Upstart that I know of.

---

### Post by grahammechanical on 2014-08-22
I have been getting some Apport reports but they were genuine. I have Psensor installed as a start up application and it has been crashing on start up. Otherwise. whole system has been behaving itself.

---

### Post by ventrical on 2014-08-22
It sends me an e-mail with this:

> 
Thank you for your report!
 
However, processing it in order to get sufficient information for the
developers failed (it does not generate a useful symbolic stack trace). This
might be caused by some outdated packages which were installed on your system
at the time of the report:
 
libdbus-1-3 version 1.6.18-0ubuntu10 required, but 1.8.6-1ubuntu1 is available
outdated debug symbol package for libdbus-1-3: package version 1.8.6-1ubuntu1 dbgsym version 1.6.18-0ubuntu10
 
 
Please upgrade your system to the latest package versions. If you still
encounter the crash, please file a new report.
 
Thank you for your understanding, and sorry for the inconvenience!
 


After apport created and reported this:

[https://bugs.launchpad.net/ubuntu/+source/indicator-keyboard/+bug/1359904](https://bugs.launchpad.net/ubuntu/+source/indicator-keyboard/+bug/1359904)

and this was after update.

edit:

But ( did notice this at least, in the stacktrace)

```

#1  0x00007f05a59a794d in ?? () from /usr/lib/x86_64-linux-gnu/libwayland-client.so.0
No symbol table info available.
#2  0x00007f05a59a4e09 in wl_display_connect () from /usr/lib/x86_64-linux-gnu/libwayland-client.so.0
No

```

and I am wondering what the E'll wayland is doing  in here . I thought we were working with mir/xorg or 
did something
get switrched yet again.

edit note:

This could be 'my bad'. I',m udating the 3.16.0-10 kernel now along with a few other updates .. Will reboot and see.

---

### Post by ventrical on 2014-08-22
Updated, hard booted and got this

[https://bugs.launchpad.net/ubuntu/+source/powerd/+bug/1351314](https://bugs.launchpad.net/ubuntu/+source/powerd/+bug/1351314)

 But the browser did not come up until I closed apport .. so apport is buggy.

edit.. and it never reported the unity-control-center problem ..so there is something not right with apport.

edit:  Started up after a two hour shutdown and now all the apport pop-ups are gone.

---

### Post by jeanfi on 2014-09-01
> **grahammechanical said:**
> I have been getting some Apport reports but they were genuine. I have Psensor installed as a start up application and it has been crashing on start up. Otherwise. whole system has been behaving itself.

It might be: [https://bugs.launchpad.net/ubuntu/+source/psensor/+bug/1346299](https://bugs.launchpad.net/ubuntu/+source/psensor/+bug/1346299)
A fix is already provided for this issue.

Start psensor from command line and see if you have the error "Attempt to unlock mutex that was not locked".

---

### Post by pixelro on 2014-09-01
> **ventrical said:**
> apport is acting up again . It is requesting me to send bugs reports and then telling me that they are invalid, then, just booting up a few minutes ago, I tried to ignore then and close them and it left a relic on my screen, when , upon clicking, it closed.

anybody else noticing bogus apport pop-ups ?

yes for months now but i was to lazy to report it :lolflag:

---

### Post by ventrical on 2014-09-01
> **pixelro said:**
> yes for months now but i was to lazy to report it :lolflag:

I hear ya .... zzzzzzzzzzz... :)

---

### Post by cariboo on 2014-09-01
I just posted a bug concerning system-config-printer, apport worked the way it should, without any drama. :)

---

### Post by mc4man on 2014-09-02
I guess this thread is a continue of [http://ubuntuforums.org/showthread.php?t=2231845](http://ubuntuforums.org/showthread.php?t=2231845) ?
If so,  while a bug was filed,  nothing much happened. In any event once apport > launchpad reports are turned off for 14.10  then it won't be of  user concern anymore.

---

### Post by ventrical on 2014-09-02
My last post pertinent to the topic was about a week ago so I'll mark the thread as solved.

---

