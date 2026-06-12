---
title: "How to make sure ufw works?"
date: 2016-04-10
forum: Server Platforms
---

### Post by mbnoimi on 2016-04-10
Hi,

I blocked some IPs using ufw as following because I discovered some illegal access attempts:

```
#ufw deny from 104.223.xxx.xxx
#ufw enable
#ufw status
Status: active
.
.
Anywhere                   DENY                   104.223.xxx.xxx
.
.
#
```

Everything seems fine but when I took a look in MySQL log I can see a new attemps for accessing MySQL as following:

```
2016-04-10T01:42:21.831316Z 7461 [Note] Access denied for user 'admin'@'104.223.xxx.xxx' (using password: YES)
```

How to make sure that ufw blocked 104.223.xxx.xxx for good?

---

### Post by Habitual on 2016-04-10
```
sudo ufw deny mysql
``` and then possibly an explicit for known hosts

See [https://help.ubuntu.com/community/UFW#Services](https://help.ubuntu.com/community/UFW#Services) and
[https://help.ubuntu.com/community/UFW#Allow_Access](https://help.ubuntu.com/community/UFW#Allow_Access)

---

### Post by mbnoimi on 2016-04-10
> **Habitual said:**
> ```
sudo ufw deny mysql
``` and then possibly an explicit for known hosts

See [https://help.ubuntu.com/community/UFW#Services](https://help.ubuntu.com/community/UFW#Services) and
[https://help.ubuntu.com/community/UFW#Allow_Access](https://help.ubuntu.com/community/UFW#Allow_Access)

I'm unable to block whole mysql service then add the known hosts because many users access mysql through ISP proxy so their IPs frequently changes.

---

### Post by MAFoElffen on 2016-04-10
From the [Ubuntu UFW Wiki]("https://help.ubuntu.com/community/UFW"):
> 
Checking the status of ufw will tell you if ufw is enabled or disabled and also list the current ufw rules that are applied to your iptables.

To check status:
```

sudo ufw status

```
*** Which you did and it showed the correct rule saying it was blocking that. What is curious is that if the firewall "IS" blocking that IP, on all port, protocols and to all apps.... Then shouldn't stop all incoming from that IP before it gets to an application such as MySQL (port 3306)?

---

### Post by Graham_Willis on 2016-04-14
I confirm that ufw behaves in the way which is not expected (the only changes in allowing/denying the traffic was if I changed default policy, which means that it is possible to block/allow exclusively connections incoming/outgoing   from all IP addresses globally, no way to block/allow connections from specific IPs, I read the manual and tried various combinations but with no luck). However, you may choose to block the rogue IP address directly with iptables:

iptables -A INPUT -s 104.223.xxx.xxx -j DROP

Remember to be very careful when working with the firewall, though (for example, if you cut off all the traffic and have neither easy and fast access to the physical machine nor a person who could do that quickly for you, then you'll cause a serious downtime).

---

### Post by mbnoimi on 2016-04-15
> **Graham_Willis said:**
> I confirm that ufw behaves in the way which is not expected (the only changes in allowing/denying the traffic was if I changed default policy, which means that it is possible to block/allow exclusively connections incoming/outgoing   from all IP addresses globally, no way to block/allow connections from specific IPs, I read the manual and tried various combinations but with no luck). However, you may choose to block the rogue IP address directly with iptables:

iptables -A INPUT -s 104.223.xxx.xxx -j DROP

Remember to be very careful when working with the firewall, though (for example, if you cut off all the traffic and have neither easy and fast access to the physical machine nor a person who could do that quickly for you, then you'll cause a serious downtime).

I may discovered the problem. 

I think ufw works fine on ipv4 so some attack attempts come from ipv6 for that I see failed access attempts. Now I'm adding some rules for ipv6 as following hope this block hacking attempts:

```
ufw deny proto ipv6 from 104.223.xxx.xxx
```

---

### Post by Habitual on 2016-04-15
> **mbnoimi said:**
> I may discovered the problem. 

I think ufw works fine on ipv4 so some attack attempts come from ipv6 for that I see failed access attempts. Now I'm adding some rules for ipv6 as following hope this block hacking attempts:

```
ufw deny proto ipv6 from 104.223.xxx.xxx
```
Good catch if that's "it".
I never think in IPv6 :(

---

### Post by mbnoimi on 2016-04-16
> **mbnoimi said:**
> I may discovered the problem. 

I think ufw works fine on ipv4 so some attack attempts come from ipv6 for that I see failed access attempts. Now I'm adding some rules for ipv6 as following hope this block hacking attempts:

```
ufw deny proto ipv6 from 104.223.xxx.xxx
```

That's it guys. After enabling ufw over ipv6 I'm no longer see the stupid spammer.

---

