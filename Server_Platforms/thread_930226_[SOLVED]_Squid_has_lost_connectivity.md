---
title: "[SOLVED] Squid has lost connectivity"
date: 2008-09-25
forum: Server Platforms
---

### Post by TinBane on 2008-09-25
I had a functioning squid install, configured and running.

I then installed some software: "sudo apt-get install mediawiki php5-gd ebox-squid ebox-samba ebox-openvpn ebox-network ebox-usersandgroups mediatomb liblame-dev libfaad-dev libx264-dev libfaac-dev libxvidcore4-dev liba52-0.7.4 liba52-0.7.4-dev libdts-dev checkinstall"

I now get:
"ERROR

The requested URL could not be retrieved

While trying to retrieve the URL: [http://www.google.com/](http://www.google.com/)

The following error was encountered:

Connection to Failed
The system returned:

    (101) Network is unreachable
The remote host or network may be down. Please try the request again.

Your cache administrator is webmaster. 
Generated Fri, 26 Sep 2008 09:37:42 GMT by trident (squid/2.6.STABLE18)"

After authenticating onto squid. Squid is running as a process, and ifconfig shows normal network connection.

Should I try and remove the packages? How does squid 'see' the internet.

---

### Post by Dr Small on 2008-09-25
Installing ebox-squid shouldn't have done anything, but it sounds like it can't resolve a hostname. You can try looking in /etc/resolv.conf and make sure you DNS servers are correct.

By the way, have you tried restarting Squid?

---

### Post by TinBane on 2008-09-25
yeah, I tried restarting squid, and also restarting the server.
Neither caused any change.

I'll look at resolv.conf

It has the correct nameserver.

---

### Post by TinBane on 2008-09-25
Weird. I used apt-get autoremove and the issue is now resolved.

WEIRD.

I'm using 32-bit, btw.

---

### Post by Dr Small on 2008-09-25
I surely don't know what the problem was, but I am glad that it was that simple to fix :) You can mark this thread as Solved now ;)

Dr Small

---

