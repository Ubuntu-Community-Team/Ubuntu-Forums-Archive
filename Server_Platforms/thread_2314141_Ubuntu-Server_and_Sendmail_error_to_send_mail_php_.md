---
title: "Ubuntu-Server and Sendmail error to send mail php from FORM"
date: 2016-02-18
forum: Server Platforms
---

### Post by 0p3nS0urc3 on 2016-02-18
Hi guys

i have searched on previous threads but haven´t found any with a clear ansewer/solution type to solve my issue i will try to explain it briefly


first things first:

1- I have installed a specific machine at our company running ubuntu-server 14xx explicit running for e-mail server (setup ISPconfig + Postfix + squirrelmail) for future webhosts, but ATM only using it as our E-mail server with POP3/IMAP etc.etc.

2- All our desktop workstations running with windows Outlook connected via POP3 + SMTP etc.etc. working great i can send and receive mails send outgoing for other mail providers and receive back.

3- We have another physical machine running as our webserver with apache2 etc....  on this machine the new website i am building uses a Contact form "This is where all my problems start" i have setup the contact form and on the contact.php i have edited and placed one of our e-mails to test receiving the conctact data.
and ofcourse it never reached.

4- so with php.ini i have checked that mail php is enabled,  that means that apt-get install sendmail was issued prior and installed correctly.


5- my var log is showing me the following errors

