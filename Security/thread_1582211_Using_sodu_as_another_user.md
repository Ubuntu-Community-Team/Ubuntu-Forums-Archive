---
title: "Using sodu as another user?"
date: 2010-09-26
forum: Security
---

### Post by Fafler on 2010-09-26
This is probably trivial, but i can't seem to find the solution myself. I have donated my old laptop to a "public" one for everyone that hangs around my house. I've made a extra user account on it, so now it has two, one for me (fafler) and one for everyone else (bruger). Fafler can sudo to do stuff as root, bruger cannot, as i wrote the password on the laptop and i don't want anyone to mess it up beyond making another clean account.

Now, to get root access from the bruger account, i need to
```
bruger@carbon:~$ su -c "sudo whoami" fafler
Password: 
[sudo] password for fafler: 
root
bruger@carbon:~$
```
and i need to sype my password twice. 

So, how do i setup sudo to ask for fafler's password instead? Or are there any other neat tricks to get around this?

---

### Post by Ryan Dwyer on 2010-09-26
Add bruger to the admin group.

When logged in as fafler (who has sudo rights):
sudo adduser bruger admin

---

### Post by endotherm on 2010-09-26
assuming you want to keep bruger a standard non-admin user, you need the account password to su, but that is happening in the shell that bruger invoked, so when the shell for fafler is invoked, sudo still wants to ask for a password. you need sudo though, so as it stands, there isn;t much you can do without altering sudo or removing the need for it. 

one option is to remove the password requirement for fafler to common commands you use as bruger via the visudo. this would remove the second password for those commands only however. [https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

another option, though I am loathe to suggest it, is to enable the root account. if you su root, there would be no need to use sudo. you may be able to do it without enabling root, but I'm not sure that su works exactly the same if the account is locked. if you want to enable root, give it a quick google. you;ll find what you seek easily.

---

### Post by Fafler on 2010-09-26
I do not want bruger to have admin rights for the reason explained above. Enabling the root account might be the best option. I'm a long time Debian user and i have good su habits.

I just thought this would be a common issue with a better workaround than this.

---

### Post by CharlesA on 2010-09-26
Not quite sure you can do that. When I've messed with user accounts that doesn't have access to sudo, I've always had to su to someone who has admin rights then use sudo.

That being said, I don't have the root account enabled, so I guess that might be an option, as long as you have a strong password and know to only use root for admin stuff (which you would, since you've used Debian)

---

