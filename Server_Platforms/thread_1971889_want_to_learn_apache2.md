---
title: "want to learn apache2"
date: 2012-05-03
forum: Server Platforms
---

### Post by imran042 on 2012-05-03
hello,, i am new to this forum,
please i want to learn apache2.
i searched for many sites  but none of them i found working out for me.

anyone who can guide for the site to learn apache2.
i know html, perl and a little bit of c, and now want to learn apache2.

waiting for reply

---

### Post by lisati on 2012-05-03
*Thread moved to **Server Platforms**.*

You might find the following helpful: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by newbie-user on 2012-05-03
The man pages for apache2 are helpful also. Is there anything specific you're looking for or just a basic intro to apache?

---

### Post by Lars Noodén on 2012-05-03
Like when learning anything else, it helps very much to have some specific goals in mind when starting.  What is it that you would like to do with Apache2?  Go from that.

Otherwise, you could look at using [content negotiation](https://httpd.apache.org/docs/2.2/content-negotiation.html) to make your site multilingual.  You'd have separate files for each supported language.  So instead of index.html you'd have index.[de](http://www.loc.gov/standards/iso639-2/langcodes.html).html, index.[en](http://www.loc.gov/standards/iso639-2/langcodes.html).html and so on.

Or you could look at [Server Side Includes](https://httpd.apache.org/docs/2.2/howto/ssi.html) to make standardized headers, footers, and menus without the pain, fuss and mess of PHP or other scripting.   Be sure to use [IncludesNOEXEC](https://httpd.apache.org/docs/2.2/mod/core.html#options) to avoid the overhead and security issues related to scripting.  

Those are just two examples.  What do you want to do with the web server?

---

### Post by imran042 on 2012-05-03
i want to study apache 2 for uploading perl form-upload scripts, on the server.
 i have done html, perl a bit of c, and now my final thing is apache2(bcoz apache2 will be needed. after completing my perl form upload script, i need to upload on the web server and apache 2 will do it for me)

waiting for reply

---

### Post by Jonathan L on 2012-05-03
> i want to study apache 2 for uploading perl form-upload scripts, on the server.
 i have done html, perl a bit of c, and now my final thing is apache2(bcoz apache2 will be needed. after completing my perl form upload script, i need to upload on the web server and apache 2 will do it for me)


Hi Imran

Not sure if you meant forms in general or uploads in particular ...

Why not try this tutorial? [http://www.seaglass.com/file-upload-pl.html](http://www.seaglass.com/file-upload-pl.html)

If you're new to this, I'd recommend PHP instead of Perl, but why not do both and have your own opinion:
[http://www.w3schools.com/php/php_file_upload.asp](http://www.w3schools.com/php/php_file_upload.asp)

Hope that's helpful.

Kind regards,
Jonathan.

---

### Post by Lars Noodén on 2012-05-03
Perl's a very good choice.  I found it much more complete and polished than PHP, back when I used both.

If you haven't already, take a look at CPAN's [CGI::Simple](http://search.cpan.org/~andya/CGI-Simple-1.113/lib/CGI/Simple.pm) and other CGI:: modules.  With it you will be easily able to read forms data.  

Another approach to CGI is using HTML::Mason, which allows you to embed pieces of script in your web pages.

---

### Post by Lars Noodén on 2012-05-03
Here are two tutorials.  There are quite many others out there so if you have questions from one, they might be answered in others.

[http://www.tutorialspoint.com/perl/perl_cgi.htm](http://www.tutorialspoint.com/perl/perl_cgi.htm)
[http://www.cs.unc.edu/~jbs/resources/perl/perl-cgi/](http://www.cs.unc.edu/~jbs/resources/perl/perl-cgi/)

When working with form data, always assume that data coming from outside the program itself must be dirty and in need of 'cleaning'.  See tutorials on perl's Taint module for an advanced treatment of data.

If you work with databases, then always use [Prepared statements](https://dev.mysql.com/doc/refman/5.0/en/sql-syntax-prepared-statements.html) with place holders.  That will help protect against injection attacks and in many cases will speed performance.

---

### Post by imran042 on 2012-05-03
where is the cgi-bin located, or how do i find that it is there or not.

---

### Post by imran042 on 2012-05-03
where is the cgi-bin located, or how do i find that it is there or not.
i am using ubuntu 11.04

---

### Post by Lars Noodén on 2012-05-03
Ah.  You'll want to first familiarize yourself with [virtual hosts](https://httpd.apache.org/docs/2.2/vhosts/).  Apache2 is configured from the beginning with the intention that you might have more than one virtual host starting out.  

If you have the default settings you'll find one virtual host configuration file in /etc/apache2/sites-available under the name 'default'.  If you look in that, you'll see [ScriptAlias](https://httpd.apache.org/docs/2.2/mod/mod_alias.html#scriptalias).  By default that points to /usr/lib/cgi-bin where you can put your scripts.  

You might want to keep a terminal open with the error log open:

```

tail -f /var/log/apache2/error.log

```

That will help with debugging the scripts.

---

### Post by Lars Noodén on 2012-05-03
Also, you might need to set directory permissions so that you can write.  If it is just you by yourself on the machine, it is enough that you take ownership of the directory.

```

sudo chown -R imran042 /usr/lib/cgi-bin

```

If you are sharing with several colleagues, then you'll need to use groups.

```

# do once:
sudo addgroup webmasters

sudo chgrp -R webmasters /var/www

sudo find /var/www -type d -exec chmod g=rwxs "{}" \;
sudo find /var/www -type f -exec chmod g=rws "{}" \;

sudo gpasswd --add imran042 webmasters
sudo gpasswd --add colleague1 webmasters
sudo gpasswd --add colleague2 webmasters
# etc.

```

---

