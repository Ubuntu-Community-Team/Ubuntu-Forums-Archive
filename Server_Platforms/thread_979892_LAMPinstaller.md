---
title: "LAMPinstaller"
date: 2008-11-12
forum: Server Platforms
---

### Post by Jasper91 on 2008-11-12
Hey everyone,

Because a lot of people I met are having a lot of trouble  setting up a simple LAMP-server, I wrote a program (my first Linux-program btw ;)) that automaticly:
- Installs and configures Apache2
- Installs and configures vsFTPd (user has to set the correct ports only)
- Installs and configures PHP5 and MySQL
- Installs OpenSSH
- Configures network-settings (requests IP and gateway first)

I don't know about any of you is in need of it, but why keeping it just for myself ;)

File: [www.jasperkouwenberg.com/LAMPinstaller](www.jasperkouwenberg.com/LAMPinstaller)
Source: [www.jasperkouwenberg.com/LAMPinstaller.cpp](www.jasperkouwenberg.com/LAMPinstaller.cpp)

PS: Only Debian-based dist. are supported!

Cya,
Jasper

---

### Post by CrucifiedEgo on 2008-11-12
Thanks for the contribution, but, two nitpicks:

1) Wouldn't this be better as a shell script?  It seems like C++ for a bunch of system() calls is overkill.

2) I think that users doing the installation themselves tends to help them understand more about what they're doing and how it works.  That's just MHO of course.

---

### Post by Jasper91 on 2008-11-12
1. It is 95% shell, but because of the network-settings (IP, gateway) I had to use a prog-language
2. Absolutely true! But this program is just for the (experienced) users who are trying to setup a LAMP-server in very little time

---

### Post by CrucifiedEgo on 2008-11-12
Why not use read?  

```
#!/bin/bash
echo -n "Testing: "
read -e VAR
echo "You entered:" $VAR
```

---

