---
title: "Apache SSL Certificate Config"
date: 2015-01-20
forum: Server Platforms
---

### Post by scott.bouch on 2015-01-20
Hi all,

I've got[ www.scottbouch.com]("http://www.scottbouch.com") live now after getting ddclient working, however, peoples browsers display security warnings that you have to accept to see the site, so after some research, I now think it's SSL certificate time..

So I bought an SSL certificate (hoping it is the fix to the issues) from GoDaddy as they have a special offer on of less than £5.00 for a 12 month certificate.
[I]
**My system: **Ubuntu Server 14.04, standard LAMP install including Apache2.[/I]

I went through the process of getting Apache to generate the key, I cut and paste this to GoDaddy's website, whereupon they aproved my request and issued me with two **.crt** files with some seemingly random hexadecimal filenames. Lovely so far, I thought.

Now I have the issue of getting the certificate files and key file into the right directory, and configuring Apache to know where they are.

I've read and followed a lot of guidance (with a few variables regarding file names and directories) on the internet, but just can't quite seem to get the last 1% sorted... [GoDaddy's guidance for Apache]("https://support.godaddy.com/help/article/5238/installing-an-ssl-certificate-in-apache-centos?countrysite=uk") is not much help, as it explicitly states "Not for Ubuntu", CentOS only...


***Current file locations and names:***

The **.key** file is in **/etc/apache2/scottbouch.key** (this is where Apache outputted it to).
Both **.crt** files are in** /etc/apache2/sites-enabled/ **(this is where one guide I read said to put the certificate files).

```

scott@6FC:/etc/apache2/sites-enabled$ ls
000-default.conf  6e1709ae5902a152.crt  gd_bundle-g2-g1.crt

```


***Config File:***

My **/etc/apache2/sites-enabled/** config file is called **000-default.conf** as you can see above. This is what Apache named it. Should this filename contain my domain name, as I've seen on some websites?

The file's contents, I added my server's actual local IP address against VirtualHost (In the hope that that was correct), and then added the lines below DocumentRoot:

```

  GNU nano 2.2.6                             File: 000-default.conf                                                                 

<VirtualHost 192.168.1.50:80>
        # The ServerName directive sets the request scheme, hostname and port that
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For the default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.
        #ServerName www.example.com

        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/html
        SSLEngine on
        SSLCertificateFile /etc/apache2/sites-enabled/6e1709ae5902a152.crt
        SSLCertificateKeyFile /etc/apache2/scottbouch.key
        SSLCertificateChainFile /etc/apache2/sites-enabled/gd_bundle-g2-g1.crt

        # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
        # error, crit, alert, emerg.

```


***Questions:***

Any advice on the most suitable directory / directories for the files to go? Or are they ok?

Do I rename the files something like "**scottbouch.com.csr**" and something similar for the bundle file, or leave the names as they are as the long hexadecimal names? (I only ask as other websites advice seems to have files named after the domain).

Is there an obvious error in my config file?

Many thanks in advance, Scott.

---

### Post by darkod on 2015-01-20
You can keep the files where ever you want. As long as you put the correct path in the config file, it doesn't care. So use a location that is best for you. The same applies to filenames. I would rename the files to suit the domain, that way you avoid confusion for the future too.

I'm not apache expert but I wouldn't use the private IP in the conf file. You serve on public IP (or through NAT) so the private IP has no relevance. You can also use * to replace any IP, so it would be like:
VirtualHost *:80

Also, are you sure only port 80 should be there? Standard port for https is 443. However I'm rusty on Apache so I will have to google if that means two separate config files, one for 80 and one for 443 (or one file with two separate sets of VirtualHost).

And of course, you have to restart apache after any change in conf.

---

### Post by SeijiSensei on 2015-01-20
The default SSL site is stored in /etc/apache2/sites-available/default-ssl.conf.  You should modify that one instead.  You'll see the various SSL declarations and the default certificate locations in that file as well.

You'll see that the virtual host is defined by a stanza that begins:
```

<VirtualHost _default_:443>

```
For more on the "_default_" host, see [http://httpd.apache.org/docs/2.4/vhosts/examples.html#default](http://httpd.apache.org/docs/2.4/vhosts/examples.html#default).

---

### Post by CharlesA on 2015-01-20
Assuming he is using ddclient, which means he is hosting this on a dynamic IP, so a private IP in the config file should be fine.

You need apache listening on port 443 to do SSL (HTTPS), and right now all you have it set to is listen on port 80.

---

### Post by darkod on 2015-01-20
Also if I'm not mistaken, the line for the CA cert should be SSLCACertificateFile, not SSLCertificateChainFile.

Did GoDaddy sent you only one CA file? Usually they can be 2 or even 3. Just few days ago I had a case of 3 chained certificates for CA but it was Comodo cert through Namecheap. Plus the domain certificate of course. So there were 4 files sent by Namecheap.

If you are missing a chain cert the warning message is normal because it needs the whole CA chain to work perfect.

Also take a quick look at this linode guide, you have done most of the work already. Try filling any gaps. Note how they say :443 and not :80.
[https://www.linode.com/docs/security/ssl/ssl-certificates-with-apache-2-on-ubuntu](https://www.linode.com/docs/security/ssl/ssl-certificates-with-apache-2-on-ubuntu)

---

### Post by CharlesA on 2015-01-20
Instructions for installing a GoDaddy SSL cert into Apache are on their site but are specific to CentOS, you can just substrute httpd.conf for your virtualhost confguration.
[https://support.godaddy.com/help/article/5238/installing-an-ssl-certificate-in-apache-centos](https://support.godaddy.com/help/article/5238/installing-an-ssl-certificate-in-apache-centos)

You can also test your site at sslabs to make sure everything is set up correctly: [http://ssllabs.com/](http://ssllabs.com/)

---

### Post by scott.bouch on 2015-01-20
Dudes, 

Thank you so much for the quick, and detailed replies!

I'll sit down now and have a look through your links and comments to see where I can improve my setup.

The SSLLABS website is great I've FAILED the SSL test! But it's great ss I'm home-hosting I can't view my website publicly due to loopback, so have been using my company's laptop on a VPN connection to our office servers to view my website and use mu browser o see certificate information!

Now, As my website is only just a hobby type site, do I need HTTPS / port 443? Is HTTP / port 80 enough? Or is it just good practice these days to go HTTPS if you can?

Please forgive the begginner-ish questions!

Cheers, Scott.

---

### Post by CharlesA on 2015-01-20
My site is set up to be accessible over https but I figured I might as well set it up as I already have the SSL cert.

Regular HTTP traffic has less overhead than HTTPS traffic, so you can use regular HTTP unless you are doing things like logging in or accessing email - those things should be done via HTTPS.

---

### Post by scott.bouch on 2015-01-20
From what you've said, I think I'll go down the https route, as I do hope to have a stab at mail server too at some point.


***My story from Midnight to 1:00am:***

I've made some changes to my config file following the advice here... Thanks for the pointers about SSLCACertificateFile etc..

```

  GNU nano 2.2.6                             File: 000-default.conf                                                                 

<VirtualHost 192.168.1.50:443>
        # The ServerName directive sets the request scheme, hostname and port that
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For the default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.
        #ServerName www.example.com

        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/html
        SSLEngine on
        SSLCertificateFile /etc/apache2/sites-enabled/6e1709ae5902a152.crt
        SSLCertificateKeyFile /etc/apache2/scottbouch.key
        SSLCACertificateFile /etc/apache2/sites-enabled/gd_bundle-g2-g1.crt

        # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
        # error, crit, alert, emerg.

```
[B]
Restarting Apache[/B] gave this error, may be a clue:

```

scott@6FC:/etc/apache2/sites-enabled$ sudo service apache2 restart
 * Restarting web server apache2
AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1. Set the 'ServerName' directive globally to suppress this message
[Wed Jan 21 00:32:58.111893 2015] [core:error] [pid 12022] (EAI 2)Name or service not known: AH00549: Failed to resolve server name for 192.168.1.50 (check DNS) -- or specify an explicit ServerName

```

**SSL Labs test result:** Assessment failed: No secure protocols supported

So Now I've edited 000-default.conf to remove my local IP address, to look like this, as suggested:

```

<VirtualHost _default_:443>

```

**Restarting Apache** gives me slightly less of an error message, who knows, maybe slightly less of an error!:
```

scott@6FC:/etc/apache2/sites-enabled$ sudo service apache2 restart
 * Restarting web server apache2
AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1. Set the 'ServerName' directive globally to suppress this message

```

Well, I was wrong..
[B]
SSL Labs test result: [/B]Assessment failed: No secure protocols supported

**AND I've got another issue -** just viewed my website via my work VPN connection, and I'm presented with an "Index Of /" screen, a bit like an FTP web interface. It shows the html directory and info.php, which are parts of my website, but is not rendering it. Below the FTP style file browser view, a line says: [SIZE=4][FONT=times new roman]*Apache/2.4.7 (Ubuntu) Server at [www.scottbouch.com]("http://www.scottbouch.com") Port 80*[/FONT][/SIZE]   - Please visit [www.scottbouch.com]("http://www.scottbouch.com") to see this. When I click into the folder and open my index.html, it does render, but not linked to my css... hmmm.. it WAS fine before I decided to get an SSL cert...

I've double checked my directories and file names for typos, and everything seems to be in order... I only am curious as I've seen different filenames for **000-default.conf** used on different guides, would Apache be looking for a file with this specific name for it's config settings (or just any file of.conf type in the right directory?), could it be that it has the wrong name? But it was created by Apache, AND I'm seeing a different error after making edits to the file, so maybe not.. Please let me know if I'm barking up the wrong tree...

Sorry to have come back with more questions... It's doing my head in now, but we all have to learn somewhere..

I REALLY appreciate the kind help people have given, and do hope I'm not pushing my luck asking for a tad more...

Thanks, Scott

---

### Post by CharlesA on 2015-01-20
That's an informational message from Apache.

You need to forward port 443 on your router to expose it to the internet.

Otherwise it won't be accessible via HTTPS.

---

### Post by scott.bouch on 2015-01-20
Good work Charles,  sorry for being a numpty...

I've just set up the https port forward... any chance you could please check my site for me? (In bed now you see!)

when you are learning, it seems like one brick wall after another, but it is the best way to learn and become more familiar ...

Thanks,  Scott

---

### Post by CharlesA on 2015-01-20
Looks like it's accessible via https. I do get a message saying the site is only partially encrypted, but I'm not sure if that's due to what you are hosting or something else.

My site gives me a nice padlock icon. [https://charlesauer.net/](https://charlesauer.net/)

The regular http version gives you a directory list with an info.php file. You should either remove that file or disable directory indexing.

---

### Post by scott.bouch on 2015-01-20
Holy Cow!

We've. Just passed the SSL test! Woohoo! Grade C, apparently I'm open to poodle attack, which has made me smile at 2;30am! that's a job for another day ...

Thanks to everyone's help on this, a great team effort!

---

### Post by CharlesA on 2015-01-21
Looks like SSLv3 is enabled by default. You also have an extra certificate somewhere in your config, but I don't think it'll mess anything up.

Have a read:
[https://raymii.org/s/tutorials/Strong_SSL_Security_On_Apache2.html](https://raymii.org/s/tutorials/Strong_SSL_Security_On_Apache2.html)
[https://cipherli.st/](https://cipherli.st/)

---

### Post by scott.bouch on 2015-01-21
Fixed a couple of issues....

I had the same issue locally (similar as I experienced last night over work VPN connection), when I browsed to my servers local IP address "192.168.1.50", I get the directory list, and when I browse to "https://192.168.1.50" I got Firefoxes security warnings and had to sign my life away just to see my website locally on my own network..

When I did get to my site, the header and menu were not displayed. These are separate HTML files on my server called up by JQuery, I've just fixed this by changing the link to the googleapi JQuery script in my html header from http:// to https:// - so all my site's linked elements are now https:// apart from a couple of linked images. Now Firefox is happier about security.

> **CharlesA said:**
> The regular http version gives you a directory  list with an info.php file. You should either remove that file or  disable directory indexing.

Thanks, I've disabled directory indexing, so it should no longer appear when you visit http:// . Now you get:*[SIZE=4][FONT=times new roman] Forbidden you don't have permission to access / on this server. Apache/2.4.7 (Ubuntu) Server at [www.scottbouch.com]("http://www.scottbouch.com") Port 80[/FONT][/SIZE]*

***RESULTS:***

YIPPEE!! Just viewed my site on my work VPN and rendered correctly!

***Last question regarding viewing the https:// site:***

Do I need to port forward :80 to :443 in my router to redirect http:// requests to https:// or is there a setting in Apache to achieve this? I can't gve someone [www.scottbouch.com]("http://www.scottbouch.com") and have them see the Forbidden page..

[B][I]POODLE:
[/I][/B]
> **CharlesA said:**
> Looks like SSLv3 is enabled by default.

I've just added "SSLProtocol All -SSLv2 -SSLv3" to my config file, and now score a whopping **B** on SSLLabs.com!!! Thanks for the tip.

Got to say, a big thank-you to all help, especially the posts by CharlesA, not only is it good to have fixed my problems, but you've given me more confidence to try a few fixes before just asking more questions, hence me fixing the things detailed in this post!

Thanks again, Scott.

---

### Post by scott.bouch on 2015-01-21
I've just had a stab at mod_rewrite to guide http:// requests to https:// ..

What I've done hasn't worked... This is what I've done:

I have created this file (.htaccess in the same folder as my website's .html and .css files):

```

  GNU nano 2.2.6                               File: .htaccess                                                                      

Rewrite Engine On
RewriteCond %{HTTPS} off
RewriteRule (.*) https://%{HTTP_HOST}%{REQUEST_URI}

```

I've enabled mod_rewrite with "a2enmod rewrite" at the command line, then restarted apache2. (followed this guide: [https://www.sslshopper.com/apache-redirect-http-to-https.html](https://www.sslshopper.com/apache-redirect-http-to-https.html), and a bit of this: [http://stackoverflow.com/questions/869092/how-to-enable-mod-rewrite-for-apache-2-2](http://stackoverflow.com/questions/869092/how-to-enable-mod-rewrite-for-apache-2-2))

I still get the *[SIZE=4][FONT=times new roman]Forbidden[/FONT][/SIZE]* webpage when I visit my site without https://

Any ideas now?

Thanks, Scott.

---

### Post by CharlesA on 2015-01-21
> **scott.bouch said:**
> Fixed a couple of issues....

I had the same issue locally (similar as I experienced last night over work VPN connection), when I browsed to my servers local IP address "192.168.1.50", I get the directory list, and when I browse to "https://192.168.1.50" I got Firefoxes security warnings and had to sign my life away just to see my website locally on my own network..

When I did get to my site, the header and menu were not displayed. These are separate HTML files on my server called up by JQuery, I've just fixed this by changing the link to the googleapi JQuery script in my html header from http:// to https:// - so all my site's linked elements are now https:// apart from a couple of linked images. Now Firefox is happier about security.



Thanks, I've disabled directory indexing, so it should no longer appear when you visit http:// . Now you get:*[SIZE=4][FONT=times new roman] Forbidden you don't have permission to access / on this server. Apache/2.4.7 (Ubuntu) Server at [www.scottbouch.com]("http://www.scottbouch.com") Port 80[/FONT][/SIZE]*

***RESULTS:***

YIPPEE!! Just viewed my site on my work VPN and rendered correctly!

***Last question regarding viewing the https:// site:***

Do I need to port forward :80 to :443 in my router to redirect http:// requests to https:// or is there a setting in Apache to achieve this? I can't gve someone [www.scottbouch.com]("http://www.scottbouch.com") and have them see the Forbidden page..

[B][I]POODLE:
[/I][/B]


I've just added "SSLProtocol All -SSLv2 -SSLv3" to my config file, and now score a whopping **B** on SSLLabs.com!!! Thanks for the tip.

Got to say, a big thank-you to all help, especially the posts by CharlesA, not only is it good to have fixed my problems, but you've given me more confidence to try a few fixes before just asking more questions, hence me fixing the things detailed in this post!

Thanks again, Scott.

The B is because you are still using weak ciphers. The site I linked to earlier will tell you how to set Apache up to use a strong cipher suite.

> **scott.bouch said:**
> I've just had a stab at mod_rewrite to guide http:// requests to https:// ..

What I've done hasn't worked... This is what I've done:

I have created this file (.htaccess in the same folder as my website's .html and .css files):

```

  GNU nano 2.2.6                               File: .htaccess                                                                      

Rewrite Engine On
RewriteCond %{HTTPS} off
RewriteRule (.*) https://%{HTTP_HOST}%{REQUEST_URI}

```

I've enabled mod_rewrite with "a2enmod rewrite" at the command line, then restarted apache2. (followed this guide: [https://www.sslshopper.com/apache-redirect-http-to-https.html](https://www.sslshopper.com/apache-redirect-http-to-https.html), and a bit of this: [http://stackoverflow.com/questions/869092/how-to-enable-mod-rewrite-for-apache-2-2](http://stackoverflow.com/questions/869092/how-to-enable-mod-rewrite-for-apache-2-2))

I still get the *[SIZE=4][FONT=times new roman]Forbidden[/FONT][/SIZE]* webpage when I visit my site without https://

Any ideas now?

Thanks, Scott.

You do not need to use .htaccess files if you have access to the web server configuration itself.

You can just add the directives to do the redirect to the virtual host files directly.

See here: [https://www.digitalocean.com/community/tutorials/how-to-create-temporary-and-permanent-redirects-with-apache-and-nginx](https://www.digitalocean.com/community/tutorials/how-to-create-temporary-and-permanent-redirects-with-apache-and-nginx)

---

### Post by scott.bouch on 2015-01-21
Bingo!!!! You've sorted the redirect issue, now a simple [www.scottbouch.com]("http://www.scottbouch.com") request goes to [https://www.scottbouch.com](https://www.scottbouch.com) ... Good work dude!! :)

I'll have a look later on at improving the ciphers to improve security.

This has been one big learning curve, and I'm probably only just scratching the surface! I think this time next year when I get a new SSL cert it'll be a bit more straightforward.

Thanks again, Scott.

---

### Post by guldberg72 on 2015-01-21
here comes some shameless self promotion :D i am running a ssl myself but you should create a virtual host for apache so you have one there is running on port 80 and another one at 443 and then force the website's visitors to be redirected to https instead of http.

and because you have your own SSL then just skip the first 2. steps
[http://techknight.eu/2014/11/15/create-and-setup-self-signed-ssl-apache/](http://techknight.eu/2014/11/15/create-and-setup-self-signed-ssl-apache/)

then create a .htacces file for you site and add these lines
 RewriteEngine On
 RewriteCond %{HTTPS} off
 RewriteRule (.*) https://%{HTTP_HOST}%{REQUEST_URI} 

and the apache conf. to allow override

---

### Post by CharlesA on 2015-01-21
You don't even need the .htaccess file and setting it up that way it only needed if you do not have access to the server configuration - shared hosting comes to mind.

As far as I can tell he has everything set up right with the redirect working.

FWIW, I use a separate vhost for each of my sites - main sites and subdomains. That way I can control how each is configured.

---

### Post by scott.bouch on 2015-01-22
> **CharlesA said:**
> You don't even need the .htaccess file and setting it up that way it only needed if you do not have access to the server configuration - shared hosting comes to mind.

As far as I can tell he has everything set up right with the redirect working.

FWIW, I use a separate vhost for each of my sites - main sites and subdomains. That way I can control how each is configured.

Yes, It seems to work well doing it as you suggested. I'm very happy with it. .htaccess gave me a headache!

I'm going to have to learn a bit in the future about separate vhosts as you have done, as my wife wants a small website for her business. I'd like to practice a little more with my own site, then have a go at hosting a second site for her - and a second vhost sounds like a good way to do it.

Cheers, Scott

---

### Post by scott.bouch on 2015-01-25
Hi again,

So I've had a stab at bringing my SSLLabs security rating up from a B by using the code on: [https://cipherli.st/](https://cipherli.st/) and am falling over at the first step..

The website says to copy / pase the Apache code into a config file, but it assumes I (a beginner) know which file to paste it into... The website makes it clear that this is for advanced people only, so, I don't' fancy my chances with beginner-ish questions over there.

So I had a go at pasting it into my SSL config file first, and Apache failed to restart, complaining about the lines I added from [https://cipherli.st/](https://cipherli.st/) (it didn't like the word "Header"):

```

scott@6FC:/etc/apache2/sites-enabled$ sudo nano 000-default.conf
scott@6FC:/etc/apache2/sites-enabled$ sudo service apache2 restart
 * Restarting web server apache2                                                                                             [fail] 
 * The apache2 configtest failed.
Output of config test was:
AH00526: Syntax error on line 28 of /etc/apache2/sites-enabled/000-default.conf:
Invalid command 'Header', perhaps misspelled or defined by a module not included in the server configuration
Action 'configtest' failed.
The Apache error log may have more information.

```

SO, I erased the code, restarted Apache2 again, and we're back to square 1. 

I then added the code to my apache.conf file to see if it would work there... and had much the same response...
```

scott@6FC:/etc/apache2$ sudo nano apache2.conf
scott@6FC:/etc/apache2$ sudo service apache2 restart
 * Restarting web server apache2                                                                                             [fail] 
 * The apache2 configtest failed.
Output of config test was:
AH00526: Syntax error on line 227 of /etc/apache2/apache2.conf:
Invalid command 'Header', perhaps misspelled or defined by a module not included in the server configuration
Action 'configtest' failed.
The Apache error log may have more information.

```

I've erased the code from this file too, and Apache is happy again.

Any idea where I should copy / paste this code to?

Thanks, Scott

---

### Post by CharlesA on 2015-01-26
The cipherli.st site isn't really for beginners.

Have a read here first if you haven't already: [https://raymii.org/s/tutorials/Strong_SSL_Security_On_Apache2.html](https://raymii.org/s/tutorials/Strong_SSL_Security_On_Apache2.html)

Not sure why it is complaining about the Header directive, but I'm not all that familiar with Apache. I usually use Nginx.

Revert your config back to normal and check out the site above to see if it explains anything.

I'll see if I can get Apache set up with strong ciphers when I get some time.

---

