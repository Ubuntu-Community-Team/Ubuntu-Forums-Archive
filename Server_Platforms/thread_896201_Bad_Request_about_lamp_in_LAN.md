---
title: "Bad Request about lamp in LAN"
date: 2008-08-20
forum: Server Platforms
---

### Post by zccpop on 2008-08-20
I have installed LAMP in my ubuntu desktop followed by the [wiki]("https://help.ubuntu.com/community/ApacheMySQLPHP").
All works normally. ~/Public_html is my documentroot.
I can access localhost or 127.0.0.1 or my LAN ip [http://172.24.213.176](http://172.24.213.176)
But others in LAN cannot access [http://172.24.213.176](http://172.24.213.176)
It said: Bad Request......
What should i do?
(files in documentroot are all 777)
My appache2 config is :


NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /home/zcc/Public_html/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/zcc/Public_html/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		Allow from all
	</Directory>
	<Directory /home/zcc/Public_html/wiki>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		Allow from all
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

---

### Post by windependence on 2008-08-21
Since you are using a directory in /home for the document root, the ownership of your files is probably not correct. Change the owner to root.

Why are you using a directory in /home?

-Tim

---

### Post by zccpop on 2008-08-21
> **windependence said:**
> Since you are using a directory in /home for the document root, the ownership of your files is probably not correct. Change the owner to root.

Why are you using a directory in /home?

-Tim

I changed the ownership of directory to root.But it didn't work,either.

I am a newer, so I have not gotten used to command. Home directory is easy to do.

---

### Post by Iowan on 2008-08-21
It may not be the files as much as the directory(s) - who owns **/home/zcc/** and **/home/zcc/Public_html/**?

Oops, you already did that...

---

### Post by zccpop on 2008-08-22
> **Iowan said:**
> It may not be the files as much as the directory(s) - who owns **/home/zcc/** and **/home/zcc/Public_html/**?

Oops, you already did that...

Maybe I should not use directory in Home really.

---

### Post by windependence on 2008-08-22
Can you post the output of:

ls -la /home/zcc

and 

ls -la /home/zcc/Public_html

-Tim

---

### Post by zccpop on 2008-08-22
> **windependence said:**
> Can you post the output of:

ls -la /home/zcc

and 

ls -la /home/zcc/Public_html

-Tim


zcc@zcc-laptop:~$ ls -la /home/zcc/Public_html
&#24635;&#29992;&#37327; 40
drwxrwxrwx  9 zcc      root 4096 2008-08-21 21:08 .
drwxr-xr-x 74 zcc      zcc  4096 2008-08-22 23:09 ..
drwxrwxrwx 16 zcc      zcc  4096 2008-08-19 22:18 mediawiki
drwxrwxrwx  3 zcc      zcc  4096 2008-08-17 00:05 PHP Beautifier
-rwxrwxrwx  1 zcc      zcc    17 2008-07-28 15:44 phpinfo.php
drwxr-xr-x  4 zcc      zcc  4096 2008-08-21 03:21 program
drwxrwxrwx 30 zcc      zcc  4096 2008-08-02 22:44 Source
drwxr-xr-x  2 www-data root 4096 2008-07-29 21:03 tmp
drwxrwxrwx  7 root     root 4096 2008-08-21 21:06 wiki
drwxrwxrwx  5 zcc      zcc  4096 2008-08-16 23:47 wordpress
zcc@zcc-laptop:~$ ls -la /home/zcc
&#24635;&#29992;&#37327; 1308
drwxr-xr-x 74 zcc  zcc    4096 2008-08-22 23:09 .
drwxr-xr-x  4 root root   4096 2008-07-27 23:46 ..
drwx------  5 zcc  zcc    4096 2008-08-19 00:13 .adobe
drwxr-xr-x  4 zcc  zcc    4096 2008-08-19 09:10 .aMule
-rw-------  1 zcc  zcc   15544 2008-08-22 23:09 .bash_history
-rw-r--r--  1 zcc  zcc     220 2008-07-27 23:46 .bash_logout
-rw-r--r--  1 zcc  zcc    2928 2008-07-27 23:46 .bashrc
drwxr-xr-x  2 zcc  zcc    4096 2008-08-16 23:30 .bluefish
drwxr-xr-x  3 zcc  zcc    4096 2008-07-27 23:54 .cache
drwx------  2 zcc  zcc    4096 2008-07-27 17:25 .chewing
drwx------  3 zcc  zcc    4096 2008-07-27 17:59 .compiz
drwxr-xr-x 14 zcc  zcc    4096 2008-08-16 00:06 .config
-rw-------  1 zcc  zcc      28 2008-08-22 23:09 .dmrc
drwxrwxrwx 10 zcc  zcc    4096 2008-08-21 01:42 Documents
drwxr-xr-x  2 zcc  zcc    4096 2008-08-21 21:34 Download
-rw-------  1 zcc  zcc      16 2008-07-27 23:54 .esd_auth
drwxr-xr-x  4 zcc  zcc    4096 2008-08-17 09:59 .eva
drwxr-xr-x  8 zcc  zcc    4096 2008-08-20 11:41 .evolution
drwxr-xr-x  2 zcc  zcc    4096 2008-07-28 14:13 .fontconfig
-rw-r--r--  1 zcc  zcc     514 2008-07-29 19:39 .fonts.conf
drwx------  2 zcc  zcc    4096 2008-08-12 09:11 .fotoxx
drwx------  5 zcc  zcc    4096 2008-08-22 23:09 .gconf
drwx------  2 zcc  zcc    4096 2008-08-22 23:12 .gconfd
drwxr-xr-x 22 zcc  zcc    4096 2008-08-15 23:55 .gimp-2.4
-rw-r-----  1 zcc  zcc       0 2008-08-22 23:10 .gksu.lock
drwx------  3 zcc  zcc    4096 2008-07-28 14:50 .gnome
drwx------ 17 zcc  zcc    4096 2008-08-22 18:13 .gnome2
drwx------  2 zcc  zcc    4096 2008-07-27 23:54 .gnome2_private
drwx------  2 zcc  zcc    4096 2008-08-22 23:09 .gnupg
drwx------  4 zcc  zcc    4096 2008-08-13 06:36 .google
drwx------  4 zcc  zcc    4096 2008-07-28 14:51 .googleearth
drwxr-xr-x  2 zcc  zcc    4096 2008-07-27 17:41 .gpilotd
-rw-r--r--  1 zcc  zcc       4 2008-07-27 17:41 .gpilotd.pid
drwx------  2 zcc  zcc    4096 2008-08-08 08:41 .gsopcast
drwxr-xr-x  2 zcc  zcc    4096 2008-08-08 08:41 .gstreamer-0.10
-rw-r--r--  1 zcc  zcc     440 2008-08-22 17:31 .gtk-bookmarks
dr-x------  2 zcc  zcc       0 2008-08-22 23:09 .gvfs
-rw-------  1 zcc  zcc    4284 2008-08-22 23:09 .ICEauthority
drwxr-xr-x  3 zcc  zcc    4096 2008-08-04 21:44 .icons
drwxr-xr-x  5 zcc  zcc    4096 2008-08-19 21:05 .ies4linux
drwxr-xr-x  3 zcc  zcc    4096 2008-08-08 10:04 .java
drwx------  3 zcc  zcc    4096 2008-07-27 19:06 .kde
-rw-------  1 zcc  zcc     364 2008-07-29 19:40 .kderc
drwx------  4 zcc  zcc    4096 2008-08-12 12:27 .liferea_1.4
drwxr-xr-x  3 zcc  zcc    4096 2008-07-27 23:54 .local
drwx------  3 zcc  zcc    4096 2008-07-28 14:50 .loki
drwx------  3 zcc  zcc    4096 2008-07-27 18:38 .macromedia
drwxr-xr-x  3 zcc  zcc    4096 2008-07-27 19:07 .mcop
-rw-------  1 zcc  zcc      31 2008-07-27 19:07 .mcoprc
drwxrwxrwx  3 zcc  zcc    4096 2008-07-27 18:40 Media
drwx------  3 zcc  zcc    4096 2008-07-27 23:54 .metacity
drwxr-xr-x  4 zcc  zcc    4096 2008-08-21 19:02 .miro
drwx------  4 zcc  zcc    4096 2008-07-29 20:22 .mozilla
drwxr-xr-x  2 zcc  zcc    4096 2008-08-08 08:39 .mplayer
drwxr-xr-x  5 zcc  zcc    4096 2008-08-15 21:34 MyCode
-rw-------  1 zcc  zcc    5689 2008-08-16 22:03 .mysql_history
drwxr-xr-x  3 zcc  zcc    4096 2008-08-22 18:13 .nautilus
-rw-r--r--  1 root root   1164 2008-08-19 08:43 .nvidia-settings-rc
drwx------  3 zcc  zcc    4096 2008-08-21 15:06 .openoffice.org2
-rw-r--r--  1 zcc  zcc       0 2008-08-16 22:52 phpmyadmin.conf~
drwxr-xr-x  4 zcc  zcc    4096 2008-08-12 13:53 .picasa
drwxrwxrwx 11 zcc  zcc    4096 2008-08-15 19:38 Picture
drwxrwxrwx  4 zcc  zcc    4096 2008-07-27 18:40 Private
-rw-r--r--  1 zcc  zcc     586 2008-07-27 23:46 .profile
drwxrwxrwx  9 zcc  root   4096 2008-08-21 21:08 Public_html
drwxr-xr-x  2 zcc  zcc    4096 2008-07-27 17:58 .pulse
-rw-------  1 zcc  zcc     256 2008-07-27 23:54 .pulse-cookie
drwx------  4 zcc  zcc    4096 2008-07-30 08:22 .purple
drwxr-xr-x  2 zcc  zcc    4096 2008-07-29 19:40 .qt
-rw-------  1 zcc  zcc    6928 2008-08-21 15:06 .recently-used
-rw-r--r--  1 zcc  zcc  885197 2008-08-22 18:13 .recently-used.xbel
drwxrwx---  3 zcc  zcc    4096 2008-07-27 17:40 .sane
drwx------  4 zcc  zcc    4096 2008-07-27 17:29 .scim
drwx------  4 zcc  zcc    4096 2008-08-16 23:30 .screem
drwxr-xr-x  3 zcc  zcc    4096 2008-08-14 00:58 .screenlets
drwxrwxrwx  9 zcc  zcc    4096 2008-08-19 21:02 Software
drwx------  2 zcc  zcc    4096 2008-07-27 23:54 .ssh
drwx------  3 zcc  zcc    4096 2008-07-27 18:51 .stardict
drwxr-xr-x  3 root root   4096 2008-08-16 22:21 .subversion
-rw-r--r--  1 zcc  zcc       0 2008-07-27 15:55 .sudo_as_admin_successful
-rw-------  1 zcc  zcc   12288 2008-08-10 13:18 .swp
drwxr-xr-x  2 zcc  zcc    4096 2008-07-27 18:51 Temp
drwxrwxrwx  3 zcc  zcc    4096 2008-07-31 12:19 .Tencent
-rw-------  1 zcc  zcc   12288 2008-08-19 10:42 .test.swp
drwxr-xr-x  4 zcc  zcc    4096 2008-08-12 20:13 .themes
drwx------  5 zcc  zcc    4096 2008-07-28 14:02 .thumbnails
drwxr-xr-x  5 zcc  zcc    4096 2008-08-21 15:26 .tomboy
-rw-r--r--  1 zcc  zcc    5544 2008-08-22 23:09 .tomboy.log
drwx------  2 zcc  zcc    4096 2008-07-27 17:39 .tsclient
drwxr-xr-x  4 zcc  zcc    4096 2008-07-30 16:56 .ubuntu-tweak
drwxr-xr-x  2 zcc  zcc    4096 2008-07-27 16:18 .update-manager-core
drwx------  2 zcc  zcc    4096 2008-07-29 18:05 .update-notifier
drwxr-xr-x  4 zcc  zcc    4096 2008-08-19 10:34 .vim
-rw-------  1 zcc  zcc    7501 2008-08-19 21:00 .viminfo
drwxr-xr-x  2 zcc  zcc    4096 2008-08-22 23:09 .wapi
drwxr-xr-x  4 zcc  zcc    4096 2008-08-19 09:32 .wine
-rw-------  1 zcc  zcc     121 2008-08-22 23:09 .Xauthority
drwxr-xr-x  2 zcc  zcc    4096 2008-07-27 19:06 .xine
-rw-r--r--  1 zcc  zcc     146 2008-07-27 17:46 .xscreensaver-getimage.cache
-rw-r--r--  1 zcc  zcc    5551 2008-08-22 23:15 .xsession-errors
drwxr-xr-x  2 zcc  zcc    4096 2008-08-21 21:39 &#26700;&#38754;

---

### Post by zccpop on 2008-08-22
I changed directory back to /var/www
and its owner is root.
But the problem is the same.

---

### Post by zccpop on 2008-08-24
I have fixed the question.
when I logout the net on my friend's PC, and the web come up.
In LAN, the ip is different, so ...

---

