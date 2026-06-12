---
title: "someone try to access to my host"
date: 2013-03-12
forum: Security
---

### Post by alfred33 on 2013-03-12
Hi all, 

I had some problem (gpu related) in my ubuntu 12.10 64bits 
I receive a message if I want to send a report ....
I accept to send the report. 
after a wile some strange thing happens , is I get message that someone with ip address ........ want to access to my host.
I don't know if it's related to the report that I send. 

many thanks

---

### Post by varunendra on 2013-03-12
*Thread moved to **Security Discussions**.*

---

### Post by mastablasta on 2013-03-12
the servers will connect to your host to collect the report i guess. 


where did the message "wand access to your host" appear?

---

### Post by saito.hiroshi on 2013-03-12
the icon of remote desktop opened and the message appear 
when I locate the ip I found is so far from me, the ip indicate that is from Madagascar and I am in Japan

---

### Post by samiux on 2013-03-12
> **saito.hiroshi said:**
> the icon of remote desktop opened and the message appear 
when I locate the ip I found is so far from me, the ip indicate that is from Madagascar and I am in Japan


Do you have remote desktop enabled?

Samiux

---

### Post by alfred33 on 2013-03-12
yes I use remote desktop to connect from my windows  seven using xrdp

---

### Post by samiux on 2013-03-12
> **alfred33 said:**
> yes I use remote desktop to connect from my windows  seven using xrdp


I guess someone out there wanted to try to connect to your box via remote desktop when your error report was sent.

I think it is not related to the error report.

Make sure your user name and password of the Ubuntu and Windows are strong enough.   Since brute force remote desktop is possible.

Samiux

---

### Post by alfred33 on 2013-03-12
Thanks samiux
is there any way to check  that I don't have malicious connection to my box ?
kind of internet security or firewall ?
Thanks

---

### Post by samiux on 2013-03-12
> **alfred33 said:**
> Thanks samiux
is there any way to check  that I don't have malicious connection to my box ?
kind of internet security or firewall ?
Thanks


I think firewall does not help much as the port for remote desktop should be accessable.

To check the current connections,  you can try netstat command to see if there is any suspicious connection.

The most important is keeping your system patched and updated.   Furthermore, the username and password of all your boxes should be strong enough.

Strong password I refer is the length is longer than 8 characters with numeric, uppercase & lowercase and symbol.   The longer the length and the more complex the better.   Meanwhile, the password should not contain any word that can be found in the dictionaries and internet.

Samiux

---

### Post by alfred33 on 2013-03-12
Many thanks for your help !

---

