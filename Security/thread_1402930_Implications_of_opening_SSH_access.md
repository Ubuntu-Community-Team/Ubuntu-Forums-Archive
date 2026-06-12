---
title: "Implications of opening SSH access"
date: 2010-02-09
forum: Security
---

### Post by weirdbeardmt on 2010-02-09
Hi. Generic security type enquiry I think. I've opened up ports 80 and 22 on my router so that I can serve a simple website out (using DDNS) and access the (dedicated) machine via SSH remotely if I need to. The router automatically forwards requests to the DDNS to the specified LAN ip of the Ubuntu machine.

I'm interested in the security implications of this. The Ubuntu machine itself holds nothing interesting - just some video feeds from my surveillance cams (which are served up over port 80 etc.) but elsewhere on the same network, could be some stuff of interest (i.e., the laptop I'm writing this post on now is my primary computer...)

Is it reasonably secure to allow SSH access to that machine? If someone did e.g., brute force the password, would they be able to get elsewhere on my home network and snoop around?

---

### Post by HermanAB on 2010-02-09
Yes, when you allow SSH access to a machine on the Wild Wild Web (not just your loacla LAN), then it is customary to change SSHD to listen on a non-standard port to throw script kiddies off and prevent brute force attacks.  Once an attacker gained access to a machine on your LAN, he can do anything.

---

### Post by movieman on 2010-02-09
> **weirdbeardmt said:**
> Is it reasonably secure to allow SSH access to that machine? If someone did e.g., brute force the password, would they be able to get elsewhere on my home network and snoop around?

Don't use port 22.
Either don't allow password logins, or ensure that you use secure passwords.
Ideally, restrict logins to a single user with a name that's hard to guess: I believe you can disallow ssh logins on a per-user basis, or at least per-group.

The two attacks you're likely to see are password-guessing on common user names and any exploit that's discovered which doesn't require logging in (e.g. a buffer overflow if you send a 10MB user name or whatever). The former, at least, generally only bother with systems running ssh on port 22.

---

### Post by weirdbeardmt on 2010-02-10
OK - Thanks. I'll change the port for SSH - although I assume that wouldn't do too much if people were using a portscanner..? 

Movieman - being dense here - what do you mean "don't allow password logins"  - what's the alternative? I'll look in to restricting which users can SSH.

---

### Post by Bachstelze on 2010-02-10
> **weirdbeardmt said:**
> OK - Thanks. I'll change the port for SSH - although I assume that wouldn't do too much if people were using a portscanner..?

The main benefit of changing your SSH port is that your logs won't get polluted by robots trying to break into your server on the standard port, which will make an actual break-in attempt more noticeable.

> **weirdbeardmt said:**
> Movieman - being dense here - what do you mean "don't allow password logins"  - what's the alternative? I'll look in to restricting which users can SSH.

There are several other authentication methods available, like key-based and host-based authentication.

---

### Post by CharlesA on 2010-02-10
> **Bachstelze said:**
> The main benefit of changing your SSH port is that your logs won't get polluted by robots trying to break into your server on the standard port, which will make an actual break-in attempt more noticeable.

This. Cleaner logs are clean. ;)

Best way would probably be to use key-based auth. Just use a really strong passphrase.

---

### Post by movieman on 2010-02-10
> **weirdbeardmt said:**
> OK - Thanks. I'll change the port for SSH - although I assume that wouldn't do too much if people were using a portscanner..?

99.999% of crackers won't bother scanning non-standard ports on random IP addresses. If they're attacking you specifically, sure, they'll scan everything, but there are nearly four billion assigned IP addresses now so scanning 65535 ports on all four billion addresses would take forever.

> Movieman - being dense here - what do you mean "don't allow password logins"  - what's the alternative?

Ideally use public key authentication, though that's not really feasible if you're going to be logging in from random computers since you need to provide your private key file to ssh to log in.

---

### Post by movieman on 2010-02-10
Oh, and if you really want to be secure, put an extra router in your network and attach the rest of your machines to that so anyone who breaks into the server can't see anything other than the server and Internet router... the second router will block attempts to connect to those machines from the server unless you enable port forwarding.

---

### Post by FuturePilot on 2010-02-10
> **Bachstelze said:**
> The main benefit of changing your SSH port is that your logs won't get polluted by robots trying to break into your server on the standard port, which will make an actual break-in attempt more noticeable.

This

---

