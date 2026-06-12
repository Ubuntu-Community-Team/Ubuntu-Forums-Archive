---
title: "Unable to configure cgi in public_html under apache2 to use ikiwiki"
date: 2009-11-12
forum: Server Platforms
---

### Post by notmatt on 2009-11-12
I am trying to setup ikiwiki under Ubuntu 9.10.  I have the wiki installed and running however when I try to access the cgi parts of the site I get prompted to download the .cgi file.  I am running the wiki (as is it's default) from my public_html dir.  Ideally I'd like to have the whole dir as a cgi-bin, not just a specific cgi-bin.  I've also tried several snippets of perl code (copied from various sites) to test things and make sure it's not an ikiwiki config issue.  I'm sure it's not.  Here's what I've tried so far:

Installed apache, perl, ikiwiki.

Versions:

This is perl, v5.10.0 built for x86_64-linux-gnu-thread-multi

Server version: Apache/2.2.12 (Ubuntu)
Server built:   Aug 18 2009 13:03:28

ikiwiki version 3.14ubuntu1


Enabled the relevant mods:

user@machine:~$ sudo a2enmod perl
Module perl already enabled
user@machine:~$ sudo a2enmod cgi
Your MPM seems to be threaded. Selecting cgid instead of cgi.
Module cgid already enabled
user@machine:~$ sudo a2enmod userdir
Module userdir already enabled

After a bit of poking through lots of forum posts and blog posts I came across the following snippet which seems to do the right thing:

       ScriptAlias /cgi-bin/ /home/*/public_html/cgi-bin/
        <Directory /home/*/public_html/cgi-bin>
                AllowOverride None
                Options ExecCGI
                AddHandler cgi-script .cgi .pl
                Order allow,deny
                Allow from all
        </Directory>

And I have placed this in the following files:

/etc/apache2/sites-enabled/000-default
/etc/apache2/mods-enabled/userdir.conf (this is where I reckon it should go)
/etc/apache2/apache.conf

I have tried several variants of the above in all the three locations.  Including specifying the full path (eg /home/user/public_html/cgi-bin).  I've restarted apache each time I've made a config change and reloaded the page and tested again.  I've also tried to place the ikiwiki cgi stuff in the normal 'user/lib/cgi-bin' dir, not much luck there either.

To rule out permissions issues I've chmoded the various cgi-bin files and folders to 777 (yes it's bad security wise, but I'd rather get it working and then lock things down).

Any ideas?

---

