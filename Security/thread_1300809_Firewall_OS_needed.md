---
title: "Firewall OS needed"
date: 2009-10-25
forum: Security
---

### Post by pawhtiobo on 2009-10-25
Hi ppl :)

I recently received 3 IBM Netfinity 4000R servers, I'm planning to use one of them as a fileshare server, the other one as a DNS/DHCP and Apache server, they will be running **Ubuntu 8.04 LTS Server**, the last one i pretend to use it a firewall to protect the network. My question is, which distro i should use as a firewall? i made dome research and take a look a distrowatch and i realized that there are some distros orientated to the firewall function, I need some advice to choose the firewall distro, i need one not to hard to manage because i'm not a network security expert and if possible with a GUI, something like webadmin.

Thank you in advance...

---

### Post by __p1n__ on 2009-10-25
Use netbsd and pf.

---

### Post by cariboo on 2009-10-25
HAve a look at [m0n0wall]("http://m0n0.ch/wall/") and [ipcop]("http:///www.ipcop.org/"), both work well and are fairly easy to use.

---

### Post by pawhtiobo on 2009-10-25
Hi :)

Thank you very much for the replies, i will give it a try to your sugestions in the next weekend and see which distro i feel most comfortable and which has the best performance, because the servers are dual pentium III 750Mhz, with only 512 Mb RAM.


see ya...

---

### Post by cariboo on 2009-10-25
Both should work equally well, as there are no guis, and management is done through a web interface.

---

### Post by Lars Noodén on 2009-10-26
I'll second the recommendation for netbsd and pf, and add openbsd and pf.

You can of course use IP Tables on the linux distro of your choice.

Or you can try a firmware-sized distro like pfsense, quagga, openwrt or tomato.

---

### Post by sahabcse on 2009-10-26
Try Devil Linux. Devil-Linux is a small CD based distribution which is used for firewalls.

---

### Post by withjigs on 2009-10-26
I am not completely sure, but how about 'www.untangle.com'?

---

### Post by Chayak on 2009-10-26
Vyatta, it's a router distro that has security features that rival cisco ASAs.  The community edition is free.

---

### Post by gnuisancev3 on 2009-10-26
IPCop is incredibly easy to use and has worked wonderfully for me for 3 years.  I love it and have never had a problem with it.

---

### Post by pawhtiobo on 2009-10-26
Hi :)

Thank you again for the replies. A friend of mine also recommended me to use the free home version of** Astaro Security Gateway**, i tried the online demo, where we can see all the options and simulate a configuration and it seem also very good. What do you think?

see ya...

---

### Post by pawhtiobo on 2009-10-26
> **withjigs said:**
> I am not completely sure, but how about 'www.untangle.com'?

I give it a look at Untangle, and it seems also a very nice bet...well one more to add to the testing list :D

Thankx :)

see ya...

---

### Post by pawhtiobo on 2009-11-03
Thank you all for the replies, i just installed Untangle and use OpenDNS, everyting is working as i expected :)

see ya...

---

