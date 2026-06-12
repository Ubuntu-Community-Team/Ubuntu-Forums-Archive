---
title: "Run script on received emails using Postfix / Courier / MySQL"
date: 2009-08-02
forum: Server Platforms
---

### Post by drake22 on 2009-08-02
Hello everyone! I have Postfix set up with an Ubuntu 9.04 installation. I used the tutorial here: [http://flurdy.com/docs/postfix/]("http://flurdy.com/docs/postfix/") I can send e-mails to my server just fine. What I want to do is run a script when an e-mail is received and, ideally, pass that e-mail into the script.

I wrote a script to write the date to /etc/public (a directory I made that has 777 permissions) and saved that script to /usr/local/sbin/email_script.sh I have tried editting /etc/aliases, /etc/postfix/master.cf, aliases table in mysql, and .forward to point to that script. None of that worked. I know the script works (I can run it manually and it writes the date just fine) and the permissions should be such that any user should be able to run the script and write to /etc/public. I am using virtual users and domains in Postfix. Please help! Thank you.

---

### Post by LepeKaname on 2009-08-02
You just need to add a line like this in your /etc/aliases:

```
myuser: myuser, "|/home/myuser/scripts/sender.sh"
```

This would be the code inside sender.sh:

```

#!/bin/sh
read MSG
echo "$MSG" >> /tmp/mailed.log
FROM=$(echo "$MSG" | cut -d " " -f 2)
exec wget -q --spider http://localhost/test.php?m=$FROM

```

---

### Post by drake22 on 2009-08-02
I just tried that and no luck :confused: That was the same as what I tried earlier except that there was the "myuser, " in your version. I assume that is to make sure the mail passes through to the myuser mailbox. I am thinking this has something to do with the fact that I am not using the Ubuntu operating system's users to authenticate for email. I am using a MySQL database instead, in which case are those aliases in /etc/alias being ignored?

If anyone wants to help, I would be glad to post any config files or database tables that you need to see. I am completely lost and I have been working on this all day.

---

### Post by LepeKaname on 2009-08-02
Yes, it may be related to that. I don't use mysql setting as I don't wanted to stress my DB when my OS can handle pretty well... Sorry I can't help more.

---

### Post by drake22 on 2009-08-02
No worries, I am not particularly attached to using MySQL, but that was the best guide I could find in general. Is it simple to configure to use the normal Ubuntu accounts instead?

---

### Post by LepeKaname on 2009-08-03
Depending on your needs. With mysql it is very easy to add/remove accounts using web browser interface. If that is what you need/want, then I guess its ok. As I don't need those interfaces, a simple script do all the job for me, for example:

```
ManageDomains somehost.com            (will add a new domain) 
ManageDomains -r somehost.com         (will remove a domain and its users)
ManageUsers user@somehost.com         (will add a user)
ManageUsers -r user@somehost.com      (will remove a user)
ManageUsers -u user@somehost.com newpassword (to update)
```
and so on (some other options can be used as well)...

I use these scripts everyday to manage all the email accounts in 4 mail servers.

I also made an installation script which can take less than 5 minutes to setup "Postfix + Dovecot + ClamAV + Spamassasin with SASL + TLS" with a hybrid setup to support virtual alias domains. The above scripts depend on the installation script, so they can not be used separately.

If you are interested, I recommend you to try it first in a virtual environment. You can get the last version at [my blog]("http://www.alepe.com/about_computers/about_linux/setting_up_a_mail_server_in_ubuntu.html").

Almost everything is explained inside the script and during the installation.

If you try it, please give me feedback so I can improved, which will help to other people as well.

Have a nice day

---

### Post by piju on 2010-03-14
how about run a script on received emails using postfix and dovecot ? 

i read a lot of tutorials, i seems that using qmail is easy to run a script after user received an email. but installing qmail is hard on ubuntu.

anyone can help me on this ?

---

