---
title: "Lazy Apache"
date: 2007-04-13
forum: Server Platforms
---

### Post by Kinslayer on 2007-04-13
I am running 6.10 desktop with a LAMP server.  Other than some minor usability tweaking (e.g. getting the mouse buttons & dvd player to work) it's otherwise a default install--I haven't even changed the wallpaper.  (And I admit a fondness for the Human theme anyway.)

I'm having a rather odd problem:  my server stops serving after a few hours.  Browsing for a webpage on the server just gets a time-out error, or never stops trying to pull up the page (and never gets anywhere).  This happens several times daily.  It's as though Apache just takes a nap or something.  

This is true whether it's LAN or WAN, from inside the network or out, but browsing localhost still pulls up the pages.  These are html or text pages, so it's not PHP or MySQL to blame, and it's not the router or dns.  It's not a problem with the connection, as I can still navigate the vast wide 'net even when the server is taking it easy... again...  Also my ISP doesn't block ports or anything.  I've managed to narrow it down to Apache.  It's lazy.  Yelling at it doesn't seem to help at all.  

Rebooting the computer fixes the problem, at least for a few hours, but restarting Apache doesn't do anything at all.  Apache restarts, and the problem still exists.  It says it restarts, but it lies.  Apache is a liar.  And it's lazy.  

There's nothing indicating a problem, other than the simple fact that it won't serve up webpages any longer.  If you ask Apache, it says that it's working great.  There are no error messages on any logs that I can find.  The server activity doesn't indicate a problem, but I can usually narrow the time down as to when it stopped serving--all traffic halts.  It's not the same time every day, but it does happen multiple times per day.  I have to reboot the computer at least three times daily because of this issue.  It's the only way I've found to at least put a temporary bandage on the problem.  

I've dug through many many how-to pages & forums, and tried everything that I can think of myself to correct this.  I have discovered that other people have had similar problems, but I have not yet found a solution.  I was wondering if anyone else here has had a similar problem, or perhaps you have some insight as to what needs be done.  



(Stupid lazy server...)

---

### Post by amohanty on 2007-04-13
Can you post the logs just prior to halting?
Also post your apache2.conf (without the comments)?

Finally do a **pgrep apache2** just after starting the service and then at the point when you detect that its not responing and post those too.

AM

---

### Post by Kinslayer on 2007-04-14
From error.log:  ```

[Sat Apr 14 02:03:20 2007] [error] [client 70.119.151.221] File does not exist: /var/www/anima.gif, referer: [http://lost-souls.servebeer.com/](http://lost-souls.servebeer.com/)
[Sat Apr 14 02:19:20 2007] [error] [client 66.249.66.1] File does not exist: /var/www/forums
[Sat Apr 14 03:56:31 2007] [error] [client 66.249.66.1] File does not exist: /var/www/forums
[Sat Apr 14 04:51:01 2007] [error] [client 85.255.117.66] File does not exist: /var/www/forum2, referer: [http://lost-souls.servebeer.com/forum2/phpBB2/profile.php?mode=register&agreed=true](http://lost-souls.servebeer.com/forum2/phpBB2/profile.php?mode=register&agreed=true)
[Sat Apr 14 04:51:01 2007] [error] [client 85.255.117.66] File does not exist: /var/www/forum2, referer: [http://lost-souls.servebeer.com/forum2/phpBB2/profile.php?mode=register&agreed=true](http://lost-souls.servebeer.com/forum2/phpBB2/profile.php?mode=register&agreed=true)
[Sat Apr 14 04:51:01 2007] [error] [client 85.255.117.66] File does not exist: /var/www/forum2, referer: [http://lost-souls.servebeer.com/forum2/phpBB2/profile.php?mode=register&agreed=true](http://lost-souls.servebeer.com/forum2/phpBB2/profile.php?mode=register&agreed=true)
[Sat Apr 14 04:51:04 2007] [error] [client 85.255.117.66] File does not exist: /var/www/forum2, referer: [http://lost-souls.servebeer.com/forum2/phpBB2/profile.php?mode=register&agreed=true](http://lost-souls.servebeer.com/forum2/phpBB2/profile.php?mode=register&agreed=true)
[Sat Apr 14 04:51:04 2007] [error] [client 85.255.117.66] File does not exist: /var/www/forum2, referer: [http://lost-souls.servebeer.com/forum2/phpBB2/profile.php?mode=register&agreed=true](http://lost-souls.servebeer.com/forum2/phpBB2/profile.php?mode=register&agreed=true)
[Sat Apr 14 04:51:04 2007] [error] [client 85.255.117.66] File does not exist: /var/www/forum2, referer: [http://lost-souls.servebeer.com/forum2/phpBB2/profile.php?mode=register&agreed=true](http://lost-souls.servebeer.com/forum2/phpBB2/profile.php?mode=register&agreed=true)
[Sat Apr 14 04:59:22 2007] [error] [client 74.52.90.234] File does not exist: /var/www/forums, referer: [http://lost-souls.servebeer.com/forums/index.php?action=unread;board=1.0](http://lost-souls.servebeer.com/forums/index.php?action=unread;board=1.0)
[Sat Apr 14 05:59:58 2007] [error] [client 66.249.66.1] File does not exist: /var/www/forums
[Sat Apr 14 06:00:02 2007] [error] [client 66.249.66.1] File does not exist: /var/www/forums
[Sat Apr 14 06:07:19 2007] [error] [client 66.249.66.1] File does not exist: /var/www/forums
[Sat Apr 14 06:10:24 2007] [error] [client 66.249.66.1] File does not exist: /var/www/forums
[Sat Apr 14 06:12:01 2007] [error] [client 66.249.66.1] File does not exist: /var/www/forums
[Sat Apr 14 06:12:08 2007] [error] [client 66.249.66.1] File does not exist: /var/www/forums
[Sat Apr 14 06:12:13 2007] [error] [client 66.249.66.1] File does not exist: /var/www/forums
[Sat Apr 14 06:12:41 2007] [error] [client 66.249.66.1] File does not exist: /var/www/forums
[Sat Apr 14 06:12:58 2007] [error] [client 66.249.66.1] File does not exist: /var/www/forums
[Sat Apr 14 06:13:51 2007] [error] [client 66.249.66.1] File does not exist: /var/www/forums

```

