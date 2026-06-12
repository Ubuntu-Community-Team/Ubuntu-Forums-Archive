---
title: "Can't log in - to much output on login screen"
date: 2015-01-16
forum: Server Platforms
---

### Post by cajus2 on 2015-01-16
So I have an 12.04 LTS Server up and running somewhere on a virtual machine, all it does right now is providing a VPN. Shorewall is also running. 
I can connect using VNC though, but the screen overflows with messages from Shorewall. ([http://www.linuxquestions.org/questions/debian-26/shorewall-firewall-and-display-cluttering-452447/](http://www.linuxquestions.org/questions/debian-26/shorewall-firewall-and-display-cluttering-452447/)) 
So I can't log in. 

Is there any simple solution to this problem? Suppressing all user-unrelated output on the terminal for example?

---

### Post by MAFoElffen on 2015-01-16
You linked to the same kind of problem... or was that you and it has been going on for 8 years? 
did you try those solutions yet? Especially:
```

Edit /etc/init.d/klogd
Edit/add this line: KLOGD="-c 4"

```

---

