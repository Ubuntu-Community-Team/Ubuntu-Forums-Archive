---
title: "UFW Cofiguration?"
date: 2010-01-10
forum: Security
---

### Post by running_rabbit07 on 2010-01-10
Does UFW need to be configured? I used GUFW and noticed it showed no rules for anything. Is this normal or do I need to make adjustments before it will truly block anything?

Thanks

---

### Post by cariboo on 2010-01-10
It depends on what you want it to do, you have to enable ufw, before it will do anything. In a terminal type:

```
sudo ufw enable
```

Once you have enabled it, you can use GUFW to adjust the rules.

---

### Post by adam814 on 2010-01-10
GUFW also shows what the default behavior is.  If the default is "deny" and it's enabled it's blocking everything (inbound) until you set up rules allowing things.

---

### Post by timzak on 2010-01-10
I've found the only allow exception I needed to make is for my internal home network.  Otherwise it runs just fine on the default deny setting.  I'm not sure what the difference is between what I did and allowing Samba shares, though.

---

### Post by running_rabbit07 on 2010-01-10
> **adam814 said:**
> GUFW also shows what the default behavior is.  If the default is "deny" and it's enabled it's blocking everything (inbound) until you set up rules allowing things.
> **timzak said:**
> I've found the only allow exception I needed to make is for my internal home network. Otherwise it runs just fine on the default deny setting. I'm not sure what the difference is between what I did and allowing Samba shares, though.

I guess this was what I am looking for. Being it showed no arguments or inputs, I didn't know if it was blocking everything or nothing. 

Now with that answered, how do I add exceptions?  Do I just add the IP of the connection I want to allow or is it more complicated than that.

Thanks

---

### Post by adam814 on 2010-01-10
You can specify as little or as much as you need.  I suppose the minimum would be specifying a port you wanted accessible from anywhere (if you were running a web server, for torrent uploads, or maybe ssh).  You could also specify the protocol(tcp/udp/both) and IP addresses and ports for source and destination.

I think you're supposed to be able to specify more complicated (iptables) rules in /etc/ufw/before.rules since UFW is just a front-end to iptables anyway.

---

### Post by bodhi.zazen on 2010-01-11
[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)

There are additional blog entries on UFW , both for desktops and servers.

---

### Post by running_rabbit07 on 2010-01-11
> **bodhi.zazen said:**
> [http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)

There are additional blog entries on UFW , both for desktops and servers.

I am definitely going to have to take time to go through all of your blogs. You have some really great information there. I hope you are getting paid well for all that knowledge by whomever you are working for.

---

