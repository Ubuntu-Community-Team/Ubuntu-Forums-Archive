---
title: "Gnarwl"
date: 2010-04-07
forum: Server Platforms
---

### Post by bluedrakonis on 2010-04-07
im following this guide 
[http://www.howtoforge.com/postfix-virtual-hosting-with-ldap-backend-and-with-dovecot-as-imap-pop3-server-on-ubuntu-karmic-koala-9.10-p5](http://www.howtoforge.com/postfix-virtual-hosting-with-ldap-backend-and-with-dovecot-as-imap-pop3-server-on-ubuntu-karmic-koala-9.10-p5)

an i do the apt-get install gnarwl but /etc/gnarwl.conf /etc/gnarwl.conf.bck is no where on my server. i even tried to install it again to make sure and it showed that it was already installed any ideas?

---

### Post by ICEB3AR on 2010-04-07
What's the output of 
```

find / -type f -name gnarwl.conf
find / -type f -name gnarwl.conf.bck

```
?

---

### Post by bluedrakonis on 2010-04-07
it says -bash: find/: no such file or directory

---

### Post by KB1JWQ on 2010-04-07
Check your spacing.

---

### Post by bluedrakonis on 2010-04-07
i may have had the spacing off because now it doesnt show anything it just goes to where i can enter another command

---

### Post by kewlrichie on 2010-04-08
I believe the author just mistyped the file name it should be /etc/gnarwl.cfg

btw on page 3 check the dovecot correction on the bottom. I submitted that when I built the older version of this guide for 8.10 and just submitted it again when he made the 9.10 just so people know

---

### Post by bluedrakonis on 2010-04-08
thanks ill give this a try and let you know how it goes

---

### Post by bluedrakonis on 2010-04-08
thanks that got gnarwl took care of now i have to fix the postfix error i get when i try to stop it

 * Stopping Postfix Mail Transport Agent postfix                                postfix: warning: valid_hostname: invalid character 32(decimal): mail.example.tld # ==> change this for your setup.
postfix: fatal: file /etc/postfix/main.cf: parameter myhostname: bad parameter value: mail.example.tld # ==> change this for your setup.
                                                                         [fail]


never mind figured it out

---

### Post by bluedrakonis on 2010-04-08
thanks that got gnarwl took care of now i have to fix the postfix error i get when i try to stop it

 * Stopping Postfix Mail Transport Agent postfix                                postfix: warning: valid_hostname: invalid character 32(decimal): mail.example.tld # ==> change this for your setup.
postfix: fatal: file /etc/postfix/main.cf: parameter myhostname: bad parameter value: mail.example.tld # ==> change this for your setup.
                                                                         [fail]

---

