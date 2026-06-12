---
title: "panp7 wireless dies randomly"
date: 2011-02-07
forum: System76 Support
---

### Post by turbofail on 2011-02-07
I just bought a new Pangolin Performance (panp7).  It came with Ubuntu 10.10 pre-installed, and I haven't messed with it except for installing the recommended upgrades.

The wireless driver appears to be extremely flaky.  During heavy usage (i.e. bittorrent), it will cease to work in a matter of seconds.  During lighter usage, it will work for a longer amount of time, but will still eventually die (by die, I mean I am unable to, say, ping my router, though NetworkManager still thinks that it's connected).

Once it has died, the only way to bring it back is by running rmmod/modprobe on the wireless driver.  The wireless router I'm using is a WRT54G running Tomato firmware v1.23.1607 (I tried running it in B-only and B/G mixed mode), with no encryption.  I haven't tried it on another wireless router yet, I will attempt to do so tomorrow.

There seem to be several threads on the Ubuntu forums regarding a problem very similar to mine, such as [http://wiki.ubuntuforums.org/showthread.php?t=1267961&page=11](http://wiki.ubuntuforums.org/showthread.php?t=1267961&page=11) and [http://ubuntuforums.org/showthread.php?t=1597881&highlight=realtek+8192se](http://ubuntuforums.org/showthread.php?t=1597881&highlight=realtek+8192se) - but none of these threads appear to have found a decent fix.  (also of note is that the output of dmesg ends up being very similar to that shown in [http://wiki.ubuntuforums.org/showpost.php?p=10170907&postcount=105](http://wiki.ubuntuforums.org/showpost.php?p=10170907&postcount=105)).

I suspect that the only real solution to this will come from RealTek, but I thought I might bring it up here first in case anybody at System76 knows something more.

-Jason

---

### Post by scarey9 on 2011-02-07
Which wireless adapter do you have installed on your computer(i.e. did you opt for the Intel Centrino adapter upgrade)?

---

### Post by isantop on 2011-02-07
We're not seeing this across the board, so I think it may be a one-off issue. The first to try would be to unplug your router, wait a few moments, plug it back in, then wait for it to finish booting up. Then try reconnecting. Did that get it?

---

### Post by turbofail on 2011-02-07
> Which wireless adapter do you have installed on your computer(i.e. did you opt for the Intel Centrino adapter upgrade)? 	

It's using the Realtek r819x driver.  lspci says it's a Realtek 8191SE.

> The first to try would be to unplug your router, wait a few moments,  plug it back in, then wait for it to finish booting up. Then try  reconnecting. Did that get it?

That was one of the first things I tried.  It didn't help.

---

### Post by turbofail on 2011-02-07
Some further updates: I tried a little bit of torrenting with a different wireless router and didn't observe the immediate death problem.  I then returned home and tried it with my usual wireless router and was again immediately confronted with the problem.  I also tried enabling and disabling the ESSID broadcast.  Neither option made any difference.  I'm about to try it with encryption enabled.  I'm not sure why that would work better, but I suppose it's worth a try.

---

### Post by smarmytime on 2011-02-08
I've been having almost the exact same problem, thought its intermittent. I have the same Realtek, and my laptop is also a brand new System76 panp7 - I got mine less than a month ago. Right now I'm really wondering if I made a mistake not getting the upgraded nic card. Right now, in fact, it stopped working, and I'm actually tethering it to my phone so that I can post this. Very frustrating, to say the least.

---

### Post by isantop on 2011-02-08
It may be an incompatibility between the router/firmware and the card. Try upgrading the firmware in the router, as that could clear thing up.

---

### Post by lextori on 2011-02-09
I am experiencing a similar issue with my panp7 purchased in early jan.

I'm not sure if it's related to particular routers though as I am seeing it at several locations.

---

### Post by isantop on 2011-02-09
I think you're having a different issue, since you're having it on different routers. Does it help to try it form a LiveCD?

---

### Post by turbofail on 2011-02-09
I tried updating the firmware on my router, still no luck.  Also, I found this bug report on launchpad ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/687692](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/687692)) that looks to be the same thing (same messages in dmesg output: "No more TX desc").  Nothing seems to have been done about it, though.

