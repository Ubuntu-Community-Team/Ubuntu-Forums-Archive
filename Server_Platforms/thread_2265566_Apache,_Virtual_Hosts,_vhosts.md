---
title: "Apache, Virtual Hosts, vhosts"
date: 2015-02-16
forum: Server Platforms
---

### Post by MAC59 on 2015-02-16
Hey Guys,

        Long time user of Ubuntu but first time poster. I am trying to point a path on my server to a FQDN something like blah.coopfire.com

so in my /etc/apache2/sites-available/ i made this file blah.coopfire.com.conf and the contents of this file is as follows.

<VirtualHost *:80>
       
        ServerName blah.coopfire.com 
       ServerAlias alias.coopfire.com
        ServerAdmin [EMAIL="someadmin@mail.com"]someadmin@mail.com[/EMAIL]
        DocumentRoot /var/www/blah

There is of course the logfile entries and such but the above is the important part for me.

</VirtualHost>

In theory, should this work? I guess what I am asking is how should the servername be since I have the mian fqdn as coopfire.com, I am just a little confused.

Thanks for your input

---

### Post by slickymaster on 2015-02-16
*Moved to the ***Server Platforms*** sub-forum*

---

### Post by MAC59 on 2015-02-16
Sorry wasn't sure where to post it thanks

---

### Post by volkswagner on 2015-02-16
All of the following are FQDN's

blah.coopfire.com 
alias.coopfire.com 
coopfire.com 

You did not describe any problem. To answer your question, what you have supplied so far is correct.

You need to have name based virtual hosts enabled. After creating the vhost file you need to run a2ensite <site conf name>
Then reload apache2 service.

Do you currently have a problem to report?

---

### Post by SeijiSensei on 2015-02-18
Perhaps you're asking about how to add virtual hosts to the DNS?  Adding virtuals on Apache is a start, but you have to add records to the DNS for those additional names if you expect people to use them.

---

