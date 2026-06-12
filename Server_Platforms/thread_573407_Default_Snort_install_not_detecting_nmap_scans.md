---
title: "Default Snort install not detecting nmap scans"
date: 2007-10-11
forum: Server Platforms
---

### Post by jamisnemo on 2007-10-11
Hello!

I've just installed a clean version of Ubuntu Server with "LAMP", vsftpd, snort, and nmap. 

The internal IP of the machine is 192.168.1.151 so I set the HOME_NET to 192.168.1.0/24. I'm pretty sure this is correct but after testing it as I'll explain below, I decided to reconfigure snort using dpkg-reconfigure and set HOME_NET to any.

For both settings of HOME_NET I tested snort in the following way:
I stopped the snort daemon using:

```
server# /etc/init.d/snort stop.
```

I started snort again at the prompt using:

```
server# snort -de  -h 192.168.1.0/24 -c /etc/snort/snort.conf
```

and, at the same time on another terminal I started a live tail on /var/log/snort/alert:

```
server# tail -f /var/log/snort/alert
```

So, as far as I can tell, I now have snort logging to the screen, and the snort alerts being looged to the screen directly from the log file.

Now to test snort I run an nmap port scan on this box from another computer on my network:

```
workstation% nmap 192.168.1.151
```

But there is no hint of detection on the snort machine. The only way I can get a detection is by nmapping another machine on my network from the server I just installed:

```
server# nmap 192.168.1.150
```

or even

```
server# nmap 192.168.1.100
```

Then the log spits out a detection.



Any help would be a big hand. I know this post is kind of long but I realy don't understand what's going wrong.

Thanks,
jamis

---

### Post by netlogic on 2007-10-11
From what I know  "nmap -P0" scan, is not going to be caught by snort. It might have been changed now. I will check it again if I have time tonight.

---

### Post by jamisnemo on 2007-10-16
Just bumping my thread... has anyone ever even installed snort on their ubuntu server?

I'm almost positive nmap -P0 scans won't be caught by snort but just a simple nmap should be picked up. Hell nmap is practically the most basic kiddie port scanner available... and nmap's default scan isn't exactly quite.

So why isn't my default install catching it?

Please, any help would be awesome,
Jamis

---