---

### Post by pafufta503 on 2011-02-09
torrenting can wreak havoc on some routers.  check for any updates from the router manufacturer.  i used to have to restart my router constantly if i torrented.

---

### Post by turbofail on 2011-02-10
Well my other devices continue to work fine on the same router when I observe this problem.  Resetting the router also doesn't bring anything back.  Moreover, when torrenting with my previous laptop (which has some sort of intel wireless card), I have never observed any such problem.

I'm in the process of sending some information to Realtek.  If they tell me anything useful I will post it here.

---

### Post by samalex on 2011-02-11
Thought it may be unrelated about 5 years ago I ran a firmware update on my Linksys wireless router which caused both my Linux laptop (not a S76 at the time) and iBook to do what you're experiencing.  The network would just drop off at random times.  I found that the problem was a bug in the firmware update and Linksys eventually rolled out a patch which fixed the problem.

So the first question I have is whether or not your router is new or if you've done a firmware update lately.  Also does your laptop show the network card loosing connection or anything weird in the logs?

Just some thoughts --

---

### Post by bonius on 2011-02-11
> **isantop said:**
> We're not seeing this across the board, so I think it may be a one-off issue. The first to try would be to unplug your router, wait a few moments, plug it back in, then wait for it to finish booting up. Then try reconnecting. Did that get it?

I got my pangolin 3 days ago, and I'm having the exact same issue.  I have an older Linksys WRT54G.

It's not just running torrents that makes this happen.  It will eventually happen with just casual surfing.

My WRT54G is ancient, and I suppose that could be the problem, although I have other laptops in the house that continue to work while my Pangolin drops.

---

### Post by isantop on 2011-02-11
Does your Pangolin drop connections from other routers as well? If so, then I think the issue is different. If not, then I think it actually is the router. You can try upgrading the firmware in the router to see if that has any effect.

---

### Post by bonius on 2011-02-11
> **isantop said:**
> Does your Pangolin drop connections from other routers as well? If so, then I think the issue is different. If not, then I think it actually is the router. You can try upgrading the firmware in the router to see if that has any effect.

No, not as far as I know.  The only other place I've tried it is at work with Cisco's fancy enterprise-y wifi stuff.

My router is like 12 years old and has the last bios linksys ever made for it.  I may run out an buy a new, fancy bgn router to see what happens.  I'll let you know if that fixes it.

---

### Post by smarmytime on 2011-02-11
> **isantop said:**
> Does your Pangolin drop connections from other routers as well? If so, then I think the issue is different. If not, then I think it actually is the router. You can try upgrading the firmware in the router to see if that has any effect.

I've not updated the firmware in my router yet, but it has happened outside the house for me. Unfortunately, it's not something I can reliably duplicate...it's very intermittent.

---

### Post by bonius on 2011-02-13
> **bonius said:**
> 
My router is like 12 years old and has the last bios linksys ever made for it.  I may run out an buy a new, fancy bgn router to see what happens.  I'll let you know if that fixes it.

Alright, I went out and bought a shiny new router, and put the latest firmware on it.  The problem has gotten better, but has not gone away entirely.  I can surf for about an hour before it drops.  Then I have to click the network manager icon, disconnect, reconnect, and everything works again for an hour.


I need to do more testing, but it seems like the "drop" may DNS related.  Even when I'm dropped, I can still manage my router by the ip address. I can ping my router, and the ip of the cable modem on the other side, but nothing else.  I would think it was an ISP problem, except that all the other wireless devices in the house continue to work while this is going on.

---

### Post by isantop on 2011-02-14
There's only a couple of things left to check. Make sure that the DHCP lease time in the router configuration is a decent amount of time (24 hours or longer). Some routers may set this to something like 3 hours by default, which doesn't sit well with Ubuntu.

---

