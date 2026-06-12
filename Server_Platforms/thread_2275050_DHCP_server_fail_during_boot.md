---
title: "DHCP server fail during boot"
date: 2015-04-24
forum: Server Platforms
---

### Post by sububtu on 2015-04-24
I had installed DHCP in UBUNTU server 12.04. 
The  DHCP server never starts at boot and showing a fail message during the boot. 
when ever i tried to start to DHCP manually it works with second attempt. I
n the first attempt i can see an error like :

    stop: Unknown instance:

I dont know how to find the error, Im using webmin to add DHCP entries.

thank you . .

---

### Post by darkod on 2015-04-24
Have you tried using ssh instead of webmin? Webmin sometimes writes config files differently than what they should be. That might be related to the problem.
dhcp is not complex to set up using ssh so you might give that a shot.

---

### Post by sububtu on 2015-04-25
> **darkod said:**
> Webmin sometimes writes config files differently than what they should be..
yes, i also believe that the misconfiguration may happened because of webmin. Is there a way to identify the line number that causing the problem? I had searched the logs. but i cant see anything special !!

---

### Post by darkod on 2015-04-25
I assume you don't have the original config file? Another benefit of doing it manually in a ssh session is that best practice is to make a copy of the original config file before starting to make your changes. That way you always have the original to revert to. But I don't know how webmin did it, I don't think it did a copy.

What you can do is purge (remove) the package for the dhcp server and install it again. That should install it with the default config file.

---

