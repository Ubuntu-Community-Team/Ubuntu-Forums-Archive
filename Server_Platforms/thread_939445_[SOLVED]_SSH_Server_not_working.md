---
title: "[SOLVED] SSH Server not working"
date: 2008-10-05
forum: Server Platforms
---

### Post by Sid1980 on 2008-10-05
When i first installed SSH server and tunneled throught putty everything went fine but after one restart i am able to logon in server throught putty but not able to tunnel throught firefox,

I am using putty v0.60 8194 and trying to tunnel in WIn XP with a openSSH server on other end having default configuration.  

PS: port 8080 is forwarded. 

any comment or help will be appreciated.

---

### Post by Sid1980 on 2008-10-08
> **Sid1980 said:**
> When i first installed SSH server and tunneled throught putty everything went fine but after one restart i am able to logon in server throught putty but not able to tunnel throught firefox,

I am using putty v0.60 8194 and trying to tunnel in WIn XP with a openSSH server on other end having default configuration.  

PS: port 8080 is forwarded. 

any comment or help will be appreciated.

Okeh i figured out myself :)
i had to loopback and use 127.0.0.1 instead of server ip in SOCKS option of Firefox ;)

---

