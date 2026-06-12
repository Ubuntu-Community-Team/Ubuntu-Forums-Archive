---
title: "Question About &quot;Port 5353 open | filtered zeroconf&quot; Service"
date: 2010-03-24
forum: Security
---

### Post by mk-naomi on 2010-03-24
Hi
I've tried to do my research as best I can but am getting nowhere with my issue so I hoping some of you experts can help please?

I recently installed Xubuntu 9.10 and used Zenmap to test my security. I have UFW enabled with a default policy DENY: which I believe blocks all incoming but not outgoing.

On a "regular" (Zenmap / Nmap 5.00) scan it shows all 1000 ports closed. Which I am quite happy with. However when a "Slow comprehensive scan" is raised against my IP it shows the following... 

The Slow comprehensive scan =

nmap -sS -sU -T4 -A -v -PE -PP -PS21,22,23,25,80,113,31339 -PA80,113,443,10042 -PO --script all (my IP address)

PORT     STATE         SERVICE  VERSION
5353/udp open|filtered zeroconf
Too many fingerprints match this host to give specific OS details.

I researched the port and came up with lots of things about zeroconf, avahi-daemon and disabling ports etc....So far I have tried:

Adding a UFW rule to deny udp and tcp in and out on port 5353.
Removed avahi-autoipd and libnss-mdns.
Disabled my un-used interface eth0 (I need "lo" open otherwise it won't run the nmap scan)
Disabled my (un-used) wireless card at startup with "gksu gedit /etc/modprobe.d/blacklist" and "blacklist ipw2200"
Tested the live cd of Xubuntu 9.10 with a Zenmap install (incase I had installed something to create the problem)...

Despite everything I try it still shows this in the scan??

I do use an "hso0" 3G mobile device for internet on my laptop and wonder if this is the root of the problem?

If anyone could please suggest a remedy it would be a huge help!!

---

### Post by cdenley on 2010-03-24
I know avahi does listen on UDP (as well as the dhcp client), but it isn't really considered a security risk. You can disable it if you want.
```

sudo netstat -ulnp
sudo /etc/init.d/avahi-daemon stop
sudo update-rc.d avahi-daemon disable
sudo netstat -ulnp

```

Are you scanning your system from itself? Those results can be misleading. Are you scanning your LAN IP or WAN IP?

---

### Post by mk-naomi on 2010-03-24
Hi cdenley.
I ran sudo netstat -ulnp (nice command - where did you find that!...)which confirmed port 49628 & 5353 were in use via the avahi-daemon.
I've removed the avahi-daemon via APT and this has solved the problem **completely.**

Thank you so much for your support - this was driving me crazy!!

---

### Post by justanothergreysky on 2010-03-24
My first instinct is that these scan results are not accurate.

I echo the question of whether you are scanning from the same system, which can give incorrect results.  I would also wonder if you are scanning from on the same LAN and if the machine you are scanning from has any filtering enabled.

UDP port scanning is a bit of an inexact science anyway, because there are no session handshake results, so you're relying on ICMP to tell you whether or not the UDP port is open.  Certain types of firewalls can knock down ICMP and give all sorts of weird results in a UDP scan.

I wouldn't stress out too much.

---

