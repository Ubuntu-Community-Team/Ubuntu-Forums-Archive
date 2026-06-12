---
title: "PHP4 parses itself when run as a cgi-binary"
date: 2006-07-30
forum: Server Platforms
---

### Post by nimrod_abing on 2006-07-30
I've been running PHP4 as an Apache2 module on a development machine. Recently, I begun experimenting with suExec. This requires that PHP4 run as a CGI binary. I have configured one of my VirtualHost setups in the following manner:

In the VirtualHost container...
```

Action php4-script /cgi-bin/php4-cgi
AddHandler php4-script .php
php_admin_flag engine off

```

Afer restarting Apache2, I view a test page containing the following:
```

<?php
phpinfo();
?>

```

I get:
```

<br />
<b>Warning</b>:  Unexpected character in input:  '' (ASCII=23) state=1 in <b>/var/www/vhosts/host1/cgi-bin/php4-cgi</b> on line <b>3138</b><br />
<br />
<b>Parse error</b>:  syntax error, unexpected '*' in <b>/var/www/vhosts/host1/cgi-bin/php4-cgi</b> on line <b>3138</b><br />

```

I can run the php4-cgi binary just fine on the command line. The closest thing that I could find on PHP Bugs is this [bug report]("http://bugs.php.net/bug.php?id=22270").

It seems that this problem is not present in the php5-cgi binary. I can run it just fine. I did a bit more digging over at PHP Bugs and I found this [old bug report]("http://bugs.php.net/bug.php?id=1831").

It looks like php4-cgi was not compiled with --enable-force-redirect. So it needs you to set either doc_root or user_dir in php.ini. Like so:

```

doc_root = /var/www/html

```

The drawback to this is that you can only set doc_root once, so getting php4-cgi to work under a VirtualHost setting is impossible. I've tried the alternative which is to use the following in .htaccess under /var/www/vhosts/host1/html:

```

SetEnv PHP_DOCUMENT_ROOT /var/www/vhosts/host1/html
PassEnv PHP_DOCUMENT_ROOT

```

I can confirm that this variable is being passed to the PHP CGI binary by setting doc_root in php.ini to the same value. However, without doc_root the error is still there. It seems that PHP_DOCUMENT_ROOT is not being used instead when doc_root is blank  as documented [here]("http://www.php.net/manual/en/security.cgi-bin.doc-root.php").

I'm not sure if anyone out there is having this same problem under Ubuntu. If someone out there has experienced this problem and has found a solution please post here. And no, using PHP5 CGI binary is not a solution :)

Short of building PHP4 from source with --enable-force-redirect enabled, I am using the workaround which is to specify the doc_root variable. Which is OK since this is only on a development machine.

I guess this thread should be of interest to hosting providers who want to offer PHP4 CGI on their Ubuntu servers.

---

