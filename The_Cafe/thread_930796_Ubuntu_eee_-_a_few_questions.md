---
title: "Ubuntu eee - a few questions"
date: 2008-09-26
forum: The Cafe
---

### Post by ZankerH on 2008-09-26
My eee pc 901 arrived today, and after fiddling around with the basic desktop mode for a bit, which I view as entirely useless for anything but web browsing and basic office stuff, I've decided to switch to the advanced desktop mode, which ended up breaking my apt repositories, xorg.conf and the ability to boot into X (in that order). System restore, try again, similar results, repeat twice. Also, I can't change the keyboard layout to anything but UK, US or Chinese without having it reset the next time I reboot.

So I've decided to just install Ubuntu, which I'm much more familiar with, having used it on my main PC and my older laptop for a long time. Turns out there's even an entire sub-distribution for the eee alone. Great, right?

Wrong. According to [this](http://www.ubuntu-eee.com/wiki/index.php5?title=EeePC_901), a lot of important functionality is still missing. What I'd like to know, from anyone that's bothered with Ubuntu eee, is just how up-to-date that site is? Is it true that neither ethernet or wi-fi work out of the box? Also, I frequently use an external monitor, what about that?

I know I should just download the live flash drive image and give it a try, but with the current state of my internet connection, downloading 1Gb is going to be a multi-day endeavor at best, and I'd like to make sure it works like it's supposed to before I attempt it.

---

### Post by smartboyathome on 2008-09-26
Ubuntu default (not eee) doesn't work with the Eee PC by default. Theres eeeXubuntu and Ubuntu-eee which DOES work though. Also, there are some companies who will install Ubuntu on your Eee PC for you if you buy it from them (ZaReason is one of them, and whom I am thinking of going with when and if I get an Eee PC).

---

### Post by mister_pink on 2008-09-26
I got an eee 901 recently and ubuntu works on it just fine, but it will require some degree of tweaking. Have a look at array.org for the best help I've seen. It is true that there is no networking at all out of the box

As for external monitors, I've only looked into it very briefly and by default it works but only at a terrible resolution. With some xorg.conf fiddling I managed to get half way to a working state, but haven't put any more time into it yet seeing as I never use an external monitor anyway!

Finally, you could also consider using the latest intrepid development release. I believe there are a lot of updates in there that will improve matters. Note I haven't tried any of the eee specific releases, just plain old ubuntu

---

### Post by der_joachim on 2008-09-26
I installed EEEBuntu with NBR on my EEE900. The basic stuff worked out of the box. I had to fiddle around a bit to configure the webcam and I had to install cpufreqtools. Other than that, everything worked out of the box.

See [http://www.eeebuntu.org/](http://www.eeebuntu.org/) for more information.

---

### Post by hamishaus on 2008-09-29
I have a 901 and installed Ubuntu-eee quite successfully ([http://www.ubuntu-eee.com/](http://www.ubuntu-eee.com/)). You need to get the ACPI scripts from here: [http://forum.eeeuser.com/viewtopic.php?id=39341](http://forum.eeeuser.com/viewtopic.php?id=39341)

Install 8.04.01 and pretty much everything works. Then d/l the scripts (just the scripts nothing else needed) and run them. Then the buttons on the top work for Screen Off/On, BT Off/On, CPU % changing, Webcam Off/On. That's it! Nothing else req'd!

To fix screensaver not accepting password issue:
sudo chown root:shadow /sbin/unix_chkpwd
sudo chmod 2755 /sbin/unix_chkpwd 

HTH
Hamish

---

### Post by Johnsie on 2008-09-29
Anyone using an eeepc should use Intrepid Ibex (the version of Ubuntu that is being developed). I know it's still in development but it is much, much more eeepc friendly. Intrepid is being developed so that it works on eeepcs.

In Intrepedid alost everything works out of the box but in Hardy very little works. I've found intrepid to be quite stable so far as they are getting very close to completetion on that version.

---

### Post by Vadi on 2008-09-29
Keep in mind that Ubuntu-EEE is *not* an official ubuntu product, even though their website poses as such.

I know, it's misleading.

---

