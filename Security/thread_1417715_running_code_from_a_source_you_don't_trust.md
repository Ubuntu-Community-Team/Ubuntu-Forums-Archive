---
title: "running code from a source you don't trust"
date: 2010-02-27
forum: Security
---

### Post by ernest_francis on 2010-02-27
Ok, I have a bit of freelance work coming up to do some unit testing on some application code, but I don't trust anything as I am a paranoid ex windows users (spit) 

I was thinking of creating a temp user account and giving it as little privaleges as possible and then run that code from users that home directory, would this work.

If its a good idea... How do I do it ... complete newbie here sorry!!!! But I want to learn!!! And... I want to do it via the command line! Not the GUI, so anyone who can help

thank you!
Ernest

---

### Post by OpSecShellshock on 2010-02-27
Run it in virtual in a test environment, see what happens.

---

### Post by Bachstelze on 2010-02-27
If you really want to be paranoid, run the code in a VirtualBox, or even on a spare old machine if you have one. Maybe the code is an exploit to a yet-unknown kernal vulnerabiity that allows privilege escalation. ;)

---

### Post by ernest_francis on 2010-02-27
Thanks good idea, what is the best virtual s/w to use ? only non-commercial stuff pls, thanks ?

ernest

---

### Post by Bachstelze on 2010-02-27
> **ernest_francis said:**
> Thanks good idea, what is the best virtual s/w to use ? only non-commercial stuff pls, thanks ?

ernest

VirtualBox is probably good enough for what you want.

---

### Post by Agent ME on 2010-02-27
Running the code on a separate user account (like the guest account) will protect your personal files from it.

---

### Post by smackc on 2010-03-01
Can you read the code?

---

