---
title: "Any user can use Administrator password in GUI to Gain Admin privileges."
date: 2011-07-01
forum: Security
---

### Post by ahears on 2011-07-01
Any user can use Administrator password in GUI to Gain Admin privileges. I am the administrator, and any normal desktop user can use the password from my account to grant system changes, mount drives, etc. 

My /etc/sudoers file is as follows:

> 

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#        
Defaults    env_reset,editor=/usr/bin/gedit,timestamp_timeout=0

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Allow members of group sudo to execute any command after they have
# provided their password
# (Note that later entries override this, so you might need to move
# it further down)
[COLOR=Red]%sudo ALL=(ALL) ALL[/COLOR]
#
#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
[COLOR=Red]%admin ALL=(ALL) ALL[/COLOR]

I have created several accounts for testing, removed all privileges, and am still able to gain Administrator status by using the admin password through the GUI while logged in as another user. Programs like synaptic won't run (the process cancels itself) but **System >> Administration >> Users and Groups** will allow access, and with the right password any user can elevate themselves. This is not available on the command line. Root account does not exist, and I am the only admin. I want an account open to guests however I can't do this if they can elevate.  How do I stop others from being able to elevate to make changes or gain Administrator privileges? Please help.

---

### Post by sisco311 on 2011-07-01
> **ahears said:**
> This is not available in the command line.


Yes it is:
```
su - **admin-username**
```

> **ahears said:**
> 
How do I stop others from being able to elevate to make changes or gain Administrator privileges? Please help.

Use a strong password and don't tell them what it is. ;)

> **ahears said:**
> 
I want an account open to guests


Search for `Ubuntu kiosk mode'

---

### Post by haqking on 2011-07-01
> **ahears said:**
> . I want an account open to guests however I can't do this if they can elevate.  How do I stop others from being able to elevate to make changes or gain Administrator privileges? Please help.


Dont let them know the password and make yours a strong one ?

of course they can elevate if they know the password, if someone else has your front door key they can open your front door ?

or am i missing something ?

---

### Post by ahears on 2011-07-01
Fair enough. Maybe I'm trying too hard. I want specific programs to fail execution dispite entering an admin password, like Synaptic. It fails even if I get the password correct. Why can't I force **System >> Administration >> Users and Groups** to behave the same? I really not willing to give up yet, but if I must... I must.

---

### Post by jerome1232 on 2011-07-01
> **haqking said:**
> Dont let them know the password and make yours a strong one ?

+1, if they know your password what's to prevent them from simply logging in as you anyways.

---

### Post by ahears on 2011-07-01
> **jerome1232 said:**
> +1, if they know your password what's to prevent them from simply logging in as you anyways.

Yeah...I know, I was thinking of allowing a guest to remote login...bla...bla... but I didn't want any user to get prompted for a password, I simply wanted the attempt to fail (I.e Synaptic), even if they get the password right. As they say; "A computer system is only as secure as its' weakest user."

---

### Post by uRock on 2011-07-01
Moved to *"Security Discussions"*

---

### Post by sisco311 on 2011-07-01
> **ahears said:**
> Fair enough. Maybe I'm trying too hard. I want specific programs to fail execution dispite entering an admin password, like Synaptic. It fails even if I get the password correct. Why can't I force **System >> Administration >> Users and Groups** to behave the same? I really not willing to give up yet, but if I must... I must.

synaptic uses sudo (more precisely gksu which is a GUI frontend for sudo).

users-admin (aka **System >> Administration >> Users and Groups**), like most modern GUI applications, uses polkit (PolicyKit).

---

### Post by ahears on 2011-07-01
> **sisco311 said:**
> synaptic uses sudo (more precisely gksu which is a GUI frontend for sudo).

users-admin (aka **System >> Administration >> Users and Groups**), like most modern GUI applications, uses polkit (PolicyKit).

GREAT ANSWER!! Thank you, it helps to understand! I knew they were different. :)

Now, for the tough question: **Where do I get a Policy Kit that I can configure easily?**

And: 

What is the reason for the differences in how the security is controlled?

> 

synaptic uses sudo (more precisely gksu which is a GUI frontend for sudo).

users-admin (aka **System >> Administration >> Users and Groups**), like most modern GUI applications, uses polkit (PolicyKit).



---

### Post by cariboo on 2011-07-01
If anyone has physical access to your computer, they don't have to guess your password, they already have root access with a simple reboot.

---

### Post by ahears on 2011-07-01
> **cariboo907 said:**
> If anyone has physical access to your computer, they don't have to guess your password, they already have root access with a simple reboot.
 
If you are referring to editing grub from boot, my boot process can only be edited in grub with a admin password. It's a sha-256 bit hash value stored in the /boot/grub/grub.cfg and it prevents tampering. The Trusted Platform Module also stores the keys to the HDD Password and cannot be used if separated from the system. The massive control I get from the TPM in Windows is the only reason I keep it. (Except to test it). If I could get an equivalent program in Ubuntu to manage my TPM I would probably eliminate Windows.

[U]**However we are completely off of the topic.**
[/U]

---

