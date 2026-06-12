---
title: "Creating New Email/Mailbox on Server"
date: 2009-06-08
forum: Server Platforms
---

### Post by redbrad0 on 2009-06-08
[FONT=Arial][SIZE=2]I was given the following steps to create a new email address but it doesn't seem to be working. When I try and send email from the same domain I get the error "[/SIZE][/FONT]  [SIZE=2][FONT=Arial][FONT=Consolas]Recipient address rejected: User unknown in virtual mailbox table[/FONT]  " so I am guessing it hasn't loaded the new user or something. Do I have to run something after I change the vmailusers and vmailbox?

How to add a new email address:
1) Connect to server
2) Run "nano -w /etc/postfix/vmailusers"
3) copy a existing line changing the variables
4) save changes
5) Run "nano -w /etc/postfix/vmailbox"
[/FONT]
[/SIZE]

---

### Post by boyguapo on 2009-06-09
how to add it again, do you have sa sample file to copy in may box.

---

### Post by LepeKaname on 2009-06-09
If you want, you can give it a try to my script:

[http://www.alepe.com/about_computers/about_linux/setting_up_a_mail_server_in_ubuntu.html](http://www.alepe.com/about_computers/about_linux/setting_up_a_mail_server_in_ubuntu.html)

You can try it first in vmware, that way you will see if that is what you want.

It setup postfix/dovecot/spamassasin/clamav (in about 5 mins) with an hybrid setup to support virtual domains. 

If you try it, let me know.

---

### Post by boyguapo on 2009-06-10
> **LepeKaname said:**
> If you want, you can give it a try to my script:

[http://www.alepe.com/about_computers/about_linux/setting_up_a_mail_server_in_ubuntu.html](http://www.alepe.com/about_computers/about_linux/setting_up_a_mail_server_in_ubuntu.html)

You can try it first in vmware, that way you will see if that is what you want.

It setup postfix/dovecot/spamassasin/clamav (in about 5 mins) with an hybrid setup to support virtual domains. 

If you try it, let me know.

ok thanks, i will try...

---

