---
title: "Early access to wifi or bluetooth"
date: 2014-11-11
forum: Security
---

### Post by dan146 on 2014-11-11
Hi everyone, 
          
 Does anyone in the community know of a way to enable either wifi or  bluetooth (or both, why not) before a user logs in (in graphical mode)? 
 I am trying to implement a mechanism that uses a second device to send  the credentials to the computer and does the authentication that way,  but I need to find a way for the second device to be able to communicate  with the first one. 
  
 Any, insights on the security implications are also welcome. 
  
 Thanks for your help!

---

### Post by TheFu on 2014-11-11
Can't help with BT - don't use it.
However, wifi can easily (for certain values of "easy")  be controlled through text configuration files in /etc/network/interfaces and /etc/wpa_supplicant/ . Avoid GUI stuff.

If you want 2FA, there are lots of ways.  Yubikey would make for good reading. Many major websites have support for the emerging standard U2F. [https://security.stackexchange.com/questions/71316/how-secure-are-the-fido-u2f-tokens](https://security.stackexchange.com/questions/71316/how-secure-are-the-fido-u2f-tokens)

If you want network-based, centralized, authentication, LDAP+Kerberos have been proven. Trying to re-invent the wheel is generally a bad idea, especially when it comes to security.  Plus, what happens when the network isn't available? Cached credentials has mostly been solved.

---

### Post by dan146 on 2014-11-11
Thank you, very useful.

I am working on a project at uni and I'm trying to implemenet SQRL to be able to log into offline systems.
The real utility is still to be seen but I want to give it a go from a theoretical point of view, and implement it as much as I can.

I just wasn't sure if enabling wifi before login was posible at all. The system also implements an 'in band' mechanism, so if the network is not available it is still posoble to log in.

Would it work the same in upstart as it would in init? Using a script and the configuration files?
And what about systemd?

---

