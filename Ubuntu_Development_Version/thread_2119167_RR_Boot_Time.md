---
title: "RR Boot Time"
date: 2013-02-23
forum: Ubuntu Development Version
---

### Post by kuvanito on 2013-02-23
This is something The Ubuntu Team has to work on at present time it is awful
It varies for me between 1:15 and 1:35 minutes while on the same PC Windows 8 boots in 20 Seconds
I am not saying Ubuntu has to match W8 but at least better it's boot time to 30 or even 40 seconds.
Over all comparison between the two RR 13.04 and W8,windows is much faster at everything. Ubuntu used to be the champ,what is happening?

---

### Post by ajgreeny on 2013-02-23
Is the Win8 time you show a real boot, or just a return from the hybrid hibernation, or whatever it's called, that Win 8 uses by default?

Also don't forget that RR is still in alpha, so a lot **_will_** change before it is released.

---

### Post by kuvanito on 2013-02-23
> **ajgreeny said:**
> Is the Win8 time you show a real boot, or just a return from the hybrid hibernation
Real Time Chronometered from the moment I push the Power button to the time I get a fully functional desktop.

---

### Post by awam66 on 2013-02-23
I find the same RR is very slow to boot. At least 2 minutes on my Sony Viao Laptop.
It seems to get slower with every release.
Can wee hope that it will speed up?

---

### Post by rtalcott on 2013-02-23
Yes...it's slow...2 machines...an HP/Intel laptop about 45 seconds to login screen and a 5+ year old Gigabyte/AMD mobo about 50 seconds to login...I can't remember when but a few years ago I was to the login screen in less than 20 seconds.

---

### Post by Curtis6767 on 2013-02-23
This has changed in the last week to ten days. 

I was going from grub to the login screen in about 30-40 seconds.

Now it's more like 50 seconds.

Edit: From grub to Win7 login in 30seconds


I'm sure this will get attended to at the appropriate time.

---

### Post by rtalcott on 2013-02-23
**This has changed in the last week to ten days. **

I think you are right...this is the first time I have watched and timed the boot in weeks and I was surprised at how slow it was...so yes this may be relatively recent..

---

### Post by brainwash on 2013-02-23
If you are experiencing a 20 sec boot delay, then you might be affected by this bug:

[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1129157](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1129157)

---

### Post by VinDSL on 2013-02-23
Interesting...

I just reinstalled BootChart (haven't run it in a while).

As of today, my ancient iron (see sig) is booting 13.04 in 1 min 16 sec.

[INDENT][ATTACH]231799[/ATTACH][/INDENT]

Looking back, at this old 11.10 screenie, it took 59 sec:

[INDENT][ATTACH]231800[/ATTACH][/INDENT]

... or an increase of 17 sec (13.04 vs. 11.10).

I would judge that to be an acceptable increase, considering I'm living on the fringe-edge of Ubudom.

Having said that, there was a time in the distant past (10.10, I think) that this machine booted Ubu in =< 30 sec.

So, boot times are definitely growing somewhat longer, as time marches on...  ;)

---

### Post by mc4man on 2013-02-23
One of the previous Ubuntu releases targeted fast boot/login & here it was about 15 sec.'s with an hdd. (forget which release, though if you check the archives it would have had a bunch of boot test threads, ect.

In the last couple of releases the boot time to greeter has gone up, though the diff here between 12.04/12.10 & 13.04 is mainly the time from greeter to desktop.

So currently on same hardware that once did 15 sec is now around 40 sec

---

### Post by Kow on 2013-02-23
Once the consolekit issue is fixed (which is why lightdm is pausing for 20 seconds during boot), most of you should see your boot times speed up by about 20 seconds.

All of these bugs are related to lightdm pausing for 20 seconds:
[https://bugs.launchpad.net/bugs/1127051](https://bugs.launchpad.net/bugs/1127051)
[https://bugs.launchpad.net/bugs/1123798](https://bugs.launchpad.net/bugs/1123798)
[https://bugs.launchpad.net/bugs/1129157](https://bugs.launchpad.net/bugs/1129157)

---

### Post by kaldor on 2013-02-23
No clue why, but Ubuntu has always booted very slowly on this PC. Windows 7 will boot in under 20 seconds, whereas Ubuntu 11.04 through 12.04 take at least 1 minute. 

I remember during the 9.04 (Jaunty) cycle boot time was a focus. My  laptop was able to boot 9.04 in about 15 seconds. What's going on?

Boot time used to be one of the things I bragged about when using Linux back in 2007-2008 :???:

---

### Post by rtalcott on 2013-02-25
Shut down the laptop last night after yesterday's updates...booted this morning to less than 30 seconds rather than the 45 or so yesterday.

---

### Post by nismoryco on 2013-02-25
Thanks. I removed whoopsie and my boot times are much better.

---

### Post by zika on 2013-02-26
> **nismoryco said:**
> Thanks. I removed whoopsie and my boot times are much better.
No need to remove whoopsie...
Simple
```
echo manual | sudo tee -a /etc/init/whoopsie.override
```
will do...

---

### Post by P-I H on 2013-02-26
You may also deactivate whoopsie in System Settings/Privacy

---

### Post by jppr on 2013-02-26
There is comin new Whoopsie update...

[https://launchpad.net/ubuntu/raring/+source/whoopsie/0.2.15](https://launchpad.net/ubuntu/raring/+source/whoopsie/0.2.15)

---

