---
title: "Metasploit..."
date: 2008-03-16
forum: Security Discussions
---

### Post by RichyGibson25 on 2008-03-16
Hey guys, here at work we are penatration testing our network, we just upgraded all of our infrastructure with new servers and new Cisco firewalls and we are trying to do testing with Metasploit 3.1. For some reasons when we try to exploit on our own network with IP's of 192.168.0.* we get the error Exploit failed: Cannot assign requested address - bind(2) . we have checked other fourms, like remote exploit, and it is very frusstrating that Metasploit does not have its own forum site. we have not been able to find any answers, has anyone else ran into this issue or does anyone know how to resolve it? thanks guys!


~Rich
IT Admin
SAU#14 High School.

---

### Post by The Tronyx on 2008-03-16
Sounds like something else is using that port.  Or it could be that you aren't running it as root.  How are you starting Metasploit?

---

### Post by RichyGibson25 on 2008-03-20
i just cd to my framework folder and i do a ./msfconsole. i will try running it as root and see if that helps, also ill check my ports. anyone else?

---

### Post by The Tronyx on 2008-03-20
That sounds like it might be an issue.  Things that require specific socket connection types can only be established as a root user.  You may also have better luck with sudo ./msfgui or sudo ./msfweb.  If you sudo ./msfweb you will need to direct your browser to the appropriate port on 127.0.0.1.  The Metasploit GUI has been much improved in 3.1.  Let me know if this helps you out.

---

