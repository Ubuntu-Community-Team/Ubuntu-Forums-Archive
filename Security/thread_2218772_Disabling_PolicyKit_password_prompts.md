---
title: "Disabling PolicyKit password prompts"
date: 2014-04-21
forum: Security
---

### Post by Ani on 2014-04-21
To make my system more secure I want to disable all PolicyKit password prompts when I am logged in as a user with account type of "Administrator".

Is there a way to auto-approve all PolicyKit password prompts?

---

### Post by bapoumba on 2014-04-22
I have a hard time relating increasing system security to disabling password prompts..

---

### Post by Ani on 2014-04-22
if a local user is compromised then it is easy to let's say add a phony "synaptic" in my path which then would prompt for a root password and by phishing that password you get elevated privileges from local to root.

if synaptic launches with no password prompt, and there are no superfluous password prompts then it gets much harder to phish for root password. therefore disabling password prompts makes the system more secure.

---

### Post by lisati on 2014-04-22
I don't see the point in phishing for a root password when it's disabled by default in Ubuntu.

---

### Post by bapoumba on 2014-04-22
> **Ani said:**
> if a local user is compromised then it is easy to let's say add a phony "synaptic" in my path which then would prompt for a root password and by phishing that password you get elevated privileges from local to root.

if synaptic launches with no password prompt, and there are no superfluous password prompts then it gets much harder to phish for root password. therefore disabling password prompts makes the system more secure.

Well, I’m not sure you realise what it would take to get into “your path” and access your password by either listening to the keystrokes you are doing or by deciphering the file where you password is stored.

But anyway, let’s say it is possible. Why bother if there is a user with admin access without a password ? Just get to that user and bam, party time. Whether you know if it is a european or an african swallow will be of no importance because there will be no one asking.

So I would not be too much worried about outside attacks in your case, unless you run a server with loose configurations. I would be much much more worried about what you could do to your own file system, in particular if you do not fully understand the need for a password and all the consequences if you disable it.

---

### Post by Ani on 2014-04-22
> **bapoumba said:**
> Well, I’m not sure you realise what it would take to get into “your path” and access your password by either listening to the keystrokes you are doing or by deciphering the file where you password is stored.

create an app called "synaptic" add it to your local path and make it pop up a simple gtk dialog asking for an administrator password.
> **bapoumba said:**
> 
But anyway, let’s say it is possible. Why bother if there is a user with admin access without a password ? Just get to that user and bam, party time. Whether you know if it is a european or an african swallow will be of no importance because there will be no one asking.

sudo will still be asking for a password. I am asking about disabling PolicyKit passwords not sudo passwords, so to gain full control of the system (sudo access) you still need to know the administrator password and PolicyKit password prompts are the best way to get to it.
> **bapoumba said:**
> 
So I would not be too much worried about outside attacks in your case, unless you run a server with loose configurations. I would be much much more worried about what you could do to your own file system, in particular if you do not fully understand the need for a password and all the consequences if you disable it.
I think I understand the consequences of disabling the PolicyKit password prompts better than you.

---

### Post by Ani on 2014-04-22
lisati, I am not asking about disabling the root password, I am asking about disabling PolicyKit password prompts which only allow you to launch various graphical apps like "synaptic" or "Software Center".

---

### Post by lisati on 2014-04-22
*cough*
 Ubuntu's root password is already disabled by default. 
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

:D

> **Ani said:**
> if a local user is compromised then it is easy to let's say add a phony "synaptic" in my path which then would [COLOR="#FF0000"]prompt for a root password[/COLOR] and by phishing that password you get elevated privileges from local to root.


> **Ani said:**
> lisati, I am not asking about disabling the root password, I am asking about disabling PolicyKit password prompts which only allow you to launch various graphical apps like "synaptic" or "Software Center".

---

### Post by bapoumba on 2014-04-23
PolicyKit works by specific groups, actions and effects I’m sure you already know that. Is this a test or what ?

---

