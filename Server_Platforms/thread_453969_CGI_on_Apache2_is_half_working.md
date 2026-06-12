---
title: "CGI on Apache2 is half working"
date: 2007-05-25
forum: Server Platforms
---

### Post by greymoose58 on 2007-05-25
I've just installed a LAMP server from the 6.06 Server CD. The only thing I can't get working is cgi. This is particularly frustrating because the site I am working on at present only really needs a bit of cgi tweaked to be mostly finished. (I borked the server trying to install Scalix and accidentally overwrote my backup config trying to undo my mistakes.)
When I go directly to a .cgi file in my browser it works fine so there doesn't appear to be a permissions issue. For cgi files which are inserted inside html pages I get nothing. SSI is definitely working ok with non-cgi pages so it is not an SSI issue. 
I've tried following every option in this [Apache Tutorial]("http://httpd.apache.org/docs/2.0/howto/cgi.html") and with no success. I've also tried the soft link work around found in [this thread]("http://ubuntuforums.org/showthread.php?t=422412") with no joy.

My apache2.conf file includes the block 
```
ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
# To use CGI scripts outside /cgi-bin/:
#
AddHandler cgi-script .cgi

``` and my .htaccess file looks like this
```

Options +Includes +ExecCGI
AddHandler cgi-script cgi pl
AddType text/html shtml html
AddHandler server-parsed shtml html cgi pl
AddOutputFilter INCLUDES .html
AddCharset UTF-8 .html .cgi

```
Does anyone have any thoughts on where I'm going wrong? I've found a few solutions to this that appear to have worked for others but I'm stumped.

Thanks in advance.

---

