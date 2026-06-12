---
title: "Webserver: How to join IP with web address?"
date: 2008-04-10
forum: Server Platforms
---

### Post by MasterJS on 2008-04-10
I've started making a webserver, having installed LAMP and everything else that is needed. I'd like to know how to join my IP address with the web address that i am going to buy.

---

### Post by songshu on 2008-04-10
welcome to the world of DNS, cause that will be what you need.

usually the one selling you the domain ( example.com) should link it to your IP, and most if not all have a nice webbased tool so you can do it yourself, just ask them how to do it if you are not sure.

mine looks like this

Name  	          Type  	Content  	       TTL
example.com  	MX10  	mail.example.com  	3600  	
example.com 	MX20 	mail.another.example.com 	3600 	
example.com 	A 	123.123.123.123 	3600 	
*.example.com 	A 	123.123.123.123 	3600 	
mail.example.com 	A 	123.123.123.123 	3600 	


the MX records are showing where mail for example.com should go to, but you don't need that for now.
setting something like below would be sufficient for a webserver

example.com 	A 	123.123.123.123 	3600 	
[www.example.com](www.example.com) 	A 	123.123.123.123 	3600

---

### Post by MrFSL on 2008-04-10
> welcome to the world of DNS, cause that will be what you need.

Yup we've all been here at one time. If you registered your Domain Name with a company like GoDaddy, it is not obvious nor intuitive how to do this. This is done intentionally because they want you to host your webpage on their servers and pay them. 

You can use a service such as [http://www.everydns.net/](http://www.everydns.net/) to point your Registered Domain Name to your IP address but then you will have to login to your account where you registered the name and update the dns records.

Hope this helps. If you are still lost let us know who you registered through and we might be able to offer additional help.

---

### Post by chuck jessup on 2008-04-10
cant you set up and run a dns server (i believe it is included in the server cd - bind9) 

i havent tried it but i think that you can do this. umm other wise there are a bunch of comapnies that do dns hosting... 

anywho best wishes -

---

### Post by justinwhite on 2008-04-10
Run your own DNS server...

It's called bind9. ;)

---

### Post by songshu on 2008-04-11
you could run your own DNS server, and bind9 is one of the several to choose from.
what you would need to do is to ask your domain registrar to make your dns server authorative for this domain.

however it does bring you some flexibilty concerning your domain, but this is normally not really needed when your registrar does a normal job and brings a lot of extra things to worry about and i would make sure you understand the concept first a little better.

so bottom line, i would let the registar do the job that it is paid for and concentrate on your webserver first.

---

### Post by Seti on 2008-04-11
Another thing to consider, is whether you have a dynamic or static IP address. Use dyndns.org and you can run a client that logs into dyndns and updates your new IP. Usually newer commercial routers will do this too.
Otherwise if you go with someone, say domainmonster.com, then you pay the fee, and you login to their site to set up the dns stuff as required.

---

