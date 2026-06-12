---
title: "apache2 sub domains"
date: 2005-12-12
forum: Server Platforms
---

### Post by Hube on 2005-12-12
With earlier versions of apache and the httpd.conf file, I used to be able to do the following:

<VirtualHost *:80>
        ServerName **www**.mydomain.com
        ServerAdmin [email]user@mydomain.com[/email]
        DocumentRoot /var/www/html/web
</VirtualHost>

<VirtualHost *:80>
        ServerName **mail**.mydomain.com
        ServerAdmin [email]user@mydomain.com[/email]
        DocumentRoot /var/www/html/mail/
</VirtualHost>

With apache2 and the modeified configuration (sites_available, sites_modified) I'm unsure how I should attempt this?  Can somebody point me in the right direction.

I believe this is called using a sub-domain (www, mail, username etc) along with the full domain name (mydoamin in the example above).

Help would be much appreciated,

Hube

---

### Post by localzuk on 2005-12-12
It should be pretty similar, here is a section taken from the httpd.conf of one of my sites running apache 2

```

<VirtualHost *:80>


        ServerName www.mail.domain.com
        ServerAlias www.mail.domain.com mail.domain.com
        ServerAdmin webmaster@domain.com
        DocumentRoot /home/overlord/domains/domain.com/public_html/mail
        ScriptAlias /cgi-bin/ /home/overlord/domains/domain.com/public_html/mail/cgi-bin/

        UseCanonicalName OFF

        SuexecUserGroup overlord overlord
        CustomLog /var/log/httpd/domains/domain.com.mail.bytes bytes
        CustomLog /var/log/httpd/domains/domain.com.mail.log combined
        ErrorLog /var/log/httpd/domains/domain.com.mail.error.log
        <Directory /home/overlord/domains/domain.com/public_html/mail>
                Options +Includes -Indexes
                php_admin_flag engine ON
                php_admin_flag safe_mode OFF
                php_admin_value sendmail_path '/usr/sbin/sendmail -t -i -f overlord@domain.com'
        </Directory>
</VirtualHost>

```

However, the set up of apache is not everything. You also need correct DNS set up, either via a DNS server (bind) or using your hosts file.

---

### Post by Hube on 2005-12-12
Thanks.

I have the domain registered so getting to the box via dns is not a problem.  I'm not sure that your example is the same as what I'm looking for.  Based on the sub-domain (www or mail) I need to get to different pages.  The [www.mydomain.com](www.mydomain.com) will go to the main web site, the mail.mydomain.com is setup to allow users to login and get their email (via imap).

It looks to me that you example provides a path to the same pages based on the user entering a number of different (but similar) urls.

Or, it could be that I'm completely missing something...??? It's certainly been known!

Cheers, Hube

---

