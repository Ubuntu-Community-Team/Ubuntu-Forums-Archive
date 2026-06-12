---
title: "Detecting if my server is sending out spam"
date: 2008-12-18
forum: Security
---

### Post by psyncho on 2008-12-18
Hi, Comcast recently shut down my port 25 saying spam was emanating from my network. I think they're wrong, but was compelled to scan all my machines anyway. 

For my Ubuntu server I have postfix, looked at all the logs, didn't find anything but system messages sent to root. I did a tcpdump and am looking over all traffic with wireshark and see pretty much no smtp other than those same system messages. I also did a clamav scan for kicks and found nothing.

Just wanted to get opinions/advice on what other folks might recommend looking at - or if there is a more practical/methodical approach recommendations I can use to hone my own trouble shooting skills. 

thanks

---

### Post by Dr Small on 2008-12-18
Did you secure postfix to reject mail for SMTP unless it is originating from the local network? Otherwise, your ISP is most probably correct, and you have been used as on open relay.

---

### Post by psyncho on 2008-12-18
I'm behind a firewall and only http and https is accessible, so unless a virus on another machine on my local network was using my mail server as a relay....

that's why I'm inspecting logs and packets, but right now I'm primarily concerned with spam originating from the server in case it was compromised, which I don't think it was. 

btw - postfix is now setup to only accept mail from localhost, although I did have security and authentication before that as well, so even then...

---

### Post by Dr Small on 2008-12-18
Ok. That's good then. If port 80 and 443 were the only ports open in the firewall, I doubt that your server was being used as an open relay.

---

