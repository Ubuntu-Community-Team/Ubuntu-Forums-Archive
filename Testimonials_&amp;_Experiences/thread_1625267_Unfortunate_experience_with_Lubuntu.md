---
title: "Unfortunate experience with Lubuntu"
date: 2010-11-18
forum: Testimonials &amp; Experiences
---

### Post by SeePU on 2010-11-18
Here is a polite description of my unfortunate experience with Lubuntu.  I congratulate the attempt to implement LXDE in an Ubuntu base to create a specific LXDE flavor of Ubuntu.  I initially liked LXDE as a lean, low-resources DE.  I was looking for a low-resources DE for an old laptop and old desktop.  LXDE seemed to fit the bill.  I entertained the idea of xfce which, ironically, I will try next.  I have been told or informed that xfce is very close in resources or at least, feel, to Gnome but no way to find out but to try it, right?  Anyway, back to the report on trying Lubuntu.

Lubuntu seemed pretty good at first until many 'bugs' were discovered.  I reported these on the Launchpad and Bug Reporting sites as requested.  These aren't the sources or main reasons for my disappointment, though.  I recently ran into some sort of problem that is difficult to describe.  I could or maybe should highlight and report the issue but I am afraid it might be a waste of time.  I am greatly concerned with the amount of feedback or attention given these reports.  Anyway, my Ubuntu install got 'corrupted' (for lack of a better description) and I cannot access folders or files.  There's an error message received.  I needed to save or move/copy various files/folders to an external drive but wasn't able to.  When I tried to access the files from my Debian LXDE partition install, I couldn't.  It's like there is some root or superuser restriction that I cannot even get to even when I try to use a root account.  When I switch to sudo and try to access the files via Lubuntu, it is unsuccessful.  I suppose I will resign myself that this is a major issue and if I am to make any progress with preserving the files, I will need to resort to the infamous Google!  But, the damage is done.  I will be switching to XFCE whether it's Xubuntu or whatever.  

My critique of Lubuntu and why I think it is warranted is because my Debian LXDE edition survived and worked much better.  There are many reports of other LXDE editions of other distros being pretty good.  Mint LXDE and others.  However, there were various obstacles or irritating predicaments or nuisances that were present in LXDE in general that convinced me to try xfce next time.  Even my Debian LXDE install is not my cup of team anymore so I am eager to give xfce a try.  I think LXDE had potential and maybe it still does.  But, I am so discouraged regarding it that I am not going to revisit it anytime soon.  If I read or hear of some encouraging words later on and there's a good justification for it at some point in the future, I might try a live CD/DVD but at this present time, I will give some other DE a spin.  Hopefully, xfce is a good balance between somewhat low resources and a user friendly DE that can permit some versatility.  

Thanks for reading.  This was longer than I intended but I thought I should give some detail rather than showing only emotion. ;)  If anyone would like the actual error messages or more specific info (RE: output of code for e.g.), let me know.  I could try to obtain it but my laptop is in bad shape.  It's on a countdown to inevitable extinction. ;)

In summary, I felt that Lubuntu was not as solid and seemed to easily get corruped while the Debian LXDE edition on another partition was able to stand up to any outside influence.  Also, I am concerned about the support.

---

### Post by johntaylor1887 on 2010-11-18
That's a much better post. ;) Thanks for sharing.

But considering there are literally 1000's of hardware configurations in the world, it's only inevitable that sooner or later you are going to find a distro that won't play nice with *your* specific configuration. For every person that has a bad experience with a specific distro, I'm sure there are 1000's that *don't* share your experience based on *their* hardware configuration. It doesn't mean it's bad, it just means it wasn't meant for *your* computer.

Just find what *does* work, and be happy we have so many choices.

---

### Post by ventrical on 2010-11-19
> **johntaylor1887 said:**
> That's a much better post. ;) Thanks for sharing.

But considering there are literally 1000's of hardware configurations in the world, it's only inevitable that sooner or later you are going to find a distro that won't play nice with *your* specific configuration. For every person that has a bad experience with a specific distro, I'm sure there are 1000's that *don't* share your experience based on *their* hardware configuration. It doesn't mean it's bad, it just means it wasn't meant for *your* computer.

Just find what *does* work, and be happy we have so many choices.

  I agree, I would just like to know  what the PC specs are of the OP. The reason is that I have Lubuntu running on an HP Pavilion, 733MHz with 256DRAM on a 10GB HDD, that currently works great at the moment , but perhaps I could stave off problems in the future.

It is obvious that the OP has  a lot of experience with Lubuntu so perhaps there are bugs there that I have not yet come across.

---

### Post by 3Miro on 2010-11-19
LXDE is under heavy development, so naturally it is the most unstable of the DEs and furthermore different distros may have different stages of LXDE (i.e. if Debian is using something newer, it will be better).

For XFCE, in many cases, distributions will combine XFCE with many components from Gnome, which can even lead to XFCE being heavier than Gnome. On a good XFCE build, it will be a little bit more resource conserving than a minimal Gnome without effects, however, the XFCE window manager has many more features. Also, Thunar is much lighter/snappier than nautilus, to the point that even when I use Gnome, I usually end up using Thunar. XFCE panel has fewer features than Gnome panel, however, it uses less resources and is less buggy. The rest is just the applications that you decide to use that are DE independent.

A new version of XFCE (4.8) will come out soon and it will have many new features.

---

### Post by ventrical on 2010-11-24
I doubt if this will help , but, I had a Lubuntu experience where I was shut out. The opening screen would come up and then I would enter my user_name and then password and the opening screen would pop right back up. So, I went into the Recovery mode from the GRUB boot menu and was given several options. One of the options was to <fix broken pipes> to this effect. So I chose this first. <Note - you have to be hooked up to internet with Ethernet Wired>. The program proceeded to run it's update script and I noticed that there was a warning  that device was <out of space>.

 I rebooted then and tried the <clean> <try to free space> option on the recovery boot menu, then rebooted and I was able to log on with a breeze!!

  I found out that all of the hullaballoo was due to three things.

1. I actually ran out of space on my 2 GB pendrive.
2. Tha avgd <anti_virus daemon> was running on start up.
3. That the Chrome Browser had the wrong flash_install pkg because there are two different flash_pkgs, one for Google Chrome and the other for Open Source Chorme.

Result!! End_user inability led to malfunctioning system. I found at first that it  would be so much easier to just blame it on a buggy install or buggy OS, but, NOPE .. in fact the whole OS installation has a superior recovery mode  system built in  that can be launched from the GRUB boot loader.

  Again , great work you guys at Lubuntu. My only suggestion would be to try Firefox as the default browser with the distro  and not Chrome.

regards..

---

### Post by overdrank on 2010-11-24
Thanks for sharing.  Thread closed.

---

