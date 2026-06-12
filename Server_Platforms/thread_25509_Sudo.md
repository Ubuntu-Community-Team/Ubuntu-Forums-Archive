---
title: "Sudo"
date: 2005-04-10
forum: Server Platforms
---

### Post by MWAAAHAAA on 2005-04-10
Hi,

I'm quite new to this whole sudo business. I read about the philosophy behind it, and it sounds all quite interesting, except that in practice, I'm experiencing the following. Whenever I'm using sudo I only have to enter my password once. After it has been entered I can sudo all I want without having to enter a password again, until I close the shell I have been working in. Is this normal behavior for sudo? If so I can't possible imagine why this would be "safer" than su -c "" 'ing.

---

### Post by kiddo on 2005-04-10
I THINK that's because it would be a lot safer to login as a sudoer, by ssh for example, than logging in as root. Please someone confirm/correct.

---

### Post by oracledarren on 2005-04-10
Hi

I had this problem too and corrected it by doing the following:-

open a terminal

sudo visudo and enter your password

look for the line

Defaults !lecture,tty_tickets,!fqdn

and add to it

,timestamp_timeout=0

and save it with control x and when you are finished close the terminal

this is the timeout period that is set by default before you have to re-enter your password.  By setting it to 0 it will ask everytime

Hope this helps

---

### Post by MWAAAHAAA on 2005-04-10
Yep, it helped!

---

### Post by gheorghe_pop on 2005-04-11
Is it wrong to set myself member of the sudo group?

---

