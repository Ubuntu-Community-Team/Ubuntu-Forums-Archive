---
title: "Webmin or ebox, which one to use"
date: 2010-02-19
forum: Server Platforms
---

### Post by A_M_S on 2010-02-19
Hello.

Webmin or Ebox what is the best for ubuntu server 9.04?

Tnx.[LEFT][/LEFT]

---

### Post by pirateghost on 2010-02-19
> **A_M_S said:**
> Hello.

Webmin or Ebox what is the best for ubuntu server 9.04?

Tnx.


that really depends on what you want to do with your server.

---

### Post by A_M_S on 2010-02-19
> **pirateghost said:**
> that really depends on what you want to do with your server.
For now i'm only using ubuntu server for testing.
I'm exploring services like http, email, dns, etc.

---

### Post by pirateghost on 2010-02-19
> **A_M_S said:**
> For now i'm only using ubuntu server for testing.
I'm exploring services like http, email, dns, etc.

if you are familiar with linux at all, go with webmin, if you are new to linux, ebox is easier


heck, why not install them both?  they can run side by side, and you can choose for yourself

---

### Post by Pro_D on 2010-02-19
Hmm, my experience with ebox was pretty negative actually.  I had managed to get a working DHCP+DNS with secure updates and ebox shredded my configuration.  I spent a few hours trying to get it working via ebox and then gave up.  Additionally it didn't seem to like me editing anything by hand.

I had done the DHCP+DNS by hand (and many guides) though and this was when ebox was new.  It's been a while, back then they didn't (seem to) run well together.


I have enjoyed webmin but then I have been trying to learn linux and I don't do much web hosting or e-mail.

---

### Post by A_M_S on 2010-02-19
Thank you for the reply.
> **pirateghost said:**
> if you are familiar with linux at all, go with webmin, if you are new to linux, ebox is easier
I think i'll try webmin ;)


heck, why not install them both?  they can run side by side, and you can choose for yourself
I read in some thread (can't remember where :( ) that there are some compatibility issues between them. But tnx anyway for the suggestion.

---

### Post by ezacon on 2010-02-20
Ebox is designed to install all needed applications and control configuration files. All configurations need to be done with web interface. A configuration change can affect several packages configurations at once.

ebox automate lots of thigs. You d'ont need to have knowledges of each package.

webmin is just a web interface, so you need to have good knowledge of packages. it just simplify the way you modify configuration files. You dónt need to know the exact sintax of each configuration file.

---

### Post by A_M_S on 2010-02-20
> **ezacon said:**
> Ebox is designed to install all needed applications and control configuration files. All configurations need to be done with web interface. A configuration change can affect several packages configurations at once.

ebox automate lots of thigs. You d'ont need to have knowledges of each package.

webmin is just a web interface, so you need to have good knowledge of packages. it just simplify the way you modify configuration files. You dónt need to know the exact sintax of each configuration file.

webmin is what i was searching.
tnx.

---

