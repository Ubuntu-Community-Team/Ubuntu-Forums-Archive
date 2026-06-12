---
title: "SFTPD server help? Please!"
date: 2010-10-26
forum: Server Platforms
---

### Post by JD32 on 2010-10-26
I've been trying to set up a FTP server for some quite some time and i keep running into problems. I'm trying to set it up via gadmin- proftpd but even with that i cant get it to run. Can anyone point me towards a good how-to or just help me out? I'm kinda new to Linux and this is my first go at servers so i really have no clue here. Any help would be greatly appreciated!

---

### Post by MechaMechanism on 2010-10-26
Useful guides.  See which one you like best.

[http://ubuntuforums.org/showthread.php?t=79588&highlight=ftp](http://ubuntuforums.org/showthread.php?t=79588&highlight=ftp)
[http://ubuntuforums.org/showthread.php?t=518293&highlight=ftp](http://ubuntuforums.org/showthread.php?t=518293&highlight=ftp)

---

### Post by schmutztaucher on 2010-10-26
Also...

[https://help.ubuntu.com/8.04/serverguide/C/ftp-server.html](https://help.ubuntu.com/8.04/serverguide/C/ftp-server.html)

---

### Post by JD32 on 2010-10-26
When i try to configure the file i cant open it, i get this 

```
jd@FILE-SERVER:~$ sudo cp /etc/vsftpd.conf
cp: missing destination file operand after `/etc/vsftpd.conf'
Try `cp --help' for more information.
jd@FILE-SERVER:~$ 

```

:confused:

---

### Post by schmutztaucher on 2010-10-26
Try

sudo vim /etc/vsftpd.conf

---

### Post by JD32 on 2010-10-26
same

```
jd@FILE-SERVER:~$ sudo vim /etc/vsftpd.conf
sudo: vim: command not found
jd@FILE-SERVER:~$ 
```

---

### Post by schmutztaucher on 2010-10-26
This will open vsftp.conf in a text editor called nano

```

sudo nano /etc/vsftpd.conf

```

If you do not know how to use nano..

[https://help.ubuntu.com/community/Nano](https://help.ubuntu.com/community/Nano)

---

### Post by JD32 on 2010-10-26
This is gonna be a dumb question but then how do i edit it?

```
# Example config file /etc/vsftpd.conf
#
# The default compiled in settings are fairly paranoid. This sample file
# loosens things up a bit, to make the ftp daemon more usable.
# Please see vsftpd.conf.5 for all compiled in defaults.
#
# READ THIS: This example file is NOT an exhaustive list of vsftpd options.
# Please read the vsftpd.conf.5 manual page to get a full idea of vsftpd's
# capabilities.
#
#
# Run standalone?  vsftpd can run either from an inetd or as a standalone
# daemon started from an initscript.
listen=YES
#
# Run standalone with IPv6?
# Like the listen parameter, except vsftpd will listen on an IPv6 socket
# instead of an IPv4 one. This parameter and the listen parameter are mutually
# exclusive.
                               [ Read 144 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell
```

---

### Post by JD32 on 2010-10-26
Nevermind I think i got it :P

---

### Post by JD32 on 2010-10-26
When i try and restart to apply changes i get this :-k

```
jd@FILE-SERVER:~$ sudo /etc/init.d/vsftpd restart
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service vsftpd restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the restart(8) utility, e.g. restart vsftpd
vsftpd start/running, process 1835
jd@FILE-SERVER:~$ 
```

---

### Post by hawk2010 on 2010-10-27
hi,

This is normal. Ubuntu new version's have the new controller called upstart. Like in Redhat flavors where  you can control a daemon usiing the service command. U can do the same with the latest ubuntu. for example service vsftpd reload will reload the vsftpd.conf Just a short cut to /etc/init.d/vsftpd reload.

---

### Post by JD32 on 2010-10-27
So did it still restart and apply changes or must i do the new "upstart" thing, i didnt really follow what it was saying... Sorry i'm new to Linux in general.

---

### Post by MechaMechanism on 2010-10-27
To stop a service, also known as a daemon.

sudo service sftpd stop



To start a service.

sudo service sftpd start



To restart a service

sudo service sftpd restart



Upon using these commands, there should be 2 types of output, OK and FAIL.  Ok means everything went fine.  Fail means there was a problem.  However there are services that do not use the ok, fail output, such as ssh.

---

### Post by JD32 on 2010-10-27
can anyone help me with connecting to my sever then with filezilla? do i have to have a domain name or can i use an IP?

---

### Post by hawk2010 on 2010-10-28
Hi, is your server using a public IP ? if so you can connect from the public IP. Say for example u are using a broadband connection. Then you need to use the public IP of the router and do port forwarding to your server. For example. If your FTP server is on a private IP 192.168.2.5 on port 21. Then u have to set router's portforwarding rules to have it's external port 21 and internal port 21 forwarded to that 192.168.2.5, When you log in using filezilla u give the public IP of the router and port 21. Router wil do the forwarding

---

