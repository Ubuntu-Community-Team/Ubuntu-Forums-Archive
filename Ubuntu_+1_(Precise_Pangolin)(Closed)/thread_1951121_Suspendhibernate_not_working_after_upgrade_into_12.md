---
title: "Suspend/hibernate not working after upgrade into 12.04 beta 2"
date: 2012-04-01
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by IamLight on 2012-04-01
Around 1 month ago I decided to install Ubuntu 12.04 beta 1. It was pretty stable for daily use.
note: after installing precise I never do system update nor installing the Nvidia driver. I just installed some software that I need because of the lack of internet connection.

At first, the suspend was working perfectly but hibernate was greyed out. Then I google for it and found this article:
```
http://askubuntu.com/questions/94754/how-to-modify-policykit-to-allow-hibernation-in-upower
```
I tried and finally can choose hibernate, and it also working perfectly.

After the release of beta 2, I decided to upgrade my machine. And last Sunday I do 'sudo apt-get dist-upgrade'.
There was no failure in upgrading, and from update manager I checked that my system is up to date. So I assume I already upgraded into Ubuntu 12.04 beta 2.

But the problem appears.. After upgrading, system suspend and hibernate not working anymore.
When I click suspend, the display went blank (with brown color in the background) and did not turned off completely. I tried to resume it by pressing 'enter', moving the mouse, even pressing the power button, but none of them work.
The same when I click hibernate. It went blank with "_" blinking in the top-left of the display.
The last effort I did was to hold the power button to shut it down :(

I tried searching in this forum but with no luck, that's why I decided to make a new one.

If anybody know how to solve this please let me know because I need to use suspend/hibernate.
And if I need to check something on my system please advise me and I'll post the result tomorrow because I did not bring my laptop right now.

Spesification:
Asus N43SL
Intel core i5
4 GiB RAM
Nvidia Geforce GT540M 2 GiB
Swap 4 GiB

Thanks in advance.

Regards.

---

### Post by cdizzle on 2012-04-06
I'm having an extremely similar problem with a fresh install of 12.04 on an Asus U46E (core i5, Intel graphics). Any help on trying to troubleshoot this would be appreciated.

EDIT 6 Apr: Latest updates fixed my problem!

---

### Post by cogumbreiro on 2012-04-06
I have an Asus U46E and some update broke suspend/resume and brightness/volume keys stoped being recognized.

As of yesterday the battery applet no longer shows and I no longer have the option to suspend. I am using GNOME 3.

EDIT: my failled attemps to "fix" the issue led me to turn off ACPI. Reverting configurations back to stock, made the problem go away, which means that an update fixed the problem.

---

### Post by OGpmpdog on 2012-04-06
Hardware variety is the spice of life!:p

I'm testing with a IBM/Lenovo T61 laptop...Hibernate/Suspend stopped working right at Alpha 2, about 3-4 weeks ago. Gnome-shell crashed more than it worked.

As of last night's updates, Hibernate AND Gnome-shell - even the extensions - work!! 

Gentlemen, please keep in mind that PP is still in development, and there will be breakages...your issues will probably be resolved within the next few days as updates will include fixes.

Peace.

---

### Post by vikrant82 on 2012-04-06
Some of you guys might have bumped into this. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/969883](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/969883)

---