These are legit errors, and they reference an older set of forums from before I moved to Ubuntu.  The timespan covers a period from when I verified that it was still serving up pages to the end of the log.  

From access.log:  
```
65.40.16.68 - - [14/Apr/2007:03:33:22 -0400] "POST /drupal/chatblock/view HTTP/1.1" 200 - "http://lost-souls.servebeer.com/drupal/chatblock/view" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)"
66.249.66.1 - - [14/Apr/2007:03:56:31 -0400] "GET /forums/index.php?PHPSESSID=baf650a16d4e9d531cb4be1f6da4a80c&action=profile;u=308;sa=showPosts HTTP/1.1" 404 314 "-" "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)"
66.98.136.46 - - [14/Apr/2007:04:44:58 -0400] "GET / HTTP/1.1" 200 26372 "http://www.servermojo.com" "ServerMojo/0.9 (http://www.servermojo.com)"
85.255.117.66 - - [14/Apr/2007:04:51:01 -0400] "POST /forum2/phpBB2/profile.php HTTP/1.0" 404 323 "http://lost-souls.servebeer.com/forum2/phpBB2/profile.php?mode=register&agreed=true" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)"
85.255.117.66 - - [14/Apr/2007:04:51:01 -0400] "POST /forum2/phpBB2/profile.php HTTP/1.0" 404 323 "http://lost-souls.servebeer.com/forum2/phpBB2/profile.php?mode=register&agreed=true" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)"
85.255.117.66 - - [14/Apr/2007:04:51:01 -0400] "POST /forum2/phpBB2/profile.php HTTP/1.0" 404 323 "http://lost-souls.servebeer.com/forum2/phpBB2/profile.php?mode=register&agreed=true" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)"
85.255.117.66 - - [14/Apr/2007:04:51:04 -0400] "POST /forum2/phpBB2/profile.php HTTP/1.0" 404 323 "http://lost-souls.servebeer.com/forum2/phpBB2/profile.php?mode=register&agreed=true" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)"
85.255.117.66 - - [14/Apr/2007:04:51:04 -0400] "POST /forum2/phpBB2/profile.php HTTP/1.0" 404 323 "http://lost-souls.servebeer.com/forum2/phpBB2/profile.php?mode=register&agreed=true" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)"
85.255.117.66 - - [14/Apr/2007:04:51:04 -0400] "POST /forum2/phpBB2/profile.php HTTP/1.0" 404 323 "http://lost-souls.servebeer.com/forum2/phpBB2/profile.php?mode=register&agreed=true" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)"
74.52.90.234 - - [14/Apr/2007:04:59:22 -0400] "POST /forums/index.php?action=login2 HTTP/1.1" 404 314 "http://lost-souls.servebeer.com/forums/index.php?action=unread;board=1.0" "Mozilla/4.0 (compatible; MSIE 5.01; Windows NT 5.0)"
66.249.66.1 - - [14/Apr/2007:05:59:58 -0400] "GET /forums/index.php?PHPSESSID=d137d4763025569bd0cc2606bfcb09df&action=post;topic=114.0;num_replies=2 HTTP/1.1" 404 314 "-" "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)"
66.249.66.1 - - [14/Apr/2007:06:00:02 -0400] "GET /forums/index.php?PHPSESSID=885a219aadbbba571a96fd3718033f6e&topic=114.msg405 HTTP/1.1" 404 314 "-" "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)"
66.98.136.46 - - [14/Apr/2007:06:06:40 -0400] "GET / HTTP/1.1" 200 26372 "http://www.servermojo.com" "ServerMojo/0.9 (http://www.servermojo.com)"
66.249.66.1 - - [14/Apr/2007:06:07:19 -0400] "GET /forums/ HTTP/1.1" 404 305 "-" "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)"
66.249.66.1 - - [14/Apr/2007:06:10:24 -0400] "GET /forums/index.php?PHPSESSID=dd44a6e47634b3bb070d32a86bd3450f&amp;topic=26.msg%25msg_id%25 HTTP/1.1" 404 314 "-" "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)"
66.249.66.1 - - [14/Apr/2007:06:12:01 -0400] "GET /forums/index.php?PHPSESSID=414a9821cfc7ca2a680af0e45f4fb306&amp;topic=77.msg%25msg_id%25 HTTP/1.1" 404 314 "-" "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)"
66.249.66.1 - - [14/Apr/2007:06:12:08 -0400] "GET /forums/index.php?PHPSESSID=18193069bf0c6130d68e2cb2f2479fe9&topic=77.msg287 HTTP/1.1" 404 314 "-" "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)"
66.249.66.1 - - [14/Apr/2007:06:12:13 -0400] "GET /forums/index.php?PHPSESSID=a5a6da3f230ab2619e3e1e307ad3db93&topic=23.msg249 HTTP/1.1" 404 314 "-" "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)"
66.249.66.1 - - [14/Apr/2007:06:12:41 -0400] "GET /forums/index.php?PHPSESSID=885a219aadbbba571a96fd3718033f6e&topic=10.msg373 HTTP/1.1" 404 314 "-" "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)"
66.249.66.1 - - [14/Apr/2007:06:12:58 -0400] "GET /forums/index.php?PHPSESSID=90bea6555c7dc57b1d728ca6062f140a&action=profile;u=480 HTTP/1.1" 404 314 "-" "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)"
66.249.66.1 - - [14/Apr/2007:06:13:51 -0400] "GET /forums/index.php?PHPSESSID=fc4a21c78791d7dcb7b1cab42c8417c9&topic=59.msg188 HTTP/1.1" 404 314 "-" "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)"
66.249.66.1 - - [14/Apr/2007:06:27:14 -0400] "GET /Class.htm HTTP/1.1" 200 31926 "-" "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)"

```

