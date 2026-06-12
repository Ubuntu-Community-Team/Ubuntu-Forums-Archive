---
title: "server, fresh install"
date: 2006-01-12
forum: Server Platforms
---

### Post by chemisus on 2006-01-12
i have installed the ubuntu server on an old computer, and i dont think dhcp is an option. i have tried manually setting the network settings, but i can only ping local computers and can not access anything on the internet.

the only way other computers can ping the server is if i use the ip address. i suspect it has something to do with dns, because i have not set a dns yet. mainly, because i dont know how, where, or what it would even look like.

what should i do?

---

### Post by Wyrm_1972 on 2006-01-12
First question I'd ask you is what do you want to do with Ubuntu?

What are you hoping to achieve with a server set-up of Ubuntu?

---

### Post by chemisus on 2006-01-12
i just want to be able to mess around with it really.

i want to install ssh server on it, but im trying to do that through apt-get. cant do that until im able to get it online.

---

### Post by chemisus on 2006-01-12
i got it to work for now with dhclient.

id still like to know how to set a static ip and have access to internet. i had inserted the line "auto eht0" and still didnt work.

---

### Post by juicybananahead on 2006-01-12
Hi chemisus,

Can you post the contents of /etc/network/interfaces please? To get my computer set up as a static ip (it's connected to my router and then onto my ISP) I have the following lines:

```
iface eth0 inet static
        address 192.168.1.7
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        dns-nameservers 81.1.113.10 81.1.113.11

auto eth0
```

---

### Post by carpenike on 2006-01-12
[QUOTE=chemisus]i have installed the ubuntu server on an old computer, and i dont think dhcp is an option. i have tried manually setting the network settings, but i can only ping local computers and can not access anything on the internet.

the only way other computers can ping the server is if i use the ip address. i suspect it has something to do with dns, because i have not set a dns yet. mainly, because i dont know how, where, or what it would even look like.

what should i do?[/QUOTE]

The reason you can't ping anything on the internet and only local is because your default gateway is not setup correctly; your router's IP.

The reason DHCP works is because it's probably assigning your default gateway to your client automatically.

---

### Post by chemisus on 2006-01-12
```

        auto eth0
        iface eth0 inet static
        address 192.168.1.5
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.254
        dns-nameservers 192.168.1.254

```

thats what i was using for the interfaces. im guessing that dns is wrong, but ive assigned that before and it still worked fine.

---

### Post by juicybananahead on 2006-01-12
I'd say that dns ip is wrong alright, that's the ip of your router, yeah? If you put in the dns of your ISP, it should work... but how are you going to get that, right? ;) Well, I'm not too sure about this, but I think that when you connect using dhcp, the dns that you need is written to /etc/resolv.conf It should look something like ```
nameserver 81.1.113.10
``` So, connect using dhcp, get the dns address, then add it to your /etc/network/interfaces file. Good luck!

---

### Post by dustyculler on 2006-01-12
A lot of dsl routers run dns (or at least forward it on) and when they hand out a dhcp lease they put their lan ip address for the first dns server, so that nameserver may be right.

If you do have dhcp running on your network and you just wanted to setup a static ip for serving, you could look at another system using dhcp and check it's dns settings, or set your server up to use dhcp and see what it puts in the the /etc/resolv.conf for dns settings and then set it up for a static ip once you've got the dns sorted out.

I've got a working setup with a few less settings than you've got in the /etc/network/interfaces file, and the dns settings in the /etc/reslov.conf.

I'll give an example below.

I've currently got this for my /etc/network/interfaces:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

iface eth0 inet static
address 192.168.159.43
netmask 255.255.255.0
gateway 192.168.159.1

auto eth0
```

And I've got this in my /etc/resolv.conf:
```

nameserver 192.168.159.1
nameserver 67.132.23.31

```

---

