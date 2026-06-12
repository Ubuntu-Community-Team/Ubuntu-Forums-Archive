---
title: "Need help.. Postfix + DoveCot configuration"
date: 2009-04-15
forum: Server Platforms
---

### Post by wsonar on 2009-04-15
I'm New at mail server configuration


using ubuntu server 8.10

I have Configured Postfix and DoveCot and done the basic testing to see they are working

I am confused about system users and virtual users and linkinig them together

from what I have read I think I have to create virtual users and link them to my system users if anybody knows the best and easiest practice for this that would be awesome this has not been an easy task.

I only have 1 system user and a root user I created another user to test also but and tried to use mailx to send test mails but when I am logged in as one of the users and do mail it says no new mail.. but root has mail and appears the only mailbox on the system

---

### Post by wsonar on 2009-04-15
I have tried following these instructions along with others but am still having no luck

[http://wiki.centos.org/HowTos/postfix]("http://wiki.centos.org/HowTos/postfix")

I added an alias for my system user but I keep trying to send myself a message  but when I check it says no new mail

---

### Post by wsonar on 2009-04-15
In var/mail do I need to create directories here for my users

there is only root here

but the instructions show it points to ~/Maildir

I would really like to see this work for a system user

---

### Post by wsonar on 2009-04-15
for sending a new mail message I do

mail username
subject:test
test
.
cc:


is this the correct way to send a message?

---

### Post by wsonar on 2009-04-15
I tried from my yahoo account to send to one of my system users and got this message

Recipient address rejected: User unknown in local recipient table [RCPT_TO]

it did show Received: from and showed the IP of the mail server so it looks like I can send from the internet but it's not recognizing my local system user account

---

### Post by wsonar on 2009-04-15
I have created aliases in the /etc/aliases file but this dosen't seem to work

---

### Post by wsonar on 2009-04-15
I tried this link to setup virtual domains and virtuial users

[https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto]("https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto")

after I try a test mail it dosen't create a directoy in the /home/vmail

---

### Post by wsonar on 2009-04-15
Man this is frustrating

When I try this
-------------------------------------------------------------
Remember that the directory structure for a particular user is create when you send he gets his firs mail.



In a terminal you can type:

mail [email]info@omydomain.org[/email]

Check the mailbox

cd /home/vmail/domain1/info/new
ls
-------------------------------

when I try to cd here under /vmail
ls shows

mydomain.org

when I try to cd to it I get permission denied
if I try sudo and cd it says unknown command



ANY body that could help on this would be awesome

---

### Post by wsonar on 2009-04-15
I tested from my system account and I can do
 
mail [email]account@gmail.com[/email]
subject: test
test

and it instantly went through to my gmail

when I hit reply I noticed it had
@localhost.localdomain after the username

---

### Post by wsonar on 2009-04-15
I have now gone through the instructions here

[https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto]("https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto")

and set up a virtual mailboxes and users

I can log in to the test accounts and test as described
-----------------------

---

### Post by wsonar on 2009-04-15
I opened the firewall port but I think I need to also forward the port on the router so I will try that when I get home

---

### Post by wsonar on 2009-04-15
when I browse to the /vmail/info/new/

there is a message in there a test I created so it does appear to be working

sorry to keep bothering everyone with my updates hopefully the final update will be everything is working

---

### Post by wsonar on 2009-04-15
I got all my MX records added with my easydns account now so things should start rolling soon

---

### Post by mckenna1977 on 2009-04-15
so far i guess you've your mx records set and you can send yourself emails and confirm receipt

using dovecot you should be able to receive emails using pop3 so try using thunderbird or something as a client to confirm

when you set up a user you can send them emails as their mail directory is set up by default - you can add the alias as required in postfix

you can use a catch all address in postfix in virtual domains - i found when doing this that i had to map the other usernames to user inboxes but didn't have to do before this

checking your logs should give you information about any problems you're having - tail /var/log/mail.log

good luck - i'll check back here...

---

### Post by wsonar on 2009-04-15
I can't do anymore testing till I forward pop and imap on the router when I get home

but I still can't figure out why if I send a message from my system account
to my gmail
it shows [email]accont@localhost.locald[/email]omain instead of [email]account@mydomain.org[/email]

I created an allias and a virtual user

---

### Post by wsonar on 2009-04-15
So I setup my virtual account in evolution on a second pc and it works great and fast sending and receiving to my gmail account

my system account still won't work so I need to figure out that then I will also try to add tls for encryption

anybody know what I need to do to get the system account to work?

technically I don't need to get mail to it  but do want to make it work

---

### Post by wsonar on 2009-04-15
so looks like the virtual accounts are working good.

This obviously works fine for my purpose I do need to learn about implementing sql and best security practices, like how a user would change there own password? I do want to try to get the squirlmail going.

the only ports im letting through are 2222, 80, 110, 143 any recomendations for making sure this is secure?

but I'd say that's the end of this thread for the most part thanks for the input...

Lots more reading to do in time.

Hope everybody has a wonderful day

---

### Post by Dy1anW on 2009-04-29
> **wsonar said:**
> Man this is frustrating


Tell me about it!  I worked off [a different how-to](http://johnny.chadda.se/2007/04/15/mail-server-howto-postfix-and-dovecot-with-mysql-and-tlsssl-postgrey-and-dspam/) when I first set up (note that it's also 2 years old), and all I get in the mail.log when receiving from my localdomain is:
```
Apr 30 02:12:30 Server deliver(mail@internal.own): Can't connect to auth server at /var/run/dovecot/auth-master: No such file or directory
```

I'll have to try out your tutorial after some sleep :P

---

