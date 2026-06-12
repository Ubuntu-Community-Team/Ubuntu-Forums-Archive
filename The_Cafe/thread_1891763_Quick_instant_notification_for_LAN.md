---
title: "Quick instant notification for LAN"
date: 2011-12-06
forum: The Cafe
---

### Post by rmcellig on 2011-12-06
My wife works upstairs on her PC (Windows XP). I work in the basement on my Mac as well as my older Linux machines. We desperately need a way to communicate without always yell at one another :) Is there a way we can set up a simple and easy cross platform way so that if she wants to send me a message, a message will pop up on my Mac, PC, or Linux machines.

---

### Post by aeiah on 2011-12-06
why not just use an instant messaging client?

---

### Post by rmcellig on 2011-12-06
any cross platform recommendations?

---

### Post by trinux_bc on 2011-12-06
Google Chat? Any web-based IM will work. If you want to use Desktop clients Pidgin (Linux and Windows) and Adium (Mac) are built off the same lib purple base.

trinux_bc

---

### Post by Roasted on 2011-12-06
Windows - Pidgin
Mac - Adium
Linux - Pidgin

Then just sign up for an account for one of the messaging protocols they support. I use AIM quite a lot. Some people like Yahoo, MSN, and even Facebook. All choices that'll do the job for you.

As trinux_bc said, Adium and Pidgin are based on the same platform, so using Adium on your Mac and Pidgin on Linux shouldn't be a real culture shock.

---

### Post by marshmallow1304 on 2011-12-06
Pidgin, Adium, and iChat all support Bonjour, which allows you to chat on a LAN without connecting to a server.

---

### Post by cariboo on 2011-12-06
Check:

```
man smbclient
```

on the Mac to see if it supports messaging, if it does, then enter the following command:

```
smbclient -M <netbios_name>
```

Where <netbios_name> is the name you've given the Mac.

---

### Post by Linuxratty on 2011-12-06
GNU Free Call?

[http://www.pcworld.com/businesscenter/article/222556/gnu_free_call_an_open_source_skype_alternative.html](http://www.pcworld.com/businesscenter/article/222556/gnu_free_call_an_open_source_skype_alternative.html)

---

