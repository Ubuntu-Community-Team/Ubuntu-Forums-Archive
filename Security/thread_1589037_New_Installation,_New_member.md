---
title: "New Installation, New member"
date: 2010-10-05
forum: Security
---

### Post by rCiv on 2010-10-05
Hi Guys!

Excited to be here, just switched over from windows to a fresh install of the latest Ubuntu download.
First and foremost, I would like to thank the entire Ubuntu community for producing such a high quality Linux distribution, it is a breeze to install, package/software management is easy and intuitive, and it runs like a deer, great job!

I'll start by outlining what I have done based on my 3 or 4 days of research and scouring the forums prior to posting here, and then I'll move forward with my questions.

Here is what I have done;

Fresh install off CD

Installed and Configured Firestarter

Enabled firewall (...)



Here is my question;

From what I have been reading and from what I can tell based on Shields Up! scan results, out of the box Ubuntu has nothing opened to the general public and thus no cause for concern,  but I use "Transmision" for torrent downloading and I'm just wondering if there are any other precautions I should take in order to keep my system safe? 

I have read about disabling IPV6 as it is not covered by my firewall? Y/N
Disabling ICMP echo replies (ping) ? (Worth it?) Y/N
Learning to read the logs?
Use Shields Up! regularily?
Security Updates Daily
... and many more

As far as I am concerned, I have come to the conclusion that so long as I don't start any servers or add any software that has known vulnerabilities that I will be "safe" as is... Am I dreaming? (Please keep in mind I cannot trust my local network, or the computers on it)

If any of you have any security tips you feel I could use, please post away. I will appreciate any quality linkage to tutorials or guides you may know of (not afraid to read, not expecting handouts).

Please let me know if you think or not that I have a safe setup for a desktop and if I can now sit back and concentrate on implementing more advanced features at my discretion at this point.

Thank you in advance!

---

### Post by oldos2er on 2010-10-05
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by rCiv on 2010-10-05
Thank you sir, that ehm...that sums it up very well, ok back to the lab then. 

See you guys in a few days.:)

---

### Post by nevius on 2010-10-05
Firestarter is old and no longer maintained. You should remove it and use UFW. 

You should also look into apparmor. Bodhi Zazen has a good apparmor primer here: [http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

and has a  profile for transmission here: [http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.04/](http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.04/)

Apparmor is probably the most effective way that you can protect your computer (apart from enabling / installing only the services that you need and know how to use).

The "Shields Up" website will only scan your router's firewall (assuming that your computer is behind a router).

---

### Post by rCiv on 2010-10-05
> **nevius said:**
> Firestarter is old and no longer maintained. You should remove it and use UFW. 

You should also look into apparmor. Bodhi Zazen has a good apparmor primer here: [http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

and has a  profile for transmission here: [http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.04/](http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.04/)

Apparmor is probably the most effective way that you can protect your computer (apart from enabling / installing only the services that you need and know how to use).

The "Shields Up" website will only scan your router's firewall (assuming that your computer is behind a router).


That would explain why Shields Up! constantly fails me saying that I answered to a ping when I disabled it on my system, I dont suppose you know how to adjust that on SMC routers do you? (Can't seem to find the option in the Web interface for the router, my ISP tech support is clueless, and SMC tech support is a 2 hour project to get through on the phone...

---

### Post by nevius on 2010-10-05
> **rCiv said:**
> That would explain why Shields Up! constantly fails me saying that I answered to a ping when I disabled it on my system, I dont suppose you know how to adjust that on SMC routers do you? (Can't seem to find the option in the Web interface for the router, my ISP tech support is clueless, and SMC tech support is a 2 hour project to get through on the phone...

I think that the problem Shields Up has with your router is that it is rejecting the connection attempt rather than dropping it. If this is the case, then I wouldn't bother trying to change it. It's not worth the time. Your network is arguably just as safe as if your firewall was dropping the connection.

This does not apply if Shields Up is detecting open ports.

---

### Post by rCiv on 2010-10-06
> **nevius said:**
> I think that the problem Shields Up has with your router is that it is rejecting the connection attempt rather than dropping it. If this is the case, then I wouldn't bother trying to change it. It's not worth the time. Your network is arguably just as safe as if your firewall was dropping the connection.

This does not apply if Shields Up is detecting open ports.


/agreed - all ports are stealth but it is not "dropping" the attempt.

So I'm not totaly obscured, however I just read something on here while i was lurking earlier that mentioned "security through obscurity" wasn't such a big deal anymore... but im just regurgitating what I read and completely talking out my *** on this, if anyone feels like elaborating on that I'll give it a thorough read.

---

### Post by rCiv on 2010-10-06
On a second note, how would i go about scanning my computer and not the firewall? Hook up a laptop to the network and nmap it?

***edit, i'm going to bed and I'm a few pages away from the whole network auditing part of the noob security guide, I understand if you all want to let me get to it lol...

---

### Post by nevius on 2010-10-06
> **rCiv said:**
> On a second note, how would i go about scanning my computer and not the firewall? Hook up a laptop to the network and nmap it?

***edit, i'm going to bed and I'm a few pages away from the whole network auditing part of the noob security guide, I understand if you all want to let me get to it lol...

I run nmap from a jailbroken 1gen iPod touch.

---

