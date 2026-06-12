---
title: "SSH Help"
date: 2011-03-31
forum: Server Platforms
---

### Post by shade34321 on 2011-03-31
I've recently set up Ubuntu Server on an old computer and set it up as a web server with SSH. I used dyndns and managed to get everything up and running yesterday. Last night I was working on getting private/public keys up and running on the server so I no longer had to use a password and the SSH no longer works and neither does the URL from DynDNS. Yet I can still SSH into my computer from my phone using the DynDNS url but if I try it from a computer I get a connection refused error back. Any help would be greatly appreciated. Thanks!

---

### Post by d3v1150m471c on 2011-03-31
try deleting the contents of .ssh/known_hosts and remake the key

---

### Post by rubylaser on 2011-03-31
Did you verify that your public ip hadn't changed, and that the ip that DynDNS matches your public ip?  And, I assume this was working outside of your LAN before, and now isn't working.  If you've never tested remotely before, I'd caulk it up to port 22 being closed on your firewall if the DNS name resolves correctly.

---

### Post by d3v1150m471c on 2011-03-31
you might also want to read this if you haven't. my ssh is working fine with it.
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

### Post by shade34321 on 2011-03-31
I just had a friend test it from his house and it allows him to ssh into it and when I use my phone I can view my index page. So it seems to be my home network that isn't allowing something. But I will try what everybody has suggested when I get home.

---

