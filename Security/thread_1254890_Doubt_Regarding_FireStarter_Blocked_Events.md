---
title: "Doubt Regarding FireStarter Blocked Events"
date: 2009-08-31
forum: Security
---

### Post by chandru155 on 2009-08-31
I was downloading using Ktorrent. I added the policy rule in FireStarter(Inbound policy Rule). Firestarter some times shows Red Alert. Does any one trying to hack my computer or is that normal since i am using Ktorrent(with port opened)?

---

### Post by lovinglinux on 2009-08-31
That's normal, since you are using a torrent client. Probably it's udp or ping connections related to the torrent download.

BTW, you don't need to run Firestarter all the time. Once you configure Firestarter rules, you can close it, because it simply creates rules for the real firewall (iptables), which runs in the background. Besides, you shouldn't run it all the time, because it requires root privileges. If an attacker gets control over it, it will have root privileges over your machine. There are reports of bugs in Firestarter that could allow that.

The recommended firewall manager nowadays is gufw, which is the graphical interface for ufw (Uncomplicated Firewall).

---

### Post by chandru155 on 2009-09-01
I closed torrent client. Restarted both my Modem and System. After that also FireStarted blocked some continuous IPs.(For every 10 Sec, I didnt run any program and also not installed any server or anything other than Normal Ubuntu Daily Update). So i though someone is trying to hack my system and i now freshley installed Ubuntu. Now that problem is over. And with Gufw, i couldnt do port forward. I added the port no for TCP and UDP, but the port doesnt open.                                                                                          Another Question, should i exit FireStarter after applying the Rule(to allow Port)?

---

### Post by lovinglinux on 2009-09-01
> **chandru155 said:**
> I closed torrent client. Restarted both my Modem and System. After that also FireStarted blocked some continuous IPs.(For every 10 Sec, I didnt run any program and also not installed any server or anything other than Normal Ubuntu Daily Update). So i though someone is trying to hack my system and i now freshley installed Ubuntu.

You have just wasted time and effort. That's also completely normal. When you run a torrent client it connects to a tracker to get the list of IPs of other peers sharing the same file. It also adds your IP to the list, so other peers can connect to you. When you close your torrent client, the other peers will keep trying to connect to you for a while, as long as the tracker has your IP listed. Some trackers update their IP list more often than others. These attempts are known as "ghost packets" and they are harmless, because your torrent client is not listening to the port anymore. So it is closed. Besides, those connections were blocked anyway, so there is nothing to worry about. If you want them to stop, all you have to do is restart your modem to get a new IP. Considering that your ISP provides you with a dynamic IP, which is the most common practice.

**When I restart the modem and get a new IP, while I still get connections attempts?**

You get connection attempts most likely because the previous user of your "new" IP was doing something like torrenting before you. The ISP does not have a single IP for each costumer. They can do that because most of the costumers won't be connected at the same time. So, when you restart your modem you get e "new" IP which is not actually new. It was previously used by someone else that disconnected just before you or a few minutes/hours before. If you get an IP that was just released by someone else that was using a torrent client, then you get his ghost packets.

Additionally, keep in mind that if you are not running a server, you don't even need a firewall. Seriously! Let's say you don't have a firewall and all ports are opened in the router. So anyone can reach you. Then you start to get hundreds of connections attempts on a specific port. Can they hack you? No. If you are nor running any server, there isn't any program listening to any port, so there is no way to a remote computer to establish a connection with yours. It's the same as having all ports closed.

Unlike windows, Ubuntu comes with no servers active by default.

**Is the torrent client a server? **

Yes! The torrent client is a server, because it has the ability to listen to a port and thus accept remote connection requests.

**Do I need a firewall to protect my network while using a torrent client?**

No. Because you want to let people connect to your torrent client, otherwise your download speed will suffer. So if you use a firewall, but open the port for the torrent client, is the same as not using a firewall, because the torrent client is the only application accepting remote connections. If you are using a firewall to block other ports, then you are blocking ports that are already closed, which is redundant.

**Opening the port in the firewall or not using a firewall while torrenting offers the same risk?**

Yes. Nevertheless, the risk is directly proportional to the server software security. So, if you are using an updated torrent client, the only risk of being hacked is if a hacker knows a security flaw in the torrent client that hasn't been discovered or fixed yet.

**When a firewall is useful?**

A firewall is useful for example if you run a ssh or samba server on your machine to allow someone else in your house to download files from your machine. In this situation, there is no need to let external machines on the internet to reach your ssh or samba port, which would be a security risk. So a firewall would allow you to accept connections only from computers on your local network, while blocking everyone else.

This is clearly not the case, because you don't have any other server running, just the torrent client and thus you need to let other machines on the Internet to reach your torrrent port. So basically, the firewall is useless for your situation.

**So what can you do to protect your machine while torrenting?**

Keep your torrent client and Ubuntu updated.

You can also use an IP blocker which is included in most torrent clients, to prevent bad known IPs to connect to you, while still retaining the ability to connect to other peers. For increased security, I recommend using a standalone ip blocker like [moblock](http://moblock-deb.sourceforge.net/) or [iplist](http://iplist.sourceforge.net/), because they protect your entire network, not just the torrent connection.

If you want to learn something cool and protect your machine even more, you can use [Apparmor](http://ubuntuforums.org/showthread.php?t=1008906), to limit what your torrent client can do on your system. So if a hacker discovers some security hole in the client, it won't be able to hack your machine, due to limited permissions given to the torrent client by Apparmor.

> **chandru155 said:**
> Another Question, should i exit FireStarter after applying the Rule(to allow Port)?

Yes. Keeping it open is a security risk, because an attacker could hack Firestarter and gain root access to your machine, since Firestarter needs root privileges to run.

I strongly recommend that you read the [Ubuntu Security](http://ubuntuforums.org/showthread.php?t=765421) tutorial, so you can understand what are the real threats.

It is common to be a little bit paranoid when coming from Windows, because that OS is full of security flaws in the default installation, lots of listening services, programs that phone home without your knowledge, viruses that connect to download more malware and other stuff. I would never run a Windows machine without a firewall even if I'm just updating it from Microsoft Update page after a fresh install. Well I have already been hacked doing exactly that :) But since I switched to Linux a year ago, I have been reducing my paranoia and learning how to make my system secure the correct way. Well I still use a firewall just because I can, but I fully understand what it can and cannot do to protect me.

---

### Post by bodhi.zazen on 2009-09-01
The fastest road to paranoia is to connect to the internet and start tracking your traffic.

Now that you have tasted paranoia, learn how to track and defend against this activity. The key to security is to properly configure and server(s) you may run, blocking traffic with a firewall is secondary.

---

### Post by chandru155 on 2009-09-02
Thanks.
(Specially [lovinglinux]("http://ubuntuforums.org/member.php?u=649167"))

---

### Post by Chasey on 2010-12-18
If fireStarter can get hacked wouldn't that be true for any software with a connection outside?

---

### Post by bodhi.zazen on 2010-12-18
> **Chasey said:**
> If fireStarter can get hacked wouldn't that be true for any software with a connection outside?

Yes, this is true of all applications and the kernel.

Because of this we use tools such as apparmor or selinux or similar to "watch" and confine network aware applications.

---

