---
title: "[SOLVED] Clarification re: virtualbox"
date: 2009-01-10
forum: Virtualisation
---

### Post by dyingsun on 2009-01-10
Hey all

I have two physical HDDs, one with Ubuntu (preferred OS) and one with XP (occasionally needed OS). I want to be able to run the XP installation in Virtualbox to save rebooting. I'm considering the enterprise version of virtualbox because afaik that is what you need for USB support?

Just a couple of questions -

How much does enterprise Vbox cost? Cant seem to find that out - Sun seems a bit cagey about giving out details!

Will I have any trouble sharing files between Hardy and XP? Last time I had to poke files through a writable shared folder, which is a pain.

Lastly, when you create a virtual disk with vbox, is it actually storing the entire target install in this image, or just parameters? i.e. would I, in effect, be storing the XP installation twice? I have 2x250gb HDDs, so there's no space issues yet, but there's a lot of video work coming up and that may change.

I've seen the Virtualisation mega-thread and will be using it as a guide to getting all this done, but these are the things I need to know before I commit any dollars to it (struggling farmers don't have much cash to bandy about! :)

I know these are not hugely ubuntu-centric questions, but this is the forum I trust for decent answers!

Thanks!

---

### Post by HotShotDJ on 2009-01-11
> **dyingsun said:**
> I'm considering the enterprise version of virtualbox because afaik that is what you need for USB support?All you need is the Personal Use (PUEL) version.  Although it is not open source, it is free of charge for personal use.  See: [http://ubuntuforums.org/showthread.php?p=6398716](http://ubuntuforums.org/showthread.php?p=6398716) for instructions on how to install the proper version and enable USB support.

> **dyingsun said:**
> Will I have any trouble sharing files between Hardy and XP? Last time I had to poke files through a writable shared folder, which is a pain.Setting up shared folders is very easy with current versions of VirtualBox.  It is now handled through the GUI settings menu.  You can also use SAMBA if you really want to.  But it is more complex and can open security holes in your system if you don't know exactly what you are doing.
> **dyingsun said:**
> Lastly, when you create a virtual disk with vbox, is it actually storing the entire target install in this image, or just parameters? You can set up VirtualBox to use an existing XP installation.  Normally, you would install the guest OS on a virtual disk, which will contain the entire guest installation.

If you opt to use an existing partition, be sure to read the [User Manual]("http://download.virtualbox.org/virtualbox/2.1.0/UserManual.pdf") and heed the warnings.  [A step-by-step howto]("http://ubuntuforums.org/showthread.php?t=984437") has been written to help you set this up.  But be warned, you can SERIOUSLY mess up your Windows set up if you are not VERY careful.  I don't recommend this method, but it is available to you.

---

### Post by dyingsun on 2009-01-11
Thanks for your reply HotShotDJ, that clears things up a lot for me!
I had a go at virtualising my XP installation - it didnt work, got a GRUB error (25). I tried doing it with MBR, as mentioned [here]("http://ubuntuforums.org/showthread.php?t=769883"), but that hasnot worked either, just hangs. Luckily I can still boot into my existing XP partition! I'll have another lash at it in a little while, after checking out your links, probably need more help, but I guess that's for another thread :) Thanks again.

---

