---
title: "Intrusion attempt"
date: 2009-10-06
forum: Security
---

### Post by gnudoc on 2009-10-06
Found this in my auth.log from yesterday:

```
login[1107]: pam_unix(login:auth): check pass; user unknown
login[1107]: pam_unix(login:auth): authentication failure; logname=LOGIN uid=0 euid=0 tty=/dev/tty6 ruser= rhost= 
login[1107]: FAILED LOGIN (1) on '/dev/tty6' FOR 'UNKNOWN', Authentication failure
login[1107]: pam_unix(login:auth): check pass; user unknown
login[1107]: pam_unix(login:auth): authentication failure; logname=LOGIN uid=0 euid=0 tty=/dev/tty6 ruser= rhost= 
login[3317]: pam_unix(login:auth): check pass; user unknown
login[3317]: pam_unix(login:auth): authentication failure; logname=LOGIN uid=0 euid=0 tty=/dev/tty6 ruser= rhost= 
login[3317]: FAILED LOGIN (1) on '/dev/tty6' FOR 'UNKNOWN', Authentication failure
login[3317]: pam_unix(login:auth): check pass; user unknown
login[3317]: pam_unix(login:auth): authentication failure; logname=LOGIN uid=0 euid=0 tty=/dev/tty6 ruser= rhost= 
login[3317]: FAILED LOGIN (2) on '/dev/tty6' FOR 'UNKNOWN', Authentication failure
```

How rude!

From the timings (the three lines saying FAILED LOGIN are 5s apart), I'm guessing this is a bot, not a human. If anyone can tell me why that's a stupid assumption, please do.

Unfortunately, my router doesnt record failed attempts to connect, only successful ones, so I can't get any further info from there. Can anyone suggest any places to look for any interesting info about this attempt?

I don't particularly care about the computer in question, and will be wiping it.

Cheers,
gnudoc

---

### Post by gnudoc on 2009-10-06
I should maybe add that these definitely weren't local login attempts, nor from any computer that I control.

gnudoc

---

### Post by cariboo on 2009-10-06
I would suggest installing denyhosts, this will ban the ip the breakin attempts are coming from. Denyhosts is in the repositories.

---

