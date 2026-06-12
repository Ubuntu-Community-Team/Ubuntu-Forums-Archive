---
title: "privilege escalation using xsendkeys?"
date: 2009-01-31
forum: Security
---

### Post by ogcub on 2009-01-31
In the light of recently discovered windows flaw, I tried similar thing with ubuntu and it works. for example this python script
```
import time
import subprocess
time.sleep(5)
subprocess.Popen(["gksudo", "nautilus"]); #could be more interesting
time.sleep(5)
subprocess.Popen(["xsendkeys", '"p+p+a+s+s+w+o+r+d+Return+Return"'])

```

If gksudo dialog don't lose focus during those 5 seconds, password gets written and program is launched under root privileges, so if some program manages to keylog user password it could do anything on your system. Also some malicious program could try to brute-force your password this way, I think
Why xsendkeys are allowed to interact with gksudo dialog? isn't this some sort of security flaw?

PS. xsendkeys works buggy for me, first and last chars are skipped

---

### Post by ogcub on 2009-02-03
anyone?

---

### Post by movieman on 2009-02-03
> **ogcub said:**
> if some program manages to keylog user password it could do anything on your system

Yes.

Solution: don't get a keylogger installed on your system.

---

### Post by glotz on 2009-02-03
lol

---

### Post by movieman on 2009-02-04
Well, I actually agree that it would be nice if gksudo had a more secure means of reading keys to ensure they came from the keyboard rather than another program, but if someone has installed a keylogger on your system your security is already toast; just not quite burnt toast yet.

---

### Post by ogcub on 2009-02-07
> **movieman said:**
> Yes.

Solution: don't get a keylogger installed on your system.

So, in other words Ubuntu is as secure as windows XP with administrator account, just more hassle is needed.

I always thought that privilege elevation should require real user input

---

### Post by cariboo on 2009-02-07
The problem with your assumption is that someone installed a keylooger on your system. The only way that could happen is if you install it yourself, or if you leave the computer without logging out first.

It always come down to the fact that the biggest security risk is between the back of the chair and the keyboard.

Jim

---

### Post by movieman on 2009-02-07
> **ogcub said:**
> So, in other words Ubuntu is as secure as windows XP with administrator account, just more hassle is needed.

1. With an admin account, you're 'logged in as root'; absolutely anything can trash your entire system.

2. Ubuntu is designed more for ease of use than security; if you want a secure Linux, go for Red Hat/CentOS or a similar less 'user-friendly' distribution.

> I always thought that privilege elevation should require real user input

If you let someone install a keylogger on your system, you have bigger security flaws to worry about. Personally I'm far more worried about people stealing my online banking passwords than I am about them getting root access, and if they installed a keylogger, that's already done.

The other thing to remember is that X is client/server; it has no idea whether you're typing from the local keyboard or from a computer thousands of miles away. If it only accepted local keypresses for the password, then, for example, I'd be unable to peform GUI administration of my mythbuntu box from my laptop.

---

### Post by glotz on 2009-02-07
But, but... I like keyloggers on mah puter! ](*,)

---

