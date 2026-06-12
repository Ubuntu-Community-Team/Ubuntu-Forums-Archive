---
title: "Unable to login using su or sudo!....."
date: 2010-10-18
forum: Security
---

### Post by VcDeveloper on 2010-10-18
At the terminal prompt, I can't login using su nor sudo.  I can only login as root at the dialog level. How do I correct this?

---

### Post by sikander3786 on 2010-10-19
Does it give any ouput like "you are not on the sudoers list" or something like that when you use sudo?

Post the error messages, they might be helpful in understanding the current situation.

---

### Post by VcDeveloper on 2010-10-19
> **sikander3786 said:**
> Does it give any ouput like "you are not on the sudoers list" or something like that when you use sudo?

Post the error messages, they might be helpful in understanding the current situation.

This is what I'm getting trying to su or sudo:
```
serveradmin@anointed:~$ su
Password: 
su: Authentication failure

```I use the same password for the gksu login dialog to use the terminal in su mode when I need to do admin commands.

---

### Post by sikander3786 on 2010-10-19
su account is disable by default in Ubuntu.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

You can use

```
sudo -i
```

We can help if you need some help regarding sudo.

---

### Post by VcDeveloper on 2010-10-19
Ok Thanks for your help!

---

### Post by cariboo on 2010-10-19
Running Maverick su only allows you to **s**witch **u**ers. For example if you have two or more users you can switch to another user:

```
cariboo@natty:~$ su me
Password: 
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

me@natty:/home/cariboo$
```

---

### Post by VcDeveloper on 2010-10-27
Ok, Thanks for your help!

---

