---
title: "OS integrity"
date: 2023-08-30
forum: Server Platforms
---

### Post by xekamtyap on 2023-08-30
I have rented a server, and it's running Ubuntu Server 22.04. I noticed that the provider has modified the base OS and installed a custom package to /sbin/. However, I am unaware of the other changes they have made or the additional packages or scripts that are currently running. How can I determine the extent of these changes? Is there a specific method or service I can employ to identify these modifications?

Furthermore, which directories should I inspect for these changes? Should I focus on /bin, /sbin, /etc, /lib, and /usr?

---

### Post by QIII on 2023-08-30
Is this a hardware server or a virtual machine?

---

### Post by Rubi1200 on 2023-08-30
Hi and welcome to the forums :-)

Firstly, I sincerely hope you are not running or storing anything sensitive on a rented server.

If you want to monitor what is going on take a look at inotifywait to monitor file and directory changes.

There are other, more powerful, auditing tools but you might be in breach of rental terms by installing them.

---

### Post by xekamtyap on 2023-08-31
> **QIII said:**
> Is this a hardware server or a virtual machine?
virtual machine 

> **Rubi1200 said:**
> 
If you want to monitor what is going on take a look at inotifywait to monitor file and directory changes.

There are other, more powerful, auditing tools but you might be in breach of rental terms by installing them.

I'm not seeking monitoring because I'm uncertain about the system files to begin with.

---

### Post by QIII on 2023-08-31
VPS vendors generally like to add some things to harden the OSes they provide.  That protects you and everyone else from the mistakes -- or even outright malfeasance -- of others living on the same hardware.

If your customer service is worth a hill of beans, they'd be happy to tell you what they have done.  I wouldn't put to much sweat into finding that stuff for yourself until you talk to them.

---

### Post by xekamtyap on 2023-08-31
> **QIII said:**
> VPS vendors generally like to add some things to harden the OSes they provide.  That protects you and everyone else from the mistakes -- or even outright malfeasance -- of others living on the same hardware.

If your customer service is worth a hill of beans, they'd be happy to tell you what they have done.  I wouldn't put to much sweat into finding that stuff for yourself until you talk to them.


t's generally more productive to refrain from posting if you don't have relevant information or assistance to provide regarding someone's question.

---

### Post by QIII on 2023-08-31
I believe "It would be easier for you to ask your vendor than to use your time looking for what they can explain to you easily" is a perfectly reasonable answer.

That said, it is generally a good idea to avoid antagonizing those providing advice ... particularly a forum Admin.

---

