---
title: "ISP blocked port 25"
date: 2009-11-08
forum: Server Platforms
---

### Post by dragonkeeper2004 on 2009-11-08
Im a relitive newbie when it comes to linux. all i know is what i've messed with at school/personal use. Now im trying to setup a LAMP server with WordPress blogging php script. The script sends an e-mail with your password once you sign up.
 
My problem is that i have ATT yahoo internet and they block port 25. here is the help document that outlines what needs to be setup to make this work. [http://www.att.com/esupport/article.jsp?sid=KB400335](http://www.att.com/esupport/article.jsp?sid=KB400335)
 
I have attatched my master.cf and main.cf to see if anyone has ideas on how to make this work. My blog is essentialy crippled since i cannot have new uses sign up.
 
[ATTACH]135239[/ATTACH]
 
[ATTACH]135240[/ATTACH]
 
Does anyone have ideas on this?

---

### Post by ian dobson on 2009-11-08
Hi,

Maybe try setting your relayhost to point to the smtp server of your provider so that the mails are set over their (ISP) mail server. Tat should solve the problem.

Alot of "home" ISP's block sending to port 25 to try and reduce the chance that an infected PC (virus) can be used to send spam emails.

Regards
Ian Dobson

---

### Post by windependence on 2009-11-08
[http://www.no-ip.com/services/managed_mail/inbound_port_25_unblock.html](http://www.no-ip.com/services/managed_mail/inbound_port_25_unblock.html)

Enjoy!

-Tim

---

### Post by kustomjs on 2009-11-08
what you could do is switch your outgoing to att outgoing server address and switch it to port 587.

---

