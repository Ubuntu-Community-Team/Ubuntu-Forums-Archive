---
title: "Trouble connecting to public WiFi"
date: 2009-07-09
forum: System76 Support
---

### Post by ebeyer on 2009-07-09
I'm hoping this has a simple solution.

I have a new Starling netbook running Ubuntu 9.04.  At home, I can connect to our wireless without too much trouble (though I do notice the range is lower than on my Macbook).  Public WiFi is hit or miss.  Mostly I can detect the public wifi network and there is good signal strength.  The wifi indicator on the top right of my screen spins for a minute or so and I receive the notification that I'm disconnected from the wireless network.

It bears mentioning that I'm having no trouble connecting to the same network at the same location with an iPhone and Macbook.

Your insight and advice is appreciated.

---

### Post by thomasaaron on 2009-07-09
How far away are you from the access points that fail? If you move closer, can you connect?

---

### Post by ebeyer on 2009-07-10
I'm in a hotel, so it's difficult to be sure.

The bar that registers signal strength shows it to be almost "full", suggesting signal strength is good.  As I said, connecting with my other laptop and my iPhone is no problem at all.

If this is a distance issue, I would submit that the WiFi unit on the Starling is pretty weak, compared to the MacBook and iPhone.  Is that the impression I should have?

---

### Post by 3Miro on 2009-07-10
I have used a number of public WiFi connections in the past and never ha trouble with my Pangolin. That is Hotels (several), Coffee Shops, Car Dealerships, Universities. There might be something off with the security protocols on the network.

---

### Post by jml on 2009-07-10
I have a Starling as well and I think that it is definitely a hardware issue.  I performed the driver update that Tom suggested in another thread without any improvement in performance.  At my home, I am able to connect easily to my wireless network with an EeePC running EeeBuntu ver. 3, a DARU1 and 3 running Jaunty, and a MacBook running OS X.5.  Of all these units, the Starling has the most trouble connecting to my network.  I have to be within 10 feet in order to connect.  As long as I stay close the connection is fine.  If I move away from the AP, the signal strength seems to remain fine, but I can't connect to anything.  The browser just churns away for a minute before displaying the error message that the site requested was not found.  My other computers can connect from much greater distances. My network uses WPA encryption.  Tom, any other ideas?  Is it possible to swap out the wireless card?  Is that a end user project? Or would the Starling have to be sent back to System 76.  I love the Starling in all other respects, it's solidly built, has a great screen, and has suprisingly good performance for an Atom processor.  Any other help would be appreciated.

Joe

---

### Post by thomasaaron on 2009-07-10
This is a driver issue. We're sure of that.

Under Intrepid, the card would not work at all. Initially under Jaunty it had about a 5-foot range. Installing backports increased it to between 40-60 feet here in our office.

The wireless card in this one is not user-accessible.

We're working on this one right now. It may be a better idea for us to open a bug report on it and point people to it, as there is no easy immediate fix for the range issue. But we are confident range will be improving, as support for this card is improving.

---

### Post by kingnerd on 2009-07-10
Just chiming in to say that I also have a very poor range, and I also can't connect or transfer any data when the signal strength is below 100%.  I hope this gets fixed before my trip in early August, as I'm going to need to rely on public/leeched WiFi to stay connected, and thus, every bit of range would help.  I might install Windows later to see if this is truly a driver issue or if it's inherent with the hardware.

---

### Post by jml on 2009-07-10
Thanks for the quick response, Tom.  I'll keep checking this forum for when a fix is posted.

Joe

---

### Post by jml on 2009-07-10
Tom, one last question.  Is the driver issue unique to Ubuntu, or is it a driver that cuts across other distros.  The reason I ask, is that I am OK trying other distros on the Starling if you think there might be one with better driver support for this wireless card.  I know that S76 only supports Ubuntu, but I would like your opinion.  Thanks.

Joe

---

### Post by thomasaaron on 2009-07-10
I'm pretty sure it is across distros. Ubuntu tends to be pretty cutting edge on this sort of thing.

---

### Post by jml on 2009-07-10
Thanks for the quick reply, Tom.  I appreciate it.

Joe

---

### Post by PatrickVogeli on 2009-07-10
Maybe some of you could try to set the link speed manually? I'm having very similar problem with a ralink card: it detects and connects fine, but you unable to do anything until you force the speed to 5, 11 o whatever. You could try that:

sudo iwconfig wlan0 rate 5.5M

wlan0 is how my wifi card gets picked up, your may be different, you'll see doing iwconfig and looking at the output.

Possible rate values are 1,2,5.5,11,18,24,36,48,54 I think. With 5.5 you should have decent speed and acceptable range.

It may not solve the problem, but it's easy to try and you'll see the results immediately. If it doesn't work, sudo iwconfig wlan0 rate auto will revert that setting.

---

### Post by jml on 2009-07-12
Thanks for the suggestion PatrickVogeli, I tried it but unfortunately, it does not improve my wireless performance.  Luckily I did not sell my ASUS EeePC 900HA yet.  I will plan to use that for traveling, and wait for the inevitable (hopefully soon,) driver update to improve things for the Starling.  I really do prefer the Starling to over the 900HA.

Joe

---

### Post by jml on 2009-07-12
I have to agree with you, Tom.  Since I have a USB optical drive, I tried EasyPeasy , EeeBuntu, PCLinux 2009.2, and pretty much all of the other Live distros I have in my collection.  Many do not even see the wireless card, and the ones that do, EasyPeasy, and EeeBuntu, do not successfully connect.  So we will have to wait for either System 76, or the Linux Community to solve the driver problem for us.  (Wish I could code.)  Anyway, I'm not posting this to complain, but to hopefully save others time.  By the way, Tom, precisely what chipset does the Starling's wireless card use

Joe

---

### Post by Ruthless on 2009-08-10
So, after a few weeks have passed, is there any news pertaining to the wireless?

---

### Post by thomasaaron on 2009-08-10
Ruthless, looked back through this thread and didn't see what kind of computer you have.

If it's a Starling, the problem is fixed.

Go to Administration > Update Manager, click the "Check" button and completely update your machine.

THEN, make sure you are running the 2.3.7 version of the System76 Driver (System > Administration > System76 Driver > About)

If you are, click the Install tab and the Install button.

When the driver is finished, reboot your computer.

---

### Post by Manolicious on 2009-09-05
Weird, on my Starling the wireless worked for 2 hours out of the box, then stopped.  But I did the system76 update with an ethernet cord and now the wireless is working just fine.  Why would the wireless card fail only after a few hours after turning it on for the first time?

---

### Post by thomasaaron on 2009-09-07
If you ran updates, and a kernel update was present, it couldn've broken your wireless. We're trying to get the wireless driver included upstream so that doesn't happen any more.

---

