---
title: "Starling wifi wont turn on"
date: 2009-10-23
forum: System76 Support
---

### Post by xtopher85 on 2009-10-23
Last night the issue started. Booted up the netbook after having shut it down when i got off work. Maybe 5 hours later is when i got back on it. The wifi indicator light never light. Tried the switch below it, no change. Tried Fn + F2, no change. Prior to this issue, when i boot from at least an hour long hibernate, the wifi would not turn on. So i would shutdown, pull the battery, boot back up and it would work. Tried that last night and it didnt help. Anything else i should try? Not finding any options in the GUI i may have missed. Nor do i recall if there is a shell command i can try. Thanks for any help!

---

### Post by thomasaaron on 2009-10-23
Establish a wired Internet connection. Then go to Administration > Update Manager. Click the "Check" button, and then install any updates. Then reboot your computer.

Now go to Administration > System76 Driver. Click the "Install" tab and the "Install" button. When the driver finishes, reboot your computer.

Your wireless LED now should be on, and you should be able to see wireless access points. If you cannot, there is a spring-loaded toggle switch on the right-hand side of the leading edge of your Starling. Toggle it *ONCE* to the right, and then release it. Now, reboot your computer.

Did that fix it?

---

### Post by xtopher85 on 2009-10-23
Tom you are brilliant sir! Did what you did word for word and its working now. Is it a good assumption that i should run updates wired in, as opposed to on wifi? That may be what caused the issue is my guess. 

Thanks again for the quick answer!

---

### Post by allersj on 2009-10-23
The same thing happened to me a couple nights ago.  My wireless stopped working right after applying a bunch of System Updates and rebooting.  I think the Linux kernel itself may have been updated.  Not sure if that could be the cause.

Followed Thomas's instructions and the wireless is back up!

---

### Post by vttay03 on 2009-10-23
same exact thing here....updated and afterwards there was no wireless connectivity so I reinstalled the System76 driver.  after a reboot everything was back to normal :)

---

### Post by Rayve on 2009-10-23
Just got my starling yesterday, also having this problem.  I cannot establish a wired connection either, though, so I can't try the fix as of yet.  I have a modem and a wireless router, not getting a wireless connection, and when I plug the ethernet from the modem into my Starling I don't get any sort of wired connection either.  :(

EDIT: Okay, took the cable from router instead of modem and this time I got wired connection in the Starling.  So, I updated packages, installed System 76 drivers, and then rebooted.  I can search for Wireless connections now, but for some reason, I can't connect wirelessly still.  I tried the WiFi button on the front too - no light, no change.

... nevermind!  Another reboot and it says connection established.  Little red light over the 3G/WiFi button.  Yay.  Just in time for me to go to work, lol.

---

### Post by jbraswell on 2009-10-24
Thanks for this.

---

### Post by rubbsdecvik on 2009-10-24
Oh thank you. I didn't even think about it when I did a Kernel update.

---

### Post by suzgould on 2009-10-25
> **Rayve said:**
> Just got my starling yesterday, also having this problem.  I cannot establish a wired connection either, though, so I can't try the fix as of yet.  I have a modem and a wireless router, not getting a wireless connection, and when I plug the ethernet from the modem into my Starling I don't get any sort of wired connection either.  :(

EDIT: Okay, took the cable from router instead of modem and this time I got wired connection in the Starling.  So, I updated packages, installed System 76 drivers, and then rebooted.  I can search for Wireless connections now, but for some reason, I can't connect wirelessly still.  I tried the WiFi button on the front too - no light, no change.

... nevermind!  Another reboot and it says connection established.  Little red light over the 3G/WiFi button.  Yay.  Just in time for me to go to work, lol.


I had the same problem, but my Starling won't connect even when I connect the cable from the router.  Is there some other change I need to make to enable the wired connection?

---

### Post by bikesandbrews on 2009-10-25
I'm having the same problem- just got the computer, which worked flawlessly until the first time I powered it down.  Now the wireless light won't come on. I followed all of Tom's directions and still nothing.  I even restored factory settings and got nothing.  Any other suggestions?  Thanks!

---

### Post by bikesandbrews on 2009-10-25
Scratch that, after a series of restarts it suddenly and inexplicably turned on!  Not looking a gift horse in the mouth however....

---

### Post by Rayve on 2009-10-26
> **suzgould said:**
> I had the same problem, but my Starling won't connect even when I connect the cable from the router.  Is there some other change I need to make to enable the wired connection?

Suzgould,

For me, the wired connection was (and has been) automatic as soon as I plug the ethernet (on my router, it's the yellow cable) from my router into my Starling.  Have you updated packages and System76 drivers (in that order) recently?

---

### Post by thomasaaron on 2009-10-27
Here's a good little tutorial that should always be the first step if something happens with wireless on the *Starling*...

> Establish a wired Internet connection. Then go to Administration > Update Manager. Click the "Check" button, and then install any updates. Then reboot your computer.

Now go to Administration > System76 Driver. Click the "Install" tab and the "Install" button. When the driver finishes, reboot your computer.

Your wireless LED now should be on, and you should be able to see wireless access points. If you cannot, there is a spring-loaded toggle switch on the right-hand side of the leading edge of your Starling. Toggle it *ONCE* to the right, and then release it. Now, reboot your computer.

---

### Post by jml on 2009-10-27
Tom, your "mini tutorial" should be made a sticky post at the top of the postings list.  It's that useful.

Joe

---

### Post by dwright15 on 2009-10-28
I just wanted to share my experience.

My system is the Starling Netbook remix running 9.04 (Jaunty Jackalope) 

which was working fine until running update manager the other night.
wireless stopped working. (wireless was not even an option in network manager afterwards)

restoring factory settings, reboot did not work. (tried several times)

after perusing the system logs, I found that the previously working wireless driver was
rtl8187 but after the update it looks like these were getting loaded instead
r8187
#not positive if these were loaded previously
ieee80211_rtl
ieee80211_crypt_tkip_rtl
ieee80211_crypt_wep_rtl
ieee80211_crypt_ccmp_rtl
ieee80211_crypt_rtl


How I got wireless working again. (I use WPA/WPA2 Personal)


$ sudo vi /etc/modprobe.d/blacklist.conf
# added this
blacklist r8187
blacklist ieee80211_rtl
blacklist ieee80211_crypt_tkip_rtl
blacklist ieee80211_crypt_wep_rtl
blacklist ieee80211_crypt_ccmp_rtl
blacklist ieee80211_crypt_rtl

$ sudo vi /etc/modules 
# added this
rtl8187
wlan

reboot


HTH someone

---

### Post by thomasaaron on 2009-10-28
dwright,

I wonder if you are using the correct version of the System76 driver. 2.3.7 already does what you mentioned.

---

### Post by Aggzza on 2009-10-30
i love how ubuntu did that, instead of installing programs or booting other stuff, you can just update your computer by going to that.

---

