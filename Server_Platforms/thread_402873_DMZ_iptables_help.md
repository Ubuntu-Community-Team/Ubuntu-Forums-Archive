---
title: "DMZ iptables help"
date: 2007-04-06
forum: Server Platforms
---

### Post by reckless2k2 on 2007-04-06
I currently have a server on my DMZ running mail & ftp services. I've got a NAS inside my LAN that I want to rsync for backup and information sharing purposes (samba). I need to know how in my iptables on my server on the DMZ that I can open the ports ONLY to that NAS on my LAN. I don't want these ports open to everyone to see. 

example:

server on DMZ - 192.168.10.100
NAS on LAN - 192.168.100.50

I'm only concerned about the server on the DMZ iptables. 

Is this the right syntax?

iptables -A INPUT -s 192.168.100.50 -p tcp --dport 137:139 -j ACCEPT

Thanks for any help.

---

### Post by reckless2k2 on 2007-04-06
Any ideas? I figure this to be a simple one for an iptables person.

---

### Post by reckless2k2 on 2007-04-08
Well judging by some searching, that syntax should have worked but it does not. I'm trying to use smb4k to mount from DMZ to LAN and I keep getting port 139 error despite 139 being open.

---

### Post by zarg@henrikke on 2007-04-10
> **reckless2k2 said:**
> 

server on DMZ - 192.168.10.100
NAS on LAN - 192.168.100.50

I'm only concerned about the server on the DMZ iptables. 

Is this the right syntax?

iptables -A INPUT -s 192.168.100.50 -p tcp --dport 137:139 -j ACCEPT

Thanks for any help.

If I wanted to only allow inbound TCP traffic on ports 137, 138, 139 from 192.168.100.50:

[FONT="Courier New"]
iptables -P INPUT DROP
iptables -A INPUT -p tcp -s 192.168.100.50 --dport 137 -j ACCEPT
iptables -A INPUT -p tcp -s 192.168.100.50 --dport 138 -j ACCEPT
iptables -A INPUT -p tcp -s 192.168.100.50 --dport 139 -j ACCEPT
[/FONT]

---

### Post by reckless2k2 on 2007-04-15
That's basically the same syntax i wrote above and used without success.

---

