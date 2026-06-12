---
title: "avoid starting sendmail as a daemon process"
date: 2010-05-01
forum: Server Platforms
---

### Post by anirup on 2010-05-01
[B][U]I currently have sendmail installed.It starts as a daemon but i want to
avoid doing that.I want to start it manually.plz help[/U][/B]

Also am a dynamic host.so every time i start my computer my ip changes.
I use ddclient to update my records at dyndns.com.but [B][U]how to configure 
sendmail in the case of dynamic hosts since it looks at the file
/etc/hosts which contains information about the static hosts.
plz help[/U][/B]

---

### Post by Bachstelze on 2010-05-01
Do you really need to have sendmail in the first place? What do you want to do with it?

---

### Post by anirup on 2010-05-01
_**well its a mail transfer agent.so i use it to send emails from my computer.rather than using hotmail,gmail,etc**_

[B][U]Well I got the problem solved.
Download sysv-rc-conf and read the manual.its a very powerful tool.[/U][/B]

---

