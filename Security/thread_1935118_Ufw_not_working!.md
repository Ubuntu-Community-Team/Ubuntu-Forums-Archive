---
title: "Ufw not working!"
date: 2012-03-03
forum: Security
---

### Post by 0011235813 on 2012-03-03
Hello forum,
I am using one of my computers that run Ubuntu, and I've found that the firewall won't start!
When I use:
```
 sudo ufw enable
```
I get the following:
```
Error: problem running ufw-init
```
does anyone know what might be wrong?

---

### Post by Dangertux on 2012-03-03
Are you using or were ypu using firestarter. Installing firestarter can someetimes break the init script for ufw.

Try using
```

sudo apt-get remove --purge ufw && sudo apt-get install ufw

```

To replace the script

---

### Post by 0011235813 on 2012-03-03
> **Dangertux said:**
> Are you using or were ypu using firestarter. Installing firestarter can someetimes break the init script for ufw.

Try using
```

sudo apt-get remove --purge ufw && sudo apt-get install ufw

```

To replace the script

That fixed it, thanks. It wasn't firestarter, but it was a graphical firewall program called "firewall configuration". I guess I should stick to command line and ignore these fancy but little known GUI programs :(

---

### Post by kevdog on 2012-03-03
Please mark thread as solved -- Thanks.

---

### Post by 0011235813 on 2012-03-10
The issue seems to have sprung up yet again and I've had to run the command... Weird. I guess I should check my firewall status more regularly, especially after updates.

---

### Post by kevdog on 2012-03-10
Get rid of ufw and just use iptables directly -- that would be my advice.  Its not really that much different to configure.

---

