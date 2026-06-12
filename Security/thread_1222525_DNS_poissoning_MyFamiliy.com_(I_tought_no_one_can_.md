---
title: "DNS poissoning MyFamiliy.com (I tought no one can do this to linux)"
date: 2009-07-25
forum: Security
---

### Post by Ajat on 2009-07-25
Hi early this morning, while i was trying to open [www.kubuntu.com](www.kubuntu.com), something strange.. my browser didn't view my desire page, instead of viewing a pages titled MyFamily.com

I try ubuntuforums.org (it works) , but [www.coldplay.com](www.coldplay.com) also drives to MyFamily.com

some sites work, but many failed.

googling around, i found that it's DNS poisoning problem. a solution is doing cache flush..
unfortunately, i dont know how to cache flush in linux. I've tried to flush my iptables by typing ```
sudo iptables --flush
``` 

but the problem persist.

This is really annoying.. why this MyFamily.com do this? :confused:

any suggestions?

---

### Post by kerry_s on 2009-07-25
that would be an isp problem, if your using there dns through your router/modem. suggest using something like opendns.

[https://www.opendns.com/start/device/ubuntu](https://www.opendns.com/start/device/ubuntu)

---

### Post by Ajat on 2009-07-25
i'm surfing with my mobile modem, when i plug my phone, the interfaces usb0 is automatically established. 

network management doesnt give me any clue about how to edit usb0 connection. 

please help. 

is this Myfamily.com can be reported? I Hate that page.

---

### Post by aesis05401 on 2009-07-25
> **Ajat said:**
> i'm surfing with my mobile modem, when i plug my phone, the interfaces usb0 is automatically established. 

network management doesnt give me any clue about how to edit usb0 connection. 

please help. 

is this Myfamily.com can be reported? I Hate that page.

This is something you need to report to whoever runs the DNS server... probably the same company you pay for internet access.

---

### Post by Ajat on 2009-07-25
I think it has nothing to do with my internet provider..
there is a security article about this issue..

since google tells me that there are a lot of people experience the same problem.

it's funny to see

```

$nslookup www.coldplay
Server:         124.195.15.98
Address:        124.195.15.98#53

Non-authoritative answer:
Name:   www.coldplay.com
Address: 66.43.25.130

```or
```
$ nslookup www.kubuntu.com
Server:         124.195.15.100
Address:        124.195.15.100#53

Non-authoritative answer:
Name:   www.kubuntu.com
Address: 66.43.25.130

```and continuing investigating by using ```
$ whois 66.43.25.130

OrgName:    Myfamily.com, Inc.
OrgID:      MYFAMI-1
Address:    360 W. 4800 N.
City:       Provo
StateProv:  UT
PostalCode: 84604
Country:    US

NetRange:   66.43.16.0 - 66.43.31.255
CIDR:       66.43.16.0/20
NetName:    MYFAMILY
NetHandle:  NET-66-43-16-0-1
Parent:     NET-66-0-0-0-0
NetType:    Direct Assignment
NameServer: NS1.MYFAMILY.NET
NameServer: NS2.MYFAMILY.NET
Comment:
Comment:    &#65533;
RegDate:    2003-01-14
Updated:    2004-01-29

RTechHandle: DOMRE-ARIN
RTechName:   Domain Registration
RTechPhone:  +1-801-705-7000
RTechEmail:  domreg@tgn.com

OrgTechHandle: DOMRE-ARIN
OrgTechName:   Domain Registration
OrgTechPhone:  +1-801-705-7000
OrgTechEmail:  domreg@tgn.com
 
```bah.. 

see references
[http://ancestryinsider.blogspot.com/2008_01_01_archive.html](http://ancestryinsider.blogspot.com/2008_01_01_archive.html)

---

### Post by kerry_s on 2009-07-25
what they describe in part 3 there can not happen to you, unless your running your browser as root, as a normal user you do not have access to internet configs & those settings are not kept in your home folder. 

normally i would think you might have one of those bad firefox plugins, but the fact your getting it in terminal points to a problem else where. 

so the only way you can get a bad dns address is if your isp gives it to you. so as i have suggested please try not using there dns, try a different dns source.
[https://www.opendns.com/start/device/ubuntu](https://www.opendns.com/start/device/ubuntu)

---

### Post by SlugSlug on 2009-07-25
> **kerry_s said:**
> what they describe in part 3 there can not happen to you, unless your running your browser as root, as a normal user you do not have access to internet configs & those settings are not kept in your home folder. 

normally i would think you might have one of those bad firefox plugins, but the fact your getting it in terminal points to a problem else where. 

so the only way you can get a bad dns address is if your isp gives it to you. so as i have suggested please try not using there dns, try a different dns source.
[https://www.opendns.com/start/device/ubuntu](https://www.opendns.com/start/device/ubuntu)


+1 opendns

---

### Post by ericab on 2009-07-25
opendns for life dawg

---

### Post by Ajat on 2009-07-25
thanks for your share guys.

But as i said, i'm using a "hotplug" connection, which automatically create usb0 interfaces, i can't find this usb0 interfaces in /etc/network/interfaces.conf

should i just add the opendns nameserver in /etc/resolv.conf ?

please help.

thanks.

Edit: take a look for [http://www.omnicron.com/~ford/dnspoison.html](http://www.omnicron.com/~ford/dnspoison.html) (an article by Michael Ditto from sun microsystem engineer.)

hmm even when i get my DNS work with opendns, i would be interested to resolve this.

---

### Post by SlugSlug on 2009-07-25
> **Ajat said:**
> thanks for your share guys.

But as i said, i'm using a "hotplug" connection, which automatically create usb0 interfaces, i can't find this usb0 interfaces in /etc/network/interfaces.conf

should i just add the opendns nameserver in /etc/resolv.conf ?

please help.

thanks.

Edit: take a look for [http://www.omnicron.com/~ford/dnspoison.html](http://www.omnicron.com/~ford/dnspoison.html) (an article by Michael Ditto from sun microsystem engineer.)

hmm even when i get my DNS work with opendns, i would be interested to resolve this.

add these to the two files
/etc/dhcp3/dhclient
prepend domain-name-servers 208.67.222.222, 208.67.220.220; 

and 

/etc/resolv.conf
nameserver 208.67.222.222
nameserver 208.67.220.220

---

### Post by kerry_s on 2009-07-25
> **SlugSlug said:**
> add these to the two files
/etc/dhcp3/dhclient
prepend domain-name-servers 208.67.222.222, 208.67.220.220, 

and 

/etc/resolv.conf
nameserver 208.67.222.222
nameserver 208.67.220.220

you got a typo there "," should be ";":
prepend domain-name-servers 208.67.222.222, 208.67.220.220**;**

---

