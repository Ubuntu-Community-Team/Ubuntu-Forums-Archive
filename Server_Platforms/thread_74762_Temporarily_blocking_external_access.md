---
title: "Temporarily blocking external access"
date: 2005-10-12
forum: Server Platforms
---

### Post by Hikaru79 on 2005-10-12
I have a workhorse ubuntu PC that's doing about a million things. It's an SMB fileserver, a printserver, an Apache server, NFS, MySQL, etc. However, I'd like to take it offline for a few days. However, I would STILL like to be able to access everything internally. Basically, I want the server to refuse ANY and ALL connections that aren't from the local network (not 192.168.1.*  , basically). Now, I know I can just filter out its local address from my router, but then when I boot, things start failing all over the place because the internet's not accessible. I don't want to have to remove everything from the server that requires net access, and have to put it all back in a few days. basically, I just want a nice clean simple way to make the server only serve the local area network. Is there any easy way to do this, guys?

Thanks in advance =)

---

### Post by herrpoon on 2005-10-12
Wouldn't just unforwarding all necessary ports be the easiest way?

---

### Post by mlomker on 2005-10-12
Have you looked at the [firestarter]("http://www.fs-security.com/screenshots.php") package?  It's a GUI front-end to IPChains and makes short-work of things like that.

---

### Post by Hikaru79 on 2005-10-12
[QUOTE=herrpoon]Wouldn't just unforwarding all necessary ports be the easiest way?[/QUOTE]
You mean from the router? No, that wouldn't be enough. Outgoing connections would still work, right? Also, doesn't port forwarding apply to the internal LAN also? (I might be wrong about that second part)

[QUOTE=mlomker]Have you looked at the firestarter package? It's a GUI front-end to IPChains and makes short-work of things like that.[/QUOTE]
I'll have a look at that right now =) Thanks!

---

### Post by angrylittleman on 2005-10-13
Just edit the hosts.allow and hosts.deny files...should keep your internal stuff working and the external stuff out...

---

### Post by LordHunter317 on 2005-10-13
Not hardly on linux.  Very few things use tcp_wrappers.  The best way is to use iptables to get blocking that will work for all applications.

---

