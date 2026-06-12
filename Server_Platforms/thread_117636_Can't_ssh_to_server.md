---
title: "Can't ssh to server"
date: 2006-01-15
forum: Server Platforms
---

### Post by irv on 2006-01-15
I can use ssh to get to any of my workstation on my network, but I can't ssh to my server. When I try I get [Couldn't display "sftp://192.168.0.105"] which is my server's ip address. I tried turning off my firewall, but get the same message.
Anyone get any ideas what to try?
Thanks

By the way, I have my server setup as a Web, FTP, Samba, SQL, Mail server.

---

### Post by papayiya on 2006-01-15
I imagine you have your computers connected to a router.  You have to forward port 22 to the computer which will handle ssh requests.  Look at your router setup.

Good luck,
George

---

### Post by bluefrog on 2006-01-16
I assume your commande line is as follows:

sftp 192.168....

james

---

### Post by irv on 2006-01-18
[QUOTE=bluefrog]I assume your commande line is as follows:

sftp 192.168....

james[/QUOTE]
From the command line:

irv@ubuntu:~$ sudo sftp 192.168.0.105
Password:
Connecting to 192.168.0.105...
The authenticity of host '192.168.0.105 (192.168.0.105)' can't be established.
RSA key fingerprint is 92:d8:a2:84:b4:8b:be:eb:38:30:8f:44:5d:90:7b:47.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '192.168.0.105' (RSA) to the list of known hosts.
root@192.168.0.105's password:
Request for subsystem 'sftp' failed on channel 0
Couldn't read packet: Connection reset by peer
irv@ubuntu:~$

---

### Post by irv on 2006-01-18
[QUOTE=papayiya]I imagine you have your computers connected to a router.  You have to forward port 22 to the computer which will handle ssh requests.  Look at your router setup.

Good luck,
George[/QUOTE]
Yes I do have port 22 set to handle ssh, but all I want is to do a ssh on my LAN not my WAN. If I try to do a ssh as a a user who is setup on the server and the workstation, and doing it from the workstation to the server this is what I get:

irv@ubuntu:~$ sftp 192.168.0.105
Connecting to 192.168.0.105...
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
92:d8:a2:84:b4:8b:be:eb:38:30:8f:44:5d:90:7b:47.
Please contact your system administrator.
Add correct host key in /home/irv/.ssh/known_hosts to get rid of this message.
Offending key in /home/irv/.ssh/known_hosts:4
RSA host key for 192.168.0.105 has changed and you have requested strict checking.
Host key verification failed.
Couldn't read packet: Connection reset by peer
irv@ubuntu:~$

---

### Post by wrtrdood on 2006-01-18
*Add correct host key in /home/irv/.ssh/known_hosts to get rid of this message.*

This is the clue...

Look for the line in your .ssh/known_hosts file that contains the IP address shown.  Remove that line then save the file and ssh will prompt you as in the previous post.  Not a perfect solution (RSA pairs should be set up properly) but it will at least it will let you connect.

It's complaining because you changed something somewhere and the client still thinks it's all the same.  I usually just delete the known_hosts files and start over.

---

### Post by MJN on 2006-01-18
Are you sure about that? It looks to me that the client is simply highlighting the mismatch of keys/hosts, yet carrying on regardless (given the user go-ahead) and that it is the *server* that's closing the connection... ???

---

### Post by Glut on 2006-01-18
[QUOTE=MJN]Are you sure about that? It looks to me that the client is simply highlighting the mismatch of keys/hosts, yet carrying on regardless (given the user go-ahead) and that it is the *server* that's closing the connection... ???[/QUOTE]
This is a fatal error for ssh, despite the slightly misleading 'connection reset by peer', it is the client that refuses to continue the connection.

---

### Post by bluefrog on 2006-01-19
don't use root (sudo) for sftp. root logging with ssh won't be possible by default on ubuntu as root account has no password.

if you have problems with ssh keys, remove /home/your-user/.ssh/known_hosts.


so in the end you should do
 sftp your-IP
your-user password:

you're in

james

---

### Post by MJN on 2006-01-19
Thanks for clarifying the error issue Glut. I should know better than to take all error messages at face value! ;) 

Mathew

---

### Post by majikstreet on 2006-01-19
[QUOTE=bluefrog]don't use root (sudo) for sftp. root logging with ssh won't be possible by default on ubuntu as root account has no password.

if you have problems with ssh keys, remove /home/your-user/.ssh/known_hosts.


so in the end you should do
 sftp your-IP
your-user password:

you're in

james[/QUOTE]
yeah...

---

