---
title: "[SOLVED] Problem with SASL authentication in postfix"
date: 2008-06-08
forum: Server Platforms
---

### Post by dash86no on 2008-06-08
Hi,

I'm running a hardy server and am currently trying to set up a web server using a combination of Webmin/Postfix 2.5.1 and the command line when Webmin is too constraining. 

I have pretty much got everything running. I can send internal mail no problem (I.e. from [email]user@mydomain.com[/email] to [email]anotheruser@mydomain.com[/email]). Also, I can receive email from an outside server. (I.e. from [email]me@gmail.com[/email] to [email]user@mydomain.com[/email])

The problem is sending mail out; my ISP blocks port 25 so I am required to go through their relay server. I have gone through the steps outlined in several tutorials out there to accomplish this:

1. Add the following to main.cf

relayhost = stmp.myisp.com
smtp_sasl_auth_enable=yes
smtp_sasl_password_maps=hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options=

2. Create sasl_passwrd file and add:

stmp.myisp.com username:password

3. chown sals_passwrd to root:root 
4. chmod sals_passwrd to rw only
5. use postmap hash to create sals_passwrd.db
6. refresh postfix

After doing this, when I try to send a mail, the mail "sits" in the mail queue for an eternity without changing status.

Interestingly, if I comment out the smtp_sasl_auth lines and try to send mail, then the mail is sent successfully, but it will bounce back with a "530 Need AUTH before MAIL" message.

From this, I believe the error must be with my sasl configuration. I believe something is set up incorrectly and therefore my server is not even trying to send out email when sasl is enabled. However, for the life of me I can't figure out what. 

I would be most grateful if someone could help me out. if you want to see any logs/ outputs etc. just let me know and I'll post them ASAP. 

Cheers

---

### Post by dash86no on 2008-06-08
> **dash86no said:**
> Hi,

I'm running a hardy server and am currently trying to set up a web server using a combination of Webmin/Postfix 2.5.1 and the command line when Webmin is too constraining. 

I have pretty much got everything running. I can send internal mail no problem (I.e. from [email]user@mydomain.com[/email] to [email]anotheruser@mydomain.com[/email]). Also, I can receive email from an outside server. (I.e. from [email]me@gmail.com[/email] to [email]user@mydomain.com[/email])

The problem is sending mail out; my ISP blocks port 25 so I am required to go through their relay server. I have gone through the steps outlined in several tutorials out there to accomplish this:

1. Add the following to main.cf

relayhost = stmp.myisp.com
smtp_sasl_auth_enable=yes
smtp_sasl_password_maps=hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options=

2. Create sasl_passwrd file and add:

stmp.myisp.com username:password

3. chown sals_passwrd to root:root 
4. chmod sals_passwrd to rw only
5. use postmap hash to create sals_passwrd.db
6. refresh postfix

After doing this, when I try to send a mail, the mail "sits" in the mail queue for an eternity without changing status.

Interestingly, if I comment out the smtp_sasl_auth lines and try to send mail, then the mail is sent successfully, but it will bounce back with a "530 Need AUTH before MAIL" message.

From this, I believe the error must be with my sasl configuration. I believe something is set up incorrectly and therefore my server is not even trying to send out email when sasl is enabled. However, for the life of me I can't figure out what. 

I would be most grateful if someone could help me out. if you want to see any logs/ outputs etc. just let me know and I'll post them ASAP. 

Cheers

Guys,


Sorry to have wasted your time. I went and checked the mail log and saw "access denied" messages for sasl_passwd, which of course should have been sasl_passwrd!

I had spelled the file differently in my config file. Stupid error but I'm glad to say I'm finally sending mail!

Cheers

---

