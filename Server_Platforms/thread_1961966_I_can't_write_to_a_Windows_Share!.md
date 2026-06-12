---
title: "I can't write to a Windows Share!"
date: 2012-04-20
forum: Server Platforms
---

### Post by Yoni5002 on 2012-04-20
Hello friends,

I have this issue that's been driving me nuts for a while...

I have a Windows server that is sharing a folder named SPAM. Basically this is an e-mail server that processes reported spam e-mails into that SPAM folder... all good, it works fine.

Now the headache:

My Ubuntu Server 10.04:

I have shared this SPAM folder in the Windows Server

I can mount the SPAM folder into my account in ubuntu server:

sudo mkdir /home/my_user/www/spam

Mount share to folder:

sudo mount -t smbfs //10.1.1.15/spam/ /home/my_user/www/spam -o rw,username=MYUSERNAME,password=MYPASSWORD

BUT I CANNOT WRITE TO IT unless I do SUDO!

mkdir test -> permission denied
sudo mkdir test -> WORKS!

That means my share is writable but I have to be root to write to it! WHY? 

I have tried chown and chmod the spam folder. I cannot write to it unless I sudo first... This is driving me nuts! Please help!

---

### Post by darkod on 2012-04-20
Wouldn't it be much easier to create a samba share and let windows write the spam emails to the share?

---

### Post by Jonathan L on 2012-04-20
Hi Yoni

> my share is writable but I have to be root to write to it! WHY? 

As you say, the share is working as a writeable share.  If you can't write to it, then it presumably is a normal permissions issue.

I'd suggest you check the permissions on the windows machine, and could you show us the ls -l output for the share and its directory?

Kind regards,
Jonathan.

---

### Post by Morbius1 on 2012-04-20
Give this a shot:

From this:
sudo mount -t smbfs //10.1.1.15/spam/ /home/my_user/www/spam -o rw,username=MYUSERNAME,password=MYPASSWORD

To this:
sudo mount -t smbfs //10.1.1.15/spam/ /home/my_user/www/spam -o rw,username=MYUSERNAME,password=MYPASSWORD,[COLOR=Blue]uid=my_user[/COLOR]

---

### Post by Cheesemill on 2012-04-20
> **Yoni5002 said:**
> sudo mkdir /home/my_user/www/spam

The mount point you created is owned by root because you used sudo to create the directory when you shouldn't have.

Unmount the share then run:
```
sudo chown user.user /home/user/www/spam
```replacing all instances of user with your username to give yourself ownership of the folder.
Remount the share and you should be good to go.

---

### Post by Yoni5002 on 2012-04-20
I figured it out. Basically I used the uid and gid. Thanks everyone for your help.

sudo mount -t smbfs //10.1.1.15/spam/ /home/www/spam -o uid=www-data,gid=www-data,username=***,password=***

I need apache to be able to write into it.
 
> Wouldn't it be much easier to create a samba share and let windows write the spam emails to the share?
No, it isn't in my case. That windows server is in production running e-mail for several domains and other servers are using it as a backend already. It will make it troublesome to point to the ubuntu server specially because I do not have root access to some of the servers pointing to that share.

@Cheesemill

Thanks a lot for your input.

---

