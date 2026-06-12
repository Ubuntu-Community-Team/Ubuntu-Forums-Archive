---
title: "Interesting facts about the Panda DesktopSecure Suite!"
date: 2006-08-07
forum: Server Platforms
---

### Post by Chrissss on 2006-08-07
The Panda DesktopSecure Suite fails in multiple ways. It took us few hours to find essential flaws inside the firewall and the virus scanner.

First) 

The firewall stores only the path of a binary which should be allowed to contact the network interfaces. This is a major flaw, when it comes to programs which are written in interpreted programming languages like Python. When you open e.g. gajim (an IM client) and contact the network, a warning pops up, that "/usr/bin/python2.4" want's to contact the network. Of course you answer that question with yes. After that you open e.g. QuodLibet (a music player written also in Python) and you've got unrestricted network access to internet radio stations. Which means every program written in Python has full internet access once you allowed the Python interpreter.

[[img]http://img468.imageshack.us/img468/2828/pandaeq7.th.png[/img]](http://img468.imageshack.us/my.php?image=pandaeq7.png)

Second)

The firewall doesn't build checksums of binaries which are inside its positive list. Open lynx, let it contact the internet, replace a binary like lynx with wget and there's no warning when you use your "new" lynx to get a file from the internet. One might argue, that you need root rights to replace a binary in /usr, but people do install software inside their homes or even use [klik](http://klik.atekon.de/) to install software inside their homes.

Third)

The Firewall is started by adding it to the gnome session. Adding a program or script to your gnome session, so that it starts before the firewall ui, leads to a program which can contact the internet without interaction of the panda firewall.

Fourth)

Typical email ports like 25 (smtp), 110 (pop), 143 (imap) get redirected to the panda mailproxy, so that it can scan emails before they are read. But IMAPS (port 993) is not. So when you use SSL-encrypted IMAP, it might be possible e.g. to use an exploit on a mail client to show a manipulated picture (similare to the wmf exploit like windows).

Conclusion)

We doubt that this "security" suite is a security plus at all. We didn't use fancy techniques, no packet sniffers, no reverse engineering. Just simple a simple "let's take a look, what happens when we do..." 

