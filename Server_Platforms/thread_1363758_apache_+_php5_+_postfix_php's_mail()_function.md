---
title: "apache + php5 + postfix: php's mail() function"
date: 2009-12-24
forum: Server Platforms
---

### Post by kylegio on 2009-12-24
hello, having trouble setting up php's mail() function. i have googled this extensively and have found contradicting answers, or people just start giving examples of something else.

background:
php5, apache2, postfix as my mail server. 

now the relevant code from my php.ini file
```
[mail function]
; For Win32 only.
SMTP = localhost
smtp_port = 25

; For Win32 only.
;sendmail_from = me@example.com

; For Unix only.  You may supply arguments as well (default: "sendmail -t -i").
;sendmail_path =
sendmail_path = /usr/sbin/postfix -t -i

; Force the addition of the specified parameters to be passed as extra parameters
; to the sendmail binary. These parameters will always replace the value of
; the 5th parameter to mail(), even in safe mode.
;mail.force_extra_parameters =


```


i think the sendmail_path part is what i need to know how to set? can anyone be clear about what should be the sendmail_path ?


thanks 
kyle

---

