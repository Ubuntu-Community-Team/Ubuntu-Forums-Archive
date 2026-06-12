---
title: "Should I run Firestarter?"
date: 2009-11-22
forum: Security
---

### Post by Cytochromec on 2009-11-22
Ok, I recently tried firestart firewall "management" tool in an attempt to be more secure. However, I came across this comment in an older thread:

 " By default, all ports are closed as iptables is set-up that way.Running the GUI for Firestarter requires it to be run in root mode. Doing this is kinda like shooting yourself in the foot, as it is a grave security risk to run an application in root mode on your desktop."

Does this comment hold any weight? Im I less secure with Firestarter? What is the best approach to firewalling my first ever Linux system? Thanks mates.

---

### Post by wojox on 2009-11-22
UFW and gUFW are recommended for ip tables. 

[https://help.ubuntu.com/community/Firewall](https://help.ubuntu.com/community/Firewall)

---

### Post by Cytochromec on 2009-11-22
> **wojox said:**
> UFW and gUFW are recommended for ip tables. 

[https://help.ubuntu.com/community/Firewall](https://help.ubuntu.com/community/Firewall)


Thanks for the credit, but I dont even know what "ip tables" are. I just dont want people connecting to me all willy nilly. I also dont want programs to access the internet without my knowledge. For example, using zone alarm in windows asked you if you want to allow program x to connect to the internet - yes or no. I had gufw running and turned on the torrent client and starting coneccting to peers no problem; both dl and ul. I would have liked for it to ask me first, you know, an intrusive firewall where you white list things. 

However, if that is less secure than what meets the eye like the quote in my original post suggests, I would like to know.

---

### Post by ewan86 on 2009-11-22
I have been wondering the very same thing myself...sorry I'm no help, newbie. I kinda got the impression from reading that the firewall runs by default but I only understand 50% of what I read about ubuntu!!

---

### Post by Cytochromec on 2009-11-22
> **ewan86 said:**
> I have been wondering the very same thing myself...sorry I'm no help, newbie. I kinda got the impression from reading that the firewall runs by default but I only understand 50% of what I read about ubuntu!!

Lol, tell me about it. I also recently moved to Ubuntu. Im loving it, but I dont know jack. Either way, there is no going back. Its just a matter of time before we get the hang of things.

---

### Post by wojox on 2009-11-22
Yes all ports are closed by default. What type of services are you going to be running? Is this a Desktop or Server edition? Do you have a router?

---

### Post by wojox on 2009-11-22
> **ewan86 said:**
> I have been wondering the very same thing myself...sorry I'm no help, newbie. I kinda got the impression from reading that the firewall runs by default but I only understand 50% of what I read about ubuntu!!

The firewall ufw is installed by default. You have to enable it. Open a terminal and paste:

```
sudo ufw status
```

---

### Post by Cytochromec on 2009-11-22
> **wojox said:**
> Yes all ports are closed by default. What type of services are you going to be running? Is this a Desktop or Server edition? Do you have a router?

I am running my laptop, not a server. Its running off a wireless 24/7, so I do have a router. I dont plan on running anything fancy. I just want to be able to account for connections with understandable detail.

I have firestarter running now and every second the tray icon says "hit from  [IP] detected" ... whats that all about? The event log of blocked ips is constantly being added to.

---

### Post by Cytochromec on 2009-11-22
I am noticing that firestarter disables ufw. Is this normal? I know you cannot run two firewalls at one time, but I thought firestarter was firewall management and not an actual firewall.

---

### Post by cariboo on 2009-11-22
Firestarter is just a gui frontend for iptables. You need to uninstall one of the frontends, as wojox said ufw is installed by default.

One thing to keep in mind is that Firestarter has not been updated in about 2 years, the debian maintainer just does bug fixes.

If you are behind a router, you really don't need another firewall, the thing you have to do is make sure your wireless connection is secure, use at least wpa, if not wpa2 to encrypt the connection.

---

### Post by teward on 2009-11-22
Here's a though:  My Dell Latitude E6500 laptop uses Firestarter for the firewall.  The only port I've configured to be open is a non-standard port, and isn't linked to anything (no, i'm not telling you the port number).  Everything else has been blocked, including pings to my computer.  Anything that is not matching the connections (such as hidden connection attempts or connection attempts that were not initiated by my computer) gets blocked and logged.  The only thing not logged is the non-standard port, because its for my SSH, and I only allow my username to connect with a very strong password.

So, if you don't want to configure ufw use Firestarter.

Oh, also, all those connection attempts you're getting on Firestarter is just standard network traffic.  I'm on a college campus, and I get about 15 hits every 15 minutes, so I just disabled the notifications.  It works, though, as a firewall and every port (inbound) is stealthed, meaning invisivle as if no computer existed there (tested with online port testers).  Note I configure my computer to not respond to port requests.  :P

---

### Post by Slowspeed on 2009-11-22
> **cariboo907 said:**
> Firestarter is just a gui frontend for iptables. You need to uninstall one of the frontends, as wojox said ufw is installed by default.

One thing to keep in mind is that Firestarter has not been updated in about 2 years, the debian maintainer just does bug fixes.

If you are behind a router, you really don't need another firewall, the thing you have to do is make sure your wireless connection is secure, use at least wpa, if not wpa2 to encrypt the connection.

I concur with cariboo907. Use the wireless encryption as described above and additionally you can turn off essid broadcasting.

---

### Post by ewan86 on 2009-11-24
> **Cytochromec said:**
> Lol, tell me about it. I also recently moved to Ubuntu. Im loving it, but I dont know jack. Either way, there is no going back. Its just a matter of time before we get the hang of things.

Same, I'm learning more everyday...when I think back though you have to get the hang of windows and there is more people to help so well pleased.

Thanks for the advice everyone, I am behind a router so I should be ok then, but I now know how to enable it if I ever do :)

---

### Post by ptn107 on 2009-11-24
```
sudo ufw enable && sudo ufw default deny
```

and your done.

---

### Post by Cytochromec on 2009-11-24
I did not know Firestarter was discontinued. I followed the advice here; running gufw in combination with hardware firewall; feel safe enough.

---

