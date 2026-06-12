---
title: "Need Guide In Hosting on Ubuntu"
date: 2009-09-09
forum: Server Platforms
---

### Post by jk.cheng on 2009-09-09
I am having 2 set of server on hand now... the purpose of the server is to do hosting... 

Therefore, i will having Services such as below to run the hosting purpose:

[LIST]
[*]DNS
[*]Apache
[LIST]
[*]PHP
[*]Ruby On Rails
[*]Python
[/LIST]
[*]Postfix
[*]MySQL
[/LIST]
**Here is the question;**
Can i do DNS with Server1 as master and Server2 as Slave, at the sametime do clustering for Apache, also Postfix, and MySQL preform both replication and clustering?

I am new and wanting to try to setting up Hosting Server. It Would be nice if i can get some guide here...

Beside that, can i hv more server running to support those services in state of just 2 server... example;

[LIST]
[*]2 DNS Server (ns1 & ns2)
[*]2 Web Server (cluster_host_1 & cluster_host_2)
[*]2 MySQL Server (master & slave)
[*]2 Mail Server (master & slave)
[/LIST]
How can i work around to links it under ISPConfig & CPanel?

---

### Post by ainsworth_t on 2009-09-09
This guide does a really good job of explaining how to get Ubuntu services up and running under ISPconfig: [http://www.howtoforge.org/perfect-server-ubuntu-9.04-ispconfig-2](http://www.howtoforge.org/perfect-server-ubuntu-9.04-ispconfig-2)

Also check out the Official Ubuntu Server Guide: [https://help.ubuntu.com/9.04/serverguide/C/index.html](https://help.ubuntu.com/9.04/serverguide/C/index.html)

and the Servers Community Documentation: [https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)

---

### Post by jk.cheng on 2009-09-09
> **ainsworth_t said:**
> This guide does a really good job of explaining how to get Ubuntu services up and running under ISPconfig: [http://www.howtoforge.org/perfect-server-ubuntu-9.04-ispconfig-2](http://www.howtoforge.org/perfect-server-ubuntu-9.04-ispconfig-2)

Also check out the Official Ubuntu Server Guide: [https://help.ubuntu.com/9.04/serverguide/C/index.html](https://help.ubuntu.com/9.04/serverguide/C/index.html)

and the Servers Community Documentation: [https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)
thanks for the info... i am looking into it now...

---

### Post by Cardale on 2009-09-09
That first tutorial on howtoforge is a great tutorial.

---

### Post by jk.cheng on 2009-09-10
> **Cardale said:**
> That first tutorial on howtoforge is a great tutorial.
yup... i hv saw it... but wonder is it possible to user onli 1 ISPConfig to control multiple server...

---

### Post by jk.cheng on 2009-09-10
Here is the more clear view on what i plan to do...

On hardware part i can add as much as i can, also it is in the budget of the company, and not prefer virtualization...

What is in my head now is like this
[img]http://lh4.ggpht.com/_rKHWMT_Xzw4/SqiqUN4vd1I/AAAAAAAAAc0/xEjLLQxXsTQ/s720/diagram.png[/img]

So, the question is;
1. which 1 is better?
2. for the 2 set server, can mysql cluster and apache cluster like that? and will it be any issue?
3. for the 6 or more server, how can i set WHM to control those server? remember, i only wan to install the WHM in web server...
4. plan to either use ispconfig or writing own WHM... hehe...

---

### Post by recentcoin on 2009-09-10
A good DNS structure has one master and several slaves.  For something like an ISP, you will want the DNS to be served off the slaves.  That makes it easy to upgrade the slaves and to replace the master when the time comes (and it *will* come)

You will probably want to have LDAP or something else to handle authentication in a central fashion.

You will probably want to have some sort of an apache server farm.  Standardized hardware and build loads are your friends.  

You will probably want more than postfix for your mail.  I suggest using dovecot for the IMAP and POP services.

---

### Post by jk.cheng on 2009-09-11
> **recentcoin said:**
> A good DNS structure has one master and several slaves.  For something like an ISP, you will want the DNS to be served off the slaves.  That makes it easy to upgrade the slaves and to replace the master when the time comes (and it *will* come)

You will probably want to have LDAP or something else to handle authentication in a central fashion.

You will probably want to have some sort of an apache server farm.  Standardized hardware and build loads are your friends.  

You will probably want more than postfix for your mail.  I suggest using dovecot for the IMAP and POP services.

thanks for the advise... so it look like i need a more advance topology then the 1 attached...

---

### Post by cameron365 on 2009-09-11
Hi,


I introdoce you a control panel called [EHCP]("http://www.ehcp.net") with very easy installation manual i am sure it is what you like it.

just check it out at [http://www.ehcp.net](http://www.ehcp.net)

---

