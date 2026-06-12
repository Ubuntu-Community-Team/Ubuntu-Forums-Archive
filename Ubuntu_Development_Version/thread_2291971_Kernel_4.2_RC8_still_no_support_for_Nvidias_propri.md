---
title: "Kernel 4.2 RC8 still no support for Nvidias proprietary driver ..."
date: 2015-08-24
forum: Ubuntu Development Version
---

### Post by xeizoo on 2015-08-24
Maybe thats one reason why Linus called off a final release for 4.2? Seems to be a licensing issue in the kernel, not allowing non-GPL drivers to use some of the essential code. This sucks, as any graphics card barely works at all for modern 3D gaming using GPL drivers. The proprietary drivers are the only that can rival Windows in 3D performance. Why use a 3D card if your only going to be looking at a desktop and a terminal? I think sometimes the GPL folks goes to far and pushes folks towards Windows .... Ok blame Nvidia/AMD for not releasing the full source, thats contra productive anyway as there are no high performance fully open source 3D hardware as an alternative.

Just a rant, but I think kernel devs should set a higher priority for 3D working as it should as early as possible in development ;)

---

### Post by grahammechanical on 2015-08-24
There is a Ubuntu kernel team meeting on Tuesday 25th August 17.00 - 18.00 on IRC at #ubuntu-meeting. You might want to follow the discussion. The minutes of the meeting will then be published on Planet Ubuntu and Voices Canonical. Here are the minutes from the last meeting. They show the status of the kernel in wily.

