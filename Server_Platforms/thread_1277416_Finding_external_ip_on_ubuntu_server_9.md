---
title: "Finding external ip on ubuntu server 9"
date: 2009-09-28
forum: Server Platforms
---

### Post by interceptor84 on 2009-09-28
Hello,

I've been doing some research and cannot seem to find out how to determine my external ip address of my ubuntu server. i need to know this information for openvpn access. any help would be great thanks.

---

### Post by openfly on 2009-09-28
[www.whatismyip.com](www.whatismyip.com)

ifconfig -a

---

### Post by smeerbartje on 2009-09-28
And the nerdy way: [click]("http://www.askdavetaylor.com/how_do_i_figure_out_my_ip_address_on_a_mac.html") :D

---

### Post by i.r.id10t on 2009-09-28
```

 wget -O - http://checkip.dyndns.org | cut -f 2 -d \: | cut -f 1 -d \<

```

---

### Post by cdenley on 2009-09-28
```

wget -q -O - http://whatismyip.org/ && echo

```

---

### Post by interceptor84 on 2009-09-28
thank you all, for the help!!!

---

