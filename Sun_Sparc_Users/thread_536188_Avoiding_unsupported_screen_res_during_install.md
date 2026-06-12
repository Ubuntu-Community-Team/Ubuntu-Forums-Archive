---
title: "Avoiding unsupported screen res during install"
date: 2007-08-27
forum: Sun Sparc Users
---

### Post by timji on 2007-08-27
I'm trying to install Dapper from the text-mode server CD on an Ultra 10, which runs Solaris 9.* without problems.

After booting from the CD, I can read the initial banner screen just fine, but shortly after I press ENTER to begin the install, my screen goes black and an "unsupported resolution" message appears.

I'm using  a 17" PC-style LCD monitor, with the usual (non-Sun specific) resolutions available.

How do I tell the instalation procedure to use only PC-style resolutions?

---

### Post by timji on 2007-08-27
I just tried the Feisty live-install CD, and immediately after showing "Booting Linux" on the screen,
the screen resolution shifts to something outside the range of a standard PC-style monitor.
So same problem I reported with Dapper.

Is there a  kernel option (like "linux res=1024x768")  I can use to get around this problem?

---

### Post by netztier on 2007-08-28
> **timji said:**
>  Is there a  kernel option (like "linux res=1024x768")  I can use to get around this problem?

At the **ok>** prompt (hit Stop-A on the Sun keyboard to get there), use the **setenv output-device screen:r1024x768x60** command, and use values for **horizontal x vertical x refresh-rate** that match your monitor's capabilities. Not all weird combinations are allowed, but the most common ones are. After that, issue the reset-all command so the machine reboots. This has worked for me on all my U60s and the U5, so they all deliver 1280x1024@60Hz to my 17" TFT.

You can check how output-device is configured with  the **printenv output-device** command.

If your machine has an ATI adapter (such as Ultra 5, Ultra 10, mabye also the Blade 100 and Blade 150), you can also pass **video=atyfb:1024x768@60** to the Linux kernel as boot option.

(some content  stolen and adapted from the Gentoo FAQ: [http://www.gentoo.org/doc/en/gentoo-sparc-faq.xml](http://www.gentoo.org/doc/en/gentoo-sparc-faq.xml))

best regards

Marc

---

### Post by timji on 2007-08-28
Setting video=atyfb:* did the trick; thanks, netztier!

However, despite the fact that I tell the installation program that my keyboard is a Sun Type 5 (it's a  5c
actually), it's misinterpreting my keystrokes in the IP address input field. 9 sends "r", etc.

Any ideas about how to fix this?

---

### Post by netztier on 2007-08-28
> **timji said:**
> Setting video=atyfb:* did the trick; thanks, netztier!

However, despite the fact that I tell the installation program that my keyboard is a Sun Type 5 (it's a  5c
actually), it's misinterpreting my keystrokes in the IP address input field. 9 sends "r", etc.


old story: dont' select sun type5 but pc104 or pc105. The 2.6 kernels have introduced this change. The same will apply when running X.org: configure a standard 104 or 105 key PC keybord.

A slight forum search might have helped, actually.

Veeeeeeeeery old story.


best regards

Marc

---

