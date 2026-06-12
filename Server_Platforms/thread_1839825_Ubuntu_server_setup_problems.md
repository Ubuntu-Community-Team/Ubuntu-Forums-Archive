---
title: "Ubuntu server setup problems"
date: 2011-09-06
forum: Server Platforms
---

### Post by mobilewords on 2011-09-06
I had ubuntu 9.04 installed and had added on top a number of server packages which allowed me to 1: remote access using NoMachines NX Client for windows(on my laptop) and linux (from a flash drive on other linux machines to check mail, open and write files, etc; like a regular desktop operation; and I had the .www folder set up for http access using a web browser pointed at a DynDNS forwarded which was updated by ddclient.
Everything worked perfectly until sometime last winter when ubuntu suggested I upgrade.
Big mistake.
The new server packages come without gnome or other desktop contrivances so I was reduced to tring to configure everything my command prompt (terminal).

Nothing has worked since; I manage to get ssh installed and apache won't work; and vice versda and so on and so on; ddclient has not worked at all.

SO, in desperation I downloaded 10.04LTS and got it installed; I set up a Samba share (which doesn't work) and am reluctant to attempt to set up any LAMP type systems because the howtos and guides are so much outdated gobblygook it is very frustrating.

Surely there must be a ubuntu package or set of pacjages that can be apt-get installed and that give the functionality I described above.

Any help appreciated; and without server administrator root logon and 10,000 incomprehensible commands.  I only want it to work and I don't care how.

---

### Post by Dangertux on 2011-09-06
> **mobilewords said:**
> I had ubuntu 9.04 installed and had added on top a number of server packages which allowed me to 1: remote access using NoMachines NX Client for windows(on my laptop) and linux (from a flash drive on other linux machines to check mail, open and write files, etc; like a regular desktop operation; and I had the .www folder set up for http access using a web browser pointed at a DynDNS forwarded which was updated by ddclient.
Everything worked perfectly until sometime last winter when ubuntu suggested I upgrade.
Big mistake.
The new server packages come without gnome or other desktop contrivances so I was reduced to tring to configure everything my command prompt (terminal).

Nothing has worked since; I manage to get ssh installed and apache won't work; and vice versda and so on and so on; ddclient has not worked at all.

SO, in desperation I downloaded 10.04LTS and got it installed; I set up a Samba share (which doesn't work) and am reluctant to attempt to set up any LAMP type systems because the howtos and guides are so much outdated gobblygook it is very frustrating.

Surely there must be a ubuntu package or set of pacjages that can be apt-get installed and that give the functionality I described above.

Any help appreciated; and without server administrator root logon and 10,000 incomprehensible commands.  I only want it to work and I don't care how.

Without incomprehensible commands and using apt-get install.... easy.

LAMP
```

sudo apt-get install lamp-server^

```

SSH
```

sudo apt-get install openssh-server

```

Dynamic IP update client (uses no-ip.com still free though)
```

sudo apt-get install noip2

```

easy enough?

---

