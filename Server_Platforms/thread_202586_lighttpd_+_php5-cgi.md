---
title: "lighttpd + php5-cgi"
date: 2006-06-23
forum: Server Platforms
---

### Post by stocksy on 2006-06-23
I'm trying to set up lighttpd with php5, but I'm not having much luck.  I installed the php5-cgi package, and php5-cgi -v gives

```

stocksy@thinkpad:~$ php5-cgi -v
PHP 5.1.2 (cgi-fcgi) (built: May 18 2006 04:59:16)
Copyright (c) 1997-2006 The PHP Group
Zend Engine v2.1.0, Copyright (c) 1998-2006 Zend Technologies

```

I enabled the fastcgi module with lighty-enable-mod, but I had to edit /etc/lighttpd/conf-enabled/10-fastcgi.conf to refer to php5 rather than 4.

The server starts fine and will serve html pages, but if I request a php page, lighttpd dies with the following error in /var/log/lighttpd/error.log:

```

2006-06-23 22:28:01: (mod_fastcgi.c.2691) write-req: error 0x080a3d70 0 9000 0 

```

Does lighttpd even work with php5?

---

### Post by Paerez on 2006-06-23
I can assure you that lighttpd works with php5, as I have it running on my gentoo box. I tried to instal lighttpd with php5 and fastcgi on my ubuntu lappy, but it didn't go well. Keep trying though!

I am gonna give it another shot this weekend since I want to experiment with ruby-on-rails.

---

### Post by stocksy on 2006-07-08
Well, thanks to the wonders of #lighttpd and the internet in general, here's the answer:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=362827](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=362827)

Essentially, just replace the 'fastcgi.server =' option in /etc/lighttpd/conf-enabled/10-fastcgi.conf with:

```

fastcgi.server    = ( ".php" =>
             	      ((
                          "bin-path" => "/usr/bin/php5-cgi",
			  "socket" => "/tmp/php.socket",
			  "max-procs" => 2,
			  "idle-timeout" => 20,
                          "bin-environment" => ( 
                            "PHP_FCGI_CHILDREN" => "4",
                            "PHP_FCGI_MAX_REQUESTS" => "10000"
                          ),
                         "bin-copy-environment" => (
                            "PATH", "SHELL", "USER"
                           ),
"broken-scriptfilename" => "enable"
				        )
				      )
			        )

```

---

