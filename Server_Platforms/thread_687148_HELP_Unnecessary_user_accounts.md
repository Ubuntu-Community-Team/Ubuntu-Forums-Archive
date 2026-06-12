---
title: "HELP: Unnecessary user accounts"
date: 2008-02-04
forum: Server Platforms
---

### Post by cjtjamandra on 2008-02-04
Iam just wondering if any of these users in my server are necessary. can someone help me trim these list of users. Iam just worrying that one of these user accounts can be used by a hacker to get access to my server. please help. thx

---

### Post by p_quarles on 2008-02-04
Those are all normal system accounts. Whether they are necessary or not depends on what you are using the server for.

They do not pose a security risk, however. None of them have root access, and their privileges are limited to their individual function.

---

### Post by cjtjamandra on 2008-02-04
Thx for the clarification. iam just worried because before i have changed my ssh port, some attackers use some users in the list to try to access to my server.

BTW how can i check if a user has a root access? and how can i restrict other user to use su and sudo,and just allow it to a specific user. Thx in advance. :)

---

### Post by p_quarles on 2008-02-04
In a default Ubuntu setup, only the first user created has root access.

If you want to double check, you can get a list of groups that a user belongs to by running:
```
groups *username*
```
Only users that belong to either "admin" or "root" have the power to do anything of consequence to the system. 

The better way to lock down the system is to make SSH more secure. Personally, I use an alternate port and an RSA keypair for authentication. Doing this makes any unauthorized SSH access nearly impossible.

---

### Post by cjtjamandra on 2008-02-04
Well i have already changed my ssh port but not using a RSA. iam currently studying how to accomplish that, but never found a good tutorial yet.. BTW thx for the clarification.

---

### Post by p_quarles on 2008-02-04
RSA keys are pretty simple, actually. On the machine you want to SSH from (i.e., not the server), do this:
```
ssh-keygen -t rsa
```
Note that you do not need to enter a passphrase if you don't want to (I don't use one). Leaving the field blank will disable the passphrase altogether. 

Now, you need to move a copy of the newly created id_rsa.pub file to the server, and add it to your authorized keys. Once you moved the file to the server, run this:
```
ssh *username*@*hostname* "cat >> ~/.ssh/authorized_keys" < ~/.ssh/id_rsa.pub
```
Henceforth, you should be able to login with the rsa key instead of the password. 

Finally, to prevent anyone from logging in *without* the RSA key, edit the SSH server's configuration:
```
sudo nano /etc/ssh/sshd_config
```
Change the "PasswordAuthentication" field to "no." 

Lastly, be careful with the other part of the keypair: the id_rsa file. This should reside only on machines from which you want to access the server remotely. It's basically your new password for SSH, so treat it accordingly.

---

### Post by cjtjamandra on 2008-02-05
Thx for the tutorial.. But i have a question, what if i want to access my server using xp boxes aat different hosts? is it possible to use rsa in this situation? thx in advance

---

