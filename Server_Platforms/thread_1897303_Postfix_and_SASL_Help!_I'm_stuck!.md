---
title: "Postfix and SASL Help! I'm stuck!"
date: 2011-12-19
forum: Server Platforms
---

### Post by TFroehlich3 on 2011-12-19
Alright, so I am following the server guide for Ubuntu. I am at the part where it tells me to

 "sudo /etc/init.d/saslauthd start"

But when I do it tells me that 

  "No run directory defined for saslauthd, not starting"

I got an error on the previous step, but the guide said that was okay, that the file would be created when you ran the script for saslauthd.

 Can someone please help me! Below is the guide I'm following.
[https://help.ubuntu.com/community/Postfix]("https://help.ubuntu.com/community/Postfix")

---

### Post by TFroehlich3 on 2011-12-19
> **TFroehlich3 said:**
> Alright, so I am following the server guide for Ubuntu. I am at the part where it tells me to

 "sudo /etc/init.d/saslauthd start"

But when I do it tells me that 

  "No run directory defined for saslauthd, not starting"

I got an error on the previous step, but the guide said that was okay, that the file would be created when you ran the script for saslauthd.

 Can someone please help me! Below is the guide I'm following.
[https://help.ubuntu.com/community/Postfix]("https://help.ubuntu.com/community/Postfix")





I forgot to mention something. When I test this out, when I do 
    telnet localhost 25
it connects no problem. But when I try
    telnet mail.example.com
it will not connect....

---

### Post by TFroehlich3 on 2011-12-19
**I have not configured my firewall or opened any ports yet. Is that the reason why I can connect when doing:**
 
*telnet localhost 25*
 
**and not** 
 
*telnet mail.example.com 25* 
 
:confused:
 
**Please HELP!**

---

### Post by CharlesA on 2011-12-19
What are you trying to do?

---

### Post by TFroehlich3 on 2011-12-19
> **CharlesA said:**
> What are you trying to do?

I am following an older guide to setup an email server so I can host my own email, rather than paying GoDaddy.com a every month for hosting my email, with limited accounts, and limited storage space. This part of the guide is not working for me and will not connect when I test the connection settings, that is connecting postfix and sasl to communicate with one another. It will let me when command this

*telnet localhost 25* and not when I command *telnet mail.example.com 25*

---

### Post by CharlesA on 2011-12-19
Well the second command is just an example, so it won't work.

Are your sure your ISP isn't blocking port 25?

I relay notifications from my server via gmail using postfix. I wrote a [tutorial]("http://charlesa.net/tutorials/centos/centosgmail.php") up on it using CentOS, but I'm pretty sure the same can be said for Ubuntu.

---

### Post by TFroehlich3 on 2011-12-20
> **CharlesA said:**
> Well the second command is just an example, so it won't work.

Are your sure your ISP isn't blocking port 25?

I relay notifications from my server via gmail using postfix. I wrote a [tutorial]("http://charlesa.net/tutorials/centos/centosgmail.php") up on it using CentOS, but I'm pretty sure the same can be said for Ubuntu.

How can I find out if they are blocking port 25? Is there a program I can run to see? I am living in an apartment and all the rooms are hard wired with wicked fast internet so I am using that, so I'm not sure what ISP they are using....

---

### Post by CharlesA on 2011-12-20
You can forward port 25 and then using something like [http://www.canyouseeme.org/](http://www.canyouseeme.org/) to see if that port is open.

---

