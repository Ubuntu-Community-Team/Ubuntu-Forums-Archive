---
title: "None windows computers need firewall and anti-virus program"
date: 2011-02-28
forum: Security
---

### Post by nec207 on 2011-02-28
I tried to ask this question in the other thread but the admin was saying to me that my other thread here [http://ubuntuforums.org/showthread.php?t=1692041](http://ubuntuforums.org/showthread.php?t=1692041) ( it was not very much the subject of the thread )
 
People that use Unix,Mac OSX or any Linux OS all none windows do you need anti-virus program like Norton or Kaspersky? And same with firewall like ZoneAlarm and Comodo ?
 
Some people say you do not need a anti-virus program like Norton or Kaspersky or any firewall.Other people say you do and some say that Unix and Mac OSX have built in firewall.
 
And if on uses windows use ZoneAlarm or Comodo has it does alot more than windows firewall and router firewall.
 
Note the admin saying the other thread was why _windows get more malware_ and not very much the subject of the thread to post there.

---

### Post by ppv on 2011-02-28
There are both anti-virus as well as firewall programs for Linux.

Most linux distributions do not come with a firewall preinstalled

Infact newer versions of Windows do have a firewall built into it. And yes that firewall is only a basic firewall.

And if you require an antivirus and a firewall for linux, it depends on your requirement, but you may need a firewall more than the antivirus.

---

### Post by sammiev on 2011-02-28
It really depends on your surfing habits. I transfer files between different OS and have never found a virus to date with Lunix. With the firewall, it usually well covered within Lunix. Try running a test with [GRC]("https://www.grc.com/x/ne.dll?bh0bkyd2") to see if all ports are closed. GL :)

---

### Post by cariboo on 2011-02-28
> **ppv said:**
> There are both anti-virus as well as firewall programs for Linux.

Most linux distributions do not come with a firewall preinstalled

Infact newer versions of Windows do have a firewall built into it. And yes that firewall is only a basic firewall.

And if you require an antivirus and a firewall for linux, it depends on your requirement, but you may need a firewall more than the antivirus.

All modern Linux distributions come with a firewall installed, in most cases it isn't activated.

---

### Post by d3nn on 2011-02-28
If you are connected to the internet through a router you probably don't need to worry about firewalls. Also if you're paranoid about viruses then it isn't a bad idea to get anti-virus programs, but like others have said, there are very few linux viruses.

---

### Post by HermanAB on 2011-02-28
Howdy,

Linux pretty much *is* a firewall.  The reason why Ubuntu ships without explicit firewall rules configured, is because the default network stack is strong enough as is.  Many of the rules that you will see in old firewall scripts protect against things that are no longer an issue in the Linux network stack.

So where does it leave a common user?  If you use Windows, put a dinky little Linux based home router by Netgear or Linksys under your desk and run the Windows machine through it.  If you are using a Linux machine - then you don't need to bother.

---

### Post by nec207 on 2011-03-01
> **HermanAB said:**
> Howdy,
 
Linux pretty much *is* a firewall. The reason why Ubuntu ships without explicit firewall rules configured, is because the default network stack is strong enough as is. Many of the rules that you will see in old firewall scripts protect against things that are no longer an issue in the Linux network stack.
 
So where does it leave a common user? If you use Windows, put a dinky little Linux based home router by Netgear or Linksys under your desk and run the Windows machine through it. If you are using a Linux machine - then you don't need to bother.
 
 
sorry what do you mean?
 
With zone-alarm it stops any thing coming in or any thing going out that I do not click on saying allow.If you tried to hack my computer zone-alarm will log you and show your IP address .If you install malware on my computer and 2 times a week that program goes on the net to report it show up in my log.
 
With zone-alarm I can even block IE or lock all network communication.And yes I use to do this when not using my computer.
 
But I have not put zone-alarm on this new computer yet.

---

### Post by CandidMan on 2011-03-01
I'm not sure you can get zone-alarm for linux. Besides you have iptables. Although it's awkward to configure at first can do everything you just mentioned
I found these articles particularly helpful
[http://librenix.com/?inode=21](http://librenix.com/?inode=21)
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)
[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)
This one's long, sorry:
[http://linuxmafia.com/~rick/faq/index.php?page=virus](http://linuxmafia.com/~rick/faq/index.php?page=virus)

---

### Post by nec207 on 2011-03-01
I thought may be you can get a firewall for it.
 
Some firewalls are better than others.

---

### Post by CandidMan on 2011-03-01
Yeah, I'd personally like something like COMODO(not intended to be a plug :))

I swear I learnt more about computer security from those help files than anyhting that came with my comp

If you don't have any running services  then no-one can initiate and maintain a connection to your PC. So it's up to you to go looking for trouble with your web browser/torrents/messenger etc

---

