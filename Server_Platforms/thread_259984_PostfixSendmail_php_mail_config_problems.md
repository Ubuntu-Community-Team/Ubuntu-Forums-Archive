---
title: "Postfix/Sendmail php mail config problems"
date: 2006-09-18
forum: Server Platforms
---

### Post by k_smolka on 2006-09-18
Hi All

I have been trying to get my php mail function to work in a simple php script .

I have installed postfix and sendmail using apt-get and have altered my php.ini file to set the sendmail path to the following combinations. 

> [mail function]
; For Win32 only.
;SMTP = localhost
;smtp_port = 25

; For Win32 only.

sendmail_from = [email]me@example.com[/email]

; For Unix only.  You may supply arguments as well (default: "sendmail -t -i").
;sendmail_path = "/usr/sbin/sendmail -t -i" 

and I have also tried usr/sbin/postifx and with the -t -i options.

In my mail log i am getting the following error messages:

Sep 18 10:55:46 localhost postfix/sendmail[8431]: fatal: Recipient addresses must be specified on the command line or via the -t option

Any help would be most appreciated.

---

### Post by chrisfay on 2006-09-18
You have the php.ini file wrong. It should be:

```
[mail function]
; For Win32 only.
;SMTP = localhost
;smtp_port = 25

; For Win32 only.

;sendmail_from = me@example.com

; For Unix only. You may supply arguments as well (default: "sendmail -t -i").
sendmail_path = /usr/sbin/sendmail -t -i
```

You needed to uncomment the section for 'sendmail_path' and comment out the 'sendmail_from' option. (only for Win machines as it says). Regardless of what MTA you use, you need to use the sendmail_path = /usr/sbin/sendmail directive.

---

### Post by k_smolka on 2006-09-18
Thanks for you help,

My php.ini files now reads

> 
[mail function]
; For Win32 only.
;SMTP = localhost
;smtp_port = 25

; For Win32 only.
;sendmail_from = [email]me@example.com[/email]

; For Unix only.  You may supply arguments as well (default: "sendmail -t -i").
sendmail_path = /usr/sbin/postfix -t -i 



I am still recieving error messages when trying to send email using postfix,

I can start postfix ok using

sudo /etc/init.d/postfix start

when i go to send an email i get the following error messages in my log file. Looks like some sort of a permissions issue and after googling i cant seeem to find an answer:

> 
Sep 18 14:13:08 localhost postfix[13725]: error: to submit mail, use the Postfix sendmail command
Sep 18 14:13:08 localhost postfix[13725]: fatal: the postfix command is reserved for the superuser
Sep 18 14:19:20 localhost postfix/master[14031]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 18 14:19:21 localhost postfix/pickup[14034]: warning: 64782F40E9: message has been queued for 1 days
Sep 18 14:19:21 localhost postfix/pickup[14034]: 64782F40E9: uid=0 from=<root>
Sep 18 14:19:21 localhost postfix/cleanup[14036]: 64782F40E9: message-id=<20060918131921.64782F40E9@localhost>
Sep 18 14:19:21 localhost postfix/qmgr[14035]: 64782F40E9: from=<root@localhost>, size=538, nrcpt=1 (queue active)
Sep 18 14:19:22 localhost postfix/local[14038]: 64782F40E9: to=<karl@localhost>, orig_to=<root>, relay=local, delay=95870, status=sent (delivered to command: procmail -a "$EXTENSION")
Sep 18 14:19:22 localhost postfix/qmgr[14035]: 64782F40E9: removed
Sep 18 14:19:29 localhost postfix[14043]: error: to submit mail, use the Postfix sendmail command
Sep 18 14:19:29 localhost postfix[14043]: fatal: the postfix command is reserved for the superuser

Thanks in advance.

Karl

---

### Post by chrisfay on 2006-09-18
> fatal: the postfix command is reserved for the superuser

You need to restart apache. Php is still trying to use the previous command you entered: 'sendmail_path = postfix' which was wrong.


```
sudo apache2ctl restart
```

or

```
sudo /etc/init.d/apache2 restart
```

---

