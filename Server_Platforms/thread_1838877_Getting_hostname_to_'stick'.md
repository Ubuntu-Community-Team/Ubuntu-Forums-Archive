---
title: "Getting hostname to 'stick'"
date: 2011-09-04
forum: Server Platforms
---

### Post by Habitual on 2011-09-04
Hello Community:

We have a hardy instance up at AWS, that we cannot get the hostname to stick.

I have set hostname (cirrhus9a) and rebooted.
I have set /etc/hosts and upon reboot, I get ip-10-250-102-102.ec2.internal for the hostname (hostname -f)
I have edited /etc/hostname and that reflects our desired hostname (cirrhus9a)

Here's our relevant files:
/etc/hosts
127.0.0.1 localhost.localdomain.localhost
10.250.6.191 ip-10-250-6-191.ec2.internal cirrhus9a

/etc/hostname
cirrhus9a

/etc/resolv.conf
search ec2.internal
nameserver 172.16.0.23

**Curious**...
```
/etc/init.d/networking restart
```
"suspect value in server_name option - discarded"

/etc/sysconfig does NOT exist?

[http://ubuntuforums.org/showthread.php?t=1325579](http://ubuntuforums.org/showthread.php?t=1325579) suggests removing domain-name and host-name from the requests section of
/etc/dhcp3/dhclient.conf which I have done, but it made no difference.

any guidance on setting a persistent hostname would be greatly appreciated.

---

### Post by papibe on 2011-09-04
Could you post your /etc/host.conf and /etc/nsswitch.conf also?

Regards.

---

### Post by papibe on 2011-09-04
After a second look, I may have an idea.

If you are getting this name after boot: ip-10-250-102-102.ec2.internal it means that you are getting that IP as DHCP lease (10.250.102.102). Is that right?

Then that will conflict with the line you have on /etc/hosts:
```
10.250.6.191 ip-10-250-6-191.ec2.internal cirrhus9a
```
that basically assume either an static IP or DHCP reservation.

Just some thoughts,
Regards.

---

### Post by Habitual on 2011-09-04
papibe:

Thanks for taking the time to help.

The non-routable IP (10.x.x.x) will change regularly as I shut down this instance when I am not working on it. We are in the process of installing Zimbra CS 7.x.x and then migrate our zimbra data (6.x.x) to this new machine, which will become our new mail server).

It does have a fixed Elastic IP associated with the instance - 107.20.181.212 and an A Record assigned to that.
```
host cirrhus9a.cirrhus9.com
``` This does not change (at least now, it stays the same). 

/etc/host.conf
```
# The "order" line is only used by old versions of the C library.
order hosts,bind
multi on

```

/etc/nsswitch.conf 
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

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```

Subscribed with interest.

Thank you for your time.

---

### Post by papibe on 2011-09-04
After a few searches, this is what I think:

It looks like it is VERY important that the address 127.0.0.1 resolves to localhost, no matter what. See [this]("http://lists.debian.org/debian-devel/2005/10/msg00559.html") in the Debian mail list.

With that in mind, the correct /etc/hosts should be something like:
```
127.0.0.1   localhost  localhost.localdomain 
```
Let's know how it goes.
Regards.

---

### Post by Habitual on 2011-09-04
papibe:

But it is already defined there.
```
127.0.0.1 localhost.localdomain.localhost
10.250.6.191 ip-10-250-6-191.ec2.internal cirrhus9a

```

on our cirrhus9b box the /etc/hosts shows:
```
127.0.0.1 localhost.localdomain localhost
127.0.1.1 cirrhus9b.cirrhus9.com cirrhus9b
```

to which I have tried the same entry (subbing a for b)

and it sticks on the c9b host there, however, it's uptime exceeds my tenure at this job. But the boss assures me he had to "do" "something" to get the hostname to stick there also.

Thanks.

---

### Post by papibe on 2011-09-04
I think that could be your answer. Have you tried:
```
127.0.0.1 localhost.localdomain localhost
127.0.1.1 cirrhus9a
```
That is a double entry for the local host.

EDIT: Note that I'm replacing the last dot for a space as in hosts for cirrhus9b.

---

### Post by Habitual on 2011-09-04
> **papibe said:**
> I think that could be your answer. Have you tried:
```
127.0.0.1 localhost.localdomain localhost
127.0.1.1 cirrhus9a
```


did not work.

Thanks for your tenacity. :)

---

### Post by Entilza on 2011-09-04
Can we see /etc/network/interfaces

So you are getting the IP on DHCP temporarily?

---

### Post by Habitual on 2011-09-04
Yes, you can see /etc/network/interfaces
but it will have to be "tomorrow". (about 10 hours from now)

Thank you for your time.

---

### Post by Habitual on 2011-09-05
/etc/network/interfaces
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp


```

Thank you.

---

### Post by SwitchLink on 2011-09-05
Is your DHCP server sending a hostname to the client?

---

### Post by Habitual on 2011-09-05
/etc/dhcp3/dhclient.conf
```
/# Configuration file for /sbin/dhclient, which is included in Debian's
#	dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#	man page for more information about the syntax of this file
#	and a more comprehensive list of the parameters understood by
#	dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#	not leave anything out (like the domain name, for example), then
#	few changes must be made to this file, if any.
#

send host-name cirrhus9a;
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name-servers,
	netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
timeout 30;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}
```

Thank you.

---

### Post by Entilza on 2011-09-05
Do you need the dhcp to send the host name?

---

### Post by Habitual on 2011-09-05
Entilza:

IDK what AWS "needs" to do for this situation.

This topic is now closed, I cannot afford to "guess" any further.

---

