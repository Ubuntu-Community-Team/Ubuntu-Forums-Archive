---
title: "SFTP connections refused"
date: 2017-01-25
forum: Server Platforms
---

### Post by keith46 on 2017-01-25
I've got a brand new installation of 16.04LTS (server) and ISPconfig.  I followed the guide here: [https://www.howtoforge.com/tutorial/perfect-server-ubuntu-16.04-with-apache-php-myqsl-pureftpd-bind-postfix-doveot-and-ispconfig/](https://www.howtoforge.com/tutorial/perfect-server-ubuntu-16.04-with-apache-php-myqsl-pureftpd-bind-postfix-doveot-and-ispconfig/)

I've tried creating several FTP user accounts (in the ISPConfig FTP user control panel) and when I attempt to connect with either SFTP or FTP I get a "connection refused" message in my file transfer software.

Could someone please offer some direction on where to troubleshoot?

---

### Post by darkod on 2017-01-26
Start by checking the logs in /var/log. The generic one is syslog but in addition to that I think ispconfig has a subfolder with more logs.

If I'm not mistaken I saw once that ispconfig does not configure correctly the ftp where to look for the logins (the correct mysql DB and settings), so double check the ftp configuration on the server. It creates the logins but if the ftp does not know where to look for them, it's pointless.

---

### Post by keith46 on 2017-01-26
I had a look at the syslog and found some interesting info (pasted below).  It looks like the server is trying to resolve the IP connection to a hostname.  What's weird is that if I have an SSH session open at the time I try to connect with FTP, the SSH session gets IMMEDIATELY dropped and I cannot reconnect - I get a connection refused message.

```
Jan 26 09:50:10 reaver postfix/smtpd[28836]: warning: hostname vps863.hidehost.net does not resolve to address 91.200.12.125: Name or service not known
Jan 26 09:50:10 reaver postfix/smtpd[28836]: connect from unknown[91.200.12.125]
Jan 26 09:50:12 reaver postfix/smtpd[28836]: warning: unknown[91.200.12.125]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
Jan 26 09:50:12 reaver postfix/smtpd[28836]: lost connection after AUTH from unknown[91.200.12.125]
Jan 26 09:50:12 reaver postfix/smtpd[28836]: disconnect from unknown[91.200.12.125] ehlo=1 auth=0/1 commands=1/2
Jan 26 09:50:27 reaver postfix/smtpd[28836]: warning: hostname vps863.hidehost.net does not resolve to address 91.200.12.140: Name or service not known
Jan 26 09:50:27 reaver postfix/smtpd[28836]: connect from unknown[91.200.12.140]
Jan 26 09:50:30 reaver postfix/smtpd[28836]: warning: unknown[91.200.12.140]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
Jan 26 09:50:30 reaver postfix/smtpd[28836]: lost connection after AUTH from unknown[91.200.12.140]
Jan 26 09:50:30 reaver postfix/smtpd[28836]: disconnect from unknown[91.200.12.140] ehlo=1 auth=0/1 commands=1/2
```

---

### Post by QIII on 2017-01-26
Hello!

Please use code tags when posting commands or their results.  That preserves formatting and makes your post easier to read.

To use code tags:

1.  Click on the # button in the menu above the text entry box, place your cursor between the code tags that appear and type or paste your text.

2.  Type or paste your text, highlight it and click the # button.

3.  Type [noparse]```
[/noparse] at the beginning of your text and [noparse]
```[/noparse] at the end of your text.

Thanks!

---

### Post by keith46 on 2017-01-26
Does anyone happen to know where pure-ftpd logs are saved?  I think if I could find those, it might help shed some light.  The only thing I see in /var/log/pure-ftpd/ is a transfer.log which is empty.

---

### Post by keith46 on 2017-01-26
Apparently this is a common problem when installing Ubuntu and ISPConfig using the "perfect server" guides.  I'd like to thank the site admins, who literally had more time to spend correcting my grammar than offering any help.  I'd also like to thank myself for helpming me solve this problem.  I couldn't have done it without me.

If anyone else runs into this issue, [here's a link to the solution I used]("http://www.green-hornet.com/2017/01/30/how-to-fix-ftp-connection-refused-problems-with-ubuntu-and-ispconfig/").  Hopefully you'll get more traction on the forums than I did.

---

### Post by raja.genupula on 2017-01-26
We are so much glad that you have solved your issue.

Please mark this thread as solved.

Thank you.

---

