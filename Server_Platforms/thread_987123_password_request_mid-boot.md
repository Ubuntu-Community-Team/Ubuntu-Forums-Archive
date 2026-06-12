---
title: "password request mid-boot"
date: 2008-11-19
forum: Server Platforms
---

### Post by diablothe2nd on 2008-11-19
Hi,

i've just installed ubuntu server 8.04, done an upgrade and dist-upgrade with apt... and now i'm getting asked for a password mid boot, just after ssh starts, and also when i tell it to shutdown/restart :confused:

the weirdest thing is, i dont need to put anything into the password field... just pressing return makes it continue, but i cant physically be at the server if i need to restart it, once it's all up and running.

whats going on?

can someone please tell me how to turn it off because this kind of requester is a total annoyance on a server that's only being remotely accessed


thanks

---

### Post by diablothe2nd on 2008-11-20
anyone got any ideas?

---

### Post by diablothe2nd on 2008-11-20
never mind.. it's stopped doing it now *scratches head*

but apache's now started asking for a password on boot now :mad: again just hitting return gets it past it.

---

### Post by threetimes on 2008-11-20
Do you use SSL?
 
[http://doc.ubuntu.com/ubuntu/serverguide/C/certificates-and-security.html](http://doc.ubuntu.com/ubuntu/serverguide/C/certificates-and-security.html):
> 
You can now enter your passphrase. For best security, it should at least contain eight characters. The minimum length when specifying -des3 is four characters. It should include numbers and/or punctuation and not be a word in a dictionary. Also remember that your passphrase is case-sensitive. 
Re-type the passphrase to verify. Once you have re-typed it correctly, the server key is generated and stored in the server.key file. 

You can also run your secure service without a passphrase. This is convenient because you will not need to enter the passphrase every time you start your secure service. But it is highly insecure and a compromise of the key means a compromise of the server as well. 


---

### Post by diablothe2nd on 2008-11-20
yes, ssl's installed and running.

so if i type a passphrase in it'll stop bugging me at startup?

is that also why i'm getting a warning that the certificate refers to localhost when i log in to email?

many thanks for pointing me to that link :)

---

### Post by MJN on 2008-11-20
> **diablothe2nd said:**
> yes, ssl's installed and running.
 
so if i type a passphrase in it'll stop bugging me at startup?Unfortunately not - it'll prompt you next time you reboot (or restart Apache).
 
You can remove the passphrase - following the instructions at [http://httpd.apache.org/docs/2.0/ssl/ssl_faq.html#removepassphrase](http://httpd.apache.org/docs/2.0/ssl/ssl_faq.html#removepassphrase) but do note the warning about ensuring your private key is root-owned and set to root-readonly.
 
The Ubuntu doc quoted above is, in my opinion, a bit misleading saying a passpraseless key is 'highly insecure' as with root-only persmissions it is only be vulnerable with physical access to machine (or root level privileges) in which case most bets are off anyway.
 
> is that also why i'm getting a warning that the certificate refers to localhost when i log in to email?No, that is because your e-mail client thinks it is connecting to somename.yourdomain.com yet the certificate was issued to localhost - the name don't match hence it looks like an imposter to the client.
 
The solution is to either configure your mail client to use the name localhost in its configuration or to get a certificate issued to the correct name.
 
Mathew

---

### Post by diablothe2nd on 2008-11-20
that's excellent, i'll look into it.

thanks!

---

