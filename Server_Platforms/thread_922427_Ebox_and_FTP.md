---
title: "Ebox and FTP"
date: 2008-09-17
forum: Server Platforms
---

### Post by zoggolino on 2008-09-17
Hi there,

I'm running an Ubuntu 8.04 server with the ebox plattform for user and groups managing. Now, I like to use FTP-Access with this users to there home directories. I tried pure-Ftpd-ldap. I have to access the ebox user informations on the ldap-server. But I have no clue how to configure it. Does someone have some experiences in this or a better solution?

thanks for every help!

Urs

---

### Post by Vegan on 2008-09-17
i use vsftpd without problem

sudo apt-get install vsftpd

---

### Post by zoggolino on 2008-09-18
Thanks for your fast answer. i changed now to vsftp and the installing was easy. But still i have a problem: I can't reach the ftp-server from outside my network.

I tried ```
$ telnet localhost 21
``` and got a connection. If try telnet localhost mydomain I didn't get any connection. I tried also with Filezilla from another network.

If I watch my port with nmap port 21 is open local but not from my domain:

```

$ nmap -sV localhost

Starting Nmap 4.53 ( http://insecure.org ) at 2008-09-18 10:43 CEST
Interesting ports on localhost.localdomain (127.0.0.1):
Not shown: 1695 closed ports
PORT     STATE SERVICE     VERSION
21/tcp   open  ftp         vsftpd 2.0.6
22/tcp   open  ssh         OpenSSH 4.7p1 Debian 8ubuntu1.2 (protocol 2.0)
25/tcp   open  smtp        Postfix smtpd
80/tcp   open  http        Apache httpd 2.2.8 ((Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch mod_ssl/2.2.8 OpenSSL/0.9.8g mod_perl/2.0.3 Perl/v5.8.8)
137/tcp  open  netbios-ssn Samba smbd 3.X (workgroup: STADTLANDFLUSS)
138/tcp  open  netbios-ssn Samba smbd 3.X (workgroup: STADTLANDFLUSS)
139/tcp  open  netbios-ssn Samba smbd 3.X (workgroup: STADTLANDFLUSS)
143/tcp  open  imap        Courier Imapd (released 2005)
389/tcp  open  ldap        OpenLDAP 2.2.X
443/tcp  open  http        Apache SSL-only mode httpd
445/tcp  open  netbios-ssn Samba smbd 3.X (workgroup: STADTLANDFLUSS)
465/tcp  open  ssl/smtp    Postfix smtpd
631/tcp  open  ipp         CUPS 1.2
783/tcp  open  spamd       SpamAssassin spamd
993/tcp  open  ssl/unknown
3306/tcp open  mysql       MySQL 5.0.51a-3ubuntu5.1
5432/tcp open  postgresql  PostgreSQL DB
9101/tcp open  jetdirect?
9102/tcp open  jetdirect?
Service Info: Host: eBox; OSs: Unix, Linux


```

```

nmap -sV xxx.org

Starting Nmap 4.53 ( http://insecure.org ) at 2008-09-18 10:40 CEST
Interesting ports on 217-162-223-223.dclient.hispeed.ch (217.162.223.223):
Not shown: 1708 filtered ports
PORT    STATE  SERVICE      VERSION
25/tcp  open   smtp         Postfix smtpd
80/tcp  open   http         Apache httpd 2.2.8 ((Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch mod_ssl/2.2.8 OpenSSL/0.9.8g mod_perl/2.0.3 Perl/v5.8.8)
137/tcp closed netbios-ns
138/tcp closed netbios-dgm
139/tcp closed netbios-ssn
445/tcp closed microsoft-ds
Service Info: Host: eBox

Service detection performed. Please report any incorrect results at http://insecure.org/nmap/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 20.194 seconds
```

---

### Post by windependence on 2008-09-18
You need to forward your port 21 to your server from your router.

-Tim

---

### Post by zoggolino on 2008-09-18
Ok. That works now. Thanks a lot. I had also to put a port forwarding in ebox configurations. But how get vsFTP the users from ebox or my ldap-server?

---

