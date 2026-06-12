---
title: "eth1:6 or eth0:6 -- Potential Bug?"
date: 2008-01-16
forum: Server Platforms
---

### Post by psi-phy on 2008-01-16
Greetings Folks,

**Quick Background:**
  About 3 months ago, I finally got my VP of IT's approval to ditch RedHat EL and let me install Ubuntu 7.10 for four brand new Dell Power Edge 1950 servers.  These servers are our main production webservers, and I couldn't wipe RHEL off quick enough. :)

  To keep things simple for me as the administrator, I gave all of the servers base IP addresses on eth1.  Then I adjusted the interfaces file to have virtual interfaces for our web-services which each have their own IP and a URL associated with it.

  The interfaces files are the same across all four boxes, however only one service runs on one box at a time.  The main idea is that if one server dies, I just bring up the same interface on another server and I don't loose downtime.

**My Problem:**
  I just came across and oddity that has baffled me.  The virtual interface :6 will NOT come up at all.  I can change the interfaces file and rename eth1:6 to eth1:7 and the virtual interface comes up fine.  :1 through :5 works fine and :7 through :9 work fine, however :6 just refuses to come up.

  Interestingly, I have the same effect across ALL four webservers which all have identical hardware and as mentioned, the interfaces file is the same as well.

  Is this a potential bug or is a virtual :6 interface reserved per-se for something that I wasn't made aware of?

  I'm also curious if I am the only who has come across this, or if it's well known.  I haven't seen anything in my searches.

  Also, if this is a bug, it would be the first time I have found one, which then would make my next question:  How to I inform the dev team of this bug?

---

### Post by HermanAB on 2008-01-16
I haven't seen that.  I suspect that you have a bad MAC or IP address defined for that interface, the system detects a clash and then won't bring it up.

---

### Post by psi-phy on 2008-01-16
Well the weird thing is that all the other virtual IP sections are the same as the :6 ones except for the actual IP.  All of these web-services are in my DMZ so they are all setup the same.  The only difference between this one and the others is the actual IP address.  

And what's odd is that I could take another virtual IP web-service make it :6 and it won't come up.  I could say put it back to :5 and it works...

It's a very odd thing which is why I wanted to mention it here. :)

---

