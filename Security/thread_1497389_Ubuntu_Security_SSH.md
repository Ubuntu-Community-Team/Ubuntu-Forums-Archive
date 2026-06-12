---
title: "Ubuntu Security SSH"
date: 2010-05-30
forum: Security
---

### Post by oshirowanen on 2010-05-30
I have been reading the following page about ubuntu security with particular interest in the section about SSH:

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

My setup is slightly different from the setup described in the link above.  In my setup, I have a hardware firewall which blocks all incoming traffic except port 22 to anyone, and then I am using UFW to LIMIT connections to port 22 to a specific IP address.

As my setup is different, do I still need to use SSH keys instead of password authentication? and do I still need to DenyHost and Fail2Ban?

---

### Post by Bachstelze on 2010-05-30
> **oshirowanen said:**
> 
As my setup is different, do I still need to use SSH keys instead of password authentication?

You never *need* to, but it is always a good idea if you can afford it. The decision is yours, there is no definitive answer. Same goes for denyhosts and fail2ban.

---

### Post by CharlesA on 2010-05-30
> **Bachstelze said:**
> You never *need* to, but it is always a good idea if you can afford it. The decision is yours, there is no definitive answer. Same goes for denyhosts and fail2ban.
+1 to using keys. It's a bit more secure than a password. (and elimiates the need for Fail2Ban and whatnot).

---

### Post by oshirowanen on 2010-05-31
Considering I am only allowing 1 IP address access to my port 22, how much further security will I get with key based authentication?

---

### Post by CharlesA on 2010-05-31
> **oshirowanen said:**
> Considering I am only allowing 1 IP address access to my port 22, how much further security will I get with key based authentication?

Not much tbh. I've got the same kind of set up, but I still use keys.

---

### Post by Peter09 on 2010-06-01
I've always had a problem using 'just' keys. Most of the times I use remote access from my laptop. Using just a key means that anybody who manages to get to my laptop (on which I hold no important data) will also immediatly gain access to my desktop via ssh (on which I do have important data).
 
Also, very occasionally, I may wish to use a friends laptop for remote access, using keys stops this.
 
I use a strong password and install 'denyhosts'. Looking at all the attempt to get into my system, 99% start with root - and get denied immediatlely. 
 
Its difficult to guess an unknown password in 5 attempts. (five fails and then get banned)
 
Also, because denyhosts has a community information setup, where you get automatically informed of rogue IP addresses, many addresses are banned before they get anywhere near my machine.

---

### Post by CharlesA on 2010-06-01
That would be why you assign a passphrase to your private key. If anyone gets a hold of the key somehow, they would have to know what the passphrase is before it will let them connect.

---

### Post by anomie on 2010-06-01
[QUOTE=oshirowanen]Considering I am only allowing 1 IP address access to my port 22, how much further security will I get with key based authentication?[/QUOTE]

What you'd get is "security in layers". For example, if you bork your host-level firewall ruleset and inadvertently open up tcp 22 to the 'net, you still have protection via pubkey-only authentication. (Assuming you've enabled and tested it.)

---

