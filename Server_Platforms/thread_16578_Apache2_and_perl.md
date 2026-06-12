---
title: "Apache2 and perl"
date: 2005-02-22
forum: Server Platforms
---

### Post by calvinpriest on 2005-02-22
I've been trying to get perl working with Apache2 on my system and it seems no matter what I do whenever I try to navigate to a perl script in a browser I get an Open/Save dialog that wants me to download the .pl file.

Is there some setting in apache2.conf I need to change?  I've installed libapache2-mod-perl2.

Seems like I must be missing something obvious, but what??

---

### Post by alastair on 2005-02-22
Is the perl script executable?

In the apache conf file, there's a "/perl" (mod perl) section I think (set to /var/www.perl perhaps) - try a script in there.

---

### Post by calvinpriest on 2005-02-22
The perl scripts are executable by all.  I checked /etc/apache2/apache2.conf and there is no reference to the word "perl" anywhere.  Should there be?

Thanks!

---

### Post by nocturn on 2005-02-23
[QUOTE=calvinpriest]The perl scripts are executable by all.  I checked /etc/apache2/apache2.conf and there is no reference to the word "perl" anywhere.  Should there be?

Thanks![/QUOTE]

Yes.

You should load mod_perl.

Also, configure the cgi-bin directory, the scrips should be stored there.

---

### Post by wulf on 2005-02-23
Just as a thought, have you checked that perl is running from the command line? That might help track down problems such as using the wrong path to perl at the top of your scripts. Something as simple as:
```
#!/usr/bin/perl
print "Hello Word";
```
will do the trick. I've found perl and apache2 have worked smoothly on both the Ubuntu installations where I've used them and I don't remember doing anything particularly fancy to get them working nicely together.

Wulf

---

### Post by calvinpriest on 2005-02-23
Ok, thanks for the tips.  Not out of the woods yet, but progress...

It looks like in Apache2 the way to enable a module is to create symlinks between mods-available and mods-enabled.  That did need to be done for perl and I've done it now and mod_perl appears to be loading (though I'm not sure how to confirm).  I restarted Apache, but I'm still getting the Open/Save dialog.

I've confirmed that Perl is ok but running the Hello World script (actually I have a perl script of my own that was cron scheduled to run every day, so I knew it would work).  Unfortunately while I can run the hello world script from the command line, in Apache it doesn't work.

Thanks again everyone.  Any other ideas?  In Apache2 is there something I do need to add to apache2.conf?  It doesn't look like it to me according to the README.  There is no reference to the module for php in that file either...

---

