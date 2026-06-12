---
title: "Checkgmail shows password in plaintext"
date: 2009-11-07
forum: Security
---

### Post by goehle on 2009-11-07
I'm not sure how much of an issue this is, so I am coming here for advice.  

I was trying to figure out some authentication issues with check gmail and found the following: 
1. run checkgmail from a terminal
2. click the applet icon 
3. the terminal should show the firefox command called, with an address
4. the address contains my gmail password in plaintext 

Is it normal to authenticate this way?  I always assumed that when checkgmail automatically logged into my account it was doing something more secure.

---

### Post by kevdog on 2009-11-07
Use https:/mail.google.com

---

### Post by goehle on 2009-11-08
I guess its not so much that I'm worring about people eavsdropping.  Its disconcerting that anyone with access to a terminal on my machine can find my gmail password.  

On the other hand, thats what you get when you save passwords.  I started thinking about it and they can do the same thing with any password stored in firefox, or in the login keyring for that matter.

---

### Post by FuturePilot on 2009-11-08
> **goehle said:**
> I guess its not so much that I'm worring about people eavsdropping.  Its disconcerting that anyone with access to a terminal on my machine can find my gmail password.  

On the other hand, thats what you get when you save passwords.  I started thinking about it and they can do the same thing with any password stored in firefox, or in the login keyring for that matter.

Firefox and the login keyring do not store passwords in plain text, they are encrypted. You might want to check out ecryptfs which can encrypt your entire /home.

---

