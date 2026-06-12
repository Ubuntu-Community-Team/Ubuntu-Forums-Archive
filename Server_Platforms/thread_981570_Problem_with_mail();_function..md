---
title: "Problem with mail(); function."
date: 2008-11-13
forum: Server Platforms
---

### Post by niiklas on 2008-11-13
i can't get my mail(); function to work. i have installed sendmail packet with:
```

apt-get install sendmail

```

but when i try this test script it just loads endlessly freezing the webserver 'not the computer just the website'

```


<?
mail(
 'niklas@website.se',
 'Someone Sent You Something!!!',
 'nothing.....',
 "From: Niklas <niklas@website.se>"
);
?>


```

php.ini settings:
```

[mail function]
; For Win32 only.
SMTP = localhost
smtp_port = 25

#sendmail_path = /usr/sbin/sendmail
sendmail_path = sendmail -t -i

sendmail_from = webmaster@website.se

```
tested both rows of sendmail_path

---

### Post by niiklas on 2008-11-13
bump

---

### Post by niiklas on 2008-11-13
bump

---

### Post by niiklas on 2008-11-14
buuuuuuuump

---

### Post by niiklas on 2008-11-14
bump :S

---

### Post by arpanaut on 2008-11-14
You might be better served by asking here:

[http://ubuntuforums.org/forumdisplay.php?f=339](http://ubuntuforums.org/forumdisplay.php?f=339)

---

### Post by Idefix82 on 2008-11-14
And everybody else might be better served if you don't bump one thread four times within 12 hours. You are not the only one on these forums who is asking for help. As a rule of thumb, you have to give people at least 24 hours to reply.

---

### Post by drubin on 2008-11-14
> **idefix82 said:**
> and everybody else might be better served if you don't bump one thread four times within 12 hours. You are not the only one on these forums who is asking for help. As a rule of thumb, you have to give people at least 24 hours to reply.

+1

---

### Post by bapoumba on 2008-11-14
Moved to Servers.

---

### Post by CrucifiedEgo on 2008-11-14
Anything interesting in /var/log/mail.log ?

---

### Post by kennedy7 on 2008-12-04
sudo apt-get install postfix. Use it instead of sendmail.

---

