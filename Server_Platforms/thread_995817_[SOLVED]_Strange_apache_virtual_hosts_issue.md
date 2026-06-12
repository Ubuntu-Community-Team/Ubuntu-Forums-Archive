---
title: "[SOLVED] Strange apache virtual hosts issue"
date: 2008-11-28
forum: Server Platforms
---

### Post by beercz on 2008-11-28
Hi All

I have apache2 running with several sub-domains pointing to the same apache web server.

For example, I have 2 sub-domains, say jcs.jaaconsult.com and website.jaaconsult.com.

I have created two virtual host files stored in /etc/apache2/sites-enabled, as follows:

For jcs.jaaconsult.com:
> # Job Costing System host configuration file

<VirtualHost *>
    ServerAdmin [EMAIL="webmaster@jaaconsult.com"]webmaster@jaaconsult.com[/EMAIL]
    ServerName jcs.jaaconsult.com
    ServerAlias jcs.jaaconsult.com

    # Indexes + Directory Root
    DirectoryIndex index.php
    DocumentRoot /home/jcs/

    # GCI Directory
    ScriptAlias /cgi-bin/ /home/jcs/cgi-bin/
    <Location /cgi-bin>
        Options +ExecCGI
    </Location>

    # Log Files
    ErrorLog /home/jcs/logs/error.log
    CustomLog /home/jcs/logs/access.log combined
</VirtualHost>
For website.jaaconsult.com:
> # Website host configuration file

<VirtualHost *>
    ServerAdmin [EMAIL="webmaster@jaaconsult.com"]webmaster@jaaconsult.com[/EMAIL]
    ServerName website.jaaconsult.com
    ServerAlias website.jaaconsult.com

    # Indexes + Directory Root
    DirectoryIndex index.php
    DocumentRoot /home/website/

    # GCI Directory
    ScriptAlias /cgi-bin/ /home/website/cgi-bin/
    <Location /cgi-bin>
        Options +ExecCGI
    </Location>

    # Log Files
    ErrorLog /home/website/logs/error.log
    CustomLog /home/website/logs/access.log combined
</VirtualHost>
When I (as root) enable the site jcs.jaaconsult.com > a2ensite jcs.jaaconsult.com the site works fine.

When I (as root) enable the site website.jaaconsult.com > a2ensite website.jaaconsult.com apache stops working and I get the following error:

> Failed to Connect
The connection was refused when attempting to contact website.jaaconsult.com.

Though the site seems valid, the browser was unable to establish a connection.

    *  Could the site be temporarily unavailable? Try again later.

    *  Are you unable to browse other sites?  Check the computer's network connection.

    *  Is your computer or network protected by a firewall or proxy? Incorrect settings can interfere with Web browsing.When I (as root) disable the site website.jaaconsult.com > a2dissite website.jaaconsult.com apache works again and the first site, jcs.jaaconsult.com works fine.

If I have only website.jaaconsult.com enabled, then apache fails to work.

Obviously, I (as root) reload apache > /etc/init.d/apache2 relaod every time I enable or disable a virtual host.

In fact I have six sites (and six sub-domains) all pointing to the same web server, and two of the virtual hosts (when enabled) work, and the other 4 do not.

I have been trying to resolve this for days. Anyone got any ideas why this is happening and what I have to do to get this issue fixed?

Thanks in advance.

---

### Post by MJN on 2008-11-28
> **beercz said:**
> When I (as root) enable the site website.jaaconsult.com apache stops working
 
You need to explain exactly why you mean by this. Does the a2ensite script complete? Does the Apache service stop? Do the logs say anything?
 
I trust you also have a **NameVirtualHost *** directive listed somewhere?
 
Mathew

---

### Post by volkswagner on 2008-11-28
You may want to post the two following files.

Apache2.conf and ports.conf

How are you handling DNS?

Do all of the directories listed in you site.conf exist, ie; /home/website/logs/?

---

### Post by cdenley on 2008-11-28
> **beercz said:**
> 
I have created two virtual host files stored in /etc/apache2/sites-enabled, as follows:

You are supposed to create site configurations in **/etc/apache2/sites-available**. Then when you enable a site, a link will be created for it in /etc/apache2/sites-enabled.

---

### Post by beercz on 2008-12-11
I have sorted this!

I feel a bit stupid really.  Problem was a really simple one.

Looking at an example of a virtual host file (for website.jaaconsult.com):
> # Website host configuration file

<VirtualHost *>
    ServerAdmin [EMAIL="webmaster@jaaconsult.com"]webmaster@jaaconsult.com[/EMAIL]
    ServerName website.jaaconsult.com
    ServerAlias website.jaaconsult.com

    # Indexes + Directory Root
    DirectoryIndex index.php
    DocumentRoot /home/website/

    # GCI Directory
    ScriptAlias /cgi-bin/ /home/website/cgi-bin/
    <Location /cgi-bin>
        Options +ExecCGI
    </Location>

    # Log Files
    ErrorLog /home/website/logs/error.log
    CustomLog /home/website/logs/access.log combined
</VirtualHost> 			 		

I have specified a location for log files (/home/website/logs).

But, I hadn't created the directory /home/website/logs.  Once I created this directory as user website, then re-enabled the site and reloads apache the site worked.

I feel soooooo stupid!!

In the words of the great(?) Homer Simpson "Doh!!!"

Thanks to all those who responded.

Marking this thread as solved.

---

