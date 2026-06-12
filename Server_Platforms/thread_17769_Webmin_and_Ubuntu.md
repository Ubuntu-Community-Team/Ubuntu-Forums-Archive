---
title: "Webmin and Ubuntu"
date: 2005-03-02
forum: Server Platforms
---

### Post by can8dnSix on 2005-03-02
Hey all,

I am having an issue logging into webmin. I think this is because the root account has not been enable, but, without it being enabled, am I able to log into Webmin? It asks for a password with the username: root. I tried my password but this does not seem to work. 

I know I could just give root a password, but is there a way I can set it back to ubuntu's default setting? I like using the sudo command and don't want to always have to "su" before I do something. I am not that smart.. lol so if anyone can give me some help that would be cool.

can8dnSix

---

### Post by az on 2005-03-02
The webmin packages in universe were made for debian.  It probably would be easy to tweak them to work with sudo, but they don't.

I found it easier to download the lates sources for Webmin and install it by hand, the old fashined way.  It works fine.




Canadian, eh?

---

### Post by tharc on 2005-03-18
Actually you just have to change the password of the root user.
Which exists in Webmin.

To change the password to "foo" for instance just run
/usr/share/webmin/changepass.pl /etc/webmin root foo

---

### Post by az on 2005-03-18
[QUOTE=tharc]Actually you just have to change the password of the root user.
Which exists in Webmin.

To change the password to "foo" for instance just run
/usr/share/webmin/changepass.pl /etc/webmin root foo[/QUOTE]

Very nice!

---

### Post by CompShrink on 2005-04-15
Wow, thanks that saved me a lot of effort down the road I'm sure... was wondering what was up... i don't ahve a root password, lol.

---

### Post by Maikel on 2005-04-16
Better to download from [www.webmin.com](www.webmin.com) ´cause you cant update the hoary-version!

---

### Post by jdong on 2005-04-17
[QUOTE=Maikel]Better to download from [www.webmin.com]("http://www.webmin.com") ´cause you cant update the hoary-version![/QUOTE]

I've received a backports request about this; and I was attempting to package 1.200 like the way Sid's 1.180 was packaged, but the attempt was a miserable failure...

Debian in general has been getting lazy with Webmin. Might wanna drop the maintainer a quick e-mail (**polite**, of course) some time.

---