> 
Feb 18 16:29:31 mydomain sendmail[1590]: u1IJTV2q001590: from=www-data, size=129, class=0, nrcpts=1, msgid=<201602181929.u1IJTV2q001590@mydomain.com>, relay=www-data@localhost
Feb 18 16:29:31 mydomain sm-mta[1591]: u1IJTVKB001591: <dude1@mydomain.com>... User unknown
Feb 18 16:29:31 mydomain sendmail[1590]: u1IJTV2q001590: to=dude1@mydomain.com, ctladdr=www-data (33/33), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=30129, relay=[127.0.0.1] [127.0.0.1], dsn=5.1.1, stat=User unknown
Feb 18 16:29:31 mydomain sm-mta[1591]: u1IJTVKB001591: from=<www-data@mydomain.com>, size=129, class=0, nrcpts=0, proto=ESMTP, daemon=MTA-v4, relay=localhost [127.0.0.1]
Feb 18 16:29:31 mydomain sendmail[1590]: u1IJTV2q001590: u1IJTV2r001590: DSN: User unknown
Feb 18 16:29:31 mydomain sm-mta[1591]: u1IJTVKD001591: from=<>, size=2172, class=0, nrcpts=1, msgid=<201602181929.u1IJTV2r001590@mydomain.com>, proto=ESMTP, daemon=MTA-v4, relay=localhost [127.0.0.1]
Feb 18 16:29:31 mydomain sendmail[1590]: u1IJTV2r001590: to=www-data, delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=31153, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (u1IJTVKD001591 Message accepted for delivery)
Feb 18 16:29:31 mydomain sm-mta[1592]: u1IJTVKD001591: to=<www-data@mydomain.com>, delay=00:00:00, xdelay=00:00:00, mailer=local, pri=32394, dsn=2.0.0, stat=Sent
Feb 18 16:29:33 mydomain sendmail[1595]: u1IJTXI5001595: from=www-data, size=129, class=0, nrcpts=1, msgid=<201602181929.u1IJTXI5001595@mydomain.com>, relay=www-data@localhost
Feb 18 16:29:33 mydomain sm-mta[1596]: u1IJTXW0001596: <dude1@mydomain.com>... User unknown
Feb 18 16:29:33 mydomain sendmail[1595]: u1IJTXI5001595: to=dude1@mydomain.com, ctladdr=www-data (33/33), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=30129, relay=[127.0.0.1] [127.0.0.1], dsn=5.1.1, stat=User unknown
Feb 18 16:29:33 mydomain sm-mta[1596]: u1IJTXW0001596: from=<www-data@mydomain.com>, size=129, class=0, nrcpts=0, proto=ESMTP, daemon=MTA-v4, relay=localhost [127.0.0.1]
Feb 18 16:29:33 mydomain sendmail[1595]: u1IJTXI5001595: u1IJTXI6001595: DSN: User unknown
Feb 18 16:29:33 mydomain sm-mta[1596]: u1IJTXW2001596: from=<>, size=2172, class=0, nrcpts=1, msgid=<201602181929.u1IJTXI6001595@mydomain.com>, proto=ESMTP, daemon=MTA-v4, relay=localhost [127.0.0.1]
Feb 18 16:29:33 mydomain sendmail[1595]: u1IJTXI6001595: to=www-data, delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=31153, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (u1IJTXW2001596 Message accepted for delivery)
Feb 18 16:29:33 mydomain sm-mta[1597]: u1IJTXW2001596: to=<www-data@mydomain.com>, delay=00:00:00, xdelay=00:00:00, mailer=local, pri=32394, dsn=2.0.0, stat=Sent
Feb 18 16:30:01 mydomain sm-mta[1628]: u1IJU1E8001628: localhost [127.0.0.1] did not issue MAIL/EXPN/VRFY/ETRN during connection to MTA-v4
Feb 18 16:35:01 mydomain sm-mta[1730]: u1IJZ1w8001730: localhost [127.0.0.1] did not issue MAIL/EXPN/VRFY/ETRN during connection to MTA-v4
Feb 18 16:36:06 mydomain sendmail[1779]: u1IJa6kL001779: from=www-data, size=129, class=0, nrcpts=1, msgid=<201602181936.u1IJa6kL001779@mydomain.com>, relay=www-data@localhost
Feb 18 16:36:06 mydomain sm-mta[1780]: u1IJa6dB001780: <dude1@mydomain.com>... User unknown
Feb 18 16:36:06 mydomain sendmail[1779]: u1IJa6kL001779: to=dude1@mydomain.com, ctladdr=www-data (33/33), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=30129, relay=[127.0.0.1] [127.0.0.1], dsn=5.1.1, stat=User unknown
Feb 18 16:36:06 mydomain sm-mta[1780]: u1IJa6dB001780: from=<www-data@mydomain.com>, size=129, class=0, nrcpts=0, proto=ESMTP, daemon=MTA-v4, relay=localhost [127.0.0.1]
Feb 18 16:36:06 mydomain sendmail[1779]: u1IJa6kL001779: u1IJa6kM001779: DSN: User unknown
Feb 18 16:36:06 mydomain sm-mta[1780]: u1IJa6dD001780: from=<>, size=2172, class=0, nrcpts=1, msgid=<201602181936.u1IJa6kM001779@mydomain.com>, proto=ESMTP, daemon=MTA-v4, relay=localhost [127.0.0.1]
Feb 18 16:36:06 mydomain sendmail[1779]: u1IJa6kM001779: to=www-data, delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=31153, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (u1IJa6dD001780 Message accepted for delivery)
Feb 18 16:36:06 mydomain sm-mta[1782]: u1IJa6dD001780: to=<www-data@mydomain.com>, delay=00:00:00, xdelay=00:00:00, mailer=local, pri=32394, dsn=2.0.0, stat=Sent
Feb 18 16:40:01 mydomain sm-mta[1881]: u1IJe1cn001881: localhost [127.0.0.1] did not issue MAIL/EXPN/VRFY/ETRN during connection to MTA-v4






on the sendmail config folder i have the 

local-host-names

localhost
mydomain.con


Any hints and advises will be appreciated as so far i have not been able to fix it, as i still have some doubts of how the system fully works

from what i understood for security reasons the contact form gets submited locally to a database where the data gets stored right?
then sendmail collects this data and sends it to my external mail.domainservername? together with the destination e-mail address from my external  mail.domainservername right?

so for now i am still not sure of the message in var/log   DSN=5.1.1.   USER unknown

Edit1 = BTW i have removed from local-host-names  in sendmail config  my    mydomain.com  and left only localhost, but still getting the same error.

---

### Post by 0p3nS0urc3 on 2016-02-18
Ok guys

