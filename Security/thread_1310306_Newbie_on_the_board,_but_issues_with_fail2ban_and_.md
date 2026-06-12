---
title: "Newbie on the board, but issues with fail2ban and SSH"
date: 2009-11-01
forum: Security
---

### Post by woodside100 on 2009-11-01
No, isn't the standard chroot or the typical stuff and I'm using 8.4 of fail2ban and 9.4 Ubuntu.

I have a home network which is forwarding port 80 to a putty machine which then connects back to a Ubuntu server on SSH:22.  So, Internet router forwards port 80 to a client putty machine tunnel which then forwards port 22 to my SSH server.  All works, not the issue.

Problem is that since L22 is forwarded to my SSH:22, the Ubuntu SSH only sees its own IP for incoming, so fail2ban bans the servers own IP......so bans everything going through the putty client.  Not working.

I need to allow fail2ban to see the actual IP of the offending machine, or something else that will fix this.  The reason I am using the putty client to get to SSH is due to a limitation on the Linksys router I'm using, which will only allow forwarding to connected subnets (had no clue when I bought it) and you can't use a hacked firmware on it.......not supported.

Internet>Router:xxx.0:80>80:puttyc:22>yyy.0>SSHServer:22=fail2ban fail

Any help figuring a method of getting Fail2ban to work would be greatly appreciated.

---

