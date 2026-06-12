---
title: "Air Crack question."
date: 2010-07-22
forum: Security
---

### Post by LILEDDIE on 2010-07-22
I've been studying air crack so that i can learn ways to improve my home wireless network and using air crack on ubuntu isn't as easy as i thought it would be. Can i get some help or suggestions?

---

### Post by Agent ME on 2010-07-22
Using aircrack is the easy part; I'm assuming you're also trying to figure out airodump.

Right-click your network manager applet (the little wireless icon at the top-right) and uncheck "Enable wireless" (recheck it when you're done with airodump). Now in a terminal, run "sudo airodump-ng -w dump wlan0". It will show a number of networks and what encryption they each use.

Choose the network you want to listen in on (should be one using WEP) and note its channel number (under the CH heading). Press ctrl-c, and then run "sudo airodump -w dump -c 6 wlan0" where 6 is replaced with whatever the channel number was. (When you don't pick a specific channel, all of the channels are cycled through, but many packets are missed.)

Now if there is any traffic on the network happening, you should see the number in the DATA column increasing. This tells you how many data packets have been captured. There isn't a specific number of data packets you'll need to get, but in my experience at least 20,000 will be needed for a 64-bit WEP network, and at least 100,000 for 128-bit WEP. So this will take many hours to run.

Open a new terminal while airodump is running, and run "aircrack-ng *.cap". Pick the network you want, and it will try to crack it. If it fails, leave it and it will automatically try again once you've captured a certain amount more data packets.

There are methods that work faster by forcing the network to generate data packets faster, but you'll need a wireless driver that supports injection.

---

### Post by Bachstelze on 2010-07-22
> **LILEDDIE said:**
> I've been studying air crack so that i can learn ways to improve my home wireless network

No need aircrack.  Don't use WEP, and use WPA2-CCMP if possible.  Done.

---

### Post by Agent ME on 2010-07-22
Some devices don't support using WPA and there may be a need for WEP. It's interesting to figure out how easy it is to crack one; after I did mine I set my router to have two wireless networks; one with WPA, and one with WEP that only my xbox uses. Doesn't stop others from getting onto my internet perfectly, but it does protect all of my web traffic which goes over WPA.

---

### Post by Austin25 on 2010-07-23
Air Crack I don't know much about, but for securing your network, it depends on how much security you need. To keep relatively unexperienced neighbors of your wifi, use WPA. If you need to keep someone from sniffing your packets, use WPA and VPN tunneling. They'll still sniff your packets, but It'll be hard to find what they mean if you use a good key.

---

### Post by LILEDDIE on 2010-08-02
Ok, here's a new question that goes along with the first... I'm trying to understand all of this by playing with it in Vmware and i'm wondering if Vmware is keeping me from doing everything that's capable of performing everything it is capable of. The reason i ask this is my brother has a Compaq laptop that's dual booted, one side windows one side ubutu 10.4 and on his ubuntu side he use every aspect of air crack.

---

### Post by cariboo on 2010-08-02
I would suggest you use the BT4 Live CD instead of VMWare. It is available [here]("http://www.backtrack-linux.org/"). Remember you need at least 2 wireless device besides the one you are using to monitor the signal.

You can search the forums for howto's on using aircrack-ng.

---

### Post by MasterGamerJK on 2010-08-02
> **Agent ME said:**
> Some devices don't support using WPA and there may be a need for WEP. It's interesting to figure out how easy it is to crack one; after I did mine I set my router to have two wireless networks; one with WPA, and one with WEP that only my xbox uses. Doesn't stop others from getting onto my internet perfectly, but it does protect all of my web traffic which goes over WPA.


its actually extremity hard to crack a PROPERLY configured 128-bit WEP key with a 64 char no pass phrase key topped off with MAC address filtering. That way you can ensure compatibility to devices like a Nintendo DS/Wii and a 360

Problems with haveing dual encryption:
1-radio interference (poor single quality)
2- your network is only as secure as its lowest point, ppl can still Man in the Middle your wpa traffic via tapping into your wep connection
3-WEP takes about 5-40 min to crack if not setup properly/ WPA takes about 40-a few days (thats not RLY that  long) / WPA2 could be a bit longer  (all of these times are dependent on the level of skill of the user/script and the legnth/complexity of the users key/passphrase)
NOTE: the best way to gain access to someones network is to use a wifi pineapple (google it) and steal the wifi config files from their machines directly or Man in the Middle their auth on connect

---

### Post by MasterGamerJK on 2010-08-02
> **cariboo907 said:**
> I would suggest you use the BT4 Live CD instead of VMWare. It is available [here]("http://www.backtrack-linux.org/"). Remember you need at least 2 wireless device besides the one you are using to monitor the signal.

You can search the forums for howto's on using aircrack-ng.


its a good idea to play around with it in BT4 first, at least untill you gte the hang of it, or do what i did and write some scripts for aircrack suite  and learn that way:popcorn:

---

### Post by Agent ME on 2010-08-02
> **MasterGamerJK said:**
> its actually extremity hard to crack a PROPERLY configured 128-bit WEP key with a 64 char no pass phrase key topped off with MAC address filtering. That way you can ensure compatibility to devices like a Nintendo DS/Wii and a 360
How do you mean properly configured? And once the encryption is broken, MAC address filtering doesn't help much if someone else decides to spoof the MAC of an allowed device.

---

### Post by MasterGamerJK on 2010-08-03
> **Agent ME said:**
> How do you mean properly configured? And once the encryption is broken, MAC address filtering doesn't help much if someone else decides to spoof the MAC of an allowed device.
  by properly configured i mean with setting such as "only allowing X number of IP address to be given out by your dhcp server,  X being the number of devices you have" and "assigning each specific IP address to a corresponding MAC address" and "by limiting the times each IP can access the web (ie: if your not going to be playing xbox at 4 AM dont allow it to be connected at 4 AM)" and "by MAC filtering both wifi and hardware address so that a hardware MAC cant be spoofed to a Wifi one" and "by useing open wrt or a small liht weight script/built in firewall tool to: monitor all net traffic and actively monitor whos connected to your network" to name a few. I use all of these dayly so feel free to msg me with any questions I will do my best tp help!

---

### Post by Agent ME on 2010-08-03
None of those things make a difference with cracking the WEP and preventing eavesdropping. Setting the DHCP server to not always give out addresses is not even a hindrance if the attacker sets a static IP.

MAC filtering again is not an issue if they spoof a valid MAC (An attacker can just listen on the network for a while to find a valid MAC). Preventing wired MACs from being used on the wireless is only security if there are no wireless MACs available to spoof.
> **MasterGamerJK said:**
> "by limiting the times each IP can access the web (ie: if your not going to be playing xbox at 4 AM dont allow it to be connected at 4 AM)" and **...** "by useing open wrt or a small liht weight script/built in firewall tool to: monitor all net traffic and actively monitor whos connected to your network" to name a few.
These are the only ideas in the post worth doing in my opinion, and I'm curious if you have any good scripts to recommend such as for OpenWRT or whichever gateway you use.

(Also, why are you quoting every point in that post?)

---

### Post by plunder on 2010-08-05
i wrote a script to run aircrack for me, you will still be required to know what you're doing though, you just don't have to remember commands

it's too big to attach here and i took it off my old site, if you want it message me on here i guess

---

