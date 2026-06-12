---
title: "adding records"
date: 2011-12-18
forum: Server Platforms
---

### Post by donsmouse on 2011-12-18
how do i add A and MX recordords in ubuntu server 11.10?
which file do i edit?
could you please give me some examples of adding these records
 
 
Thanks In Advance

---

### Post by lykwydchykyn on 2011-12-18
When you create a zone in the master config file, you specify a file that will hold its records.

[This page](https://help.ubuntu.com/community/BIND9ServerHowto) might be a good place to start reading to understand better.

---

### Post by donsmouse on 2011-12-18
thank you ill give it a try and let you know

---

### Post by donsmouse on 2011-12-18
:confused:ok i followed the guide and got everything setup except the MX records it doesnt show which file or how to put it in?????

---

### Post by moonpup on 2011-12-18
If this is regarding your other post and using the Dyn service, you need to setup the MX records at DYN. Is there a reason you are trying to add these locally?

---

### Post by donsmouse on 2011-12-18
yes im trying to setup my server on my machine to send/recieve mail from everywhere
 
i did set it up on the dyn side

---

### Post by donsmouse on 2011-12-18
i was using outlook 2010 on my laptop and trying to send email from:smouse1973@comcast.net to [EMAIL="donald@smousecomputers.dyndns"]donald@smousecomputers.dyndns[/EMAIL]-server .com
 
and here is the errors it gives me:
 
 
Reporting-MTA: dns; qmta01.westchester.pa.mail.comcast.net [76.96.62.24]
Received-From-MTA: dns; omta14.westchester.pa.mail.comcast.net [76.96.62.60]
Arrival-Date: Sun, 18 Dec 2011 23:46:01 +0000
 
Final-recipient: rfc822; [EMAIL="donald@smousecomputers.dyndns-server.com"]donald@smousecomputers.dyndns-server.com[/EMAIL]
Action: failed
Status: 5.1.1
Diagnostic-Code: smtp; 550 You must authenticate to use MailHop Outbound
Last-attempt-Date: Sun, 18 Dec 2011 23:46:02 +0000
 
and i did setup my username and password on my server

---

### Post by moonpup on 2011-12-19
What services did you specifically buy from Dyn. I'm not sure you purchased the correct ones.

---

### Post by donsmouse on 2011-12-19
dyn email lite and dyn standard pro i believe

---

### Post by moonpup on 2011-12-19
For you to receive email on your server at home on a port other than 25 you need the email gateway service which I mentioned to you before.

It can be found here - [http://dyn.com/email/dyn-email-gateway/](http://dyn.com/email/dyn-email-gateway/)

Note the section about alternate email relay ports.

As for the DNS piece, I used this - [http://dyn.com/dns/dyn-standard-dns/](http://dyn.com/dns/dyn-standard-dns/)

Read the documentation about setting up your DNS and MX records, and then how to setup the email gateway service. It's all pretty straight forward if you read their docs.

---

### Post by donsmouse on 2011-12-19
ok thank you so much

---

