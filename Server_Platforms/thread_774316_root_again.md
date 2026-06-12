---
title: "root again"
date: 2008-04-29
forum: Server Platforms
---

### Post by dave103 on 2008-04-29
Hi

Following on from my last problem trying to recover sudo rights, what is the best way to deal with the fact that while there is no root user on installing 8.04, all files and folders are installed with owner and group set to root!!

So for example, if (as I tried and screwed up last time) I want to edit my apache config file what is the preferred way of doing it?  Should I change ownership of the apache folder (I suspect that would be a bad idea) or can I make myself part of the "root" group.   If so, how do I do it safely - last time I tried I lost admin rights for some reason.

What do you advise?

Dave

---

### Post by moonpup on 2008-04-29
No, do not change the ownership of those directories. By default the first user account you create in ubuntu is added to the admin group which is effectively root. Everytime you use sudo to modify a file, start a service etc... you are running as root. I'm a redhat guy, but I believe I am correct and hopefully someone will correct me if i'm wrong :)

---

### Post by dave103 on 2008-04-29
> **moonpup said:**
> No, do not change the ownership of those directories. By default the first user account you create in ubuntu is added to the admin group which is effectively root. Everytime you use sudo to modify a file, start a service etc... you are running as root. I'm a redhat guy, but I believe I am correct and hopefully someone will correct me if i'm wrong :)

No I think you are wrong there - my one and only user (which has admin rights) does not run as root itself.  I got permission denied when I tried to do anything like chmod etc. Can I not make myself part of the "root" group?  If so how - I'm a bit paranoid to get this wrong again as last time required a whole re-install.

Dave

---

### Post by wirelessmonkey on 2008-04-29
No, moonpup is correct. Rather than using ~$ chmod filename, which will not work, use ~$ sudo chmod filename, which escalates your command to 'root' to chmod the file.

You do not, and probably should not, need to run as the root user account.  

See [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo") for more information.

Best of Luck

---

### Post by moonpup on 2008-04-29
wirelessmonkey has just explained it perfectly... so now I don't have to :)

---

