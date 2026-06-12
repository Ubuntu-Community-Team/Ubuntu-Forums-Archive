---
title: "what do I need smtp server for?"
date: 2012-01-07
forum: Server Platforms
---

### Post by Samic on 2012-01-07
I have a vps with Ubuntu server and I have set up Postfix because I want to use my domain for email though it's just for forwarding:
[EMAIL="info@mydomain.com"]info@mydomain.com[/EMAIL]   -->   [EMAIL="my.main.email@gmail.com"]my.main.email@gmail.com[/EMAIL]
I don't use my server for sending emails or Thunderbird or so.

my question is do I really need smtp server? can I block access to my smtp port (25)?
this is because I'm not really sure that I have secured my smtp server enough.

---

### Post by lisati on 2012-01-07
If all you're going to use your Postfix installation for is forwarding emails, and you're not expecting mail from outside your network, you can safely leave port 25 closed.

---

### Post by ajishrao on 2012-01-07
Yes we should keep mail server of if your always using the Postfix. It is always safe to keep most ports off till you don't really know why it is open.

---

### Post by Samic on 2012-01-07
ok! I did az you told! I ran this:

iptables -A INPUT -p tcp --destination-port 25 -j DROP

But now when I send an email from "my.email@hotmail.com"  to  "info@mydomain.com" , I don't get it at "my.main.email@gmail.com" as before!

---

### Post by dirtrider1 on 2012-01-07
By closing port 25 you just blocked smtp which is the default port for most services like Hotmail. You will need it open to receive mail from outside mail servers.

---

### Post by computerfox on 2012-07-01
If you're running your own server from home, the only ports that you should open are the ones that you are actually using: http,https,control panel. 

You shouldn't ever close the smtp port because then no one on your network will be able to send mail.  Just because something is there, that doesn't mean you have to actually use it.  You don't need it, just let it be.

---

### Post by SeijiSensei on 2012-07-02
If you close inbound port 25, you'll also make it impossible for remote serves to send administrative messages like non-delivery notices in response to the mail you send.

---

