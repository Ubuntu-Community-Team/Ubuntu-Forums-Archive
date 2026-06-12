---
title: "Open Ports"
date: 2010-05-27
forum: Security
---

### Post by oshirowanen on 2010-05-27
Dear Community,

How do I find out which ports are open on a standard installation of Ubuntu 10.04?

---

### Post by Rubi1200 on 2010-05-27
> **oshirowanen said:**
> Dear Community,

How do I find out which ports are open on a standard installation of Ubuntu 10.04?

By default, Ubuntu does not ship with open ports. However, cups (the printing service) will be listed as LISTENING.

Run the following to find out what is happening on your system:

sudo lsof -i -n -P

Also, visit the GRC ShieldsUP website and test for open ports.

As I said, only cups should be listed as listening unless you are running something like vnc or ssh, in which case read this:

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by Soul-Sing on 2010-05-27
on a clean 10.4 avahi and cups should give you some "results".

---

### Post by Joe of loath on 2010-05-27
Install nmap, then scan localhost. My machine simply has CUPS open.

---

### Post by cdenley on 2010-05-27
Technically, avahi and dhclient have open UDP ports, but they aren't really a concern. Cups only listening on 127.0.0.1, so it can't be connected to remotely. Port scanners such as nmap aren't the best way to check for open ports, since they typically only check commonly used ports and UDP ports are difficult to probe reliably. It is better to check with this command:
```

sudo netstat -tulnp

```
since that will check for all listening processes instead of probing ports, and even lists the name and PID of the process. However, some malware which listens for network connections can hide itself from netstat's output.

---

### Post by rookcifer on 2010-05-27
> **cdenley said:**
>  Port scanners such as nmap aren't the best way to check for open ports, since they typically only check commonly used ports 

Not true.  Nmap can check all 65535 TCP and UDP ports if you pass the right flags to it.  One can use a command like this:

```
nmap -sT -sU **-p-** <ip addy>
```

This will scan all possible TCP and UDP ports.  In the above example, the "-p-" flag is left blank, which means it will default to scanning all ports.  If you don't specify a -p- flag, it will only scan like a couple thousand service ports (not sure the exact number but it doesn't scan them all).  Of course, if you want to get an accurate result you need to scan the machine from outside the firewall or NAT.

Nmap is a very sophisticated port scanner with the ability to stealth scan, connect scan, X-mas tree, decoy scanning, spoof the source, etc..  It is pretty much the industry standard with a number of clones.  man nmap for more info.

But I will agree that nmap isn't the best way to simply check what you have open on the machine (assuming the machine has not been compromised or rootkitted).  It's simpler to just run netstat or lsof.

---

### Post by cdenley on 2010-05-27
> **rookcifer said:**
> Not true.  Nmap can check all 65535 TCP and UDP ports if you pass the right flags to it.

I said **typically**. As in with the default options. Also, I still don't think it could probe UDP ports well since it is a connectionless protocol. It is very useful for probing remote servers, but netstat is much better if you have local access.

---

### Post by bodhi.zazen on 2010-05-27
> **rookcifer said:**
> If you don't specify a -p- flag, it will only scan like a couple thousand service ports (not sure the exact number but it doesn't scan them all). 

I think the default is just 1024, the "privileged" ports.

I would +1 all these suggestions, nmap is nice, as is lsof as is netstat


```
netstat -an | grep LISTEN | grep -v ^unix
netstat -ntulp
lsof -i -n -P 
nmap -v -A -PN ip_address
```

Use zenmap if you wish a graphical interface for nmap.

Use the additional nmap flags " -sT -sU -p- " if you want a "full" port scan.

IMO losf is nice for new users as it gives information as to which service is using the open port.

---

