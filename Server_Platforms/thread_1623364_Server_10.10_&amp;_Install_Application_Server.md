---
title: "Server 10.10 &amp; Install Application Server"
date: 2010-11-16
forum: Server Platforms
---

### Post by madmondeoman on 2010-11-16
Hi
 
This is the first ubuntu server install I have done. I have got it installed and managed to install the GUI, the problem is I cannot seem to install the application center to get the server software to update etc so that I can install a browser etc.
 
[http://ubuntuhelpblog.wordpress.com/2010/10/11/ubuntu-tweak-ubuntu-10-10-maverick-0-5-7-released-a-ppa/](http://ubuntuhelpblog.wordpress.com/2010/10/11/ubuntu-tweak-ubuntu-10-10-maverick-0-5-7-released-a-ppa/)
 
I have followed this but ut doesnt seem to work. Could someone put me in the right direction.
 
Thanks
 
Shaun

---

### Post by BQAggie2006 on 2010-11-16
As this is your first server install and the utility you are trying to install is a third party application, it would probably be easier for you to use a native Ubuntu tool to install software.

View [this]("https://help.ubuntu.com/10.10/add-applications/C/installing.html#installing-others") guide that describes how to install software from Synaptic Package Manager, Ubuntu's GUI package manager.

If the Synaptic Package Manager is not an available option from your System > Administration menu, run the following command from a terminal and try again:

```
sudo apt-get install synaptic
```

---

### Post by madmondeoman on 2010-11-17
Hi
 
I ran sudo apt-get install synaptic and now when I go System > Administration menu it asks for a password, I enter it and it just says itswrong. Rebooted server and logged in ok but still says wrong password

---

### Post by madmondeoman on 2010-11-17
Sussed it ran a update script and rebooted and the synaptic package manage is now working brill!
 
Thanks for the help
 
Shaun

---

### Post by pawhtiobo on 2010-11-22
Hi all,

Yesterday i had the same problem, i solved it changing the user and root password, using this command:

**sudo passwd root**

(difine new passord and confirm it)

**sudo passwd user** (your user)


(difine new passord and confirm it)

see ya....

---

