---
title: "su login help- authorization failure"
date: 2008-08-26
forum: Security
---

### Post by josephellengar on 2008-08-26
Hiya guys!  I'm a real n00b when it comes to linux so please bear with me.  I'm using Ubuntu and the bash shell.  I have the ability to use sudo and put in the password. However, I am trying to edit my fstab file and they won't let me save the changes, and whenever I try to use su, with any options, they tell me that I have an authorization failure?  Any idea what could be up here?  Thanks.

---

### Post by kpatz on 2008-08-26
First you say you can use sudo, then you talk about using su?  They are two different commands.

Put "sudo" in front of the command, not "su" - so, "sudo vi /etc/fstab" for example.  Then enter your password if prompted.

---

### Post by Cheesehead on 2008-08-26
/etc/fstab is not in your home directory, so you *as a user* do not have permission to save it.

However, if you edit the file *as an admin* you can.
The easiest way is from the command line:
```
sudo gedit /etc/fstab
```

---

### Post by josephellengar on 2008-08-26
> **kpatz said:**
> First you say you can use sudo, then you talk about using su?  They are two different commands.

Put "sudo" in front of the command, not "su" - so, "sudo vi /etc/fstab" for example.  Then enter your password if prompted.

Yeah- I know that they are different commands.   I was just using that as an example of that I know my password.  For some reason, it won't let me use su.  I wanted to become a superuser so that I could edit my fstab file.

---

### Post by wgrant on 2008-08-26
> **idigchess said:**
> Yeah- I know that they are different commands.   I was just using that as an example of that I know my password.  For some reason, it won't let me use su.  I wanted to become a superuser so that I could edit my fstab file.

su wants the root password, which doesn't exist. Use sudo instead. See [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo).

---

### Post by Dr Small on 2008-08-26
> **idigchess said:**
> Yeah- I know that they are different commands.   I was just using that as an example of that I know my password.  For some reason, it won't let me use su.  I wanted to become a superuser so that I could edit my fstab file.
Use:
```
sudo vim /etc/fstab
```

To edit fstab with sudo rights, with vim.

---

