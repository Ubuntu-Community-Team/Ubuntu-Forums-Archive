---
title: "Web address direct with multiple addresses"
date: 2012-01-22
forum: Server Platforms
---

### Post by np123 on 2012-01-22
Hi there,

I have set up a few new servers at home, all running Ubuntu server 11.10 64 bit.

Now, each one has a static IP address within my network, say for example:

172.1.1.9 server 1
172.1.1.10 server 2
172.1.1.11 server 3

SSH is set up on all of them. I have 1 router without a static IP, so I have dynamic dns set up, lets say I have a web address set up to my external IP at [www.me](www.me) . com.

On server 1 I have some websites I want to host, but where im struggling is how to set up the websites to forward to that servers internal IP address and get the right site.

On servers 2 and 3 all I want is to be able to SSH externally. How do I go about setting this up so that I can route to server 2 or server 3, ideally by setting up a web address and typing that in, but if not then just using the IP?

Really appreciate your help here!

---

### Post by volkswagner on 2012-01-22
You will need to forward port 80 to server1 (172.1.1.9) using your routers admin interface.

This will allow outside access to your web pages via your external ip or your dnyDns domain if properly setup.

To allow ssh access you can forward port 22 to anyone machine and use that machine as a gateway to ssh into the remaining two.

ie: forward port 22 to server1, then you can ssh via your dynDns domain or external ip to get into server one.  From there you can ssh internally to the remaining two.

Or you other option would be to change the listening port for ssh on the remaining two.  Then forward that port to each respective internal ip using your router's admin page.

Then you would need to specify the port when ssh'ing into the machine.
like:
```
ssh user@me.com:2200
```

---

### Post by np123 on 2012-01-22
Thankyou very much....I will give that a whirl tonight. Doesnt seem as bad as i thought it might be. Fingers crossed.

Thanks again for the help.

---

