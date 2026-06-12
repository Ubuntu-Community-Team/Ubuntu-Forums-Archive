---
title: "Running multiple websites on single server (VirtualHost)"
date: 2010-08-25
forum: Server Platforms
---

### Post by jrtboht on 2010-08-25
I currently am running 10.04.1 and have successfully setup my home web server to run a single website.  My current settings are:

-I have registered the domain name annarrankings.com through godaddy
-A record is   -   host = @ and points to = 71.114.220.3
-CName is   -   host = www and points to = @
-on my server I have the site running in /var/www

---------------------------------------------------------------------------------------

I've done some research and found that to run multiple websites I need to setup VirtualHost.  

-So I created a folder /var/www/annarrankings.com and moved my site to that folder
-Edited Apache2.conf to add the following line
[IMG]http://lh3.ggpht.com/_aEwLsvC9j1k/THT5kQb5RJI/AAAAAAAAAiQ/cqHinFcRRzI/s800/img1.jpg[/IMG]

-I then went to /etc/apache2/sites-enabled and copied the default file to a new file called annarrankings.com.  Here's the annarrankings.com file after I edited it
[IMG]http://lh6.ggpht.com/_aEwLsvC9j1k/THT_g2MekHI/AAAAAAAAAis/LbzQDfd3NbI/s800/img2.jpg[/IMG]

-I then created a link in /etc/apache2/sites-enabled to the annarrankings.com file in /etc/apache2/sites-available

-Next I editied /etc/hosts 
[IMG]http://lh3.ggpht.com/_aEwLsvC9j1k/THT99sGExGI/AAAAAAAAAig/WF85ddRJZ68/s800/img3.jpg[/IMG]

-when i went to enable the site using a2ensite annarrankings.com I got the following
***************************************
jeremy@webserver: /etc/apache2/sites-available$ a2ensite annarrankings.com
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_US.UTF-8"
     are supported and installed on your system.
perl: warning: Failling back to the standard locale ("C").
Site annarrankings.com already enabled
***************************************


I figured this was ok since I had already created a symbolic link earlier (a result of trying to following multiple tutorials and youtube videos at once) so I reloaded apache2.  I created an index.html file in /var/www/ just for testing purposes and when I load [www.annarrankings.com](www.annarrankings.com) I get the file located in /var/www/ instead of the website located in /var/www/annarrankings.com   Do I need to change my A record or CName in godaddy or did I just do this completely wrong?

---

### Post by Ryan Dwyer on 2010-08-25
You need to add ServerAlias [www.annarrankings.com](www.annarrankings.com) to your vhost file, then reload Apache again.

---

### Post by Bachstelze on 2010-08-25
Also you don't need to copy the whole file, the first three lines ov the VirtualHost block should suffice.

---

### Post by cdenley on 2010-08-25
Also, you shouldn't have edited apache2.conf. That line should already be in ports.conf, and shouldn't appear twice in your configuration files. And it is best to allow the a2ensite, a2dissite, a2enmod, and a2dismod commands to manage the symlinks, not create them manually.

---

### Post by jrtboht on 2010-08-25
Thanks for the replies.  I took all your suggestions and here's what I got

-I deleted the symbolic link
-I uncommented out the NameVirtualHost *:80 line in ports.conf

/etc/apache2/apache2.conf
> 
# Define an access log for VirtualHosts that don't define their own logfile
CustomLog /var/log/apache2/other_vhosts_access.log vhost_combined


# Include of directories ignores editors' and dpkg's backup files,
# see README.Debian for details.

# Include generic snippets of statements
Include /etc/apache2/conf.d/

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled//etc/apache2/ports.conf


> NameVirtualHost *:80
Listen 80

<IfModule mod_ssl.c>
    # If you add NameVirtualHost *:443 here, you will also have to change
    # the VirtualHost statement in /etc/apache2/sites-available/default-ssl
    # to <VirtualHost *:443>
    # Server Name Indication for SSL named virtual hosts is currently not
    # supported by MSIE on Windows XP.
    Listen 443
</IfModule>

<IfModule mod_gnutls.c>
    Listen 443
</IfModule>/etc/apache2/sites-available/annarrankings.com
> 
VirtualHost *:80>
        ServerAdmin [EMAIL="webmaster@annarrankings.com"]webmaster@annarrankings.com[/EMAIL]
        ServerName annarrankings.com
        ServerAlias [www.annarrankings.com]("http://www.annarrankings.com")
        DocumentRoot /var/www/annarrankings.com
</VirtualHost>When I went to enable the site I got the message

> sudo a2ensite annarrankings.com

perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Enabling site annarrankings.com.I reloaded apache2 and everything seems to be working

I posted my settings anyway just in case anyone stumbles across this thread with the same problem or in case anyone sees anything in my files that doesn't look right (even though it seems to be working fine).  Thanks guys

---

### Post by Bachstelze on 2010-08-25
The errors when you run a2ensite are because the en_US.UTF-8 locale is apparently not installed on your system.  You can install language-pack-en to get rid of them.

---

### Post by TheFuturian on 2010-08-25
I thought that all a2ensite does is create the symlink..? I think the error might have been because you'd already done the work.

---

### Post by TheFuturian on 2010-08-25
> **jrtboht said:**
> 
***************************************
jeremy@webserver: /etc/apache2/sites-available$ a2ensite annarrankings.com
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LANG = "en_US.UTF-8"
     are supported and installed on your system.
perl: warning: Failling back to the standard locale ("C").
Site annarrankings.com already enabled
***************************************


> **Bachstelze said:**
> The errors when you run a2ensite are because the en_US.UTF-8 locale is apparently not installed on your system.  You can install language-pack-en to get rid of them.

There's an error and a notification, seems Bachstelze's advice could be spot on?

---

### Post by jrtboht on 2010-08-25
I installed language-pack-en and now I have no warnings when enabling sites anymore, thanks for the tip

---

