---
title: "Secure a Laptop Connecting to a Foreign Wireless Network"
date: 2013-01-02
forum: Security
---

### Post by c0deyellow on 2013-01-02
I want to start using a laptop on a foreign wireless network. I will use ssh to tunnel internet traffic. What other important security measures can I take to avoid snooping, cracking, and malware? (Do not include security measures that should be taken regardless. I'm looking for extra security needed when connecting to a foreign network.)

---

### Post by Bucky Ball on 2013-01-02
Please give more detail. What network and where? Are you currently traveling in a foreign country?

---

### Post by EnigmaticCoder on 2013-01-02
wrong thread. please delete.

---

### Post by c0deyellow on 2013-01-02
Not a foreign country. I want a general solution so I can use my laptop at school, hotels, libraries, etc.

I'm also not looking for an exhaustive list of security measures, just practical steps to take to avoid things such as an infected router sending out malware, someone else on the network sniffing packets, connecting to a network that may or may not practice good security, etc.

---

### Post by Ms. Daisy on 2013-01-03
Obviously turn off any services you might normally run on the laptop before connecting to the wifi.

I would run a software firewall with strong inbound/outbound rules if I really didn't trust the network. I'd allow port 53, 67, 68, 80 and your ssh port out, then I'd block 80 after establishing the ssh tunnel. You can also force 53 DNS over the ssh tunnel, see this:
[http://askubuntu.com/questions/147936/does-creating-a-socks-proxy-via-ssh-hide-my-activities-from-my-isp](http://askubuntu.com/questions/147936/does-creating-a-socks-proxy-via-ssh-hide-my-activities-from-my-isp)

But I imagine you need to leave 67 & 68 open lest you won't get your IP lease renewed.

I wouldn't install any updates or software when I was on said network.

---

