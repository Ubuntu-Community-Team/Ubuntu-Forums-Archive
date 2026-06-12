---
title: "Foswiki Perl CGI setup"
date: 2011-04-04
forum: Server Platforms
---

### Post by MikeyDL on 2011-04-04
Been trying to setup Foswiki but having the hardest time setting up perl cgi.  My main source of info is an ubuntugeeks.com article:

[http://www.ubuntugeek.com/how-to-install-apache2-webserver-with-phpcgi-and-perl-support-in-ubuntu-server.html]("http://www.ubuntugeek.com/how-to-install-apache2-webserver-with-phpcgi-and-perl-support-in-ubuntu-server.html")

I'm not just having a problem with Foswiki setup but also just getting a simple perl CGI script to execute in apache2.  I"ve been googling and researching the issue for about a week without much sucess so i thought I'd layout the basics steps I've been going through and see if anyone can see some basic or missing steps.

Basically I've done the following:

1.  Installed Apache2

2.   PHP already installed (php -v gives PHP 5.3.3)

3.   Perl already installed (perl -v give PERL version 5.10.1)

4.  Installed "php5 libapache2-mod-php5"

5.  Edited /ect/apache2/apache2.conf and added "ServerName localhost" at bottom (from UG guide)

6.  Tested php installation with "phpinfo()" test (it worked fine)

7.  Started to configure a cgi-bin directory (such as "/var/www/cgi-bin") but decided to keep it simple and just put the script into "/usr/lib/cgi-bin".  

8.  There is already a ScriptAlias setup for /usr/lib/cgi-bin so left that alone.

Pastbin of [/etc/apache2/sites-available/default]("http://pastebin.ubuntu.com/589395/") 

Pastebin of [/etc/apache2/apache2.conf]("http://pastebin.ubuntu.com/589396/")

9.  Created a perltest.pl file which is pretty much a HelloWorld type output.

```
###Start###

#!/usr/bin/perl -w:
print "Content-type: text/html\n";
print "Hello there!<br />\nJust testing .<br />\n";
###End###:
```

10.  Changed perms on the pertest to rx with ```
sudo chmod a+x perltest.pl
```

11.  when I run [http://loaclahost/cgi-bin/perltest.pl](http://loaclahost/cgi-bin/perltest.pl) I get a 500 error.  The output for the /var/log/apache2/error.log is as follows:

```
[Sun Apr 03 07:53:45 2011] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.3 with Suhosin-Patch mod_perl/2.0.4 Perl/v5.10.1 configured -- resuming normal operations
[Mon Apr 04 08:53:19 2011] [error] [client 127.0.0.1] (8)Exec format error: exec of '/usr/lib/cgi-bin/perltest.pl' failed
[Mon Apr 04 08:53:19 2011] [error] [client 127.0.0.1] Premature end of script headers: perltest.pl
[Mon Apr 04 09:26:13 2011] [error] [client 127.0.0.1] (8)Exec format error: exec of '/usr/lib/cgi-bin/perltest.pl' failed
[Mon Apr 04 09:26:13 2011] [error] [client 127.0.0.1] Premature end of script headers: perltest.pl
[Mon Apr 04 09:26:16 2011] [error] [client 127.0.0.1] (8)Exec format error: exec of '/usr/lib/cgi-bin/perltest.pl' failed
[Mon Apr 04 09:26:16 2011] [error] [client 127.0.0.1] Premature end of script headers: perltest.pl
```

I've run the scrip with perl-wc perltest.pl and no errors returned.  

Figure I'm doing some thing basic wrong with the cgi-setup that I haven't been able to pickup yet.  

FOSWIKI

With regards to Foswiki they have a foswiki.conf which is pregenerated which I edited

PASTEBIN of [foswiki.conf]("http://pastebin.ubuntu.com/589399/")

I got a little clever and figured out that maybe adding the foswiki.conf in the include section of apacahe2.conf was the way to go.  

However when I run the basic [https://localhost/foswiki/bin/configure](https://localhost/foswiki/bin/configure) page I get the script just dumping as a test page in the browser.  So I figure I still don't have it setup to execute correctly, I'm guessing I need to add a ScriptAlias into sites-available default.  

Foswiki setup info does have you setup permissions for the directory with the following ```
chown -R www-data:www-data /var/www/foswiki
```.

Any help or tips on setup sure would be appreciated.

---

### Post by MikeyDL on 2011-04-05
Okay so making progress here.  

I was using a perltest example from 2009 which had two basic lines:

```
print "Content-type: text/html\r\n\r\n";
print "Hello there!<br />\nJust testing .<br />\n";
```

which was giving the 500 errors.  Looking at some other code samples I replace that with:

```
use CGI qw(:standard escapeHTML);
print header( ), start_html("Howdy there!"),
      p("Hello World"),
      end_html( );

```

Which runs and doesn't give the 500 error messages.  I'm taking it that apache2 is more strict with the HTML setup on the basic page adn that a simple "Content-type: text/html" doesn't cut it anymore?

Also with regards to foswiki they have you generate a foswiki.conf file.  I've edited that file and added that in an include section of the apache2.conf (httpd.conf is blank).  Would this be correct.  

Also above I displayed my ScriptAlias for the /etc/apache2/sites-available/default file to try and get the script to run as perl code as opposed to a text dump.  I noticed that the scripts don't have a .pl extension in the foswiki/bin directory.  They are exe permed (i.e. green) but is the a special parameter you need to setup in the ScriptAlias section to get them to parse as code?

Thanks!

---

