---
title: "echo 1 &gt; /proc/sys/net/ipv4/ip_forward"
date: 2006-12-23
forum: Server Platforms
---

### Post by mayonaise15 on 2006-12-23
```
echo 1 > /proc/sys/net/ipv4/ip_forward
```

Is there any way to make that permanent?

This machine is only being used as an OpenVPN server, no GUI to put it into System -> Sessions.

---

### Post by kidders on 2006-12-23
Hi there,

You can add **net.ipv4.conf.default.forwarding=1** to your /etc/sysctl.conf. That should do the trick.

---

### Post by mayonaise15 on 2006-12-23
I'm not brave enough to put that line in and reboot the server over SSH, so I will have to wait a few days to see if that actually worked.  Regardless of that, thanks for the reply kidders.

---

### Post by kidders on 2006-12-23
Hehe I can understand that!

Other than waiting until you're physically sitting in front of the box, you could take the precautionary measure of adding a cron job that would execute **echo "1" > /proc/sys/net/ipv4/ip_forward** as root every half hour, and *then* reboot. That way, there would only be a brief period of inaccessibility if my suggestion fails.

The only reason I suggest it is that, should you have a power failure, your machine could reboot unexpectedly before you get to it.

---

### Post by ashrack on 2007-04-22
> **kidders said:**
> Hi there,

You can add **net.ipv4.conf.default.forwarding=1** to your /etc/sysctl.conf. That should do the trick.
This doesn't work for me I must still do it the manual way every boot since it still doesn't enable it after reboot:
```
root@ubuntu:~# cat /proc/sys/net/ipv4/ip_forward 
0

```
```
#
# /etc/sysctl.conf - Configuration file for setting system variables
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com
#net/ipv4/icmp_echo_ignore_broadcasts=1

# the following stops low-level messages on console
kernel.printk = 4 4 1 7

##############################################################3
# Functions previously found in netbase
#

# Uncomment the next line to enable Spoof protection (reverse-path filter)
#net.ipv4.conf.default.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.conf.default.forwarding=1

# Uncomment the next line to enable packet forwarding for IPv6
#net.ipv6.conf.default.forwarding=1

```
What could be the problem?

---

### Post by kidders on 2007-04-22
Hi ashrack,

Now that you mention it, I can reproduce this on Feisty too. I have no explanation. :confused:

Give **net.ipv4.conf.all.forwarding=1** a try, and see what happens.

---

### Post by ashrack on 2007-04-22
> **kidders said:**
> Hi ashrack,

Now that you mention it, I can reproduce this on Feisty too. I have no explanation. :confused:

Give **net.ipv4.conf.all.forwarding=1** a try, and see what happens.

with this line it works. 
Please add your name to the launchpad bug report and also any other ppl who have this problem:
[https://bugs.launchpad.net/ubuntu/+bug/108896](https://bugs.launchpad.net/ubuntu/+bug/108896)

---

### Post by kidders on 2007-04-22
> **ashrack said:**
> [https://bugs.launchpad.net/ubuntu/+bug/108896](https://bugs.launchpad.net/ubuntu/+bug/108896)I've seen issues similar to this posted elsewhere in Launchpad. Technically, this is a feature ... not a bug.

---

### Post by ashrack on 2007-04-23
what kind of a feature, what is this feature suppose to do?*

---

### Post by kidders on 2007-04-23
> **ashrack said:**
> what kind of a feature, what is this feature suppose to do?*

**net.ipv4.conf.default.forwarding** only affects interfaces that haven't been initialised yet, so whether it does anything depends on the order in which things happen during boot-up. **net.ipv4.conf.all.forwarding** is not the same thing, so I'm guessing that a bug report that suggests that they *should* be will just get closed.

---

