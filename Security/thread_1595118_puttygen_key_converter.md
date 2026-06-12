---
title: "puttygen key converter"
date: 2010-10-12
forum: Security
---

### Post by Abadon125 on 2010-10-12
I am trying to use puttygen to create a ppk file that I can use with putty.  I try to import the private key and it gives me the error: Couldn't load private key (ciphers other than DES-EDE3-CBC not supported)

Now I obviously know this is telling me that I have the wrong cipher, but what what do I do to use the correct one?  [Here ]("http://linux-sxs.org/networking/openssh.putty.html")are the instructions that I used to create the keys.

Thanks for the help!

Edit: also, when I open the key this is the top:

-----BEGIN RSA PRIVATE KEY-----
Proc-Type: 4,ENCRYPTED
DEK-Info: AES-128-CBC

and then some other stuff that I don't think I should share.  But the weird thing (to me atleast) is that it lists CBC right at the top there which is what puttygen wants.  Why won't it accept it?

---

### Post by Abadon125 on 2010-10-13
Alright, a friend actually helped me work this one out.  

[Here is a link]("http://www.phwinfo.com/forum/comp-security-ssh/441246-interesting-changes-openssh-5-4p1-affected-putty.html")  
That has the problem and solution in it.  Need to use the dev build of puttygen.

---

### Post by FMaz008 on 2011-04-01
Ho that's great.

Now I just need to be able to _create_ AES-128-CBC private key using putty ( or anything else that can run on windows )

---

