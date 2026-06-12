---
title: "The madness of King William"
date: 2008-10-24
forum: Security
---

### Post by Nesaskewatch on 2008-10-24
With apologies for such a stupid question.

I am brand new at Linux after having been a chronic and habitual Windows user all my computing life.  I am loving this Ubu OS more everyday, and now almost continually hum the Willie Nelson song; "Nothing but Blue Sky..."  However, I am still suffering from demented paranoia with regards to security.  After all, that is what I spent the most time dealing with for the last 11 years.  

My question is; Is Ubuntu 8.04 safe "right out of the box" while I learn about Ubu security?  I see that I have a lot of reading to do, but would feel better knowing I am not loitering in a dark alley with no clothes on...

Thanks!

---

### Post by bigken on 2008-10-24
safe as houses my son though i would suggest a firewall no need for virus software

---

### Post by PmDematagoda on 2008-10-24
You could also sandbox the applications using AppArmor so that even if an application does get compromised, it won't easily affect the other applications. Although something like this requires time and patience and probably isn't necessary since Ubuntu is quite secure without it, especially if you use good firewall rules and is careful about rootkits.

---

### Post by nubdora on 2008-10-24
For the use of a desktop? Yes, it is fine right out of the box, but I would still configure the iptables to deny.

For the use of a server? No, more configurations are needed for a "secure" server.

What about viruses, malware, and worms, you ask? There are very few of these written for the Linux kernel in the wild. Also, Ubuntu has root privileges disabled by default, so, the user is prompted with the root password when any thing is to be run as root. File sharing is also disabled by default.

Best advice for security - do not install as root if you have any doubts about the application; if it's in the repository it is usually fine. Do not run strange commands especially if the command starts with "sudo"

Related to security, but not always mentioned: Do not delete files that begin with "."

Example: /dev/.java
These are hidden files and are generally needed by the OS.

The exception to this is if you believe your system has been compromised because malicious users tend to store hidden files after a break-in or you have installed some not-so-trusted applications and you know the hidden file does do not belong.

---

### Post by jerome1232 on 2008-10-24
I wouldn't worry about the firewall so much as I would browser security. On a desktop it's really the only window to your system. Tracking cookeis, malicious javacript, malicious java while not able to damage your system, may be able to hijack the clipboard or infringe on your privacy.

Firfox addons like noscript and flashblock is my recomendation. I guess I just don't see the point of a firewall dropping packets when nothing is listening in the first place.

---

