---
title: "setting up email on a Ubuntu VPS"
date: 2013-09-20
forum: Server Platforms
---

### Post by Kev_Martin on 2013-09-20
Hello All

I am using a 123-reg VPS with Ubuntu. The web sites are working fine as is mySql Database, mail is another issue. I get the following error when sending a email to the new server via outlook: 

retry time not reached for any host after a long failure period  

And through Thunderbird: 

An error occurred while sending mail. The mail server responded:   Requested action not taken: mailbox unavailable or not local. Please  check the message recipient [EMAIL="kev@mydomain.com"]kev@mydomain.com[/EMAIL] and try again.

  

The setup is thus..

  VPS is at 212.xx.xx.xx7 Domain name is mydomain.com.
The domain is registered at Joker.com

  
My settings at Joker

  A Records
Host                                 Target              TTL
mydomain.com         212.xx.xx.xx7       7200
[www.mydomain.com]("http://www.mydomain.com")     212.xx.xx.xx7       8200
mx.mydomian.com      212.xx.xx.xx7       1800
ldap.mydomian.com    212.xx.xx.xx7       1800
mail.mydomian.com    212.xx.xx.xx7       1800

MX-Records          Target              Priority
Mydomain.com        mail.mydomain.com   10
  On the VPS I used this step thru guide ([http://www.pixelinx.com/2013/09/creating-a-mail-server-on-ubuntu-postfix-courier-ssltls-spamassassin-clamav-amavis/](http://www.pixelinx.com/2013/09/creating-a-mail-server-on-ubuntu-postfix-courier-ssltls-spamassassin-clamav-amavis/)) setting mail.example.com to match above.

  
dig mx mydomain.com returns

  mydomain.com 86400 IN MX 10 mail. mydomain.com
mail. mydomain.com 86400 IN A 212.xx.xx.xx7
  authtest kev@ mydomain.com returns
  Authenticated: [EMAIL="kev@mydomain.com"]kev@mydomain.com[/EMAIL] (uid 5000, gid 5000)
  Etc etc, all looks correct

  So, can anyone see where I am going wrong please?

Thanks in advance

---

### Post by Kev_Martin on 2013-09-24
Anyone got any ideas please?

---

### Post by CharlesA on 2013-09-24
Have you checked the logs on the server?

I used [this]("http://mxtoolbox.com/SuperTool.aspx") tool a lot when I was trying to get my mail server up and running. Give it a shot and see what it says.

---

