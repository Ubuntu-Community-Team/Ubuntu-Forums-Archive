---
title: "Qemu &amp; Synaptic problems (Port fowarding?)"
date: 2007-11-02
forum: Virtualisation
---

### Post by Ian505 on 2007-11-02
Here is my problem:

I have [Qemu Manager]("http://www.davereyn.co.uk/download.htm") installed on my portable, 2.5" 80G USB drive. I can boot Ubuntu 7.10 just fine as well as browse the internet through firefox- but I cannot refresh my repo list. 

What is wrong? I smell a port that is not being forwarded... but I don't know which port Synaptic uses to access the WWW, so I can't tell. Any suggestions?

Thanks!
Ian

---

### Post by ruibernardo on 2007-11-02
Hi lan505,

I suppose you are using net user network. I don't know if you really need to forward anything, but if you do, you could try this:

```
sudo -i
echo 1 > /proc/sys/net/ipv4/ip_forward
exit
```

---

### Post by Ian505 on 2007-11-03
> **epimeteo said:**
> Hi lan505,

I suppose you are using net user network. I don't know if you really need to forward anything, but if you do, you could try this:

```
sudo -i
echo 1 > /proc/sys/net/ipv4/ip_forward
exit
```

I tried your command in the terminal- no luck. I still can not refresh my repo list. The window comes up saying it is downloading it, finishes in about 1 second and then disappears. (If you can't tell I am not the most ubuntu-savvy user in the world..)

Also, the network connection in the top panel starts out with a ! in the lower corner and I have to click it and select wired connection every boot before I can use the internet at all. 

I will create a video of the boot if that helps.

I think it has to do with the emulator... I don't think that it is allowing forwarding certain ports. Again I will create a video of my settings and boot if that helps at all.

-Ian

---

