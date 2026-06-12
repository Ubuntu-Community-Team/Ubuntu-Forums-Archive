---
title: "/etc/hosts ignored"
date: 2008-12-07
forum: Server Platforms
---

### Post by kdad on 2008-12-07
This is the first Ubuntu problem I've had to post a question about.  It's got me stumped.  I'm running Ubuntu server 8.04 and it seems to be ignoring my /etc/hosts file.  I also have a Kubuntu desktop system that has no problem using it's /etc/hosts file.

/etc/hosts from the server (192.168.0.110):

```
127.0.0.1       localhost
192.168.0.110   titan

192.168.0.103   bearcat

```

From the server I can ping localhost, but not titan or bearcat ( I get an unkown host error)

I understand the /etc/nsswitch.conf file can control the use of /etc/hosts but it seems good to me:

```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files dns
networks:       files

protocols:      files
services:       files
ethers:         files
rpc:            files

netgroup:       nis
```

What could the problem be?

---

### Post by stiV on 2008-12-09
how does your /etc/resolv.conf look like? are you using a local dns cache (like dnsmasq)?

---

### Post by Krupski on 2008-12-09
> **kdad said:**
> This is the first Ubuntu problem I've had to post a question about.  It's got me stumped.  I'm running Ubuntu server 8.04 and it seems to be ignoring my /etc/hosts file.  I also have a Kubuntu desktop system that has no problem using it's /etc/hosts file.

/etc/hosts from the server (192.168.0.110):

```
127.0.0.1       localhost
192.168.0.110   titan

192.168.0.103   bearcat

```

From the server I can ping localhost, but not titan or bearcat ( I get an unkown host error)


What could the problem be?

Are the IP addresses correct? Usually, private Intranet (LAN) addresses are assigned via DHCP and they can change.

Another thing... how did you create the hosts file? Does it have DOS/Windows carriage returns in it?

It has to be in UNIX format (linefeeds only).

Lastly... it is located at "/etc/hosts"? And are it's permissions set properly (chmod 0644 /etc/hosts) which looks like "-rw-r--r--"?

-- Roger

---

### Post by MJN on 2008-12-09
Another few things things worth checking:

1. That your /etc/host.conf resolver config file contains a reference to the hosts file:

```
order hosts,bind
```2. Add an additional reference to 127.0.0.1 in /etc/hosts and trying pinging the new entry:

```
127.0.0.1 localhost test
``````
ping test
```3. Make sure there is a blank line at the end of the file (HOSTS files were historically notorious for not working properly without one).

Mathew

---

### Post by kdad on 2008-12-10
> **stiV said:**
> how does your /etc/resolv.conf look like? are you using a local dns cache (like dnsmasq)?

Here is my /etc/resolv.conf:
```

search san.rr.com
nameserver 66.75.160.63
nameserver 66.75.160.64

```

I never setup a local dns cache unless it's there in the default install.  ps -A | grep dns shows nothing like that.

---

### Post by kdad on 2008-12-10
> **Krupski said:**
> Are the IP addresses correct? Usually, private Intranet (LAN) addresses are assigned via DHCP and they can change.

Another thing... how did you create the hosts file? Does it have DOS/Windows carriage returns in it?

It has to be in UNIX format (linefeeds only).

Lastly... it is located at "/etc/hosts"? And are it's permissions set properly (chmod 0644 /etc/hosts) which looks like "-rw-r--r--"?

-- Roger

Yes the IP addresses are correct.  I have my router set to always give the same IPs to the same MAC addresses.

The /etc/hosts file was created by editing the default file after install.  I use vim.  I'm sure it's in UNIX format.

The permissions are 0644.

---

### Post by kdad on 2008-12-10
> **MJN said:**
> Another few things things worth checking:

1. That your /etc/host.conf resolver config file contains a reference to the hosts file:

```
order hosts,bind
```2. Add an additional reference to 127.0.0.1 in /etc/hosts and trying pinging the new entry:

```
127.0.0.1 localhost test
``````
ping test
```3. Make sure there is a blank line at the end of the file (HOSTS files were historically notorious for not working properly without one).

Mathew


1.  my /etc/host.conf:
```
# The "order" line is only used by old versions of the C library.
order hosts,bind
multi on

```

2. changed /etc/host.conf as suggested:
```

127.0.0.1       localhost test
192.168.0.110   titan

192.168.0.103   bearcat



```

can't ping test either:
```
jason@titan:~$ ping test
ping: unknown host test

```

3.  Added several blank lines to end of /etc/hosts but no change.....

---

### Post by MJN on 2008-12-10
I'm running out of ideas. Have you tried deleting your current hosts file and recreating from scratch?
 
Mathew

---

### Post by croo on 2009-09-27
I have the same issue with 9.04 did you ever find the solution?
I can always use DNS but it's a pain for temp changes to test something.

---

### Post by kdad on 2009-09-28
Never found a solution.  Later I bought an iPhone.  I couldn't access it's /etc/hosts file (before I jailbroke it) so I decided to setup DNS on my server.  As I started to install BIND, I found it was already installed and running.  That surprised me since it is not installed on any of my desktop ubuntu machines.  It does make sense for a server though.  I assume it was BIND that was preventing my /etc/hosts file from being used.  Since I needed to setup DNS anyway, I never looked into it further.

---

