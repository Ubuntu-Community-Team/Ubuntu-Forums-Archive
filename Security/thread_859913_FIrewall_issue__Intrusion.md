---
title: "FIrewall issue?  Intrusion?"
date: 2008-07-15
forum: Security
---

### Post by kulturloseramerikaner on 2008-07-15
Today I fired up my desktop (week old Hardy install) to check email after getting home from work.  I usually go into "administration" and start the Firestarter GUI to make sure there's nothing amiss.  Today, I had an issue I've never seen.  As soon as I opened Firestarter it registered a hit.  I opened up the "events" tab and I couldn't keep up with it - I was getting bombed.  A continuous stream of new hits at less than 1 sec. intervals, from various IP addresses.  What the heck?  I've run Ubuntu now for a year and a half (started on Dapper) and never saw anything like this, even while filesharing.
I pay bills online and whatnot and absolutely loathe the idea of someone being in my system.  Only a week-old install?  No biggie; I just repaved to be done with it; took less time than having to troubleshoot.  20 min later, new install; first package I install is Firestarter.  Fire it up and SAME THING.
What is going on?  I don't trust my system at the moment and am writing this from the lappy and PCLinuxOS.  I installed Firestarter on there too just to see if there was a network issue maybe; hasn't scored a hit yet.

---

### Post by Dr Small on 2008-07-15
It doesn't mean anyone is getting in, it just simply means that you are getting bombarded with attacks. Different ports, or all the same? It could be a portscan.

---

### Post by kulturloseramerikaner on 2008-07-15
They were all on port 40728.  Port 80 opened briefly after the reinstall to let updater do its thing.
If it was a port scan, wouldn't it be getting hit on different ports from the same IP address?

---

### Post by Dr Small on 2008-07-15
Yes. But as long as long as you don't have any services running, you really shouldn't worry. It's like sitting in front of your nice big bullet-proof picture window, watching the crook fire round after round at your window.

But if you leave your side-door unlocked, he can get in.

Port 80 did not open for updates. That is your system connecting *outbound* to another host that has port 80 opened, to receive updates. This is not opening the port on your system.

Dr Small

---

### Post by kulturloseramerikaner on 2008-07-15
The problem is though that if the crook keeps firing, eventually a hole does open up.
I did a "top" to see was going on as far as services; it looked to be mostly maintenance stuff, most of which I honestly don't recognize as good or bad.  There were as many six instances of "getty" running, which seemed a bit odd; is that actually normal?
Would running the top command even provide a warning if someone did get into my system?  
I would like this to stop, A) for my own piece of mind and B) so that I can tell in the future if there *is* something that I should take action on, it won't just disappear into the background of whatever Firestarter is warning me about.  If someone was doing a port scan, wouldn't the other systems behind my router also show this activity?

---

### Post by todb on 2008-07-15
Though you haven't provided much in the way of details, you mention that this is happening "at home" and you're not seeing this on other systems "behind your router."

These make me think that you have picked up an IP address that was recently being used as a torrent peer, and you have your router configured in such a way to allow all inbound connections to your Ubuntu machine's IP address (usually something like a "DMZ Host" option, I don't recall the particular syntax on Linksys or whatever router you're using).

So, the first order of business sounds like you need to get your Ubuntu machine out of DMZ-land; consult your router's (cable modem's) documentation on how to do that, or just google for "<your router's brand name> dmz."

You can look at your traffic with more fidelity with an application like Wireshark (sudo apt-get install wireshark). Hours of fun, that.

Pounding on ports, even from a variety of IP addresses, is a normal condition of an unfiltered Internet connection. It's nothing to worry about, but you're right -- it will mask actually interesting traffic.

If you're feeling slightly more adventurous, listen in on the traffic with netcat (sudo apt-get install netcat); open a port to whatever the askers want, and see if there's an initial client-side request to help you fingerprint the service.

hth.

---

### Post by kulturloseramerikaner on 2008-07-16
Well I just got into the router and confirmed that the dmz setting is disabled... I'll fire the desktop back up in a bit and see if I still have the issue going on.

---

### Post by kulturloseramerikaner on 2008-07-16
Dr. Small, todb, thank you for your suggestions and your time.  I haven't had the issue so far today and am going to go ahead and label this as solved.  What I think may have happened was that Gamespy tagged me as someone hosting a Civilization IV game; I play online sometimes with a buddy of mine, so even though that wasn't running I was getting hits from others in the network.  I can't think of what else it might have been anyway!

---

### Post by todb on 2008-07-18
Well, that is a fantastically interesting resolution, since I'm a Civ dork as well ([http://val-hell-yeah.blogspot.com](http://val-hell-yeah.blogspot.com)), and I've been meaning to get around to figuring out the wire protocols involved in multiplayer.

Thanks for the follow up! I'm guessing that your Ubunutu machine picked up an IP address that you had already set at your router for "okay for Civ" or whatever (I've never hosted a game so I don't know what's involved on that). That would be why it was seeing the traffic.

---

