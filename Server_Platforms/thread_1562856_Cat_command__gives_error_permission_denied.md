---
title: "Cat command  gives error permission denied"
date: 2010-08-28
forum: Server Platforms
---

### Post by xtrmsound on 2010-08-28
Hi


I am kinda new to Linux, I am trying to achieve some goals and learn more about Linux.

I am using Ubuntu server edition 10.04.1 running in Vmware server 2.02.

I am connect via Putty so I can use copy and paste.

My first goal is configuring a ftp server using PureFtpd using this [guide]("http://www.ivankristianto.com/os/ubuntu/howto-install-ftp-server-with-user-management-in-ubuntu/1181/").
I want to secure it as much as I can so this is way I chose this guide.



In section 10 I need to write this command 
[COLOR=#c20cb9]**cat**[/COLOR] [COLOR=#000000]**/**[/COLOR]dev[COLOR=#000000]**/**[/COLOR]null [COLOR=#000000]**>**[/COLOR] [COLOR=#000000]**/**[/COLOR]etc[COLOR=#000000]**/**[/COLOR]pure-ftpd[COLOR=#000000]**/**[/COLOR]db[COLOR=#000000]**/**[/COLOR]mysql.conf

I am getting this error

almog@Testing:~$ sudo cat /dev/null > /etc/pure-ftpd/db/mysql.conf
-bash: /etc/pure-ftpd/db/mysql.conf: Permission denied

I tried with and without "sudo" and I am getting the same error.

Why and how can I fix it?

Thanks

---

### Post by Ryan Dwyer on 2010-08-28
Doesn't work for me either.

It looks like they're trying to get you to create an empty file. This should have the same effect:
sudo rm /etc/pure-ftpd/db/mysql.conf # delete it if it already exists
sudo touch /etc/pure-ftpd/db/mysql.conf # create it

---

### Post by TwoEars on 2010-08-28
Yeah, if you want to do it the way they've telling you(I don't know why you would, but whatever), you're going to want to use ```
cat /dev/null | sudo tee /etc/pure-ftpd/db/mysql.conf
```

The problem you had is that ">" isn't given root privileges if you use sudo.

---

### Post by BkkBonanza on 2010-08-28
> **xtrmsound said:**
> Hi
In section 10 I need to write this command 
[COLOR=#c20cb9]**cat**[/COLOR] [COLOR=#000000]**/**[/COLOR]dev[COLOR=#000000]**/**[/COLOR]null [COLOR=#000000]**>**[/COLOR] [COLOR=#000000]**/**[/COLOR]etc[COLOR=#000000]**/**[/COLOR]pure-ftpd[COLOR=#000000]**/**[/COLOR]db[COLOR=#000000]**/**[/COLOR]mysql.conf


As long as you know that cmd wipes out the mysql.conf file. 
You could also just remove the file and touch a new one. 
eg. rm mysql.conf; touch mysql.conf

The tutorial sounds like it's for Red Hat as they don't use sudo by default as in Ubuntu. You may find yourself repeatedly having problems with non root. It may be easier to **sudo su**, do the tutorial, and then **exit** back out.

---

