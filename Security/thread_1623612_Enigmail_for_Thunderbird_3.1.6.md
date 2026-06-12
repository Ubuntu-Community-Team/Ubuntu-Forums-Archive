---
title: "Enigmail for Thunderbird 3.1.6?"
date: 2010-11-16
forum: Security
---

### Post by PDA1 on 2010-11-16
For the life of me I can't get Enigmail to install on Thunderbird 3.1.6.

Any ideas how to solve the problem?

All I really want to do is digitally sign my emails for security reasons.  Can you recommend some other add-on for TB that would do the trick?

Thanks

---

### Post by cariboo on 2010-11-16
How are you trying to install enigmail? I just install it from the repositories.

---

### Post by PDA1 on 2010-11-17
I installed it from Synaptic.

It sort of runs on one of my machines but won't generate some sort of key when using the set up wizard.

On the other machine it doesn't appear at all in TB.

---

### Post by DZ* on 2010-11-17
> **PDA1 said:**
> It sort of runs on one of my machines but won't generate some sort of key when using the set up wizard.

Do you already have a gpg keypair? It may take a long time for enigmail to generate it. You could try doing that manually
```
gpg --gen-key
```
If it takes too long, try to cat something big to /dev/null, while gpg is working on generating the keypair, e.g.
```
cat /usr/bin/* > /dev/null
```

> **PDA1 said:**
> On the other machine it doesn't appear at all in TB.

Is it listed and enabled under Tools -> Add-ons -> Extensions?

---

### Post by cariboo on 2010-11-17
If enigmail is installed properly, you should have a menu item for it called **OpenPGP**

---

### Post by PDA1 on 2010-11-17
No, it doesn't appear in Extensions.

I generated a key using your instructions.

What am I supposed to do with it  now?

---

### Post by DZ* on 2010-11-17
> **PDA1 said:**
> No, it doesn't appear in Extensions.

I generated a key using your instructions.

What am I supposed to do with it  now?

Restart Thunderbird and run OpenPGP Setup Wizard again. It should pick up the key.

I don't know what to do about the second computer where the extension doesn't show up. Perhaps you could rename the ~/.thunderbird directory and copy over the one from the second computer where it shows up (I think it used to be ~/.mozilla-thunderbird before 10.04).

---

### Post by PDA1 on 2010-11-17
It works!

I did just as you said and all is well.


What is the purpose of using those fancy "Certificates" in sending email?

---

### Post by oiram on 2010-11-25
> **PDA1 said:**
> 

What is the purpose of using those fancy "Certificates" in sending email?



is it a REAL question? or you just playing stupid?

---