### Post by wulf on 2005-02-23
Hmmnn... perl is definitely running on my webserver (I've been experimenting with the blosxom blog software) but /etc/apache2/mods-enabled doesn't contain a link to the perl.load script in mods-available. In fact, that perl.load file is the only one under /etc/apache that contains any reference to perl (grep -ir 'perl').

I have got libapache2-mod-perl2 installed - maybe that makes a difference?

Wulf

I'm racking my brain trying to remember if I did anything

---

### Post by calvinpriest on 2005-02-23
I also have libapache2-mod-perl2 installed.

I've made some progress though by uncommenting and modifying a section in apache2.conf (i added ".pl" to the end of the line):
AddHandler cgi-script .cgi .pl

Now I get past the Open/Save dialog and I get an error: "403 Forbidden: You don't have permission to access /test/test.pl on this server", which I consider to be progress.  At the bottom of the page it shows the Apache version and "mod_perl" so it looks like the module is working.

So now the question is how to get around the permissions error?  Anyone who has perl working who could post their apache2.conf file?

Also, should i be trying a script under cgi-bin first?  Where is it located?

---

### Post by calvinpriest on 2005-02-23
Ok, it turns out cgi-bin is located at /usr/lib/cgi-bin.  Now if I try to execute a simple perl script from there I get a different error: "500 Internal Server Error".

Does anyone out there have perl and apache2 installed and working together?  If so, could you post your apache2.conf file?

---

### Post by calvinpriest on 2005-02-23
Ok, so now I have a script working under cgi-bin.  Turns out there was a problem with my test script -- thus the "internal server error".

So now it seems the problem has come down to how to run perl scripts outside of the cgi-bin directory.  I still get the "403 Forbidden: You don't have permission..." error when trying to run scripts from anywhere else.

Any ideas on that?

---

### Post by alastair on 2005-02-23
I run the standard apache-perl package, and have the following in my httpd.conf file :

```

# If the perl module is installed, this will be enabled.
<IfModule mod_perl.c>
  <IfModule mod_alias.c>
   Alias /perl/ /var/www/perl/
  </IfModule>
  <Location /perl>
    SetHandler perl-script
    PerlHandler Apache::Registry
    Options +ExecCGI
  </Location>
</IfModule>

```

Perl scripts in "/perl" should run under modperl.

---

### Post by calvinpriest on 2005-02-23
Ok, I've got it.

I had to add one more thing to apache2.conf:
<Files ~ "\.pl$">
    Options +ExecCGI
</Files>

Now all is well.

---

### Post by Jester on 2005-03-05
Ok, i've been having the same problem. i've done all you did, adding the .pl to the addhandler line, added the <files> stuff, everything. still cant seem to get it to run .pl stuff outside of the cgi-bin directory...

---

### Post by Jester on 2005-03-05
[QUOTE=Jester]Ok, i've been having the same problem. i've done all you did, adding the .pl to the addhandler line, added the <files> stuff, everything. still cant seem to get it to run .pl stuff outside of the cgi-bin directory...[/QUOTE]


Ok, too either A. clear things up, or B. help people who's problems vary, i put the <files> stuff in apache2.conf, didnt seem to work. Then, in "default", located in "sites-enabled" (actually a symlink, but still editable) i added ExecCGI to the Options in the /var/www Directory section, now it seems to almost be working properly. Actually, yeah, its working. I'm sure the remaining problems i'm having have to do with permissions....

---

### Post by lindsay_keir on 2006-09-22
Probably too late, but, I found with Ubuntu Server (Apache2.0.55) to run cgi, perl scripts from any directory I had to set, in 
 # **/etc/apache2/apache2.conf**
 AddHandler cgi-script .cgi
 <Files ~ "\.pl$"> 
 Options +ExecCGI
 </Files>
 <Files ~ "\.cgi$">
 Options +ExecCGI
 </Files>
There was NO virtual server involved, no .htaccess - my target (VOCP) was picked up from being installed in /var/wwww/vocpweb

---

### Post by darcy on 2007-12-20
Hello everyone.

I'm trying to run perl in my Ubuntu-Server as well.

This is what my configuration look like for my Web root.

mkdir /home/darcy/www
sudo rm -r /var/www
sudo ln -s /home/darcy/www /var/www

sudo apt-get install libapache2-mod-perl2
sudo /etc/init.d/apache2 restart

I read the posts above but don't understand. 

In /etc/apache2/apache2.conf I added:


AddHandler cgi-script .cgi
<Files ~ "\.pl$">
Options +ExecCGI
</Files>
<Files ~ "\.cgi$">
Options +ExecCGI
</Files>

<IfModule mod_perl.c>
<IfModule mod_alias.c>
Alias /perl/ /home/darcy/www/perl/
</IfModule>
<Location /perl>
SetHandler perl-script
PerlHandler Apache::Registry
Options +ExecCGI
</Location>
</IfModule>


I just added this to the file and restarted apache.

When I visit my file in a web browser it just tries to download the file rather than running it.

[http://myserver.com/perl.pl](http://myserver.com/perl.pl)
[http://myserver.com/perl/perl.pl](http://myserver.com/perl/perl.pl)
[http://myserver.com/cgi-bin/perl.pl](http://myserver.com/cgi-bin/perl.pl)

Actually, with the cgi-bin directory, it doesn't let me view the directory and when I try and run the file in there it gives me a 404.

So what do I do if I want to run perl in ubuntu?

So far ubuntu's been easy for everything but I'm finding it hard to find a clear answer on what to do for this.

Darcy

---

### Post by motang on 2007-12-25
> **darcy said:**
> Hello everyone.

I'm trying to run perl in my Ubuntu-Server as well.

This is what my configuration look like for my Web root.

mkdir /home/darcy/www
sudo rm -r /var/www
sudo ln -s /home/darcy/www /var/www

sudo apt-get install libapache2-mod-perl2
sudo /etc/init.d/apache2 restart

I read the posts above but don't understand. 

In /etc/apache2/apache2.conf I added:


AddHandler cgi-script .cgi
<Files ~ "\.pl$">
Options +ExecCGI
</Files>
<Files ~ "\.cgi$">
Options +ExecCGI
</Files>

<IfModule mod_perl.c>
<IfModule mod_alias.c>
Alias /perl/ /home/darcy/www/perl/
</IfModule>
<Location /perl>
SetHandler perl-script
PerlHandler Apache::Registry
Options +ExecCGI
</Location>
</IfModule>


I just added this to the file and restarted apache.

When I visit my file in a web browser it just tries to download the file rather than running it.

[http://myserver.com/perl.pl](http://myserver.com/perl.pl)
[http://myserver.com/perl/perl.pl](http://myserver.com/perl/perl.pl)
[http://myserver.com/cgi-bin/perl.pl](http://myserver.com/cgi-bin/perl.pl)

Actually, with the cgi-bin directory, it doesn't let me view the directory and when I try and run the file in there it gives me a 404.

So what do I do if I want to run perl in ubuntu?

So far ubuntu's been easy for everything but I'm finding it hard to find a clear answer on what to do for this.

Darcy

Hey Darcy,
I just got mine working since you are using .pl files add a .pl to your
> AddHandler cgi-script .cgi .pl

After that restart apache web server and it should work.  I did for me.  Good luck.

---

### Post by Hakachukai on 2008-01-02
I had a similar problem that had me ripping my hair out for about 3 hours, but the cause was completely different.

What was happening was that either Apache, or the browser did not understand that I was trying to stream it HTML code, so it tried to download it instead because it had no idea what it was.

The solution is to properly use the html header.

---------------------------------------------
print "Content-type: html

";

print "<html> <body><p>";
---------------------------------------------


Notice the 2 '\n' charactors on the content type line. It won't work if you don't have those 2 '\n' charactors there.

---

### Post by stevyrey on 2008-01-22
Hi all,

right having the same problem
have tried all the solutions posted previously.

Here are my apache2.conf and httpd.conf files.

apache2.conf
```
#
# Based upon the NCSA server configuration files originally by Rob McCool.
#
# This is the main Apache server configuration file.  It contains the
# configuration directives that give the server its instructions.
# See http://httpd.apache.org/docs/2.2/ for detailed information about
# the directives.
#
# Do NOT simply read the instructions in here without understanding
# what they do.  They're here only as hints or reminders.  If you are unsure
# consult the online docs. You have been warned.  
#
# The configuration directives are grouped into three basic sections:
#  1. Directives that control the operation of the Apache server process as a
#     whole (the 'global environment').
#  2. Directives that define the parameters of the 'main' or 'default' server,
#     which responds to requests that aren't handled by a virtual host.
#     These directives also provide default values for the settings
#     of all virtual hosts.
#  3. Settings for virtual hosts, which allow Web requests to be sent to
#     different IP addresses or hostnames and have them handled by the
#     same Apache server process.
#
# Configuration and logfile names: If the filenames you specify for many
# of the server's control files begin with "/" (or "drive:/" for Win32), the
# server will use that explicit path.  If the filenames do *not* begin
# with "/", the value of ServerRoot is prepended -- so "/var/log/apache2/foo.log"
# with ServerRoot set to "" will be interpreted by the
# server as "//var/log/apache2/foo.log".
#

### Section 1: Global Environment
#
# The directives in this section affect the overall operation of Apache,
# such as the number of concurrent requests it can handle or where it
# can find its configuration files.
#

#
# ServerRoot: The top of the directory tree under which the server's
# configuration, error, and log files are kept.
#
# NOTE!  If you intend to place this on an NFS (or otherwise network)
# mounted filesystem then please read the LockFile documentation (available
# at <URL:http://httpd.apache.org/docs-2.1/mod/mpm_common.html#lockfile>);
# you will save yourself a lot of trouble.
#
# Do NOT add a slash at the end of the directory path.
#
ServerRoot "/etc/apache2"

#
# The accept serialization lock file MUST BE STORED ON A LOCAL DISK.
#
#<IfModule !mpm_winnt.c>
#<IfModule !mpm_netware.c>
LockFile /var/lock/apache2/accept.lock
#</IfModule>
#</IfModule>

#
# PidFile: The file in which the server should record its process
# identification number when it starts.
#
PidFile /var/run/apache2.pid

#
# Timeout: The number of seconds before receives and sends time out.
#
Timeout 300

#
# KeepAlive: Whether or not to allow persistent connections (more than
# one request per connection). Set to "Off" to deactivate.
#
KeepAlive On

#
# MaxKeepAliveRequests: The maximum number of requests to allow
# during a persistent connection. Set to 0 to allow an unlimited amount.
# We recommend you leave this number high, for maximum performance.
#
MaxKeepAliveRequests 100

#
# KeepAliveTimeout: Number of seconds to wait for the next request from the
# same client on the same connection.
#
KeepAliveTimeout 15

##
## Server-Pool Size Regulation (MPM specific)
## 

# prefork MPM
# StartServers: number of server processes to start
# MinSpareServers: minimum number of server processes which are kept spare
# MaxSpareServers: maximum number of server processes which are kept spare
# MaxClients: maximum number of server processes allowed to start
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

# worker MPM
# StartServers: initial number of server processes to start
# MaxClients: maximum number of simultaneous client connections
# MinSpareThreads: minimum number of worker threads which are kept spare
# MaxSpareThreads: maximum number of worker threads which are kept spare
# ThreadsPerChild: constant number of worker threads in each server process
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule mpm_worker_module>
    StartServers          2
    MaxClients          150
    MinSpareThreads      25
    MaxSpareThreads      75 
    ThreadsPerChild      25
    MaxRequestsPerChild   0
</IfModule>

User www-data
Group www-data

#
# AccessFileName: The name of the file to look for in each directory
# for additional configuration directives.  See also the AllowOverride
# directive.
#

AccessFileName .htaccess

#
# The following lines prevent .htaccess and .htpasswd files from being 
# viewed by Web clients. 
#
<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
</Files>

#
# DefaultType is the default MIME type the server will use for a document
# if it cannot otherwise determine one, such as from filename extensions.
# If your server contains mostly text or HTML documents, "text/plain" is
# a good value.  If most of your content is binary, such as applications
# or images, you may want to use "application/octet-stream" instead to
# keep browsers from trying to display binary files as though they are
# text.
#
DefaultType text/plain


#
# HostnameLookups: Log the names of clients or just their IP addresses
# e.g., www.apache.org (on) or 204.62.129.132 (off).
# The default is off because it'd be overall better for the net if people
# had to knowingly turn this feature on, since enabling it means that
# each client request will result in AT LEAST one lookup request to the
# nameserver.
#
HostnameLookups Off

# ErrorLog: The location of the error log file.
# If you do not specify an ErrorLog directive within a <VirtualHost>
# container, error messages relating to that virtual host will be
# logged here.  If you *do* define an error logfile for a <VirtualHost>
# container, that host's errors will be logged there and not here.
#
ErrorLog /var/log/apache2/error.log

#
# LogLevel: Control the number of messages logged to the error_log.
# Possible values include: debug, info, notice, warn, error, crit,
# alert, emerg.
#
LogLevel warn

# Include module configuration:
Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf

# Include all the user configurations:
Include /etc/apache2/httpd.conf

# Include ports listing
Include /etc/apache2/ports.conf

#
# The following directives define some format nicknames for use with
# a CustomLog directive (see below).
#
LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %b" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent

#
# ServerTokens
# This directive configures what you return as the Server HTTP response
# Header. The default is 'Full' which sends information about the OS-Type
# and compiled in modules.
# Set to one of:  Full | OS | Minor | Minimal | Major | Prod
# where Full conveys the most information, and Prod the least.
#
ServerTokens Full

#
# Optionally add a line containing the server version and virtual host
# name to server-generated pages (internal error documents, FTP directory 
# listings, mod_status and mod_info output etc., but not CGI generated 
# documents or custom error documents).
# Set to "EMail" to also include a mailto: link to the ServerAdmin.
# Set to one of:  On | Off | EMail
#
ServerSignature On



#
# Customizable error responses come in three flavors:
# 1) plain text 2) local redirects 3) external redirects
#
# Some examples:
#ErrorDocument 500 "The server made a boo boo."
#ErrorDocument 404 /missing.html
#ErrorDocument 404 "/cgi-bin/missing_handler.pl"
#ErrorDocument 402 http://www.example.com/subscription_info.html
#

#
# Putting this all together, we can internationalize error responses.
#
# We use Alias to redirect any /error/HTTP_<error>.html.var response to
# our collection of by-error message multi-language collections.  We use 
# includes to substitute the appropriate text.
#
# You can modify the messages' appearance without changing any of the
# default HTTP_<error>.html.var files by adding the line:
#
#   Alias /error/include/ "/your/include/path/"
#
# which allows you to create your own set of files by starting with the
# /usr/share/apache2/error/include/ files and copying them to /your/include/path/, 
# even on a per-VirtualHost basis.  The default include files will display
# your Apache version number and your ServerAdmin email address regardless
# of the setting of ServerSignature.
#
# The internationalized error documents require mod_alias, mod_include
# and mod_negotiation.  To activate them, uncomment the following 30 lines.

#    Alias /error/ "/usr/share/apache2/error/"
#
#    <Directory "/usr/share/apache2/error">
#        AllowOverride None
#        Options IncludesNoExec
#        AddOutputFilter Includes html
#        AddHandler type-map var
#        Order allow,deny
#        Allow from all
#        LanguagePriority en cs de es fr it nl sv pt-br ro
#        ForceLanguagePriority Prefer Fallback
#    </Directory>
#
#    ErrorDocument 400 /error/HTTP_BAD_REQUEST.html.var
#    ErrorDocument 401 /error/HTTP_UNAUTHORIZED.html.var
#    ErrorDocument 403 /error/HTTP_FORBIDDEN.html.var
#    ErrorDocument 404 /error/HTTP_NOT_FOUND.html.var
#    ErrorDocument 405 /error/HTTP_METHOD_NOT_ALLOWED.html.var
#    ErrorDocument 408 /error/HTTP_REQUEST_TIME_OUT.html.var
#    ErrorDocument 410 /error/HTTP_GONE.html.var
#    ErrorDocument 411 /error/HTTP_LENGTH_REQUIRED.html.var
#    ErrorDocument 412 /error/HTTP_PRECONDITION_FAILED.html.var
#    ErrorDocument 413 /error/HTTP_REQUEST_ENTITY_TOO_LARGE.html.var
#    ErrorDocument 414 /error/HTTP_REQUEST_URI_TOO_LARGE.html.var
#    ErrorDocument 415 /error/HTTP_UNSUPPORTED_MEDIA_TYPE.html.var
#    ErrorDocument 500 /error/HTTP_INTERNAL_SERVER_ERROR.html.var
#    ErrorDocument 501 /error/HTTP_NOT_IMPLEMENTED.html.var
#    ErrorDocument 502 /error/HTTP_BAD_GATEWAY.html.var
#    ErrorDocument 503 /error/HTTP_SERVICE_UNAVAILABLE.html.var
#    ErrorDocument 506 /error/HTTP_VARIANT_ALSO_VARIES.html.var



# Include of directories ignores editors' and dpkg's backup files,
# see README.Debian for details.

# Include generic snippets of statements
Include /etc/apache2/conf.d/

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/


#Perl stuff
AddHandler cgi-script .cgi .pl
<Files ~ "\.pl$">
Options +ExecCGI
</Files>
<Files ~ "\.cgi$">
Options +ExecCGI
</Files>

<IfModule mod_perl.c>
<IfModule mod_alias.c>
Alias /perl/ /home/darcy/www/perl/
</IfModule>
<Location /perl>
SetHandler perl-script
PerlHandler Apache::Registry
Options +ExecCGI
</Location>
</IfModule> 
```

httpd.conf
```
### Apache httpd.conf version 1x ###
ServerType standalone
ServerName www.example.org
Listen 0.0.0.0:80
ServerAdmin webmaster@www.example.org
ServerTokens OS
Timeout 120
LockFile /var/lock/apache.lock
PidFile /var/run/apache.pid
ScoreBoardFile /var/run/apache.scoreboard
KeepAlive On
MaxKeepAliveRequests 100
KeepAliveTimeout 15
MinSpareServers 5
MaxSpareServers 10
StartServers 5
MaxClients 150
MaxRequestsPerChild 100
ServerSignature On

DocumentRoot "/var/www/"
ServerRoot "/etc/apache2"
User nobody
Group nobody
<IfModule mod_status.c>
    ExtendedStatus On
</IfModule>

<Directory />
	Options SymLinksIfOwnerMatch
	AllowOverride None
</Directory>

<Directory /var/www/>
	Options Indexes Includes FollowSymLinks MultiViews
	AllowOverride None
	Order allow,deny
	Allow from all
</Directory>

<IfModule mod_userdir.c>
	UserDir public_html
	<Directory /home/*/public_html>
	    AllowOverride FileInfo AuthConfig Limit
	    Options MultiViews Indexes SymLinksIfOwnerMatch IncludesNoExec
	    <Limit GET POST OPTIONS PROPFIND>
    	Order allow,deny
    	Allow from all
	    </Limit>
	    <Limit PUT DELETE PATCH PROPPATCH MKCOL COPY MOVE LOCK UNLOCK>
    	Order deny,allow
    	Deny from all
	    </Limit>
	</Directory>
</IfModule>

<IfModule mod_dir.c>
	DirectoryIndex index.html index.htm index.shtml index.cgi index.php
</IfModule>

AccessFileName .htaccess
<Files ~ "^\.ht">
	Order allow,deny
	Deny from all
</Files>

UseCanonicalName Off
TypesConfig /etc/mime.types
<IfModule mod_mime_magic.c>
	MIMEMagicFile /usr/share/file/magic.mime
</IfModule>
HostnameLookups Off
ErrorLog /var/log/apache/error.log
LogLevel warn
LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %b" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent
CustomLog /var/log/apache/access.log combined
<IfModule mod_log_forensic.c>
	ForensicLog /var/log/apache/forensic.log
</IfModule>

<IfModule mod_backtrace.c>
	EnableExceptionHook On
</IfModule>

<IfModule mod_whatkilledus.c>
	EnableExceptionHook On
</IfModule>

<IfModule mod_alias.c>
	Alias /icons/ /usr/share/apache/icons/
	<Directory /usr/share/apache/icons>
        Options Indexes MultiViews
        AllowOverride None
        Order allow,deny
        Allow from all
	</Directory>

	Alias /images/ /usr/share/images/
	<Directory /usr/share/images>
     Options MultiViews
     AllowOverride None
     Order allow,deny
     Allow from all
	</Directory>

</IfModule>

<IfModule mod_alias.c>
	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory /usr/lib/cgi-bin/>
      AllowOverride None
  	   Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
  	   Order allow,deny
  	   Allow from all
	</Directory>
</IfModule>
<IfModule mod_autoindex.c>
	IndexOptions FancyIndexing NameWidth=*
	AddIconByEncoding (CMP,/icons/compressed.gif) x-compress x-gzip

	AddIconByType (TXT,/icons/text.gif) text/*
	AddIconByType (IMG,/icons/image2.gif) image/*
	AddIconByType (SND,/icons/sound2.gif) audio/*
	AddIconByType (VID,/icons/movie.gif) video/*
	AddIcon /icons/binary.gif .bin .exe
	AddIcon /icons/binhex.gif .hqx
	AddIcon /icons/tar.gif .tar
	AddIcon /icons/world2.gif .wrl .wrl.gz .vrml .vrm .iv
	AddIcon /icons/compressed.gif .Z .z .tgz .gz .zip
	AddIcon /icons/a.gif .ps .ai .eps
	AddIcon /icons/layout.gif .html .shtml .htm .pdf
	AddIcon /icons/text.gif .txt
	AddIcon /icons/c.gif .c
	AddIcon /icons/p.gif .pl .py
	AddIcon /icons/f.gif .for
	AddIcon /icons/dvi.gif .dvi
	AddIcon /icons/uuencoded.gif .uu
	AddIcon /icons/script.gif .conf .sh .shar .csh .ksh .tcl
	AddIcon /icons/tex.gif .tex
	AddIcon /icons/bomb.gif core
	AddIcon /icons/deb.gif .deb
	AddIcon /icons/back.gif ..
	AddIcon /icons/hand.right.gif README
	AddIcon /icons/folder.gif ^^DIRECTORY^^
	AddIcon /icons/blank.gif ^^BLANKICON^^
	DefaultIcon /icons/unknown.gif

	AddDescription "GZIP compressed document" .gz
	AddDescription "tar archive" .tar
	AddDescription "GZIP compressed tar archive" .tgz
	ReadmeName README.html
	HeaderName HEADER.html
	IndexIgnore .??* *~ *# HEADER.html HEADER.txt RCS CVS *,v *,t
</IfModule>

<IfModule mod_mime.c>
AddEncoding x-compress Z
AddEncoding x-gzip gz tgz
	AddLanguage da .dk
	AddLanguage nl .nl
	AddLanguage en .en
	AddLanguage et .ee
	AddLanguage fr .fr
	AddLanguage de .de
	AddLanguage el .el
	AddLanguage it .it
	AddLanguage ja .ja
	AddCharset ISO-2022-JP .jis
	AddLanguage pl .po
	AddCharset ISO-8859-2 .iso-pl
	AddLanguage pt .pt
	AddLanguage pt-br .pt-br
	AddLanguage lb .lu
	AddLanguage ca .ca
	AddLanguage es .es
	AddLanguage sv .se
	AddLanguage cs .cz

	<IfModule mod_negotiation.c>
	    LanguagePriority en da nl et fr de el it ja pl pt pt-br lb ca es sv
	</IfModule>
AddType application/x-httpd-php .php
AddType application/x-httpd-php-source .phps
AddType application/x-tar .tgz
AddType image/bmp .bmp
AddType text/x-hdml .hdml
AddHandler cgi-script .cgi .sh .pl

	<IfModule mod_include.c>
	 AddType text/html .shtml
	 AddHandler server-parsed .shtml
	</IfModule>

AddHandler type-map var
</IfModule>
AddDefaultCharset on

<IfModule mod_setenvif.c>
	BrowserMatch "Mozilla/2" nokeepalive
	BrowserMatch "MSIE 4\.0b2;" nokeepalive downgrade-1.0 force-response-1.0
	BrowserMatch "RealPlayer 4\.0" force-response-1.0
	BrowserMatch "Java/1\.0" force-response-1.0
	BrowserMatch "JDK/1\.0" force-response-1.0
	BrowserMatch "Microsoft Data Access Internet Publishing Provider" redirect-carefully
	BrowserMatch "MS FrontPage" redirect-carefully
	BrowserMatch "^WebDrive" redirect-carefully
	BrowserMatch "^WebDAVFS/1.[0123]" redirect-carefully
	BrowserMatch "^gnome-vfs/1.0" redirect-carefully
	BrowserMatch "^XML Spy" redirect-carefully
	BrowserMatch "^Dreamweaver-WebDAV-SCM1" redirect-carefully
</IfModule>

<IfModule mod_perl.c>
  <IfModule mod_alias.c>
     Alias /perl/ /var/www/perl/
  </IfModule>
  <Location /perl>
     SetHandler perl-script
     PerlHandler Apache::Registry
     Options +ExecCGI
  </Location>
</IfModule>

<IfModule mod_alias.c>
	Alias /doc/ /usr/share/doc/
</IfModule>

<Location /doc>
	order deny,allow
	deny from all
	allow from 127.0.0.0/255.0.0.0
	Options Indexes FollowSymLinks MultiViews
</Location>
<IfModule mod_proxy.c>
	ProxyRequests Off
	ProxyVia Off
	<Directory proxy:*>
      Order deny,allow
      Deny from all
      Allow from .your_domain.com
	</Directory>
	CacheRoot "/var/cache/apache"
	CacheSize 5
	CacheGcInterval 4
	CacheMaxExpire 24
	CacheLastModifiedFactor 0.1
	CacheDefaultExpire 1
	NoCache a_domain.com another_domain.edu joes.garage_sale.com
</IfModule>

Include /etc/apache2/sql-ledger-httpd.conf

```
( the sql ledger bit at the bottom is for what i'm trying to run)

Thanks in advance guys&gals

Regards
Steve

---

### Post by rchille on 2008-01-25
stevyrey,

I'm having the same-ish problem, but you might be running afoul on:
```
Alias /perl/ /home/darcy/www/perl/ 
```

I think that this might be a specific location on darcy's computer (unless you created it too.) That and I've seen a few people mention that httpd.conf isn't used for apache2, again I'm having my own problems so not an expert opinion. :)

Anyone else have ideas?

What I did:
I have Apache2 installed (for the standard ubuntu repos) and work nicely. I have python installed and apache does and excellent job severing *.py  scripts from /var/www/. I'd like the same functionality with perl (serving up .pl's from /var/www).

I used Synaptic to install libapache-mod-perl2. 
Going to localhost I can see:
```
Apache/2.2.4 (Ubuntu) mod_python/3.3.1 Python/2.5.1 mod_perl/2.0.2 Perl/v5.8.8 Server at localhost Port 80
```

I wrote the follow script and tested from the command line:
```
 #!/usr/bin/perl
print "Content-type: text/html\n\n";
print "It worked!!!\n"
```;

And that worked.

Then I moved it to /var/www and set the permissions to 755.
When I goto that file (localhost/test.pl) it gives me an Open/Save dialog box.

I've played around with the solutions the darcy and calvinpriest  got but I'm stuck at getting a 500 Internal Server Error.

This is config that I made to my /etc/apache2/apache2.conf
```
AddHandler cgi-script .cgi .pl
<Files ~ "\.pl$">
Options +ExecCGI
</Files>
<Files ~ "\.cgi$">
Options +ExecCGI
</Files>

<IfModule mod_perl.c>
<IfModule mod_alias.c>
Alias /perl/ /var/www/
</IfModule>
<Location /perl>
SetHandler perl-script
PerlHandler Apache::Registry
Options +ExecCGI
</Location>
</IfModule>


```

Please some tell me I did something bone-headed that is easy to fix!

Thanks in advance!

---

### Post by rosegarden78 on 2008-01-25
I installed a LAMP last year.  When Perl was installed with the Apache bindings and stuff, Perl scripts would execute only if I put them in /var/www/ or a sub-subdirectory in the server.  I might also have used localhost to access the scripts.  When Perl wasn't installed properly I think I had the same problem.

---

### Post by stevyrey on 2008-01-25
rchilie,

Indeed the darcy line could be causing the problem!

Though i've managed to fix it now by removing what i was trying to get to work (sql ledger) and taking out all the changes i'd made to the apache files then reinstalling it by a different method.

Thanks anyway

Regards

Steve

---

### Post by rchille on 2008-01-28
Thanks for the replies rosegarden and stevyray.!

I finally tracked down the trouble. I took a break from working on it this weekend and when I got in this morning, instead of using the gui text editor, I pulled my script up in vim. Sure enough I have a couple of hidden characters that were choking the process. I removed them and instantly my test worked!

Scratch another problem up to cut/paste and another solution to walking away and coming back with a fresh mindset.

:)

-Rob

---

