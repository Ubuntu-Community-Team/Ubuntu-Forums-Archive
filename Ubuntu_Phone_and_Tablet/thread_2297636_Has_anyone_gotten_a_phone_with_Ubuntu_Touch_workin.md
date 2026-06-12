---
title: "Has anyone gotten a phone with Ubuntu Touch working on AT&amp;T 3G or 4G LTE?"
date: 2015-10-05
forum: Ubuntu Phone and Tablet
---

### Post by callmebruce on 2015-10-05
I use AT&T cell phone service. I have an ancient Samsung Galaxy S3. I currently have 5 lines under my account, with kids and wife running a variety of Android, IOS and Windows. I'd like to shake up the mix a bit and try out Ubuntu Touch. I realize the Meizu MX4 is sold out, and was not available in the US. I also realize the Aquaris (I think that's it) only works on 2G stuff.

So - has anyone had success getting a phone running Ubuntu Touch to accept an AT&T sim and run on 3G UMTS network - 850/1900MHz bands or 4G LTE network - AWS/700/850/1900MHz bands? Also, any luck with a mapping application that uses location services and takes traffic into account (okay, a Google maps-like app), a Yelp app, general e-mail client, facebook client, and OpenVPN client?

I've flashed a tablet before and didn't brick it - but flashed a generic Android image, not Ubuntu image. Picking up a working item might be a better choice for me. Does the Google Nexus work on AT&T 3G/4G networks? And is it fairly simple to flash?

(I should have researched further. Looks like Nexus 4 might be interesting, but does not support LTE. It does support HSPA, though. I think I should wait a few months to see if anything gets announced for US market availability and LTE support. Although, ...)

---

### Post by callmebruce on 2015-10-19
I purchased a used Nexus 5. Flashed Ubuntu Touch for Nexus 5 (hammerhead) using the devel channel. Am able to send and receive calls and text messages. Initially had trouble getting cellular data working, but seems to be fine now. I had a Samsung S3 that I dropped and cracked the screen on. So I swapped the sim from my Samsung to the Nexus 5. No issues whatsoever getting the Nexus 5 working on AT&T with my Samsung SIM. After making sure it worked, I flashed Ubuntu Touch. It seems to work fine (other than no Bluetooth, but the Nexus 5 Ubuntu Touch notes pointed that out anyway).

Anyway, I can make and receive calls. I can do SMS text messaging. I can surf the Internet over wifi at home and over my carrier when out.

---

### Post by vq1 on 2015-10-19
As I understand it LTE is not yet supported on Ubuntu Touch. 

I flashed Ubuntu Touch on my Nexus 4 very easily (it is a supported device). With my sim card I can make calls/texts etc. I do not use it as my daily phone so I couldnt tell you good the service is.

---

### Post by callmebruce on 2015-10-20
I think networking might be a little buggy, at least on the Nexus 5 (but that isn't a supported model anyway). My phone connects to my WAP just fine and can work all day, but when I go outside and have to use my cell data connection, I get network error messages in my web browser. Can't connect to anything. If I reboot the phone, it works just fine over the cell connection (I tried it hanging out in a parking lot and again on the side of the road trying to get Google Maps up. Google maps didn't work when I tried to get driving directions). When I get back home, it connects to my WAP again, but I can't get anywhere at all over wifi. If I reboot at home, it works just fine.

If I go to settings and turn cell data on or off, or turn wifi on or off - it doesn't clear up my connection problems. Doing a hard boot clears the problems up. Do you have that problem with your Nexus 4?
Also - anyone on the forum know a command line way to reset networking or a command line way to do a reboot? If I install a terminal application, can I do a sudo reboot?

edited: I installed terminal and can do a "sudo reboot". Password is just my passcode for unlocking the screen. Easy enough!

---

