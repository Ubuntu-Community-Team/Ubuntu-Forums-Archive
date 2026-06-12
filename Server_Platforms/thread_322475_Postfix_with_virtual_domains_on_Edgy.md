---
title: "Postfix with virtual domains on Edgy"
date: 2006-12-20
forum: Server Platforms
---

### Post by godlike on 2006-12-20
Hey guys I'm havin a dam annoying time trying to get postfix and dovecot (or courier) to work with virtual hots on edgy. Im not sure if its beacuase the howtos seem to be based on dapper or if its just my own mistake. Anyways any help would be greatly appreciated. 
Basically all I want to do is have an email server with a few virtual domains using mysql or files for the database and tls or even without it if that makes it any easier for some help ](*,)

---

### Post by linuchsan on 2006-12-20
you really have to give use more information for what is going wrong

---

### Post by peanut butter on 2006-12-20
i can confirm that the howto on the wiki dosnt work. even on dapper. I lost 3 hrs trying to figure that out.](*,)

---

### Post by godlike on 2006-12-20
Ya ive tried more then a few of them lol Hopfully somewill will help us out =)

---

### Post by peanut butter on 2006-12-20
this might not be applicable to you but you might try [ebox]("http://www.ebox-platform.org") its a customized debian, i used it after failing miserably at using ubuntu.

---

### Post by godlike on 2006-12-20
Hey well basically I get diffrent problems with every howto lol one i can never log into the mail another just wont send or recieve mail etc... I'll check out that ebox thanks for the tip. Id like to stay with ubuntu becuase its still the best distro in my opinion and usually its easy to find a good walk through or get help. Except so far when it comes to postfix and edgy lol

---

### Post by godlike on 2006-12-20
I checked out ebox... It looks like a pretty cool project. It doesnt look to have a web server by default but im sure you can install one sein its just basically debian. I'll read some more of the faqs for it and I guess if no one can help with postfix on edgy i may switch.

---

### Post by chrisfay on 2006-12-20
> sually its easy to find a good walk through or get help. Except so far when it comes to postfix and edgy

I think you would get better help if you provided more detail about your problem. What howto have you been following? Are you wanting a MySQL backed Postfix virtual setup or flat file based? Do you have a fully functioning Postfix Dovecot/Courier setup before attempting more complicated configurations?

The last question is very important. If you attempt a complicated configuration without a functioning base setup, you're only making it that much more difficult to debug.  You also should realize that a MySQL virtual user setup with SMTP Auth for your clients is not a simple setup. Because of this, its much more difficult to tailor a hundred howtos to every possible setup. You kinda have to know what you're doing and modify the available references to fit your needs. 

That being said, I have a personal reference documentation of how I configured my Postfix, MySQL, Dovecot, SASL and TLS/SSL located on my forum here:

