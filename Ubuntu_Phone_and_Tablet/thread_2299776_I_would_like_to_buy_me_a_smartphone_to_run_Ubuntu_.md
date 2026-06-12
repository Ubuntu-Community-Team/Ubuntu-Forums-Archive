---
title: "I would like to buy me a smartphone to run Ubuntu alongside Android"
date: 2015-10-21
forum: Ubuntu Phone and Tablet
---

### Post by LastStarDust on 2015-10-21
Hello,
I am about to take the leap and buy me a smartphone. For the time being I prefer to buy an android phone, only because of the wider app availability. I am here because I would be happy to have a phone able to dual boot into Ubuntu Phone OS too. I know it is possible, but even after reading some articles scattered online, there are some things still unclear to me.


[LIST]
[*]**QUESTION : What is the best buy, given that ... ? **
[/LIST]



[LIST]
[*]REQUIREMENTS (in order of importance):
[/LIST]


[LIST=1]
[*]Ubuntu Compatibility: Ubuntu Touch can be installed and can provide the most basic functions as calls, messages, wifi-bluetooth-3G.
[*]Long Term Support: I want to keep my phone as long as I can so which is the hardware with the longest expected support (from canonical or from the community)?
[*]Budget: under ~150 euros. I am perfectly ok with a used phone.
[*]Connectivity: Sometimes I would want to plug the phone to a screen, mouse and keyboard and use Ubuntu Touch in a "desktop-style", is it possible?
[/LIST]

Thanks in advance for your advices

---

### Post by grahammechanical on 2015-10-21
Where do you get the idea that it is possible to dual boot Android and Ubuntu Phone? There once was a private project by some Canonical engineers and the code and method for doing this were made public but it has not gone beyond a technical preview. This wiki page explains the situation for Ubuntu Phone/Android dual boot.

> Ubuntu Dual Boot Installer is provided as a tech  preview for developers who want to run Ubuntu and Android on a single  device. **It is not intended to be used by regular users**, neither at this  point **nor as its ultimate goal**. Those developers installing it should be  familiar with the Ubuntu and Android partition layouts and should also  feel at home with manually flashing partitions in case something goes  wrong. 


Ubuntu  Dual Boot Installer was born as an internal skunkworks project some  Canonical Engineers dedicated a limited amount of their time to. Seeing  the good progress, it was decided to release this preview for the  developer community to test, study and contribute to.

[https://wiki.ubuntu.com/Touch/DualBootInstallation](https://wiki.ubuntu.com/Touch/DualBootInstallation)

As far as I know Canonical does not provide hardware support. That would be the responsibility of the Original Equipment Manufacturer. The OS and core apps on retail Ubuntu phones are supported for an indefinite period. Ubuntu Phones get updates to the OS every six weeks or so. In this way the OS is always up to date. For example, The first BQ Ubuntu phones had an OS built on Ubuntu utopic (14.10) code base. The latest Ubuntu phone models get an OS built on vivid (15.04) code base. But by updating those original BQ Ubuntu phones will be running on same OS as the latest Ubuntu Phone.

Keep in mind that Ubuntu Phone is a phone OS and not Ubuntu desktop squeezed into a phone, what you get if you have the right hardware is Ubuntu phone accessible through a mouse and keyboard and visible on a monitor. This video demonstrates the work being done but these features are not yet available on standard Ubuntu Phone OS. But all the Phone core apps are being designed to scale from phone screen size, through tablet screen size and up to PC monitor and TV screen sizes.

[https://plus.google.com/+WillCooke/posts/BWBndjXhzUt](https://plus.google.com/+WillCooke/posts/BWBndjXhzUt)

[http://www.noobslab.com/2015/02/ubuntu-touch-detailed-review-of-current.html](http://www.noobslab.com/2015/02/ubuntu-touch-detailed-review-of-current.html)

Regards.

---

### Post by handaxe on 2015-10-22
I thought there was the multiROM approach based in Android. At least that is what I recall in passing.

---

### Post by LastStarDust on 2015-10-22
Thanks a lot for your kind and quick answer. You made your point. Although I am familiar with manually flashing partitions on ARM devices, I am not a developer so, as you have pointed out, there is little if no use in installing Ubuntu on an Android phone for me. I was hoping to exploit both Android and Ubuntu strengths by having them on the same machine (as I do with Ubuntu and Windows on my desktop), but for the time being maybe it is too early.
Thanks again
Giorgio

---

