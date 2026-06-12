---
title: "Changed master password, refuses to change back"
date: 2010-08-06
forum: Security
---

### Post by BastardNamban on 2010-08-06
I have an odd, simple problem. My previous root password was a single character long (I know, I know- dangerous). I changed it through the panel 
user icon last night to something long, and today, trying to change it back refuses anything one-character, or even 4 or 5 character, for that matter. 
Keyring is asking for my old password, but Ubuntu won't let me change back to it.

Ideally, I wanted to log in under a simple password, and make a different root password, but I don't know if that's possible to do and keep my user name. 
I'm new to password management. Can anything here be done, or anyone have suggestions?

---

### Post by sisco311 on 2010-08-06
> **BastardNamban said:**
> 
Ideally, I wanted to log in under a simple password, and make a different root password, but I don't know if that's possible to do and keep my user name. 


As root you can set a weak password for your user. 

You can set up a root password and configure sudo to prompt for the target user's password (by default root). Just edit the sudoers file and append the Defaults line with **,targetpw**.

To configure policykit to prompt you for the root password, rename the /etc/polkit-1/localauthority.conf.d/51-ubuntu-admin.conf file to /etc/polkit-1/localauthority.conf.d/49-ubuntu-admin.conf. You may have to repeat this step every time when policykit is upgraded.

For details, check out:
[uhelp]community/RootSudo[/uhelp]
[uhelp]community/Sudoers[/uhelp]
and
[http://hal.freedesktop.org/docs/polkit/](http://hal.freedesktop.org/docs/polkit/)
[http://hal.freedesktop.org/docs/polkit/pklocalauthority.8.html](http://hal.freedesktop.org/docs/polkit/pklocalauthority.8.html)
and, of course the man pages:
```
man sudo 
man sudoers
man polkit
man pklocalauthority
```

---

### Post by BastardNamban on 2010-08-06
Sisco, thank you. I didn't know you could do that, quite interesting. If you have to rename though, how often is policykit updated? Is that something pretty often, or rare?

What confuses me more than anything is how I could have the original password as a single character (same password for root as login), but it won't let me change it back to the same thing. Any explanation on how this happened, and allowed the first one in the first place?

---

### Post by sisco311 on 2010-08-06
> **BastardNamban said:**
> Sisco, thank you. I didn't know you could do that, quite interesting. If you have to rename though, how often is policykit updated? Is that something pretty often, or rare?


Hmmm ,if you create a new file in the /etc/polkit-1/localauthority.conf.d/ directory, i.e. 52-root-pw.conf with the following content:
```
[Configuration]
AdminIdentities=unix-user:0

```
then you don't have to worry about the upgrades.

I guess, I should re-read the polkit documentation :)


> **BastardNamban said:**
> 
What confuses me more than anything is how I could have the original password as a single character (same password for root as login), but it won't let me change it back to the same thing. Any explanation on how this happened, and allowed the first one in the first place?

During the installation you are allowed to set up a weak password.

---

### Post by BastardNamban on 2010-08-06
> **sisco311 said:**
> 
During the installation you are allowed to set up a weak password.

Is there no way to redo that without reinstalling?

If really not, I'll just make a simple logon, and a complex root password.

---

### Post by sisco311 on 2010-08-07
> **BastardNamban said:**
> Is there no way to redo that without reinstalling?

If really not, I'll just make a simple logon, and a complex root password.

Once again, as root you can change your user's password to a weak one... Simply run the **passwd username** command as root (where **username** is your login name).

---

