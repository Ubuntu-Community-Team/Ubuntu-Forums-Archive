---
title: "Identify which application wants keyring access?"
date: 2010-05-02
forum: Security
---

### Post by mixim on 2010-05-02
Hello guys, is there a way to identify exactly what application is asking for keyring access at the given time?

I get this query every boot and it's getting annoying...

The annoyance is there, but more importantly and from a personal security standpoint on desktop systems, it's pretty bad that it doesn't say what application want's the access.

If there is some way, please share it with me!

// Regards Joakim from Sweden

---

### Post by cariboo on 2010-05-02
The way to stop the message is to either disable auto-login, or create a blank password for the keyring. Go to Applications->Accessories->Passwords and Encryption Keys, right-click login and select change password.

The preferred method is to disable auto-login.

---

### Post by mixim on 2010-05-03
> **cariboo907 said:**
> The way to stop the message is to either disable auto-login, or create a blank password for the keyring. Go to Applications->Accessories->Passwords and Encryption Keys, right-click login and select change password.

The preferred method is to disable auto-login.


Thank you for your answer. But I'm actually fine with the keyring prompt whenever an application needs a password. Don't really want to disable it, but still would like to know what app is asking for it. Right now, mostly out of curiosity.

Is this possible in any way?

---

### Post by cariboo on 2010-05-03
It would help if you told us a little more about your setup, do you connect to the network via wireless?

---

### Post by mixim on 2010-05-03
> **cariboo907 said:**
> It would help if you told us a little more about your setup, do you connect to the network via wireless?

10.04 LTS - Fresh install. No, i'm using network via cable, network manager is disabled on boot. Anything other i should add?

---

### Post by mortti on 2010-05-09
I have the exact same problem with 10.04 fresh install and it gets annoying.

---

### Post by cariboo on 2010-05-09
Basically all entering your password does is to open the keyring, so you have access to your ssh and gpg keys.

My post #2 tells you how to bypass it.

---

### Post by mixim on 2010-05-10
> **cariboo907 said:**
> Basically all entering your password does is to open the keyring, so you have access to your ssh and gpg keys.

My post #2 tells you how to bypass it.

Yeah did this at the end, but a shame there is only a workaround and not a real way to identify what application is asking for the keyring.

---

