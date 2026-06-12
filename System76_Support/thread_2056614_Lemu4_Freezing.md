---
title: "Lemu4 Freezing"
date: 2012-09-11
forum: System76 Support
---

### Post by Ubun2to on 2012-09-11
Well, I've had this problem for awhile, but it nearly vanished when I started keeping only 1 or 2 tabs open on Chromium, so I figured that was the problem-keeping tons of tabs open. But, I have given up on that idea since it just froze on me while playing Minecraft (not on a server-just Minecraft, and my networking was turned off to save battery).
I initially had this problem, but it was caused by the Intel HD graphics glitch, which was fixed by a kernel update.
So, I am just going to try and tackle it once and for all.
Why does my Lemu4 freeze with 2 tabs open, whereas my desktop, which has equivalent specs (but with an AMD chip and ATI graphics), can juggle 20 tabs and not freeze?

---

### Post by Rader on 2012-09-11
Are you running Unity (i.e., "3D")?  When it freezes, is it just the display/window manager, with the machine still running, so that the mouse cursor can be moved, and the tty1 session is available at (Ctl-Alt-F1)?  Or is the kernel itself frozen, and nothing works?  

In the first case, it is possible to recover the display manager without rebooting.  That does not clear up what is going wrong, unfortunately.  To recover the display manager, see my comment at [http://ubuntuforums.org/showthread.php?t=2008813&highlight=unity+freezes&page=8](http://ubuntuforums.org/showthread.php?t=2008813&highlight=unity+freezes&page=8).

---

### Post by Ubun2to on 2012-09-12
> **Rader said:**
> Are you running Unity (i.e., "3D")?  When it freezes, is it just the display/window manager, with the machine still running, so that the mouse cursor can be moved, and the tty1 session is available at (Ctl-Alt-F1)?  Or is the kernel itself frozen, and nothing works?  

In the first case, it is possible to recover the display manager without rebooting.  That does not clear up what is going wrong, unfortunately.  To recover the display manager, see my comment at [http://ubuntuforums.org/showthread.php?t=2008813&highlight=unity+freezes&page=8](http://ubuntuforums.org/showthread.php?t=2008813&highlight=unity+freezes&page=8).

I do use Unity 3D. (Unity 2D is lacking in too many features for the performance benefits, in my opinion).
It is not possible to get to the command line to restart LightDM (which I learned how to do after it forgot to bring up the lock screen when I opened my laptop lid-very useful, as this is a shaky feature on basically all laptops running Ubuntu), and the mouse does not respond.
It does not respond to key combinations, either (both to get to the command line and to restart).
I'm pretty sure the kernel is just completely locking up. I can wait 5 minutes with the key combinations and get no response.
Also, I am not getting freezes due to a lack of resources-I have an 8 GB swap partition, and 8 GB of RAM, and the System Monitor shows memory usage very low before it freezes.
Here is an oddball item that could be useful-if I open Chromium before or during the "Connected to [WiFi SSID here]" message shows up, it usually freezes right after I open the browser. This is not repeated across other applications, however.

---

### Post by joe4ska on 2012-09-22
The only time I have freezes it's usually caused by a Flash advertisement or something Flash related. Does this only happen with Chromium?

---

### Post by Ubun2to on 2012-09-23
> **joe4ska said:**
> The only time I have freezes it's usually caused by a Flash advertisement or something Flash related. Does this only happen with Chromium?

I'm not sure.
It stopped happening entirely now. I wonder if it was the kernel update-I am now running 3.2.0-31, rather than 3.2.0-30.

---

### Post by Welly Wu on 2012-09-23
You need to upgrade to Linux kernel 3.3.6-030300.

I had a similar problem and I contacted System76. Mark Hoffart reported that some Lemur Ultra Thin customers still experienced random system freezes after applying the Linux kernel 3.2.0-27 generic update. He said that this is a workaround that solves the problem.

Hi Welly

Below are some steps to try a different Kernel that people used as a work around when the first bug initially developed. Some people actually stuck with this because it seemed the patched didn't cure their individual situations fully. 

cd /tmp && wget -O linux-headers-3.3.6-030300_3.3.6_all.deb [http://goo.gl/zNlMy](http://goo.gl/zNlMy)
sudo dpkg -i linux-headers-3.3.6-030300_3.3.6_all.deb
cd /tmp && wget -O linux-headers-3.3.6-generic_amd64.deb [http://goo.gl/Z9Ztt](http://goo.gl/Z9Ztt)
sudo dpkg -i linux-headers-3.3.6-generic_amd64.deb
cd /tmp && wget -O linux-image-3.3.6-generic_amd64.deb [http://goo.gl/jji3o](http://goo.gl/jji3o)
sudo dpkg -i linux-image-3.3.6-generic_amd64.deb

---

### Post by Welly Wu on 2012-09-23
The Linux kernel 3.2.0-x generic is slightly flawed. It will continue to give you on and off again random system freezes until you upgrade to a newer Linux kernel version like 3.3.6. If you don't upgrade to a newer Linux kernel, then you will never figure out why your System76 Lemur Ultra keeps randomly locking up and freezing.

---

### Post by Welly Wu on 2012-09-23
On my System76 Lemur Ultra Thin (lemu4), Linux kernel 3.3.6-030306 generic is the latest stable version and it completely solved all lockups and freezes permanently. I can run 36 software applications at the same time without any problems and I can suspend and resume from RAM instantly. I have stressed tested this specific Linux kernel version and it is good to go.

---

### Post by Ubun2to on 2012-09-24
> **Welly Wu said:**
> You need to upgrade to Linux kernel 3.3.6-030300.

I had a similar problem and I contacted System76. Mark Hoffart reported that some Lemur Ultra Thin customers still experienced random system freezes after applying the Linux kernel 3.2.0-27 generic update. He said that this is a workaround that solves the problem.

Hi Welly

Below are some steps to try a different Kernel that people used as a work around when the first bug initially developed. Some people actually stuck with this because it seemed the patched didn't cure their individual situations fully. 

cd /tmp && wget -O linux-headers-3.3.6-030300_3.3.6_all.deb [http://goo.gl/zNlMy](http://goo.gl/zNlMy)
sudo dpkg -i linux-headers-3.3.6-030300_3.3.6_all.deb
cd /tmp && wget -O linux-headers-3.3.6-generic_amd64.deb [http://goo.gl/Z9Ztt](http://goo.gl/Z9Ztt)
sudo dpkg -i linux-headers-3.3.6-generic_amd64.deb
cd /tmp && wget -O linux-image-3.3.6-generic_amd64.deb [http://goo.gl/jji3o](http://goo.gl/jji3o)
sudo dpkg -i linux-image-3.3.6-generic_amd64.deb

uname -a now returns:
```
Linux hostname 3.3.6-030306-generic #201205121335 SMP Sat May 12 17:36:12 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux.
```
Hopefully this will work. Only time will tell.

---

### Post by Ubun2to on 2012-10-01
The kernel upgrade seems to have worked, but there has been an increase in boot time of about 5.2 seconds.

---

### Post by Welly Wu on 2012-10-01
What's more important to you?

I value stability as it won't destroy my PC hardware due to constant and random freezes and lock ups. Linux kernel 3.3.6-030306 is extremely stable and reliable. I have tested it extensively under the heaviest work loads and it has performed admirably. I have noticed a longer boot-up period, but that is negligible to me compared to stability.

---

### Post by Ubun2to on 2012-10-02
> **Welly Wu said:**
> What's more important to you?

I value stability as it won't destroy my PC hardware due to constant and random freezes and lock ups. Linux kernel 3.3.6-030306 is extremely stable and reliable. I have tested it extensively under the heaviest work loads and it has performed admirably. I have noticed a longer boot-up period, but that is negligible to me compared to stability.

I was just pointing that out. No need to kill the messenger boy.

---

### Post by mellster on 2012-10-31
Thanks - that kernel upgrade fixed a bunch of issues such as browser freezes and problems with a USB mouse. One other problem that is much  better after the kernel upgrade as well but not sure if completely gone is that over time the (wireless) networking capability seemed to degrade with regards to host resolution. Once a connection is made I get standard DSL (AT&T) download speeds, but on sites that communicate with a lot of different hosts as well as the initial resolution can sometime take quite  a while. This did not happen in the beginning, the lemur is now 8 months old. Otherwise this is a great little sturdy bastard. Anybody experiencing this as well? Thanks & cheers

---

### Post by screaminj3sus on 2012-11-01
> **mellster said:**
> Thanks - that kernel upgrade fixed a bunch of issues such as browser freezes and problems with a USB mouse. One other problem that is much  better after the kernel upgrade as well but not sure if completely gone is that over time the (wireless) networking capability seemed to degrade with regards to host resolution. Once a connection is made I get standard DSL (AT&T) download speeds, but on sites that communicate with a lot of different hosts as well as the initial resolution can sometime take quite  a while. This did not happen in the beginning, the lemur is now 8 months old. Otherwise this is a great little sturdy bastard. Anybody experiencing this as well? Thanks & cheers

No problems here on my lemur ultra

---

### Post by Ubun2to on 2012-11-01
> **mellster said:**
> Thanks - that kernel upgrade fixed a bunch of issues such as browser freezes and problems with a USB mouse. One other problem that is much  better after the kernel upgrade as well but not sure if completely gone is that over time the (wireless) networking capability seemed to degrade with regards to host resolution. Once a connection is made I get standard DSL (AT&T) download speeds, but on sites that communicate with a lot of different hosts as well as the initial resolution can sometime take quite  a while. This did not happen in the beginning, the lemur is now 8 months old. Otherwise this is a great little sturdy bastard. Anybody experiencing this as well? Thanks & cheers

I hate it when people go gravedigging.
Sounds like your Internet is just slow, and your browser takes awhile because the cache is dumped on closing.

---

