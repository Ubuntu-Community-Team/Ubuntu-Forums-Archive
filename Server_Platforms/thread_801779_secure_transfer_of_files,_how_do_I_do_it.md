---
title: "secure transfer of files, how do I do it?"
date: 2008-05-20
forum: Server Platforms
---

### Post by Superdude_123 on 2008-05-20
Ok, so here's my question and problem:

I'm a noob at Linux, and most of my experience is based on using X server in gusty. I would like to make a server, for the simple purpose of transferring files securely trough the Internet from point A to B. I've been doing allot of research on whether I should use SFTP, FTPS, or simply SSH. The idea is to transfer the files (less then 700 mb) from a windows xp system to my Linux server in an encrypted method, witch I hope can be automated on the windows system. So my questions are:

1) What encryption would be best for this task?
2) Can you point me to either a software package that I can install and configure with X server or a guide that walks me trough it step by step?

---

### Post by eniacpx on 2008-05-20
In my opinion, SFTP via the OpenSSH package cannot be beat. You just install your ssh server, configure it to your liking and SFTP just works. There are no extra ports to open and really no extra config besides your typical sshd configuration.

For your WinXP box I highly recommend you download "WinSCP" as your client software, it is quick and simple and offers a few bells and whistles for free.

---

### Post by Superdude_123 on 2008-05-20
Ok, I'm still stuck

I installed Openssh server (from [https://help.ubuntu.com/7.10/server/C/openssh-server.html)on](https://help.ubuntu.com/7.10/server/C/openssh-server.html)on) my laptop (just to get a feel for what I'm doing, its using gusty) but how do I make the keys, and configure the sftp?

---

### Post by eniacpx on 2008-05-20
Start Here:
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

After installing the OpenSSH-server package are you able to ssh into your box? If so, SFTP should already work. As long as SSH works SFTP should as well.

Unless I am mistaken, the keys you require are generated during install.

Here is my "/etc/ssh/sshd_config" I use two ports, one for external connections into my box (22000) and one for internal (though they both work when internal), I have bolded a line below, it is important (in my opinion) to add this to yours as well, you don't to open yourself up to external root access if you can help it:
```

# What ports, IPs and protocols we listen for
Port 22
Port 22000
Protocol 2

# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key

#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
**PermitRootLogin no**
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication no

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes

# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no

# similar for protocol version 2
HostbasedAuthentication no

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
PasswordAuthentication yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
KeepAlive yes

#MaxStartups 10:30:60
Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes

```

---

### Post by Wim Sturkenboom on 2008-05-21
There is one thing that I don't like about sftp and that is that it's a mission (my opinion) to jail a user to his home directory.
Therefor I (still) use vsftpd with TLS/SSL (see [http://www.brennan.id.au/14-FTP_Server.html#secure](http://www.brennan.id.au/14-FTP_Server.html#secure) for a setup)

---

### Post by hyper_ch on 2008-05-21
This is very simple:

(a) On the server

(1) install openssh-server
```

sudo apt-get install openssh-server

```

(2) install denyhosts (recommended)
```

sudo apt-get install denyhosts

```
For more infos, have a read here:  [http://www.howtoforge.com/preventing_ssh_dictionary_attacks_with_denyhosts](http://www.howtoforge.com/preventing_ssh_dictionary_attacks_with_denyhosts)

(3) give your server a static IP in your lan


On the router

(1) Forward port 22 to your server (it should have a static IP now) --> this is needed if you want to load stuff onto your server from outside your lan

(2) If possible, setup a dyndns on your router - some alternate firmware like dd-wrt/tomato-wrt allow that... if that's not possible, you can setup some dyndns on the server  --> this is needed if you have not a static IP in your internet account


On windows

(1) Get WinSCP
[http://www.winscp.com](http://www.winscp.com) --> Free and Open Source

(2) Enter your server's IP and your username/password and access it


On Linux

Get a program that allows SCP/SFTP (I know Konqueror does [use fish://user@server in Konqueror address bar]

That's it...

---

### Post by windependence on 2008-05-21
I agree with hyper_ch. scp and winscp work great. You can use pscp to script on the Windows side and fully automate your process.

BTW guys, it is usually not necessary to install ssh on your box unless you specifially told it not to install with the OS.

-Tim

---

### Post by hyper_ch on 2008-05-21
ssh-server does not get installed by default :) so that needs to be installed.

---

