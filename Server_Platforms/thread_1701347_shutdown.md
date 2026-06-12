---
title: "shutdown?"
date: 2011-03-06
forum: Server Platforms
---

### Post by macstl on 2011-03-06
I installed server 10.10 . I type in sudo shutdown now. I get a recovery screen over and over. I select repair. It goes through a thousand lines of code. It still does the same thing aferward.

I load gnome onto the server, from gnome the system shutdown and power of with no problems.

What is going on here?

---

### Post by CharlesA on 2011-03-06
Try using halt instead:

```
sudo halt
```

---

### Post by BkkBonanza on 2011-03-06
I've always used **sudo poweroff** and it's worked. Not sure what the difference is and the man page doesn't clarify.

---

### Post by CharlesA on 2011-03-06
> **BkkBonanza said:**
> I've always used **sudo poweroff** and it's worked. Not sure what the difference is and the man page doesn't clarify.
I checked out the manpage for halt and it said this:

```
HALT(8)

NAME
       halt, reboot, poweroff - stop the system.

SYNOPSIS
       /sbin/halt [-n] [-w] [-d] [-f] [-i] [-p] [-h]
       /sbin/reboot [-n] [-w] [-d] [-f] [-i]
       /sbin/poweroff [-n] [-w] [-d] [-f] [-i] [-h]

```

The manpage for shutdown was a bit different:

```
SHUTDOWN(8)

NAME
       shutdown - bring the system down

SYNOPSIS
       /sbin/shutdown [-akrhPHfFnc] [-t sec] time [warning message]

```

---

### Post by macstl on 2011-03-06
Sudo halt works fine from the cmd line. Thanks for advise.

---

