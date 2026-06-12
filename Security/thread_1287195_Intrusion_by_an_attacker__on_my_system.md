---
title: "Intrusion by an attacker  on my system"
date: 2009-10-09
forum: Security
---

### Post by sparker1 on 2009-10-09
Hello,
I am a new (noob) Ubuntu user. When I was configuring samba for printing from other windows machines I turned off firestarter and forgot to turn it back on. That was probably the start of the problem but now I have an attacker using my ubuntu computer - the mouse will move by itself, a terminal opens and the attacker is exploring the various drives on my computer. There was also an ttempt to hijack the browser by re-typing an address on the address bar of firefox. I guess it is a trojan of some kind. If this was windows I could use various programs to get rid of it but I don't know enough about Ubuntu. That is why I am here. Is there anyone that has any suggestions? The system is a dual boot Ubuntu/XP and so far the XP system still seems to work fine. Ubuntu will boot but after a few minutes the attacker is there exploring away. So far nothing malicious just intrusion and exploration! Grateful for any help.

---

### Post by wojox on 2009-10-09
Yeah reinstall Ubuntu. Any computer that gets compromised needs to be reformatted and reinstalled.
Even Windows.

---

### Post by theozzlives on 2009-10-09
> **wojox said:**
> Yeah reinstall Ubuntu. Any computer that gets compromised needs to be reformatted and reinstalled.
Even Windows.

Boo! Not a trojan, and firestarter is just a front end for iptables (that runs all the time). My guess is you have Remote Desktop enabled. Just turn it off.

---

### Post by update_manager on 2009-10-09
> **sparker1 said:**
> Hello,
I am a new (noob) Ubuntu user. When I was configuring samba for printing from other windows machines I turned off firestarter and forgot to turn it back on. That was probably the start of the problem but now I have an attacker using my ubuntu computer - the mouse will move by itself, a terminal opens and the attacker is exploring the various drives on my computer. There was also an ttempt to hijack the browser by re-typing an address on the address bar of firefox. I guess it is a trojan of some kind. If this was windows I could use various programs to get rid of it but I don't know enough about Ubuntu. That is why I am here. Is there anyone that has any suggestions? The system is a dual boot Ubuntu/XP and so far the XP system still seems to work fine. Ubuntu will boot but after a few minutes the attacker is there exploring away. So far nothing malicious just intrusion and exploration! Grateful for any help.

Reinstalling Ubuntu seems to be the best way to go in my opinion.

After the reinstall, you might want to use a new password and make sure a firewall (ufw) is enabled.

---

### Post by sparker1 on 2009-10-09
> **theozzlives said:**
> Boo! Not a trojan, and firestarter is just a front end for iptables (that runs all the time). My guess is you have Remote Desktop enabled. Just turn it off.
 
Thanks for the quick replies. I thought about re-installing but thought I would see what was said here first. I will turn off "Remote desktop" and see what happens. I am at work now so I won't be able to do it for another 8 hours. unless I do it remotely!  lol!

---

### Post by theozzlives on 2009-10-09
> **update_manager said:**
> Reinstalling Ubuntu seems to be the best way to go in my opinion.

After the reinstall, you might want to use a new password and make sure a firewall (ufw) is enabled.

Why is everybody so quick to have this poor OP to go through the hassle of a re-install? IPTables is THE ONLY firewall, all the other programs are just front-ends to set the rules of IPTables!

Just disable Remote Desktop or set/change the password (System > Preferances > Remote Destop). If you want just change your password (System > Administration > Users and Settings), you don't need to re-install!

---

### Post by lovinglinux on 2009-10-09
> **theozzlives said:**
> Why is everybody so quick to have this poor OP to go through the hassle of a re-install? 

Because the attacker could have "planted some seeds" on the machine. Best practice is indeed to reinstall, so you can be sure the system is clean again.

---

### Post by Chayak on 2009-10-10
Turing on remote desktop on an internet facing (not behind a router or having connections directed to that machine) is security suicide.  It's not low hanging fruit with no password.  It's a special delivery to anyone who portscans looking for open ports.

