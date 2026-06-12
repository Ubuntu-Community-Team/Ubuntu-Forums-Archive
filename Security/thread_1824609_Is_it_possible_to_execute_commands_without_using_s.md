---
title: "Is it possible to execute commands without using sudo ??"
date: 2011-08-14
forum: Security
---

### Post by arunb on 2011-08-14
Hi,

I found this site here which lists some dangerous commands..
[http://www.junauza.com/2008/11/7-deadly-linux-commands.html]("http://www.junauza.com/2008/11/7-deadly-linux-commands.html")

Can these commands be executed without using sudo ??

thanks
a

---

### Post by sidzen on 2011-08-14
Yes

---

### Post by scorp123 on 2011-08-15
> **arunb said:**
>  Can these commands be executed without using sudo ??

Yes. BUT: only "root" has enough power to really hose a system. If you execute those commands under your own 'normal' account chances are you will most likely only harm your own session or your own home directory ... in most cases you won't have the permissions needed to really hose the entire system. Only "root" could do that. Hence why executing some commands as a normal user isn't dangerous at all (because you're lacking the needed permissions to cause real damage) whereas using the same commands with a "sudo" is very very dangerous because as "root" you have infinite powers on the system and nothing can stop you from doing anything, even if it's something really harmful, stupid or dangerous.

---

### Post by Bachstelze on 2011-08-15
> **scorp123 said:**
> Yes. BUT: only "root" has enough power to really hose a system. If you execute those commands under your own 'normal' account chances are you will most likely only harm your own session or your own home directory ... in most cases you won't have the permissions needed to really hose the entire system. Only "root" could do that. Hence why executing some commands as a normal user isn't dangerous at all (because you're lacking the needed permissions to cause real damage) whereas using the same commands with a "sudo" is very very dangerous because as "root" you have infinite powers on the system and nothing can stop you from doing anything, even if it's something really harmful, stupid or dangerous.

Actually the forkbomb works as a user by default (you can prevent it by using limits but they aren't there by default).

---

### Post by scorp123 on 2011-08-15
> **Bachstelze said:**
> Actually the forkbomb works as a user by default  I know ;)  ... that's why I said *"_some_ commands ...*"* and *"... in most cases ...*"*
:D

Yes, the good old fork bomb will pretty much bring your system to a full stop even without root priviledges.

---

