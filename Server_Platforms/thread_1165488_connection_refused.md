---
title: "connection refused"
date: 2009-05-20
forum: Server Platforms
---

### Post by Vegan on 2009-05-20
i installed telnetd so I can remote admin the server, fresh install of 9.04 after the disk died.

connection refused.

---

### Post by Sub101 on 2009-05-20
I find it better to use ssh to admin my server. Might be worth a look for you.

---

### Post by sickdude on 2009-05-20
Yea im with Sub101 ssh is the way to go! Far more secure then telnet.

---

### Post by Vegan on 2009-05-20
I am using a Windows terminal client, telnet is fine. I am behind a firewall so I am secure.

I am only wondering why it refused to let me in after I installed telnetd

---

### Post by doas777 on 2009-05-20
> **Vegan said:**
> I am using a Windows terminal client, telnet is fine. I am behind a firewall so I am secure.

I am only wondering why it refused to let me in after I installed telnetd

have you confirmed that telnetd is running?
```
sudo ps -ef | grep telnet
```

---

### Post by sickdude on 2009-05-20
And did you configure it right?

[edit]

Got a firewall running btw? On the server that is...

---

### Post by Vegan on 2009-05-20
I found the problem, the stupid Linksys WRT54G was the problem. Changed the port forwardings to get it to cooperate. Curious as I was directly addressing the machine.

---

### Post by Sub101 on 2009-05-21
Were you already behind the router?

---

### Post by Vegan on 2009-05-22
Both machines are attached to the WRT54G and on an intranet.

---

### Post by doas777 on 2009-05-22
do you have gufw or firestarter or whatever configured on the server? any IPTables configuration?
and like i asked above, are you certian that telnetd is running?

---

### Post by Vegan on 2009-05-22
first thing I installed after the CD was finished was telnetd

---

### Post by windependence on 2009-05-22
> **Vegan said:**
> I am using a Windows terminal client, telnet is fine. I am behind a firewall so I am secure.

I am only wondering why it refused to let me in after I installed telnetd

I wouldn't be so sure if any part of your intranet is also connected to the internet.

The other question would be "But why?" Why when ssh is so easy to use would you want to use an insecure outdated technology like telnet?

-Tim

---

### Post by wirelessmonkey on 2009-05-22
Just remember, telnet sends absolutely everything cleartext, so if anyone gets on your local network, or something is misconfigured, or any exploits become available for your router firmware, or if port 23 gets spoofed somehow, everything sent via telnet (username, pass, keys, config, sessions, etc...) is completely visible.

If you're not concerned with that, then security is a non-issue.

---

### Post by doas777 on 2009-05-23
> **Vegan said:**
> first thing I installed after the CD was finished was telnetd
that doesn't answer my question.

---

### Post by Vegan on 2009-05-23
> **doas777 said:**
> that doesn't answer my question.

I checked and telnetd is running. Seems my old WRTY54G is not all that smart. Maybe is MOD is in order.

---

### Post by Vegan on 2009-07-09
The Linksys firewall was the problem, Ubuntu is not universal Plug & Play so I have to run the LAN manually, not a problem.

The Linksys box supports uPnP so I figured Linux supported it natively or as a default package.

---

