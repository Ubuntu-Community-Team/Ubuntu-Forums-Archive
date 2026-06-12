---
title: "NB: I think my system's been hacked! What do I do?"
date: 2006-01-19
forum: Server Platforms
---

### Post by fergus.b on 2006-01-19
Hi

It seems very likely that a hacker has somehow gained access to my system. 

There are weird things happening like:
- as soon as I go online the screen blanks and I can't get control back of the pc at all
- there's a file called dbootstrap_settings in my root folder that I've never seen before (although it might be perfectly legit)
- when I tried to run gksudo for something it reported that it couldn't get access to the keyboard and there might be a third party eavesdropper on what I was typing
- etc.

This is the first time anything like this has happened to me on Linux - I don't have a clue where to start and I'm not too clued up about Linux security (although would definitely like to learn more). 

At this point I'm thinking the best would be to reinstall to make sure that I get rid of all the backdoors, rootkits, etc. that might have been installed. Seems to be the safest to me.

Any suggestions?

---

### Post by LordHunter317 on 2006-01-19
[QUOTE=fergus.b]
There are weird things happening like:
- as soon as I go online the screen blanks and I can't get control back of the pc at all[/quote]That's odd, but sounds like hardware to me.

> - there's a file called dbootstrap_settings in my root folder that I've never seen before (although it might be perfectly legit)That was there from install.

> - when I tried to run gksudo for something it reported that it couldn't get access to the keyboard and there might be a third party eavesdropper on what I was typingThat can be a problem. or a illegimate error.

I don't see anything to be worried, ATM.

---

### Post by HJThis on 2006-01-19
Hello,fergus.b

Sorry to hear about your problem but i would hold off
on a reinstall tell one of the pros here have a look at this
for you.

but i will add this if you can get on some other
PC before the reinstall download 

rkhunter & chkrootkit

Best of luck

---

### Post by gord on 2006-01-19
just in case though its allways a good idea to get a firewall going

---

### Post by LordHunter317 on 2006-01-19
No, it isn't.

---

### Post by Galoot on 2006-01-19
Whatever. Let's stay on the topic.

---

### Post by LordHunter317 on 2006-01-19
:rolleyes: Because you've provided a wealth of relevant or helpful information...

---

### Post by fergus.b on 2006-01-19
[QUOTE=HJThis]but i will add this if you can get on some other
PC before the reinstall download 

rkhunter & chkrootkit

Best of luck[/QUOTE]
Thanks for that tip, HJThis. I've got a Knoppix 4 cd so I'm going to try get online with that. If I can download those apps I'll scan my Ubuntu install from Knoppix.

---

### Post by LordHunter317 on 2006-01-19
That would be reasonable I suppose, but I'd be somewhat shocked if you found anything.

---

### Post by fergus.b on 2006-01-19
Ok, I've scanned using rkhunter and chkrootkit from both Knoppix and Ubuntu now. From Knoppix nothing was detected. There were some warnings when I ran it from Ubuntu though. 

Firstly when I did apt-get install rkhunter it said it depended on postfix so I installed that as well. I just find it funny for rkhunter to need postfix, they don't seem related. If I try remove postfix it says it needs to also remove mailx and rkhunter?? 

Then rkhunter gave a warning when scanning for hidden files:
> Please inspect: /dev/.static (directory)  /dev.udevdb (directory)  /etc/.java (directory)
I had a look at these folders: 
/dev/.static basically looks like a duplicate of /dev and is 112K
/dev/.udevdb has a few hundred files beginning with class@*, each of which is around 30 - 50 bytes totalling 2.8M
/etc/.java has one empty folder in it called deployment

So I can't spot anything overly suspicious in any of those, but then I wouldn't really know how anyway. And that was all rkhunter came up with.

chkrootkit said something about dhclient3 but I can't get it to repeat it and I didn't save the message. If I can get it to print it again I'll post that message.

Edit - here's the message: wlan0: PACKET SNIFFER(/sbin/dhclient3[9235])

I'm feeling a bit better about things today. The systems more stable and I'm thinking it might have been my wireless hardware and ndiswrapper playing up but I just want to make sure. Thanks for the help everyone.

---

### Post by LordHunter317 on 2006-01-19
> **fergus.b]Ok, I've scanned using rkhunter and chkrootkit from both Knoppix and Ubuntu now. From Knoppix nothing was detected. There were some warnings when I ran it from Ubuntu though. [/quote]You never run it on your potentially compromised system said:**
> rkhunter wants to mail stuff using mailx, this requires an MTA.  The default MTA is postfix.



> Then rkhunter gave a warning when scanning for hidden files:

I had a look at these folders: 
/dev/.static basically looks like a duplicate of /dev and is 112K
/dev/.udevdb has a few hundred files beginning with class@*, each of which is around 30 - 50 bytes totalling 2.8M
/etc/.java has one empty folder in it called deployment

So I can't spot anything overly suspicious in any of those, but then I wouldn't really know how anyway. And that was all rkhunter came up with.All of those are normal.  The first two are consequences of udev running.  The third is just Java.  Empty folders are nothing to be concerned about.

Edit - here's the message: wlan0: PACKET SNIFFER(/sbin/dhclient3[9235])Yes, of course your DHCP client is a packet sniffer.  This is a false positive.

---

### Post by fergus.b on 2006-01-19
Ok thanks, LordHunter317. Looks like I might've gotten all exited for nothing :o

Do I need to be concerned about securing my Ubuntu above and beyond the default settings. I have firestarter installed but I don't normally run it - isn't it just a nice frontend for iptables?

---

### Post by dbee on 2006-01-19
Try bastille from the repositories. It's a pretty cool security script that walks you through a some steps to hard your linux box. It can build you a firewall too if you wish. 

You might try nessus too while your at it. And make sure your ssh has a strong password.

---

### Post by fergus.b on 2006-01-19
Cool, I'll try those out, thanks dbee.

---

### Post by LordHunter317 on 2006-01-19
[QUOTE=fergus.b]Do I need to be concerned about securing my Ubuntu above and beyond the default settings.[/quote]Unless you're running a server, no.  Don't be stupid on the Internet.

> I have firestarter installed but I don't normally run it - isn't it just a nice frontend for iptables?Yes, it is.

---

