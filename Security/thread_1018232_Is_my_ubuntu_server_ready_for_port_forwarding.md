---
title: "Is my ubuntu server ready for port forwarding?"
date: 2008-12-21
forum: Security
---

### Post by pshootr on 2008-12-21
I have setup an 8.10 (intrepid) server on my lan to act as a fileserver. I connect to the net through a Linksys NAT router/firwall. I have the SSH portion of the server configured to only exept protocol 2 SSH connections which require an authentication key, which is invoked by a passphrase. Is it now safe for me to forward my chosen port for SSH to my server machine so that I can access it from the web?

---

### Post by Drezard on 2008-12-21
Make sure your password to your username is really long. Also change the default port to something like 543 or 987. Last but not least, make sure the root account is disabled.

Daniel

---

### Post by Mattventura on 2008-12-21
Yes. Also, if you are using key-based authentication, you probably don't need to change the port or anything. Something you should do, though, is edit the file /etc/ssh/sshd_config, and find the line "PermitRootLogin yes" and change it to "PermitRootLogin no". Then, instead of needing a key or password for root, they have to have a key, a username, and a password to do real damage to the system.

If you want to make it more secure, keep root logins enabled through ssh, but in /etc/passwd change root's login shell to /bin/false. That way, root logins will be successful but they will immediately be disconnected.

---

### Post by pshootr on 2008-12-21
> **Drezard said:**
> Make sure your password to your username is really long. Also change the default port to something like 543 or 987. Last but not least, make sure the root account is disabled.

Daniel

Cool, thanks for the tips. I will follow your advice. My port has been changed to a random port instead of the default. I guess I could beef up the user pass. But I have a random key type password. And every password list I have ever used to try and crack it fails. I guess what strikes me the most though is disabling the root account (just in case). Good thinking.

---

### Post by pshootr on 2008-12-21
> **Mattventura said:**
> Yes. Also, if you are using key-based authentication, you probably don't need to change the port or anything. Something you should do, though, is edit the file /etc/ssh/sshd_config, and find the line "PermitRootLogin yes" and change it to "PermitRootLogin no". Then, instead of needing a key or password for root, they have to have a key, a username, and a password to do real damage to the system.

Ok cool, thanks a lot. I will check my ssh.conf to make sure I have 'PermitRootLogin no'
 Thanks again.

---

### Post by pshootr on 2008-12-21
> **pshootr said:**
> Ok cool, thanks a lot. I will check my ssh.conf to make sure I have 'PermitRootLogin no'
 Thanks again.

Yes i did select no for permitrootlogin. tanks again.

---

### Post by cdenley on 2008-12-22
> **Mattventura said:**
> Yes. Also, if you are using key-based authentication, you probably don't need to change the port or anything. Something you should do, though, is edit the file /etc/ssh/sshd_config, and find the line "PermitRootLogin yes" and change it to "PermitRootLogin no". Then, instead of needing a key or password for root, they have to have a key, a username, and a password to do real damage to the system.

If you want to make it more secure, keep root logins enabled through ssh, but in /etc/passwd change root's login shell to /bin/false. That way, root logins will be successful but they will immediately be disconnected.

In ubuntu, the root account doesn't have a valid password, so as long as passwords are required, the "PermitRootLogin" option is pointless.

I would recommend this option in /etc/ssh/sshd_config:
```

AllowGroups admin

```
This will only allow members of the admin group to use ssh. Then install something like denyhosts or fail2ban. This will block hosts after a few authentication failures to prevent attackers from having too many guesses.

Also, there is more to password security than making a long password. If a long password is in a password dictionary, then it is an extremely bad password. Avoid any real words or patterns, and use mixed case, numbers, or special characters (!@#$%^&*()-_).

---

### Post by pshootr on 2008-12-22
> **cdenley said:**
> In ubuntu, the root account doesn't have a valid password, so as long as passwords are required, the "PermitRootLogin" option is pointless.

I would recommend this option in /etc/ssh/sshd_config:
```

AllowGroups admin

```
This will only allow members of the admin group to use ssh. Then install something like denyhosts or fail2ban. This will block hosts after a few authentication failures to prevent attackers from having too many guesses.

Also, there is more to password security than making a long password. If a long password is in a password dictionary, then it is an extremely bad password. Avoid any real words or patterns, and use mixed case, numbers, or special characters (!@#$%^&*()-_).

Very good imformation. Thanks you for sharing, I really like the idea of having either denyhosts or fail2ban. I will have to read up on them and check them out. Thanks alot.

---

### Post by hyper_ch on 2008-12-23
changing the port will not make it any more secure.

---

### Post by Masuran on 2008-12-23
Setup packet filtering rules using iptables to only allow SSH connections from your router and block everything else.

---

### Post by trendyguide on 2008-12-23
Ubuntu releases

---

### Post by erwall on 2008-12-23
I'd highly recommend installing denyhosts.

```
sudo aptitude install denyhosts
```

It'll block an ip permanently if they attempt logging in 3 times and fail.  It's pretty much impossible to guess a password given 3 chances.  Also, I'd recommend whitelisting local management ip's, or simply the whole internal subnet.

---

### Post by pshootr on 2008-12-27
> **Masuran said:**
> Setup packet filtering rules using iptables to only allow SSH connections from your router and block everything else.

Sounds secure, but I want to be able to connect from the net also.

---

### Post by pshootr on 2008-12-27
> **erwall said:**
> I'd highly recommend installing denyhosts.

```
sudo aptitude install denyhosts
```

It'll block an ip permanently if they attempt logging in 3 times and fail.  It's pretty much impossible to guess a password given 3 chances.  Also, I'd recommend whitelisting local management ip's, or simply the whole internal subnet.

Thank you, I installed "denyhost". But how do I go about whitelisting?

---

### Post by hyper_ch on 2008-12-27
> **pshootr said:**
> Thank you, I installed "denyhost". But how do I go about whitelisting?

/etc/hosts.allow

---

