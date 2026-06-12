---
title: "Using Remmina to Connect to an RDP Server through a TS/RDP Gateway"
date: 2013-09-26
forum: Server Platforms
---

### Post by flickerfly on 2013-09-26
I've been able to successfully ender xfreerdp commands to connect through an RDP Gateway. I understand that Remmina uses xfreerdp under the hood to provide RDP features. It seems logical that I should be able to edit the config or something after I create a server to add the gateway credentials. Anyone know how this might be accomplished?

Thanks!

---

### Post by Bucky Ball on 2013-09-26
*Thread moved to **Server Platforms**.*

Someone here might. ;)

---

### Post by flickerfly on 2013-09-26
Thanks Bucky Ball

---

### Post by omriasta2 on 2013-10-24
I'm interested in this as well. I'm guessing that Remmina support for this new feature will take a while since it's not really stable yet but is there a way to add it manually?

---

### Post by chrisguk on 2013-10-25
If you are happy to use command line you will get better results with rdesktop.  A typical command with screen sizing would be:

```
sudo rdesktop -g 80% 10.1.1.2
```

If you use the man page for rdesktop ```
man rdesktop
```  you will find some great information with many other options.

---

### Post by flickerfly on 2014-10-23
There is a feature request here for Remmina to include the freerdp gateway features:
[https://github.com/FreeRDP/Remmina/issues/347](https://github.com/FreeRDP/Remmina/issues/347)

---

