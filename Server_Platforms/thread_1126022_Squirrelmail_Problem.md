---
title: "Squirrelmail Problem"
date: 2009-04-15
forum: Server Platforms
---

### Post by DaleHUtch on 2009-04-15
Greetings,

I'm still kinda new to Linux and would like some help with a problem I'm having. 

I recently got a Ubuntu 8.10 Server up and running with Postfix, Courier, MySQL, and Apache2. I installed SquirrelMail last and it seems to work. I am able to use Firefox and view the login screen. The problem I have is when I use a username and password the next screen is blank. I've run out leads trying to figure out what could be wrong. I checked the logs and I don't see anything. I installed the debugger for SquirrelMail and the following is what appears after I try to log in... 

Any suggestions is greatly appreciated...

DH
----------------------------------------------


Notice: A session had already been started - ignoring session_start() in /usr/share/squirrelmail/functions/global.php on line 388


Stack Trace:

session_start()
/usr/share/squirrelmail/functions/global.php
line 388

    sqsession_start()
    /usr/share/squirrelmail/functions/global.php
    line 368

        sqsession_is_active()
        /usr/share/squirrelmail/functions/global.php
        line 229

            sqsession_register("http://10.10.5.25", "sq_base_url")
            /usr/share/squirrelmail/functions/strings.php
            line 350

                get_location()
                /usr/share/squirrelmail/src/redirect.php
                line 37



My browser information:
  Mozilla/5.0 (Windows; U; Windows NT 6.1; en-US; rv:1.9.0.8) Gecko/2009032609 Firefox/3.0.8

My web server information:
  PHP Version 5.2.6-2ubuntu4.1
  PHP Extensions (List)
    * 0 = zip
    * 1 = xmlwriter
    * 2 = libxml
    * 3 = xml
    * 4 = wddx
    * 5 = tokenizer
    * 6 = sysvshm
    * 7 = sysvsem
    * 8 = sysvmsg
    * 9 = session
    * 10 = SimpleXML
    * 11 = sockets
    * 12 = soap
    * 13 = SPL
    * 14 = shmop
    * 15 = standard
    * 16 = Reflection
    * 17 = posix
    * 18 = mime_magic
    * 19 = mbstring
    * 20 = json
    * 21 = iconv
    * 22 = hash
    * 23 = gettext
    * 24 = ftp
    * 25 = filter
    * 26 = exif
    * 27 = dom
    * 28 = dba
    * 29 = date
    * 30 = ctype
    * 31 = calendar
    * 32 = bz2
    * 33 = bcmath
    * 34 = zlib
    * 35 = pcre
    * 36 = openssl
    * 37 = xmlreader
    * 38 = apache2handler
    * 39 = curl
    * 40 = gd
    * 41 = imagick
    * 42 = imap
    * 43 = mcrypt
    * 44 = memcache
    * 45 = mhash
    * 46 = ming
    * 47 = mysql
    * 48 = mysqli
    * 49 = PDO
    * 50 = pdo_mysql
    * 51 = pdo_sqlite
    * 52 = pspell
    * 53 = recode
    * 54 = snmp
    * 55 = SQLite
    * 56 = tidy
    * 57 = xmlrpc
    * 58 = xsl

SquirrelMail-specific information:
  Version:  1.4.15
  Plugins (List)
    * 0 = compatibility
    * 1 = change_sqlpass
    * 2 = debugger

My IMAP server information:
  Server type:  courier
  Server info:  * OK [HIDDEN] IMAP4rev1 UIDPLUS CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA IDLE ACL ACL2=UNION STARTTLS] Courier-IMAP ready. Copyright 1998-2008 Double Precision, Inc.  See COPYING for distribution information.
  Capabilities:  IMAP4rev1 UIDPLUS CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA IDLE ACL ACL2=UNION STARTTLS

---

### Post by DaleHUtch on 2009-04-16
Figured it out...


Config.php was messed up...

---

### Post by woodbot on 2010-03-19
> **DaleHUtch said:**
> Figured it out...


Config.php was messed up...

 Hi can you please tell me how you fixed it? Is there a way to debug it? Below is my config.php. My table names are probably a little different...PS of what use is $csp_debug???

---

### Post by HermanAB on 2010-03-20
Howdy,

Glad you got squirrel to worrk.  However, my beef with squirrel is that it is fugly....

You should try RoundCube instead.

---

### Post by DaleHUtch on 2010-05-13
I heard of this roundcube. 

I will take a look.

---

