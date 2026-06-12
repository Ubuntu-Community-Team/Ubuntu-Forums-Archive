---
title: "Postfix - deny fake header ?"
date: 2008-05-09
forum: Server Platforms
---

### Post by Phulerock on 2008-05-09
I have a question about secure postfix.

I don't want my local user use their username to send email with fake header. ex: 
domain: test.com
user: Phu (Linux system user)

I want user Phu can only send mail with header is [email]phu@test.com[/email], he can't sent email with any fake header, if it happens, system will log it.

Anyone help ?

---

### Post by MJN on 2008-05-09
I've not done this myself so cannot guide through the process, however you need to look at the [reject-authenticated_sender_login_mismatch]("http://www.postfix.org/postconf.5.html#reject_authenticated_sender_login_mismatch") directive within smtpd_sender_restrictions. This will enable [reject_sender_login_mismatch]("http://www.postfix.org/postconf.5.html#reject_authenticated_sender_login_mismatch") to do exactly what you want to do. Of course you need to force clients to authenticate to send mail if they're not already doing so.
 
Hopefully that will give you a starting point.
 
Mathew

---

### Post by Phulerock on 2008-05-15
I had add these line to main.cf:
smtpd_sender_restrictions = reject_sender_login_mismatch

the result is my mail-client can't send any email although I use right username that map with header (user phulerock, mail address: [email]phulerock@test.com[/email])
error message from evolution: [email]phulerock@test.com[/email], sender address is rejected, this not owned by user Phulerock
screenshot here: [http://picasaweb.google.co.uk/phulerock/PhuLeRock/photo?authkey=sbiBh-Po_jA#5200640307794157506](http://picasaweb.google.co.uk/phulerock/PhuLeRock/photo?authkey=sbiBh-Po_jA#5200640307794157506)
error message from server /var/log/mail.log: 
```
May  8 04:20:56 mail postfix/smtpd[4340]: connect from unknown[192.168.195.1]
May  8 04:20:56 mail postfix/smtpd[4340]: setting up TLS connection from unknown[192.168.195.1]
May  8 04:20:56 mail postfix/smtpd[4340]: Anonymous TLS connection established from unknown[192.168.195.1]: TLSv1 with cipher DHE-RSA-AES256-SHA (256/256 bits)
May  8 04:21:30 mail postfix/smtpd[4340]: NOQUEUE: reject: RCPT from unknown[192.168.195.1]: 553 5.7.1 <phulerock@test.com>: Sender address rejected: not owned by user phulerock; from=<phulerock@test.com> to=<phulerock@gmail.com> proto=ESMTP helo=<[192.168.195.1]>
May  8 04:21:30 mail postfix/smtpd[4340]: disconnect from unknown[192.168.195.1]

```
[IMG]http://picasaweb.google.co.uk/phulerock/PhuLeRock/photo?authkey=sbiBh-Po_jA#5200640307794157506[/IMG]

Read on postfix manual, this option may be used with option "smtpd_sender_login_maps", but i'm still not how to config it properly !! :(

anyone help me ? 

ps: My system configure via [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

---

### Post by MJN on 2008-05-15
You need to tell Postfix who owns what e-mail address.

For example, create a file called **senderloginmaps** in /etc/postfix/ and configure it along the following lines:

```

phulerock@test.com phulerock
john@test.com john
sales john
@test2.com mike,steve

```(see [here]("http://www.postfix.org/postconf.5.html#smtpd_sender_login_maps") for further details)

..then create a database out of that that Postfix can use with **sudo postmap senderloginmaps** and finally reference the map in Postfix with the directive **smtpd_sender_login_maps = hash:/etc/postfix/senderloginmaps**

(Note that the hash: reference will assume the .db extension which postmap will have created for you)

Mathew

---

### Post by Phulerock on 2008-05-15
Thanks so much for your support ! yeahhh !
i do :
```
touch senderloginmaps
echo "phulerock@test.com phulerock" >> senderloginmaps
echo "root@test.com root" >> senderloginmaps
sudo postmap senderloginmaps
```
in main.cf:
```
smtpd_sender_restrictions = reject_sender_login_mismatch
smtpd_sender_login_maps = hash:/etc/postfix/senderloginmaps

```
issue:
```
sudo /etc/init.d/postfix restart
```

everything work well :guitar:

Thanks MJN

---

### Post by MJN on 2008-05-16
You're welcome - glad you got it working!

---