[http://cjfay.com/forums/showthread.php?t=155](http://cjfay.com/forums/showthread.php?t=155)

It is very informal and slightly disorganized, but has the information necessary to successfully complete the setup. It may be a bit confusing, thought it could be a decent place to start and generate questions...

---

### Post by godlike on 2006-12-21
Well my problem is basically i must be a lil slow or somthing lol
every howto ive tried never works lol I waqs hoping someone knew of a complete idiots guide to how to do it lol

---

### Post by godlike on 2006-12-21
Your howto looks pretty good though I'll try it now and let ya know thanx alot

---

### Post by chrisfay on 2006-12-21
What stage are you in the setup? What packages do you have installed? Do you have a basic functioning mail server where you can send and receive mail internally and externally?

In order to direct you to good documentation, or give you ideas on how to go about setting it up, we need more information on where you are in the process....

---

### Post by chrisfay on 2006-12-21
> Your howto looks pretty good though I'll try it now and let ya know thanx alot

Let me know if you have any questions 'when' you get stuck....:p  (i say that due to my convoluted documentation)

---

### Post by godlike on 2006-12-21
Ok I tried your howto i get this error in my logs when trying to send mail


Dec 20 23:01:02 blackheaven dovecot: POP3(godlike@godlike.ca): pop3_uidl_format setting is missing from config file

And this one when i try to check mail

Dec 20 23:03:43 blackheaven postfix/smtpd[14278]: lost connection after AUTH from (yadda.yadda.com)  <--- that was my real address 

Any ideas?

---

### Post by godlike on 2006-12-21
Oh and actually I found that to be the easiest howto yet lol  Was nice and c&p which is good for noobies like me.

Im sure those errors are just somthing I musta forgot to change or somthing lol

---

### Post by godlike on 2006-12-21
Oh and also i just noticed in the mail.warn log i got alot of these

Dec 20 23:12:01 blackheaven postfix/qmgr[14031]: warning: connect to transport smtp-amavis: No such file or directory

---

### Post by chrisfay on 2006-12-21
> Dec 20 23:12:01 blackheaven postfix/qmgr[14031]: warning: connect to transport smtp-amavis: No such file or directory

This is because of the amavisd-new directive in main.cf. I forgot that was something I have on my setup but didn't include in the docs. You would need to remove:

```
####### amavisd decleration  ###########
content_filter=smtp-amavis:[127.0.0.1]:10024
```

...from /etc/postfix/main.cf.This will clear that error. 

To fix:
```
Dec 20 23:01:02 blackheaven dovecot: POP3(godlike@godlike.ca): pop3_uidl_format setting is missing from config file
```
...you need to open up /etc/dovecot/dovecot.conf and scroll down about 60% of the file and look for this directive:
```
pop3_uidl_format =
```

You need to make it look like this:

```
pop3_uidl_format = %08Xu%08Xv
```

Fix those and try again...I'll have to double check on the auth error.

Don't forget to restart both Postfix and Dovecot:

```
sudo /etc/init.d/postfix restart
sudo /etc/init.d/dovecot restart
```

---

### Post by godlike on 2006-12-21
Ok after deleting the amavis lines I'm still gettin this in mail.warn log

Dec 21 00:01:03 blackheaven postfix/qmgr[15037]: warning: connect to transport smtp-amavis: No such file or directo$
Dec 21 00:01:07 blackheaven dovecot: Killed with signal 15

The other log files are gettin no errors when trying to check the accounts but I think thats probablly becuase it looks like dovecot stopped in that above error?


And btw thanx sooo much for your help this has been annoying me for like a month lol

---

### Post by chrisfay on 2006-12-21
Unless for some reason you have an amavisd-new directive somewhere else in your main.cf file, removing what I listed should stop Postfix from referencing that package altogether. 

Can you try sending an email somewhere outside your network and post the resulting logs from /var/log/mail.log?
```

sudo tail /var/log/mail.log
```

or if there's more than 10 lines of relevant info:

```
sudo vi /var/log/mail.log
```

....and post em here.

---

### Post by godlike on 2006-12-21
Dec 21 00:23:01 blackheaven postfix/smtpd[15107]: connect from MYHOSTNAME[MYIP]
Dec 21 00:23:03 blackheaven postfix/qmgr[15037]: warning: connect to transport smtp-amavis: No such file or directory
Dec 21 00:23:09 blackheaven postfix/smtpd[15107]: warning: SASL authentication failure: Password verification failed
Dec 21 00:23:09 blackheaven postfix/smtpd[15107]: warning: MYHOSTNAME[MYIP]: SASL PLAIN authentication failed: authentication failure
Dec 21 00:23:09 blackheaven postfix/smtpd[15107]: warning: MYHOSTNAME[MYIP]: SASL LOGIN authentication failed: authentication failure


Now I was reading somwhere about that plain_auth line yes line in dovecot.conf but that is set to the proper thing so thats the only reason I coulda thought of for that.

Also dont know if this will help but when i try and check mail this is the log for that

Dec 21 00:25:40 blackheaven dovecot: pop3-login: Login: user=<godlike@godlike.ca>, method=PLAIN, rip=24.67.68.141, lip=19    2.168.0.100, TLS
Dec 21 00:25:40 blackheaven dovecot: POP3(godlike@godlike.ca): Disconnected: Logged out top=0/0, retr=0/0, del=0/0, size=    0


Also i did a search for amavis in the postfix conf and just incase the dovecot conf also and nothing comes up so I dont know lol

---

### Post by chrisfay on 2006-12-21
> lso i did a search for amavis in the postfix conf and just incase the dovecot conf also and nothing comes up so I dont know

Before you attempted this, did you have a clean install of your postfix package or where there leftover mods from previous howtos? 

Is there anything pertaining to amavisd in your /etc/postfix/master.cf file from something you did before? If there was, it would probably have something like this:

```
smtp-amavis unix -      -       n       -       4  smtp
    -o smtp_data_done_timeout=1200
    -o smtp_send_xforward_command=yes
    -o disable_dns_lookups=yes
    -o max_use=20

```

If there is, remove that as well...Otherwise, I'm not realy sure why you'd have any reference of amavisd in your postfix config. Maybe try running:

```
sudo /etc/init.d/postfix stop
sudo /etc/init.d/postfix start
```
> 
```
Dec 21 00:23:09 blackheaven postfix/smtpd[15107]: warning: SASL authentication failure: Password verification failed
Dec 21 00:23:09 blackheaven postfix/smtpd[15107]: warning: MYHOSTNAME[MYIP]: SASL PLAIN authentication failed: authentication failure
Dec 21 00:23:09 blackheaven postfix/smtpd[15107]: warning: MYHOSTNAME[MYIP]: SASL LOGIN authentication failed: authentication failure
```

Now I was reading somwhere about that plain_auth line yes line in dovecot.conf but that is set to the proper thing so thats the only reason I coulda thought of for that.

The SASL auth failures are regarding Postfix's attempt to auth with MySQL and allow you to relay through the server. How are you attempting to send the email? Is it using a mail client on the same machine, or another on your same network? 

Also, when you added your user into the MySQL fields, did you add a clear text password in the 'clearpassword' field for SASL auth? This field is used by Postfix to authenticate a client for relaying. If you're sending an email from localhost it should not be an issue though...

Also, I would remove the TLS/SSL stuff in main.cf to eliminate as much unnecessary junk for debugging purposes. You can add them later when you know it works.

---

### Post by godlike on 2006-12-21
Ya it was a fresh install of ubuntu all together so postfix was installed when I apt-get installed from your tutorial. Ill look more for the amavis part..

And At the moment I'm tryin to send it from thunderbird on a windows box in my network. I'll try to send it from the linux box see if that matters.

Ok I just found a couple goofs I missed. in the main.cf I missed a couple parimeters that where relating to your setup so I changed that and it seems to connect good now but it still wont recieve or send mail.

 and im still gettin this in the mail.warn  log

Dec 21 01:10:00 blackheaven postfix/qmgr[15455]: warning: connect to transport smtp-amavis: No such file or directory
Dec 21 01:10:18 blackheaven postfix/qmgr[15595]: warning: connect to transport smtp-amavis: No such file or directory
Dec 21 01:10:25 blackheaven dovecot: Killed with signal 15


Also I have no idea where else i can even look for the amavis refrence lol I checked all the dovecot and postfix files and nothing comes up with a search for amavis. lol

---

### Post by godlike on 2006-12-21
Ok what I think I am going to do is a fresh install rite now then try again and see if it works then. Although I havent done any postfix stuff on this install I have set up my apache and a few other things so maybe thats where the amavis crap is comming from. Either way it will make it easier to trouble shoot if its fresh. So I'll try back here in a lil bit and let ya know ;)

---

### Post by godlike on 2006-12-21
Well ok I did a clean install and went threw your howto again and I'm still getting errors

here are the logs

tail /var/log/mail.log
Dec 21 03:16:22 blackheaven postfix/smtpd[8023]: CB76BB4058: client=shawcable.net[24.24.24.24]
Dec 21 03:16:22 blackheaven postfix/cleanup[8028]: CB76BB4058: message-id=<458A6CDB.4050103@shaw.ca>
Dec 21 03:16:22 blackheaven postfix/qmgr[7923]: CB76BB4058: from=<martind73@shaw.ca>, size=1317, nrcpt=1 (queue active)
Dec 21 03:16:22 blackheaven postfix/smtpd[8023]: disconnect from shawcable.net[24.24.24.24]
Dec 21 03:19:42 blackheaven postfix/anvil[7988]: statistics: max connection rate 1/60s for (smtp:24.24.24.24) at Dec 21 03:15:11
Dec 21 03:19:42 blackheaven postfix/anvil[7988]: statistics: max connection count 1 for (smtp:24.24.24.24) at Dec 21 03:15:11
Dec 21 03:19:42 blackheaven postfix/anvil[7988]: statistics: max cache size 1 at Dec 21 03:15:11
Dec 21 03:21:46 blackheaven dovecot: pop3-login: Login: user=<user@domain.ca>, method=PLAIN, rip=24.24.24.24, lip=192.168.0.100, TLS
Dec 21 03:21:46 blackheaven dovecot: POP3(user@domain.ca): Disconnected: Logged out top=0/0, retr=0/0, del=0/0, size=0




tail /var/log/mail.err
Dec 21 03:14:17 blackheaven dovecot: stat(/home/vmail/godlike.ca/godlike) failed: No such file or directory





tail /var/log/mail.warn
Dec 21 03:15:11 blackheaven postfix/smtpd[7985]: warning: TLS library problem: 7985:error:140DC002:SSL routines:SSL_CTX_use_certificate_chain_file:system lib:ssl_rsa.c:720:
Dec 21 03:15:16 blackheaven postfix/smtpd[7985]: warning: SASL authentication failure: Password verification failed
Dec 21 03:15:16 blackheaven postfix/smtpd[7985]: warning: shawcable.net[24.24.24.24]: SASL PLAIN authentication failed: authentication failure
Dec 21 03:15:16 blackheaven postfix/smtpd[7985]: warning: shawcable.net[24.24.24.24]: SASL LOGIN authentication failed: authentication failure
Dec 21 03:15:22 blackheaven postfix/master[7918]: warning: process /usr/lib/postfix/smtpd pid 7985 killed by signal 11
Dec 21 03:15:22 blackheaven postfix/master[7918]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Dec 21 03:16:22 blackheaven postfix/smtpd[8023]: warning: cannot get certificate from file /etc/dovecot/ssl/host.cert
Dec 21 03:16:22 blackheaven postfix/smtpd[8023]: warning: TLS library problem: 8023:error:02001002:system library:fopen:No such file or directory:bss_file.c:352:fopen('/etc/dovecot/ssl/host.cert','r'):
Dec 21 03:16:22 blackheaven postfix/smtpd[8023]: warning: TLS library problem: 8023:error:20074002:BIO routines:FILE_CTRL:system lib:bss_file.c:354:
Dec 21 03:16:22 blackheaven postfix/smtpd[8023]: warning: TLS library problem: 8023:error:140DC002:SSL routines:SSL_CTX_use_certificate_chain_file:system lib:ssl_rsa.c:720:


Now those are with trying to check mail and for trying to send mail

---

### Post by chrisfay on 2006-12-21
Some of the errors where from TLS/SSL. Like I said, don't mess with that stuff until you have everything working. There's no point. 

Remove from main.cf:
```
smtpd_tls_key_file = /etc/dovecot/ssl/host.key
smtpd_tls_cert_file = /etc/dovecot/ssl/host.cert
smtpd_use_tls=yes
```

Also, when you re-installed Postfix, did you configure it so it could send and receive email before attempting anything in my docs? If you have base level errors in your configuration, trying to add in MySQL and SASL will only make it a ton harder to debug. I would highly recommend getting Postfix and Dovecot working using system user accounts before going virtual.

After you have that completed, then do one thing at a time. Start with Dovecot and get it authenticating using your MySQL tables to send and receive. The tables and how they are made are listed in my docs. Once you make the tables, add in the queries I have listed for dovecot.conf. Once that works, move on to Postfix.

Start adding in one postfix option at a time. Test the Postfix virtual domain table, and make sure your domains work via MySQL. Once they do, then start limiting your relaying via SMTP Auth using the listed MySQL tables. Since it seams you are having issues with this part, I would suggest removing the following from your main.cf:

```
####### SMTPD sasl for authenticating clients for relaying mail through my server (without manually adding ips) ######
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = $myhostname
smtpd_sasl_application_name = smtpd
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = 
permit_sasl_authenticated, 
permit_mynetworks, 
reject_unauth_destination
```

Make sure everything works before adding that back in. You might have an open relay until you do, so make sure and either add this back in, or limit relaying using the default directives once finished.

Also, I'm not sure how much you copied from my main.cf but make sure you didn't copy this:
```
####### SMTP sasl for authenticating and relaying through Comcasts servers ###########
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options=
```
...as its specific to my system.

My point here is, the only way to get through setting this up is to chip away at it. If you do it all at once, it makes it much more difficult to debug each step. Doing it one thing at a time will help you make immediate changes, get that step working, then move on to the next. Its much more efficient that way.

---

### Post by godlike on 2006-12-21
Hey ok thanx alot for your help man. I finally found a howto that worked at [http://www.urbanpuddle.com/articles/2006/12/20/setup-a-postfix-mail-server-on-ubuntu-edgy-eft](http://www.urbanpuddle.com/articles/2006/12/20/setup-a-postfix-mail-server-on-ubuntu-edgy-eft)

It uses courier instead of dovecot but I think that can be changed easy enuff plus for now it works so good enough for me lol

I do appreciate the time ya spent to help me though. Your howto taught me alot about gettin it all working.

---

### Post by chrisfay on 2006-12-21
Glad to hear it! :D

---