Same thing--my checking the pages late last night to the end.  And now we know who was looking for that older forum setup--googlebot.

So far, nothing at all out of the ordinary. 


Stripped apache2.conf: 

```
ServerRoot "/etc/apache2"
LockFile /var/lock/apache2/accept.lock
PidFile /var/run/apache2.pid
Timeout 300
KeepAlive On
MaxKeepAliveRequests 100
KeepAliveTimeout 15
<IfModule prefork.c>
StartServers         5
MinSpareServers      5
MaxSpareServers     10
MaxClients          20
MaxRequestsPerChild  0
</IfModule>
<IfModule worker.c>
StartServers         2
MaxClients         150 
MinSpareThreads     25
MaxSpareThreads     75
ThreadsPerChild     25
MaxRequestsPerChild  0
</IfModule>
<IfModule perchild.c>
NumServers           5
StartThreads         5
MinSpareThreads      5
MaxSpareThreads     10
MaxThreadsPerChild  20
MaxRequestsPerChild  0
AcceptMutex fcntl
</IfModule>
User www-data
Group www-data
LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %b" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent
ErrorLog /var/log/apache2/error.log
Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf
Include /etc/apache2/httpd.conf
Include /etc/apache2/ports.conf
Include /etc/apache2/conf.d/[^.#]*
Alias /icons/ "/usr/share/apache2/icons/"
<Directory "/usr/share/apache2/icons">
    Options Indexes MultiViews
    AllowOverride None
    Order allow,deny
    Allow from all
</Directory>
<IfModule mod_negotiation.c>
<IfModule mod_include.c>
    Alias /error/ "/usr/share/apache2/error/"
    <Directory "/usr/share/apache2/error">
        AllowOverride None
        Options IncludesNoExec
        AddOutputFilter Includes html
        AddHandler type-map var
        Order allow,deny
        Allow from all
        LanguagePriority en es de fr
        ForceLanguagePriority Prefer Fallback
    </Directory>
    ErrorDocument 400 /error/HTTP_BAD_REQUEST.html.var
    ErrorDocument 401 /error/HTTP_UNAUTHORIZED.html.var
    ErrorDocument 403 /error/HTTP_FORBIDDEN.html.var
    ErrorDocument 404 /error/HTTP_NOT_FOUND.html.var
    ErrorDocument 405 /error/HTTP_METHOD_NOT_ALLOWED.html.var
    ErrorDocument 408 /error/HTTP_REQUEST_TIME_OUT.html.var
    ErrorDocument 410 /error/HTTP_GONE.html.var
    ErrorDocument 411 /error/HTTP_LENGTH_REQUIRED.html.var
    ErrorDocument 412 /error/HTTP_PRECONDITION_FAILED.html.var
    ErrorDocument 413 /error/HTTP_REQUEST_ENTITY_TOO_LARGE.html.var
    ErrorDocument 414 /error/HTTP_REQUEST_URI_TOO_LARGE.html.var
    ErrorDocument 415 /error/HTTP_SERVICE_UNAVAILABLE.html.var
    ErrorDocument 500 /error/HTTP_INTERNAL_SERVER_ERROR.html.var
    ErrorDocument 501 /error/HTTP_NOT_IMPLEMENTED.html.var
    ErrorDocument 502 /error/HTTP_BAD_GATEWAY.html.var
    ErrorDocument 503 /error/HTTP_SERVICE_UNAVAILABLE.html.var
    ErrorDocument 506 /error/HTTP_VARIANT_ALSO_VARIES.html.var
</IfModule>
</IfModule>
DirectoryIndex index.html index.cgi index.pl index.php index.xhtml
AccessFileName .htaccess
<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
</Files>
UseCanonicalName Off
TypesConfig /etc/mime.types
DefaultType text/plain
HostnameLookups Off
IndexOptions FancyIndexing VersionSort
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
AddIcon /icons/back.gif ..
AddIcon /icons/hand.right.gif README
AddIcon /icons/folder.gif ^^DIRECTORY^^
AddIcon /icons/blank.gif ^^BLANKICON^^
DefaultIcon /icons/unknown.gif
ReadmeName README.html
HeaderName HEADER.html
IndexIgnore .??* *~ *# HEADER* RCS CVS *,t
AddEncoding x-compress Z
AddEncoding x-gzip gz tgz
AddLanguage da .dk
AddLanguage nl .nl
AddLanguage en .en
AddLanguage et .et
AddLanguage fr .fr
AddLanguage de .de
AddLanguage el .el
AddLanguage it .it
AddLanguage ja .ja
AddLanguage pl .po
AddLanguage ko .ko
AddLanguage pt .pt
AddLanguage no .no
AddLanguage pt-br .pt-br
AddLanguage ltz .ltz
AddLanguage ca .ca
AddLanguage es .es
AddLanguage sv .se
AddLanguage cz .cz
AddLanguage ru .ru
AddLanguage tw .tw
AddLanguage zh-tw .tw
LanguagePriority en da nl et fr de el it ja ko no pl pt pt-br ltz ca es sv tw
AddCharset ISO-8859-1  .iso8859-1  .latin1
AddCharset ISO-8859-2  .iso8859-2  .latin2 .cen
AddCharset ISO-8859-3  .iso8859-3  .latin3
AddCharset ISO-8859-4  .iso8859-4  .latin4
AddCharset ISO-8859-5  .iso8859-5  .latin5 .cyr .iso-ru
AddCharset ISO-8859-6  .iso8859-6  .latin6 .arb
AddCharset ISO-8859-7  .iso8859-7  .latin7 .grk
AddCharset ISO-8859-8  .iso8859-8  .latin8 .heb	
AddCharset ISO-8859-9  .iso8859-9  .latin9 .trk
AddCharset ISO-2022-JP .iso2022-jp .jis
AddCharset ISO-2022-KR .iso2022-kr .kis
AddCharset ISO-2022-CN .iso2022-cn .cis
AddCharset Big5        .Big5       .big5
AddCharset WINDOWS-1251 .cp-1251   .win-1251
AddCharset CP866       .cp866
AddCharset KOI8-r      .koi8-r .koi8-ru
AddCharset KOI8-ru     .koi8-uk .ua
AddCharset ISO-10646-UCS-2 .ucs2
AddCharset ISO-10646-UCS-4 .ucs4
AddCharset UTF-8       .utf8
AddCharset GB2312      .gb2312 .gb 
AddCharset utf-7       .utf7
AddCharset utf-8       .utf8
AddCharset big5	       .big5 .b5
AddCharset EUC-TW      .euc-tw	
AddCharset EUC-JP      .euc-jp
AddCharset EUC-KR      .euc-kr
AddCharset shift_jis   .sjis
AddType application/x-tar .tgz
<FilesMatch "\.shtml(\..+)?$">
    SetOutputFilter INCLUDES
</FilesMatch>
BrowserMatch "Mozilla/2" nokeepalive
BrowserMatch "MSIE 4\.0b2;" nokeepalive downgrade-1.0 force-response-1.0
BrowserMatch "RealPlayer 4\.0" force-response-1.0
BrowserMatch "Java/1\.0" force-response-1.0
BrowserMatch "JDK/1\.0" force-response-1.0
BrowserMatch "Microsoft Data Access Internet Publishing Provider" redirect-carefully
BrowserMatch "^WebDrive" redirect-carefully
BrowserMatch "^gnome-vfs" redirect-carefully 
BrowserMatch "^WebDAVFS/1.[012]" redirect-carefully
Include /etc/apache2/sites-enabled/[^.#]*
ServerName localhost

```
I haven't altered this file, by the way.  It's as the install meant it to be.  That is, unless there is something else that alters apache2.conf that I don't know of.  


