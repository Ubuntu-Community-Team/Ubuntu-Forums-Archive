---
title: "2 ssh servers on different operating systems on the same machine"
date: 2009-07-12
forum: Server Platforms
---

### Post by ooobooontooo on 2009-07-12
Hi,

I have a machine with 2 operating systems on it. I have ssh servers installed on both operating systems and every time I try to log into one of them, ssh complains that the rsa key sent by the server is different than expected (because of the other operating system). In most cases this is a good thing, but I don't want to have to remove and readd the key every time I want to switch between the operating systems...any advice? Thanks in advance.

---

### Post by andrewc6l on 2009-07-12
Maybe set up the machines with different hostnames / IP addresses for the different OSes? If you don't want to do that, I know OpenBSD lets you specify your own ssh keys in /etc/ssh/*_key - looks like Ubuntu has the same thing. Assuming both your OSes have ssh-keygen or something like that, you might be able to copy the key files from one side to the other.

---

### Post by ooobooontooo on 2009-07-12
> Maybe set up the machines with different hostnames / IP addresses for the different OSes?
I don't think this is possible because my dhcp server assigns ip addresses and it does it by mac addresses. Because the 2 operating systems use the same nic, they end up having the same ip address (they do have different hostnames though....but I don't think that does much...)


> If you don't want to do that, I know OpenBSD lets you specify your own ssh keys in /etc/ssh/*_key - looks like Ubuntu has the same thing. Assuming both your OSes have ssh-keygen or something like that, you might be able to copy the key files from one side to the other.
Excellent advice. I think that's exactly what I was looking for. Thank you.

---

### Post by windependence on 2009-07-12
Easy. You should have static IPs anyway, so set them up. Then copy the key to the other machine so both of them have the same key. Problem solved.

-Tim

---

