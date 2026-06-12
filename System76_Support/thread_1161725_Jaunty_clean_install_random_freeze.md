---
title: "Jaunty clean install random freeze"
date: 2009-05-17
forum: System76 Support
---

### Post by Zxaos on 2009-05-17
Hi

I performed a clean install of kubuntu Jaunty a couple of days ago, and since then I have been experiencing random "freezes". The machine stops responding, and although I can move the mouse, I cannot cause anything to happen. I can reboot the machine using the rseiub code, but only that or powering the machine off and restarting can cause any difference.

This freeze appears to happen at random intervals, and occurs both with desktop effects enabled and disabled. I've found a couple of bug reports that seem to be about this issue but I was hoping for some concrete actions I might take to resolve it. Any suggestions?

---

### Post by thomasaaron on 2009-05-17
1. Which System76 model do you have?
2. Have you tried to run...
sudo apt-get install linux-backports-modules-jaunty
...?
3. Please go to System > Administration > System76 Driver > Support (tab) > Create (button). This will create an archive called logs.tar in your home directory. Please attach that archive to this thread.

I'll have a look at it and see what I can figure out.

We don't support Kubuntu, and I'm not getting any reports like that for Ubuntu. But maybe we can still figure it out with the logs.

---

### Post by Zxaos on 2009-05-17
Oops, forgot my model. I'm running a panv3.

I'll try the backports and the make the logs and report back.

---

### Post by Zxaos on 2009-05-19
Installing the backports has not resolved the issue. I've reinstalled the system76 driver (I had removed it after discovering that I did not need it). I'll restart my system and post the logs the next time the system freezes.

---

### Post by AugustinZ on 2009-05-21
Yes, I've got the same bug. Is there any solution?

---

### Post by AugustinZ on 2009-05-21
> 
I can find two different workarounds for this
[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)
or
[http://www.ubuntu-inside.me/2009/03/how-to-enable-uxa-at-ubuntu-jaunty.html](http://www.ubuntu-inside.me/2009/03/how-to-enable-uxa-at-ubuntu-jaunty.html)
 see [http://osdir.com/ml/kubuntu-users/2009-05/msg00474.html](http://osdir.com/ml/kubuntu-users/2009-05/msg00474.html)

Might help.

---

### Post by thomasaaron on 2009-05-21
Does pressing the space bar alleviate the freeze temporarily?

---

### Post by Zxaos on 2009-05-22
Of course, since installing the system76 driver so I can get the logs, I haven't  been able to replicate it. Next time it happens, I'll try the spacebar as well as grab the logs after I restart.

---

### Post by Zxaos on 2009-05-24
Ok, it just happened again. I was just reading feeds in Akgregator when the system froze completely. Pressing space did not temporarily alleviate the problem. I created the attached logs archive just after the machine was rebooted using the rseiub sequence.

---

### Post by Zxaos on 2009-05-24
In the meantime, I've enabled UXA in my xorg.conf. We'll see how things go!

---

### Post by thomasaaron on 2009-05-26
Since I'm not seeing this in Ubuntu Jaunty on PanV3 notebooks, I'm starting to suspect Kubuntu. 

It looks like your system ran a cron job, the wireless AP dropped the connection a minute or two later and then the machine just froze up, but that's about all I can see before you did the RSEIUB reset.

How do you have your router set up, and what wireless manager are you using?

---

### Post by Zxaos on 2009-05-31
My router is set up using WEP on a wireless g network. It uses DHCP, although the router is configured to always provide this machine's MAC with a specific address. I'm using the default network manager installed with Kubuntu - I'm not sure how to find it's name. Are there any specific settings you want me to check?

Now, I haven't experienced the issue since switching X over to using UXA. The system seems more stable although the performance seems to be worse overall.

---

### Post by thomasaaron on 2009-06-01
If that holds, it would definitely point towards x and not wireless. You might want to check out some of these, as I'm not really set up to test with Kubuntu...

[http://www.google.com/search?q=kubuntu+jaunty+random+freezes&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=kubuntu+jaunty+random+freezes&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