Reinstall the system.  It's way too easy to hide a backdoor in *nix boxes and very hard to dig them out even for experts.  Nuke it from orbit, it's the only way to be sure.  Then UFW enable, default to deny, and don't allow any outside connections until you study up on how to properly secure it.

---

### Post by unspawn on 2009-10-10
> **theozzlives said:**
> Why is everybody so quick to have this poor OP to go through the hassle of a re-install?
Simply because this forum is FFA and a lot of people here who reply (as far as I can tell from the width and depth of their replies) are not that skilled when it comes to basic security concepts, let alone having practical experience with incident response or even forensics.

If a system is (perceived) breached it should no longer be trusted nor used. It should be isolated until a decision is made to investigate or to reformat & reinstall. Note that in scenarios where the point(s) of entry are unknown just reinstalling might just as quickly expose the same loophole again.


* BTW, and with all due respect, but calling reinstallation a "hassle" points to a flaw in your perception. As running GNU/Linux is (or should be) based on performance and providing services in a continuous, stable and secure way, when there is doubt that doubt should be addressed properly and timely. If the outcome is to reformat and reinstall then one should realise that updating, proper system hardening, auditing regularly and best practices are there for a reason.

---

### Post by theozzlives on 2009-10-10
> **unspawn said:**
> and with all due respect, but calling reinstallation a "hassle" points to a flaw in your perception.

It would probably be a hassle for the OP because he/she is new, probably don't have a separate /home, and would probably not know how to save any 3rd party sources and software.

---

### Post by Rob_H on 2009-10-10
+1 for reinstalling. The attack you witnessed might not have been the only one that occurred. You can't trust that box anymore, regardless of what OS it is running.

After reinstalling, I would also recommend rethinking the idea of exposing any service over the Internet for any period of time without securing it first. If you need to share files with Windows machines over the Internet, there are better tools than Samba from a security standpoint. SSH (SFTP) is one, but again, it needs to be secured like any other service. People here can help you do that, or there are [plenty of web pages]("http://www.google.com/search?q=securing+ssh") on the subject.

---

### Post by Kinstonian on 2009-10-10
Reinstalling the OS is always the most secure option.  However, people and businesses generally don't exist to be secure, so the most secure option is not always the **best** option.

1.  What if the attacker didn't get root?
2.  What if a rootkit wasn't installed?
3.  What if the attacker wasn't even able to get his toolkit on the system because a firewall filtered outbound connections?
4.  What if it was a skiddie who didn't bother deleting any evidence and you have the skills to recover without a reformat?
5.  What if the service was chrooted and there was no evidence of the attacker escaping it?
6.  What if the victim was a mission critical server and management couldn't tolerate the downtime?
7.  What if it was malware that only stayed in memory and a simple reboot would fix the problem?
8.  What if all of the above was true and you wanted to recover the best you can, then increase the monitoring of the system to see if the attacker ever returned?

I'm not saying reformatting didn't turn out to be the best thing to do with this incident.  I just constantly see people prematurely telling others to reformat after getting hacked, not only without enough information to make that decision, but they even say to reformat without figuring out how it happened so it can be prevented from happening again.  Sometimes, they say to reformat without even being sure an incident really occurred.  Trust me, reformatting, should be one of the last steps of incident recovery, not the first.

And to the OP, containment is the next step that should be taken after an incident has been detected.  Leaving a compromised system online like that was a not a good idea. ;)

---

### Post by sparker1 on 2009-10-10
> **Kinstonian said:**
> 
And to the OP, containment is the next step that should be taken after an incident has been detected.  Leaving a compromised system online like that was a not a good idea. ;)
Thanks to everyone. I did, indeed, leave the remote desktop open. I think I did that when I was having so much trouble getting my windows computers to see the printer. Obviously, that was both stupid and unrelated to the printer.  It has been turned off now and there is no more suspicious activity (that I can tell).
If I don't reinstall what "containment" measures are recommended? Are there any online places that a Ubuntu computer can go like Windows can eg. for online scans etc?

---

### Post by Rob_H on 2009-10-10
> **sparker1 said:**
> Are there any online places that a Ubuntu computer can go like Windows can eg. for online scans etc?

