---
title: "Send email vai MS Exchange"
date: 2011-11-29
forum: Server Platforms
---

### Post by clubbing80s on 2011-11-29
How can my scripts send email via MS Exchange server. The MS Exchange server requires authentication and STARTTLS. I can seem to get mail delivered via Sendmail, I keep getting the following error :

Nov 29 20:09:36 nzhmlwks0091 sm-mta[18533]: STARTTLS=client, relay=mail2.et.endace.com., version=TLSv1/SSLv3, verify=FAIL, cipher=AES128-SHA, bits=128/128
Nov 29 20:09:41 nzhmlwks0091 sm-mta[18533]: pAT79aTa018531: to=<greg.machin@endace.com>, ctladdr=<greg.machin@nzhmlwks0091.ad.endace.com> (187178764/187171329), delay=00:00:05, xdelay=00:00:05, mailer=relay, pri=120395, relay=mail2.et.endace.com. [192.168.32.6], dsn=5.0.0, stat=Service unavailable

Please help ....

G

---

### Post by clubbing80s on 2011-11-29
Configuring Authenticated Sendmail for sendind email via Exchange.

There are many ways to configure sendmail but the final options that need to be set are the same . YMMV .

using m4 methode on a clean install of sendmail. 
Note this applies to sendmail version 8.12 and higher.


root@nzhmlwks0091:/root# cd /etc/mail
root@nzhmlwks0091:/etc/mail# vi sendmail.mc

add the following line :
    define(`SMART_HOST',`smtp.mydom.com') dnl

Save using 
:wq!

root@nzhmlwks0091:/etc/mail# m4 sendmail.mc > sendmail.cf
this will with a new configuration file. 

root@nzhmlwks0091:/etc/mail# vi access

add the following line replaing "first.last" and "Password" with you AD login and password :
    AuthInfo:smtp.et.endace.com    "U:smmsp" "I:first.last" "P:Password" "M:LOGIN"

Save using 
:wq!

root@nzhmlwks0091:/etc/mail# makemap hash access.db < access
this converts the test file access into a hash database file access.db

root@nzhmlwks0091:/etc/mail# service sendmail restart
this will load the new configuration. 

root@nzhmlwks0091:/etc/mail# tail -f /var/log/mail.log 

tail the log file to check Sendmail has started without errors and while sending test messages.

For earlier versions of Sendmail :
I haven't tested the following but it should work.

root@nzhmlwks0091:/root# cd /etc/mail
root@nzhmlwks0091:/etc/mail# vi sendmail.mc

add the following lines :
    define(`SMART_HOST',`smtp.mydom.com') dnl
    FEATURE(`authinfo',`hash /etc/mail/auth/client-info.db')dnl

Save using 
:wq!

Create the directory and file that will hold the user authentication information.

root@nzhmlwks0091:/etc/mail# mkdir auth
root@nzhmlwks0091:/etc/mail# chmod 700 auth
root@nzhmlwks0091:/etc/mail# cd auth
root@nzhmlwks0091:/etc/mail# touch client-info
root@nzhmlwks0091:/etc/mail# vi client-info

add the following line replaing "first.last" and "Password" with you AD login and password :
    AuthInfo:smtp.et.endace.com    "U:smmsp" "I:first.last" "P:Password" "M:LOGIN"

Save using 
:wq!

root@nzhmlwks0091:/etc/mail# makemap hash client-info.db < client-info

root@nzhmlwks0091:/etc/mail# service sendmail restart
this will load the new configuration. 

root@nzhmlwks0091:/etc/mail# tail -f /var/log/mail.log 

tail the log file to check Sendmail has started without errors and while sending test messages.

---

### Post by clubbing80s on 2011-11-29
Although I still have verify=FAIL, my mail is going out with using authentication.

---

### Post by xtwochu on 2011-12-16
Hellow
I would like to send email via MS exchange2003
I have followed your instruction but I encounter this error:


Dec 16 13:14:25 vmdemo sm-mta[22710]: pBG5EPQU022708: AUTH=client, available mechanisms do not fulfill requirements
Dec 16 13:14:25 vmdemo sm-mta[22710]: AUTH=client, relay=<HIDDEN>, temporary failure, connection abort

Could you help?

---

### Post by SeijiSensei on 2011-12-16
> **clubbing80s said:**
> Although I still have verify=FAIL, my mail is going out with using authentication.

"verify=FAIL" means that the sending and receiving servers can't verify each other's SSL certificates.  If you're using a self-signed certificate, all your messages will fail verification.  As you discovered, they still get sent.

---

