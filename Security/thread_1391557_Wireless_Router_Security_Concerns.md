---
title: "Wireless Router Security Concerns"
date: 2010-01-26
forum: Security
---

### Post by b1lancer on 2010-01-26
Hello All!

Today, one of my laptops was infected with a bad case of spyware... naturally, it was running M$ XP. I started it in Safe mode with networking and accessed my wireless internet router to download tools to help with the situation. Eventually, I ended up using Ubuntu to backup my files and doing a clean install.

My concern is this: while I know Ubuntu is not prone to spyware/malware/viruses, could my wireless router have been affected? I do still need to access it using M$ XP computers every now and then. What say the experts??

Thanks!

---

### Post by pirateghost on 2010-01-26
> **b1lancer said:**
> Hello All!

Today, one of my laptops was infected with a bad case of spyware... naturally, it was running M$ XP. I started it in Safe mode with networking and accessed my wireless internet router to download tools to help with the situation. Eventually, I ended up using Ubuntu to backup my files and doing a clean install.

My concern is this: while I know Ubuntu is not prone to spyware/malware/viruses, could my wireless router have been affected? I do still need to access it using M$ XP computers every now and then. What say the experts??

Thanks!
there is little to no chance that it affected your router, your router doesnt run windows :)

---

### Post by adam814 on 2010-01-26
+1

Two reasons I'll bet your router is fine:

1)  Most internally run embedded Linux 2.4.
2)  You can't write to anything important on the router without flashing the firmware.  On mine you can write to /tmp (if you've hacked it to allow telnet access), so in theory you could put trojan executables there and run them, but it wouldn't survive a power cycle.

---

### Post by Agent ME on 2010-01-27
The only cases I've ever heard of hacked routers had to do with a worm that propagated through routers flashed with a 3rd party firmware (thinking OpenWRT or DD-WRT) which had been left with the default password and set to be remotely accessible by people on the internet, instead of just by people on the LAN.

If you haven't put a 3rd party firmware on your router yourself, then you more than likely don't need to worry.

---

### Post by b1lancer on 2010-01-27
Ok! Thanks for the reassurance. Yeah, I haven't installed any third party firmware. And I also disconnected the power and turned it back on, as with my dsl.

Do Belkin routers run on Linux? Just curious.

I do have to set a password because I've left it with the default one. Is there a thread someone can point me to that addresses wireless network security?

Thanks again for the responses.

---

### Post by rookcifer on 2010-01-27
> **b1lancer said:**
> Ok! Thanks for the reassurance. Yeah, I haven't installed any third party firmware. And I also disconnected the power and turned it back on, as with my dsl.

Do Belkin routers run on Linux? Just curious.

I do have to set a password because I've left it with the default one. Is there a thread someone can point me to that addresses wireless network security?

Thanks again for the responses.

There's really nothing to it other than making sure you have set an authentication password.  You should use WPA2/PSK if your router allows it, and you should use as long of a password as possible.  I recommend generating a random one of 63 characters.

And I recommend flashing your router with Tomato (or DD-WRT) if your router allows it.

---

### Post by jlb.think on 2010-01-28
use WPA2 as mentioned, if you can only use WEP, then your router is old enough it needs upgraded anyways.  In college I actually cracked the WEP to the teachers network to get faster internet access than the student wi-fi, the greedy bastards wanted all the speed to themselves!

They did their best to slow p2p traffic on the student side, where as I could get 10 mbps a second on bittorrent on the teacher's network until I encrypted all my bittorrent traffic and their network monitors thought it was a viruss.  I was a little scared when all the IT staff started running around trying to figure out what was going on and they shut down their whole network for a day trying to find which one of their computers had a virus.  They were convinced that somebody had rooted one of their machines and was using it as a command and control server for a botnet or something.  Us IT students laughed about it for a long time, but I never gave the key to anyone else because I couldn't trust them to shut it off and not get in trouble.

Back to the subject at hand:  If you don't want your router hacked make sure the configuration interface is only open to a physical connection.   Most routers are set by default to not allow configuration over wireless, but many people change this for convenience, dont.  Also use good passwords.  I've been in more than one place without an internet connection to see "Mary's Internet" and use their connection by typing "Internet" or "Mary" for a password.

Lastly configure the firewall in your router.  I know everyone wants to configure it on the individual machines, but you should close every single port but the ones you use, and if you use VNC or SSH only on the in network, but don't punch in from the outside, block these ports from outside access.  Don't think I mean you shouldn't configure your firewall on your machines, it just that an extra layer of protection is always good, it reduces your chances of problems if you carlessly forget to close something on your machines since Windows sets all kinds of ports to open by default.

---

