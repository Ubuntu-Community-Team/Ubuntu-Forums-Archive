---
title: "DNS Problems (resolv.conf)"
date: 2006-07-23
forum: Server Platforms
---

### Post by nemodx on 2006-07-23
Hi all,

A while ago, I decided that I should try the ubuntu server instead of debian, which actually to my surprise worked super nice. So I have put it on my production server.

However I have a problem with my dhcp server overwriting my resolv.conf with stuff that I dont want to have in there.

on my old debian server, I would simply write the following lines info /etc/dhclient-script:

```
  make_resolv_conf() {
    echo "search mydomain.com" >/etc/resolv.conf
    for nameserver in $new_domain_name_servers; do
      echo "nameserver 10.10.10.10" >>/etc/resolv.conf
 done

```

Where mydomain.com is my domain, and namserver is the ip that I want in there.

That however, doesnt seem to work on ubuntu server.

I have also tried to modify the dhclient.conf file with a supersede line, and that didnt work either.

Even when adding a /etc/dhclient-enter-hooks with the following lines:

```
make_resolv_conf() {
        echo "doing nothing to resolv.conf"
}

```
nothing happens :(

Can someone help me out here? What is the diffrence between debians behaviour and ubuntu's on this?

Im greatful for ANY hints or help I can get on this matter.

Thanks!

Nemo

---

### Post by nemodx on 2006-07-23
Oke, the diffrence being that the dhclient-script is now in /etc/dhcp3/

Edited the file, and it works like a charm again! Sorry for wasting peoples time. Maybe someone else has the same problem one day, and this post might then come handy :)

---

