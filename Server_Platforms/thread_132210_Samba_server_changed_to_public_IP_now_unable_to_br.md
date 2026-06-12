---
title: "Samba server changed to public IP now unable to browse"
date: 2006-02-17
forum: Server Platforms
---

### Post by rmarkin on 2006-02-17
Hello,

I am running Ubuntu Breezy as a Postfix and Samba (3.014) server.  

Original setup:
DSL with one dynamic IP that was obtained by router using PPPOE.
Three XP machines access samba shares by //Ubuntu/share with no problems.  IP for server was statically set to 192.168.2.200.  XP machines obtained IP's from router by DHCP starting at 192.168.2.100 and up.  Worked great.

Current setup:
DSL with five static IP's one of which is assigned to Ubuntu machine 64.149.xxx.xxx.  Router still assigns IP's to clients using DHCP 192.168.2.100 and up.  I can no longer browse to the server with "My Network Places" or connect using //Ubuntu/share.  I now have to enter the IP address of the server in the address bar of Windows Explorer.

I also cannot search by "Computer Name" to see the server.

Postfix still works fine.

Any ideas why I have lost the ability to "browse" apparently because of the IP address change?

Robert

---

### Post by rmarkin on 2006-02-18
Is this something that WINS might help with?

---

### Post by JohnSJ on 2006-02-18
How is your network wired up?

You'd most likely want your samba server to be multi-homed - either 2 nic cards or one nic card with two IP addresses - in either case you need one on the 192.x network and the other on the WAN IP - it can be the same nic depending on how the network is wired.

Samba should only listen on the 192.x network.

It should all just work after that (like it did before)

---

### Post by rmarkin on 2006-02-23
Thanks for the reply,

I finally decided that the simplest way to fix this issue was to rearrange which services were on which machine.  Samba is now on a different machine that is nat'd with a "local" address and Apache, Postfix are on the machine with a "public" address.  Works like a champ.

Thanks again.

---

