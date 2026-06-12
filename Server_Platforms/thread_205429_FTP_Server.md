---
title: "FTP Server"
date: 2006-06-28
forum: Server Platforms
---

### Post by Ryan H on 2006-06-28
I have LAMP set up and working correctly, now all I have left is to install FTP and SSH on it, then my web server will be complete! Muhahahaha-*cough*. I want to have atleast two users, with each one pointing two a different directory. For example user `ryan` will be able to use /home/ryan/www/; whereas user `betta` will be able to browse /home/betta/www/. I also don't completely know about SSH. I know it is more secure than FTP because it encrypts the information on whim then decrypts it on the other side, but I'm guessing because of this it is slower, but by home much?

-Ryan H

---

### Post by hagen00 on 2006-06-28
[QUOTE=Ryan H]I also don't completely know about SSH. I know it is more secure than FTP because it encrypts the information on whim then decrypts it on the other side, but I'm guessing because of this it is slower, but by home much?

-Ryan H[/QUOTE]

SSH and FTP are used for two different things. SSH is a replacement for Telnet (SSH is encrypted) and basically gives you a command line interface from a remote computer. So anything you can do on the commandline, you can do from SSH from a remote computer. FTP is to transfer files from a computer to your server (not encrypted though - SFTP is based on SSH and is).

So what do you want to do. Access your computer remotely and execute commands (SSH) or transfer files to your computer (FTP)?

---

### Post by Ryan H on 2006-06-28
Thanks for clearing that up. I'd like to do both but FTP is more important, so let's start with that. How would I get that up and running?

-Ryan

---

### Post by harisund on 2006-06-28
A couple of things to point out : 

Clarification: SSH can be used to file transfer. I mean, once you have a SSH server running, file transfer too is possible. Just that the mentality is to use FTP for web access. If you want more help regarding this, I can let you know.  The simple way to get everything to work is execute "sudo apt-get install openssh-server" which will setup a SSH server that people can use to login, execute commands and transfer files (using scp.. but I can explain that later if required). sftp and scp can be used to file transfer. more information on that later if you want .. 

Next, the simplest way to get what you want is to enable a module called userdir in apache. Execute "sudo a2enmod userdir" and then on, each user has to create a directory named "public_html" and put his webpages there, which can then be accessed using [http://domain-name/~username](http://domain-name/~username)

Example: let's say your machine is example.org and there are users alice and bob. they both have a folder named "public_html" on their machines. 

Alice's webpage: [http://example.org/~alice](http://example.org/~alice)
Bob's webpage: [http://example.org/~bob](http://example.org/~bob)

You can pretty much do away with FTP server, but if you want it desperately, that's a different issue.

---

### Post by Ryan H on 2006-06-28
I'll install them in a little while, right now I'm running Synaptic Package Manager, so I can't install anything else while it's running. I'd really like to use FTP, it's faster than HTTP, atleast in a browser, and it's more flexable for my needs.

-Ryan

Edit: Now I've installed the SSH server, how do I set it up? And what is the Linux program used to connect to it? I used to use PuTTy in Windows.

---

### Post by harisund on 2006-06-28
The software I use for installing a FTP server is proftpd. Of course there are tons of FTP servers, and I am pretty sure someone is going to come along and say 'proftpd sucks - use this instead' and give their own personal choice. 

Just use Synaptic to install "proftpd" ... you can always purge yourself of it if you think it is indeed horrible.

and >  A powerful replacement for wu-ftpd, this File Transfer Protocol
 daemon supports hidden directories, virtual hosts, and per-directory
 ".ftpaccess" files.  It uses a single main configuration file, with a
 syntax similar to Apache.

 Because of the advanced design, anonymous-FTP directories can have
 an arbitrary internal structure (bin, lib, etc, and special files are
 not needed).  Advanced features like multiple password files and
 upload/download ratios are also supported.

 This package contains only the basic functionality of proftpd and PAM
 authentication.  If you need SQL, use proftpd-mysql or proftpd-pgsql
 and if you need LDAP, use proftpd-ldap.

 More information can be found at [http://www.proftpd.org/](http://www.proftpd.org/).


This is taken from the package description of proftpd. 

it's configuration file is at /etc/proftpd.conf in case you want to have a look. 

and finally, why do you have Synaptic (GUI) running if you intend to have a server? not a big problem actually, but if you are running a serious server it wouldn't be very good to be running GUI.. but then again, it's your own choice, as is everything in the open source world :D

---

### Post by Ryan H on 2006-06-28
I'm not actualy running a server. I develope localy before putting things on my actual server, I'm actualy on Ubuntu Desktop. This is what I have in my proftpd.conf:
> 
<Anonymous /home/ryan/www/>
 User            ryan
 Group            nogroup
 UserAlias          anonymous ftp
 DirFakeUser on ftp
 DirFakeGroup on ftp
 RequireValidShell      off
 MaxClients         10
 DisplayLogin        welcome.msg
 DisplayFirstChdir      .message
 <Directory *>
  <Limit WRITE>
   DenyAll
  </Limit>
 </Directory>
</Anonymous>


I want to connect to the ftp through my IP address, but my FTP client can't connect to my IP? And how do I set up a password for my user?

-Ryan

---

### Post by harisund on 2006-06-28
Actually I didn't even edit that part which you have shown here. 

first make sure your FTP address is running and correctly configured using "ftp localhost" it should ask you for user name and password and after enetering it see if everything works the way you want it. 

Next, ensure your ISP doesn't block port 21, the FTP port.

---

### Post by Ryan H on 2006-06-28
I've used FTP before for to connect to actualy FTP servers, so I don't see how it could be blocked. And I made sure my router is configured to allow it. And I don't want to connect to my localhost, I want to connect remotely to this computers IP with FTP.

-Ryan

---

### Post by Ryan H on 2006-06-28
I've used FTP before for to connect to actualy FTP servers, so I don't see how it could be blocked. And I made sure my router is configured to allow it. And I don't want to connect to my localhost, I want to connect remotely to this computers IP with FTP.

-Ryan

---

### Post by harisund on 2006-06-28
Hmm... no.... the fact that you could connect to other FTP servers doesn't imply you can connect to your own. ISPs don't block outgoing FTP connections, only incoming ones likely. 

If you have a router, remember not to use passive FTP and only active FTP.

Yes, I mentioned localhost only so to test that FTP is working on the machine. Once we know it is for sure, we can head over to checking it from other machines.

---

### Post by Ryan H on 2006-06-28
I don't see why they would block it, is there a way to test? Also ftp.localhost doesn't connect.

-Ryan H

---

### Post by harisund on 2006-06-28
Ah! if ftp localhost doesn't work you have got yourself a problem. check with ```
sudo netstat -plant | grep LISTEN
``` if indeed your ftp port 21 is open. can you check that?

---

### Post by Ryan H on 2006-07-02
```

tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     4856/mysqld
tcp        0      0 127.0.0.1:35186         0.0.0.0:*               LISTEN     4581/hpiod
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     4633/cupsd
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN     5005/master
tcp        0      0 127.0.0.1:50751         0.0.0.0:*               LISTEN     4585/python
tcp6       0      0 :::80                   :::*                    LISTEN     5237/apache2
tcp6       0      0 :::22                   :::*                    LISTEN     5039/sshd

```

That's what it says.

-Ryan H

---

### Post by harisund on 2006-07-03
See, port 21 is not open. In fact, your FTP server is not running at all. Can you tell me how you installed your FTP server and what FTP server you installed?

---

### Post by faultyCPU on 2006-07-03
may be your local firewall blocking it ? just a guess 
use 
iptables -L

---

