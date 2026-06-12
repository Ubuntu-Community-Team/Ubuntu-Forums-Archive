---
title: "Ubuntu Server Network connection Virtual Box"
date: 2017-12-24
forum: Virtualisation
---

### Post by jbl92 on 2017-12-24
Hello, 

I am beginner on Ubuntu server and linux in general. 

I would like to connect a virtual ubuntu server to both a virtual lan network as well as the internet. 

For this I've enable two networks cards on virtual box for this particular virtual machine.

Unfortunately my internet connection works only when I set just one card (the first) in NAT. 

My question: how to define the network card where the internet trafic is suposed to come from ? Which option enable or modify in which file ? 

Thank you in advance :)

---

### Post by howefield on 2017-12-24
Thread moved to the "*Virtualisation*" forum.

---

### Post by SeijiSensei on 2017-12-25
First, if you're going to get into things like networking virtual machines, you really need to read the VirtualBox manual, probably more than once, particularly [https://www.virtualbox.org/manual/ch06.html](https://www.virtualbox.org/manual/ch06.html).

As for your other question, you might want to try setting the Internet-facing adapter to use "Bridged Networking."  Then the VM will appear to be on your physical network with an address in the same space as the host machine.  You can change this in the Settings for the virtual machine.  The VM will then have the same access to the Internet as any other machine on your network like the host.

---

### Post by jbl92 on 2017-12-26
Ok thank you.

---

