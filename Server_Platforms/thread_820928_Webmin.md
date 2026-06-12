---
title: "Webmin"
date: 2008-06-06
forum: Server Platforms
---

### Post by JonRohan on 2008-06-06
What is the general consenus in using webmin on server systems? Do you use webmin to manage your servers or do you prefer SSH action? Webmin strikes me (in my limited linux knowledge) as a little insecure with root logon etc?

Your thoughts?

---

### Post by SpaceTeddy on 2008-06-06
webmin is nice to just get things done, or to have it for others that are not feelings very... comfortable in a CLI. I personally ALWAYS use ssh consoles to do anything on a server. I don't touch webmin. But i have to run it on almost all systems so that all the other admins can also use the servers as they are afraid of anything that only has two colors...

in general, yes, webmin is a heap of security issues and i would NEVER EVER let it run so people from the internet can access it (no matter what, i will not let that happen). On internal systems, i either restrict the access via iptables, bind it to specific network card i know are in trusted networks or use ssh/vpn tunnels to access it. Anything but a "normal" network connection where any joe blow could find it. 

Besides that, the openssh server runs as root aswell - so that is not really an argument. The reason i don't trust it is that this thing is wastly big that nobody knows where bugs are... openssh is more tightly monitored, and more important - it is simpler !

kiss - keep it simple, silly

i like that one. i hope my thoughts helped you :)

---

### Post by lodp on 2008-06-06
i do use webmin on my server, and it helps a lot if you're only starting out with server management. every application you add will also add security issues. but then again, you can screw up pretty badly in a host of ways, without ever even having heard about webmin. how many people are using password-based authentication and weak passphrases on ssh? many hosting companies even deliver their servers that way. and as it turned out recently, not even certificate-based authentication on ubuntu was as secure as we might have thought.

there's a number of measures built into webmin it that are supposed to tackle some of the gravest risks. http is alway redirected to https. you can restrict access to a single IP, make it blacklist IPs after a number of failed login attempts.you can make it listen on a non-standard port...

---

### Post by JonRohan on 2008-06-07
Thanks for your comments. :)

Ultimately it is probably better to do without then as I guess the more you add to a server the more chance of security leaks, bugs and things breaking. 

I like the idea of binding Webmin to a specific network card with IP address filters.

---

