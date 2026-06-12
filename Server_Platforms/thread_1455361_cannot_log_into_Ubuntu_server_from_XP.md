---
title: "cannot log into Ubuntu server from XP"
date: 2010-04-15
forum: Server Platforms
---

### Post by mobiblu on 2010-04-15
First off, I am still new to Ubuntu and have no experience with server. 

-My Objective was to create a simple NAS using Ubuntu to share files between pc at home( 1 Macbook, and a few XP laptop).

Being the noob as I am, I found and follow this great guide that basically hand walk me through all the setup. [Link to Guide]("http://forums.ebuyer.com/showthread.php?t=31797")
After following through the guide installing 8.04 LTS, I went to my XP machine. Start>Run. Type in \\Core. I see the home directory but when I try to log into my account. It won't validate my account. Can you tell me what I'm missing or if guide i'm following is missing some step.

---

### Post by buntunoob on 2010-04-15
the first post after that had your fix
Sudo Smbpasswd –a username

---

### Post by mobiblu on 2010-04-15
I actually went through that process as well. I created 2 user accounts in Samba. I try to log into both account but couldn't.

---

### Post by speed32219 on 2010-04-15
Well, I would first download putty for your xp PC's it is an excellent program (Of course you need openssh-server and openssh-client installed on your server, sudo apt-get install openssh-server openssh-client).  Also, you should be able to go to windows explorer, right click on network and then explore.  L@@k to see if the server name is on your network.  If it is then you should be able to click on it and it will ask you for your user name and password. OTher stuff to try.

1. Check your /etc/hosts file
 
something like this:
```
127.0.0.1       localhost
127.0.1.1       server01 # Your server name from output of sudo /bin/hostname

[B]# The following lines would have your IP address and net
# bios names of your exiting PC's.[/B]
 192.168.1.119 pc-1
 192.168.1.111 pc_2
 192.168.1.115 pc-3
 192.168.1.118 pc-4
 192.168.1.101 XP_1
 192.168.1.110 XP_2
 gateway 192.168.1.254

```

2. check your /etc/resolv.conf file for proper config.
something like this:
domain gateway.2wire.net #(Could be domain launchmodem.com)
search gateway.2wire.net #(Could be search launchmodem.com)
nameserver 192.168.1.254 # Your nameserver or Gateway ip address

3. check your smb.conf file.
You can use one like this to just work the bugs out. just rename your /etc/samba/smb.conf to /etc/samba/smb.conf.BAK. (Use sudo mv and then sudo nano /etc/samba/smb.conf to create the test one and past the contents below, but make the changes I highlighted)

```
[global]
workgroup = **WORKGROUP** #Yours
netbios name = **your server name, like server01 from above**
#security = user
hosts allow = 192.168.0. 192.168.2. 127
#passdb backend = tdbsam
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
#============================ Share Definitions ==============================
[main]
comment = Movies, Videos, Documents, Desktop,  etc . . .
path = /home/**Your Userid**/
writable = yes
[Sys]
path = /

```

 I think that should get you moving in the right direction.

---

### Post by SRST Technologies on 2010-04-18
> **mobiblu said:**
> I actually went through that process as well. I created 2 user accounts in Samba. I try to log into both account but couldn't.

Since you didn't mention anything about two accounts on your samba server in the previous posts, I think it might be pointed out that any user you try to add to samba must also exist in the real world of the rest of the operating system, too.  Trying to add john to a server that does not have a john username is not going to work.

As for speed's suggestion, I he already has samba installed and configured, you know.  The first post said that.

---

