---
title: "Battery level incorrect"
date: 2015-06-26
forum: Ubuntu Phone and Tablet
---

### Post by RichardUK on 2015-06-26
I have a [Aquaris E5]("http://www.bq.com/gb/aquaris-e5-ubuntu-edition") HD and 'was' impressed with the battery usage. After two days, including a few phone calls, the battery level was @ 54%. Wow I thought. 20 mins later, phone died, would not boot. Plugged charger in, battery was in fact flat as a pan cake. After about 10 minutes where there was enough charge for the phone to turn on, it was reading 40%. Way of from what it was saying on the firmware battery level.

I was going to post a bug but I got lost in the launch pad options. 

So, first of all, any one else seeing this?

Ta. :)

---

### Post by tgalati4 on 2015-06-27
Understand that battery level for most phones is measured by voltage level of the battery.  The current (milliamperes) required to keep the phone running is not reflected in the % remaining.  So you can have a battery at 50%, but when you try to take a picture, the phone will shut off suddenly, because the battery could not supply enough current to the phone and the camera at the same time.  When you reboot the phone, the battery shows 48%.  This happens frequently with my Samsung SG3 and a Samsung replacement battery.

So it's possible that the battery is bad, or underrated for the phone.  Under Android, there are several apps that will log the battery's voltage, current, and power draw over time, so you can see the current spikes and resulting voltage drops.  I'm not sure what is available in Ubuntu to get similar information.

---

### Post by RichardUK on 2015-06-29
As the phone lasted so long after it's first charge I am sure the battery is fine. I suspect that the OS is using the wrong reference values for the battery or maybe as you say, it's underrated in that it falls to a level that is '50%' of the charge and the phone just gives up. In any event, dying @ 50% it is very bad for the user experience which I why I am asking here if anyone else has seen this with the Aquaris E5 HD?

---

### Post by Harald_Walker on 2015-07-07
There is a similar bug report for the MX4:
[https://bugs.launchpad.net/canonical-devices-system-image/+bug/1471913](https://bugs.launchpad.net/canonical-devices-system-image/+bug/1471913)

---

### Post by handaxe on 2015-07-08
All I hope is that the charge management does not hurt the battery while they sort it out...

---

