---
title: "FTP Server problems: Connection Refused"
date: 2008-08-24
forum: Server Platforms
---

### Post by Marzhall on 2008-08-24
Hey guys,
 I'm trying to set up an ftp server using proftpd on a low-memory machine, meant to be used solely by myself. I used the "advanced" setting from [http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588), because I'm using ssh to control the machine; I have no physical access to it, and it's not powerful enough to handle an x-session. However, having attempted to use both proftpd and vsftpd, I have not been able to connect using either a terminal ftp command or fireftp, nor have I even been able to connect to localhost from the server itself. I'm assuming the problem is with port 21, but I don't know what to do. Thanks in advance, guys.
Edit: Also, pinging the server returns packets, so it's up. Thanks.


output of netstat:
wolf@random-server:~$ netstat -a | grep ftp
unix  2      [ ACC ]     STREAM     LISTENING     16134    /var/run/proftpd/proftpd.sock
unix  2      [ ACC ]     STREAM     LISTENING     16143    /var/run/proftpd/proftpd.sock

output of ftp:
wolf@random-server:~$ ftp localhost
ftp: connect: Connection refused

output of  netstat -an | grep "LISTEN ":
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:3128            0.0.0.0:*               LISTEN     
tcp6       0      0 :::80                   :::*                    LISTEN     
tcp6       0      0 :::22                   :::*                    LISTEN     
tcp6       0      0 :::1980                 :::*                    LISTEN

---

### Post by Krupski on 2008-08-24
> **Marzhall said:**
> Hey guys,
 I'm trying to set up an ftp server using proftpd on a low-memory machine, meant to be used solely by myself. I used the "advanced" setting from [http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588), because I'm using ssh to control the machine; I have no physical access to it, and it's not powerful enough to handle an x-session. However, having attempted to use both proftpd and vsftpd, I have not been able to connect using either a terminal ftp command or fireftp, nor have I even been able to connect to localhost from the server itself. I'm assuming the problem is with port 21, but I don't know what to do. Thanks in advance, guys.
Edit: Also, pinging the server returns packets, so it's up. Thanks.
output of netstat:
wolf@random-server:~$ netstat -a | grep ftp
unix  2      [ ACC ]     STREAM     LISTENING     16134    /var/run/proftpd/proftpd.sock
unix  2      [ ACC ]     STREAM     LISTENING     16143    /var/run/proftpd/proftpd.sock

output of ftp:
wolf@random-server:~$ ftp localhost
ftp: connect: Connection refused

Do you have a user account named "ftp"?

If you like, give this a try. If you already have a user called "ftp", you will just get an error message: "useradd: user ftp exists".

Try this:

```

sudo useradd -d /home/users/ftp -s /bin/false -r ftp

```

The '-d' means "this is the new user's directory" (substitute the path YOUR ftp users are meant to access).

The '-s' means "this is the new user's shell" (which is set to nothing usable).

The '-r' means "create a system account" (called 'ftp').

Now, vsftpd requires that the root of the ftp user's directory NOT be writable, so next type this:

```

sudo chmod 0555 /home/users/ftp

```

"0555" makes the directory read and execute, but not write.

Of course, substitute YOUR path for my example '/home/users/ftp'.

If you use vsftpd, the config file it generates upon install (/etc/vsftpd.conf) should work "out of the box"... you don't need to edit it.

You should be able to do anonymous logins if all works properly.

Good luck!

-- Roger

(edit to add): If you need remote control of your server for both a terminal as well as secure FTP uploads and downloads (all through SSH port 22), try using the awesome free program "Bitvise Tunnelier" (download it from [**[color=blue]HERE[/color]**]("http://www.bitvise.com/tunnelier.html")). It's a Windows program, and it gives you both a terminal and a two window SFTP client (one side Windows, other side Linux) and you can just drag-n-drop files to and from either machine as easy as can be.

-- Roger

---

### Post by Marzhall on 2008-08-24
> **Krupski said:**
> Do you have a user account named "ftp"?

If you like, give this a try. If you already have a user called "ftp", you will just get an error message: "useradd: user ftp exists".

Try this:

```

sudo useradd -d /home/users/ftp -s /bin/false -r ftp

```

The '-d' means "this is the new user's directory" (substitute the path YOUR ftp users are meant to access).

The '-s' means "this is the new user's shell" (which is set to nothing usable).

No, still no go. I did not know about that, however- thank you, as that would have been a problem later. 

The '-r' means "create a system account" (called 'ftp').

Now, vsftpd requires that the root of the ftp user's directory NOT be writable, so next type this:

```

sudo chmod 0555 /home/users/ftp

```

"0555" makes the directory read and execute, but not write.

Of course, substitute YOUR path for my example '/home/users/ftp'.

If you use vsftpd, the config file it generates upon install (/etc/vsftpd.conf) should work "out of the box"... you don't need to edit it.

You should be able to do anonymous logins if all works properly.

Good luck!

-- Roger