Pgrep apache2 from immediately after a reboot:  

```
4512
4575
4576
4577
4578
4579

```

When it takes a nap:  

```
4512
4575
4576
4577
4578
4579
5849
6854
9056
10307
10312

```

And just now, pgrep apache2 after a stop:  

{nothing}


After starting the service (from a stop, not a restart)

```
22117
22121
22122
22123
22124
22125

```

It's still not serving up pages after this stop & start process; a direct restart does the same thing--nothing.  It takes a complete reboot to temporarily fix this mess.

---

### Post by amohanty on 2007-04-15
among the myriad of reason two possibilities could be:
1. php has gone crazy.
2. the os just does not like apache serving request.

Can you see anything of interest in the php logs or via dmesg?

AM

---

### Post by NPALeech on 2007-04-15
I'm having a similar problem on Dapper. I can access my site locally all the time, I can access all the time using my local IP, but can only access it using my WAN IP only some of the time. It's as if it just stops serving pages to the outside world after a while. The thing is, it seems to change every ten minutes or so. "Unable to connect" for about ten minutes, then I can access it for ten. Rinse and repeat.

To investigate further I installed elinks on the server itself. From there I tried to access my site via my WAN IP and it gave me a "Connection refused" error. This is odd because my router is setup to use static IP's and all the necissary ports are forwarded. So I'm not understanding why I'm getting these particular errors sometimes, when it works fine others.

