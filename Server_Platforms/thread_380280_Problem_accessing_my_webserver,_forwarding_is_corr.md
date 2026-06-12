---
title: "Problem accessing my webserver, forwarding is correct"
date: 2007-03-09
forum: Server Platforms
---

### Post by d1gital on 2007-03-09
I am trying to run a web server (lighttpd). It is only for personal use, so i am not using the server edition of ubuntu.  I have it configured to use port 8080 because my ISP blocks incoming connections on port 80 (they want you to upgrade...)  My ports are forwarded correctly, i tested this with the ShieldsUp portscanner at grc.com.  When the webserver is running, port 8080 is open, and when it is not, port 8080 is closed. so far sso good. The problem i am having is that when i try to navigate to "http://<my ip>:8080" it loads indefinitely, and eventually times out.  Navigating to "http://127.0.0.1:8080" works fine. Thanks in advance.

---

### Post by Mr. C. on 2007-03-10
Is the <my ip> you listed your WAN IP or your LAN IP ?

Many routers will not allow you to access your site via your WAN's public IP, since you are on the LAN.

MrC

---

### Post by d1gital on 2007-03-10
That is my WAN IP.  I can access it thru my LAN IP, but obviously that only works on my LAN.

---

### Post by Mr. C. on 2007-03-10
I can't tell from your response if you've tried your WAN IP from some station outside of your LAN?  In otherwords, are saying other's cannot access your site via the public IP?

---

### Post by nix4me on 2007-03-11
You cannot access your website with your WAN IP from a computer that is behind your router.  This is "feature" of  most all routers.

Go to a friend or neighbors house and access it, i'm sure its working fine.

nix4me

---

### Post by Nikron on 2007-03-11
Or, use a proxy from home to look at your WAN IP, I'm sure it's fine then too...

---

