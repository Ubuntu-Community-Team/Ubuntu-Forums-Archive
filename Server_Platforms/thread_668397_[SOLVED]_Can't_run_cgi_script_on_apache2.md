---
title: "[SOLVED] Can't run cgi script on apache2"
date: 2008-01-15
forum: Server Platforms
---

### Post by marco81 on 2008-01-15
Hi everibody,
I can't run cgi scripts under apache2.
I added the following lines in /etc/apache2/sites-available/default:

```
ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">

		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch FollowSymLinks
		Order allow,deny
		Allow from all
	</Directory>
```
        
I also created a directory /var/www/cgi-bin but when I put my script in /usr/lib/cgi-bin with 755 permission I can't run it. I obtain an Internal server error and error.log says:

```
[Tue Jan 15 18:01:05 2008] [error] [client 192.168.1.105] (8)Exec format error: exec of '/usr/lib/cgi-bin/first.cgi' failed
[Tue Jan 15 18:01:05 2008] [error] [client 192.168.1.105] Premature end of script headers: first.cgi
```

Please, help me!
Thanks
Cheers
Marco

---

### Post by MJN on 2008-01-15
Does your CGI script work (outside of Apache)?

Mathew

P.S. There's no need for the cgi-bin directory in /var/www - you may as well remove it to avoid confusion (in case you drop something in there expecting it to work)

---

### Post by freymann on 2008-01-15
> **marco81 said:**
> 
```
[Tue Jan 15 18:01:05 2008] [error] [client 192.168.1.105] (8)Exec format error: exec of '/usr/lib/cgi-bin/first.cgi' failed
[Tue Jan 15 18:01:05 2008] [error] [client 192.168.1.105] Premature end of script headers: first.cgi
```


 The message "Premature end of script headers" means there's a problem with your source code.

 Try editing the script and removing any line feeds at the very end.

 Other than that, you'll have to try and figure out what is wrong with the code....

---

### Post by marco81 on 2008-01-16
Thanks for your quick reply!
I'm trying to run this simple script but I get the same error:

```

        #!/usr/bin/perl
        print "Content-type: text/html\r\n\r\n";
        print "Hello, World.";
```

What do you suggest?
Thanks
Cheers
Marco

---

### Post by MJN on 2008-01-16
You still haven't answered the question - does it run outside of Apache (i.e. from the commandline)?
 
Mathew
 
P.S. You might prefer to use a platform-agnostic linefeed i.e. \n\n as opposed to \r\n\r\n as the server will translate this into the appropriate CRLF for the platform as required by HTTP - this can avoid many headaches, particularly when changing platforms.

---

### Post by freymann on 2008-01-16
> **MJN said:**
> You still haven't answered the question - does it run outside of Apache (i.e. from the commandline)?


 Yeah, that's a pretty basic script...

 You can test it at the command line like this:

```

perl -d /path/to/scirpt.pl

```

Just enter the letter q for quit.

If there are no errors with the script (like hidden carraige returns you can't see) then you'll end up with the debug on line <1>. If there are problems, you see them echo'd on the screen.

---

### Post by marco81 on 2008-01-16
No, it doesn't run properly in shell!!! :-(
But I created a second script named first.sh (adding .sh exntension to config file too) which is the following:

```
#! /usr/bin/sh
pwd
cd /home

```

It's very basic but I can't run it.

It's the first time I use Apache, sorry!
Thank u
Marco

---

### Post by MJN on 2008-01-16
That's good - at least we can rule out Apache problems.
 
What happens when you try and run the perl script (let's stick with that one)?
 
Mathew

---

### Post by freymann on 2008-01-16
> **marco81 said:**
> No, it doesn't run properly in shell!!! :-(
But I created a second script named first.sh (adding .sh exntension to config file too) which is the following:

```
#! /usr/bin/sh
pwd
cd /home

```

It's very basic but I can't run it.


 You'd have to make the shell script executable with a 

```

chmod 755 filename.ext

```

or perhaps prefixed with the sudo command, depending on where it is, who owns it, etc.

But a shell script is not a perl scirpt, however, you may be required to make the perl script executeable too!

So do that on the test.pl script you are playing with.

Meaning...

Issue the command:

chmod 755 test.pl

(or even 777 if you have to)

Then try to run it from your web browser...

---

### Post by marco81 on 2008-01-16
Dear all, 
both sh and perl script have the right executable permissions but the error is still the same. 
About perl script I found a configuration file on the web to copy in conf.d directory and now if I run the script from /var/www/perl/ directory it works
But I can't figure out why sh script doesn't run!!!
thanks
Marco

---

### Post by MJN on 2008-01-16
Marco - please help us to help you by providing the information we ask for!

So you're up-and-running now with your CGI Perl scripts and can hence close the thread? For the sake of others please describe what you did to fix it and add [SOLVED] to the thread title.

Mathew

---

### Post by marco81 on 2008-01-16
Dear Mathew,
I can't say the problem is solved because I have .sh and python script to run too and following the instruction found on Apache website I can't do anything 
About perl script I copied fedora configuration file perl.conf in conf.d:

```

#
# Mod_perl incorporates a Perl interpreter into the Apache web server,
# so that the Apache web server can directly execute Perl code.
# Mod_perl links the Perl runtime library into the Apache web server
# and provides an object-oriented Perl interface for Apache's C
# language API.  The end result is a quicker CGI script turnaround
# process, since no external Perl interpreter has to be started.
#

LoadModule perl_module modules/mod_perl.so

# Uncomment this line to globally enable warnings, which will be
# written to the server's error log.  Warnings should be enabled
# during the development process, but should be disabled on a
# production server as they affect performance.
#
PerlSwitches -w

# Uncomment this line to enable taint checking globally.  When Perl is
# running in taint mode various checks are performed to reduce the
# risk of insecure data being passed to a subshell or being used to
# modify the filesystem.  Unfortunately many Perl modules are not
# taint-safe, so you should exercise care before enabling it on a
# production server.
#
#PerlSwitches -T

# This will allow execution of mod_perl to compile your scripts to
# subroutines which it will execute directly, avoiding the costly
# compile process for most requests.
#
Alias /perl /var/www/perl
<Directory /var/www/perl>
    SetHandler perl-script
    PerlResponseHandler ModPerl::Registry
    PerlOptions +ParseHeaders
    Options +ExecCGI
</Directory>

# This will allow remote server configuration reports, with the URL of
#  http://servername/perl-status
# Change the ".example.com" to match your domain to enable.
#
<Location /perl-status>
    SetHandler perl-script
    PerlResponseHandler Apache2::Status
    Order deny,allow
    Deny from all
    Allow from 127.0.0.1
</Location>
```

thanks
Marco

---

### Post by marco81 on 2008-01-16
Problem SOLVED:
you can leave a blank space in the first line before #! /usr/bin/...
I can't believe it was so simple
thanks a lot
Cheers
Marco

---

### Post by MJN on 2008-01-16
You shouldn't need that conf.d config.

Did you previously have the Perl Apache module loaded? (post the output of **ls /etc/apache2/mods-enabled**). If not, enable it with **sudo a2enmod perl**, remove the conf.d config and restart Apache.

Mathew

---