(edit to add): If you need remote control of your server for both a terminal as well as secure FTP uploads and downloads (all through SSH port 22), try using the awesome free program "Bitvise Tunnelier" (download it from [**[color=blue]HERE[/color]**]("http://www.bitvise.com/tunnelier.html")). It's a Windows program, and it gives you both a terminal and a two window SFTP client (one side Windows, other side Linux) and you can just drag-n-drop files to and from either machine as easy as can be.

-- Roger



Thanks for the input- it didn't fix the problem, but that would have been a problem later on. I was using proftp at that moment, but I reinstalled vsftpd (uninstalling proftpd to avoid problems), just to give it a try. Thanks for the advice about the windows program, it sounds neat. 

So, any other ideas? I'm pretty sure it's not program-related, as it happens with both programs, and I can't be that inept at following simple instructions... Hopefully... :P. Don't be afraid to hit me with terminal heavy stuff, or anything confusing; I'm not a developer, but it's been a few years since I installed my first distro. Thanks for your help.

---

### Post by Reid_PMP on 2008-08-26
Hi Marzhall,

I'm having a similar problem. I had vsftp working on my original install of ubuntu 7.10, but after trying to get a network printer service working (and not being successful) I reinstalled the server with a clean start.

Now I'm not able to get vsftp working. I have found several posts about the problems that I'm having but no clear solutions. My problems are;

[LIST]
[*]when trying to restart vsftpd the message returns that the service wasn't running
[*]vsftp is not listening to port 21
[/LIST]

Here is the outputs that you noted above;

output for netstat ftp;
reid@zebra:~$ netstat -a | grep ftp
-- blank, nada, nuttin there --

output for ftp:
reid@zebra:~$ ftp localhost
ftp: connect: Connection refused

output for netstat Listen:
reid@zebra:~$ netstat -an | grep "LISTEN"
tcp     0    0  127.0.0.1:3306   0.0.0.0:*    LISTEN
tcp6    0    0   :::80           :::*         LISTEN
tcp6    0    0   :::22           :::*         LISTEN
unix 2   [ACC]   STREAM   LISTENING  8664 /var/run/mysqld/mysqld.sock

The only services that I set up so far is openssh (it works) and vsftpd (it doesn't work.)

Thanks in advance for any help,

Reid

---

### Post by Marzhall on 2008-08-27
> **Reid_PMP said:**
> Hi Marzhall,

I'm having a similar problem. I had vsftp working on my original install of ubuntu 7.10, but after trying to get a network printer service working (and not being successful) I reinstalled the server with a clean start.

Now I'm not able to get vsftp working. I have found several posts about the problems that I'm having but no clear solutions. My problems are;

[LIST]
[*]when trying to restart vsftpd the message returns that the service wasn't running
[*]vsftp is not listening to port 21
[/LIST]

Here is the outputs that you noted above;

output for netstat ftp;
reid@zebra:~$ netstat -a | grep ftp
-- blank, nada, nuttin there --

output for ftp:
reid@zebra:~$ ftp localhost
ftp: connect: Connection refused

output for netstat Listen:
reid@zebra:~$ netstat -an | grep "LISTEN"
tcp     0    0  127.0.0.1:3306   0.0.0.0:*    LISTEN
tcp6    0    0   :::80           :::*         LISTEN
tcp6    0    0   :::22           :::*         LISTEN
unix 2   [ACC]   STREAM   LISTENING  8664 /var/run/mysqld/mysqld.sock

The only services that I set up so far is openssh (it works) and vsftpd (it doesn't work.)

Thanks in advance for any help,

Reid
I still have yet to get it working, but in the meantime, you can use the scp command to grab and put files on the computer.
To use it to put files on the server,
```
scp /home/username/Desktop/file.txt user@domain.com:/home/username/Desktop
```
where the first directory is pointing to a file on my machine, and the second directory first declares the domain to transfer to, then the directory to put it in. To recieve a file, just reverse the formula:
```
scp user@domain.com:/home/username/Desktop/file.txt /home/username/Desktop
```
Hope this helps until the ftp is figured out.

---

### Post by Reid_PMP on 2008-08-27
Marzhall,

I use Windows Vista as my pc and Dreamweaver as my web development application. Dreamweaever can either connect via ftp or local network. I've used both methods of connecting DW to my test and production servers. This is the first time I've tried to setup a server at home.

Being a newbie to setting up a linux server doesn't help. For every problem I can find ten solutions that don't seem to clear up my problem.

Can someone tell me why vsftpd would not be listening to port 21? (yes, I've setup the config file to listen to port 21.)

---

### Post by Reid_PMP on 2008-08-30
Resolution to my problem:

low level format and install ubuntu server verson 8.04

The reinstalls must not have removed all of the old files, thus corrupting my install.

---

### Post by windependence on 2008-08-30
Re-installing is almost never a fix for all things Linux. This is the Windoze way. Most times, in Linux or Unix, it just leaves configs all over and messes you up.

FYI from Windows you can use WinSCP to put and get files and even edit code with the built in editor. I use it all the time on my sites, but then I don't use a WYSIWYG editor any more. If you use CSS for your design, it really isn't that hard without a GUI dev environment.

-Tim

---

