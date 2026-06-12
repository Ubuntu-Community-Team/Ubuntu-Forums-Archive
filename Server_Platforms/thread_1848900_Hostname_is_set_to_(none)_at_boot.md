---
title: "Hostname is set to (none) at boot"
date: 2011-09-23
forum: Server Platforms
---

### Post by Evilware on 2011-09-23
LTSP, running 10.04.3

at boot the host is set to none
the contents of /etc/hostname

123-ltsp-nyc

the contents of my /etc/hosts


127.0.0.1       localhost.localdomain localhost
127.0.1.1       123-ltsp-nyc
10.20.27.253    123-ltsp-nyc


# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
~
##########
I can set the hostname manually, running hostname, but this only sticks till the device is rebooted. 

The bigger issue is clients show up on a who as ltsp(Number).local versus an ip address. 

Any insight or help on this would be appreciated.

---

### Post by SeijiSensei on 2011-09-26
If the machine gets its information from DHCP, it will ignore the local hostname definition and use the one the DHCP server gives it.  The best solution is to use [static addressing]("https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html"), but if you need to stick with DHCP, edit /etc/dhcp3/dhclient.conf and remove the "host-name" item from the "request" directive.

---

### Post by collisionystm on 2011-09-26
From this site [http://adminuser.wordpress.com/2008/02/10/change-hostname-permanently-on-debian-or-ubuntu/](http://adminuser.wordpress.com/2008/02/10/change-hostname-permanently-on-debian-or-ubuntu/)

Debian based systems use the file /etc/hostname to read the hostname of the computer at boot time and set it up using the init script /etc/init.d/hostname.sh

We can edit the file /etc/hostname and change the hostname and then run:

/etc/init.d/hostname.sh start

Steps:

1. sudo gedit /etc/hostname
 2. Save the file with the hostname you like to set
 3. sudo /etc/init.d/hostname.sh start

---

### Post by Evilware on 2011-09-26
The system is set to static ip, I did a force remove of dhcp3-client.

The system in question is running Ubuntu 10.04.3 LTS

the contents of /etc/hostname is what I want. however, there is no hostname.sh found in /etc/init.d/

there is a symbolic link to an upstart job in lib/init/ but that does not appear to set the hostname either

---

### Post by redmk2 on 2011-09-26
> **Evilware said:**
> The system is set to static ip, I did a force remove of dhcp3-client.

The system in question is running Ubuntu 10.04.3 LTS

the contents of /etc/hostname is what I want. however, there is no hostname.sh found in /etc/init.d/

there is a symbolic link to an upstart job in lib/init/ but that does not appear to set the hostname either

In your original post you say this is a thin client 10.04 LTSP (e.g Linux Terminal Server Project).  Is this a thin client of did you just mistype?

You are correct in that the system has changed since 2008.  Your system uses Upstart to initialize the system instead of the old SysV methods.  The sym-links are to try and preserve some continuity. 

So, Is this a fat or thin client we are dealing with?

---

### Post by Evilware on 2011-09-26
This is the actual server, the fat clients get the name of ltsp(somenumber).local.  I have the same setup and config running on multiple boxes and they all work correctly except for this one box.

---

### Post by redmk2 on 2011-09-26
> **Evilware said:**
> This is the actual server, the fat clients get the name of ltsp(somenumber).local.  I have the same setup and config running on multiple boxes and they all work correctly except for this one box.

Do you mean the thin clients?  Fat clients stand alone.  They have their own HDD to boot off of.  I'm confused (but not for the first time)  :-)

Usually .local domains are serviced by AVAHI (zeroconf).  Are you running AVAHI?

While not knowing anything in detail about LTSP, I am assuming, this is a configuration parameter somewhere.  How does this happen: *the fat clients get the name of ltsp(somenumber).local*?  What is the purpose of your server if there are no thin clients?

---

### Post by Evilware on 2011-09-27
Forgot I said anything about fatclients, this is the server. if it was a fat client issue, I would just rebuild the image and reboot the machines.. Heh


At this point I am not sure what it is. I went ahead and checked "avahi-daemon" which is running. I restarted the service to change the instance name from none.local to 123-ltsp-nyc.local

---

### Post by redmk2 on 2011-09-27
> **Evilware said:**
> Forgot I said anything about fatclients, this is the server. if it was a fat client issue, I would just rebuild the image and reboot the machines.. Heh


At this point I am not sure what it is. I went ahead and checked "avahi-daemon" which is running. I restarted the service to change the instance name from none.local to 123-ltsp-nyc.local

So this server is really Ubuntu desktop.  Was this host actually listed as *none.local*?  This makes no sense.  The hostname is defined by the /etc/hostname file.  The /etc/hosts file just maps the hostname to the IP address for that host.  I wonder what you get when you issue the command: *hostname* when initially booting the system.  How does restarting the service change the name?  Is this host stored as an image too?

It sure sounds like you are using AVAHI to configure the IP addressing and domain name (.local).  This is local LAN only and the addressing should be in the 169.254.0.0/24: useless for anything involving the internet.  I avoid AVAHI like the plague.

What is this: *10.20.27.253 123-ltsp-nyc*?  What are the IP addresses of your hosts on this network?

I would configure everything on the "server" statically (e.g via conf files).  That would put you in control.  This means all host naming and IP addressing.  Does this mean your images need updating?

---

### Post by Evilware on 2011-09-28
The server is a server, for pxeboot clients.

The class C block of the network is 10.20.27.0/24

The images are updated weekly to keep up with the latest patch

Yes everything is configured staticly on this server, this is only one server of many, and its the only one that has this issue. 

this is one of those things that has perplexed me, as it does not make sense that the hostname is correct in /etc/hostname and yet it boots with (NONE) as a label after reboot

---

