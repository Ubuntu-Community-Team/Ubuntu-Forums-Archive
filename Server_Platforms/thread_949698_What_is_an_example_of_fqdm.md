---
title: "What is an example of fqdm?"
date: 2008-10-16
forum: Server Platforms
---

### Post by bcl420 on 2008-10-16
Trying to get the server up and running. This is my first time setting up a server. I have run servers but never installed and configured. I'm using smoothwall 3 and don't quite get the orange card configuration. Anyone done a similar setup? This is for ppc by the way.

---

### Post by lykwydchykyn on 2008-10-16
It's been a long time since I last demo'd smoothwall, so forgive me for not knowing what the orange card configuration is; but I assume you mean "fqdn" which stands for "Fully Qualified Domain Name".  

It basically means your hostname with the DNS domain name appended to the end.  e.g. -- host.example.com.

---

### Post by bcl420 on 2008-10-16
Thank you for the example. That helps alot:)

Using smoothwall alot if you have any questions.

---

### Post by bcl420 on 2008-10-16
how do i set the fqdn? What is the command(s)?

---

### Post by lykwydchykyn on 2008-10-16
Typically, you edit /etc/hostname and /etc/hosts and just put it in there.

---

### Post by bcl420 on 2008-10-16
awesome thanx!!!!!!!!!!!!!:KS

---

### Post by bcl420 on 2008-10-16
Now I can't maintain an ip. Everytime i reboot it disappears. I set it static using the ifconfig eth0 192.168.1.101.

---

### Post by lykwydchykyn on 2008-10-16
To make it persist, you need to add it to /etc/network/interfaces, like so:

```

auto eth0
iface eth0 inet static
  address 192.168.1.101
  netmask 255.255.255.0
  gateway 192.168.1.1

```

Then you can ifdown eth0 && ifup eth0 and it'll be set.

---

### Post by bcl420 on 2008-10-17
Nice just got that set. Just before your reply. Much thanx!!!!

I'm almost there. I was thinking to direct my adns/bdns to my account at dyndns which would forward to my server. Is this delusional?


By the way i have connection to my server from the green card but my orange card or dmz doesn't connect to internet. Any ideas?:guitar:

---

