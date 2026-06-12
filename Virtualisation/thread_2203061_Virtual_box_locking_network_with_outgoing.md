---
title: "Virtual box locking network with outgoing??"
date: 2014-02-01
forum: Virtualisation
---

### Post by einstein**-7 on 2014-02-01
I'm running virutal box on 12.04 with a virtual 12.04 and I have the network type setup as bridge but as soon as the virtual machine starts up virtual box sends 50-200k outgoing to the router and locks down the router for the real and virtual machine.. Screenshot shows the situation, Why is this ???????[IMG]https://dl.dropboxusercontent.com/u/81208150/Screenshot%20from%202014-02-01%2008%3A58%3A28.png[/IMG]

---

### Post by bashiergui on 2014-02-02
What do you mean "locks down the router?"

---

### Post by einstein**-7 on 2014-02-02
> **bashiergui said:**
> What do you mean "locks down the router?"

The outgoing trafic is so high than the bandwidth available for incoming is super slow. Takes a full minute for a "apt-get update" normal, 8 sec..

---

### Post by bashiergui on 2014-02-02
Sounds like a memory shortage. What are your host and guest RAM & hdd sizes?

If you weren't aware, VMs typically run slower than a host OS unless you have a powerful machine.

---

### Post by einstein**-7 on 2014-02-02
> **bashiergui said:**
> Sounds like a memory shortage. What are your host and guest RAM & hdd sizes?

If you weren't aware, VMs typically run slower than a host OS unless you have a powerful machine.

The screenshot shows I'm running on an i7 with 24GB ram...   virtual machine 1 core 3Ghz 2Gb ram this is a network issue- as soon as I start a virtual machine the "sent" network traffic shoots up and slows down the internet for the real and virtual machine the systems run fine..

---

### Post by bashiergui on 2014-02-02
So it does, I missed it. If your router allows you to configure QoS then have you adjusted it? I assume you don't have the same issues when no VM is running.

---

### Post by einstein**-7 on 2014-02-04
> **bashiergui said:**
> So it does, I missed it. If your router allows you to configure QoS then have you adjusted it? I assume you don't have the same issues when no VM is running.

Correct, no issues when no vm is running. Unfortunatly I cant set the qos on my router.... Its wack that virtual box would be sending so much information out though and no one else seems to have this particualr issue??

---

### Post by bashiergui on 2014-02-04
If you're familiar with Wireshark or tcpdump, I'd recommend you look at the packets the VM is sending. That might narrow it down to a network or software problem.

---

### Post by einstein**-7 on 2014-02-06
Ok, found the problem!! tcpdump shows a constant stream of udp packets going from my real machine to Ip 224.0.etc but only after a virtual machine is started.  Friend mentioned that udp is usally multimedia so after googling that IP with pulseaudio I found this bug [https://bugs.freedesktop.org/show_bug.cgi?id=44777](https://bugs.freedesktop.org/show_bug.cgi?id=44777)  this is older but exact same thing here.  Temp solution is to start the VM and Kill pulseaudio which then restarts itself but no crazy stream.

---

### Post by bashiergui on 2014-02-06
Cool, glad you found a workaround.

---

