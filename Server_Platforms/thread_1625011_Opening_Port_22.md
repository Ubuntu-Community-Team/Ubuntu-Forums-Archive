---
title: "Opening Port 22"
date: 2010-11-18
forum: Server Platforms
---

### Post by trentscott on 2010-11-18
I just setup SSH key-based authentication between my server and laptop (client) machines and plan on using SFTP exclusively for uploading website files. Is it safe to open port 22 on my router and open this up to the world or are there other security measures I need to take? From what I understand, SFTP and SSH with keys are about as secure as it gets -- just want to make sure I don't open this until it's safe to do so. Thanks! :D

---

### Post by arrrghhh on 2010-11-18
Using keys is definitely more secure than just a straight-up password - now people cannot brute force your server.  I'd also put a password on the key files, that way if someone gets your private key you'll have a little bit of time to generate new keys before they crack your priv. key.

With that said, on to your question - port 22 open to the world - I wouldn't recommend it.  I have 22 open on my LAN, but I have my router forward it to a different port.  Pick something big, and random - above 1024.  So long as it's not being used by something else, you should be fine.

This extra step just ensures it's even more difficult to hit your box from the outside.

---

### Post by trentscott on 2010-11-18
> **arrrghhh said:**
> 
With that said, on to your question - port 22 open to the world - I wouldn't recommend it.  I have 22 open on my LAN, but I have my router forward it to a different port.  Pick something big, and random - above 1024.  So long as it's not being used by something else, you should be fine.

This extra step just ensures it's even more difficult to hit your box from the outside.

Altering the port means I need to also change it in the OpenSSH config file, correct? Do I need to do anything to change the SFTP port or does that default to whatever SSH is set to use on the server? Thanks :D

---

### Post by pricetech on 2010-11-18
Install fail2ban.  It will drop any IP that fails authentication after 3 tries.

Change the port for SSH.  Some will say that's merely "security through obscurity" but it doesn't hurt.

---

### Post by arrrghhh on 2010-11-18
> **trentscott said:**
> Altering the port means I need to also change it in the OpenSSH config file, correct? Do I need to do anything to change the SFTP port or does that default to whatever SSH is set to use on the server? Thanks :D

SFTP and SSH are interchangeable really.  

You can do it one of two ways - your method certainly works, changing the conf file.The other method I mentioned earlier - I have 22 open on my LAN, but then I have my router redirect the traffic to a different port.  So thru the WAN, there's a completely different port in use for SSH.

Security thru obscurity - I like that haha.  It's true, but every little bit helps.

I forgot about fail2ban - I would definitely install that as well.

---

### Post by trentscott on 2010-11-18
Thanks guys, installed fail2ban and decided to go with the router method.

---

