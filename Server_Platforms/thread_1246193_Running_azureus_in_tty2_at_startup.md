---
title: "Running azureus in tty2 at startup"
date: 2009-08-21
forum: Server Platforms
---

### Post by bferd on 2009-08-21
Is there any way to do this? I start it at the prompt with

```
$ java -jar /usr/share/java/Azureus2.jar --ui=console
```

and I can get it to run at startup using the Webmin Bootup and Shutdown script:

```
#!/bin/sh
java -jar /usr/share/java/Azureus2.jar --ui=console 
```

I'd like to get this running in tty2 if possible.

Any help is appreciated.

---

### Post by cdenley on 2009-08-21
You can try editing the last line in /etc/event.d/tty2.
```

exec /usr/bin/sudo -u usertorunas /usr/bin/java -jar /usr/share/java/Azureus2.jar --ui=console

```

This may start before you have a network connection established. I'm not sure if that would be a problem.

---

### Post by bferd on 2009-08-21
> **cdenley said:**
> You can try editing the last line in /etc/event.d/tty2.
```

exec /usr/bin/sudo -u usertorunas /usr/bin/java -jar /usr/share/java/Azureus2.jar --ui=console

```

This doesn't work, it causes tty2 to not to spawn at all.

---

### Post by cdenley on 2009-08-21
> **bferd said:**
> This doesn't work, it causes tty2 to not to spawn at all.

It should launch the given command instead of the original getty command. You can try tweaking the command or remove "respawn". Maybe I made a mistake. I haven't tried this since edgy, though. Perhaps it works differently. You did replace "usertorunas" with the appropriate user, right?

---

### Post by bferd on 2009-08-21
> **cdenley said:**
> You did replace "usertorunas" with the appropriate user, right?

Nope I'm stupid. I think I forgot to tell you. :lol:
I'll try that.

What do you mean remove "respawn"?

---

### Post by bferd on 2009-08-21
Still can't get it to work.

---

### Post by bferd on 2009-08-22
Anybody?

---

