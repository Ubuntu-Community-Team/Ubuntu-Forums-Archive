---
title: "Dansguardian VBlocking ALL Traffic"
date: 2010-05-20
forum: Ubuntu Christian Edition
---

### Post by johnathanamber on 2010-05-20
Hello everyone,

I've installed Dansguardian with the GUI and TinyProxy.

For some reason when it is turned on it blocks ALL traffic.

What do I need to do to fix this?

I have completely removed the three packages above and restarted and then reinstalled... same issue.

I've installed IPTABLES and FIREHOL... same issue.

I've stopped, autoconfigured and started... same issue.

What else do I need to check?

Thank you and God bless,
Johnathan

---

### Post by david_kt on 2010-05-20
> **johnathanamber said:**
> Hello everyone,

I've installed Dansguardian with the GUI and TinyProxy.

For some reason when it is turned on it blocks ALL traffic.

What do I need to do to fix this?

I have completely removed the three packages above and restarted and then reinstalled... same issue.

I've installed IPTABLES and FIREHOL... same issue.

I've stopped, autoconfigured and started... same issue.

What else do I need to check?

Thank you and God bless,
Johnathan

Tonight I will start to work on Lucid CE, and first thing offcourse I will take a look into dansguardian. I hope I could solve this issue.

DK

---

### Post by david_kt on 2010-05-25
I have finished making ubuntu-ce lucid repository, please check:

[http://ubuntuforums.org/showthread.php?t=1492885](http://ubuntuforums.org/showthread.php?t=1492885)

DK

---

### Post by johnathanamber on 2010-05-26
david_kt,

I got the repository setup and thus far it is working right.

I did upgrade the latest Dansguardian (2.5) but I get 'Transparent Proxy' is OFF and others are on... thus far it isn't hurting the internet experience... but then again I don't try to access things I shouldn't that would require content filtering. ;)

Any ideas?

Thank you and God bless,
Johnathan

---

### Post by david_kt on 2010-05-26
> **johnathanamber said:**
> david_kt,

I got the repository setup and thus far it is working right.

I did upgrade the latest Dansguardian (2.5) but I get 'Transparent Proxy' is OFF and others are on... thus far it isn't hurting the internet experience... but then again I don't try to access things I shouldn't that would require content filtering. ;)

Any ideas?

Thank you and God bless,
Johnathan

Could you try to launch parental control (dansguardian gui), stop dansguardian, and then start dansguardian again. See if the transparent proxy is ON now.

DK

---

### Post by johnathanamber on 2010-05-26
david_kt,

Thank you for the help. I have already tried that in that... was the 1st thing I did.

I also tried to autoconfigure as well.

What is the transparent proxy? What handles it?

Thank you and God bless,
Johnathan

---

### Post by david_kt on 2010-05-26
> **johnathanamber said:**
> david_kt,

Thank you for the help. I have already tried that in that... was the 1st thing I did.

I also tried to autoconfigure as well.

What is the transparent proxy? What handles it?

Thank you and God bless,
Johnathan

Transparent Proxy redirect all traffic from port 80 to port 8080. Otherwise, you have to set proxy for firefox to localhost, port 8080, in order to use dansguardian.

You might have other firewall/iptables running. Please disable/remove all other program that use iptables.

DK

---

### Post by johnathanamber on 2010-05-26
Ah, you hit the nail on the head... ufw was installed and I didn't know it.

Working on testing it out... will let you know. probably later tonight.

---

### Post by david_kt on 2010-05-26
> **johnathanamber said:**
> Ah, you hit the nail on the head... ufw was installed and I didn't know it.

Working on testing it out... will let you know. probably later tonight.

Ufw is installed, but normally not running. You could give me the output of this :

```
cat /etc/init.d/ubuntu_ce_firewall
```

DK

---

### Post by johnathanamber on 2010-05-26
david_kt,

That does return anything as the file is not found. I have a minimal Ubuntu installation. I didn't install from the Ubuntu Desktop CD or the UbuntuCE CD.

---

### Post by david_kt on 2010-05-27
> **johnathanamber said:**
> david_kt,

That does return anything as the file is not found. I have a minimal Ubuntu installation. I didn't install from the Ubuntu Desktop CD or the UbuntuCE CD.

But how did you install dansguardian-gui?
Please try this:

[http://ubuntuforums.org/showthread.php?t=1492885](http://ubuntuforums.org/showthread.php?t=1492885)

replace ubuntu-ce with dansguardian-gui

DK

---

### Post by johnathanamber on 2010-05-27
I am working on a script for a minimal Ubuntu installation... smaller and snapier than the distro on CD. Right now even with all of my apps installed... things are faster with compiz graphics running and I am using about 3.5 GB of space... although I have to admit that I am not sure how much space is used after a normal GUI install with all of my apps installed... I am sure it is bigger... it is slower... THAT I do know. Anywho...

After adding the repository I simply went through Synaptic and checked dansguardian-gui which selected dansguardian and tinyproxy.

Installed those.

Yesterday I uninstalled everything except iptables, only because it would also remove ubuntu-standard.

Right now I just selected dansguardian-gui, it then selected both tinyproxy and dansguardian to install as well.

**1st attempt after isntall:**
===============================================================
Once that installed I went to the 'Configure Parental Controls'

Transparent Proxy = OFF
Tony Proxy = ON
Dansguardian = OFF
Internet Sharing = OFF
===============================================================

**2nd Attempt:**
===============================================================
Stopped Dansguardian. Everything is OFF.
Started Dansguardian.

Transparent Proxy = ON
Tony Proxy = ON
Dansguardian = OFF
Internet Sharing = OFF
===============================================================

**3rd attempt:**
===============================================================
Stopped Dansguardian. Everything is OFF.
Autoconfigured.

Transparent Proxy = OFF
Tony Proxy = ON
Dansguardian = ON
Internet Sharing = OFF
===============================================================

**4th attempt:**
===============================================================
Stopped Dansguardian. Everything is OFF.
Started Dansguardian.

Transparent Proxy = ON
Tony Proxy = ON
Dansguardian = ON
Internet Sharing = OFF
===============================================================

**5th attempt to make sure all is well:**
===============================================================
Stopped Dansguardian. Everything is OFF.
Started Dansguardian.

Transparent Proxy = ON
Tony Proxy = ON
Dansguardian = ON
Internet Sharing = OFF
===============================================================

So for some reason it is working now... But I've uninstalled before... so not sure what has changed other than a reboot.

Thank you David for your time, patience and support.

God bless you brother,
Johnathan

---

### Post by david_kt on 2010-05-27
> **johnathanamber said:**
> 
So for some reason it is working now... But I've uninstalled before... so not sure what has changed other than a reboot.

Thank you David for your time, patience and support.

God bless you brother,
Johnathan

The reason is last time you use dansguardian-gui for karmic, it won't work. I just release the version for lucid, which is you are using now.

DK

---

