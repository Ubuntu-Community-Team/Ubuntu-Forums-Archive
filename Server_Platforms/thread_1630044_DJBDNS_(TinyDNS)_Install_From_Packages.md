---
title: "DJBDNS (TinyDNS) Install From Packages"
date: 2010-11-24
forum: Server Platforms
---

### Post by starlily on 2010-11-24
I love DJBDNS. Its fast and secure, and superior to BIND in many ways, imho. 

There are Ubuntu packages for it, but little or no clear documentation on how to install them successfully. Until now. 

I present to you; the super simple DJBDNS Install From Packages Instructions. This will install a DNS NAMESERVER (not a cache). 

You will need to be root for this. 
 
First, install the packages:
```
apt-get install daemontools
apt-get install daemontools-run
apt-get install ucspi-tcp
apt-get install djbdns
```

Then, add the necessary user accounts:
```
adduser --no-create-home --disabled-login --shell /bin/false dnslog
adduser --no-create-home --disabled-login --shell /bin/false tinydns
```

Configuration. 
 Step 1: 
```
tinydns-conf tinydns dnslog /etc/tinydns/ EXTERNAL.IP.ADDRESS
```(where EXTERNAL.IP.ADDRESS == your internet IP)

 Step 2: 
```
mkdir /etc/service ; cd /etc/service ; ln -sf /etc/tinydns/
```

Start it: ```
initctl start svscan
```

Check it: ```
svstat /etc/service/tinydns
```
Stop it: ```
svc -d /etc/service/tinydns
```
Start it: ```
svc -u /etc/service/tinydns
```

Now you just need to set up your records. This URL will tell you how: [http://cr.yp.to/djbdns/tinydns-data.html](http://cr.yp.to/djbdns/tinydns-data.html)

---

### Post by qbitza on 2010-11-29
This is awesome \\:D/

Now we just need a qmail one, and we're set!

---

### Post by phaidros on 2011-02-07
nice one! thanks

:popcorn:

---

