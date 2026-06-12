---
title: "Unknown source IP in Wireshark packet capture"
date: 2009-05-10
forum: Security
---

### Post by kewl_123 on 2009-05-10
Hi,
    i installed wireshark on Ubuntu 8.04 yesterday and was connected to net wirelessly. I ran wireshark as sudo. Here is a line from packets captured on wireless interface:

who has?               tell
10.232.218.1           10.232.218.117

Now my IP begins with 192.168 and same for my default gateway. From what little knowledge I have, this seems to be and ARP msg but how come its from some IP address other than my computer (i.e. 10.232.218.117 )

Also there was a line "Zhongxin_81:94:e7"   which was an ARP broadcast.

Can anyone please explain what these two things mean?

Thank you.

---

### Post by cariboo on 2009-05-10
Do you have any vm's running when you see the these ip addresses? With networking set for nat I get an ip address of 10.0.2.2. running Jaunty in Virtualbox.

---

### Post by kewl_123 on 2009-05-10
I have nothing running on my Laptop.
I use it only to surf net.
Even today I am seeing the same IP addresses.


( i searched for it and found its from Private IP address range and it cant be on internet...)

---

### Post by miluns on 2009-05-10
Go to [www.whatismyip.com](www.whatismyip.com) and see if that is the WAN IP for you.


192.168.x.x should be your LAN IP.

My LAN assigns 192.168.x.xx to my network but my WAN is 75.64. etc...


If I understand LAN and WAN IP protocols correctly.


Good luck,

Mike

---

### Post by mr-woof on 2009-05-10
Can you ping either of the addresses?

Have you looked at your router, who's attached? Do you use wireless security?

---

### Post by kewl_123 on 2009-05-10
> **mr-woof said:**
> Can you ping either of the addresses?

Have you looked at your router, who's attached? Do you use wireless security?

I cant ping either address.

I couldnt make out if someone is attached to my router.

As for wireless security, the only thing I have is the ID and Password entered in router by the ISP guy. I asked him can anyone connect to my wireless network and he said no one can as they dont have my ID and Password.
But when I had a look at my router interface, one thing that i saw was it said "authentication disabled" in the wireless section, no WEP or anything.


**Miluns**:
No, thats not my WAN IP.
  From as much as I know, IP startting with 10 cant be an IP on internet as its reserved as private IP and those packets will get dropped.

---

### Post by The Cog on 2009-05-11
I think it is likely coming from your ISP for some reason, in which case all you can do is ignore it. You could examine the source MAC address to see which hardware NIC is sending it, and compare that with the MAC address your router is using.

---

