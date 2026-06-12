---
title: "purchased .com, have it point at my server?"
date: 2008-03-25
forum: Server Platforms
---

### Post by android6011 on 2008-03-25
Ok, this is my first experience with a .com and everything so I'm not sure what all I need to do. I have a server sitting at my house, and I registered the name with godaddy.com . How do I get the mysite.com to point at my server? thanks

---

### Post by andyho on 2008-03-25
I'm registered with godaddy too! Their tools are pretty easy to use. Since you're using your own server you should just need to log into your godaddy site info and set it to use your servers ip address. :)

---

### Post by android6011 on 2008-03-25
> **andyho said:**
> I'm registered with godaddy too! Their tools are pretty easy to use. Since you're using your own server you should just need to log into your godaddy site info and set it to use your servers ip address. :)

where do I set it at? thanks

---

### Post by rickyjones on 2008-03-25
> **android6011 said:**
> where do I set it at? thanks

Under your domain in Godaddy you should have a link called Total DNS Control. This tool will allow you to create and delete DNS records for your domain. It will, by default, point to various Godaddy services. If you wish to point it to your server for mail/web/etc... then change the "@" records IP address to your public IP address.

-Richard

---

### Post by android6011 on 2008-03-25
Ok thank you. so for the services that are listed for example mail which i dont need at the moment why does it say pop.secureserver.net ?

---

### Post by volkswagner on 2008-03-25
Login to godaddy >select "my account"> select "manage Domains" > select the domain you want to modify> select the forward link > clik enable> enter your url IE:  [http://##.###.###](http://##.###.###)

Select permanent or temporary.  Note if your isp provides you with a dynamic address this will work until your ip changes.  If it changes often you will need to set up Dyn DNS solutions with DynDns.com, NoISP.com, even godaddy.com

This should get you started.

---

### Post by rickyjones on 2008-03-25
> **android6011 said:**
> Ok thank you. so for the services that are listed for example mail which i dont need at the moment why does it say pop.secureserver.net ?

Because that is the godaddy POP3 server.

By default Godaddy will point all your records to themselves in the event that you do hosting with them.

-Richard

---

### Post by android6011 on 2008-03-25
> **volkswagner said:**
> Login to godaddy >select "my account"> select "manage Domains" > select the domain you want to modify> select the forward link > clik enable> enter your url IE:  [http://##.###.###](http://##.###.###)

Select permanent or temporary.  Note if your isp provides you with a dynamic address this will work until your ip changes.  If it changes often you will need to set up Dyn DNS solutions with DynDns.com, NoISP.com, even godaddy.com

This should get you started.


you can have dyndns update godaddy? how?

---

