---
title: "Limit ssh access to local hosts"
date: 2009-06-26
forum: Security
---

### Post by WitchCraft on 2009-06-26
Question:

At the moment, I disabled ssh password login in the sshd config of my server (using 4096 RSA authentication instead).

Now I want to autorize ssh access via password, but only for a subset of the local IP range: 192.168.1.2 to 192.168.1.10
or at least to 
192.168.1.*

How can I limit ssh password login in sshd to be only allowed for this/these IP range/s?
For Public IP ranges, I want to keep RSA.

---

### Post by brian_p on 2009-06-26
> **WitchCraft said:**
> 

How can I limit ssh password login in sshd to be only allowed for this/these IP range/s?
For Public IP ranges, I want to keep RSA.

You could run two instances of sshd.

---

### Post by HermanAB on 2009-06-26
...and use iptables to allow only the LAN or specific IP addresses to port 22 or port 2222 for your two instances of sshd.

---

### Post by Rob_H on 2009-06-26
> **HermanAB said:**
> ...and use iptables to allow only the LAN or specific IP addresses to port 22 or port 2222 for your two instances of sshd.

And if you're not comfortable with setting up iptables from scratch, you might want to use [ufw]("https://help.ubuntu.com/9.04/serverguide/C/firewall.html"), which comes with Jaunty. Much less intimidating in my opinion. ;-)

---

### Post by brian_p on 2009-06-26
> **HermanAB said:**
> ...and use iptables to allow only the LAN or specific IP addresses to port 22 or port 2222 for your two instances of sshd.

Or set up one of the sshd config files to recognise only LAN users.

---

### Post by bodhi.zazen on 2009-06-26
Or use host-based authentication.

[http://users.telenet.be/mydotcom/howto/linux/sshpasswordless.htm](http://users.telenet.be/mydotcom/howto/linux/sshpasswordless.htm)

---

### Post by DGortze380 on 2009-06-27
yet another option

/etc/hosts.allow

add sshd as the service, all (your ip range)

/etc/hosts.deny

add sshd as the service, deny all

---

### Post by scorp123 on 2009-06-27
> **WitchCraft said:**
>  Now I want to autorize ssh access via password, but only for a subset of the local IP range: 192.168.1.2 to 192.168.1.10
or at least to 
192.168.1.*
 As someone already wrote, you could work with these files:
[LIST]
[*]/etc/hosts.allow
[*]/etc/hosts.deny
[/LIST]

There is a nice tutorial written by our Debian-brothers:
[http://www.debian-administration.org/article/Keeping_SSH_access_secure](http://www.debian-administration.org/article/Keeping_SSH_access_secure)

---

