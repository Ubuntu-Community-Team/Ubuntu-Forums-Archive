---
title: "DNS for email server"
date: 2009-01-20
forum: Server Platforms
---

### Post by xiaomahe on 2009-01-20
Hai, currently i am doing email server for my college's project, and i am still new to this server thingy, but will learn very fast if there is enough help

when i want to install Postfix, it asked me for a domain name. [https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

Well, i dun have any domain name to put inside.
So, how can i get a domain name? (rather than buying from domain provider)

---

### Post by hyper_ch on 2009-01-20
you could use a dynamic one like provided by dyndns.org or noip.com besides that you can get .com/.net/.org for $ 9.99/y and you the free tool [http://www.everydns.net](http://www.everydns.net) to manage the dns for it.

---

### Post by xiaomahe on 2009-01-20
if i use the dynamic one, would other people can access my domain? like the real online domain.. where anyone can just access to my domain, so it is not restricted on a certain network only

---

### Post by hyper_ch on 2009-01-20
depends on whether you can portforward the according ports... if you're on a university network, I don't think you can portforward to your computer.

---

### Post by karanpals on 2009-01-20
You need a dynamic or paid domain name etc, if you are to receive emails from Internet. If you are just to make a test case. Setup bind (DNS server) on the mail server itself and test your scenario.
Following things you must study about DNS before setting up a mail server
1) What are MX records
2) What are DNS based black lists 
3) Whar are  A records.
4) What are PTR records.

Its not so difficult to under stand these things

Next would be setting up the mail server.

vmailadmin.org gives a nice web based frontend to manage postfix with domains/users information getting stored in mysql.

All the best

---

### Post by trentscott4 on 2009-01-21
Or you can manage it within webmin (if you have it installed):

[http://rimuhosting.com/support/settingupemail.jsp?mta=postfix](http://rimuhosting.com/support/settingupemail.jsp?mta=postfix)

---

