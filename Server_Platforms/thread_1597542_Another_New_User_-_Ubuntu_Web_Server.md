---
title: "Another New User - Ubuntu Web Server"
date: 2010-10-15
forum: Server Platforms
---

### Post by reklaw on 2010-10-15
Another new user...

I'm trying to run an Ubuntu web server, the purpose of which is to host a small file-sharing site, forum, and wiki. I have no experience with Ubuntu.

So far I've setup mediawiki and phpbb3 and am able to access them internally. I've also setup ssh and am able to access the server remotely, but the connection seems to be too slow for any thing other than the command line to open remotely. For example if I am installing phpbb3 and it is asking for the sql config I just see a blue screen. Locally if I use ssh to connect it has no problems.

When I try to connect to the server through the web I see the basic Apache page saying nothing is configured which is correct, but if I browse to the /mediawiki site or the /phpbb site it will just hang.

I've moved the server to the DMZ of my firewall/switch hoping that would help but it doesn't seem to have improved anything. Before this I forwarded port 80 to the server.

Any help would be greatly appreciated. Please let me know if any logs or other information needs to be posted.

Thanks,
Lee

---

### Post by dapperdanny77 on 2010-10-15
you can access your php apps locally - means you use a locally installed firefox/whatever - right?

did you change the default ubuntu apache config?

you can see accesses to apache in /var/log/apache2
theres an access log and an error log - if you don't see any entries in the access log your requests not reaching apache

---

### Post by reklaw on 2010-10-15
Sorry, by locally I mean from my local network. I haven’t attempted to access anything from the actual server. It’s just the command line. Maybe a bad choice for starting out but I figured I’d just jump in the deep end and learn to swim.

I haven’t made any changes to the default config other than the changes recommended during the package installs of phpbb3 and mediawiki. 

What should I use to open the access log? I’m currently using PuTTY to SSH into the webserver.

Thanks!

---

### Post by dapperdanny77 on 2010-10-15
you can use less to open files for viewing

```

less filename

```

---

### Post by dapperdanny77 on 2010-10-15
checkout 

[https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

to see what's necessary for a working lamp installation on ubuntu

---

### Post by reklaw on 2010-10-15
LAMP server is installed and running fine. Checked the access logs at lunch using nano and tested them while I was sitting there with my phone.

When I attempt to open Mediawiki with my phone is showed up in the log with 3 different lines. 

"GET /mediawiki HTTP/1.1" 301 573 "-" "Opera/9.80 (Android; Opera Mini/5.1.21126
"GET /mediawiki/ HTTP/1.1" 301 683 "-" "Opera/9.80 (Android; Opera Mini/5.1.21126 
"GET /mediawiki/index.php/Main_Page HTTP/1.1" "Opera/9.80 (Android; Opera Mini/5.1.21126

And there were two similar lines for the phpBB attempted access as well. So the request is reaching the server without any issues.

Just tried opening up the error log using the less command but that doesn't work over SSH either.

Thanks!

---

### Post by reklaw on 2010-10-15
Update

On my home network mediawiki is now extremely slow. The first time I open a page up it takes a good 30 seconds to load. phpBB on the other hand is running fine.

Thanks!
Lee

---

### Post by SeijiSensei on 2010-10-16
301 is the [reply code]("http://www.ietf.org/rfc/rfc1945.txt") for "moved permanently."  Usually that happens if there's a [Redirect]("http://httpd.apache.org/docs/2.0/mod/mod_alias.html#redirect") directive in Apache.  See if there's one in the mediawiki configuration and determine why it's there.  I'm guessing it's a configuration error.

---

### Post by reklaw on 2010-10-16
Thanks Sensei, 

Here are the log files and config files.

/etc/mediawiki/apache.conf file

# Uncomment this to add an alias.
# This does not work properly with virtual hosts..

Alias /mediawiki /var/lib/mediawiki

<Directory /var/lib/mediawiki/>
        Options +FollowSymLinks
        AllowOverride All
        order allow,deny
        allow from all
</Directory>

# some directories must be protected
<Directory /var/lib/mediawiki/config>
        Options -FollowSymLinks
        AllowOverride None
</Directory>
<Directory /var/lib/mediawiki/upload>
        Options -FollowSymLinks

error log when I tried to open mediawiki and phpbb from a remote machine

[Sat Oct 16 00:11:05 2010] [error] [client 208.109.168.113] PHP Warning:  dba_o$
[Sat Oct 16 00:11:06 2010] [error] [client 208.109.168.113] PHP Warning:  dba_o$
[Sat Oct 16 00:11:07 2010] [error] [client 208.109.168.113] PHP Warning:  dba_o$
[Sat Oct 16 00:11:08 2010] [error] [client 208.109.168.113] PHP Warning:  dba_o$
[Sat Oct 16 00:11:09 2010] [error] [client 208.109.168.113] PHP Warning:  dba_o$
[Sat Oct 16 00:11:10 2010] [error] [client 208.109.168.113] PHP Warning:  dba_o$
[Sat Oct 16 00:11:11 2010] [error] [client 208.109.168.113] PHP Warning:  dba_o$
[Sat Oct 16 00:11:12 2010] [error] [client 208.109.168.113] PHP Warning:  dba_o$
[Sat Oct 16 00:11:12 2010] [error] [client 208.109.168.113] PHP Warning:  dba_o$
[Sat Oct 16 00:11:12 2010] [error] [client 208.109.168.113] PHP Warning:  dba_o$
[Sat Oct 16 00:11:12 2010] [error] [client 208.109.168.113] PHP Warning:  dba_o$
[Sat Oct 16 00:11:12 2010] [error] [client 208.109.168.113] PHP Warning:  dba_o$

Access files when I tried to open mediawiki and phpbb from a remote machine

208.109.168.113 - - [16/Oct/2010:00:10:34 -0700] "GET /phpb HTTP/1.1" 404 504 "$
208.109.168.113 - - [16/Oct/2010:00:10:37 -0700] "GET /phpbb HTTP/1.1" 301 568 $
208.109.168.113 - - [16/Oct/2010:00:10:37 -0700] "GET /phpbb/ HTTP/1.1" 200 406$
208.109.168.113 - - [16/Oct/2010:00:10:45 -0700] "GET / HTTP/1.1" 200 485 "-" "$
208.109.168.113 - - [16/Oct/2010:00:10:46 -0700] "GET /favicon.ico HTTP/1.1" 40$
208.109.168.113 - - [16/Oct/2010:00:10:52 -0700] "GET /mediawiki HTTP/1.1" 301 $
208.109.168.113 - - [16/Oct/2010:00:10:52 -0700] "GET /mediawiki/ HTTP/1.1" 301$
208.109.168.113 - - [16/Oct/2010:00:11:02 -0700] "GET /mediawiki/index.php/Main$

I didn't see any redirects in there. Thanks for the idea!

---