There's no such thing as a web-based virus scan for Windows or any other OS. I believe what you're thinking of are misleading ads that appear on some web sites that claim to scan your computer in order to sell you software.

---

### Post by lovinglinux on 2009-10-10
> **Rob_H said:**
> There's no such thing as a web-based virus scan for Windows or any other OS. I believe what you're thinking of are misleading ads that appear on some web sites that claim to scan your computer in order to sell you software.

There are several web-based virus scanners for Windows like [Kaspersky Online Scanner ](http://www.kaspersky.com/virusscanner)and others. But they need to install an engine on your machine anyway.

But I still believe the best course of action on this case is to re-install Ubuntu.

---

### Post by jerome1232 on 2009-10-10
I don't see how anybody could have made a connection, a router is effectively a firewall and if you have multiple computers your are behind a router.

Unless this attack was coming from behind your router.

---

### Post by sparker1 on 2009-10-11
> **jerome1232 said:**
> I don't see how anybody could have made a connection, a router is effectively a firewall and if you have multiple computers your are behind a router.
 
Unless this attack was coming from behind your router.
 
Yes, I am definitely behind a router and a switch but there isn't anybody here (at home) that would be able to do what I saw happenning. It was my daughter who originally noticed the activity (like, who wouldn't when a terminal opens up and typing starts). She called me down and I saw it myself. The attacker called himself/herself the "turkish team". Since the remote desktop has been turned off there hasn't been any more visible problems. I'm still thinking about a reinstall.

---

### Post by update_manager on 2009-10-11
> **theozzlives said:**
> Why is everybody so quick to have this poor OP to go through the hassle of a re-install? IPTables is THE ONLY firewall, all the other programs are just front-ends to set the rules of IPTables!


How can he know what access an attacker has to his system? 

Since he can't easily (arguably possibly) know that, the only solution is to reinstall.

ufw is considerably easier for a user to use than writing iptables scripts.

---

### Post by update_manager on 2009-10-11
> **jerome1232 said:**
> I don't see how anybody could have made a connection, a router is effectively a firewall and if you have multiple computers your are behind a router.

Unless this attack was coming from behind your router.

Some versions of VNC use a server in the middle to allow connections to hosts behind NATs.

Also, the attacker could just open up ports on the router using a variety of XSRF or XSS attacks.

---

### Post by update_manager on 2009-10-11
> **Kinstonian said:**
> 
1.  What if the attacker didn't get root?
2.  What if a rootkit wasn't installed?
3.  What if the attacker wasn't even able to get his toolkit on the system because a firewall filtered outbound connections?
4.  What if it was a skiddie who didn't bother deleting any evidence and you have the skills to recover without a reformat?
5.  What if the service was chrooted and there was no evidence of the attacker escaping it?
6.  What if the victim was a mission critical server and management couldn't tolerate the downtime?
7.  What if it was malware that only stayed in memory and a simple reboot would fix the problem?
8.  What if all of the above was true and you wanted to recover the best you can, then increase the monitoring of the system to see if the attacker ever returned?


Some counter arguments:

1. So? If the attacker has access to a regular user account, they have access to files owned by the user, firefox traffic, etc.

2. Even if one wasn't, its very hard to confirm that the attack was limited to a specific vector.

3. How could you know this? Confirming that the firewall stopped installation of an attack toolkit is possible, confirming that it stopped all attempts to install a toolkit is much harder.

4. How do you know it wasn't a super hacker who threw some crap around?

5. Valid. Works for anything with a reasonable sandbox (javascript, Flash)

6. No backup server? Epic fail.

7. Impossible to know for sure.

8. Valid.

---

### Post by The Cog on 2009-10-11
> **sparker1 said:**
> Yes, I am definitely behind a router and a switch but there isn't anybody here (at home) that would be able to do what I saw happenning. It was my daughter who originally noticed the activity (like, who wouldn't when a terminal opens up and typing starts). She called me down and I saw it myself. The attacker called himself/herself the "turkish team". Since the remote desktop has been turned off there hasn't been any more visible problems. I'm still thinking about a reinstall.

