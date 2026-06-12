---
title: "dns server"
date: 2013-01-31
forum: Server Platforms
---

### Post by Vegan on 2013-01-31
I use Hyper-V in my shop and I was wondering, how lean a Ubuntu server install can be for RAM allocation for running BIND as a DNS server

The rival Microsoft product uses a lot of memory.

---

### Post by papibe on 2013-01-31
Hi Vegan.

That service will require very low requirements. You can go as low as the minimum system requirements for the server itself:
```
300 MHz x86 processor
128 MiB of system memory (RAM)
1 GB of disk space
```
Let us know how it goes.
Regards.

---

### Post by Vegan on 2013-02-02
storage is not a problem but virtual machine loads can be more of a nuisance

I can manage the VM from the Hyper-V host connection.

I noticed a program called xrdp was in some distributions, guess even Linux is hopping onboard.

---

### Post by papibe on 2013-02-02
I don't think xrdp would help you on a server.

The Ubuntu server edition is 100% text mode, so no desktop to connect to.

The most common way to admin a Linux server is through ssh. You install the server package on the server, and you can use the native client on any Linux machine and OSX, or the well-known Putty on Windows.

Let us know how it goes.
Regards.

---

### Post by Vegan on 2013-02-10
I can connect to the hypervisor and see the console that way.

No need for any direct remote access. A DNS server is all it does.

Is there a quick way to install a raft of forwards for BIND?

---

### Post by papibe on 2013-02-10
> **Vegan said:**
> I can connect to the hypervisor and see the console that way.

Of course. You're absolute right.

It is very simple to set up forwarding DNS. Check out the section called 'Caching Server configuration' in this [tutorial]("https://help.ubuntu.com/community/BIND9ServerHowto").

Let us know how it goes.
Regards.

---

### Post by Vegan on 2013-02-11
Simply uncomment and edit the following in"

```
sudo nano /etc/bind/named.conf.options
```

scroll down to

```

[...]

forwarders {
    1.2.3.4;
    5.6.7.8;
 };

[...]

```

add as many to the list as desired, I suggest adding your ISP servers as well as some extras

Google has 2 free to use DNS servers:

8.8.8.8
8.8.4.4

you can also find lots of other free server to act as forwards
this will boost your browsers like mad, no more waiting messages

:guitar:

I first tried this with Window Server where its also easy to add forwards, just that Linux is way less resource hungry. Windows DNS Server has a memory footprint of over 400 MB so the VM needs at least 1 GB to run efficiently.

Sure RAM is at all time lows, but when you need to run a few dozen virtual machines it does take its toll.

:D

---

### Post by Vegan on 2013-02-11
> **papibe said:**
> Hi Vegan.

That service will require very low requirements. You can go as low as the minimum system requirements for the server itself:
```
300 MHz x86 processor
128 MiB of system memory (RAM)
1 GB of disk space
```
Let us know how it goes.
Regards.

The 64-bit version crapped out with an out of memory error.

So I increased the RAM to 256 MB and it installs fine.

I allocated 2 logical processors so that the installer would be quicker.

---

### Post by Doug S on 2013-02-11
Yes, virtual machine installation requires more memory.
see: [https://bugs.launchpad.net/ubuntu/+source/lowmem/+bug/1050595](https://bugs.launchpad.net/ubuntu/+source/lowmem/+bug/1050595)
**[FONT=Courier][SIZE=1][FONT=Courier][SIZE=1][/SIZE][/FONT][/SIZE][/FONT]** 
[B][FONT=Courier][SIZE=1][FONT=Courier][SIZE=1] 
[/B][/SIZE][/FONT][/SIZE][/FONT]

---

### Post by Vegan on 2013-02-11
blasted thing crapped out with a connection refused 127.0.0.1$553

back to the old server, this looks like it may take a while

I can access this via the server, so no need to excess fluff like webmin etc

I googled the problem, nothing worked

I have to use the latest version as the LTS disk does not recognize the network adapter

---

