---
title: "Guide to Install Bandersnatch"
date: 2005-09-21
forum: Server Platforms
---

### Post by bartman007 on 2005-09-21
Bandersnatch is a message logger for Jabber servers.  Unfortunately the version of the package (0.31) in the Hoary (and Breezy) repository is broken. It relies on libnet-jabber-perl version 1.30-1mtech while Hoary contains 2.0-2. Debian repositories contain 0.32, and the only difference is that the dependancy on jabberd 1.x has been changed to eJabberd.  In either version (0.31 or 0.32) Bandersnatch appears to run, and says that it successfully connects to the jabber server, and the mySQL database, it does not log any messages.  
This information was found in an old Debian bug report, located here: [Debian Bug 301889](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=301889) 
The options to correct this are a) downgrade libnet-jabber-perl or b) upgrade bandersnatch.

I chose option b.  These are the steps I took to acheive a sucessful Bandersnatch installation with eJabberd (which is a superior alternative jabber server to jabberd 1.x
1) Install bandersnatch-frontend via apt-get/synaptic.  This will select all of the packages bandersnatch and the bandersnatch-frontend are dependant on.
```
sudo apt-get install bandersnatch-frontend
``` 
2) Completely uninstall bandersnatch-frontend, bandersnatch, jabberd and apache via "apt-get --purge remove"/synaptic.
```
sudo apt-get --purge remove bandersnatch-frontend bandersnatch jabber apache
``` 
3) Install eJabberd via apt-get/synaptic.  For help configuring an eJabberd server, refer to [this guide](http://www.process-one.net/en/projects/ejabberd/docs/guide_en.html).
```
sudo apt-get install ejabberd
```
4) Install apache2 (this is the Ubuntu approved version of apache, and the version that php works with out of the box.)
```
sudo apt-get install apache2
``` 
5) Download [bandersnatch 0.4RC1](http://www.funkypenguin.co.za/filestore2/download/5/bandersnatch-0.4.RC1.tar.gz)  from [FunkyPenguin](http://www.funkypenguin.co.ca)
```
wget -c http://www.funkypenguin.co.za/filestore2/download/5/bandersnatch-0.4.RC1.tar.gz
``` 
6) Extract the files and move to /usr/share/bandersnatch
```
sudo tar xzvf bandersnatch-0.4.RC1.tar.gz
sudo mv bandersnatch-0.4.RC1 /usr/share/bandersnatch
```
7) Copy the files in the doc folder into /usr/share/doc/bandersnatch
```
sudo cp -r /usr/share/bandersnatch/doc /usr/share/doc/bandersnatch
```
8) Move the frontend folder to /usr/share/bandersnatch-frontend
```
sudo mv /usr/share/bandersnatch/frontend /usr/share/bandersnatch-frontend
```
9) Copy the default config to /etc/ejabberd
```
sudo cp /usr/share/bandersnatch/config.xml /etc/jabber/bandersnatch.xml
```
10) Copy the bandersnatch executable to /usr/sbin and set the proper permissions
```
sudo cp /usr/share/bandersnatch/bandersnatch /usr/sbin/bandersnatch
sudo chmod 744 /usr/sbin/bandersnatch
```
11) Create the mySQL database structure
```
sudo mysql < /usr/share/bandersnatch/bandersnatch.sql
``` 
12) Follow the Bandersnatch manual located at /usr/share/doc/bandersnatch/bandersnatch.html, but make sure to omit the mysql database creation done in the step above.
13) Add the bandersnatch specific settings to ejabberd.cfg, refer to step three of [this guide](http://ejabberd.jabber.ru/install-bandersnatch).
14) Add an alias to the Bandersnatch-frontend web directory into the apache config
```
sudo echo Alias /bandersnatch /usr/share/bandersnatch-frontend/htdocs >> /etc/apache2/httpd.conf
``` 
15) Create a symlink to the bandersnatch front-end config.
```
ln -sf /usr/share/bandersnatch-frontend/includes/config.inc.php /etc/jabber/bandersnatch-frontend.conf.php
```
16) Create an init.d script for bandersnatch and set the permissions for it.
Create a file containing the following using your favorite editor at "/etc/init.d/bandersnatch"
```
#! /bin/sh
#
# skeleton      example file to build /etc/init.d/ scripts.
#               This file should be used to construct scripts for /etc/init.d.
#
#               Written by Miquel van Smoorenburg <miquels@cistron.nl>.
#               Modified for Debian GNU/Linux
#               by Ian Murdock <imurdock@gnu.ai.mit.edu>.
#
# Version:      @(#)skeleton  1.8  03-Mar-1998  miquels@cistron.nl
#
# This file was automatically customized by dh-make on Fri, 27 Feb 2004 00:35:14 +0000

PATH=/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/sbin/bandersnatch
NAME=bandersnatch
DESC=bandersnatch
CMDLINE=' /etc/jabber/bandersnatch.xml'

test -f $DAEMON || exit 0

set -e

case "$1" in
  start)
        echo -n "Starting $DESC: "
        start-stop-daemon -m -b --start --quiet --pidfile /var/run/$NAME.pid \
                --exec $DAEMON -- $CMDLINE
        echo "$NAME."
        ;;
  stop)
        echo -n "Stopping $DESC: "
        start-stop-daemon --oknodo --stop --quiet --pidfile /var/run/$NAME.pid
        rm -f /var/run/$NAME.pid
        echo "$NAME."
        ;;
  #reload)
        #
        #       If the daemon can reload its config files on the fly
        #       for example by sending it SIGHUP, do it here.
        #
        #       If the daemon responds to changes in its config file
        #       directly anyway, make this a do-nothing entry.
        #
        # echo "Reloading $DESC configuration files."
        # start-stop-daemon --stop --signal 1 --quiet --pidfile \
        #       /var/run/$NAME.pid --exec $DAEMON
  #;;
  restart|force-reload)
        #
        #       If the "reload" option is implemented, move the "force-reload"
        #       option to the "reload" entry above. If not, "force-reload" is
        #       just the same as "restart".
        #
        echo -n "Restarting $DESC: "
        start-stop-daemon --stop --quiet --pidfile \
                /var/run/$NAME.pid --exec $DAEMON
        sleep 1
        start-stop-daemon --start --quiet --pidfile \
                /var/run/$NAME.pid --exec $DAEMON
        echo "$NAME."
        ;;
  *)
        N=/etc/init.d/$NAME
        # echo "Usage: $N {start|stop|restart|reload|force-reload}" >&2
        echo "Usage: $N {start|stop|restart|force-reload}" >&2
        exit 1
        ;;
esac

exit 0



```
Then do
```
sudo chmod 744 /etc/init.d/bandersnatch
```
17) Install Boot-Up Manager (BUM).  I highly recommend this program, it is a GUI to manage services that start upon linux booting.  Also, if I remember correctly, it is going to be included in Breezy.
```
wget -c http://ftp.us.debian.org/debian/pool/main/b/bum/bum_1.3.3-1_all.deb
sudo dpkg -i ubm_1.2.4-0ubuntu1_all.deb

```
18) Run Boot-Up Manager (should be in System --> Administration after a GNOME restart, which can be achived with Ctrl-Alt-Backspace, but don't do this until you have saved everything you have open) and make sure the box next to bandersnatch is checked.
19) Restart ejabberd and mysql, and start both bandersnatch and apache2
```
sudo /etc/init.d/ejabberd restart
sudo /etc/init.d/mysql restart
sudo /etc/init.d/bandersnatch start
sudo /etc/init.d/apache2 start
```

Congratulations you should now have working Bandersnatch installation.
This can be verified by going to [http://localhost/bandersnatch](http://localhost/bandersnatch) and checking the number of logged messages.

-Bartman007

P.S.  Please let me know if any of the instructions are wrong.  I typed this up a week I configured eJabberd and Bandersnatch, but referred to my configs, and the notes I made while doing the write-up.

---

