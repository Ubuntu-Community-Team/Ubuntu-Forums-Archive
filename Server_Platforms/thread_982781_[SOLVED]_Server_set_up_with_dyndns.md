---
title: "[SOLVED] Server set up with dyndns"
date: 2008-11-15
forum: Server Platforms
---

### Post by andydurham on 2008-11-15
Hi guys

Apologies if theres another post on this that ive missed but im a little confused.  My ISP wont provide a static IP address for me so Im having to use dyndns site name.  However I'm following this guide

[http://www.howtoforge.org/perfect-server-ubuntu-8.10-p3](http://www.howtoforge.org/perfect-server-ubuntu-8.10-p3)

**When it gets to this part:**

then edit /etc/hosts. Make it look like this:

vi /etc/hosts

127.0.0.1       localhost.localdomain   localhost
192.168.0.100   server1.example.com     server1

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Im not sure what to put in the first two lines.

Say for example I use the following dyndns account - durham.linuxhome.net where do i insert that?  Also Ive called my server ubuntu during setup instead of a proper server name.   Where do I need to pop that in the above lines. Also the static IP ive assigned my server is is 192.168.1.150

Im doing this as a first ever server project to learn more than anything and Im stumped.  I would rather ask now than spend hours looking at my server box saying what wnet wrong?

Thank you in advance for all your help.

Best wishes

Andy

---

### Post by MJN on 2008-11-15
Hi Andy,

There may be no requirement for you to explicitly list your private IP address inside /etc/hosts, particularly if your router supports so-called 'NAT loopback' which would allow your server to make Internet DNS and make connections to your public IP address. I'm sure this means nothing to you at this stage, but suffice to say that such additions to your hosts file may not be required.

The /etc/hosts file effectively acts, amongst other things, as a local lookup table which is consulted before DNS - if a match is found then DNS is not consulted at all.

What is your server's hostname according to /etc/hostname ? Add this, along with your full-qualified domain to /etc/hosts as:

```
127.0.0.1 localhost localhost.localdomain <hostname from above>  <hostname.your domain> durham.linuxhome.net
```(substitute your hostname and domain as required)

Give this a shot and see how you get on.

Mathew

---

### Post by andydurham on 2008-11-15
Hi Matthew

Im really sorry but im even more confused now.  

127.0.0.1 localhost localhost.localdomain <hostname from above>  <hostname.your domain> durham.linuxhome.net

SO do i type 

127.0.0.1 localhost localhost.localdomain durham.linuxhome.net hostname.your domain durham.linuxhome.net

Sorry I bet i sound really thick.  Ive just never done this before.

Many thanks

Andy

---

### Post by MJN on 2008-11-15
No worries.. my explanation was not the clearest.

Let's take this one step at a time...

What is the host name inside /etc/hostname? Am I right in assuming that your domain name is durham.linuxhome.net?

Mathew

---

### Post by andydurham on 2008-11-17
Hey

Its ok I think I cracked it. It was dyndns that was confusing me.

I didnt realise that when u choose a name with them u use your host name then your domain name i.e server1.linuxhome.net

So Im setting it up with the following (i hope this is right)

127.0.0.1 localhost.localdomain.localhost
192.168.1.150 server1.linuxhome.net server1

Is that right?

Thanks for all your help in advance.

Cheers

Andy

---

### Post by MJN on 2008-11-17
It'll work. However if this is the HOSTS file on the server then there's no need to seperate out the lines - all names are referring to the server which can be referenced by the loopback address (127.0.0.1)
 
e.g.
 
```
127.0.0.1 localhost.localdomain.localhost server1.linuxhome.net server1
```
 
Mathew

---

