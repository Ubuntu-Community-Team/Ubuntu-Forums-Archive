---
title: "Do I need a Firewall?"
date: 2011-03-03
forum: Security
---

### Post by Rasputin69 on 2011-03-03
Newbie.

Do I need a firewall and if so what do you recommend?

---

### Post by Irihapeti on 2011-03-03
There's a firewall already built into Ubuntu but it's not activated.

If you are just a desktop user, and especially if your machine is behind a router, you probably don't need it.

I have it activated on my netbook, because I can't be sure what kind of security is in use at coffee shops, libraries and so on.

You can activate the preinstalled firewall from the command line

```
sudo ufw enable 
```

If you prefer the gui method, install gufw from the repos. It's a front end for ufw.

If you start installing or activating services accessible from the internet e.g. SSH server, web server, then you definitely need something. Reading the [Ubuntu Security sticky]("http://ubuntuforums.org/showthread.php?t=510812") is a good place to start. It's worth reading anyway.

I've been on the forums for about 3 1/2 years. Nearly all the intrusion problems I've seen seem to result from people activating remote desktop or not setting SSH or other server up properly.

---

### Post by nrundy on 2011-03-04
If you want a GUI to the firewall you can install GUFW, Rasputin69 :)

---

### Post by handy on 2011-03-04
Unless you are serving Windows machines, you can forget about a firewall. The way Ubuntu installs it has no open public ports.

You need no anti-virus either.

Using non-Windows systems is vastly more secure. If you stay with the Linux/BSD (& others) systems, you will learn as time goes by, that it is MS that does things in an insecure manner high maintenance manner.

---

### Post by rookcifer on 2011-03-04
You don't need a firewall with the default install.  However, I recommend you turn on UFW if you plan on enabling any services like SSH or Samba, etc.

---

### Post by inobe on 2011-03-04
i insist you use a firewall, at least this way you can become familiar with one 'if so.

you can manipulate rules by use of commands, or a graphical user interface "GUI"

ufw [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

gufw [https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw)

the thing about firewalls, you can limit types of connections inbound or outbound, you can also screw things up if you aren't sure what it is that are you doing.

---

### Post by handy on 2011-03-05
> **inobe said:**
> i insist you use a firewall, at least this way you can become familiar with one 'if so. 

What sense does that argument make?

Apply it to everything that you don't know about in life, but may or may not find useful sometime before you die.

---

### Post by inobe on 2011-03-05
> **handy said:**
> What sense does that argument make?

Apply it to everything that you don't know about in life, but may or may not find useful sometime before you die.

i felt the same way till i realized of all the great things i could do with networking/ servers and beyond!

by default all ports are closed until opened, do you think new users install server programs by accident, it happens all the time, now we have open ports ;) 

do you think a majority of users only browse the web and check email, do you think it would be nice to understand a firewall before meddling with servers?

---

### Post by handy on 2011-03-05
I don't agree with what you say inobe, but I'm not going to press it. :)

---

### Post by inobe on 2011-03-05
> **handy said:**
> I don't agree with what you say inobe, but I'm not going to press it. :)

maybe i might learn something, bring it :)

---

### Post by wdtd on 2011-03-14
```
sudo ufw enable
sudo ufw default deny
``` is easy and safe, I think.  (Remember this is incoming connections.) You can look at installing GUFW if you want a pretty GUI to use with UFW and its IPtables.

Why? As far as I can tell, you have nothing to lose and if you do install something that turns on a service, you have additional protection. And don't forget to review the great Ubuntu stickies on this forum to help as well.

---

### Post by Rasputin69 on 2011-03-14
> **wdtd said:**
> ```
sudo ufw enable
sudo ufw default deny
``` is easy and safe, I think.  (Remember this is incoming connections.) You can look at installing GUFW if you want a pretty GUI to use with UFW and its IPtables.

Why? As far as I can tell, you have nothing to lose and if you do install something that turns on a service, you have additional protection. And don't forget to review the great Ubuntu stickies on this forum to help as well.

Thanks. I consider it solved and have so marked it.

---

### Post by nec207 on 2011-03-14
[QUOTE] 
> **Irihapeti said:**
> There's a firewall already built into Ubuntu but it's not activated.
 
