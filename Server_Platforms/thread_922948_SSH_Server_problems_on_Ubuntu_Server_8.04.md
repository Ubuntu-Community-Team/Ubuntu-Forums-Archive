---
title: "SSH Server problems on Ubuntu Server 8.04"
date: 2008-09-17
forum: Server Platforms
---

### Post by CapTlnsano on 2008-09-17
Just converted an old dell box to an Unbuntu Server box for its SSH capabilities - its running the latest (far as i know?) 2.6.24-19-server kernel. 

From a fresh install, with the core SSH files installed (when prompted what type of server on install I choose openSSH server...i cannot get past testing it locally by 'ssh localhost'. 

I get an error "ssh: connect to host localhost port 22: Connection refused"

So i'm thinking possible the service isnt even running; i attempt to restart the SSH daemon via: 'sudo /etc/init.d/ssh restart'

which only returns an error: 
sudo: /etc/init.d/ssh: command not found

I cannot remote into the box via the other unbuntu workstation i have either, even though i have verified network connectivity. 


Would someone kindly let me know what ridiculously simple piece im missing here (it always is when i become frustrated enough to post :))

Thanks

---

### Post by mrsteveman1 on 2008-09-17
try doing sudo apt-get install ssh

---

### Post by cariboo on 2008-09-17
First make sure ssh is running:

```
ps aux | grep ssh
```

If it isn't try:

```
sudo /usr/sbin/sshd
```

If that doesn't work, make sure you have openssh-server install and not just the client.

Jim

---

### Post by RealPSL on 2008-09-17
Do you have the openssh-server package installed? ```
dpkg --list openssh-server
```

That is the package that has the /etc/init.d/ssh file and the other files to run the server. If you do not have it you can install it with ```
sudo apt-get install openssh-server
```

If that does not work we will have to dig deeper.

---

### Post by CapTlnsano on 2008-09-18
Cariboo:

Never used the grep command before so i'm not sure what im seeing/supposed to be seeing, either way the output on that is: 

austin  4217 0.0 0.0 3004 752 tty1   R+ 07:08  0:00 grep ssh


The output for sudo /usr/sbin/sshd is
sudo: /usr/sbin/sshd: command not found

---

### Post by CapTlnsano on 2008-09-18
> **RealPSL said:**
> Do you have the openssh-server package installed? ```
dpkg --list openssh-server
```

That is the package that has the /etc/init.d/ssh file and the other files to run the server. If you do not have it you can install it with ```
sudo apt-get install openssh-server
```

If that does not work we will have to dig deeper.

I've thought of checking to see if this package is installed and i might add this is also a big quirky:

When I use dpkg --list openssh-server, i get: 

Desired=Unknown/Install/Remove/Purge/Hold
|Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad
||/Name         Version      Description
+++-============-===========-======================

un openssh=server <none>      (no description available)






Sorry for the manual transfer of code, but if im reading that right its basically saying the package isnt installed/installed correctly? 

Thanks in advance for the help.

---

### Post by kamaji792 on 2008-09-18
> **CapTlnsano said:**
> Cariboo:

Never used the grep command before so i'm not sure what im seeing/supposed to be seeing, either way the output on that is: 

austin  4217 0.0 0.0 3004 752 tty1   R+ 07:08  0:00 grep ssh


The output for sudo /usr/sbin/sshd is
sudo: /usr/sbin/sshd: command not found

**ps** list the running processes.

**grep** is a command that can be used to filter the output of other commands, as it is in this case.

So you will only see output lines from **ps** that have **ssh** in them.

What the output is telling you is the **grep** command is being run (looking for 'ssh') :)

My output for the command was:
```

 ps aux | grep ssh
root      4355  0.0  0.1   5312  1020 ?        Ss   08:59   0:00 /usr/sbin/sshd
root      5163  0.0  0.7  11352  3716 ?        Ss   11:18   0:00 sshd: sys-admin [priv]
1000      5165  0.0  0.3  11508  1996 ?        S    11:18   0:00 sshd: sys-admin@pts/0
1000      5449  0.0  0.1   3004   756 pts/0    R+   12:36   0:00 grep ssh

```

From what I have seen on this thread it looks like you don't have OpenSSH installed or the installation went wrong.

So I guess your are in
```
sudo apt-get install openssh-server
```
All the best.

---

