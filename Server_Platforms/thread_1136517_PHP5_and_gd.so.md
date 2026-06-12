---
title: "PHP5 and gd.so"
date: 2009-04-25
forum: Server Platforms
---

### Post by ciaran73 on 2009-04-25
I have combed every thing Google and Ubuntu forums have to offer about this subject. I cannot get gd graphic library to work. From what I understand, I want the php gd libraries. I have done:
apt-get php5-gd
installed php5 and libgd from source.
php -m reports gd enabled
var_dump(gd_info()); reports "Fatal error: Call to undefined function gd_info() in..........line whatever"
I have completely uninstalled php5 and gd and php5-gd and reinstalled just php5 and php5-gd from repositories. I restarted Apache /etc/init.d/apache2 restart after every install, reinstall, or configuration changes. I have made a symbolic links to every libgd.so.2 that I can find in the OS and still restarting apache2 after every change. Some files and errors if they will help.
Fatal error: Call to undefined function imagecreatefromjpeg()
Fatal error: Call to undefined function gd_info()

@server1:/usr/lib/php5/20060613+lfs$ ldd gd.so
        linux-gate.so.1 =>  (0xb7ef1000)
        libgd.so.2 => /usr/local/lib/libgd.so.2 (0xb7e86000)
        libt1.so.5 => /usr/local/lib/libt1.so.5 (0xb7e33000)
        libfreetype.so.6 => /usr/local/lib/libfreetype.so.6 (0xb7dc5000)
        libX11.so.6 => /usr/local/lib/libX11.so.6 (0xb7cde000)
        libXpm.so.4 => /usr/local/lib/libXpm.so.4 (0xb7cce000)
        libpng12.so.0 => /usr/local/lib/libpng12.so.0 (0xb7cab000)
        libz.so.1 => /usr/local/lib/libz.so.1 (0xb7c96000)
        libjpeg.so.62 => /usr/local/lib/libjpeg.so.62 (0xb7c76000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7b26000)
        libfontconfig.so.1 => /usr/local/lib/libfontconfig.so.1 (0xb7afc000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7ad7000)
        libxcb-xlib.so.0 => /usr/local/lib/libxcb-xlib.so.0 (0xb7ad5000)
        libxcb.so.1 => /usr/local/lib/libxcb.so.1 (0xb7abd000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7ab8000)
        /lib/ld-linux.so.2 (0xb7ef2000)
        libexpat.so.1 => /usr/local/lib/libexpat.so.1 (0xb7a97000)
        libXau.so.6 => /usr/local/lib/libXau.so.6 (0xb7a94000)
        libXdmcp.so.6 => /usr/local/lib/libXdmcp.so.6 (0xb7a8f000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7a77000)

from php.ini
; Directory in which the loadable extensions (modules) reside.
extension_dir = "/usr/local/lib"
$php -m
[PHP Modules]
bcmath
bz2
calendar
ctype
curl
date
dba
dom
exif
filter
ftp
gd
gettext
hash
iconv
imagick
imap
json
.
...

and syslog has nothing about Apache, php or gd libraries.

HELP!!
And thanks ahead of time.

---

### Post by ciaran73 on 2009-04-27
Ok, adding more to this saga I have add to my sources.list another repository:"deb [http://package.dotdeb.org](http://package.dotdeb.org) stable all" and its source, apt-get update and reinstalled php5-gd, which installed some additional packages. Again, I restarted apache2..no joy. I found that this was a bug last year but all the fixes reported failed. Help, anybody out there?

---

### Post by simondelliott on 2009-04-28
You are not alone, I also had this problem. 

What I did to fix it was to use the synaptic package manage to reinstall php5-gd then. I restarted apache2ctl 
bada bing It worked fine.

---

### Post by ciaran73 on 2009-04-29
Thanks for the response
I have installed, reinstalled, uninstalled, compiled from source php5-gd, php5, libgd and restarted apache2 after each step with restart and force-reload. Still no joy. More suggestion would be welcome and appreciated.

---

### Post by kkimmell on 2009-04-29
I have somewhere in the neighborhood of 20-30  Debian Etch and Ubuntu 6.06 - 8.04 LTS servers running apache2 and php4 or php5 with php-gd and have installed just about every single instance with the command:

apt-get install apache2 php5 php5-gd


I use the standard repos for each system and haven't had any major problems. The GD library is installed and linked properly via the aptitude program.

The only caveat I'd add is that the Debian (thus Ubuntu) repositories don't include the latest GD libraries because of some perceived security flaw so I have followed the instruction in the following link for building from source with GD support:

[http://cumu.li/2008/5/13/recompiling-php5-with-bundled-support-for-gd-on-ubuntu](http://cumu.li/2008/5/13/recompiling-php5-with-bundled-support-for-gd-on-ubuntu)

Good luck!

---

### Post by ciaran73 on 2009-04-29
I followed the directions on cumu.li for the third time. I got a an error connot find png.h, compiled libpng from source, that fixed that. Then rerunning cumu.li dirctions I get cannot find xpm.h, installed libxpm, fixed that error and after waiting for php to finish I still get warning gd.so cannot be found or cannot acces share. Any more suggestions?

---

