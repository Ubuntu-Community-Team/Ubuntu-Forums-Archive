---
title: "I cant ping XP to XP (both are inside virtual box) via router"
date: 2009-02-10
forum: Virtualisation
---

### Post by Rytron on 2009-02-10
Hi.
I have connected my Ubuntu laptop and Ubuntu desktop via a router and cat5 straight through cables. Everything works smoothly between my Ubuntu installations. I also have Windows XP installed on both laptop and desktop computers in Virtual Box. While in XP in Virtual box on both computers, I have assigned them both static addresses. They can not ping each other. Why is this? The addresses I use: 
XP inside Desktop Virtual Box 192.168.1.1
XP inside Laptop Virtual Box 192.168.1.3

Note: I am not connected to the internet when I tried.

:confused:

---

### Post by mindwarp on 2009-02-10
> **Rytron said:**
> Hi.
I have connected my Ubuntu laptop and Ubuntu desktop via a router and cat5 straight through cables. Everything works smoothly between my Ubuntu installations. I also have Windows XP installed on both laptop and desktop computers in Virtual Box. While in XP in Virtual box on both computers, I have assigned them both static addresses. They can not ping each other. Why is this? The addresses I use: 
XP inside Desktop Virtual Box 192.168.1.1
XP inside Laptop Virtual Box 192.168.1.3

Note: I am not connected to the internet when I tried.

:confused:

If your networking type is set to 'nat' this will not work.  You should switch the adapter mode to 'bridged'.

---

### Post by Rytron on 2009-02-10
Thank you mindwarp. I'll try that.

:P

---

### Post by Rytron on 2009-02-10
> **mindwarp said:**
> If your networking type is set to 'nat' this will not work.  You should switch the adapter mode to 'bridged'.

I see the NAT option is ticked. How do I switch the adapter mode to 'bridged'?

The two Virtual Box Windows XP operating systems can ping 127.0.0.1 and their own ip addresses.

---

### Post by mindwarp on 2009-02-15
In virtual box under the VM's network settings, where it says 'Attached to:' switch it from NAT to Host Interface and that will put it on your network so you can ping out / in etc.

---

### Post by Rytron on 2009-02-15
Thanks.

:popcorn:

---

