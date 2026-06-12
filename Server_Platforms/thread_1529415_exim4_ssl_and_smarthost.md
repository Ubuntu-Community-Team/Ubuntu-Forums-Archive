---
title: "exim4 ssl and smarthost"
date: 2010-07-12
forum: Server Platforms
---

### Post by pdc124 on 2010-07-12
I use exim too relay mail to my ISPs SMTP server and its been fine for several years . They are changing  it to 

SSL on port 465 

ive tried configuring it using gmail as an example 
[http://www.manu-j.com/blog/wordpress-exim4-ubuntu-gmail-smtp/75/](http://www.manu-j.com/blog/wordpress-exim4-ubuntu-gmail-smtp/75/)

and then 

root@server:~# exim -v -odf [email]xxxx@xxx.ac.uk[/email]
test
.
LOG: MAINConnecting to smtp.blueyonder.co.uk [195.188.53.60]:465 ... connected
LOG: MAIN
  SMTP timeout while connected to smtp.blueyonder.co.uk [195.188.53.60] after initial connection: Connection timed out
LOG: MAIN
  == [email]xxx@xxx@.ac.uk[/email] R=send_via_BY T=BY_smtp defer (110): Connection timed out: SMTP timeout while connected to smtp.blueyonder.co.uk [195.188.53.60] after initial connection
server@server:~$

and thats it. nothing in /var/log/exim/main_log


FWIW configuring when t'bird  to connect directly the settings are usign SSL /TLS with a emailaddress as pasword but with secure authentication unchecked .  

So how do i replicate that in exim ?

---

