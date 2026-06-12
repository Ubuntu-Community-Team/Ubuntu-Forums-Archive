---
title: "Got My Serval last night too!"
date: 2009-04-14
forum: System76 Support
---

### Post by serval1 on 2009-04-14
What an awesome machine! 4 GB, 320GB 7200 HD, Q9000, non-glossy screen. Everything was functional from the time I set my username. I had a number of updates, and one of them hosed my Grub.lst. But luckily, there was a backup Grub.lst that fixed everything. The webcam works great. The only item is a dead pixel at the lower right, on the screen. This machine is fast. and solid. The keyboard has a very good feel. I need to set up my bluetooth headset now. the BT mouse just worked right away.

Virtual Box is giving me a little problem, but I think that will turn out to be a small instalation issue. Flash and java are right on the money with smooth video and audio. Java applets, that require the latest, work fine.

Overall an extremely good first impression.

---

### Post by thomasaaron on 2009-04-15
Glad you like the Serval. What are your VirtualBox problems? If it is USB support, I have a tutorial that should get that up and running.

---

### Post by serval1 on 2009-04-15
Yes, I really like this computer. I am impresed with how solid it is. Very good for travelling. I thought I read that the Serval had a USB port that allowed for charging or powering USB devices while turned off. Does mine have that feature? I cannot seem to find it.

My problem with Virtualbox is a permissions thing. I have not researched it yet, but the virtual machine fails with a mesage "Failed to open /dev/net/tun". I chmod 0666 /dev/net/tun, but it still does not work. I need to look at it more.

I love this screen....

---

### Post by thomasaaron on 2009-04-16
> Yes, I really like this computer. I am impresed with how solid it is. Very good for travelling. I thought I read that the Serval had a USB port that allowed for charging or powering USB devices while turned off. Does mine have that feature? I cannot seem to find it.

That was on a previous model.

> My problem with Virtualbox is a permissions thing. I have not researched it yet, but the virtual machine fails with a mesage "Failed to open /dev/net/tun". I chmod 0666 /dev/net/tun, but it still does not work. I need to look at it more.

Try...
sudo chmod -R 777 /dev...

I've not heard of that particular problem with VirtualBox, but I suppose a lot of other folks have...

[http://www.google.com/search?q=Failed+to+open+%2Fdev%2Fnet%2Ftun&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=Failed+to+open+%2Fdev%2Fnet%2Ftun&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by serval1 on 2009-04-18
Thanks Thomas. My Virtualbox issue was an incorrect default network setting. I change it to NAT, and now have a virtual machine running.

I installed my Insignia Bluetooth headset, and it works very well, although I notice a bandwidth limitation when using a bluetoth mouse at the same time. However, when testing the headset with all applications, I noticed the DVD playback was not working. I installed LIBDVDCSS2, and finally got an image running, however Totem cannot navigate through the DVD menus.

I found this bug - [https://bugs.launchpad.net/ubuntu/+source/gst-plugins-bad0.10/+bug/260765](https://bugs.launchpad.net/ubuntu/+source/gst-plugins-bad0.10/+bug/260765), can you confirm this is still a problem wth intrepid, or is DVD playback broken on my computer?

---

### Post by serval1 on 2009-04-18
Well, a series of tests proved that with libdvdcss2 installed, the DVD playback is fine and works everytime PROVIDED I do not load the bluetooth headset. The combination of Totem, Pluse Aduio and the Bluetooth headset will work for the first DVD, then all audio after Totem is shutdown, fails. Totem will not play another DVD until the computer is restarted.

If I do not attempt to operate the headset, Totem works each and everytime. There appears to be a compatibility problem with the bluetooth audio, Totem and Pulse Audio. It seems Totem does not release the stream when it is shutdown. Nothing can access the audio after that. I don't have enough experience to kill the right  modules, so a restart fixes the problem.

Has anyone else experienced a similar issue?

---

### Post by thomasaaron on 2009-04-20
> however Totem cannot navigate through the DVD menus.

Yes, totem is famous for that. Try downloading VLC. It is much better, IMHO.

---

