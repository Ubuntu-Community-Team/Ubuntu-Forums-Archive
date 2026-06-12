---
title: "Website directs to 127.0.0.1"
date: 2014-03-05
forum: Server Platforms
---

### Post by astarmathsandphysics on 2014-03-05
Obviously I don't want that.
I want it to direct to 111.90.150.93
How do I do this?

---

### Post by Lars Noodén on 2014-03-05
Can you give a little more detail as to what you do that leads up to the undesired results?

---

### Post by astarmathsandphysics on 2014-03-05
I had a server set up about 6 weeks ago.
#Now I have transferred some more moresites onto it and need to set up the nameservers to point to it. 

At the moment they points to 127.0.0.1

---

### Post by nerdtron on 2014-03-05
Please post the contents of /etc/hosts file.

---

### Post by guptesh on 2014-03-06
All you have to do is restart bind to clear its cache:
 
# /etc/init.d/named restart

 You can also use rndc command as follows flush out all cache:

 # rndc restart 

 OR
 
# rndc exec
 
BIND v9.3.0 and above will support flushing all of the records attached  to a particular domain name with rndc flushname command. In this  example flush all records releated to example.com domain:
 
# rndc flushname example.com
 
It is also possible to flush out BIND views. For example, lan and wan views can be flushed using the following command:
 
# rndc flush lan
 
# rndc flush wan

---

### Post by astarmathsandphysics on 2014-03-06
Here is etc/hosts

127.0.0.1	localhost
4545.6.7.21	server42.abc.com	server35

Virtual Hosts

234.54.6.46 	thexxxxxxxxxx.info

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

I was using external DNS and hadn't set up dns on my own server. Have done that now and am waiting for them to point the website. I may not have to deal with this until domain expires.

I am a bit confused here. Do I I need to install bind on my own server?

---

### Post by SeijiSensei on 2014-03-06
No, you can let the domain registrar maintain your records.  What matters are the A records that map from [www.example.com](www.example.com) to an IP address.

---

### Post by astarmathsandphysics on 2014-03-07
theexxxxxxxl.info does map to 111.90.150.92

You can see it at [http://111.90.150.92/theexxxxxxxxxl/](http://111.90.150.92/theexxxxxxxxxl/)

The server maps it to localhosr 127..0.0.1

---

