---
title: "Need to run a script as different user"
date: 2011-01-26
forum: Server Platforms
---

### Post by gyzer on 2011-01-26
I'm currently writing some backup scripts for my headless ubuntu 9.10 server. I'm running virtualbox and I need to backup the vdi files. I'm going to be using the VBoxManage clonehd command to clone the vdi files to my backup hard drive. I first need to run the VBoxManage controlvm vm acpipowerbutton to shutoff the vms. This command has to be run under a user called vbox. The rest of my script needs to run under root. How can I run the virtualbox parts of my script as the vbox user and the rest of the script as root?

---

### Post by Darkness Des on 2011-01-26
I recommend just prefixing that command with sudo so that it is run as root, as Root contains all privileges and is in all groups (to the best of my knowledge).

---

### Post by gyzer on 2011-01-26
I've tried adding that to the line in the script where I run the VBoxManage changevm vm acpipowerbutton command and that doesn't work. That command will not run properly unless its run as the vbox user.

---

### Post by arrrghhh on 2011-01-26
su -c?

---

### Post by koenn on 2011-01-26
> **arrrghhh said:**
> su -c?
yeah.
```
su vbox -c changevm ... 
``` or something

---

### Post by gyzer on 2011-01-26
I think I tried that, but I'll go ahead and try that again. Remember I need to do su vbox -c within a script that is run by root.

---

### Post by datamove on 2011-01-27
you can also compose a line in /etc/sudoers

userid ALL=(vbox) NOPASSWD: /your/command

where userid is who runs the script. Then just use sudo /your/command

should work

---

### Post by gyzer on 2011-01-27
I found that when you use
su user -c 

You have to put the command in quotes like
su user -c "command" and that worked perfectly

---

### Post by jmaltube on 2011-08-21
> **gyzer said:**
> I found that when you use
su user -c 

You have to put the command in quotes like
su user -c "command" and that worked perfectly

What if the user i need to use has a password?. How do i include the password in the command?

---

### Post by SeijiSensei on 2011-08-21
The root user can run jobs as another user without requiring a password.

---

