---
title: "postfix amavisnew fatal error main.cf"
date: 2008-03-31
forum: Server Platforms
---

### Post by bytemind on 2008-03-31
Hi,

According to [https://help.ubuntu.com/community/PostfixAmavisNew](https://help.ubuntu.com/community/PostfixAmavisNew)

Postfix integration
For postfix integration, you only need to edit /etc/postfix/main.cf and add the following line: 

sudo postconf -e "content_filter = smtp-amavis:[127.0.0.1]:10024"

but that gives me an fatal error when i try to reload postix

 * Reloading Postfix onfiguration...
postfix: fatal: /etc/postfix/main.cf, line 39: missing '=' after attribute name: "sudo postconf -e "content_filter = smtp-amavis:[127.0.0.1]:10024""

---

### Post by Mr. C. on 2008-04-01
Remove the spaces before and after the = character.

---

### Post by bytemind on 2008-04-01
The line is now

sudo postconf -e "content_filter=smtp-amavis:[127.0.0.1]:10024"

same error

---

### Post by Mr. C. on 2008-04-01
That command works just fine for me:

```
$ sudo postconf -e "content_filter=smtp-amavis:[127.0.0.1]:10024"
$ grep content_filter /etc/postfix/main.cf
content_filter = smtp-amavis:[127.0.0.1]:10024
```

Just edit the /etc/postfix/main.cf file manually:

```
sudo vi /etc/postfix/main.cf
```

---

### Post by UJukkis on 2008-06-19
I have also same problem.  Everything should be OK, but this same stupid error occur all the time.

gytemind: Have you still that problem.

this is my file.

<------cut----
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
sudo postconf -e "content_filter=smtp-amavis:[127.0.0.1]:10024"
-----cut------>

And this is main error message.

<-----cut------
sendmail: fatal: /etc/postfix/main.cf, line 55: missing '=' after attribute name: "sudo postconf -e"content_filter=smtp-amavis:[127.0.0.1]:10024""
-----cut------>

---

### Post by Mr. C. on 2008-06-19
Why does your main.cf file contain the "sudo" command!

sudo postconf -e "content_filter=smtp-amavis:[127.0.0.1]:10024"

Edit this line manually - and make it look like:

content_filter=smtp-amavis:[127.0.0.1]:10024

---

### Post by UJukkis on 2008-06-21
The following line seams to be / work OK, is it OK?

    content_filter = amavis:[127.0.0.1]:10024

Why sudo, because of instractions at:
[https://help.ubuntu.com/community/PostfixAmavisNew](https://help.ubuntu.com/community/PostfixAmavisNew)


**Chapter: Postfix integration**

For postfix integration, you only need to edit /etc/postfix/main.cf and add the following line:

sudo postconf -e "content_filter = smtp-amavis:[127.0.0.1]:10024"

but but is that earlier line OK?  No error messages anymore!

---

### Post by Mr. C. on 2008-06-21
> **UJukkis said:**
> The following line seams to be / work OK, is it OK?

    content_filter = amavis:[127.0.0.1]:10024


Yes, this is correct.

> **UJukkis said:**
> 
Why sudo, because of instractions at:
[https://help.ubuntu.com/community/PostfixAmavisNew](https://help.ubuntu.com/community/PostfixAmavisNew)

**Chapter: Postfix integration**

For postfix integration, you only need to edit /etc/postfix/main.cf and add the following line:

**sudo postconf -e "content_filter = smtp-amavis:[127.0.0.1]:10024"**

but but is that earlier line OK?  No error messages anymore!
That line in the instructions, as a cookbook, is incorrect.  Only the **content_filter= ...** part should be added, and **sudo postconf -e** is the command that accomplishes that.

It is important that you gain a sense of some understanding of what you are doing, and not blindly follow various HowTo instructions.

I'll see if I can correct the article.

---

### Post by Mr. C. on 2008-06-21
The article has been corrected. Please take a look to see if it is clearer to you.

---

