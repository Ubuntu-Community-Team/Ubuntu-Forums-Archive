---
title: "Nvidia Geforce 710M, Optimus: Low resolution screen only available then freeze"
date: 2014-01-03
forum: Ubuntu Development Version
---

### Post by Ramesh_Jude_Fernando on 2014-01-03
Hi I booted up Trusty 14.04 after the latest updates, and for some reason received a only low resolution screen available as you must configure your screen ... options.  Then it asked you to select something, but the mouse pointer and thus mouse/pointing pad on laptop wouldn't work. I might add one reason for the problem is I have Acer Aspire V3 771G which uses the Intel core i5-3230M processor along with NVDIA Geforce 710M with Optimus drivers. Note I am not an expert on Optimus but did install the 319 drivers and run the script as mentioned in [http://www.webupd8.org/2013/12/more-work-to-support-nvidia-optimus.html](http://www.webupd8.org/2013/12/more-work-to-support-nvidia-optimus.html) and it's links as I want to fully use my Optimus and 710M graphics capability rather than just the Intel chipset.

Strangely, after I  cold shutdown by just pressing the power button (Ubuntu is still smart enough to close all daemons and other drivers etc first before shutting down) I was able to reboot and get back into the login and now even be able communicate on Internet, as I am posting this message!

Any suggestions would be helpful for what went wrong?? would be helpful!

Two things, first to the moderators like Anne what's her name  who jump on people if we posted without checking previous posts, I did search "screen" and "low resolution" and didn't find any postings so I apologize if someone else has posted this problem, but I did not see it. #2 Anyone who tells me I am stupid to run Trusty in the first place  and the 319 NVDIA drivers with support for Optimus chipset and adding the repositories , look you need some people to take risk and test, if no one did, the Ubuntu developers  who work on Optimus chipset systems wouldn't be able to fix problems would they?

---

### Post by Ramesh_Jude_Fernando on 2014-01-03
Oh I think I made a mistake, if I am correct I have 331 drivers and running uname -a to get the kernel  I have
Linux ramesh 3.12.0-8-generic #16-Ubuntu SMP Thu Jan 2 16:09:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
regards,
Ramesh

---

### Post by grahammechanical on 2014-01-03
You are posting in the Ubuntu+1 section. So, welcome to this little group of stupid people who run Trusty Tahr. :) You have joined our club! In this section we post our experiences. Sometimes someone will have a workaround. But not always. Sometimes I advise people to expect problems. If we cannot accept that then it is best to await until release day.

By the way, I do not yet have Linux kernel 3.12.0-8. So, you are a little in advance of me. And your experience confirms a couple of things that I have noticed. Often an update/upgrade fixes things, and it often takes a reboot after an update to prove if something has been fixed or if something else has been broken. And there is something else. Some of us here like to take risks with development code.

Regards.

---

### Post by mc4man on 2014-01-03
works here with a 660m, maybe support for a 710m is lacking or the kernel you're using?
( 3.12.0-7-generic #15-Ubuntu SMP here.

Overall for general purpose & multimedia use see no reason to use the nvidia side, the intel side is better. Currently there is no vsync available using nvidia-prime, tearing is quite prevelant *everywhere*

---

### Post by cariboo on 2014-01-04
> **Ramesh_Jude_Fernando said:**
> Two things, first to the moderators like Anne what's her name  who jump on people if we posted without checking previous posts, I did search "screen" and "low resolution" and didn't find any postings so I apologize if someone else has posted this problem, but I did not see it. #2 Anyone who tells me I am stupid to run Trusty in the first place  and the 319 NVDIA drivers with support for Optimus chipset and adding the repositories , look you need some people to take risk and test, if no one did, the Ubuntu developers  who work on Optimus chipset systems wouldn't be able to fix problems would they?

The moderator's name is oldos2er, so you may want to apologize directly. For your second point, this is the U+1 sub-forum, if your thread didn't belong here, it would be moved elsewhere.

---

### Post by Ramesh_Jude_Fernando on 2014-01-17
Thanks for all your help. As my other posts states, I removed Nvidia drivers and just using the Intel chipset drivers, I assume these are generic. I think there is perhaps some problems with the Optimus chipset working with the drivers. Well not in a blame game, but it would be nice if NVIDIA was more open with their features and used open source. Hopefully, after Googling and finding this [http://arstechnica.com/information-technology/2013/09/nvidia-seeks-peace-with-linux-pledges-help-on-open-source-driver/](http://arstechnica.com/information-technology/2013/09/nvidia-seeks-peace-with-linux-pledges-help-on-open-source-driver/) perhaps Nvidia can be more open in the near future!

---

### Post by VMC on 2014-01-17
> **Ramesh_Jude_Fernando said:**
> Hi I booted up Trusty 14.04 after the latest updates, and for some reason received a only low resolution screen available as you must configure your screen ... options.  Then it asked you to select something, but the mouse pointer and thus mouse/pointing pad on laptop wouldn't work. I might add one reason for the problem is I have Acer Aspire V3 771G which uses the Intel core i5-3230M processor along with NVDIA Geforce 710M with Optimus drivers. Note I am not an expert on Optimus but did install the 319 drivers and run the script as mentioned in [http://www.webupd8.org/2013/12/more-work-to-support-nvidia-optimus.html](http://www.webupd8.org/2013/12/more-work-to-support-nvidia-optimus.html) and it's links as I want to fully use my Optimus and 710M graphics capability rather than just the Intel chipset.

Strangely, after I  cold shutdown by just pressing the power button (Ubuntu is still smart enough to close all daemons and other drivers etc first before shutting down) I was able to reboot and get back into the login and now even be able communicate on Internet, as I am posting this message!

Any suggestions would be helpful for what went wrong?? would be helpful!
...
Lately I had issues with nvidia having low resolution. One thing to check is the kernel. Are you using 3.13.0-3-generic? The newest 3.13.0-4-generic fixed one issue I had of freezing without using *nomodeset*. Now 3.13.0-4-generic works as normal, except now when I just install nvidia-304.116 it went back to low resolution mode. I couldn't change it. Then reverting to nvidia-173 fixed that issue. A state of flux, I suppose. Maybe a newer X is to blame.   nvidia-304.116 has always worked before.

---

