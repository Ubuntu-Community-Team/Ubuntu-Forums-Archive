---
title: "How to dual boot Lollipop 5.1.1. and Ubuntu on Tablet?"
date: 2016-04-07
forum: Ubuntu Phone and Tablet
---

### Post by federicodemaria on 2016-04-07
Hi, 
I've been an happy Ubuntu user with my laptop for over ten years.

Now, I need a Tablet. The one with Ubuntu touch was too expensive for my budget, so that I bought a second hand Samsung Galaxy Tab A LTE 9.7.
It has Android (Lollipop 5.1.1.) and 2 GB RAM. Here all details: [http://www.samsung.com/it/consumer/mobile-devices/tablets/galaxy-tab-a/SM-T555NZWAITV](http://www.samsung.com/it/consumer/mobile-devices/tablets/galaxy-tab-a/SM-T555NZWAITV)  

**Could I manage to install a Dual boot with Ubuntu (be it Ubuntu desktop or touch)? **
If not, could I easily replace Android with Ubuntu Touch? 

I'm not a very experienced user, but in the past I had managed to install a dual boot with Windows and Ubuntu. 

On the web, I have found some information but no exhaustive responses and users experiences.  

DUAL BOOT
[http://askubuntu.com/questions/668286/can-i-get-ubuntu-on-a-samsung-galaxy-tab-a-t350](http://askubuntu.com/questions/668286/can-i-get-ubuntu-on-a-samsung-galaxy-tab-a-t350)
[http://askubuntu.com/questions/359163/installing-ubuntu-touch-on-a-samsung-galaxy-tab-2-p3113](http://askubuntu.com/questions/359163/installing-ubuntu-touch-on-a-samsung-galaxy-tab-2-p3113)
[http://www.phonearena.com/news/Ubuntu-Touch-gets-official-dual-boot-with-Android_id50662/comments](http://www.phonearena.com/news/Ubuntu-Touch-gets-official-dual-boot-with-Android_id50662/comments)
[http://www.xda-developers.com/dual-boot-on-android-a-power-users-holy-grail/](http://www.xda-developers.com/dual-boot-on-android-a-power-users-holy-grail/)

I have found these guidelines, but it says it's only a "tech preview for developers", so I guess not for me.  
[https://wiki.ubuntu.com/Touch/DualBootInstallation](https://wiki.ubuntu.com/Touch/DualBootInstallation)

UBUNTU TOUCH INSTEAD OF ANDROID 
My device doesn't seam to appear on the list of supported devices ([https://developer.ubuntu.com/en/start/ubuntu-for-devices/devices/](https://developer.ubuntu.com/en/start/ubuntu-for-devices/devices/)) 
[http://www.pcadvisor.co.uk/how-to/linux/how-install-ubuntu-touch-image-3531970/](http://www.pcadvisor.co.uk/how-to/linux/how-install-ubuntu-touch-image-3531970/)
[https://developer.ubuntu.com/en/start/ubuntu-for-devices/installing-ubuntu-for-devices/](https://developer.ubuntu.com/en/start/ubuntu-for-devices/installing-ubuntu-for-devices/)

From what I understand, Dual Boot is difficult to install, while replacing Android with Ubuntu Touch shall be feasible. Any experiences? 

About Ubuntu touch, I'm not sure about its limitations. For instance, can you easily install common apps?

Thank you for your help

Best, 
f

---

### Post by grahammechanical on 2016-04-07
As I understand it, and I think that your research will confirm it, if the device is not officially supported then you are looking for a community port that may or may not have progressed to being useful. If there is not a community port available then you are looking at doing the porting yourself. If you are going to try porting Ubuntu for Devices to that device, then my advice would be to become familiar with re-flashing Android back onto that device.

As regards what you call "common apps," there are a couple of threads in this section where I explain the situation in a manner that I think is clear to understand. I am not going to repeat myself again. So, the answer is simply, No. In the future the answer is, well, maybe.

Ubuntu Touch is not Ubuntu desktop squeezed on to a mobile device. It was never meant to be. Ubuntu for Devices (Touch) is a completely different approach to creating an OS for mobile devices. It has a different packaging scheme and security model as well as a different display server (Mir). "Common apps" (also known as X apps) are not packaged for Ubuntu Touch and their security model is not secure enough to be installed on a Ubuntu tablet.

Work is being done on the Ubuntu convergence vision that would include a method for installing X apps in a Linux container so that they can run on Ubuntu without compromising security. How well this will work and how many apps it would apply to is unknown .

Regards.

---

### Post by federicodemaria on 2016-04-14
Thank you, your response is exhaustive. 

Yes, my device is not officially supported. 

I shall investigate what a 'community port' actually means, I had never heard of it before.

For what I understand now, it looks like I'll have to wait a bit more. 

Thank you once again

Best, 
f

---