i have tested the  mailtest.php sent to another e-mail outside our e-mail server from the company and the actuall system is working sending e-mail correctly i have analyzed the log from sendmail in var/log and it worked , also checked and it received the e-mail.
So the problem now is surely on our side somewhere on our domain local e-mail server...

> Feb 18 17:47:37 mydomain sendmail[4282]: u1IKlbP8004282: from=www-data, size=126, class=0, nrcpts=1, msgid=<201602182047.u1IKlbP8004282@mydomain.com>, relay=www-data@localhostFeb 18 17:47:37 mydomain sm-mta[4283]: u1IKlbAm004283: from=<www-data@mydomain.com>, size=407, class=0, nrcpts=1, msgid=<201602182047.u1IKlbP8004282@mydomain.com>, proto=ESMTP, daemon=MTA-v4, relay=localhost [127.0.0.1]


Feb 18 17:47:37 mydomain sendmail[4282]: u1IKlbP8004282: to=contact@mydomain2.com, ctladdr=www-data (33/33), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=30126, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (u1IKlbAm004283 Message accepted for delivery)
Feb 18 17:47:42 mydomain sm-mta[4285]: STARTTLS=client, relay=mydomain2-com02e.mail.protection.outlook.com., version=TLSv1/SSLv3, verify=FAIL, cipher=ECDHE-RSA-AES256-SHA384, bits=256/256
Feb 18 17:47:44 mydomain sm-mta[4285]: u1IKlbAm004283: to=<contact@mydomain2.com>, ctladdr=<www-data@mydomain.com> (33/33), delay=00:00:07, xdelay=00:00:07, mailer=esmtp, pri=120407, relay=mydomain2-com0...ction.outlook.com. [207.46.163.247], dsn=2.0.0, stat=Sent (<201602182047.u1IKlbP8004282@mydomain.com> [InternalId=26929444962030, Hostname=SN1PR12MB0864.namprd12.prod.outlook.com] 6074 bytes in 0.368, 16.085 KB/sec Queued mail for delivery)




---

### Post by SeijiSensei on 2016-02-18
On the machine running sendmail, what do you see if you run the command "host -t mx mydomain.com"? Does it point to that server?

Sendmail consults DNS first to decide where to route a message.  You can override the DNS results with a mailertable database, but let's start with DNS first.

I'm assuming there's an account called "dude1" on the server or that it's an alias for some other address.  If not, that's certainly a big problem to start with.

Here's another test you can try.  Connect to the server with the command
```
telnet host.mydomain.com 25
```
where host.mydomain.com is the machine's fully-qualified domain name.  It should be the name referenced in the MX records for mydomain.com.  Then when sendmail replies, try the following dialog
```

ehlo localhost
==> sendmail replies
mail from: you@somewhere.com
==> reply
rcpt to: dude1@mydomain.com
==> What happens here??

```

---

### Post by 0p3nS0urc3 on 2016-02-20
Hi SeijiSensei

Thanks for your input ok so lets check the output result

> test#   host -t mx mydomain.com
mydomain.com mail is handled by 10 mail.mydomain.com


test# telnet mydomain.com 25

Trying xxx.xxx.xxx.xx.... (ip ofuscated but its the real public ip of the machine webmail server)
Connected to mydomain.com
Escape character is '^]'.
220 email.mydomain.com ESMTP Postfix (Ubuntu)
quit
221 2.0.0 Bye


In other words i configured sendmail with   mydomain.com , but looks like i need to configure it with my  email.mydomain.com ?? cause thats configured for the e-mail server.. so looks like i configured it wrong?

do i need to change this ?

and yes dude1.mydomain.com is an account created in our mail server it uses POP3/IMAP with SSL and TLS enabled on our mail server could it also be an issue there?


EDIT1=  OK update this is the output result now of var/log mail.log


