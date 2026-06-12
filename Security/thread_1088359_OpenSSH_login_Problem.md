---
title: "OpenSSH login Problem"
date: 2009-03-05
forum: Security
---

### Post by bilal_jan on 2009-03-05
hello everyone
i have installled OpenSSH Client and server on my two PCs both running Ubuntu 8.10... One problem wh i am facing and i wasnt able to correct that error is that whenever i wanna logon to my server (running OenSSH server) from my client machine(running OpenSSH client)... 
i was prompted for passowrd thress times(first time i enered password it was rejected so is passowrd entered second and third time) and at last i was given that error


```
permission denied : (Public key, Password)
```
i am entering pasword of my local machine but it was rejected ... i dont know wh other password to enter in order to get connected.
thanks for ur consideration

---

### Post by brian_p on 2009-03-06
> **bilal_jan said:**
> 

i am entering pasword of my local machine but it was rejected ... 

The password should be the one for the account on the server.

---

### Post by Dr Small on 2009-03-06
You need to enter the password of the account on the remote machine, not the local machine.

---

