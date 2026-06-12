---
title: "Are Trojans a threat on Linux?"
date: 2009-01-09
forum: Security
---

### Post by Ted_Smith on 2009-01-09
Me and my friends were chatting about software Firewalls that run on Windows. My friend has a router which, when probed, is fully stealthed (does not reply back, no open ports etc) so I told him to just tunr off ZoneAlarm, and the all the other Windows type Firewalls and just rely on your router FW which will be just fine. 

But one of them said about Trojans - "What if you get a Trojan that tries to communicate out? - your router will allow that whereas the software FireWall would block it" 

I said that might be a fair point and I said that because I use Linux I tend not to worry about things like that. 

But it made me think. Should I? Is a Linux box likely to get infected with a Trojan? I realise it needs root privs to install itself, but what about these web page based scripts (although I use 'NoScript' with Firefox). 

Ted

---

### Post by leg on 2009-01-09
If you install the software that contains a trojan then he has a point. I don't know if software firewalls block outward coms or not. Basic rule only install trusted software.

---

### Post by halovivek on 2009-01-09
first you should understand LINUX IS NOT WINDOWS.
as my experience i went to the sites in the internet which puts trojan in your system. if you visit in microsoft, it will be in browsers and it will send reports to the sites and it will gain your system knowledge. but in Linux cases i have tried the same thing and it can be done anything since Trojans are used to collect information and to hack the system. basically linux will not allow that. so there is no worry on that.

---

### Post by hyper_ch on 2009-01-09
if you install it there's nothing by default that would keep it from phoning home... but then, on linux, you don't go on shady sites to find crackz for the latest "whatever..."...

---

### Post by adamlau on 2009-01-09
I go to shady sites to find crackz for the latest "whatever..." :( :D . The short answer is that you are susceptible to exploits as long as you are connected to a network, particularly the Internet. No debating that point. However, ample anecdotal evidence points to the fact that a default Ubuntu install is fairly resistant to network attacks due to a number of inherent facilities. But as hyper_ch pointed out, there is no native outbound application firewall available in a default install. It stands to reason that on such a default install that the use of native tools such as AppArmor, ufw (iptables), permissions and cautious browsing habits are best bet solutions to deal with exploit potentials.

---

### Post by forger on 2009-01-09
> I go to shady sites to find crackz for the latest "whatever..."   
Maybe, but you don't go to shady sites for Ubuntu-related software.
Ubuntu has a centralized package maintenance and source repository that introduces old and new software to the user through package management.

That means, if you're interested in something, it's probably already packaged! Check out System > Administration > Synaptic Package Manager, or Applications > Add/Remove.
(Or Adept if you're using kubuntu/KDE)

---

### Post by The Cog on 2009-01-09
Don't get too complacent. Linux is not immune to infection by trojans, although it's probably harder than Windows for them. And anyone who goes to the effort of making a Linux trojan will probably have a handle on a flaw that gives them root access. I'm sure it'll happen one day. 

I'm not convinced that having a firewall that prevents a compromised machine calling home is a good idea. Any decent trojan would just disable the firewall and then phone home - just like many windows ones do.

---

### Post by brian_p on 2009-01-10
> **Ted_Smith said:**
> 

But it made me think. Should I? Is a Linux box likely to get infected with a Trojan? I realise it needs root privs to install itself, but what about these web page based scripts (although I use 'NoScript' with Firefox). 

Ted

Trojans don't **install themselves** on the system. The superuser is the only person who can do that. You won't.

---

### Post by slowth5 on 2009-01-10
> **brian_p said:**
> Trojans don't **install themselves** on the system. The superuser is the only person who can do that. You won't.

Don't place too much emphasis on limited user accounts, since privilege escalation attacks exist.  However, I do think limited user accounts offer more protection than a Windows machine in full administrator (malware buffet) mode.

[http://en.wikipedia.org/wiki/Linux_trojan](http://en.wikipedia.org/wiki/Linux_trojan)

---

