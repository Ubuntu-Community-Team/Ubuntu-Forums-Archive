---
title: "please how i put password to open partattions and to network lan and &gt;&gt;"
date: 2008-11-27
forum: Security
---

### Post by mohammedabdoo on 2008-11-27
please iam anew and little english
i have the latest ubuntu and when i login   the windows contain text box was appears to enter the password and when i dont enter any thing  after 30 secound the systen opend  without password
i want to create password to all partations and password to open my computer from lan
and need to disable   all sharing on lan
please help me
thanks for all

---

### Post by cariboo on 2008-11-28
You must have enabled autologin during the nstallation. Any time the system ask for a password use the password you set up during the installation of Ubuntu.

---

### Post by mohammedabdoo on 2008-11-28
thanks 
yes i reinstall it and leave the option "log in automaticaly" and it work good
naw i need to disable file and filder sharing  because i member of windows lan groub and naw i can see the others computers on lan and its mean me computer  enabled file and folder sharing

how i stob the sharing
and how i hide my computer from lan 
like in windows i write in cmd "net config server /hidden :yes"
what the same in ubuntu 
please

---

### Post by cariboo on 2008-11-28
Before  answering any more questions, are you using Ubuntu against company policy? Because it looks like you are trying to hide your computer from the rest of the network.

Jim

---

### Post by mohammedabdoo on 2008-11-29
thanks for replay
first 
iam the administrator of this network and it asmaal lan 
this computer is my secounde  in this lan and i want to try the linux power on firewal than windows

can you help me

---

### Post by cariboo on 2008-11-30
The windows computers on the network can't see the linux computer, unless you have Samba installed. You will be able to see the windows cpmputers on the network. If you have samba installed, I would uninstall it, by using the following comand in a Applications-->Accessories-->Terminal:

```
sudo apt-get purge samba
```

or if you don't want to uninstall it, just stop the service. In the same terminal type:

```
sudo /etc/init.d/samba stop
```

Jim

---

