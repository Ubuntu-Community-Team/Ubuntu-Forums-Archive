---
title: "Apache2 + Perl"
date: 2006-12-05
forum: Server Platforms
---

### Post by nhandler on 2006-12-05
I am trying to get Perl working with Apache2. I am capable of getting them both working on their own, but I can't get them to work together. By work together, I mean being able to go to [http://localhost/myscript.pl](http://localhost/myscript.pl) and having it execute myscript.pl instead of prompting to download it. Could someone please give me a hand?

P.S. I'm running Edgy

---

### Post by adamkane on 2006-12-05
This one is not well documented, but you may find the info here:
[http://ubuntuforums.org/showthread.php?t=16578](http://ubuntuforums.org/showthread.php?t=16578)
[http://wiki.bestpractical.com/index.cgi?UbuntuInstallGuide](http://wiki.bestpractical.com/index.cgi?UbuntuInstallGuide)

Please, please, tell us how you got it working.

I'll then post the info here:
[http://doc.gwos.org/index.php/ServerGuide](http://doc.gwos.org/index.php/ServerGuide)

---

### Post by houstonbofh on 2006-12-06
I have done this, but I can't remember how...  First, where is the script?  Also, you may need this in your apache2.conf...
> # To use CGI scripts outside /cgi-bin/:
#
AddHandler cgi-script .cgi

# To use server-parsed HTML files
#
<FilesMatch "\.shtml(\..+)?$">
    SetOutputFilter INCLUDES
</FilesMatch>

---

### Post by nhandler on 2006-12-06
> **houstonbofh said:**
> I have done this, but I can't remember how...  First, where is the script?  Also, you may need this in your apache2.conf...

Wouldn't that just make .shtml files work? Also, I have the AddHandler cgi-script .cgi .pl thing in the conf file. The location of the file is in the /var/www folder. If needed, I could put them in the cgi-bin, but I prefer them in the /var/www folder.

---

### Post by houstonbofh on 2006-12-07
Been banging my head a while today.  Go to /etc/sites-available/default and change/add         <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews +Includes
                AllowOverride None
                Order allow,deny
                allow from all
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                #RedirectMatch ^/$ /apache2-default/
                AddType text/html .shtml
                AddOutputFilter INCLUDES .shtml
        </Directory>
        <Directory "/var/www/calendar">
                AllowOverride None
                Options +ExecCGI +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

The calander app is all perl.

---

### Post by nhandler on 2006-12-07
It still didn't work. I think I need to add something to the conf file telling the server that .pl is a perl script.

---

### Post by houstonbofh on 2006-12-08
> **Cheater said:**
> It still didn't work. I think I need to add something to the conf file telling the server that .pl is a perl script.
Is the perl script marked executable?

---

### Post by nhandler on 2006-12-08
> **houstonbofh said:**
> Is the perl script marked executable?

Yes, it is marked as executable.

---

### Post by houstonbofh on 2006-12-08
Post your default /etc/apache2/sites-available here.  And the path you are trying to run.

---

### Post by MJN on 2006-12-09
A daft question perhaps, but have you got the Perl Apache module installed?

Mathew

---

### Post by nhandler on 2006-12-09
Here is /etc/apache2/sites-available/default
> NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews +Includes +ExecCGI +SymLinksIfOwnerMatch
		AllowOverride None
		Order allow,deny
		allow from all
		# Uncomment this directive is you want to see apache2's
		# default start page (in /apache2-default) when you go to /
		#RedirectMatch ^/$ /apache2-default/
		AddType text/html .shtml
		AddOutputFilter INCLUDES .shtml
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined
	ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>


I am not sure about the perl apache module. How do I install it (to be on the safe side)

---

### Post by MJN on 2006-12-09
sudo a2enmod perl

(Then restart Apache)

Mathew

---

### Post by nhandler on 2006-12-09
> **MJN said:**
> sudo a2enmod perl

(Then restart Apache)

Mathew

It says that this module is already enabled.

---

### Post by houstonbofh on 2006-12-10
Now where in the real server path is the file you are trying to run?  Can you run it from the command line?

---

### Post by nhandler on 2006-12-10
The file is located at /var/www/hello.pl
That should be the root of the server

I am able to run it from the terminal by typing: perl /var/www/hello.pl

Here is the script:

```
#!/usr/bin/perl
print "Hello Word";
```

---

### Post by houstonbofh on 2006-12-10
> **Cheater said:**
> The file is located at /var/www/hello.pl
That should be the root of the server

I am able to run it from the terminal by typing: perl /var/www/hello.pl

Here is the script:

```
#!/usr/bin/perl
print "Hello Word";
```
type "cp hello.pl hello.cgi" and try "http://server/hello.cgi"

PS: My test-perl.cgi is below.
> #!/usr/bin/perl

print "Content-type: text/html\n\n";
print "Yes, the perl script ran ! \n";



---

### Post by nhandler on 2006-12-10
> **houstonbofh said:**
> type "cp hello.pl hello.cgi" and try "http://server/hello.cgi"

PS: My test-perl.cgi is below.

I got it to work!!! I used your cgi script (although I think it will work with any script as long as I print the content-type) and chmod 777. The 777 part probably wasn't needed. I probably could have just used chmod +x. I then attempted to copy that cgi file to a pl file. That file wouldn't work (even with chmod 777). I probably can set some alias to treat .pl like .cgi, but I'm not going to worry about that right now.

Thanks soooo much for all the help.

---

### Post by houstonbofh on 2006-12-11
<Takes Bow>
Any time. :D

---

