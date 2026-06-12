---
title: "question about installing Debian (or other distro)"
date: 2011-07-01
forum: System76 Support
---

### Post by chexmix on 2011-07-01
Good morning, all -

I am interested in trying out other Linux distros on my Starling. I actually have installed distros (as well as BSDs and even Plan9) on laptops before, so it's a familiar process for the most part ... however, I was wondering if there were any System76-specific "gotchas" I should be aware of. I don't want to louse up my Ubuntu installation, which works fine ... at least, not until I have something else working well.

I presume it's okay to install another distro as I have in the past, and install grub as part of that procedure, and so on, to get a dual boot netbook ...?

I will try Debian first, which I understand folks have had good luck with, and only then try something like Slackware.

Thanks,

Glenn

---

### Post by collisionystm on 2011-07-01
> **chexmix said:**
> Good morning, all -

I am interested in trying out other Linux distros on my Starling. I actually have installed distros (as well as BSDs and even Plan9) on laptops before, so it's a familiar process for the most part ... however, I was wondering if there were any System76-specific "gotchas" I should be aware of. I don't want to louse up my Ubuntu installation, which works fine ... at least, not until I have something else working well.

I presume it's okay to install another distro as I have in the past, and install grub as part of that procedure, and so on, to get a dual boot netbook ...?

I will try Debian first, which I understand folks have had good luck with, and only then try something like Slackware.

Thanks,

Glenn


If you are just interested in trying out the the different distros, just run them virtually in Virtualbox or Vmware Player. Then you can get a feel for how they work and find out if you will enjoy it or not. If ubuntu works on your netbook, I am sure another distro will to.

---

### Post by chexmix on 2011-07-01
> **collisionystm said:**
> If you are just interested in trying out the the different distros, just run them virtually in Virtualbox or Vmware Player. Then you can get a feel for how they work and find out if you will enjoy it or not. If ubuntu works on your netbook, I am sure another distro will to.

Well, I already know I like Debian and Slackware (and Arch and OpenBSD and ...). I'm really most concerned about mucking up whatever System76-specific things reside on the netbook.

---

### Post by gamerchick02 on 2011-07-01
Installing another distro shouldn't be a problem for your Starling.  You might run into an issue with the driver, but everything else should work.

I've tried Jolicloud on the Star1 and it worked pretty well.  I'm using Xubuntu right now, and I love it.

Granted those are both based on Ubuntu.

Good luck in your distro-hopping.

Amy

---

### Post by drewbenn on 2011-07-02
> **chexmix said:**
> Well, I already know I like Debian and Slackware (and Arch and OpenBSD and ...). I'm really most concerned about mucking up whatever System76-specific things reside on the netbook.

We've run Debian on a pair of older (2-3 years old) System76 laptops, though not a Starling, with no real issues at all.  Haven't done much dual-booting, though.

What System76 adds is their driver (installed into /opt/system76/ if you want to go grep around to see what it does; 'grep -IiR star[0-9] opt/system76/* | wc -l' returned 64 for me), which in turn adds any drivers for your hardware or makes whatever other tweaks are necessary.  You can grab it from [http://planet76.com/repositories/](http://planet76.com/repositories/) if you want (and of course extract it with 'dpkg -x' so you can look at its contents) if you need to find it after you've moved to another OS.

The biggest thing to remember is that Debian Stable (if that's what you're planning on running) was frozen in 2010-08, or more than a full Ubuntu release ago, so it doesn't have full support for newer hardware.

---

### Post by jml on 2011-07-02
Just to add my two cents worth.  In part, it depends on which version of the Starling you own.  The first generation Starling (STAR1) had a real wireless performance problem with all Linux distros, including Ubuntu. To get the wireless to work properly,you needed to have System 76's driver to fix the problem.  That required the use of Ubuntu. Straight Debian installed just fine on the Starling,all hardware was recognized, but the wireless performance was not very good.  I have read that newer versions of the Starling had a less finicky wireless card.

I agree, try before you install.  If you have a USB optical drive, download the live version of Debian, burn it to a disk and see if it works to your satisfaction.  That is how I knew that Debian would not work on my STAR1.  I do not think that Slackware has a live disc.  So running that in a VM may be your only choice.

And do not worry about screwing up your original install. You can always reinstall straight Ubuntu, and then go to the System 76 site to reinstall the System 76 drivers.  There is a how to on their website.

---

