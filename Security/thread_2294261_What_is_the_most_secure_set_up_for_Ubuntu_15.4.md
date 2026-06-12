---
title: "What is the most secure set up for Ubuntu 15.4 ?"
date: 2015-09-10
forum: Security
---

### Post by david434 on 2015-09-10
I am on a quest to come up with the safest system I can.  My thoughts  are to use Ubuntu 15.4 with VyprVPN, Firefox with NoScript/HTTPS  Everywhere/Track Me Not/AdBlock Plus/Ghostery, run Chkrootkit 5.0 and  RKhunter.  You may not agree, but I encrypted my entire drive in  addition to my Home folder.  Also, I check my logs, use Tripwire, ClamTK, and ufw.


Then part of the time I use TAILS (from disk), standard 1.5.1

Any other ideas?  I appreciate your thoughts. 				

---PS.  Not that I trust ClamTK!!  And what's up with having a disabled firewall by default?  Scary.   Also, why are security programs not listed in the Ubuntu Software Center so users can easily see them?  Is it because security is not a priority?  Has this been done on purpose?

---

### Post by CharlesA on 2015-09-10
Seeing as there are no ports listening for connections by default on a Ubuntu install, you don't really need a firewall enabled, and that is how it has been set up by default.

If this is a desktop install, you are going completely overboard. Best case scenario of using all those applications is you might get a notification that a file has changed after an update. Worse case - a ton of false positives that will only lead you to being more paranoid.

If you do not trust ClamTK, why even bother using it? It is known for false positives. As for these "security programs" not showing in software center... which security programs are you talking about? If it's things like tripwire, why would a normal desktop user need to install that on their desktop install? Server installs, I can see for intrusion detection, but unless you are running services off a desktop install (why??) you do not need it.

---

### Post by maglin2 on 2015-09-10
Here is a link to a guide on linux workstation security that was posted in the forum recently.

[https://github.com/lfit/itpol/blob/master/linux-workstation-security.md](https://github.com/lfit/itpol/blob/master/linux-workstation-security.md)

It  is said to be aimed at systems administrators who are remote workers,'to help ensure that their workstations pass core security requirements in order to reduce the risk that they become attack vectors'. This is probably not exactly the same thing as ensuring that your own security/privacy aren't compromised, but there must be significant overlap.

---

### Post by CharlesA on 2015-09-10
In addition to the link magin2 posted, there is also a document on basic security here:
[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

---

### Post by david434 on 2015-09-11
At Maglin2--thanks a lot, that was very informative.

---

### Post by david434 on 2015-09-11
At CharlesA--thanks a lot.  

Well, by "security programs" I meant RKHunter, ChkRootkit, ClamAV, all of them.  I was just making a general observation that Ubuntu does not even list security programs.  That surprised me.

Many people who work in the US intell community want to have robust security for their personal devices.  As a rule of thumb, that means to take all precautions that are possible.  If something as basic as a firewall is turned off, that sends a clear signal to anyone who is not asleep.

Thanks again for your help and I will read that document thoroughly.

---

### Post by The Cog on 2015-09-11
> If something as basic as a firewall is turned off, that sends a clear signal to anyone who is not asleep.
And how do you think a firewall would improve the security of a default Ubuntu install? What would it prevent?

---

### Post by david434 on 2015-09-11
Quote (from DangerTux, in 2011):

"There are two additional factors that come into play there. One, if you  do not utilize a firewall on the basis that you have no open ports, you  are crippling your own security because if an application that you do  have is exploited and code execution occurs a new socket can be created  and bound to an arbitrary port. The other important factor here is that  if you are not utilizing a firewall you also have no outbound traffic  control whatsoever. In the wake of an exploited application, instead of a  new socket being created and a port being bound, another alternative an  attacker can utilize is to create a reverse connection back to a  malicious machine. Without any firewall rules in place this connection  will go through unhindered.

[Article demonstrating how different types of firewall rules can be bypassed by an attacker.]("http://dangertux.wordpress.com/2011/10/03/a-firewall-is-not-a-catch-all/")


 If you were setting up a desktop system with best practices in mind you  would want both strict inbound and strict outbound firewall rules. This  would minimize the impact of either a listening service being bound or a  reverse connection being initiated."

---

### Post by The Cog on 2015-09-11
Fair enough, if you are going to the effort of whitelisting all the IP addresses you might ever want to browse to. I don't know many users who do that though. It's reasonable in a server environment (we have http access only to whitelisted sites such as windows and linux update servers), but unlikely for desktop users.

---

### Post by maglin2 on 2015-09-11
If I'm reading DT's article correctly it seems to imply that there is actually  little point in having outbound firewall rules because any exploit worthy of the name will simply choose an outbound port that must have been opened to connect to it in the first place (eg 53, 80 or 443). Application specific outbound rules (as I seem to recall was the norm with Comodo and other windows firewalls I once used) might be of use, but only if the exploit can be recognised as a discrete application, and not just part of whatever application it has exploited.

---

### Post by david434 on 2015-09-11
DangerTux's article is excellent.  He really knows how to explain complex things clearly.  This kind of post makes this forum invaluable.

---

### Post by The Cog on 2015-09-11
> **maglin2 said:**
> If I'm reading DT's article correctly it seems to imply that there is actually  little point in having outbound firewall rules because any exploit worthy of the name will simply choose an outbound port that must have been opened to connect to it in the first place (eg 53, 80 or 443). Application specific outbound rules (as I seem to recall was the norm with Comodo and other windows firewalls I once used) might be of use, but only if the exploit can be recognised as a discrete application, and not just part of whatever application it has exploited.
I agree entirely with this. Whitelisting every web site you want to visit is too much of a PITA for your typical user, including myself. 

I don't know if application specific rules are all that reliable - whether malware could masquerade as a trusted app. Launching a trusted utility in the background perhaps. They seem common in windows but not linux for some reason. 

Linux can do user specific rules, which I haven't seen used in either linux or windows based firewalls.

And all this assumes the malware doesn't just disable the firewall anyway.

---

### Post by ant2ne on 2015-09-11
The firewall on linux conversation comes up quite a bit. You forget that malware COULD run in userland. Without rooting the machine. And could then be used as a launchpad to find other more vulnerable systems in your network. Or the malware could open listeners to let other things into the box. A few simple iptables rule would prevent that. As for blocking outgoing ports: if you allow established,related and ports 443, 80, 123 and 53 (maybe a handful of others) for outgoing and block the rest the average user would probably never notice.

Security is layers. Your host based firewall is one of those layers.

---

