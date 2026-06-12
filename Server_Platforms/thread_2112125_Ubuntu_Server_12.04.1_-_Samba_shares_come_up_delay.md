---
title: "Ubuntu Server 12.04.1 - Samba shares come up delayed. Eh?"
date: 2013-02-03
forum: Server Platforms
---

### Post by Roasted on 2013-02-03
I'm running Ubuntu Server 12.04.1 on a box with a mirror running. That volume is sitting on 192.168.1.20. I have a bookmark in Nautilus (Ubuntu desktop edition 12.04) on my desktop and laptop. In both instances, if I click that link, it comes up with a white screen. In the meantime, if I count to about 12-15, then hit refresh, they magically appear.

This first happened when my "server" was actually an Atom powered nettop I had here. I've since done a fresh install and rebuilt the configs from ground up (smb.conf, etc.) on a new i3 3220T powered rig. That install does the same thing.

I'm just curious if this is, for some reason, expected behavior now-a-days. I've used Samba for YEARS, even though my LAN has been an exclusive Linux shop for quite some time (user based authentication just makes sense, in my opinion). But I don't recall ever seeing a delayed reaction like this. Any insight?

---

### Post by HermanAB on 2013-02-03
The tools you need to investigate Samba issues:
tail -f /var/log/whatever.log
top
ntop
tcpdump
smbclient

and sometimes dig or nslookup.

---

