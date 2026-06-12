---
title: "rkhunter and exim4"
date: 2007-03-17
forum: Server Platforms
---

### Post by rottenbreed on 2007-03-17
Greetings...

I am new to Linux and I have been running Ubuntu for only 2 weeks now. I just recently had the time to read up on security precautions and such. I installed "rkhunter" which in return installed "exim4." My question is this... do I need exim4 running? I do not need an email server/notifications unless rkhunter depends on that service. I did a "sudo netstat -pan --ip" and noticed how exim4 is listening on port 25. I want all ports closed if possible that I do not use, so is it safe to remove/uninstall exim4? If so, would I just run "apt-get remove exim4" ??

I do not want to break rkhunter therefore I ask first.

I searched around these forums and google before starting this post, but maybe I didn't use the right keywords or overlooked something since I never found my answer of if I can safely remove exim4 without breaking rkhunter.

Thanks in advance for whoever bothers to reply.

---

### Post by Nikron on 2007-03-17
Huh?  exim4 is not a dependency of rkhunter...

---

### Post by johnc4510 on 2007-03-18
See attached screenshot:

---

### Post by Nikron on 2007-03-18
Oh, it is a dependency... on feisty..  It isn't on my edgy server install..

---

### Post by rottenbreed on 2007-03-18
My main concern was exim4 listening on port 25. But since it seems rkhunter depends on it I am stuck with an open port. Hmmm.

tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN     6705/exim4

---

### Post by johnc4510 on 2007-03-18
Just because it's listening, it doesn't mean that it will respond to the outside.
This is more of a firewall issue. Ubuntu comes with the firewall iptables installed and running. To make it easy to configure, install firestarter from synaptic package mgr. With this you can easily configure the firewall. When you configure it, be sure to check the box that says icmp or imcp, can't remember for sure. Then google  for a firewall tester called shieldsup. You can go to that site and have it check the ports to make sure none are responding to the outside.

---

### Post by rottenbreed on 2007-03-18
I'm good then. I had already installed Firestarter but didn't have the ICMP box checked. My box passed all of Shields Up's tests. Thanks for the info.

---

### Post by dannyboy79 on 2007-04-18
i'd also like to point out that exim4 is listening on port 25 but only from the localhost. don't you see the 127.0.0.0:25. 127.0.0.0 is the loopback basically meaning itself. that means that it's only going to send out emails that are sent from the localhost. I always was curious about this as well when I used netstat. apparently when you run netstat and see a port "listening", if it only has the port, than that means it's listening on all interfaces not just the loopback (known as localhost). so you're ok. also you could always just block it with a software firewall and then if your hardware firewall isn't forwarding ports than there's certainly no way a spammer would be able to use your smtp server. you'll all set.

---