That causes me real concern. Unless you have forwarded port 5900 through the router to your Ubuntu box then the unknown user must have been using one of your windows boxes as a stepping-stone to get to the Ubuntu system. It seems to me that you might be well and truly compromised.

---

### Post by unspawn on 2009-10-11
> **The Cog said:**
> Unless you have forwarded port 5900 through the router to your Ubuntu box then the unknown user must have been using one of your windows boxes as a stepping-stone to get to the Ubuntu system. 
Unless the OP provides "evidence" that's nice but it's still pure speculation.


> **The Cog said:**
> It seems to me that you might be well and truly compromised.
If the system was compromised then evidence should be found. I'm surprised (OK, maybe not) nobody actually *asked* the OP for any...

---

### Post by sparker1 on 2009-10-11
> **unspawn said:**
> Unless the OP provides "evidence" that's nice but it's still pure speculation...

Guys, thanks for all the input and help. I don't think any of the windows boxes were on at the time. As far as evidence goes, unless someone can show me where the relevant logs are, if any, I won't be much help there. I can only give you my assurances that this was a genuine and witnessed event.  It has been 2 days now and there hasn't been any more problems since the remote desktop was turned off.

---

### Post by Jive Turkey on 2009-10-12
Some routers will pass connections to computers on their networks even without port forwarding or DMZ.

---

### Post by jerome1232 on 2009-10-12
> **Jive Turkey said:**
> Some routers will pass connections to computers on their networks even without port forwarding or DMZ.

How do they decide which computer to send the taffic to... just pick one randomly? I ask because I've never heard of this before.

---

### Post by Rob_H on 2009-10-12
> **jerome1232 said:**
> How do they decide which computer to send the taffic to... just pick one randomly? I ask because I've never heard of this before.

Jive is referring to a conventional router, not a NAT router/firewall.

---

### Post by unspawn on 2009-10-12
> **sparker1 said:**
> I don't think any of the windows boxes were on at the time. 
well, that's the nice thing about computing: you don't have to *think*. Just reading the system logs (and verifying filesystem contents) will make clear if the boxes were on or not at the time. (Mind you, not that I deal with mcrsft machines enough to point you to the logs w/o having to check the mmc myself.)


> **sparker1 said:**
> As far as evidence goes, unless someone can show me where the relevant logs are, if any, I won't be much help there.
About everything system or daemon-wise will log to /var/log (except VNC as it may log to /home/$LOGNAME/.vnc/*) so that's what you could look at. For instance any remote IP addresses that connect to your locally used VNC server port. While nothing beats reading logs, if that seems a daunting task to you, you could use 'logwatch' to create an easier digestible report for you.


> **sparker1 said:**
> It has been 2 days now and there hasn't been any more problems since the remote desktop was turned off.
That observation could point to the 0) measures having worked, 1) the intruder being scared off, 2) the intruder having moved on to another target or 3) Something Else (probably *A Larch* ;-p). In other words: without you actually checking your system it remains inconclusive. Checking logs and checking file integrity should provide the final "clean or compromised" verdict IMHO.

---

### Post by witeshark17 on 2009-10-12
What are the default desktop permissions? If the attacker wants to install software as a back door for later use, he may need to enter a password after a promt that he likely doesn't have. But obviously, a format and install would be advisable.

---

### Post by update_manager on 2009-10-16
> **jerome1232 said:**
> How do they decide which computer to send the taffic to... just pick one randomly? I ask because I've never heard of this before.

Sometimes NAT routers base destination choices on source IP, especially with UDP. 

For example if this happens:
Lan PC 1 (192.168.2.5) --> router --> (destination port 9000) Wan Server <public IP>

then the router allows this:
Lan PC 1 (192.168.2.5) <-- router <-- (source port 9001) Wan Server <public IP>

---

### Post by jerome1232 on 2009-10-16
That's an outgoing connection, not an incoming, if traffic comes to the wan ip for port 22 for example the router won't know which computer to forward it to without port forwarding rules.

 What your talking about happens with connections established by the computer behind the router.

---

### Post by Sam on 2009-10-17
Maybe the OP is using a unsecured wireless network ? That may explain why the attacker had bypassed NAT.

---

