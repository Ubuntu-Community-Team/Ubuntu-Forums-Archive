---
title: "Unable to connect to internet using bridge network in virtualbox"
date: 2016-09-19
forum: Virtualisation
---

### Post by ebuono on 2016-09-19
Hello to everyone,
 Im new to ubuntu server, so if this question has been made before i wasn't able to find it, and if the question is dumb i hope you have some patience..
So, the thing is that I  managed to install ubuntu server in a virtual machine with virtualbox  and using bridge network mode to grab the host machine ip, i was able to  configure LAMP succesfully, the problem appears when i export this  virtual machine to another host, when i boot, a message is displayed  saying:

 "a start job is running for raise network interfaces"

 it keeps  displaying that message for about 5 minutes and then it boots, but  network is not working and no eth0 configuration appears in **/etc/network/interfaces.d**,  i've read in this forum that when i change the host the mac adress is  not recognized since is different of course, so i tried with something  that someone post here:

  [https://ubuntuforums.org/showthread.php?t=1945029](https://ubuntuforums.org/showthread.php?t=1945029)
 
that it would restart  the mac adress by removing this file  "**/etc/udev/rules.d/70-persistent-net.rules**" and forcing the os to create  it again but it didn't work. So I would like to know what should I do or  where should I go to fix this. Any kind of help will be greatly  appreciated.

 Thanks in advance.

---

### Post by &amp;KyT$0P# on 2016-09-19
Have you checked the VM's hardware network settings on the new host?

---

### Post by MAFoElffen on 2016-09-20
Trying to not take anything for granted, so:

1. What is the host operating system that you have virtualbox installed on?

2. What version of Ubuntu server do you have installed as a guest?

3. 
- a. If your Host OS is Linux Ubuntu Linux system, then what is the result of 
```

[code]ifconfig -a
sudo lshw -n -c network
```
- b. If your host system is a Windows OS, then what is the result of 
```
ifconfig /all
netsh interface show interface
```

4. On the Ubuntu Server VM Guest, show the results of the commands in 3.a.

5. On the host, show the results of 
```

VBoxManage showvminfo "Name_Of_VM_Guest"

```

---

### Post by ebuono on 2016-09-20
> **halogen2 said:**
> Have you checked the VM's hardware network settings on the new host?

Yes I did. I configured it in the exact same way.

---

### Post by ebuono on 2016-09-20
> **MAFoElffen said:**
> Trying to not take anything for granted, so:

1. What is the host operating system that you have virtualbox installed on?

2. What version of Ubuntu server do you have installed as a guest?

3. 
- a. If your Host OS is Linux Ubuntu Linux system, then what is the result of 
```

[code]ifconfig -a
sudo lshw -n -c network
```
- b. If your host system is a Windows OS, then what is the result of 
```
ifconfig /all
netsh interface show interface
```

4. On the Ubuntu Server VM Guest, show the results of the commands in 3.a.

5. On the host, show the results of 
```

VBoxManage showvminfo "Name_Of_VM_Guest"

```

My host is windows, the thing is that i'm doing this from inside my work network, I don't know if that could be a problem.

---

