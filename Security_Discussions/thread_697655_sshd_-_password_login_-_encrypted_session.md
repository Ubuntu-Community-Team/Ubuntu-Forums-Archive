---
title: "sshd - password login - encrypted session?"
date: 2008-02-15
forum: Security Discussions
---

### Post by Spitphire on 2008-02-15
I login to sshd with putty and just have password authoication on, i don't use public/private keys to encrypt the session.

My question:

If i just use password auth, is the session still encrypted? 

the reason i don't use keys with password auth off, is because freenx needs password auth on...

---

### Post by mrsteveman1 on 2008-02-15
SSH is always encrypted. Those settings are for people who want to disable password auth so that random hackers cant hammer a server with login attempts.

People sometimes use public/private key logins so that it becomes much much harder to bruteforce an SSH login.

Rest assured no matter what you do SSH is encrypted end to end.

---

### Post by Spitphire on 2008-02-15
Thanks for the reply, 

So if it's password auth or public/private key, the encryption of the session is always the same strength?

---

### Post by Dr Small on 2008-02-15
I am not much in the know about SSH encryption, but whether you are using a password or ssh keys, it's still going to be encrypted so a person sniffing your network won't be able to see what is gaing on.

Dr Small

---

### Post by mrsteveman1 on 2008-02-15
the public/private keypairs are only used to negotiate a session key, the actual encryption is done by a symmetric cipher.

The SSH2 spec lists the following ciphers:

3des-cbc         REQUIRED         
      blowfish-cbc     OPTIONAL          
      twofish256-cbc   OPTIONAL          
      twofish-cbc      OPTIONAL       
      twofish192-cbc   OPTIONAL    
      twofish128-cbc   OPTIONAL    
      aes256-cbc       OPTIONAL            
aes192-cbc       OPTIONAL  
      aes128-cbc       RECOMMENDED  
      serpent256-cbc   OPTIONAL         
      serpent192-cbc   OPTIONAL      
      serpent128-cbc   OPTIONAL      
      arcfour          OPTIONAL   
      idea-cbc         OPTIONAL  
      cast128-cbc      OPTIONA
      none             OPTIONAL

It does appear the spec allows for no encryption at all but you would have to manually specify this, by default ssh is encrypted by one of the ciphers supported on both ends.

[URL="http://www.ietf.org/rfc/rfc4253.txt"]
Here[/URL] is the rest of the spec for the transport layer which is where the encryption occurs.

---

### Post by Spitphire on 2008-02-15
Ok, got it. Thanks!

---

