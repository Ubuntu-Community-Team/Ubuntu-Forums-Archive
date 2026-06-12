---
title: "Can't start xdebug"
date: 2012-10-13
forum: Server Platforms
---

### Post by razor7 on 2012-10-13
Hi, I managed to install xdebug and enable it through local php.ini files when needed.

It was working just fine for about a month, but today It doesn't.

If I try to start a debug session with Zend Studio IDE, it gets stuck in "57%  launching: waiting for xdebug session"

If I run this command "$ sudo netstat -tunlp | grep 9000" on server console, I get:
> tcp        0      0 127.0.0.1:9000          0.0.0.0:*               LISTEN    1609/php-fpm.conf)


phpinfo reports Xdebug v2.1.0

local php.ini 
> zend_extension='/usr/lib/php5/20090626/xdebug.so'

[xdebug]
xdebug.remote_autostart=Off
xdebug.remote_enable=On
xdebug.remote_connect_back = On
xdebug.remote_port=9000
xdebug.remote_handler="dbgp"
xdebug.profiler_enable = Off
xdebug.profiler_enable_trigger = On
xdebug.profiler_output_name = cachegrind.out.%t.%p
xdebug.profiler_output_dir = '/media/data/www/clients/client1/web2/tmp/'
xdebug.remote_log='/media/data/www/clients/client1/web2/log/xdebug_didomenica.log'

Specs 
Ubuntu server 12.04, upgraded today
PHP Version 5.3.10-1ubuntu3.4
Xdebug v2.1.0

Any help is really appreciated!

Thanks a lot!

---

### Post by razor7 on 2012-10-15
Hi, just forget it.
With this config options it works! (just changed port to 9001)
zend_extension='/usr/lib/php5/20090626/xdebug.so'

> [xdebug]
xdebug.remote_enable=On
xdebug.remote_connect_back = On
xdebug.remote_port=9001
xdebug.remote_handler='dbgp'
xdebug.remote_log='/media/data/www/clients/client1/web2/log/xdebuga.log'
xdebug.profiler_enable=Off
xdebug.profiler_enable_trigger=Off
xdebug.profiler_output_name=cachegrind.out.%t.%p
xdebug.profiler_output_dir='/media/data/www/clients/client1/web2/tmp/'

For some reason, I had to erase my ZendStudio "workspaces" folder, and import all my projects again, and of course, changed por of debugger in "windows->preferences->php->debug->configure"

---

