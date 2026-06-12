---
title: "Block Pinging with GUFW"
date: 2010-01-25
forum: Security
---

### Post by Silvertones on 2010-01-25
I did one of the  recommended port scans and all ports passed but failed on pinging. How do you turn pinging on & off with GFUW?

---

### Post by cdenley on 2010-01-25
[https://answers.launchpad.net/ufw/+question/26585](https://answers.launchpad.net/ufw/+question/26585)

---

### Post by Silvertones on 2010-01-25
Info not clear to me as what to do.

---

### Post by CharlesA on 2010-01-25
Open a terminal window and type:

```
gksudo gedit /etc/ufw/before.rules
```

Find the string that says "-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT" and put a # in front of it. Save and restart UFW.

EDIT: If you don't want your network to respond to pings, and you are behind a  router, you would need to set the router to not respond to ping requests.

---

### Post by bodhi.zazen on 2010-01-25
See also : 

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

There is an entire section on ping on the wiki page.

---

### Post by cdenley on 2010-01-25
```

gksu gedit /etc/ufw/before.rules

```

Add the red "#":
```

# ok icmp codes
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j ACCEPT
-A ufw-before-input -p icmp --icmp-type source-quench -j ACCEPT
-A ufw-before-input -p icmp --icmp-type time-exceeded -j ACCEPT
-A ufw-before-input -p icmp --icmp-type parameter-problem -j ACCEPT
[COLOR="Red"]**#**[/COLOR]-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT

```

Save, close, reboot.

---

### Post by Silvertones on 2010-01-25
Thanks. It's very clear however it doesn't appear that there's anything to gain by disabling pinging.

---

### Post by bodhi.zazen on 2010-01-25
> **Silvertones said:**
> Thanks. It's very clear however it doesn't appear that there's anything to gain by disabling pinging.

With modern cracking techniques ,  not much benefit at all.

---

### Post by dogdo on 2010-01-26
> **bodhi.zazen said:**
> With modern cracking techniques ,  not much benefit at all.

Elaborate-what techniques?

I have connect via wireless- i have the router set to not to respond to pings but the gufw firewall does respond to pings-do i have anything to gain from disabling gufw pinging?

---

### Post by CharlesA on 2010-01-26
Google can probably give you the answer, as I am not sure we are allowed to talk about it here.

---

### Post by bodhi.zazen on 2010-01-26
> **dogdo said:**
> Elaborate-what techniques?

I have connect via wireless- i have the router set to not to respond to pings but the gufw firewall does respond to pings-do i have anything to gain from disabling gufw pinging?

This site is for Ubuntu support and we strongly discourage cracking on these forums, even as "proof of concept" discussions.

If you are interested, google will help you find various sites, white hat, grey hat, and black hat.

You could also look at DVL

[http://www.damnvulnerablelinux.org/](http://www.damnvulnerablelinux.org/)

---

