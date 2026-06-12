---
title: "Apache2, SSL, Shared certificate"
date: 2007-11-17
forum: Server Platforms
---

### Post by drhiii on 2007-11-17
I've poured over doxs and examples and I almost have this licked, in my head that is.  Meaning am almost getting my head wrapped around this.  But let me pose the scenario anyway and hopefully someone can point me to a HOWTO that pulls it all together. 

As an FYI, this post came as close as I have found to solving the need.

[http://ubuntuforums.org/showthread.php?t=605064&highlight=ssl+apache](http://ubuntuforums.org/showthread.php?t=605064&highlight=ssl+apache)

I have multiple vhosts.  A single IP (though I could acquire more as this is on a relatively vacant Class C).  I am looking to create a single certificate that can be used by multiple sites.  The application is a front end image gallery with a backend commerce application.  The image gallery can run http but the commerce end needs to run under SSL.  I can't point the multple image galleries to a single commerce installation.  

What I am looking to do is create a single cert (wildcard??), and create in each vhost SSL for each installation, using the same cert.  Is this possible?  It would look like:

[http://123.abc.com/image](http://123.abc.com/image)     and    [https://123.abc.com/image/commerce](https://123.abc.com/image/commerce)

and

[http://456.abc.com/image](http://456.abc.com/image)     and    [https://456.abc.com/image/commerce](https://456.abc.com/image/commerce)

And so on.  As you will see, it is the same top level domain, but different virtual domains based off this single TLD.  Anyone point to a tutorial, example, HOWTO that might shed some light on this?  Or, do I need to go the multiple IP route to solve this?

tx

---

### Post by kidders on 2007-11-18
Hi there,

The point of a server-side certificate is to allow clients to verify a server's identity. A certificate cannot be used to validate more than one host.

Additionally, as you suggested, you will need multiple IPs to host more than one HTTPS service on the same machine/port.

---

### Post by frankos44 on 2007-11-18
I too had issues using a one certificate shared by more than one domain on the same server.

In the end I found it much simpler to have a common index.php page where all the domains pointed at. This page then used $_SERVER['HTTP_HOST'] to attain the domain used and then re-directed the user to the appropriate area on the web server (Take care to make sure secure parts of the software are not under the domains physical path)

Once directed any secure pages will use the secure url which also points at the same server. Effectively a funnel for all the websites on the server.

Its worth mentioning that the server hostname needs to match the secure domain name else the cert wont match up.

The advantages with this method are:

1. I don't need to play around with virtual hosts every time I add a new website
2. I only need one secure certificate for all the websites to use
3. I only need the one file in sites-available called default

Disadvantages:

All websites will use a common secure URL.

This was not a problem in my case because all the websites belonged to the same group of companies e.g.

[https://www.fredbloggsecure.com](https://www.fredbloggsecure.com)
[http://www.fredbloggscars.com](http://www.fredbloggscars.com)
[http://www.fredblogsholidays.com](http://www.fredblogsholidays.com)
[http://www.fredbloggswidgets.com](http://www.fredbloggswidgets.com)

Here is an example of "/etc/apache2/sites-available" :

NameVirtualHost *:443
NameVirtualHost *:80

<VirtualHost *:80>
        ServerName [www.fredbloggssecure.com](www.fredbloggssecure.com)
        DirectoryIndex index.php
        DocumentRoot /var/www/afolder/htdocs
        ErrorLog /var/log/apache2/error.log
        CustomLog /var/log/apache2/access.log combined
</VirtualHost>

<VirtualHost *:443>
        ServerName [www.fredbloggssecure.com](www.fredbloggssecure.com)
        DirectoryIndex index.php
        DocumentRoot /var/www/afolder/htdocs
        ErrorLog /var/log/apache2/error.log
        CustomLog /var/log/apache2/access.log combined

        SSLEngine on
        SSLOptions +FakeBasicAuth +ExportCertData +StrictRequire
        SSLCertificateFile /etc/ssl/certs/server.crt
        SSLCertificateKeyFile /etc/ssl/private/server.key
</VirtualHost>

I know its not that elegant but it sure works well.

---

### Post by drhiii on 2007-11-18
Thank you for this response.  This is essentially what I want to do... just as you described.  I will follow your model and see if I can affect this solution.  All of the sites come under one TLD anyway, so this may be the ticket.

Thankx a mil for drilling into the explanation.....

> **frankos44 said:**
> I too had issues using a one certificate shared by more than one domain on the same server.

In the end I found it much simpler to have a common index.php page where all the domains pointed at. This page then used $_SERVER['HTTP_HOST'] to attain the domain used and then re-directed the user to the appropriate area on the web server (Take care to make sure secure parts of the software are not under the domains physical path)

Once directed any secure pages will use the secure url which also points at the same server. Effectively a funnel for all the websites on the server.

Its worth mentioning that the server hostname needs to match the secure domain name else the cert wont match up.

The advantages with this method are:

1. I don't need to play around with virtual hosts every time I add a new website
2. I only need one secure certificate for all the websites to use
3. I only need the one file in sites-available called default

Disadvantages:

All websites will use a common secure URL.

This was not a problem in my case because all the websites belonged to the same group of companies e.g.

[https://www.fredbloggsecure.com](https://www.fredbloggsecure.com)
[http://www.fredbloggscars.com](http://www.fredbloggscars.com)
[http://www.fredblogsholidays.com](http://www.fredblogsholidays.com)
[http://www.fredbloggswidgets.com](http://www.fredbloggswidgets.com)

Here is an example of "/etc/apache2/sites-available" :

NameVirtualHost *:443
NameVirtualHost *:80

<VirtualHost *:80>
        ServerName [www.fredbloggssecure.com](www.fredbloggssecure.com)
        DirectoryIndex index.php
        DocumentRoot /var/www/afolder/htdocs
        ErrorLog /var/log/apache2/error.log
        CustomLog /var/log/apache2/access.log combined
</VirtualHost>

<VirtualHost *:443>
        ServerName [www.fredbloggssecure.com](www.fredbloggssecure.com)
        DirectoryIndex index.php
        DocumentRoot /var/www/afolder/htdocs
        ErrorLog /var/log/apache2/error.log
        CustomLog /var/log/apache2/access.log combined

        SSLEngine on
        SSLOptions +FakeBasicAuth +ExportCertData +StrictRequire
        SSLCertificateFile /etc/ssl/certs/server.crt
        SSLCertificateKeyFile /etc/ssl/private/server.key
</VirtualHost>

I know its not that elegant but it sure works well.

---

### Post by drhiii on 2007-11-18
Oh, one other question... other than the ../sites-available/vhostname file,  are there any required tweaks to any other files like ports.conf, or other?  And am repeating here, but you are running multiple vhosts under this single certificate yes?  So each ../sites-availabe/vhostnameA, ../sites-availabe/vhostnameB, and so on looks pretty much the same except for the domain entries?

tx





> **frankos44 said:**
> I too had issues using a one certificate shared by more than one domain on the same server.

In the end I found it much simpler to have a common index.php page where all the domains pointed at. This page then used $_SERVER['HTTP_HOST'] to attain the domain used and then re-directed the user to the appropriate area on the web server (Take care to make sure secure parts of the software are not under the domains physical path)

Once directed any secure pages will use the secure url which also points at the same server. Effectively a funnel for all the websites on the server.

Its worth mentioning that the server hostname needs to match the secure domain name else the cert wont match up.

The advantages with this method are:

1. I don't need to play around with virtual hosts every time I add a new website
2. I only need one secure certificate for all the websites to use
3. I only need the one file in sites-available called default

Disadvantages:

All websites will use a common secure URL.

This was not a problem in my case because all the websites belonged to the same group of companies e.g.

[https://www.fredbloggsecure.com](https://www.fredbloggsecure.com)
[http://www.fredbloggscars.com](http://www.fredbloggscars.com)
[http://www.fredblogsholidays.com](http://www.fredblogsholidays.com)
[http://www.fredbloggswidgets.com](http://www.fredbloggswidgets.com)

Here is an example of "/etc/apache2/sites-available" :

NameVirtualHost *:443
NameVirtualHost *:80

<VirtualHost *:80>
        ServerName [www.fredbloggssecure.com](www.fredbloggssecure.com)
        DirectoryIndex index.php
        DocumentRoot /var/www/afolder/htdocs
        ErrorLog /var/log/apache2/error.log
        CustomLog /var/log/apache2/access.log combined
</VirtualHost>

<VirtualHost *:443>
        ServerName [www.fredbloggssecure.com](www.fredbloggssecure.com)
        DirectoryIndex index.php
        DocumentRoot /var/www/afolder/htdocs
        ErrorLog /var/log/apache2/error.log
        CustomLog /var/log/apache2/access.log combined

        SSLEngine on
        SSLOptions +FakeBasicAuth +ExportCertData +StrictRequire
        SSLCertificateFile /etc/ssl/certs/server.crt
        SSLCertificateKeyFile /etc/ssl/private/server.key
</VirtualHost>

I know its not that elegant but it sure works well.

---

### Post by frankos44 on 2007-11-19
Hi, im glad to be of assistance.

Points to bear in mind when doing things this way:

Certificate:
You will need to install the certificate in the normal way. I assume you have a copy of the Ubuntu server documentation

Server:
The server hostname must match the SSL domain name.  Essentially this is the only website you need configure on the server. Install the certificate, replace default in sites-available and thats it. Other domains simply point at the same IP address. Don't forget that I used index.php as mentioned earlier to decipher which domain was used and under program control transferred to the correct website rather than using virtual hosts.

Emails:
All emails will be sent from the secure domain when using Postfix.

Links:
Links to secure pages use full url strings including path even if page resides in the same folder as the non-secure site.  e.g.  [https://www.fredbloggssecure/requestCallback.php](https://www.fredbloggssecure/requestCallback.php)

Sessions:
All sessions variables in PHP (assuming you are using sessions) will be unavailable to the secure page as you would expect. If you are using POST or GET when calling the secure page the data sent is NOT secure.  Only pages  rendered from https are secure. I highly recommend you do not send the session ID across to the secure page in an attempt to keep all your session variables as this is asking for SESSION hi-jacking!

Returning back from secure server::
This is a little bit more complicated to do. I like simplicity so I fire-up another browser instance for secure pages. Once the fired-up page is closed the original website is still intact underneath together with all its session variables intact as before. You can use javascript to change the page on the original website when clicking the secure link if you so wish. 

You can see my working example on [www.youngmarmalade.co.uk](www.youngmarmalade.co.uk)

Have fun!

---

### Post by drhiii on 2007-11-20
Hello!

All points understood.  Thank you for taking this time to articulate these out.  I do have certs installed.   Matches domain name.  One interesting thing I am working through is the self signed cert only works so far in Konqueror.  Can't get it to work in Opera or Firefox.  Odd.  

But understand the need for PHP calls al the way through secure pages, etc.  

And, very cool site:  youngmarmalade.co.uk   Has a great feel to it all the way through.  Very nice.

Again, tx for the responses.  If you have a thought about self seigned certs being moody with browsers, that is where I am at the moment....

regards



> **frankos44 said:**
> Hi, im glad to be of assistance.

Points to bear in mind when doing things this way:

Certificate:
You will need to install the certificate in the normal way. I assume you have a copy of the Ubuntu server documentation

Server:
The server hostname must match the SSL domain name.  Essentially this is the only website you need configure on the server. Install the certificate, replace default in sites-available and thats it. Other domains simply point at the same IP address. Don't forget that I used index.php as mentioned earlier to decipher which domain was used and under program control transferred to the correct website rather than using virtual hosts.

Emails:
All emails will be sent from the secure domain when using Postfix.

Links:
Links to secure pages use full url strings including path even if page resides in the same folder as the non-secure site.  e.g.  [https://www.fredbloggssecure/requestCallback.php](https://www.fredbloggssecure/requestCallback.php)

Sessions:
All sessions variables in PHP (assuming you are using sessions) will be unavailable to the secure page as you would expect. If you are using POST or GET when calling the secure page the data sent is NOT secure.  Only pages  rendered from https are secure. I highly recommend you do not send the session ID across to the secure page in an attempt to keep all your session variables as this is asking for SESSION hi-jacking!

Returning back from secure server::
This is a little bit more complicated to do. I like simplicity so I fire-up another browser instance for secure pages. Once the fired-up page is closed the original website is still intact underneath together with all its session variables intact as before. You can use javascript to change the page on the original website when clicking the secure link if you so wish. 

You can see my working example on [www.youngmarmalade.co.uk](www.youngmarmalade.co.uk)

Have fun!

---

### Post by frankos44 on 2007-11-21
Hi

I only have self signed certs here for testing locally but not on the live server of course.

I noticed that  got a 2 stage process of warning dialogs when I got the 'Common Name' wrong in the self signed cert. 

Firstly warning of the certificate being self-signed and after accepting that  yet another saying the that the domain did not match and "Blah blah blah"

I test with mozilla but I wonder if opera dosent like that. if this is the case make sure that the domain matches "Common Name" when creating the cert.

On my local server (my desktop ubuntu 7.10)  i set this to localhost as it cannot determine a fully qualified domain name when apache starts, on the live server it is set to mydomainname.co.uk

I would be interested if this may related to your problem.

---

### Post by drhiii on 2007-11-21
Than you for this response.   I have been mindful of the domain name as it relates to Common Name yes.  At first I tried the wildcard convention of *.123.com and it doesn't like to play nice.  Then I have tested with the fully qualified name as in   abc.123.com and that doesn't play nice either.  It will in Konqueror, but not Opera or Firefox.  This latter surprised me as I felt if Konqueror worked, certainly Firefox would be as forgiving, but no.  Am sure the problem lies in this area as you rightfully point out.  I will continue working with these names to see if I can discover the formula.  Am sure there are many who read this thinking "dude, it isn't that difficult."  But for the life of me I can't get the behavior to be consistent.  I do believe tho it is in the name/Common Name area.

If you have any other ideas, be most grateful to hear them of course.  

regards

---

### Post by drhiii on 2007-11-21
Oh, and the interesting thing is all browsers accept the self signed certs that Webmin chruns out!!  So I know it is in the syntax somewhere...

---