---

### Post by amohanty on 2007-04-16
Another thing to try would be to use tcpdump to see if the os is even accepting the packets. 
So fire up tcp dump with the packet type tcp and dst your host ip and dst port 80 and see if you can hit the site from another machine. 
Manual: [http://www.tcpdump.org/tcpdump_man.html](http://www.tcpdump.org/tcpdump_man.html)

10:48 PM: ~
=ROOT= # tcpdump -i eth0 -a -N -q tcp dst port 80

You will need to run as root and make sure you are not using a web browser. 

HTH
AM

---

### Post by Kinslayer on 2007-04-16
The php logs are clean, and php pages still pull up on localhost when this problem occurs.  Dmesg did uncover another, unrelated problem though.  It seems my cd/dvd's weren't mounting properly, causing startup & shutdown to take 5-10 minutes each.  This only added to the frustration of having to reboot multiple times per day.  That problem is fixed & I'll post the solution to the appropriate threads where others were having the same issues.  

Tcpdump is showing that the packets are getting through (1602 packets captured, 3204 packets received by filter, 0 packets dropped by kernel) but it's not serving pages when I hit it with another machine.  I saw Googlebot & some other browsers during this, but the other computer I was using just timed out after a couple of wasted minutes.  The same thing happened when I tried using a proxy on either machine.  

Would a reinstall of the LAMP stack work?  Would it need to be uninstalled first?  Would a simple "apt-get apache2..." help or would that hose everything I've created so far on my website?

---

### Post by amohanty on 2007-04-16
> The php logs are clean, and php pages still pull up on localhost when this problem occurs

This is very interesting, which tells me that apache is fine and dandy, something else is blocking your incoming requests which you also mentioned previously.

Are you running a firewall like firestarter or something? can you post the output of **ps aux**.

Also when you ran tcpdump were you trying to hit it from another machine?
Also in the tcpdump command, can you change the **dst** to **src** to see if apache is receiving the packets and responding at all?

AM

PS: you do not need to lose any data. I think in edgy apache2 serves out of /var/www. I don't remember where the php files are served out of. I usually put them in a custom folder and symlinked to /var/www. So just backup your files , _completely_ remove apache2 and php and install it again.

HTH

---

### Post by Kinslayer on 2007-04-18
No firewall, at least not this time around.  I realised that Ubuntu's native security seemed rather good, and the firewall would just let me screw around with things that should probably be left alone.  The dst/src switch gives essentially the same results:  1200 captured, 2400 received, 0 dropped.

PS AUX:

```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.1   1632   412 ?        Ss   Apr16   0:01 /sbin/init spla
root         2  0.0  0.0      0     0 ?        S    Apr16   0:00 [migration/0]
root         3  0.0  0.0      0     0 ?        SN   Apr16   0:00 [ksoftirqd/0]
root         4  0.0  0.0      0     0 ?        S    Apr16   0:00 [watchdog/0]
root         5  0.0  0.0      0     0 ?        S<   Apr16   0:00 [events/0]
root         6  0.0  0.0      0     0 ?        S<   Apr16   0:00 [khelper]
root         7  0.0  0.0      0     0 ?        S<   Apr16   0:00 [kthread]
root         9  0.0  0.0      0     0 ?        S<   Apr16   0:00 [kblockd/0]
root        10  0.0  0.0      0     0 ?        S<   Apr16   0:00 [kacpid]
root        11  0.0  0.0      0     0 ?        S<   Apr16   0:00 [kacpi_notify]
root        94  0.0  0.0      0     0 ?        S<   Apr16   0:00 [kseriod]
root       128  0.0  0.0      0     0 ?        S    Apr16   0:00 [pdflush]
root       129  0.0  0.0      0     0 ?        S    Apr16   0:02 [kswapd0]
root       130  0.0  0.0      0     0 ?        S<   Apr16   0:00 [aio/0]
root      1716  0.0  0.0      0     0 ?        S<   Apr16   0:00 [khubd]
root      1795  0.0  0.0      0     0 ?        S<   Apr16   0:00 [kjournald]
root      1868  0.0  0.1   1600   372 ?        Ss   Apr16   0:00 //sbin/logd
root      2014  0.0  0.1   2612   380 ?        S<s  Apr16   0:00 /sbin/udevd --d
root      2749  0.0  0.0      0     0 ?        S<   Apr16   0:00 [shpchpd]
root      2876  0.0  0.0      0     0 ?        S<   Apr16   0:00 [kpsmoused]
root      2943  0.0  0.0      0     0 ?        S<   Apr16   0:00 [kgameportd]
root      3035  0.0  0.0      0     0 ?        S<   Apr16   0:00 [scsi_eh_0]
root      3036  0.0  0.0      0     0 ?        S<   Apr16   0:00 [usb-storage]
dhcp      3390  0.0  0.2   2396   564 ?        S<s  Apr16   0:00 dhclient3 -pf /
root      3595  0.0  0.1   1596   328 tty1     Ss+  Apr16   0:00 /sbin/getty 384
root      3596  0.0  0.1   1600   328 tty2     Ss+  Apr16   0:00 /sbin/getty 384
root      3597  0.0  0.1   1596   328 tty3     Ss+  Apr16   0:00 /sbin/getty 384
root      3598  0.0  0.1   1600   328 tty4     Ss+  Apr16   0:00 /sbin/getty 384
root      3599  0.0  0.1   1596   328 tty5     Ss+  Apr16   0:00 /sbin/getty 384
root      3600  0.0  0.1   1596   328 tty6     Ss+  Apr16   0:00 /sbin/getty 384
root      3809  0.0  0.1   2200   416 ?        Ss   Apr16   0:00 /usr/sbin/acpid
root      3932  0.0  0.1   1728   336 ?        Ss   Apr16   0:00 /bin/dd bs 1 if
klog      3934  0.0  0.1   2424   412 ?        Ss   Apr16   0:00 /sbin/klogd -P
root      4006  0.0  0.2  11800   596 ?        Ss   Apr16   0:00 /usr/sbin/gdm
root      4007  0.0  0.3  12156   884 ?        S    Apr16   0:00 /usr/sbin/gdm
root      4026  0.6  7.1  30148 18248 tty7     Ss+  Apr16  13:23 /usr/X11R6/bin/
root      4077  0.0  0.1   4904   380 ?        Ss   Apr16   0:00 /usr/sbin/hpiod
hplip     4080  0.0  0.3   9676   912 ?        S    Apr16   0:00 python /usr/sbi
root      4133  0.0  0.1   1656   272 ?        S    Apr16   0:00 /bin/sh /usr/bi
mysql     4199  0.0  2.3 130320  5916 ?        Sl   Apr16   0:16 /usr/sbin/mysql
root      4200  0.0  0.1   1584   376 ?        S    Apr16   0:00 logger -p daemo
103       4281  0.0  0.2   2176   724 ?        Ss   Apr16   0:02 /usr/bin/dbus-d
106       4298  0.0  0.9   7108  2544 ?        Ss   Apr16   0:41 /usr/sbin/hald
root      4299  0.0  0.2   2912   752 ?        S    Apr16   0:00 hald-runner
106       4342  0.0  0.1   2028   504 ?        S    Apr16   0:00 /usr/lib/hal/ha
root      4346  0.0  0.1   1904   500 ?        S    Apr16   0:38 /usr/lib/hal/ha
106       4348  0.0  0.2   2024   536 ?        S    Apr16   0:00 /usr/lib/hal/ha
106       4364  0.0  0.2   2028   600 ?        S    Apr16   0:02 /usr/lib/hal/ha
106       4366  0.0  0.2   2032   604 ?        S    Apr16   0:00 /usr/lib/hal/ha
root      4386  0.0  0.2  13616   604 ?        S    Apr16   0:00 perl /usr/share
nobody    4413  0.0  0.2   1936   596 ?        Ss   Apr16   0:00 /usr/bin/no-ip
root      4475  0.0  0.1   2072   484 ?        Ss   Apr16   0:00 /usr/sbin/hcid
root      4482  0.0  0.1   1668   344 ?        Ss   Apr16   0:00 /usr/sbin/sdpd
root      4493  0.0  0.0      0     0 ?        S<   Apr16   0:00 [krfcommd]
daemon    4525  0.0  0.1   1852   304 ?        Ss   Apr16   0:00 /usr/sbin/atd
root      4538  0.0  0.1   2192   504 ?        Ss   Apr16   0:00 /usr/sbin/cron
1000      4561  0.0  1.7  37512  4420 ?        Ss   Apr16   0:01 x-session-manag
root      4612  0.0  0.7  20404  1944 ?        Ss   Apr16   0:00 /usr/sbin/apach
1000      4672  0.0  0.0   4480   252 ?        Ss   Apr16   0:00 /usr/bin/ssh-ag
1000      4675  0.0  0.1   2532   392 ?        S    Apr16   0:00 /usr/bin/dbus-l
1000      4687  0.0  0.2   2180   720 ?        Ss   Apr16   0:00 /usr/bin/dbus-d
www-data  4688  0.0  2.1  30452  5492 ?        S    Apr16   1:34 /usr/sbin/apach
www-data  4691  0.0  3.7  30316  9684 ?        S    Apr16   1:41 /usr/sbin/apach
www-data  4692  0.0  2.5  30316  6640 ?        S    Apr16   1:31 /usr/sbin/apach
1000      4694  0.0  0.9   6088  2372 ?        S    Apr16   0:00 /usr/lib/libgco
1000      4697  0.0  0.1   2592   480 ?        S    Apr16   0:00 /usr/bin/gnome-
1000      4700  0.0  1.1  28748  3052 ?        Sl   Apr16   0:04 /usr/lib/contro
1000      4710  0.0  0.1   1660   260 ?        Ss   Apr16   0:00 /bin/sh -c /usr
1000      4711  0.0  0.2   4552   592 ?        S    Apr16   0:00 /usr/bin/esd -t
1000      4716  0.0  2.1  15896  5604 ?        Ss   Apr16   0:16 /usr/bin/metaci
1000      4721  0.0  3.5  42088  9184 ?        Ss   Apr16   0:12 gnome-panel --s
1000      4723  0.0  2.0  77196  5332 ?        Ss   Apr16   0:01 nautilus --no-d
1000      4727  0.0  0.6  39512  1736 ?        Ssl  Apr16   0:00 /usr/lib/bonobo
1000      4729  0.0  0.8  18412  2264 ?        Ss   Apr16   0:00 gnome-volume-ma
1000      4736  0.0  1.3  32736  3348 ?        Ss   Apr16   0:00 update-notifier
1000      4739  0.0  0.5   8252  1516 ?        S    Apr16   0:00 /usr/lib/gnome-
1000      4755  0.0  7.6  51504 19544 ?        Ssl  Apr16   0:20 /usr/bin/perl -
1000      4756  0.0  0.1   3096   380 ?        Ss   Apr16   0:00 imwheel -k -b 6
1000      4767  0.0  1.3  67228  3484 ?        Ssl  Apr16   0:00 /usr/lib/evolut
1000      4821  0.0  1.1  47344  2932 ?        Ss   Apr16   0:40 gnome-cups-icon
1000      4834  0.0  1.3  31452  3492 ?        Ss   Apr16   0:03 gnome-power-man
1000      4838  0.0  1.3  64356  3504 ?        S    Apr16   0:00 /usr/lib/gnome-
1000      4861  0.0  0.2   2508   560 ?        S    Apr16   0:00 /usr/lib/nautil
1000      4868  0.0  0.7  56972  1792 ?        Sl   Apr16   0:00 /usr/lib/evolut
1000      4874  0.0  0.9  27480  2420 ?        Sl   Apr16   0:00 /usr/lib/evolut
1000      4910  0.0  3.1  65356  8092 ?        Sl   Apr16   0:02 python /usr/lib
1000      4912  0.0  1.7  52508  4384 ?        Sl   Apr16   0:01 mono /usr/lib/t
1000      4914  0.0  2.3  70320  6132 ?        S    Apr16   0:01 /usr/lib/gnome-
1000      4936  0.0  1.4  34560  3784 ?        S    Apr16   0:00 /usr/lib/gnome-
1000      4951  0.0  1.3  15856  3568 ?        Ss   Apr16   0:05 gnome-screensav
www-data  4978  0.0  5.2  30292 13516 ?        S    Apr16   1:47 /usr/sbin/apach
www-data  5484  0.0  5.6  30316 14412 ?        S    Apr16   1:43 /usr/sbin/apach
cupsys   18739  0.0  0.4   4568  1048 ?        SNs  Apr17   0:19 /usr/sbin/cupsd
www-data  8012  0.2  5.2  30332 13360 ?        S    Apr17   1:30 /usr/sbin/apach
www-data  8930  0.1  4.8  30404 12328 ?        S    Apr17   0:45 /usr/sbin/apach
www-data  8960  0.1  4.5  30052 11708 ?        S    Apr17   0:47 /usr/sbin/apach
www-data  8967  0.1  5.4  30540 13952 ?        S    Apr17   0:48 /usr/sbin/apach
www-data  8978  0.0  1.5  30360  3968 ?        S    Apr17   0:29 /usr/sbin/apach
root     10311  0.0  0.0      0     0 ?        S    Apr17   0:00 [pdflush]
root     22791  0.0  0.2   1652   620 ?        SNs  07:36   0:00 /sbin/syslogd
1000     25373 20.2 17.6 151952 45244 ?        Sl   09:23   0:23 /usr/lib/firefo
1000     25387  0.0  0.0      0     0 ?        Z    09:23   0:00 [net] <defunct>
1000     25431  9.2  5.7  53344 14752 ?        Sl   09:24   0:00 gnome-terminal
1000     25437  0.0  0.3   2508   808 ?        S    09:25   0:00 gnome-pty-helpe
1000     25438  5.6  1.1   5404  2968 pts/0    Ss   09:25   0:00 bash
1000     25457  0.0  0.3   2472   988 pts/0    R+   09:25   0:00 ps aux
```

Let's hope that it's some odd glitch that the upgrade to Feisty fixes tomorrow.  Then a reinstall of LAMP, then... I don't know...

And by the way, thank you very much for all of your help.

---

### Post by pgeorge83 on 2007-04-18
Hmm.  Can you access other services via WAN, when you cannot access Apache via WAN?

-Phillip

---

### Post by Kinslayer on 2007-04-18
Meaning do I still have a 'net connection?  Yes, the only indication that something's wrong is when I try to pull up my own site.  One would think that it wouldn't be difficult to browse pages on the same box...

If you mean is it pingable, I don't know.  I believe that's handled by the router.

---

### Post by amohanty on 2007-04-19
Have you by any chance setup quotas for processes?
Try setting up MaxRequestsPerChild  to be something like 10, so that the apache child gets killed after serving 10 requests or so. In you case it never dies.

AM

---

### Post by Kinslayer on 2007-04-22
Whatever the problem was, updating to 7.04 (along with the update to Apache2.5) seems to have fixed it.  It's been a couple of days now with no problems.  

The only problem was it killed Drupal, but that's a whole other set of issues, and one I think I know how to fix.  

Thank you for all of your kind assistance.

---

