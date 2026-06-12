---
title: "Script to send email ssmtp for pure-uploadscript"
date: 2009-11-23
forum: Server Platforms
---

### Post by Almeister9 on 2009-11-23
Hi All,

I am looking for some help to add a much needed functionality to an FTP server.
The server is built on Ubuntu 9.04 32-bit Server and PureFtpd using virtual users as per a tutorial at "[http://www.howtoforge.com]("http://www.howtoforge.com/virtual-hosting-with-pureftpd-and-mysql-incl-quota-and-bandwidth-management-on-ubuntu-9.04")" by Falko.

I want to have an email sent when a file is uploaded to the FTP server, to let us know that it has arrived.

I have successfully installed ssmtp and configured it to relay emails through my gmail account for now. I can successfully send an email from the command line by typing "ssmtp recipient_email_address" Then using the format
```
To: recipient_email@Address
From: originating@address
Subject: Subject Line

Body Text
```Then hitting crtl-D

I believe that I have configured Pureftpd's conf file to enable the pure-uploadscript
```
STANDALONE

UPLOADUID=0
UPLOADGID=0

UPLOADSCRIPT=/usr/local/sbin/uploadhandler.sh
```I read on the pure-uploadscript man page that UID and GID have to be 0
Also
```
echo "yes" > /etc/pure-ftpd/conf/CallUploadScript
```

I tried to follow the instructions from 
[http://blog.derjohn.de/comments/start/2006-11-14/1]("http://blog.derjohn.de/comments/start/2006-11-14/1") 
but I didn't know how to do some of the things suggested.

If some kind soul could show me how to make a script that would send an email using ssmtp, hopefully passing the arguments from pure-uploadscript, which I think are "$1" among others, I would be VERY grateful.

Cheers Al.

---

### Post by Almeister9 on 2009-11-23
I have made a little more progress.
I have changed /etc/default/pure-ftpd-common to read
UPLOADUID=2001 
UPLOADGID=2001
This is the userID of pureftpd.
I then made a script called /usr/sbin/upload2.sh which has the following code:
```
#!/bin/sh
echo "$1" > /tmp/pure-was-here$(date +%Y%m%d%H%M%S)
```I then did this```
chmod +x upload2.sh
```and restarted Pureftpd.
I then uploaded a file to the ftp server and went to /tmp and the file was there!! YAY!
So I made a txt file called /usr/sbin/msg1.txt which contains:
```
To: recipient@address
From: Originating@address
Subject: Test from FTP Server

This is a test
```then created a script called /usr/sbin/upload1.sh which contains:```
ssmtp recipient@address.com < msg1.txt
```and I ran```
chmod +x upload1.sh
```then restarted PureFTPd.

This however does not work.
If I move to the containing folder
cd /usr/sbin
and type ./upload1.sh
The email IS sent.

I feel I am very close now but it is still not working.
Any help Anyone?

---

### Post by Almeister9 on 2009-11-24
Using this script I found at [http://www.axllent.org/docs/networking/ssmtp_on_the_console]("http://www.axllent.org/docs/networking/ssmtp_on_the_console")

```
#!/bin/bash
CURDATE=`date`
ssmtp -oi recipient@address.com << EOF
From: FTP Server <originator@gmail.com>
To: recipient@address.com
Subject: File uploaded to FTP SERVER on $CURDATE

The file $1 was uploaded to the FTP-SERVER on $CURDATE.

EOF
```

$1 is the argument passed from pure-uploadscript(8) so the email I got says:

The file home/www.example.com/ST15_01.pdf was uploaded ...

YAY double YAY
and thanks to axllent.org for the script

---

