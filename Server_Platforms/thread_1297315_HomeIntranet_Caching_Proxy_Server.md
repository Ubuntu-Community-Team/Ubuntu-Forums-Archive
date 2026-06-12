---
title: "Home/Intranet Caching Proxy Server"
date: 2009-10-21
forum: Server Platforms
---

### Post by localfiend on 2009-10-21
I'm looking for the best option for a small network caching proxy server.  I already have a jaunty server that runs two websites via apache, as well as a full blown postfix/courier setup for e-mail.  

To keep things simple I think I'd like to use another PC (got one handy) to act as a caching proxy server.  I mainly want to be able to track all internet traffic and bandwith from inside my local network, and figured the caching ability might be helpful as well.

From my research, the simplest solution seems to be that I should install apache with some kind of proxy module.  I am just unsure about the best way to go about this.  Is there a recent tutorial any where out there that I can follow?  Or are there better options for what I want to do?  Squid?

Thanks

---

### Post by undecim on 2009-10-21
squid is a caching http proxy server. I used it for a while (before my server went on strike) and was quite pleased with it.

[https://help.ubuntu.com/9.04/serverguide/C/squid.html](https://help.ubuntu.com/9.04/serverguide/C/squid.html)

---

### Post by localfiend on 2009-10-21
Never tried squid before so I decided to give it a go.  Everything seems to be up and running - I'm just a bit bewildered looking for a good program to monitor the log files.  Most of them have way to much information, anyone know of a simple addon that can monitor log files and give me basic information (like total traffic for a certain time period)?

---

### Post by cariboo on 2009-10-21
Have a look at bandwidthd, it is in the repositories.

---

### Post by localfiend on 2009-10-22
> **cariboo907 said:**
> Have a look at bandwidthd, it is in the repositories.

Installed bandwidthd using aptitude and have it working through apache.  The only thing is that it doesn't seem to be measuring traffic correctly.  Tried downloading a couple of file from various computers, and browsing around.  Bandwidthd reports for all used IP's but its not displaying the correct amount of traffic.  I'm downloading and uploading far more than is being reported.  I have it set to monitor my 192.168.0.0/24 subnet.  Is that the wrong way to go about it?

---

### Post by localfiend on 2009-10-22
Well, just ssh'd back into my server to do some double checking and discovered that I have 2 zombie processes.  :(

Running: ps -el | grep 'Z'

Comes up with: 
F S   UID   PID  PPID  C PRI  NI ADDR SZ WCHAN  TTY          TIME CMD
1 Z     0  7475  7386  0  85   5 -     0 exit   ?        00:00:00 bandwidthd <defunct>
1 Z     0  7584  7385  0  85   5 -     0 exit   ?        00:00:00 bandwidthd <defunct>

So it looks like the repository version of bandwidthd must have some problems.  From what I can tell its a pretty old program, If I can find an updated version I might try it out.  Otherwise I think I'm stuck with finding something that will do the same thing with my proxy logs.

---

### Post by KeithEckstein on 2009-10-24
**Localfiend** - I have (am in the process of finishing and documenting) a 600MHz celeron with 256MB of Ram and a 9GB hard drive that is running Squid, Squid-Prefetch and PDNSD (DNS caching) - it also has a hosts file (based on one from hostfiles.org) to filter out ad sites.  I built it because, living in rural France, I only get 512KBs ADSL.

Realistically, although it has done very little to improve the internet speed (apart from filtering out adverts and doing some caching), my machines feel twice as fast (about how they were when I was on a 1MBs connection.)

Have done basic documentation on what I have done (and how to replicate it) but have also got an automated install (via preseeding) that makes it a doddle to set up.)

When I've got something worth showing, I'll post the web address here and you can have a play with it (tomorrow, I hope, or maybe Monday.)

All the best

Keith

---

### Post by localfiend on 2009-10-24
That'd be great Kieth, thanks!

---

