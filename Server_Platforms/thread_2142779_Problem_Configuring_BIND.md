---
title: "Problem Configuring BIND"
date: 2013-05-06
forum: Server Platforms
---

### Post by OR83 on 2013-05-06
I'm currently setting up my server and I've been having problems configuring a static IP I've followed 3 different tutorials and I still get a non-authoritative IP I've called my ISP they told me to call my router manufacturer I added the IPs they told me I could use and I'm still having the same problem. if anyone could help me I'd greatly appreciate it. 
Thanks in advanced.

---

### Post by papibe on 2013-05-06
Hi OR83.

Are you trying to set up a Public static IP, or a LAN static IP?

What is your router's brand and model?

Could you post the result of these commands?
```
apt-cache policy network-manager

cat /etc/network/interfaces
```
Regards.

---

### Post by OR83 on 2013-05-06
It's a Dell poweredge 2850 I'm trying to have it set up so I can host websites. I already have it set up to the static IP I was told to use by linksys. however, it still says non-authoritative when I went to my godaddy.com to point the domain name it said DNS not registered. If you can help me out I'd appreciate it.

---

### Post by OR83 on 2013-05-06
That's the result of the command apt-cace network manager


thor@Valhalla:~$ apt-cache policy network-manager
network-manager:
  Installed: (none)
  Candidate: 0.9.8.0-0ubuntu6
  Version table:
     0.9.8.0-0ubuntu6 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring/main amd64 Packages

---

### Post by OR83 on 2013-05-06
And the CAT command



# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network inerface
auto eth0
iface eth0 inet static
        address 192.168.1.2
        netmask 255.255.255.0
        gateway 192.168.1.1

---

### Post by papibe on 2013-05-06
Let me see if I understand your situation.

You set up an static public IP with your ISP.

You registered a domain with GoDaddy, and you pointed it to your new public IP.

You are trying to setup your own BIND server at home, and trying to point your DNS Servers from GoDaddy to your home server?

Is that it?

Why just don't let GoDaddy to handle your records?

If you don't want to do that, have you registered your nameserver? Have you checked that they are OK using a nameserver whois ([http://www.internic.net/whois.html](http://www.internic.net/whois.html))?

If they are not registered, have you tried register them using GoDaddy: [Registering your own nameservers hosts]("http://support.godaddy.com/help/article/668/registering-your-own-nameservershosts").

Regards.

---

### Post by OR83 on 2013-05-07
hmm I wasn't aware of that. but yeah, I when I check them using ssh I get the nameservers I set up and my servers static IP.

---

### Post by OR83 on 2013-05-07
and I didnt let go daddy handle my records because I've always done that with a different web host plus I see it as an opportunity to learn more if I handle it myself

---