> 
Feb 20 11:32:38 mydomain sendmail[7687]: alias database /etc/mail/aliases rebuilt by webpagina
Feb 20 11:32:38 mydomain sendmail[7687]: /etc/mail/aliases: 2 aliases, longest 4 bytes, 24 bytes total
Feb 20 11:32:39 mydomain sm-mta[6211]: restarting /usr/sbin/sendmail-mta due to signal
Feb 20 11:32:39 mydomain sm-mta[7734]: starting daemon (8.14.4): SMTP+queueing@00:10:00
Feb 20 11:33:52 mydomain sendmail[7811]: u1KEXq0M007811: from=www-data, size=317, class=0, nrcpts=1, msgid=<201602201433.u1KEXq0M007811@mydomain.com>, relay=www-data@localhost
Feb 20 11:33:52 mydomain sm-mta[7812]: u1KEXqu0007812: from=<www-data@mydomain.com>, size=599, class=0, nrcpts=1, msgid=<201602201433.u1KEXq0M007811@mydomain.com>, proto=ESMTP, daemon=MTA-v4, relay=localhost [127.0.0.1]
Feb 20 11:33:52 mydomain sendmail[7811]: u1KEXq0M007811: to=dude1@mydomain.com, ctladdr=www-data (33/33), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=30317, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (u1KEXqu0007812 Message accepted for delivery)
Feb 20 11:33:52 mydomain sm-mta[7814]: STARTTLS=client, relay=email.mydomain.com, version=TLSv1/SSLv3, verify=FAIL, cipher=ECDHE-RSA-AES256-GCM-SHA384, bits=256/256
Feb 20 11:33:52 mydomain sm-mta[7814]: u1KEXqu0007812: to=<dude1@mydomain.com>, ctladdr=<www-data@mydomain.com> (33/33), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=120599, relay=email.mydomain.com [1xx.xxx.xxx.xxx], dsn=5.1.1, stat=User unknown
Feb 20 11:33:52 mydomain sm-mta[7814]: u1KEXqu0007812: u1KEXqu0007814: DSN: User unknown
Feb 20 11:33:52 mydomain sm-mta[7814]: u1KEXqu0007814: to=<www-data@mydomain.com>, delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=30000, relay=email.mydomain.com [1xx.xxx.xxx.xx], dsn=2.0.0, stat=Sent (Ok: queued as CC8D43A3AA5)






> **SeijiSensei said:**
> On the machine running sendmail, what do you see if you run the command "host -t mx mydomain.com"? Does it point to that server?

Sendmail consults DNS first to decide where to route a message.  You can override the DNS results with a mailertable database, but let's start with DNS first.

I'm assuming there's an account called "dude1" on the server or that it's an alias for some other address.  If not, that's certainly a big problem to start with.

Here's another test you can try.  Connect to the server with the command
```
telnet host.mydomain.com 25
```
where host.mydomain.com is the machine's fully-qualified domain name.  It should be the name referenced in the MX records for mydomain.com.  Then when sendmail replies, try the following dialog
```

ehlo localhost
==> sendmail replies
mail from: you@somewhere.com
==> reply
rcpt to: dude1@mydomain.com
==> What happens here??

```

---

### Post by SeijiSensei on 2016-02-20
So are mail.mydomain.com and email.mydomain.com the same machine or different ones?  Choose one name and use it consistently.  Whatever name you choose needs to be listed in /etc/mail/local-host-names.  If the machine accepts mail as "mydomain.com," "mail.mydomain.com," and "email.mydomain.com" then all three names need to be listed in local-host-names.

---

### Post by 0p3nS0urc3 on 2016-03-04
Ok guys i will try to describe the output

1- here in my worksite we have several public IPs , and we have 4 Machines working as DNS servers with backups included.

2- we use 2 different public IP´s   i will use as an example to decribe the following setence the following IPs :

2.1 - Machine 1  E-mail server "running Postfix+apache2+dovecot+spamasassin and few other stuff"  IP =>  171.10.158.10

2.2 - All the DNS ZONES of this e-mail server IP are pointing in to email.mydomain.com hostname

