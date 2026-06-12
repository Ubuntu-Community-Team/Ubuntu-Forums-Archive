---
title: "why is it soo hard to install ubuntu problem-free?"
date: 2012-03-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by nathan1337 on 2012-03-23
This is VERY frustrating
 
After last week spending 2 days screwing around with raid, it install properly
 
spent the following week installing and uninstall ubuntu 12.04 alternate version
 
awesome! now it will load into the login screen
 
30 seconds later, pink screen.. okey i'll wait another minute see what happens...pink screen. (just snapped my head phones in half)
 
okey, let's reinstall it a few more times with different boot options
i915.modeset=0 .. or 1
nomodeset
xforcevesa
 
neither worked, and now my keyboard is semi-functional
 
honestly, it's not my fault my computer isn't ancient, and it's not my fault I don't know how to fix it, why can't there be more options to perhaps download the drivers for the video card during installation, or perhaps default BOOTUP to boot in an all-round acceptable interface to the desktop until the user installs the video card??
 
anyway, if anyone has any other bright ideas, my specs are as follows...
 
GTX560 nvida geforce
 
and.. I cannot boot to a command prompt because it doesnt get that far... i can go in to recovery mode into command prompt however.
 
it doesn't hang, i can only see movement when i type(nothing that can be seen, it's like a broken display distortion screen)

---

### Post by Megaptera on 2012-03-23
Hi,
12.04 is stil in 'Beta' (testing) so there may be bugs and glitches. Have you tried the latest stable version 11.10?

---

### Post by markbl on 2012-03-23
> **nathan1337 said:**
> spent the following week installing and uninstall ubuntu 12.04 alternate version
Nathan, you really think it reasonable to publicly complain about a beta version of anything not being "problem-free"?

If you aren't willing to accept compromises on quality and stability then you should not try any beta version. Most of us don't touch a new Ubuntu version until it is formally released.

---

### Post by Splooshie123 on 2012-03-23
Since you're installing a development version, that contributes to the problem.

Another factor is the millions of hardware configurations available make it very difficult (I lie. Its impossible) to create one OS that runs perfectly on all.

Take a look at Apple, they create both the hardware and the OS. Because they know for sure what hardware the OS will be running on, they can fine-tune it to run perfectly.

Now take a look at Microsoft, their Windoze OS runs out-of-the-box on most systems but only because most systems come with the OS pre-installed by the manufacturer. The manufacturer pre-installs the system and I think they use customized versions that run perfectly on their hardware.

Finally, take a look at Linux in general. Except in special cases, you usually end up installing from a single generic version. No custom-tailored Ubuntu for, say, an HP laptop or whatever.

When installing Linux, it helps to be prepared to spend a bit of time to get it all working.

