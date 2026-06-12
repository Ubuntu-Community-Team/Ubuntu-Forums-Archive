---
title: "SSH identity changed on new Server"
date: 2008-01-02
forum: Server Platforms
---

### Post by feenster on 2008-01-02
Hi all,
I run a Ubuntu data server, with clients rsync'ing their data onto it via SSH. This was running 6.10, but i've upgraded to 7.10 today. 

Everything has gone fine except that the SSH identity of the Server has changed. As my clients use password-less authentication using private keys, this is a bit of a pain as no-one can send any data (we use custom made software that doesn't give them the opportunity to accept the new host).

Is there any way to change the SSH identification back to what it was? I installed on a new hard drive, so everything else from the working install of 6.10 remains intact. The IP address and hostname are the same too.

Any help would be greatly appreciated.

Matt

---

### Post by andol on 2008-01-02
The files you are looking for are: /etc/ssh/ssh_host_*

---

### Post by feenster on 2008-01-02
> **andol said:**
> The files you are looking for are: /etc/ssh/ssh_host_*

Hi,
But to get things running, do I just replace them completely? There are 4 (2 for RSA and 2 for DSA).

Matt

---

### Post by andol on 2008-01-02
Yes.

You might have to restart your sshd as well.

---

### Post by feenster on 2008-01-02
> **andol said:**
> Yes.

You might have to restart your sshd as well.

Many thanks - i'll try it now and get back to you :)

Matt

---

### Post by feenster on 2008-01-02
> **andol said:**
> Yes.

You might have to restart your sshd as well.

Andol,
Thanks you - you have saved me many hours frustration. It works perfectly :-)

Matt

---

### Post by andol on 2008-01-02
> **feenster said:**
> Andol,
Thanks you - you have saved me many hours frustration. It works perfectly t
Well, if you ever run into me in a pub, and you actually realize that it is me, I expect you to buy me a drink :-P

---

### Post by feenster on 2008-01-02
Hehe! Of course, I would be happy to.

Matt

---