Yours
Security Supporters [otzenpunk](http://www.ubuntuusers.de/users/otzenpunk/) and [Chrisss](http://www.ubuntuusers.de/users/Chrissss/) of [UbuntUsers.de](http://www.ubuntuusers.de)

[1]: If you are able to read german you might enjoy our german original [report](http://forum.ubuntuusers.de/topic/42047/), which has got a few more details etc.

---

### Post by nikro on 2006-08-08
Good Job!

---

### Post by Ride Jib on 2006-08-08
Nice findings. I wonder what the backgrounds are of the developers of said 'security suite'...

---

### Post by LordHunter317 on 2006-08-10
> **Chrissss said:**
> The Panda DesktopSecure Suite fails in multiple ways.Not especially.

> The firewall stores only the path of a binary which should be allowed to contact the network interfaces.Yeah, it's an iptables limitation.  It's actually more limited than that, as there's a hard path length limit << MAXPATH.

> Which means every program written in Python has full internet access once you allowed the Python interpreter.Welcome to UNIX.  This is why no one botheres with command-based filtering.  Nevermind it doesn't add much security anyway.

> The firewall doesn't build checksums of binaries which are inside its positive list.Again, iptables limitation.

> One might argue, that you need root rights to replace a binary in /usr, but people do install software inside their homes or even use [klik](http://klik.atekon.de/) to install software inside their homes.And?  If an attacker can compromise the system and install a trojaned binary, he can also bypass a message saying "binary changed".  Popups like this serve no security purpose whatsoever.

"Hey, this binary was changed!"  "Of course it was, I was one the one who did it."

> But IMAPS (port 993) is not. So when you use SSL-encrypted IMAP, it might be possible e.g. to use an exploit on a mail client to show a manipulated picture (similare to the wmf exploit like windows).Hey, it can't read SSL-encrypted connections.  No virus client can without explict client support for passing the message to the AV engine.  Big surprise there.

---

### Post by Chrissss on 2006-08-12
@LordHunter317

I think you didn't get our intentions right. In our forums there was a huge fight about this software. One side said "finally a personal firewall for linux" the other side said "you don't need one, because the concept of a pf is wrong" etc. Unfortunately the ZoneAlarm brainwashed "pro" side was very loud and yelled out, that this piece of software is useful... Unfortunately those people couldn't be stopped by arguing with them, so we had to come up with some first hand arguments.

Our goal wasn't to show that panda could have delivered a better product, but to show that their marketing
> ...This powerful solution incorporates antivirus technologies, heuristic technologies and a firewall aimed at protecting Linux computers from malware, and preventing these computers from being used as a gateway to spread infections across the Windows workstations in the local network....
[http://www.pandasoftware.com/products/DesktopSecure](http://www.pandasoftware.com/products/DesktopSecure)
is selling snakeoil.

BTW, they don't just use plain iptables rules, they divert the traffic via "-j QUEUE" rules into userspace, where a daemon picks up those packets. So they cope with the limitations of iptables.

CU
 Christoph

---

### Post by LordHunter317 on 2006-08-13
> **Chrissss said:**
> I think you didn't get our intentions right.Well, you didn't make them quite apparent here :p

Nevertheless, some of the logic presented didn't quite follow to me.

> Our goal wasn't to show that panda could have delivered a better product, but to show that their marketing is selling snakeoil.Of course it's snakeoil.  It's all snakeoil.

> BTW, they don't just use plain iptables rules, they divert the traffic via "-j QUEUE" rules into userspace, where a daemon picks up those packets.I thought they used some other rules as well.  It's been quite some time since I looked at their ruleset.

---

### Post by PDSSWDT on 2006-08-22
Hi, 

We are working at Panda Software developing Panda DesktopSecure product, and after reading this post, we think it could be useful to try to answer some of the topics.

The firewall shipped with DesktopSecure product is as you have said an application firewall, as it filters all incoming and outgoing traffic with "system rules" (based on network parameters) and "application rules" (based on applications trying to access network).

Some comments about topics posted, and explanations of how firewall works:

> The firewall stores only the path of a binary which should be allowed to contact the network interfaces.[...] Python has full internet access once you allowed the Python interpreter
The firewall asks about interpreter application and not about interpreted application: This happens with perl, python, java, mono, KDE suite applications, etc. We inform the user through the popup message that accepting this communication entitles the acceptance of all the future communications that make use of this interpreted language. Nevertheless, this is being improved for a future version.


> The firewall doesn't build checksums of binaries which are inside its positive list.
We are also working on this for a future version. 

> The Firewall is started by adding it to the gnome session
This is not really true. Firewall starts at boot time. Nevertheless, there is a problem with machines that need remote mounts at boot time that could lead to hang machines during boot if rules are made effective too soon. We are working on it at the moment. 

> Encrypted mail protocols are not scanned
This is not our fault.  It also happens with password encrypted files, that cannot be scanned. One way to do this would be using some hook on every mail user agent. In our opinion, this is too intrusive.


We are happy to receive feedback about the product, since we are working hard to improve it. 

It is glad to see the interest arising around the product; be sure we will do our best to fulfill the expectations.

Panda DesktopSecure SW Development Team

---

### Post by Chrissss on 2006-08-28
> **PDSSWDT said:**
> The firewall asks about interpreter application and not about interpreted application: This happens with perl, python, java, mono, KDE suite applications, etc. We inform the user through the popup message that accepting this communication entitles the acceptance of all the future communications that make use of this interpreted language. Nevertheless, this is being improved for a future version.
I'm looking forward to see how you are going to solve that dilema ;) 

> **PDSSWDT said:**
> This is not really true. Firewall starts at boot time. Nevertheless, there is a problem with machines that need remote mounts at boot time that could lead to hang machines during boot if rules are made effective too soon. We are working on it at the moment.
We were able to bypass the firewall by adding a program to the gnome session. So let's say the the reporting mechanism doesn't work until the GUI is completely up and running

> **PDSSWDT said:**
> This is not our fault.  It also happens with password encrypted files, that cannot be scanned. One way to do this would be using some hook on every mail user agent. In our opinion, this is too intrusive.
Of course this is not the fault of your product, but a fault in your ads. Tell your PR, that this ad
--
Email is the main means of propagation used by malware. It is essential to ensure that you have _permanent_ protection that monitors the email messages sent to users’ mailboxes in order to eliminate the threat before it infects the file system. Panda DesktopSecure scans mail reaching the most widely used mail clients, such as Ximian Evolution, Kmail, Mozilla Mail and Thunderbird
--
needs a addition "as long as you don't use encrypted protocols". Which is what every mailuser should do... Which renders the mail filter apriori useless.

The main issue remains. All this hype for non-existing threats... I wish you luck with your product. Really. But instead of using the old-fashioned windows marketing trick "Scare the users until they buy your security software", what about the simple truth... 

And why not build a product which "just" works without "threat" levels and big buzz words. You are the first company in the market. So, build your product correct, and the community might appreciate your work :)

Sincerly
Christoph

---

