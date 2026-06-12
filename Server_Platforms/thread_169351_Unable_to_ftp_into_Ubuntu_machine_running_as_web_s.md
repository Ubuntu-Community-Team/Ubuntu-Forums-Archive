---
title: "Unable to ftp into Ubuntu machine running as web server"
date: 2006-05-02
forum: Server Platforms
---

### Post by transistor on 2006-05-02
I have my Ubuntu 5.10 box set up as an intranet server. Apache running and serving up php / mysql, etc. All is well ... except that I can not ftp into it from my Windows machines. Ultraedit, Filezilla, etc. can't connect.

I'm using my admin account and have tried another account with all priviledges enabled.

Do I have to turn something on for ftp to work?

Thanks.

---

### Post by mandrakethepenguin on 2006-05-02
What ftpd are you using? To test your ftpd, in gnome go to **Places -> Connect to Server** Choose FTP (with login) and for the server, enter 127.0.01 . Then of course enter all the login info.

---

### Post by harisund on 2006-05-02
I hope you have a FTP server installed :)

Anyway, to make sure you have a FTP server running, the above post would be a good suggestion. Otherwise, simply open a terminal and type in "sudo netstat -plant" to get a list of open ports on your machine. The FTP port is by default 21 I think. 

If not, you will have to install a FTP server first.

---

### Post by transistor on 2006-05-03
Thanks, chaps.

I have ftpd installed. Here's what netstat reports.
```

 sudo netstat -plant
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:32770         0.0.0.0:*               LISTEN     6173/hpiod
tcp        0      0 127.0.0.1:32771         0.0.0.0:*               LISTEN     6187/python
tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN     6320/mysqld
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN     6579/smbd
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     10299/cupsd
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN     6469/master
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN     6579/smbd
tcp        0      0 127.0.0.1:32770         127.0.0.1:51845         ESTABLISHED6173/hpiod
tcp        0      0 127.0.0.1:51845         127.0.0.1:32770         ESTABLISHED6187/python
tcp        0      0 10.62.10.7:3306         10.62.7.13:4257         ESTABLISHED6320/mysqld
tcp        0      0 127.0.0.1:56182         127.0.0.1:631           ESTABLISHED7519/gnome-cups-ico
tcp        0      0 127.0.0.1:631           127.0.0.1:56182         ESTABLISHED10299/cupsd
tcp6       0      0 :::80                   :::*                    LISTEN     25123/apache2
tcp6       0      0 :::22                   :::*                    LISTEN     6596/sshd

```

---

### Post by harisund on 2006-05-03
You dont seem to have a ftp server installed at all? 

if you look at all the listening ports, you won't find a 21. That means you don't have any ftp server running.

---

### Post by transistor on 2006-05-03
Thanks Harisund.
Do you have any idea how I should turn it on? I tried mandrakethepenguin's suggestion but wasn't too sure of what to enter or how this would enable ftp.

---

### Post by hagen00 on 2006-05-03
> I have ftpd installed. Is that even an ftp server? I've got vsftpd. 

```
apt-get install vsftpd
```

Edit: Hmm, i see that it is an ftp server.

Then try doing
sudo /etc/init.d/ftpd start

---

### Post by harisund on 2006-05-03
Firstly, I think ftpd is not a stand alone server, but is rather one that relies on inetutils-inetd to start. 

I don't know how to configure vsftpd but I can give you a quick how to for configuring another ftp server. 

First, begin with ```
sudo apt-get install proftpd inetutils-inetd
```
At some point you may be asked if you want it to run stand alone or with inetd. I chose the latter. 

Then edit your /etc/inetd.conf to make sure it has the following line in it: 
```
 ftp   stream   tcp   nowait   root  /usr/sbin/tcpd /usr/sbin/proftpd
```
It may already have this line, in which case you don't really need to bother. 

Then edit your /etc/proftpd.conf to ensure it has the following lines in this way ```

ServerType   inetd
User       your_user_name
Group      your_user_name

```
The user and group occur a bit later in the file,and ensure that your_user_name is replaced appropriately. 

Then to start the server you would do
```
sudo invoke-rc.d inetutils-inetd start
```
And to switch it off it would be
```
sudo invoke-rc.d inetutils-inetd stop
```

---

