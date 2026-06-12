---
title: "AMD proprietary driver 11.11 released"
date: 2011-11-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Harry33 on 2011-11-15
This new proprietary AMD Catalyst 11.11 driver has some great improvements.
First of all, it does have the xserver 1.11 support. NVidia managed to do this several weeks ago.
Secondly, Catalyst 11.11 does have the OpenCL run-time integration.

---

### Post by magarciar on 2011-11-15
could you please upload it to some server? the link in amd.com is down and the open-source driver doesn't work for me

---

### Post by jfernyhough on 2011-11-15
[http://www2.ati.com/drivers/linux/ati-driver-installer-11-11-x86.x86_64.run](http://www2.ati.com/drivers/linux/ati-driver-installer-11-11-x86.x86_64.run)

--edit
Also very easy to get this one running (though need a reboot to verify)

$ chmod +x ./ati-driver-installer-11-11-x86.x86_64.run
$ ./ati-driver-installer-11-11-x86.x86_64.run --buildpkg Ubuntu/precise
[might need to $ sudo apt-get remove fglrx-updates]
$ sudo dpkg -i *.deb

--edit 2
Yup, that was easy. Even works with Liquorix 3.1. I think it should work with mainline 3.2-rc2 but I'm not testing any kernel earlier than rc3. :)

---

### Post by ranch hand on 2011-11-16
> **Harry33 said:**
> This new proprietary AMD Catalyst 11.11 driver has some great improvements.
First of all, it does have the xserver 1.11 support. NVidia managed to do this several weeks ago.
Secondly, Catalyst 11.11 does have the OpenCL run-time integration.
Well, this is great to hear.

Just put a warning in your xorg thread about that.  The xorg upgrade has been in my repo here under Debian for a long time and, so far, I have not been able to use it.  A real pain in the posterior.

I think I can wait for the driver to show up in the repo.

Thanks for the news.  Been getting cranky about this.

---

### Post by kaldor on 2011-11-16
Could someone who is using this driver give some feedback as to how well it's working?

---

### Post by benjamimgois on 2011-11-16
What about powerxpress ? is it working ?

---

### Post by alphacrucis2 on 2011-11-16
> **kaldor said:**
> Could someone who is using this driver give some feedback as to how well it's working?

I haven't tested it in precise yet but under oneiric it works very well with unity/compiz. With gs/clutter I still have trouble with video glitches every few seconds.

---

### Post by floydsp on 2011-11-16
I installed it in Precise and 1st time this computer didn't screw up
fonts as all the other times I tried using amd proprietary drivers

floydsp

---

### Post by Harry33 on 2011-11-17
More about this new driver in the Phoronix article:
**[SIZE=2]AMD Catalyst 11.11 Brings Critical Linux Changes:[/SIZE]**

[http://www.phoronix.com/scan.php?page=news_item&px=MTAxNTc](http://www.phoronix.com/scan.php?page=news_item&px=MTAxNTc)

---

### Post by McFeud on 2011-11-17
I installed and it seemed to work pretty easy ...  the previous driver screwed up unity ... at least everything seems to be running fine. But i'm really not sure if I really have the latest driver installed. What shoud CCC tell on driver numbers with this 11.11 release? 

Catalyst version: 11.9
Driver: 8.892-110914m-125703C-ATI
2D driver: 8.88.7
Catalyst Control Ceneter: 2.13
RandR ver 1.3

OpenGL ver: 4.1.11005

On my system those are on my native language so i tried to translate to proper names. But do i have latest driver or not? I have a hunch that driver isnt really installed

---

### Post by Harry33 on 2011-11-17
You seem to have Catalyst 11.9 installed, not 11.11.
Did you reboot after installation?

You should see this:
Catalyst version 11.11
Driver version 8.91

---

### Post by McFeud on 2011-11-19
Thanks. I rebooted but i didnt remove glrx-updates and stuff. After that i just tried to find out what version numbers should be shown after install but couldnt find any. I'll try again with removing.

---

### Post by linuxman94 on 2011-11-19
Make sure you purge the drivers and not just remove them:

```
sudo apt-get purge fglrx*
```After you've built the new packages and installed them, run this command.

```
sudo amdconfig --initial -f
```I had the same problem you have and this solved it.

---

### Post by McFeud on 2011-11-22
Thanks all. I got it working now. I think some previous failures to install post release drivers had something to do with my little headache. All works now - at least as good as release drivers. Beeing busy for "testing" :)

---

