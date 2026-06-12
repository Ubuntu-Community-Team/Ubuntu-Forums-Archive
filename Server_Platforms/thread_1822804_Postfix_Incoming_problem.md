---
title: "Postfix Incoming problem"
date: 2011-08-11
forum: Server Platforms
---

### Post by balagosa on 2011-08-11
good day to all as subject said, I am having trouble with my postfix reconfiguration. My email is hosted on a domain. The DNS settings have no problem anymore because I can send email but I can not receive any emails.

The error listed in /var/log/maillog shows this
```
Aug 11 22:11:39 mail postfix/qmgr[2513]: BDACEF048B: from=<daniel_gelie@yahoo.com>, size=3413, nrcpt=1 (queue active)
Aug 11 22:11:39 mail MailScanner[2740]: Uninfected: Delivered 1 messages
Aug 11 22:11:39 mail postfix/smtp[3498]: BDACEF048B: to=<dbalagosa@jinisyssoftware.com>, relay=none, delay=2.6, delays=2.6/0/0/0, dsn=5.4.4, status=bounced (Host or domain name not found. Name service error for name=cbuchidc00.jinisyssoftware.com type=A: Host not found)
Aug 11 22:11:39 mail postfix/cleanup[3492]: CCE01F0486: message-id=<20110811141139.CCE01F0486@mail.jinisyssoftware.com>

```

The error lies in the **Host or domain name not found. Name service error for name=cbuchidc00.jinisyssoftware.com type=A: Host not found**. I have setup a DMZ and this is where i placed my relay mail. The log above is from the relay mail. I know the mail server is working fine because I can send email. The email server connects directly to internet without going through DMZ.

```
192.168.100.221         cbuchidc00.jinisyssoftware.com cbuchidc00
127.0.0.1       mail.jinisyssoftware.com mail localhost.localdomain localhost
10.0.10.200     mail.jinisyssoftware.com mail

```
Above code is my /etc/hosts file. The IP address of 192.168.100.221 is my mail server. The DMZ relay mail is 10.0.10.200. 

The relay mail has a MailScanner and postfix installed.

---

### Post by dinu90 on 2011-08-11
check /etc/nsswitch.conf
It should be:
```

hosts:      files dns

```
If dns comes first then you need to change it to be second

[**java tutorials**]("http://www.java-forums.org/java-tutorial/")

---

### Post by balagosa on 2011-08-11
Opened the file and it is as you said sir, no changes made. Thanks for replying

---

### Post by balagosa on 2011-08-11
no hope?

---

### Post by balagosa on 2011-08-12
```
postconf -e 'smtp_host_lookup = dns, native'
```

This seemed to work, hopefully this will be permanent. I execute above code in terminal. As a result it added that to the last line of my **/etc/postfix/main.cf** file. Odd enough because that option is not included in my postfix version

**man postconf** for more info

---

