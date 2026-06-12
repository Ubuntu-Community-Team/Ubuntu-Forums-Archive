---
title: "DenyHosts blocks all SSH connections immediately"
date: 2013-08-20
forum: Server Platforms
---

### Post by tr3 on 2013-08-20
Hi
I am trying to configure denyhosts on Ubuntu Server 12.04.2 LTS.

I have SSH configured as default except for a different port.

I've installed denyhosts and left its configuration as the default.

When I try to SSH into the server, denyhosts immediately adds my IP address to /etc/hosts.deny and closes the connection. It doesn't even give me an opportunity to give my login details before banning me.

I've checked the default config and it appears like I should have 5 failed login attempts before being banned, but it bans me immediately before I've even had a chance at a login attempt.

Does anyone know what might be wrong?

Thanks

---

### Post by alarme on 2013-08-20
Hi.

Take a look at  [http://www.linuxquestions.org/questions/linux-security-4/problem-with-denyhost-when-changing-ssh-port-22-a-841434/](http://www.linuxquestions.org/questions/linux-security-4/problem-with-denyhost-when-changing-ssh-port-22-a-841434/)

Cheers

---

### Post by TheFu on 2013-08-20
If you can, check out the log files on the server and increase the verbosity on the ssh command.  I find it most helpful to **tail -f** the server logs, add some spaced to my screen, then kick off the ssh from a remote box.

BTW, if denyhosts doesn't work for you (for whatever reason), another option is Fail2Ban. It handles ssh out of the box on the default port.  I like to use the router for port translation 55000 for inbound ssh translates to 22 on the specific server. Inside the LAN, all ssh is on default ports. This also lets me easily know for certain which method WAN or LAN that I'm using to ssh through.  I think both are fantastic tools, so this is NOT a slam at all.

---

