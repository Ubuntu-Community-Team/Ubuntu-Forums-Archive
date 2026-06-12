---
title: "Postfix as my SMTP Server"
date: 2010-09-22
forum: Server Platforms
---

### Post by karthick87 on 2010-09-22
I have installed postfix in my ubuntu.How can i use this  local SMTP server for the PHP mail() function which allows me to  quickly  send emails via  PHP function.

---

### Post by karthick87 on 2010-09-23
I  have  sucessfully  installed  postfix...

```
karthick@Ubuntu-desktop:~$ sudo /etc/init.d/postfix status
 * postfix is running
karthick@Ubuntu-desktop:~$ sudo /etc/init.d/postfix restart
 * Stopping Postfix Mail Transport Agent postfix                         [ OK ] 
 * Starting Postfix Mail Transport Agent postfix                         [ OK ] 
karthick@Ubuntu-desktop:~$ sudo /etc/init.d/postfix stop
 * Stopping Postfix Mail Transport Agent postfix                         [ OK ] 
karthick@Ubuntu-desktop:~$ sudo /etc/init.d/postfix status
 * postfix is not running
karthick@Ubuntu-desktop:~$ sudo /etc/init.d/postfix start
 * Starting Postfix Mail Transport Agent postfix                         [ OK ] 
```

What  next..?Someone guide me..

---

### Post by karthick87 on 2010-09-26
Bump..

---

### Post by dcstar on 2010-09-26
> **getyourkarthick said:**
> Bump..

Stop continually being a help vampire and do a simple web search for the hundreds of posts already out there for setting up and using Postfix.

You continually beg for simple help with whatever package that you decide to use - as anyone who examines your posts in this forum can clearly see.

---

### Post by lisati on 2010-09-26
Moved to "Server Platforms"

Recommended reading: [https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

---

### Post by karthick87 on 2010-09-26
> **dcstar said:**
> Stop continually being a help vampire and do a simple web search for the hundreds of posts already out there for setting up and using Postfix.

You continually beg for simple help with whatever package that you decide to use - as anyone who examines your posts in this forum can clearly see.

Stop using unnecessary words,i have been searched in google i couln't get the relevant answer.Thats why i posted here.If you cant answer just keep quiet let others help me.

---

### Post by karthick87 on 2010-09-26
> **lisati said:**
> Moved to "Server Platforms"

Recommended reading: [https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)


Thanks a lot :)

---

