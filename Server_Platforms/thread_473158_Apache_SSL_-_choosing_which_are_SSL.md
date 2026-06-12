---
title: "Apache SSL - choosing which are SSL?"
date: 2007-06-13
forum: Server Platforms
---

### Post by pkarjala on 2007-06-13
I've set up our LAMP server so that Apache works with SSL and serves pages via https requests.

Except that now it does this with every single page.  If I attempt to access a page using http, it gives this error:

> Bad Request

Your browser sent a request that this server could not understand.
Reason: You're speaking plain HTTP to an SSL-enabled server port.
Instead use the HTTPS scheme to access this URL, please.

    Hint: [https://xxxxxx.company.com/](https://xxxxxx.company.com/)

Apache/2.0.55 (Ubuntu) PHP/5.1.6 mod_ssl/2.0.55 OpenSSL/0.9.8b Server at xxxxxxx.company.com Port 443

The problem is temporarily bypassed by using https for all sites on the box.  But I'd like to be able to have https active for only some of these sites, such as our webmin and phpmyadmin sections.

How can I go about selectively enabling https for certain portions of our site, while letting it serve as normal for others?

---

### Post by carcioni on 2007-06-18
In that you haven't gotten any responses, I will take a little crack at this.
First, you may get better results with respect to apache and SSL by posting this request to one of the apache httpd forums instead, as there are members there that live this stuff every day.

That said, be sure that the standard 'Listen 80' line in the httpd.conf  file has not been removed or commented out. A 'netstat -a | grep http' should show the port being available.

I expect what has happened is the 'httpd-ssl.conf' file has overridden the default <VirtualHost> entry and replaced _default:80 with _default:443 in the main httpd.conf file, or somehow forced everything through https.

You can change the behaviour for specific URL's using virtual hosts. There may be a httpd-vhost.conf file or something like it that you can use as an example.

As I said earlier, there is a whole other group of people who do this everyday at apache.org. Also, the docs there for setting this up are quite good.

Sorry, I am not as much help as you'd like, but apache httpd administration  is a pretty broad  topic, and SSL is a bit specialized to try to clarify too much here. Give the apache site a try.

Cheers
D

---

### Post by pkarjala on 2007-06-18
Thanks for the pointers.  I'll dig through the .conf files and see what I can find; otherwise, I'll go poke the apache forums and see what I can find out.

Thanks!

---

### Post by dfreer on 2007-06-19
might have to do with your virtual hosts setup. what does your /etc/apache2/sites-enabled/default look like?
if you didn't set up a seperate virtual host for SSL, it will use SSL on your entire site. Here's an short example of what it should (roughly) look like:
```

Name VirtualHost *:80
Name VirtualHost *:443

<VirtualHost *:80>
      ServerName mysite.company.com
      .....
<VirtualHost />
<VirtualHost *:443>
     ServerName mysite.company.com
     .....
     SSLEngine on
     SSLCertificateFile /where/this/file/is/located.pem
<VirtualHost />

```

So basically, you can use the same documentroot and servername (or different ones if you wish), just specify the one to use SSL.

The above will result in [http://mysite.company.com](http://mysite.company.com) to show one page, and [https://mysite.company.com](https://mysite.company.com) to show the same page but encrypted.

---

### Post by mcc666 on 2007-06-21
I did the same - but i can not see nothing in ssl mode. Could you please give me some hint how to force apache to log more information about ssl?


Rgds,
MCC

---

### Post by dfreer on 2007-06-21
try adding the CustomLog and ErrorLog to the SSL virtual host config. There should already be in the default config, just copy and paste it in and change the log filenames (from /var/log/apache2/error.log to /var/log/apache2/ssl.error.log for example). sorry I'm posting from windows, so I can't give you the exact info right now :(

---