When installing an experimental version of Linux, it is REQUIRED for you to be prepared (Isn't that why you installed the development version? to test it?).

---

### Post by Bucky Ball on 2012-03-23
Wait for a couple of months after 12.04 LTS is released and try again.

In the meantime, try a stable version. 10.04 LTS is rock solid with support until April 2013 (and a one click upgrade to 12.04 LTS when you're ready). 

As mentioned, a lot depends on your hardware to start with. If you boot from the regular desktop LiveCD, 'Try Ubuntu' and everything works okay (but probably not wireless until you've done a hard drive install) then you're good to go.

---

### Post by cariboo on 2012-03-23
If you really want a trouble free install, break your raid array apart, and just install to one of your hard drives. For a desktop installation, there really isn't any advantage to using a raid array. For the small amount of speed increase using raid 0, or using raid 1 or better, you're still going to need to do proper backups to make sure your data is safe.

Whatever you've learned using Windows really doesn't transfer to using Ubuntu. especially when using non-standard hardware set ups. I'd suggest you spend an equal amount of time learning to use Ubuntu, as you spent learning to use Windows, then try installing on non-standard hardware systems.

---

### Post by effenberg0x0 on 2012-03-23
As you begin to use Linux and, hopefully, Ubuntu you get some notions that are very different from the Windows universe:

- Although Ubuntu has improved greatly in recently years and raised the bar in the Linux world, it is not *always* as easy to setup as Windows. It's harder for Linux developers to make it *alwys* work out-of-the-box, as hardware manufacturers many times do not release specs to Open Source developers. Yet, mostly any hardware can be made to work. Just don't expect it to *always* be something WYSIWYG, "Click-Here-To-Create-A-Datacenter", etc. 
- There's more than one way to do things. What you consider to be "broken" (ex. not having an accelerated desktop activated), other user might consider a feature (server, low-end machine). Windows activates sound, video acceleration, etc in servers, which makes no sense in most cases, and we waste a lot of time disabling those. 
- 99.9% of the problems and doubts you may have are answered repeatedly in many forums, blogs, etc. Simple 10-second Google searches are enough to a Google search. Eventually you get to a point in which if you Google something and can't find an exact match in less than 5 minutes, congratz, you find a new undocumented bug. You'll get more proficient in finding relevant info.
- After you use Ubuntu for a couple months, you're able to fix most Ubuntu problems with little effort, no focus, while doing other stuff. Suddenly you realize that you don't think too hard anymore, everything just works perfectly, fast and reliably for you, and some people are struggling to see something in the screen. It's not the OS that improved just for you, it's you that by then will be aware of what you are doing and doing correct procedures seemingly.
- Finally: As other mentioned, development releases are not for those that just want to get the thing to work. Even the development releases of Windows are broken. If you have something important that you need to accomplish, just boot to Windows or a stable release of Ubuntu. Don't stress over it too much. Learn and test when you can afford to without getting too stressed.

Regards,
Effenberg

---

### Post by Quackers on 2012-03-23
My laptop came with raid0 enabled by default. As cariboo907 has stated, it really isn't worth keeping for its supposed performance "gain". It stops certain backup software working (or restoring) too! I ditched my raid some time ago and now just enjoy the 2 separate drives.
It does mean that you'll need to re-install Windows though (if you are keeping it) but you may enjoy more trouble-free computing.

---

### Post by jerrylamos on 2012-03-23
> **effenberg0x0 said:**
> As you begin to use Linux and, hopefully, Ubuntu you get some notions that are very different from the Windows universe:

- Although Ubuntu has improved greatly in recently years and raised the bar in the Linux world, it is not *always* as easy to setup as Windows.

I don't know what rock I've been living under, but "installing" any level of "Windoze" takes hours and hours for me.

"Windoze 7" said I could make backup DVD's.  Four of them! hours later got done.

Sure enough, an ubuntu install thoroughly screwed up boot couldn't get anything so I re-installed "Windoze 7" from the four DVD's.

Wow....hours later, I got to mess around with gparted since Windoze 7 always takes all the primary partitions and all of the 250 GB of disk.

Finally free enough space for linux again.

Some months later, "precise pangolin" install totally borked boot couldn't even read the initial screen.

Solution?  Bring up Lucid Lynx CD live, install into a spare partition, fixed grub so I could boot again.  Note the various methods of "rescue" did not fix grub and particularly any attempt to use Live to do a grub-install wouldn't work at all.  Installing to a spare partition avoided the hours and hours to restore Windoze 7 again.

Even quicker solution: Open the case, remove Windoze 7 hard drive, plug in a spare 100 GB hard drive to fool around with unstable ubuntu.  Much much faster!  

I still have the Windoze 7 if my wife needs it to support web sites with proprietary software not available with linux. 

My Compaq tower came with Windoze Vista.  First boot of the installed from factory Windoze took a good half hour..

Jerry

---

### Post by grahammechanical on 2012-03-23
Six years ago when I was looking to try out Linux I did some research (reading Linux magazines) I was advised not to expect Linux to *work out of the box* on new hardware.

I was advised to check for Linux compatibility.

Has anyone in Linux ever claimed that Linux will work on the very latest hardware?

Ubuntu is just a distribution. It relies a lot on the work of others and they are playing catch-up all the time.

There is a way for a Ubuntu install to be trouble free. Strictly limit the hardware that it can be installed on. We would not like that would we?

Regards.

P.S. My first install of Ubuntu on my self-built machine was trouble free. Now why was that?

---

### Post by Bucky Ball on 2012-03-23
> **grahammechanical said:**
> 

P.S. My first install of Ubuntu on my self-built machine was trouble free. Now why was that?

Exactly. I've even written a HOWTO on that very topic (though dated now). There is a link in my signature. ;)

PS: It was a little tricky on my new HP laptop with 7.04 five years ago but with help and persistance I nutted it out. When I installed on my home-made desktop though I got lucky and that was a breeze. Worked straight off (and it has pretty much been the same ever since because all new computers since then, self-built or laptops, have been chosen with Linux in mind).

---

