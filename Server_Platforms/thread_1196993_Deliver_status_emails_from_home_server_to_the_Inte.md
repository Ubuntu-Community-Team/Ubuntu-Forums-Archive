---
title: "Deliver status emails from home server to the Internet"
date: 2009-06-25
forum: Server Platforms
---

### Post by matthewboh on 2009-06-25
I want to be able to set up my home server so that status messages and emails can be emailed to me and my brother.  I've read and read and don't know what I should install / modify.

The server is Ubuntu 8.04 with postfix and postfix-ldap installed (I have openLDAP running for Samba).  Do I need something else?  People mention dovecote and exim4.  Also, I have a dynamic dns and Verizon ISP as well as accounts on Hostmonster.  Can I just send the mail out into the Internet or do I need to configure an account on my ISP or the hosting server?

What are some specific words to use to search for answers / howtos?

Thanks in advance - sorry about the noob questions.

Okay!  Got it working and it was relatively easy.  I simply did

```
sudo apt-get install postfix
```

and ran through the dpkg configuration selecting the satellite system and filling in the name of the mail server for the relay server.

Now my question - my host supports either clear connections or SSL.  I know that SSL and TSL are different, but do I want to run SSL under SASL?  All these make no sense to me.

---

