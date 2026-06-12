---
title: "Ubuntu 10.10 - Help with FTP server"
date: 2011-02-28
forum: Server Platforms
---

### Post by fernandu3 on 2011-02-28
Hi all,

Not sure if this is the correct forum to ask this question:

Does anybody know which ftp come (by default) with Ubuntu Server 10.10 ?

I am asking this because I installed a server with Ubuntu 10.10, I was able to connect to the server using Putty and also using a FTP client. But I didn't install the ftp server by myslef.
When  I was installing Ubuntu, I choose LAMP server + FTP, DNS, Email etc...

I searched for "vsftp" and "proftp" but seems that they are not installed.

Could you help please ?

I am afraid of installing a new ftp (vsftp) if I already have one (once I can connect using a FTP client - WinSCP).

Thanks.

---

### Post by Kljuka on 2011-02-28
I don't know which one comes with it (if any).
check /etc/ directory:
```

ls -la | grep "ftp"
```

or which process is listening on port 21:
```

netstat -nlp | grep ":21"
```

It might be pure-ftpd

---

### Post by HermanAB on 2011-02-28
Run Synaptic and look for one of vsftpd, proftpd or pure-ftpd.  They all work fine.

---

### Post by fernandu3 on 2011-02-28
> **Kljuka said:**
> I don't know which one comes with it (if any).
check /etc/ directory:
```

ls -la | grep "ftp"
```or which process is listening on port 21:
```

netstat -nlp | grep ":21"
```It might be pure-ftpd


No results for those commands.

I just figured out what happened...
I don´t have a ftp server installed.
When I connected to the server using WinSCP it was using SFTP not FTP protocol.

I fount this comment in other thread:

"I personally would not bother with FTP at all and stick to OpenSSH  instead. The entire exercise with setting up a FTP server and enabling  SSL certificates so you'd get "FTPS" seems highly redundant to me, when  instead you could simply stick to SSH and use SFTP which already  provides this functionality right out of the box."

Should I install a FTP server or continue using SSH ? 
Sorry, this is the first time that I setup a server. Only 2-3 people will use FTP...

---

### Post by Kljuka on 2011-02-28
if you trust those people, you can use ssh. But beware that they have shell access to your server (so they can read most of your server files/config).

---

### Post by usatonycuba on 2011-03-06
> **fernandu3 said:**
> Hi all,

Not sure if this is the correct forum to ask this question:

Does anybody know which ftp come (by default) with Ubuntu Server 10.10 ?

I am asking this because I installed a server with Ubuntu 10.10, I was able to connect to the server using Putty and also using a FTP client. But I didn't install the ftp server by myslef.
When  I was installing Ubuntu, I choose LAMP server + FTP, DNS, Email etc...

I searched for "vsftp" and "proftp" but seems that they are not installed.

Could you help please ?

I am afraid of installing a new ftp (vsftp) if I already have one (once I can connect using a FTP client - WinSCP).

Thanks.
When you installed Ubuntu, it is possible that you also have installed "SSH Server" .. and if you could connect with Putty .. is because (by default) Putty can connect you THROUGH SSH client.....  (SSH is the default, I mean pre-selected connection type in Putty).

To install another ftp client, I do not think you have some kind of issue... [Here is]("http://www.ivankristianto.com/os/ubuntu/howto-install-ftp-server-with-user-management-in-ubuntu/1181/") a good tutorial installing pure-ftpd, i do used that one, and works pretty good.. GL

---