2.3 - On the Email server i have created the email account  [EMAIL="dude1@mydomain.com"]dude1@mydomain.com[/EMAIL] (this e-mail account is configured on my machine workstation with outlook and working with TLS and SSL and it works great i can forward send and receive e-mails to all kinds of emails servers gmail,outlook,hotmail, etc.etc.etc.

3- Machine 2 Webhost machine were we host several websites IP = > 171.10.158.100 
3.1 - All DNZ Zones with hostnames pointing to hostname=> mydomain.com

3.2 - One of our websites has a Contact form in PHP which uses sendmail.php (so i have installed on this linux machin the sendmail) and i have configured the sendmail contact form.php the recipients e-mail => [EMAIL="dude1@mydomain.com"]dude1@mydomain.com[/EMAIL]  

3.3 on the sendmail.mc conf i have done the following tests:

3.3.1 -> First i used localhost on:
         > 
      define(`MAIL_HUB', `localhost')      define(`LOCAL_RELAY', `localhost')
         

        but ofcourse it doesn´t send anything.... so i tried adding the Machine2 hostname

3.3.2 -  > 
      define(`MAIL_HUB', `mydomain.com')      define(`LOCAL_RELAY', `mydomain.com')
        

       it also doesn´t work obviously because the e-mail server is running on another serverhost so i cannot receive any e-mail on [EMAIL="dude1@mydomain.com"]dude1@mydomain.com[/EMAIL].


3.3.3 - So i have decided to change and use the hostname of the e-mail server

         > 
            define(`MAIL_HUB', `email.mydomain.com')            define(`LOCAL_RELAY', `email.mydomain.com')
           

         This worked to some extend, i can see on  machine2  "171.10.58.100" mail.log the following data beeing sent from www-data@  at this point i can see that its trying to send it to the correct e-mail server IP machine address "171.10.58.10".

Also as a Sidenote "If i input on the contact.php form a different recipient e-mail server like  example [email]dude1@gmail.com[/email] or [email]dude1@hotmail.com[/email] or [email]dude1@anothercompany.com[/email]"
this other recipient e-mails will receive the message from the contact form on there inbox from e-mail www-data@ 
So it uses the ougoing , but cannot receive it on the inbox of the same e-mail server.

> 
Mar  4 09:54:00 mydomain sendmail[9914]: u24Ds0nD009914: from=www-data, size=191, class=0, nrcpts=1, msgid=<201603041354.u24Ds0nD009914@mydomain.com>, relay=www-data@localhost
Mar  4 09:54:00 mydomain sm-mta[9915]: u24Ds0UC009915: from=<www-data@mydomain.com>, size=424, class=0, nrcpts=1, msgid=<201603041354.u24Ds0nD009914@mydomain.com>, proto=ESMTP, daemon=MTA-v4, relay=localhost [127.0.0.1]
Mar  4 09:54:00 mydomain sendmail[9914]: u24Ds0nD009914: to=dude1@mydomain.com, ctladdr=www-data (33/33), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=30191, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (u24Ds0UC009915 Message accepted for delivery)
Mar  4 09:54:00 mydomain sm-mta[9917]: STARTTLS=client, relay=email.mydomain.com, version=TLSv1/SSLv3, verify=FAIL, cipher=ECDHE-RSA-AES256-GCM-SHA384, bits=256/256
Mar  4 09:54:00 mydomain sm-mta[9917]: u24Ds0UC009915: to=<dude1@mydomain.com>, ctladdr=<www-data@mydomain.com> (33/33), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=120424, relay=email.mydomain.com [171.10.58.10], dsn=5.1.1, stat=User unknown
Mar  4 09:54:00 mydomain sm-mta[9917]: u24Ds0UC009915: u24Ds0UC009917: DSN: User unknown
Mar  4 09:54:00 mydomain sm-mta[9917]: u24Ds0UC009917: to=<www-data@mydomain.com>, delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=30000, relay=email.mydomain.com [171.10.58.10], dsn=5.1.1, stat=User unknown
Mar  4 09:54:00 mydomain sm-mta[9917]: u24Ds0UC009917: u24Ds0UD009917: return to sender: User unknown
Mar  4 09:54:00 mydomain sm-mta[9917]: u24Ds0UD009917: to=root, delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=30000, relay=email.mydomain.com [171.10.58.10], dsn=5.1.1, stat=User unknown
Mar  4 09:54:00 mydomain sm-mta[9917]: u24Ds0UC009917: Saved message in /var/lib/sendmail/dead.letter




But still showing up an error user unknown eventually we will get there


4- So i have opened the e-mail server machine1  Var/log / mail.log and i have noticed the following as shown below


> 
Mar  4 09:54:00 email postfix/smtpd[12501]: connect from [www.mydomain.com]("http://www.mydomain.com")[171.10.58.100]
Mar  4 09:54:00 email postfix/smtpd[12501]: NOQUEUE: reject: RCPT from [www.mydomain.com]("http://www.mydomain.com")[171.10.58.100]: 550 5.1.1 <dude1@email.mydomain.com>: Recipient address rejected: User unknown in relay recipient table; from=<www-data@email.mydomain.com> to=<dude1@email.mydomain.com> proto=ESMTP helo=<mydomain.com>
Mar  4 09:54:00 email postfix/smtpd[12501]: NOQUEUE: reject: RCPT from [www.mydomain.com]("http://www.mydomain.com")[171.10.58.100]: 550 5.1.1 <www-data@email.mydomain.com>: Recipient address rejected: User unknown in relay recipient table; from=<> to=<www-data@email.mydomain.com> proto=ESMTP helo=<mydomain.com>
Mar  4 09:54:00 email postfix/smtpd[12501]: NOQUEUE: reject: RCPT from [www.mydomain.com]("http://www.mydomain.com")[171.10.58.100]: 550 5.1.1 <root@email.mydomain.com>: Recipient address rejected: User unknown in relay recipient table; from=<> to=<root@email.mydomain.com> proto=ESMTP helo=<mydomain.com>
Mar  4 09:54:00 email postfix/smtpd[12501]: disconnect from [www.mydomain.com]("http://www.mydomain.com")[171.10.58.100]




Any ideas ?

i have noticed that the incomming e-mail adress for recipients on email server log is showing  [EMAIL="dude1@email.mydomain.com"]dude1@email.mydomain.com[/EMAIL]  but the correct e-mail address registered on the email server is [EMAIL="dude1@mydomain.com"]dude1@mydomain.com[/EMAIL] thats the reason for sure that the contact message from the contact form is not arriving on the correct email inbox assigned.

on the machine2  website server side , if i change the local hub to  mydomain.com   the email server will not receive the emails cause of course they are different public IP´s and different hostnames.

---

### Post by SeijiSensei on 2016-03-04
I don't know how you have a machine with 127.0.0.10 since that address is in the localhost range of 127.0.0.0/8 and not typically routed over networks.

Please show us the contents of local-host-names on email.mydomain.com and the results of

```
ifconfig
```

```
route -n
```

and

```
grep dude1 /etc/passwd
```

on that same machine.

---

### Post by 0p3nS0urc3 on 2016-03-04
> **SeijiSensei said:**
> I don't know how you have a machine with 127.0.0.10 since that address is in the localhost range of 127.0.0.0/8 and not typically routed over networks.

Please show us the contents of local-host-names on email.mydomain.com and the results of

```
ifconfig
```

```
route -n
```

and

```
grep dude1 /etc/passwd
```

on that same machine.






Hi here is the output


ifconfig

> 
eth0      Link encap:Ethernet  address de HW 00:0x:2x:ex:1x:xd
          inet addr.: 171.10.58.10  Bcast:171.10.58.127  Masc:255.255.255.128
         





and  route -n


> 

Routing table IP from Kernel
Destination         Router        MáscGen.    Metric Options Ref   Iface used
0.0.0.0         171.10.58.1 0.0.0.0         UG    0      0        0 eth0
171.10.58.0    0.0.0.0         255.255.255.128 U     0      0        0 eth0







i am lost grep dude1 /etc/passwd ??????  doesnt show anything here




BTW = IP 127.0.0.10  was an example ip on previous post.. as the real IP was obfuscated.

---

### Post by SeijiSensei on 2016-03-04
Then there is no "dude1" account on that machine which is why you get user unknown.

---

### Post by 0p3nS0urc3 on 2016-03-04
> **SeijiSensei said:**
> Then there is no "dude1" account on that machine which is why you get user unknown.


hmmm i am confused

i dont know what u mean with not dude1 account on that machine..

let me repeat the information


Email-server "171.10.58.10"  running ISPconfig+Postfix+dovecot+apache2+spam+squirrelmail thats where e-mail server is hosted via ispconfig (we have over 50 e-mail accounts setup) we can access the machine directly via web with squirrelmail and access the e-mails , also on our workstations we have configured the office outlook to download all emails from the e-mail server using the POP3/SMTP configuration

input mail server: email.mydomain.com
outgoing SMTP: email.mydomain.com

so example dude1 account works perfect and its enabled..

what i am trying to do is having another Machine2 IP  [www.mydomain.com](www.mydomain.com) "which is hosted on a different public IP" to forward the submitted input data to be received by  [email]dude1@mydomain.com[/email] which is enabled on the e-mailserver Machine1 public IP

---

### Post by 0p3nS0urc3 on 2016-03-04
New update

using the webpage machine where contact.php form is installed with sendmail enabled..

i can send the message and receive it on a external e-mail.

here is the log 
> 

Mar  4 23:20:52 mydomain sendmail[2563]: u253Kp8W002563: from=www-data, size=175, class=0, nrcpts=1, msgid=<201603050320.u253Kp8W002563@mydomain.com>, relay=www-data@localhost
Mar  4 23:20:52 mydomain sm-mta[2564]: STARTTLS=server, relay=localhost [127.0.0.1], version=TLSv1/SSLv3, verify=NOT, cipher=DHE-RSA-AES256-GCM-SHA384, bits=256/256
Mar  4 23:20:52 mydomain sendmail[2563]: STARTTLS=client, relay=[127.0.0.1], version=TLSv1/SSLv3, verify=FAIL, cipher=DHE-RSA-AES256-GCM-SHA384, bits=256/256
Mar  4 23:20:52 mydomain sm-mta[2564]: u253KqZe002564: from=<www-data@mydomain.com>, size=408, class=0, nrcpts=1, msgid=<201603050320.u253Kp8W002563@mydomain.com>, proto=ESMTP, daemon=MTA, relay=localhost [127.0.0.1]
Mar  4 23:20:52 mydomain sendmail[2563]: u253Kp8W002563: to=contact@eletronic-web.com, ctladdr=www-data (33/33), delay=00:00:01, xdelay=00:00:00, mailer=relay, pri=30175, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (u253KqZe002564 Message accepted for delivery)
Mar  4 23:20:54 mydomain sm-mta[2566]: STARTTLS=client, relay=eletronicweb-com02e.mail.protection.outlook.com., version=TLSv1/SSLv3, verify=OK, cipher=ECDHE-RSA-AES256-SHA384, bits=256/256
Mar  4 23:20:56 mydomain sm-mta[2566]: u253KqZe002564: to=<contact@eletronic-web.com>, delay=00:00:04, xdelay=00:00:04, mailer=esmtp, p




the issue is only on the other machine e-mail server we have the e-mail account created in the e-mail server is not receiving the contact form message.. and giving the 550 user unknown aldo the log of Postfix shows as if  sendmail from website machine is sending wrong recipients e-mail   [email]dude1@email.mydomain.com[/email]  instead of [email]dude1@mydomain.com[/email] which is the real user account created on the e-mail server running postfix.

---

### Post by SeijiSensei on 2016-03-05
I'm pretty much lost now.  

I was responding to this error you posted above:
> Mar 4 09:54:00 mydomain sm-mta[9917]: u24Ds0UC009915: to=<dude1@mydomain.com>, ctladdr=<www-data@mydomain.com> (33/33), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=120424, relay=email.mydomain.com [171.10.58.10], dsn=5.1.1, stat=User unknown
That indicates there is no user named "dude1" on the machine email.mydomain.com.  However the local-host-names file on that machine must have mydomain.com as one of the entries, otherwise you'd get a different error ("Mail loops back to me").

---

