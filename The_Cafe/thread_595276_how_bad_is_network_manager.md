---
title: "how bad is network manager?"
date: 2007-10-28
forum: The Cafe
---

### Post by garba on 2007-10-28
I usually don't like complaining about things that come for free as in free beer, but when it comes to NetworkManager I really can't help it. I've just given gutsy a spin on my old trusty home PC. This machine sits behind a d-link router and is equipped with two network cards. I don't have a dhcp server running on the router hence manual ip configuration is a must for me. So I go about booting up gutsy and the first thing I do is pretending I were a total noob who just wants to get its network configuration to work through a GUI. I spot an icon on the right top corner of the screen. I click on it and choose manual configuration. 

From there on, I couldn't understand if it was me who is totally retarded or what. I have a checkbox on the left whose purpose is beyond me. Then there's this icon which would suggest that my nic cable is unplugged. Actually, one is unplugged but the other one isn't. Perhaps that icon more likely just stands for "cabled connection". Anyway we have a huge piece of information missing here: I can't tell from the applet if the network cable is unplugged, and I am 100% sure the kernel properly reports the link status, at least with my NICS. I then go about setting up my static ip trying to guess which interface is actually the plugged one cause from text strings such as eth0 eth1 alone no one could tell (appending something like hardware type? nah confusing). I fill in all the fields, I click "close" (apply? cancel? nah that's deprecated...). I then click on the resolver tab and type in my provider's name server. For some reason, there was a bogus entry there, an empty one...

I then fire up firefox and nothing works.

So what next?

You guessed: ifconfing and found out that my network interface was left unconfigured. /etc/network/interfaces was properly set up though. I do the ifconfig thing and my link is up and working in no time, but the applet isn't properly notified. I toy around, try clicking on "disable networking", the applet icon turns into something with a warning but the connection is still up. I can't even save the network profile, I click on save and nothing happens, nothing gets added to the drop down list.

I don't know, perhaps it's just the gnome graphical frontend to networkmanager that has got problems but I am left wondering, this thing lacks even the most basic functionalities, it can't even configure a static ip address. Please somebody tell me, what's this thing supposed to do besides irritating me to no end? :lolflag:

---

### Post by n3tfury on 2007-10-28
it sucks. i don't bother with it. so i ise wicd

[http://wicd.sourceforge.net/screenshot.php](http://wicd.sourceforge.net/screenshot.php)

---

### Post by Polygon on 2007-10-28
works perfectly for me

auto detected my wifi network and all i had to do to set it up is click the icon, and it asked me for my wep password, after i entered that it connected.

and when i had a lan party a while ago, i plugged in a ethernet cable and it switched to that, and when i unplugged my ethernet cable it disconnected and tried to connect to my wifi network, which it did and i still had internet

so here comes the case of "it works for me"

---

### Post by Anessen on 2007-10-28
I find it a _complete_ nightmare getting NetworkManager to work properly and for Gnome's little applet to report status properly. All it seems to do is get in the way and try to reconfigure things wrong.

---

### Post by D-EJ915 on 2007-10-28
the ring thing is a pain in the *** so I just deleted network-manager, I configure my wireless through command line now.

---

### Post by 23meg on 2007-10-28
Depends on your hardware.

[http://live.gnome.org/NetworkManagerHardware](http://live.gnome.org/NetworkManagerHardware)

---

### Post by tbroderick on 2007-10-28
> **n3tfury said:**
> it sucks. i don't bother with it. so i ise wicd

[http://wicd.sourceforge.net/screenshot.php](http://wicd.sourceforge.net/screenshot.php)

Yep. wicd is much better. Even has a refresh button!!!

---

### Post by vexorian on 2007-10-28
Not that bad.

Like any software it got bugs. (Enphasis put on any, I am yet to see something 'perfect' on either the free software world or the propietary world)

---

### Post by Dimitriid on 2007-10-28
A known bug in gutsy is that you cannot shutdown properly and its tied to network manager. That made me decide I needed to uninstall it. Thing is, wicd its not being much better for me: first of all it outright refuses to start the little icon thing on start up ( the command is right but it won't ever open unless I try to manually open then two instances show up immediately )

Second, dropped connections. So ok so I blame it on my broadcom wireless card and the fact that the wireless AP is a few concrete walls away.

So I tried ethernet cable...wicd dropped connection too! That was pretty pathetic to be perfectly honest. The little icon thing also was always reporting the status wrong.

I don't know if its just gutsy that is plain bad for networking or both are fairly bad network managers. All I know is that Arch was just unstable as hell on my laptop and Gutsy seems stable, except no network manager works without giving me a violent headache.

Im waiting for Mint 4.0 but realistically speaking im looking into downgrading to Feisty or trying debian. Nothing seems to like my notebook though.

---

### Post by Polygon on 2007-10-28
i would highly suggest you either report these as bugs or post in existing bugs as a 'me to' to maybe let them know they are still there..as i said earlier.. nm-applet and network manager work perfectly for me....

---

### Post by Dimitriid on 2007-10-28
> **Polygon said:**
> i would highly suggest you either report these as bugs or post in existing bugs as a 'me to' to maybe let them know they are still there..as i said earlier.. nm-applet and network manager work perfectly for me....

I think I have but im not sure. Still doesn't solves my laptop issues and im about to give up and just put XP on it....

---

### Post by init1 on 2007-10-28
> **Polygon said:**
> works perfectly for me

auto detected my wifi network and all i had to do to set it up is click the icon, and it asked me for my wep password, after i entered that it connected.

and when i had a lan party a while ago, i plugged in a ethernet cable and it switched to that, and when i unplugged my ethernet cable it disconnected and tried to connect to my wifi network, which it did and i still had internet

so here comes the case of "it works for me"

> **Polygon said:**
> i would highly suggest you either report these as bugs or post in existing bugs as a 'me to' to maybe let them know they are still there..as i said earlier.. nm-applet and network manager work perfectly for me....
Yeah, but I assume that you are using the default DHCP and not static IP.

---

### Post by vexorian on 2007-10-28
I can't help but think this is actually my fault since I didn't beta test gutsy even though I can take a bunch of bugs and not die in despair, not to mention I got the time, but I posponded the gutsy download until it was too late.

I got an static IP thus it would have been easy to catch the bugs.

> I think I have but im not sure. Still doesn't solves my laptop issues and im about to give up and just put XP on it....
Try to learn how to deal with the command line, it isn't as hard as it looks initially. Also look for your wireless brand and specs and verify it is correctly supported. Mint may not change things heavily considering it is not too different from ubuntu in that kind of areas, unless you need a propietary driver to improve your compatibility that is.

From what it looks like gutsy network manager should have issues with static IP (definitely ) and not well supported wireless cards. Although initial gutsy feedback was stating it improved in the wireless part of it, so I am rather clueless.

If you are having issues with both managers this sounds like it is a hardware/driver issue. Using another network manager won't fix a driver issue.

---

### Post by 50words on 2007-10-28
I love it on my ThinkPad T43. Actually, I often boot in Ubuntu rather than Windows XP to get wireless access, since it picks up more networks, and more easily, than Windows does.

---

### Post by fuscia on 2007-10-28
works fine for me, but i haven't tried to mess with it much. i just boot up and pick the wireless connection i want and go.

---

### Post by 23meg on 2007-10-28
[QUOTE=garba]..... I click on it and choose manual configuration. [/QUOTE]

...and thus you abandon Network Manager, and work with GNOME's network-admin from there on. Network Manager is configured to evoke network-admin when you choose "Manual configuration" in Ubuntu. So perhaps your rant has nothing to do with Network Manager, other the fact that you couldn't even use it since it can't do static IP configuration (coming up in 0.7),  unless I'm missing something in the details.

---

### Post by Depressed Man on 2007-10-28
Doesn't seem to realize that my router's WPA password is stored in the keyring (keeps asking me for it). But I suppose this is better then in the tribe versions when I had to switch to WICD just to get it to work with my router.

Not sure if it's network manager's problem though..

---

### Post by macogw on 2007-10-29
On Feisty, it worked perfectly.  There's been a BIG regression :-/  If I'm wireless and plug in a wire, it doesn't recognize that.  Disabling networking doesn't disable wireless (wtf?) anymore, either.  Sometimes the vpnc plugin doesn't work right, too (it'll say it couldn't connect to the VPN, but if i do "sudo vpnc" it's fine).  It also doesn't realize the VPN passwords are in the GNOME keyring (just like Depressed Man's WPA password), which is yet another regression.

---

### Post by garba on 2007-10-29
> **23meg said:**
> ...and thus you abandon Network Manager, and work with GNOME's network-admin from there on. Network Manager is configured to evoke network-admin when you choose "Manual configuration" in Ubuntu. So perhaps your rant has nothing to do with Network Manager, other the fact that you couldn't even use it since it can't do static IP configuration (coming up in 0.7),  unless I'm missing something in the details.

hence I seem to understand we have two apps with overlapping functionalities (sorry i never use those tools), wonderful, and i guess that all network-admin does is parsing the /etc/network/interfaces file and amend it... no event based notification, no active monitoring, nothing... now please tell me, is this is the proper way to deal with networking on a desktop system? I don't think so

---

### Post by 23meg on 2007-10-29
[QUOTE=garba]hence I seem to understand we have two apps with overlapping functionalities [/QUOTE]

One of the apps does static IP configuration, whereas the other can't, which is where they don't overlap, and which is the main reason we have both. The "Manual configuration" + Roaming mode" UI twist makes them live together pretty well.

[QUOTE=garba]now please tell me, is this is the proper way to deal with networking on a desktop system? I don't think so[/QUOTE]

In a perfect world, no. In a non-perfect world where what we can and can't do depends on upstream features, it's a pretty good compromise. With the upcoming NM 0.7, we'll probably not need it any longer.

---

