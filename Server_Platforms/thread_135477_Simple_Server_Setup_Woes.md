---
title: "Simple? Server Setup Woes"
date: 2006-02-23
forum: Server Platforms
---

### Post by Jedeye on 2006-02-23
Im having a little trouble. I have searched around for a few hours but to no avail.. it just doesn't seem to work for me. I set up apache and it seems to be working fine. I go to [http://localhost](http://localhost) and its good. But all I want to do is set it up so I can have a another person(not on my network) connect to it by punching in the ip address. I don't care about any special security as I only run it briefly and host nothing of importance. I am hooked into a router so I think that may be causing some trouble but think that there should still be a workaround. Im really at a loss. I know the dsl server package I have includes a static ip address but I do not know what it is(can I look it up on my comp or do I need to call them)

Well that is where I am. Any info would be greatly appreciated!

---

### Post by heimo on 2006-02-23
Is your computers ip address something like 192.168.x.x or 10.x.x.x? (run ifconfig) Then check what's your external ip address (disable proxy if you're using one) by going to [http://www.whatismyip.com/](http://www.whatismyip.com/)

If you have access to your router - so that you can change it's settings, find its manual and look for port forwarding. You want to change your computers ip to fixed if it's using DHCP now, so that port forwarding can work. Forward 80 port from your external ip to your computers ip. Enter your external ip to browser and check that it works.

---

### Post by VinceDee on 2006-02-24
Here, try this out: 

[http://www.ubuntuwebservers.com/?q=node/46](http://www.ubuntuwebservers.com/?q=node/46)

Hope that helps,

Vince

---

### Post by herrpoon on 2006-02-24
[QUOTE=heimo]Is your computers ip address something like 192.168.x.x or 10.x.x.x? (run ifconfig) Then check what's your external ip address (disable proxy if you're using one) by going to [http://www.whatismyip.com/](http://www.whatismyip.com/)

If you have access to your router - so that you can change it's settings, find its manual and look for port forwarding. You want to change your computers ip to fixed if it's using DHCP now, so that port forwarding can work. Forward 80 port from your external ip to your computers ip. Enter your external ip to browser and check that it works.[/QUOTE]

Depending on the router you have, the bottom bit may or may not work.  If it doesn't and you are sure you've forwarded the ports correctly etc., get someone outside of your network to try before pulling any hair out!

---

### Post by jinacio on 2006-02-24
If you have any trouble setting up your router to forward port 80, check [this site ]("http://www.portforward.com/english/applications/port_forwarding/HTTP/HTTPindex.htm")
(it has howto's for setting up for forwaring on may routers/ports)

cheers

---

### Post by Jedeye on 2006-02-26
thanks for the tips guys! I now have it up and running :D

---

