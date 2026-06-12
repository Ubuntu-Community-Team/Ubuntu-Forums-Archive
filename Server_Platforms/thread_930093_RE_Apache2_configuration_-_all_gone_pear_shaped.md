---
title: "RE Apache2 configuration - all gone pear shaped"
date: 2008-09-25
forum: Server Platforms
---

### Post by redeyejake on 2008-09-25
After about 10 days of trying to get this working properly, i've decided to post so please don't dismiss this (!) it's not like i haven't made the effort..

Wanted to host a website on my Ubuntu server. A few months ago got a small HP Proliant to run as a RAID mirror array file server for backing up HD video footage for a documentary shot on a tapeless camera. Usaul story, Ubuntu seemed like the best choice and the initial SAMBA setup worked after a bit of sweat and a steepish learning curve... Therefore, couple of weeks ago thought, why not host my website on the server too.. Hmm. 

Basically to cut this long story short, i've followed a multitude of online tutorials to do various things in order to host my site and ended up with a load of stuff i probably don't need. Struggled a bit with virtual hosts then lost my default apache site in the process. IE i can't access the 'It Works' site or my virtual sites through my static internal IP, in a browser: 192.168.1.100 reveals:

Not Found
The requested URL /apache2-default.html/ was not found on this server.
Apache/2.2.8 (Ubuntu) Server at 192.168.1.100 Port 80

The site in /etc/apache2/sites-available/default is as follows:

NameVirtualHost *
<VirtualHost *>
        ServerAdmin jake@localhost
        DocumentRoot /var/www/

        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                RedirectMatch ^/$ /apache2-default/
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
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



...and has been activated by: a2ensite default, then apache restarted gracefully. I've tried relocating the /var/www directories and Allowing from 192.168.1.101 which is my mac which i use to administer the server via open ssh. As far as i know, 127.0.0.0 is not usable for the server because i'm using my mac over open-ssh to administer and the server has no gui or monitor or browser.

Funnily enough after about 8 days, i got so p$£$%d off i tried to set up apache on my mac and using the original apache installed on OS X 10.4.1 through the UNIX shell. Strangely it works fine and i've pointed my DNS to my external static ip and my mac is serving up one of my sites over the net no problem. However, this is no solution as my mac is a power hungry workstation. 

This did inspire me to return to my HP Ubuntu server and apt-get remove apache and as many of it's partners in crime as i could find - including by apt-get purge, and reinstall. Still my configuration files are exactly the same and i'm very tempted to just delete them now although have read in these forums that this is a bad idea.

Sorry (i'm British), i'm new to all this and I know there are many posts similar to this and i've spent a long time scouring for answers, so please i'm hoping that there is some blaringly obvious error i've made that someone more experienced can spot a mile off.

Here's hoping :popcorn:

PS UBUNTU 8.04 Hardy Heron

---

### Post by redeyejake on 2008-10-18
Got this sorted in the end. I had uninstalled/reinstalled Apache - which didn't work. So took the plunge and just deleted all my Apache .conf files manually then reinstalled again. Then just reset the file path to my web directory and bingo, back online.

---

