---
title: "[SOLVED] What is this and how should I react?"
date: 2008-07-14
forum: Security
---

### Post by nuddernuby on 2008-07-14
The following message was received while updating the system (8.04) and while opening SPM:

> 
Granted permissions without asking for password

The '/usr/sbin/synaptic' program was started with the privileges of the root user without the need to ask for a password, due to your system's authentication mechanism setup.

It is possible that you are being allowed to run specific programs as user root without the need for a password, or that the password is cached.

This is not a problem report; it's simply a notification to make sure you are aware of this.


I am unaware of having changed the security and guess that it would be better to be asked for a password.
Please advise what steps should be taken to rectify this.
Thank you

---

### Post by HermanAB on 2008-07-14
Don't worry about it.  The system uses Sudo with a timeout to avoid incessantly asking for the password.

Cheers,

Herman

---

### Post by mikewhatever on 2008-07-14
I've never seen such a message. Do you get asked for the password when opening Synaptic?

---

### Post by nuddernuby on 2008-07-17
Yes, I normally get asked for a password when opening Synaptic - that's why I found this unusual.

Thanks for your inputs.  I'll work on HermanAB's advice.

---

