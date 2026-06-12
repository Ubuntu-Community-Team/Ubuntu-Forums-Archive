---
title: "LAMP Server configuration and hardening guides?"
date: 2006-06-27
forum: Server Platforms
---

### Post by auspuff on 2006-06-27
So i installed and configured my very own LAMP server using ubunto dapper server edition! hurray! ;-)

i really like it so far ... there is loads of information to be found on how to install everything i need. so i,ve got ssh login working, sftp working, mysql configured etc etc and everything is working fine ... 

but ... with all this talk from paranoid *nix administrators i do not feel quite comfortable to actualy use the server to run a public website.

There are many good guides to get everything installed and running quickly but i have not yet found a good guide to properly configure a fairly secure LAMP server.

I just want to make shure that i,m not overlooking anything or doing something really stupid ;-)

---

### Post by harisund on 2006-06-27
Ok give me your IP address and I will let you know how secure your machine is ;)

hehe just kidding. I have my machine setup the exact same way that you are talking about right now .. and I am also searching for some "secure" stuff.. not that I have found any or am desperate to find any, but every bit will be of help. 

Anyone?

---

### Post by houstonbofh on 2006-06-29
It is quite secure by default.  Be careful what cgi scripts you dump into it.  Be careful of the file systems below it.  Apply security patches regularly.  Most of the exploits you hear of are part of packages installed *after* the system is running.

---

### Post by auspuff on 2006-06-30
What do you mean by "Be careful of the file systems below it." ?

---

### Post by auspuff on 2006-06-30
i stubled upon this guide via digg and it seems very thorough:

[http://www.freesoftwaremagazine.com/articles/hardening_linux](http://www.freesoftwaremagazine.com/articles/hardening_linux)

---

### Post by houstonbofh on 2006-07-03
[QUOTE=auspuff]What do you mean by "Be careful of the file systems below it." ?[/QUOTE]
Don't put a link to "/" or "/bin" or similar in your web pages... Obvious, I know, but still done far to often.

---

### Post by VileTimes on 2008-05-04
> **auspuff said:**
> i stubled upon this guide via digg and it seems very thorough:

[http://www.freesoftwaremagazine.com/articles/hardening_linux](http://www.freesoftwaremagazine.com/articles/hardening_linux)

Thanks for this. Still very relevant.

---

