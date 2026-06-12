---
title: "Setting up postfix with mysql..."
date: 2009-09-14
forum: Server Platforms
---

### Post by hockey97 on 2009-09-14
Hi, I currently followed this tutorial:  [http://www.howtoforge.com/virtual_postfix_mysql_quota_courier_ubuntu_edgy_p2](http://www.howtoforge.com/virtual_postfix_mysql_quota_courier_ubuntu_edgy_p2)

just that page. 

It shows how to setup postfix with mysql.  

I done whats on that page only.  If you go to the next page  which is page 3.  I want to know  if I need to do anything more then just whats on page 2 which is the link I provided above it's page 2. 

I want to know what else I would need to do to get the postfix to work with mysql?

---

### Post by windependence on 2009-09-14
Any reason you didn't want to use something like Zimbra? It uses postfix, MySQL, LDAP, ClamAV, and Spamassassin, all in one package.

-Tim

---

### Post by hockey97 on 2009-09-14
well I want to provide e-mail service so I need to customize the layout look of the webmail.

---

### Post by windependence on 2009-09-14
You CAN do that with Zimbra. You can even change themes. Comcast uses Zimbra for their ISP customers and you wouldn't even know it. Yahoo's mail client is also Zimbra.

-Tim

---

### Post by hockey97 on 2009-09-15
would I be able to edit the code or scripts to add new functions? 

I am making a social network site. So the mail area will also display internal messages and other stuff.

---

### Post by hockey97 on 2009-09-18
> **windependence said:**
> You CAN do that with Zimbra. You can even change themes. Comcast uses Zimbra for their ISP customers and you wouldn't even know it. Yahoo's mail client is also Zimbra.

-Tim

What I want to do is use php to do a lookup in mysql database.  Then the php scripts will be able to show the mail via a web interface.  I am not sure but I think e-mails are saved as text files at a folder. I thought with php I can simply open those files and I can also show whats in the user mail box before they open e-mail. 

I want to have control on the e-mail interfaces. I would like the mail area to also hold internal messages from users inside my website. 

So I don't want to just install software that is set to go already made. Since I am not making a webmail interface similar functions to aol,msn, or other mailing services they have. 

I was told that making posft work with mysql is simple. I just followed that tutorial exactly how it tells me to make the configs.  Right now the mail server dosen't work at all no outgoing or e-mail from outside coming in. They showed to download the postfix-mysql modual and install it.

Then make 5 files which will hold mysql sql code to do a lookup on the databases in mysql and then create those databases. One is for domains, another is users, and then transport.  I created those and then setup
the postfix server.

One thing I didn't understand about he tutorial is if you scroll down where you start to see red text. It states to use your FQDN. I am guessing  it's my hostname of my computer/server? 

I typed in terminal hostname and then use that data as the hostname.

---