### Post by bonius on 2011-02-14
> **isantop said:**
> There's only a couple of things left to check. Make sure that the DHCP lease time in the router configuration is a decent amount of time (24 hours or longer). Some routers may set this to something like 3 hours by default, which doesn't sit well with Ubuntu.

I set it for 48 hours (default was 24), but the problem is the same.  It's not just DNS, It's like I loose all connectivity beyond the router.  

I gotta think this is a driver problem.  The router/cable modem/ISP is working fine for every other device on the network, and I have zero problems if I patch the laptop directly into the router with an ethernet cable.

Is there a log somewhere I can look for error messages on the wireless interface?

---

### Post by isantop on 2011-02-15
Thanks for looking into that. That should definitely be long enough. The last thing left to try would be to go to System > Preferences > Network Connections. Under the Wireless tab, go ahead and clear out all of the connections listed. Now, close that window and try reconnecting through the Network Manager Icon. See if it still drops.

---

### Post by bonius on 2011-02-15
> **isantop said:**
> Thanks for looking into that. That should definitely be long enough. The last thing left to try would be to go to System > Preferences > Network Connections. Under the Wireless tab, go ahead and clear out all of the connections listed. Now, close that window and try reconnecting through the Network Manager Icon. See if it still drops.


Well, I went one better.  I completely reformatted the HD, and setup a dual boot with Windows 7 and Natty Alpha2.

The problem does not happen at all under windows, so that rules out laptop hardware, the router, cable modem, et al.

The problem *does* happen even off the Natty live DVD, and with Natty installed.  I even tried rmmod r8192se_pci / modprobe r8192se_pci hwwep=0

I saw a few threads where people were having problems with hardware wep encryption, but that didn't do anything, either.


Update:
I took the pango to work today, and the wireless works fine here.  I'm officially out of ideas.

---

### Post by isantop on 2011-02-16
In that case, it's probably an issue with the firmware in the router. It may not be compatible with the wireless card, which, although rare, can happen. Can you confirm that by taking it to a library or coffee shop and trying it there?

---

### Post by bonius on 2011-02-17
> **isantop said:**
>  Can you confirm that by taking it to a library or coffee shop and trying it there?

Ok, I took it to the coffee shop, and everything works there.  I have tried two different routers at home; a WRT54G and a Linksys E2000.

Neither work under Linux, both worked under windows on the same panp7.

The APs at work are Cisco Aironet 1240 AGs, if that helps.  No idea what the coffee shop is using.

Is there a list anywhere of all the options you can pass to the r8192se_pci module?  I could try fooling around with various options or something like that?  r8192se_pci is the correct driver, yes?  lspci shows the card as a 

Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)


I've also tried changing the channel on my router to various channels in case one of my neighbors is conflicting with me.  None of them seemed to work any better.

---

### Post by pafufta503 on 2011-02-19
i can confirm this.  there are a few wireless networks that i've had no problem staying connected, but my sister's wireless router disconnects every so many minutes, depending on how much data is being transferred.  the only solution i found was to restart my computer, as i had tried working with the wireless GUI to no avail.  even after restarting it would still, without fail, disconnect again.

my guess is that it is something to do with incompatibility with the linux wireless drivers and the router.  my sister and her husband both use dell laptops with win XP on them and they have do not have the problems i have.

i could ask her what brand/product her router is if anyone is interested.  perhaps a list of incompatible routers might be a useful resource for sys76 users?

---

### Post by Tank Jr on 2011-02-21
I too am having problems with the wireless getting dropped. I however find that connecting to the WPA2 network is more troublesome at the office. The other connection at the office, the one that does not require any userid or password can stay connected for hours at a time without dropping once.
I will try to connect to the WPA2 from a different location on campus--I believe that might give a clue as to if the issue is the router, or the network per se.

---

### Post by cs35 on 2011-03-08
I too face the same problem on my System76 Lemur that I bought a couple of months ago. Router is Linksys E1000. When wireless dies (at random) I can still ping the router. Commands such as rfkill, ifconfig, iwconfig do not indicate any problem. Wifi applet on the panel indicates no problem.

