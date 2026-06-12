---
title: "Ruby, Rails, Apache2 and FastCGI"
date: 2005-04-21
forum: Server Platforms
---

### Post by Rollerbob on 2005-04-21
I'm having problems setting up my Rails app to use FastCGI with Apache2. I'm pretty sure I have the right libraries installed and I have carefully followed the howtos on the Rails site for setting up fcgi, so I'm beginning to suspect that it might be something to do with Ubuntu/Debian's support for FastCGI. 

Weirdly, the app does work some of the time, however, most of the time when I load it, my machine grinds to a halt, and using Top I can see multiple processes of 'dispatch.fcgi'. After about 3 minutes of this, i get the following error message in the browser: 'Application error Rails application failed to start properly'. 

Here's the sort of thing that appears in my error logs:

[Thu Apr 21 15:39:18 2005] [warn] FastCGI: (dynamic) server "/var/www/test/public/dispatch.fcgi" started (pid 15599)
[Thu Apr 21 15:39:21 2005] [warn] FastCGI: (dynamic) server "/var/www/test/public/dispatch.fcgi" started (pid 15602)
[Thu Apr 21 15:39:24 2005] [warn] FastCGI: (dynamic) server "/var/www/test/public/dispatch.fcgi" started (pid 15604)
[Thu Apr 21 15:39:27 2005] [warn] FastCGI: scheduled the start of the last (dynamic) server "/var/www/test/public/dispatch.fcgi" process: reached dynamicMaxClassProcs (10)
[Thu Apr 21 15:39:27 2005] [warn] FastCGI: (dynamic) server "/var/www/test/public/dispatch.fcgi" started (pid 15607)
[Thu Apr 21 15:39:45 2005] [error] [client 127.0.0.1] FastCGI: comm with (dynamic) server "/var/www/test/public/dispatch.fcgi" aborted: (first read) idle timeout (30 sec)
[Thu Apr 21 15:39:46 2005] [error] [client 127.0.0.1] FastCGI: incomplete headers (0 bytes) received from server "/var/www/test/public/dispatch.fcgi"
[Thu Apr 21 15:46:00 2005] [warn] FastCGI: (dynamic) server "/var/www/test/public/dispatch.fcgi" (pid 15607) termination signaled
Couldn't write to /var/log/fastcgi.crash.log (exit [SystemExit])
[Thu Apr 21 15:46:02 BST 2005] Dispatcher failed to catch: exit (SystemExit)
  /usr/lib/ruby/gems/1.8/gems/fcgi-0.8.5/./fcgi.rb:10:in `exit'
  /usr/lib/ruby/gems/1.8/gems/fcgi-0.8.5/./fcgi.rb:10
  /usr/lib/ruby/gems/1.8/gems/fcgi-0.8.5/./fcgi.rb:10:in `call'
  /usr/lib/ruby/gems/1.8/gems/fcgi-0.8.5/./fcgi.rb:597:in `each'
  /usr/lib/ruby/gems/1.8/gems/fcgi-0.8.5/./fcgi.rb:597:in `each_cgi'
  /var/www/test/public/dispatch.fcgi:19
FCGI process 15607 killed by this error
[Thu Apr 21 15:46:29 2005] [warn] FastCGI: (dynamic) server "/var/www/test/public/dispatch.fcgi" (pid 15607) terminated by calling exit with status '0'
[Thu Apr 21 15:51:01 2005] [warn] FastCGI: (dynamic) server "/var/www/test/public/dispatch.fcgi" (pid 15604) termination signaled


Has anyone else run into this problem and successfully got round it using Apache2 and FastCGI? I have read on other mailling lists that Apache1.3 would work better with FastCGI, however, when browsing through the packages in Synaptic, Apache1.3 doesn't seem to be the supported httpd server with Ubuntu(?).

Matt

---

### Post by alastair on 2005-04-21
If you want to test Apache 1.3, go ahead. I'm using it on 5.04 without problems.

ii  apache-common    1.3.33-4      support files for all Apache webservers
etc.

---

