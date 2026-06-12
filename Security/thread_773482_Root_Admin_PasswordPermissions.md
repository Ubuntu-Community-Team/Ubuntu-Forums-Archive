---
title: "Root Admin Password/Permissions"
date: 2008-04-28
forum: Security
---

### Post by kc5rbx on 2008-04-28
I recently installed AVG/Linux.  I need to configure the license key; however, when I input the appropriate info into app and select OK, a dialog box indicates that I don't have rights to add/change license and then opens a password dialog box for root user (super user) password.

I am the only configured user of the system.

(1) How do I determine what that password is (I installed Ubuntu from provided CD and have made no password changes, so this root/superuser password must have been created by Ubuntu during installation).

(2) How do I change the root/superuser password so that I can make needed application and service changes to my system?

Thanks for your help.

---

### Post by Dr Small on 2008-04-28
You should use Sudo. It will be *your* password, as there is not a password setup for root by default.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Dr Small

---

### Post by tliotis on 2008-04-29
thanks Dr Small i have the same problem thanks for the link

---

### Post by kc5rbx on 2008-04-29
Dr. Small-- being new to Linux, I'm not clear on how I login to root using sudo such that it allows me to use the an application launcher from the desktop. I've recently installed AVG/Linux and would like to update the app, but get the following error msg:

Update process failed.
Reason: Sorry, you do not have permission to execute avgupdate.

The link you provided gives a lot of command line examples, which I've attempted, but I'm not familiar with how to initiate avggui update from cmd line.

Could you possibly provide some spoon-feeding here?

Thanks again.

---

### Post by Dr Small on 2008-04-29
Well, I don't have AVG here, so I'll try to go on the error you posted.
You could try:
```
gksudo avgupdate
```

And see if it will run the update for the application.
Gksudo == Graphical Super User Do

---

### Post by lemming465 on 2008-04-29
Typically you don't set a root password on ubuntu; just do *sudo bash* when you need a root shell.

If you have to set a root password, the command would be *sudo passwd root*.

If you are tired of having a root password, lock the account (prevents interactive logins, not sudo, boot, etc.) with *sudo passwd --lock root*

---

### Post by bodhi.zazen on 2008-04-29
> **lemming465 said:**
> Typically you don't set a root password on ubuntu; just do *sudo bash* when you need a root shell.

If you have to set a root password, the command would be *sudo passwd root*.

If you are tired of having a root password, lock the account (prevents interactive logins, not sudo, boot, etc.) with *sudo passwd --lock root*

sudo bash works, but the preferred method, IMO, is :

```
sudo -i
```

for graphical applications you should use gksu (kdesu on kubuntu).

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

gksudo : [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Setting a root password is discouraged and I can think of only 1 thing it is needed for. The root account should then be locked again.

---

