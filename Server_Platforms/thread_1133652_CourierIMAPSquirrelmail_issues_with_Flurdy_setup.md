---
title: "Courier/IMAP/Squirrelmail issues with Flurdy setup"
date: 2009-04-23
forum: Server Platforms
---

### Post by bzarr on 2009-04-23
I seem to be having a few issues with the flurdy setup from here:

[http://flurdy.com/docs/postfix/]("http://flurdy.com/docs/postfix/")

Firstly when receiving mail I get the following in the log:
imapd: chdir /var/spool/mail/virtual/bzarr: Not a directory

Do I need to create this manually? I thought Postfix was supposed to create the folders automatically?

From the webmail interface, Squirrelmail, I get this:
ERROR: Connection dropped by IMAP server.

I'm assuming these are related, imap failing because it can't find my mail folder?

Please help!

Many thanks in advance,

Lee

---

### Post by spiderbatdad on 2009-04-23
well your guide conatains a section telling you to create the folder.
virtual in that case, is actually a user account.
```
# to add if there is not a virtual user
 mkdir /var/spool/mail/virtual 
groupadd virtual -g 5000 
useradd virtual -u 5000 -g 5000 
chown -R virtual:virtual /var/spool/mail/virtual
```

The other problem seem like an authentication failure, so they could be related. Creating a mailserver with this guide is not easy. It is going to take a lot of tweaking. You might want to look into some of the freenode irc channels ie., #courier, #postfix, #squirrelmail, but you may not get a friendly reception if you have not thoroughly read all available documentation, and dont expect immediate answers.

---

### Post by bzarr on 2009-04-23
Hey, thanks for the info...

Re the 'virtual' user setup, I did create it exactly like that, /var/spool/mail/virtual exists, but should i have done that like this instead then:

```

mkdir /var/spool/mail/virtual 
groupadd bzarr -g 5000 
useradd bzarr -u 5000 -g 5000 
chown -R bzarr:bzarr /var/spool/mail/virtual

```

With 'bzarr' being the username?

Surely if I'm using multiple email inboxes though something needs to automatically create these within /var/spool/mail/virtual/ with their own priviledges? And should this not be set somewhere?

Like:
/var/spool/mail/virtual/fred/
/var/spool/mail/virtual/john/
/var/spool/mail/virtual/bob/

Thanks again,

Lee

---

### Post by bzarr on 2009-04-23
Hmmmm... Just had another look at this and in the /var/spool/mail/virtual/ folder i do now have something, but it's not a folder, it's a file 'bzarr'

If I open the file, I see an email.

It appears squirrelmail though is looking for a folder, not file...

Any ideas?

---

### Post by john6six on 2009-04-23
Delete the bzarr file from the virtual folder. Send yourself another email and see if the system creates the /virtual/bzarr folder and puts the email in there or if it saves the email directy in the virtual folder again. If it saves the email as a file in the virtual folder and doesn't create the bzarr folder, than there is something wrong with your config.

---

### Post by bzarr on 2009-04-23
Thanks John,

I notice also that I'm getting this:
postfix/qmgr[7704]: warning: connect to transport smtp-amavis: Connection refused

Where is this transport setup? I can't find it in any configs.

Regards,

L

---

### Post by john6six on 2009-04-23
That is set up in master.cf.

[https://help.ubuntu.com/community/PostfixAmavisNew](https://help.ubuntu.com/community/PostfixAmavisNew)

---

### Post by bzarr on 2009-04-24
That helped a little bit, although the document mentions chmod 775, I could only get it to work by doing chmod 777 on the amavis/db folder.

Seems there's possibly a problem with my firewall, these are the settings shown by netstat:
```

Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 localhost.localdo:60000 *:*                     LISTEN      -
tcp        0      0 localhost.localdo:10024 *:*                     LISTEN      -
tcp        0      0 localhost.localdo:10025 *:*                     LISTEN      -
tcp        0      0 localhost.localdo:mysql *:*                     LISTEN      -
tcp        0      0 *:submission            *:*                     LISTEN      -
tcp        0      0 localhost.localdo:spamd *:*                     LISTEN      -
tcp        0      0 *:www                   *:*                     LISTEN      -
tcp        0      0 *:ssmtp                 *:*                     LISTEN      -
tcp        0      0 *:ssh                   *:*                     LISTEN      -
tcp        0      0 *:smtp                  *:*                     LISTEN      -
tcp        0      0 10.88.91.30:ssh         10.88.91.20:45517       ESTABLISHED -
tcp        0      0 10.88.91.30:ssh         10.88.91.20:45516       ESTABLISHED -
tcp6       0      0 [::]:imaps              [::]:*                  LISTEN      -
tcp6       0      0 [::]:pop3s              [::]:*                  LISTEN      -
tcp6       0      0 [::]:pop3               [::]:*                  LISTEN      -
tcp6       0      0 [::]:imap2              [::]:*                  LISTEN      -
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN      -

```

It doesn't show 'master' i.e. postfix listening for stmp (25), should it? Does it matter?

Thanks in advance again!

---

### Post by john6six on 2009-04-24
SMTP is running, just above the entries for you ssh session. I have recently built the same setup and it took me a couple rebuilds to get it working. Your original question was regarding squirrelmail and IMAP. Have you verified the server is working properly independent of IMAP? Do you get the proper response from "telnet localhost 25"? The last line should read "220 yourservername ESMTP Postfix" or something similar. You are putting the cart before the horse if you are trying to get IMAP working on a Postfix server that is not funtioning properly.

---

