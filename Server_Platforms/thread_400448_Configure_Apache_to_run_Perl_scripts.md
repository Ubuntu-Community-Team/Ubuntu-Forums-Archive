---
title: "Configure Apache to run Perl scripts"
date: 2007-04-03
forum: Server Platforms
---

### Post by Winterdream on 2007-04-03
I've installed Ubuntu desktop and Apache.  I have Apache working, it will serve a simple HTML page on localhost.  Now I want to configure it to execute Perl scripts from a cgi-bin.  I tried making a new folder in var/www/ named "cgi-bin" and just putting a script in there - naturally, that doesn't work.

I think I need to do this:
gksudo gedit /etc/apache2/apache2.conf
and edit that file to make this happen.

I really don't want to mess this up, could someone please tell me what changes are required?  All I want to do is run my Perl scripts on this system so I can work on them.

Many thanks for any advice!

---

### Post by mechdave on 2007-11-28
All I did was install mod perl with apt-get install libapache2-mod-perl2 and then verified that /etc/apache2/mods-enabled/perl.load was present. Then all I did was add the following file called perl.conf (from my Fedora 7 machine ;) ), perl.conf. I have pasted it for your convinience below...

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

Put this file in the /etc/apache2/conf.d/ directory and it should all work after you restart apache2 with /etc/init.d/apache2 restart.
Happy Linuxing,
     Mechdave...

---