If you are just a desktop user, and especially if your machine is behind a router, you probably don't need it.

 
A good firewall keeps log of all port scanning and any other IP address trying to get in and well Ubuntu firewall or router firewall cannot do this.
 
 
zone-alarm blocks all out going traffic even IE you have to say yap IE or word can connect to the internet in zone-alarm.
 
You cannot do this with Ubuntu firewall or router firewall .
 
Also get program that looks at the packets coming in and out I mean really looking at the packets .

---

### Post by bodhi.zazen on 2011-03-14
> **nec207 said:**
> [QUOTE] Ubuntu firewall or router firewall cannot do this.

Can not do what ? logs ?

iptables and ufw and gufw all keep logs, it would be up to you to analyze them.

I have not seen a router that does not keep logs.

Sounds as if you do not know how to configure iptables / ufw or your router, I am not sure.

---

### Post by nec207 on 2011-03-14
> **bodhi.zazen said:**
> [QUOTE=nec207;10560100]
 
Can not do what ? logs ?
 
iptables and ufw and gufw all keep logs, it would be up to you to analyze them.
 
I have not seen a router that does not keep logs.
 
Sounds as if you do not know how to configure iptables / ufw or your router, I am not sure.
 
I don't what to log into the router all the type to look at the logs and the router will not show port scanning or more advance log.
 
I want real time monitoring.If there is port scanning now or some IP address try to connect to my computer** I want** a pop up ASAP that is now not were by **I have check** the routers setting to look at the log later.

---

### Post by bodhi.zazen on 2011-03-14
> **nec207 said:**
> [QUOTE=bodhi.zazen;10560322]
 
I don't what to log into the router all the type to look at the logs and the router will not show port scanning or more advance log.
 
I want real time monitoring.If there is port scanning now or some IP address try to connect to my computer** I want** a pop up ASAP that is now not were by **I have check** the routers setting to look at the log later.[/quote]

Well, that is very different from your claim.

If you want "real time monitoring" , I highly suggest snort. You can configure the alerts any way you wish and it saves you from looking at all the normal traffic.

---

### Post by nec207 on 2011-03-14
> **bodhi.zazen said:**
> Well, that is very different from your claim.
 
If you want "real time monitoring" , I highly suggest snort. You can configure the alerts any way you wish and it saves you from looking at all the normal traffic.
 
Can you elaborate here.

---

### Post by bodhi.zazen on 2011-03-15
> **nec207 said:**
> Can you elaborate here.

What do you want to know about snort ?

Snort is a NIDS and it uses a rule set to alert you to potential threats / malicious activity.

So rather then reviewing (potentially) hundreds of thousands of events, most of which will be false positives, you can review say 10 events, most of which will still be false positives mind you, but 2 may be actual problems.

You can also use OSSEC which has an active response mechanism.

See the security stickies.

[http://ubuntuforums.org/showthread.php?t=1477696](http://ubuntuforums.org/showthread.php?t=1477696)

[http://ubuntuforums.org/showthread.php?t=1477662](http://ubuntuforums.org/showthread.php?t=1477662)

---

### Post by nec207 on 2011-03-16
Or you can just use zone-alarm and problem solved.
 
It is good enough and forget about snort unless you live in ghetto where everyone is hacking.

---

### Post by Rasputin69 on 2011-03-16
> **nec207 said:**
> Or you can just use zone-alarm and problem solved.
 
It is good enough and forget about snort unless you live in ghetto where everyone is hacking.

Zone Alarm says it's for Windows.

---

### Post by nec207 on 2011-03-16
> **Rasputin69 said:**
> Zone Alarm says it's for Windows.
 
I'm sure there has to be Zone- Alarm version for non windows if not than bad on the company .
 
 
If not I'm sure there are other out there.

---

### Post by Rasputin69 on 2011-03-16
> **nec207 said:**
> I'm sure there has to be Zone- Alarm version for non windows if not than bad on the company .
 
 
If not I'm sure there are other out there.

Zone Alarm
[http://www.zonealarm.com/security/en-us/zonealarm-pc-security-free-firewall.htm](http://www.zonealarm.com/security/en-us/zonealarm-pc-security-free-firewall.htm)

"Compatible with Windows 7, Windows Vista and Windows XP"

---

