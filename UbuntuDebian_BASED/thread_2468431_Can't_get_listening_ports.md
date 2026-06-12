---
title: "Can't get listening ports"
date: 2021-10-29
forum: Ubuntu/Debian BASED
---

### Post by thumper76 on 2021-10-29
I am running the following three commands to find listening ports and  I not getting any listing with any of them. Is something blocking these commands? What's going on?

```

  sudo netstat -tunlp
  sudo ss -tunlp
  sudo lsof -nP -iTCP -sTCP:LISTEN
 
```

---

### Post by The Cog on 2021-10-29
That would indeed suggest that no processes are listening, which is unusual for an Ubuntu install. Is this in a VM? What's the context?

---

### Post by thumper76 on 2021-10-29
OK, I have to "fess up". I dual boot ubuntu 20.04 with another Debian based operating system. It's the other OS that causing this problem. However the Ubuntu Forums  seems to be the only place I can competent answers. I assume the problem would be the same  on any Debian based OS.

---

### Post by The Cog on 2021-10-30
What makes you think that any service is listening? Maybe this "other" distro doesn't have any listening processes. The only services I see listening here are avahi-daemon, cupsd (printer service), cups-browsed sshd and brave. Only avahi and cups are running by default. A more security conscious distro might not start them by default.

Try this command to briefly open a listening port (9999):
```
nc -lv 9999
```
Then use your commands to look for open ports in a different terminal window.

---

### Post by thumper76 on 2021-10-30
OK that did show up with all three commands. Could it be there are no listening port with this OS (it's Kali by the way)? I'm surprised!!

---

### Post by The Cog on 2021-10-31
Kali is a security conscious penetration testing distro. It should not surprise you at all that it's not listening on any ports by default. I'd be a little surprised if it was.

---

### Post by coffeecat on 2021-10-31
Not Ubuntu. *Thread moved to **Ubuntu/Debian Based** sub-forum.*

---

