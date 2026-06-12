---
title: "Install nVidia 195 Ubuntu Studio 10.04 ...or...make everything excessively stupid day"
date: 2010-05-26
forum: Ubuntu Studio
---

### Post by WrinkledCheese on 2010-05-26
Hello,

Here's the short and sweet.  The Ubuntu Studio DVD seems to have the WRONG SOURCE installed for an AMD64 system. I'm not sure if this is AMD64 kernel specific.
Headers installed: 2.6.31
Kernel installed: 2.6.32

Someone tell me I'm wrong and need sleep.

Sorry if this is a bit ranty but.....my head is going to explode.

So I downloaded Ubuntu Studio 10.04, figured I'd give it another try.  I burn it, on my Slackware box after figuring out that I needed to install KD3 compatibility packages for K3B because they KNOW it's broken... Release notes says it's pretty much useless for anyone and to use the KDE4 K3B and to install the packages in extra...manually.  Anyway...enough Slackware stupidity.  I got it burned about 2 minutes later after making 2 coasters before reading release notes...

I installed it, and I updated my system and now I'm trying to get more than 800x600 resolution.  Drivers for my 6200 nVidia card are in order(195 driver).  I install it, it says "no kernel source installed"  So I look at the /usr/src and there is no linux symlink.  There are two folders that both seem to me to be source directories...

I look at the Synaptic description for these, to see which is which.  They are for kernel 2.6.31...  WTF  I said!  Didn't uname -r say I was running 2.6.32-22-preempt or something like that.  It sure as hell did.

After looking, and trying, 3 different packages that says Linux Source for version 2.6.32-22 I FINALLY find linux-headers-2.6.32-22-preempt.

I reinstall nVidia driver.  It builds.  I say:  What jackass installed 2.6.31 kernel headers for a distro release that has a 2.6.32 kernel installed?

Hope this ranty solution helps someone with an AMD64 trying to install Ubuntu Studio and then nVidia drivers for a 195(nvidia-current) driver.

P.S.  Did I mention I manually created the /usr/src/linux symlink?

---

### Post by WrinkledCheese on 2010-05-26
So I rebooted and everything works fine...seriously the wrong headers...

---

### Post by mango42 on 2010-05-26
Hi **WrinkledCheese** - sounds great for pizza, anyway ;-)

For us lesser mortals, could you please give us amd64/nVidia (7900GS SLI in my case) users a blow by blow account on how to fix this possible issue? That is, reel live chunks of terminal arcanery, aka 'code'? If your head is exploding and you're au fait with Linux, imagine the state-of-head with us old demi-semi-computerate musos... ;-)

Now let's see if I can remember that uname command whilst I boot up the amd64...:confused: - confused 'cos Jack is giving me loads of xruns without anything else loaded...

:popcorn:

---

### Post by WrinkledCheese on 2010-05-26
I installed the proper kernel source using Synaptic, after trying to figure out which source that was.  For me, it's the package titled "linux-headers-2.6.32-22-preempt"  If you check /usr/src you should have two directories with headers.  For me they were named "linux-headers-2.6.31-10-rt" and "linux-rt-headers-2.6.31-10".

Here is what I did step-by-step.  You can skip the lines listed as skipable so long as you didn't to them already ;)

-Installed fresh Ubuntu Studio 10.04
-Updated latest packages with update manager
-SKIP THIS:Installed nvidia-current <-doesn't build kernel module without proper source
-SKIP THIS:In terminal ran: 'nvidia-xconfig' <-causes bad X config so you get a prompt at boot saying your X needs to be reconfigured after showing you some X errors
-Run Synaptic
-look for the kernel headers for your current running kernel.  For me it was "linux-headers-2.6.32-22-preempt".  You can find out what kernel version you're running by typing uname -r  I  remember it by calling it "Unix Name Dash Revision"
-(re)install nvidia-current
-run 'nvidia-xconfig' in the terminal
-reboot

I forgot to mention that it's not all that complicated, but it's annoying as hell when you're being tricked into thinking there are already kernel headers installed, when they don't even match kernel version.

One thing I sure do miss is restarting X without a full reboot.

---

