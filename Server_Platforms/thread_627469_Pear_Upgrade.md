---
title: "Pear Upgrade"
date: 2007-11-30
forum: Server Platforms
---

### Post by L30N on 2007-11-30
I recently installed pear via the php-pear package and then went to upgrade pear using:

sudo pear upgrade pear

I then received the following :

```
Could not download from "http://pear.php.net/get/PEAR-1.6.2.tgz", cannot download "pear/pear" (File http://pear.php.net:80/get/PEAR-1.6.2.tgz not valid (redirected but no location))
Error: cannot download "pear/PEAR"
Could not download from "http://pear.php.net/get/Console_Getopt-1.2.3.tgz", cannot download "pear/Console_Getopt" (File http://pear.php.net:80/get/Console_Getopt-1.2.3.tgz not valid (redirected but no location))
Error: cannot download "pear/Console_Getopt"
Download failed
upgrade failed
```

Does anyone have any ideas on the cause or solution to this?

Thanks in advance.

Leon

---

### Post by homegrown on 2007-12-07
It appears that you have an issue getting the package - have you tried downloading it manually & installing it?

or some troubleshooting starting points:

Provide the output of **config-show**]? - to show anything odd with your setup

& **list-channels** will show you where you're getting your updates from

---

### Post by L30N on 2007-12-10
Sorry for the delayed responce.

Yeah installing manually works fine. Here is the output from config-show and list-channels:

```
Configuration (channel pear.php.net):
=====================================
Auto-discover new Channels     auto_discover    <not set>
Default Channel                default_channel  pear.php.net
HTTP Proxy Server Address      http_proxy       <not set>
PEAR server [DEPRECATED]       master_server    pear.php.net
Default Channel Mirror         preferred_mirror pear.php.net
Remote Configuration File      remote_config    <not set>
PEAR executables directory     bin_dir          /usr/bin
PEAR documentation directory   doc_dir          /usr/share/php/docs
PHP extension directory        ext_dir          /usr/lib/php5/20060613+lfs
PEAR directory                 php_dir          /usr/share/php
PEAR Installer cache directory cache_dir        /tmp/pear/cache
PEAR data directory            data_dir         /usr/share/php/data
PEAR Installer download        download_dir     /tmp/pear/download
directory
PHP CLI/CGI binary             php_bin          /usr/bin/php
php.ini location               php_ini          <not set>
PEAR Installer temp directory  temp_dir         /tmp/pear/temp
PEAR test directory            test_dir         /usr/share/php/tests
Cache TimeToLive               cache_ttl        3600
Preferred Package State        preferred_state  stable
Unix file mask                 umask            22
Debug Log Level                verbose          1
PEAR password (for             password         <not set>
maintainers)
Signature Handling Program     sig_bin          /usr/bin/gpg
Signature Key Directory        sig_keydir       /usr/etc/pearkeys
Signature Key Id               sig_keyid        <not set>
Package Signature Type         sig_type         gpg
PEAR username (for             username         <not set>
maintainers)
User Configuration File        Filename         /home/[username]/.pearrc
System Configuration File      Filename         /usr/etc/pear.conf
```

```
Registered Channels:
====================
Channel      Summary
pear.php.net PHP Extension and Application Repository
pecl.php.net PHP Extension Community Library
__uri        Pseudo-channel for static packages
```

---

