---
title: "Honeypots"
date: 2010-08-12
forum: Security
---

### Post by rkasparek on 2010-08-12
Starting to have Denial of Service attacks on our internal network protected by a Netgear wireless router. We have turned off the IP ping response as well as port forwarding. It has been suggested to me that we take one of our old computers and set it up as a honeypot to capture the intruder's efforts.

Does anyone have any experience with setting these up and is there a good software anyone can recommend?

---

### Post by DrMelon on 2010-08-12
Well, it's important to give the honeypot some weak spots, to engage the interest of your attacker. Some kind of logging software to monitor usage would be useful. Include some false data in there as well, some gibberish marked "password hashes" or something.

---

### Post by rkasparek on 2010-08-12
Thanks... any ideas on how to set it up? Keep in mind - I am a newbie with Ubuntu. The only thing I have messed with is Ubuntu desktop.

---

### Post by Rubi1200 on 2010-08-12
I have no experience with this, but have found some links for you that I hope will make for interesting reading and perhaps some ideas on how to proceed:

[http://manpages.ubuntu.com/manpages/hardy/man8/thpot.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/thpot.8.html)

[http://kojoney.sourceforge.net/](http://kojoney.sourceforge.net/)

[http://manpages.ubuntu.com/manpages/dapper/man8/honeyd.8.html](http://manpages.ubuntu.com/manpages/dapper/man8/honeyd.8.html)

[http://en.wikipedia.org/wiki/Honeypot_%28computing%29](http://en.wikipedia.org/wiki/Honeypot_%28computing%29)

---

### Post by wacky_sung on 2010-08-12
> **rkasparek said:**
> Starting to have Denial of Service attacks on our internal network protected by a Netgear wireless router. We have turned off the IP ping response as well as port forwarding. It has been suggested to me that we take one of our old computers and set it up as a honeypot to capture the intruder's efforts.

Does anyone have any experience with setting these up and is there a good software anyone can recommend?

If you think it is a DDOS attack and why must you waste your time on honeypot?

The purpose of DDOS attack is jammed up your traffic making it impossible for you to use it.

The use of honeypot is created an environment for malicious hack break in and gather information of their hack prior using it in court as evidence for their act.

You shall use your old pc act as a firewall gateway to filter out the attack.Below have a lot of option for you to choose.

[http://www.clearfoundation.com/Software/overview.html](http://www.clearfoundation.com/Software/overview.html)
[http://sourceforge.net/apps/trac/ipcop/wiki](http://sourceforge.net/apps/trac/ipcop/wiki)
[http://www.ebox-platform.com/](http://www.ebox-platform.com/)
[http://m0n0.ch/wall/](http://m0n0.ch/wall/)
[http://www.pfsense.org/](http://www.pfsense.org/)
[http://www.smoothwall.org/](http://www.smoothwall.org/)
[http://www.smoothwall.net/](http://www.smoothwall.net/)

---

### Post by rkasparek on 2010-08-12
Thanks Wacky... I was simply told by a network engineer that a honeypot would work. Heck I'm new to this so I'm just taking suggestions - thanks for yours!

Has anyone had any experience using ebox as a firewall?

---

### Post by OpSecShellshock on 2010-08-12
What's led you to the conclusion that these were denial of service attacks rather than either unauthorized access attempts or false positives? If evidence suggests it was a denial of service attack, did it succeed in causing your devices and operations to stop functioning?

---

### Post by bodhi.zazen on 2010-08-12
I would echo some of the sentiments on this thread.

I do not believe a honeypot is the tool for the task at hand.

I would start by looking at your network traffic, ntop, logs, wireshark, tcpdump, etc.

If in doubt I would use psad, fwsnort, snort, ossec, or other similar tools.

IMO honeypots are more for studying the enemy, you put up a vulnerable system, allow it to be cracked, and see what happens. You need to take care that your intruder is contained in the honeypot, however ...

If it is a DOS attack, a honeypot is overkill. In addition, what makes you think the honey pot will specifically targeted.

Better question for you -  how would you analyze the honeypot ? Take those analysis tools and apply them to your server.

---

### Post by rollin on 2010-08-12
Thread title caught my eye as I attempted to run one of these on Windows systems and it was a bit of a waste of time unfortunately.

As another suggestion to the excellent tools recommended in the above posts you mention an internal network, is there some kind of authentication access to this? They may be attempting to brute force the password  which could have the same effect. 

If this sounds possible a tool like fail2ban could work well as it checks /var/log/pwdfail or /var/log/apache/error_log (copied from webpage)and bans IPs that generate a set number of failed password attempts. 

Here's a link with more info: [http://www.fail2ban.org/wiki/index.php/Main_Page](http://www.fail2ban.org/wiki/index.php/Main_Page)

---

### Post by lisati on 2010-08-12
One thing to do is to see if the "attacks" are coming from within the network from a machine that would normally have legitimate access to the network, and eliminate the possibility that it has caught something nasty.

---

### Post by rkasparek on 2010-08-13
Thanks for the insights! At the moment we're setting up a machine to act as a firewall. We're trying eBox. We have visited each machine and have run several anti virus programs on each machine. We don't have an authentication for our network at the moment - it was originally a T1 and router with a few computers on it - it has grown considerably since then.

---

