---
title: "MX Record"
date: 2010-05-14
forum: Server Platforms
---

### Post by sligoman on 2010-05-14
Hi All

---

### Post by mamies on 2010-05-14
If you don't have a DNS setup I would first set it up and if it is going to be on the same machine I advise installing something like Webmin ([http://www.ubuntugeek.com/webmin-installation-and-configuration-in-ubuntu-linux.html](http://www.ubuntugeek.com/webmin-installation-and-configuration-in-ubuntu-linux.html)).
 
After you have installed BIND and Webmin I would then create an Internal and External view (this took me a long time to learn) which will allow you to change the DNS records to point where you like. You are able to easily create MX and A records through Webmin.
 
I use it for the business I work for and it works great.
 
Thanks,

Matthew

---

### Post by cdenley on 2010-05-14
MX records are a type of DNS record. Where is your DNS server? Either you are running one yourself, or you are using a hosted DNS service, probably from the same place you registered your domain. Can you give us your domain? Are you running bind at the moment?

---

### Post by sligoman on 2010-05-14
Hi mamies and cdenley

Thanks for the reply.

@ mamies.  Bind DNS and webmin are on the server already I don't use the DSN server because I have set-up the named domains Virtually.

@  cdenley: As above the DNS server was installed but I have set-up the named domains Virtually I.E. Two domains on the same static IP. The sites are not yet live but are accessible using their domain names. my domain name register 'Name Cheap' has an option to use FreeDNS. 

Mail Servers postfix and dovecot were set-up using the guide from:

[http://library.linode.com/email/postfix/postfix-dovecot-mysql-debian-5-lenny]("http://library.linode.com/email/postfix/postfix-dovecot-mysql-debian-5-lenny")

One part of the instructions sugested:

"Please note that you'll need to modify the DNS records for any domains that you wish to handle email by adding an MX record that points to your mail server's fully qualified domain name. If MX records already exist for a domain you would like to handle the email for, you'll need to either delete them or set them to a larger priority number than your mail server. Smaller priority numbers indicate higher priority for mail delivery, with "0" being the highest priority."

And that is where I have hit a snag as this is new territory to me.

Every thing seems to be working OK, except that I can not receive emails from my hosted website to my email client I.E. Thunderbird or evolution so I don't want to do something that may screw all the hard work put into setting up this server.

Hope that helps

Regards

Liam

---

### Post by cdenley on 2010-05-14
> **sligoman said:**
> 
@  cdenley: As above the DNS server was installed but I have set-up the named domains Virtually I.E. Two domains on the same static IP. The sites are not yet live but are accessible using their domain names. my domain name register 'Name Cheap' has an option to use FreeDNS. 


That doesn't make any sense. If your domain can be resolved to an IP address from anywhere, then you are using DNS. It doesn't matter if you're using virtual hosting or not. Your domain still needs to be resolved to an IP using DNS. You must be using DNS. What we need to know is where your DNS server is. You said you are running a DNS server (bind?), but you aren't using it? Are you using FreeDNS as a DNS server. If so, did you try creating an MX record with them? Once again, this would be easier if you gave us your domain.

---

### Post by sligoman on 2010-05-15
Hi Since your last reply I have since made these sites live and have found out that the MX Record can be edited at the site where I registered by domain names.

I am putting the email issue on hold at the moment as I have another issue that has just popped up.

My sites are now showing the IP address before the domain names only on pages that have been accessed using an internal link the main page is OK 

[http://www.discountsuperstore-uk.com](http://www.discountsuperstore-uk.com)
[http://www.discountfootballgifts-uk.com](http://www.discountfootballgifts-uk.com)

So if any one could shed some light on this for me or need further info please let me know

Regards and thanks for the help so far

Liam

---

### Post by cdenley on 2010-05-15
That is related to the content of your website, and I'm not familiar with oscommerce. Somewhere it is using the value "http://81.149.219.88/discountfootballgifts-uk.com/" where it should be "http://discountfootballgifts-uk.com/". Check the configuration for oscommerce.

---

### Post by sligoman on 2010-05-15
Thank you for the replies and time

Will look into the configuration side of oscommerce

Many Thanks

Liam

---

