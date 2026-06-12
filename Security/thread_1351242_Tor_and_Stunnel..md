---
title: "Tor and Stunnel."
date: 2009-12-10
forum: Security
---

### Post by zozza on 2009-12-10
Apologies if this is not "strictly" security but I hope it is close enough. 

I have installed tor and polipo with the vidalia GUI.  All is fine.  Now I wish to use stunnel to add SSL from the last hop to the desired website (assuming the website is not already HTTPS).

How do I do this? I have been unable to find a guide and it is clear that stunnel is considered a program that often causes errors.

To reiterate: I want to combine tor, polipo, and stunnel so that I have encryption between the tor exit node and the website deisred.

Thanks.

---

### Post by cdenley on 2009-12-10
If the server you are connecting to doesn't use SSL encryption, then you won't be able to negotiate an SSL connection. The server won't be able to do anything with encrypted data. You can't force arbitrary servers to start using SSL.

---

### Post by Dr Small on 2009-12-11
Impossible.
Tor provides an encrypted tunnel from you to the exit node, but from the exit node to the requested host, the connection then becomes unencrypted (unless the website supports SSL).

---

### Post by doas777 on 2009-12-11
well, as the others have pointed out, as long as the remote endpoint supports ssl, you should just be able to point stunnel to the local port for tor. there shouldn't be much more too it. any stunnel endpoint needs to be ssl capable.

---

### Post by zozza on 2009-12-12
Thanks all - you have cleared this issue up for me.  Obviously I misunderstood what I had read.  

Therefore it seems to be that using Stunnel is pointless in this situation because if the end site has SSL then Ubuntu's normal SSL support will kick in making Stunnel irrelevant.

---

