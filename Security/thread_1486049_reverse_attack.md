---
title: "reverse attack"
date: 2010-05-17
forum: Security
---

### Post by cdenley on 2010-05-17
I have noticed a lot of brute-force or dictionary attacks on my FTP server. Most of the time, the attacker is running their own FTP server, so they were probably themselves compromised by the same attack, and their system is now being used by their attacker to attack my server. I've been using fail2ban to block them, but I thought it might be cool instead to actually connect to their server and proxy everything, logging any successful logins.

Would there be anything illegal about this? My script doesn't spoof, it only proxies. Their own FTP banner will be sent to them. They are essentially interacting with their own server. It does log passwords, but they willingly connected to my server and provided the passwords.

---

### Post by teh_drizzle on 2010-05-17
I would be concerned about implicating yourself in already-compromised system behavior. If you're redirecting logins from your host and they are successful then you're now a user on their FTP server (a big if). (Authorized or otherwise) You now have to hope there's nothing on there that might incriminate you. (most likely not)

Although you are presenting them with their own banner, does that banner say "you are allowed to use this system for your own purpose", or anything about it being an open system? 

To what end are you redirecting the attacks? Are you simply trying to find out what username/passwords work on the compromised system? Although that sounds interesting it may not be worth the risk (of involving yourself) if you're only going to uncover bad passwords.

---

### Post by cdenley on 2010-05-17
You make a good point! Their server was already compromised, and is being used for malicious purposes. If their own attack on my server was proxied back to their server and they crack their own password, their logs show my IP was used to crack it! Their system was already compromised, and the attack originated from their server not mine, but someone reading that log might not know that, and might suspect my IP when trying to identify the origin of any malicious actions done with that server.

My script doesn't give any kind of notice, it just straight proxies. As soon as the TCP connection is established, they are interacting with their own server, so the banner is provided by their own server. Unless they have no server, in which case it gives "421 Too many authentication failures" and disconnects. I could easily replace their banner with some kind of warning or legal notice, though.

I guess there isn't really a point besides satisfying my own curiosity about who is attacking me and how that system got compromised. You're probably right, not worth the risk.

---

### Post by OpSecShellshock on 2010-05-17
If their server is compromised, then there's a good chance that they don't know it. They may end up suspecting you of attacking them (well, apart from it appearing that they're attacking themselves).

---

### Post by teh_drizzle on 2010-05-17
Right, there are a few Grey-hat techniques you could use if you're really interested in finding out how they were compromised (intense documentation, reporting to a CIRT, your own logging, anonymous access). (But things like anonymity start to complicate your simple proxying scenario.) :(

---

### Post by OpSecShellshock on 2010-05-17
With it being FTP related I'd be inclined to suspect Gumblar--not on the FTP server itself, but on the owner's client machine.

---

### Post by HermanAB on 2010-05-18
Hmm, three things:
1. FTP is insecure, 
2. rather run a SSH server.
3. Do not run a public facing server on standard ports.

For example, install ssh-server and run it on port 1234 or whatever and your brute force attacks will go away.

---

### Post by cdenley on 2010-05-18
> **HermanAB said:**
> Hmm, three things:
1. FTP is insecure, 
2. rather run a SSH server.
3. Do not run a public facing server on standard ports.

For example, install ssh-server and run it on port 1234 or whatever and your brute force attacks will go away.

1. FTP with SSL encryption is secure. However, a lot of non-technical people use the server, so I made SSL encryption optional. After all, it is the user's data that would be unencrypted. I guess if someone captured a password, they could send files which are identified as being sent by that user, but that wouldn't be a big deal with how the system is implemented. Everyone knows how to upload using FTP, and that is what is most important in my situation.

2. My configuration is rather complicated and would not be possible with openssh-server. I can't use local users. The FTP server must have it's own user database. Each session must have its own unique directory. It should be impossible to see any previously uploaded files from other sessions. Database entries, e-mails, and checksums must be generated at the end of a session, using a user-specific configuration. Anonymous uploads must be allowed. Try doing all this with SSH!

3. One again, non-technical users. We don't want to have to explain how to enter the non-standard port on whatever FTP client they may be using. Also, I have no way of notifying all existing users that I have moved it to a different port.

---

### Post by HermanAB on 2010-05-18
OK, so install fail2ban or similar.

---

### Post by cdenley on 2010-05-18
> **HermanAB said:**
> OK, so install fail2ban or similar.
As I said, I already do.
> **cdenley said:**
> **I've been using fail2ban to block them**, but I thought it might be cool instead to actually connect to their server and proxy everything, logging any successful logins.


By the way, I got the idea from your ssh version in your link.
[http://www.aeronetworks.ca/ssh-kiddies.html](http://www.aeronetworks.ca/ssh-kiddies.html)

---

