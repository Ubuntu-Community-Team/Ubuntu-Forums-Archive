---
title: "Noob needs to apply an rt kernel patch"
date: 2009-07-08
forum: Ubuntu Studio
---

### Post by sonicpainter on 2009-07-08
I have been trying for a month to get audio software (especially Rosegarden) to work under Ultimate Edition 2.2, Ubuntu Studio 9.04, Ubuntu 9.04 with Studio added...to no avail.  The Ubuntu Studio 9.04 that I downloaded (twice) will not correctly install.  

But the thrust of my question is:  Can I get a detailed list of instructions regarding how to find my kernel version, and then how to apply the appropriate rt patch?

I( know there are thousands of posts similar to this - I've read almost all of them - but I still haven't found a straight answer.)  Thanks!!!

Sonic

---

### Post by sgx on 2009-07-08
Hi, using synaptic package manager, install qjackctl, it prompts you to add a few dependancies, then update all the alsa/libalsa/libalsa2 apps
that show up in synaptic, then install aoss, zynaddsubfx synth and hydrogen drum machine, and their dependancies. Now  you can make music, time for root user to run the alsaconf command to configure your sound. Forget rosegarden and RT for a few days, and get familiar with a couple of excellent instruments, and connecting them to the i/o in qjackctl. Please! There are 3 tabs in qjackctl, each with a panel of options. Select (highlight) items in the left side of a panel to connect to  ones in the right side, then click the connect button on the panel. Do this in
the panels from both the left and right tabs. Forget the middle tab for now. Zynaddsubfx and hydrogen need connecting to your sound system  before you can hear them. The synth has a VK button to open an onscreen keyboard, and the drum machine has demo loops you can start to jam with.
Cheers

---

### Post by sonicpainter on 2009-07-09
ok, I'll try that.  But, does anyone know about applying Xenomai?  Are there horror stories?  Are there happily-ever-after stories?:guitar:

---

### Post by malrost on 2009-07-09
To tell what kernel version you're currenly using:

```
uname -r
```

To install the rt kernel:

```
 sudo apt-get install linux-rt
```

then do this:

```
sudo apt-get install linux-headers-rt
sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf'
sudo su -c 'echo @audio - nice -19 >> /etc/security/limits.conf'
sudo su -c 'echo @audio - memlock unlimited >> /etc/security/limits.conf'
```

Check this page out for more details, particularly the "Real Time Support" section: [https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)



If, despite this, you would much rather really want to compile and install your own patched kernel, this guide looks accurate enough:

[http://easylinuxcds.com/blog/?p=3244](http://easylinuxcds.com/blog/?p=3244)

Compiling your own kernel isn't particularly difficult. Just make sure you back up your currently working kernel (and that you know how to revert back to it) in case the new kernel doesn't work.

As for the Ubuntu Studio version that you downloaded twice not correctly installing... did you make sure the entire thing was downloaded by verifying the md5sum, and verifying the disc once you burned it (there's an option for this during install)? It's possible that your download or disc was corrupted.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