[http://voices.canonical.com/kernelteam/2015/08/](http://voices.canonical.com/kernelteam/2015/08/)

Windows gaming has pushed the need for ever more powerful hardware. This issue is important to you but it means nothing to me. My hardware is old enough for my video adapter to no longer be supported by the latest Nvidia drivers. And that is not a problem because I have absolutely no interest in gaming.

I knew from the moment I first installed a Linux distribution that it takes a while for the Linux developers to bring in support for the very latest hardware. That was one of the reasons I did not purchase the latest hardware. The other reason was that I did not want to spend the money on the latest machines.

I am saying these things so that you understand that you are not the only person with a voice. And I may or may not agree with you.

Regards

---

### Post by JMB74 on 2015-08-24
Ubuntu have applied the fix in git for their 4.2 kernel at least

[http://kernel.ubuntu.com/git/kernel-ppa/mirror/ubuntu-wily.git/commit/?h=master-next&id=b13ceb87dafd75bbb8f619fbf6301778001f903b](http://kernel.ubuntu.com/git/kernel-ppa/mirror/ubuntu-wily.git/commit/?h=master-next&id=b13ceb87dafd75bbb8f619fbf6301778001f903b)

---

### Post by dino99 on 2015-08-24
RC7 at least works fine with nvidia-355 (4.2.0.5.5 from canonical-kernel-team), so RC8 will also when the build will be done

---

### Post by xeizoo on 2015-08-25
> **dino99 said:**
> RC7 at least works fine with nvidia-355 (4.2.0.5.5 from canonical-kernel-team), so RC8 will also when the build will be done

Thanks! I knew things where cooking, adding kernel-team ppa and the new graphics-drivers ppa( [http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action) ) I finally got 4.2 up and running with my Nvidia card! So I guess the next releases in the normal repos will work as well :D

**BUT **not all well with the 4.2.0-6.6 kernel, Nvidia do work alright but it can't drive my integrated network(Realtek), possibly because of the same non-GPL status of Realteks driver? A computer without network is of no big use, so still stuck with the 4.1.6 kernel  GAAH! ...

---

### Post by dino99 on 2015-08-26
which network-manager version ? (i've already posted a couple days ago that the newest 1.0.4 is not working (see my post))

---

### Post by xeizoo on 2015-08-26
> **dino99 said:**
> which network-manager version ? (i've already posted a couple days ago that the newest 1.0.4 is not working (see my post))

Thanks, tried the downgrade as suggested in your thread but didnt work, Im on 64-bit.

---

### Post by syntaxerror74 on 2015-08-28
Dumb question: which NV prop. driver would you recommend for us Linux 3.x people?
Gotta admit that I just grabbed the latest one from nvidia.com. But all I got was a beautifully black screen. :P

Side-note: Nouveau seems to be getting worse and worse as well. Older machine with FX6200 card never made it to LightDM, I was almost about to jump into the monitor, in that instant of wrath...
And nooo, card is not "broken". I think nouveau just tries to force a resolution on that card that is WAY too high in the first place. However, latest (stable) version seems to now completely ignore the *video=....* line given to kernel line. Tracked down nouveau's activity (by booting in debug mode) and indeed, it used 1600x1200 framebuffer (?!??). And this is a *desktop *PC, ladies & gentlemen...FB is for notebooks. Also, it complained something cryptic about "GPU lockup".

So it's on you guys now to wonder why I really want to ENTIRELY replace that nouveau junk by NV's driver. In time terms, the hours of troubleshooting that the former driver has cost me would easily add up to a whole week.

---

### Post by aljosa2 on 2015-09-01
[Kernel – 4.2 Final – Still Breaks NVIDIA]("http://rglinuxtech.com/?p=1550")

Tested the 4.2 Final kernel, and the later NVIDIA drivers still fail to install, with the same GPL-only error..

A simple patch to fix this was proposed for 4.2-rc5, some time ago, but – for some reason – has failed to make it into the ‘final’ release..’

Details of the patch are here: [http://lkml.iu.edu/hypermail/linux/kernel/1508.0/02260.html](http://lkml.iu.edu/hypermail/linux/kernel/1508.0/02260.html)

Maybe this will be fixed in 4.2.1, but maybe we have to wait for 4.3-rc1?

*Robert Gadsdon.   August 31, 2015.*

---

### Post by dino99 on 2015-09-01
i'm using 4.2.0.7  kernel (canonical kernel team) with nvidia-352 : no problem (as usual  :p )

---

### Post by xeizoo on 2015-09-01
> **dino99 said:**
> i'm using 4.2.0.7  kernel (canonical kernel team) with nvidia-352 : no problem (as usual  :p )

Yeah, but as obvious from previous posts so does kernel-team:s kernels include the patch, which is not the case with official kernels nor the source.

Also, Realtek integrated LAN still doesn't work in kernel 4.2.0-7.7, now running Liquirix 4.1.6 which at least has a lot faster USB file transfers(+30-40%) than the Ubuntu kernel and everything works. Maybe Liquirix will release the first fully functional 4.2.0 kernel?

Why did Linus release the kernel when a lot of common network adapters doesn't work in it, and many Nvidia cards? Has standards gone down lately?

---

### Post by dino99 on 2015-09-01
if you give a ref for the faulty chipset, then someone will be able to check for a patch on lkml :o

---

### Post by xeizoo on 2015-09-01
Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 11)

So Ubuntu released a separate Realtek 8168-dkms package, didnt solve anything though, it compiled alright but still no internet. It even destroyed internet for 4.1.6 as well. Had to be removed, so far kernel 4.2 look like a real lemon ...

---

### Post by rrnbtter on 2015-09-06
Greetings,
> **dino99 said:**
> i'm using 4.2.0.7  kernel (canonical kernel team) with nvidia-352 : no problem (as usual  :p )

Same here! I am running a 4.2.0.7 with an Intel chipset and can't get the same speed with an earlier kernel. I know this post is supposed to be about Nvida but "no internet" isn't necessarily a Nvida problem. If you "the OP" have "Proposed" enabled in updates you may have just zapped you Network with the  1.0.4 Network Manager. If thats the problem downgrade it to 0.9.10 or just upgrade to 1.0.4 manually and see if it works. "apt-cache policy network-manager"  and see what you have.

---

### Post by xeizoo on 2015-09-06
> **rrnbtter said:**
> Greetings,


Same here! I am running a 4.2.0.7 with an Intel chipset and can't get the same speed with an earlier kernel. I know this post is supposed to be about Nvida but "no internet" isn't necessarily a Nvida problem. If you "the OP" have "Proposed" enabled in updates you may have just zapped you Network with the  1.0.4 Network Manager. If thats the problem downgrade it to 0.9.10 or just upgrade to 1.0.4 manually and see if it works. "apt-cache policy network-manager"  and see what you have.

I mentioned earlier in the thread I've tried downgrading already, problem seem to be kernel vs realtek which is also indicated by the new Realtek dkms-package from Ubuntu(which doesnt work, but seem to be an effort at least).

Good it works for you with Intel, but it's rather limiting hardwarewise.

Kernel 4.2.0.9 landed, still no network with realtek nic, 4.1.6 still works flawless with all other updates from today. Kernel 4.2 is very irritating!

---

### Post by dino99 on 2015-09-10
> **xeizoo said:**
> Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 11)

you should open a report against that 4.2 regression; as i know nobody have sent a request yet

---

### Post by xeizoo on 2015-09-11
> **dino99 said:**
> you should open a report against that 4.2 regression; as i know nobody have sent a request yet

Yes, looks like I have too, kernel 4.2.0-10 landed today and still no improvement. I guess all kernel devs are on Intel laptops these days and will never observe this regressen. The nic in question are the most common on gaming oriented mainboards, most of which runs Windows. Im one of the madhatters who games on Linux.

Done!

[https://bugzilla.kernel.org/show_bug.cgi?id=104411](https://bugzilla.kernel.org/show_bug.cgi?id=104411)

---

### Post by dino99 on 2015-09-11
One thing to know is: is it a kernel upstream issue, or only the custom ubuntu one.
You may also open a report on Launchpad (regression reason) and linked it to  the bugzilla one

---

### Post by xeizoo on 2015-09-14
Kernel 4.2.0-10.11 came, and still no internet. The new kernel 4.1.7 works fine though, I dont think Ill even bother trying the 4.3 RC. Something happened from 4.2 and onwards ...

I marked this thread as solved, as it is solved according to the thread title, I will start a new thread on the Realtek nic.

---