Clicking on wifi applet and clicking on the "connected" ssid will result in a reconnect (disconnect and connect). This get the wifi working again.

Please let me know if I can provide any more information that could help fix this.

---

### Post by scarey9 on 2011-03-09
i have had no issues Using any of the following routers. Linksys E4200, Apple Time Capsule a newer belkin and an two year old Netgear.  The screen shot is from my linksys E4200.

---

### Post by cs35 on 2011-03-09
> **scarey9 said:**
> The screen shot is from my linksys E4200.

How did you get that window/dialog to show? I would like to check that when my connections dies.

---

### Post by scarey9 on 2011-03-09
> **cs35 said:**
> How did you get that window/dialog to show? I would like to check that when my connections dies.

Right click on the Network indicator on the panel and go to connection information.

---

### Post by bonius on 2011-03-09
Just an update, this problem seems to have resolved itself for me, at least.  I wish I knew for sure what fixed it, but it seems to have been something in the router configuration.  I was poking around in there, just trying random things, and now it works.  I set the channel selection to 'auto', set the frequency to 2.4GHz, set the network mode to 'BG mixed'.  So, maybe try stuff like that if you're having the problem?

---

### Post by scarey9 on 2011-03-09
It was more than likely the change to 2.4GHz that did it. I am having issues with 5GHz. Not so much with disconnecting but with the reception being less. This is to be expected with a higher frequency when range is a factor....but it should not be an issue when you are ten feet away.

---

### Post by Tank Jr on 2011-04-13
So is there a solution in sight? The wireless is right now very unreliable when connecting to secured networks.

---

### Post by isantop on 2011-04-13
Make sure the router frequency is set to 2.4 GHz. That should help out a lot.

---

### Post by Tank Jr on 2011-04-13
Actually that is not an option at least not at the university.
Is this the hardware, or is this Ubuntu?
If the hardware, it may be possible to use a different wireless card (USB ?), I think.

---

### Post by isantop on 2011-04-13
It's actually the router configuration at this point. 5 GHz connections are not ideal for longer distance connections.

---

### Post by Tank Jr on 2011-06-10
I confirmed from the University that the area where I'm having problems is covered by a 80211b network. I looked it up and found that it corresponds to 2.4 GHz. So definitely my problem is not due to the 5/2.4GHz thing.

---

### Post by isantop on 2011-06-10
It is sounding like hardware at this point. Running from a USB wireless card would go a long way towards helping confirm that, as would running your system from a LiveCD.

---

### Post by Tank Jr on 2011-06-13
It seems other people have also had issues with this card, and drivers.
[http://ubuntuforums.org/showthread.php?t=1597881]("http://ubuntuforums.org/showthread.php?t=1597881")
Has anyone seen this issue with an Intel WiFi card?

---

### Post by scarey9 on 2011-06-14
Yes. I am having pretty much the same problem with my Intel card. I am on a commercial grade network but i need to have a really good signal or my TX dies. As long as my signal is about 50% i am good.

---

### Post by Tank Jr on 2011-07-01
OK, so I note that I can ping the router, but no Intenet access. What would that mean?

---

### Post by scarey9 on 2011-07-01
I will tell you what it means. It means that the Wireless drivers for Linux are *****. I am getting really tired of having to reconnect my network every five or ten mins because it just decided it was going to stop. Not that it is kind enough to tell me. Nope as far as all the connection information is concerned everything is fine.

---

### Post by Tank Jr on 2011-07-03
I have a computer ( a netbook) with a Broadcom 4322 wireless. I no longer have Ubuntu on it, but if I recall, it used to be better in terms of wireless at the same spot under Ubuntu 10.10. Right now it has Mandriva, and I did not see too many problems either.
They are both 32 bit versions, mind you.
That's why I think the wireless card (RealTek )may have an issue with Ubuntu/Linux.
I just want to confirm that it is indeed the wireless card; if so, I will just swap it out with a compatible card.

---

### Post by Tank Jr on 2011-07-06
Anyone from system76??
I really need to have wireless working properly.
Any clues?

---

