---
title: "Issues with a fresh WP install on a VPS"
date: 2012-08-09
forum: Server Platforms
---

### Post by Lightmaster on 2012-08-09
Hello everyone!I just bought a new VPS, installed Ubuntu 12.04 on it, followed an online tutorial on how to install Wordpress on it and now I'm having problems.

I finished the tutorial step by step, but when I try to access the website, all I get is the default apache page.

What could be the issue?

---

### Post by Cheesemill on 2012-08-09
Which tutorial did you follow?

---

### Post by Lightmaster on 2012-08-09
Ooops, I forgot to post it

[http://echotutorials.com/96/ubuntu-complete-wordpress-setup-guide/tutorial/screencast/guide.php#more-96](http://echotutorials.com/96/ubuntu-complete-wordpress-setup-guide/tutorial/screencast/guide.php#more-96)

This is it.

---

### Post by Cheesemill on 2012-08-09
Did you make sure that you enabled your site using the a2ensite command and restarted Apache?

What's the output of:
```
ls -l /etc/apache2/sites-enabled
```

---

### Post by Lightmaster on 2012-08-09
root@ubi:~# ls -l /etc/apache2/sites-enabled
total 0
lrwxrwxrwx 1 root root 26 Aug  9 10:59 000-default -> ../sites-available/default
lrwxrwxrwx 1 root root 35 Aug  9 11:12 garajulindie.com -> ../sites-available/garajulindie.com
root@ubi:~#
 
I see two webites there.That might be the problem.Question is, how do I remove that?

---

### Post by Cheesemill on 2012-08-09
That's how it should be. Can you give me the output of:
```
cat /etc/apache2/sites-enabled/garajulindie.com
```

---

### Post by Lightmaster on 2012-08-09
root@ubi:~# cat /etc/apache2/sites-enabled/garajulindie.com
<VirtualHost *:80>
        ServerAdmin [email] blocked out [/email]
        ServerName garajulindie.com
        ServerAlias [www.garajulindie.com](www.garajulindie.com)
        DocumentRoot /var/www/garajulindie.com/public_html/
        ErrorLog /var/www/garajulindie.com/logs/error.log
        CustomLog /var/www/garajulindie.com/logs/access.log combined
        <Directory /var/www/garajulindie.com/public_html>
                Options FollowSymLinks
                AllowOverride All
                RewriteEngine On
                RewriteCond %{HTTP_HOST} ^www.garajulindie.com$ [NC]
                RewriteRule ^(.*)$ http://garajulindie.com/$1 [R=301,L]
        </Directory>
</VirtualHost>


There you go.Thank you so much for helping me out :)

PS: I blocked out the email adress over there to not show up on the forum.

---

### Post by Cheesemill on 2012-08-09
Hmmm, that all looks good to me.

Usually the problem you are having with the default page appearing happens either when name-based virtual hosting isn't set up properly or if you access the webserver using an address that doesn't match any of the ServerName or ServerAlias directives.

You are trying to access your site by going to either garajulindie.com or [www.garajulindie.com](www.garajulindie.com) and not by its IP address aren't you?

---

### Post by dbrooke on 2012-08-09
> **Lightmaster said:**
> Hello everyone!I just bought a new VPS, installed Ubuntu 12.04 on it, followed an online tutorial on how to install Wordpress on it and now I'm having problems.

I finished the tutorial step by step, but when I try to access the website, all I get is the default apache page.

What could be the issue?

Did you enable your virtualhost?

man a2ensite

service apache2 restart

Edit: Sorry, didn't see cheesemill already suggested this!
Donovan

---

### Post by Lightmaster on 2012-08-09
Ah...I was trying to acces the website via de IP adress.I'm such an newbie.I've updated the DNS records and now, instead of the default apache page, I'm getting a "Error establishing a database connection" page.

I don't know what the hell is wrong.The wp-config page is good, same user/pass as with the mysql database I have created.


LE: Nevermind, small typo= a lot of wasted time.Nonetheless, thank you very much!

---

