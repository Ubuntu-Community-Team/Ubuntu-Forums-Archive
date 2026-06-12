---
title: "Stop Users Uploading/Using PHP/CGI Scripts?"
date: 2006-07-23
forum: Server Platforms
---

### Post by Johnsie on 2006-07-23
Hi... I'm letting people upload to my webserver. Each user has their own folder in htdocs.

I dont want them being able to have any kind of executable files like php scripts or cgi scripts because that would compromise my system.

What would be the best way to go about securing my system against these scripts being uploaded or run? I dont mind them being there as long as I'm 100% sure they cannot be chmodded executable or excecuted

I'm using Xammp (Apache/PHP/Mysql/Perl/Proftp)

Thanks in advance,

John

---

### Post by scxtt on 2006-07-23
what method do you use to let them upload files?

---

### Post by Johnsie on 2006-07-23
My ftp server is ProFTPD 1.3.0 Server
My webserver is apache

I actually haven't created any extra ftp users yet. Is that enough info?

---

### Post by scxtt on 2006-07-23
i've not used proftp, but i'd think there'd be a way to restrict files w/ a certain extension (which, sure, could be bypassed) - but i'm thinking if someone tries to upload "index.php" or "my_script.cgi" that proftp could disallow that ... but you're probably looking for something that could parse through a file looking for certain content (like **<?php** or something perl-like) ...

i've also never created an ftp server, no real need w/ SSH - but maybe you can create users w/ VERY basic functioning that ***only*** allows them to upload (not chmod or execute) ...

---

### Post by Johnsie on 2006-07-23
hmmm... I'm thinking that chmodding thier folders read/write only might work better? 

Is there a way to stop them from being able to chmod files within their folder?

---

### Post by scxtt on 2006-07-23
that won't help, when a directory is executable that just means it can be cd'd into ... they'll be able to chmod any files they own ... an idea i have off the top of my head would be to have a script (cron, probably) that runs at an interval you're happy with that will chown/chmod files that have been uploaded so they can't do anything with them at a later time ...

---

### Post by LordHunter317 on 2006-07-24
PHP files don't have to be marked executable for Apache to execute them.

The simple and obvious solution is just not to have the PHP, CGI, etc. DSOs loaded into Apache.

---

### Post by Johnsie on 2006-07-24
I need cgi and php to run my own scripts. I wouldn't mind having a specified cgi-bin and a php-bin that only I can access. And then making that php/cgi files uploaded to any other directory can't possibly be run. Is that possible? I'm not really in favour of using any cron jobs to do this but thanks for the suggestion.

---

### Post by fnjordy on 2006-07-25
Check out the Apache documentation, specifically the [mod_mime](http://httpd.apache.org/docs/2.0/mod/mod_mime.html) section.  You need to remove handlers for all configured script handlers: .pl for Perl, .php for PHP, etc.  You need to [disable .htaccess files](http://httpd.apache.org/docs/2.0/mod/core.html#allowoverride), and [disable most of the options](http://httpd.apache.org/docs/2.0/mod/core.html#options) that allow CGI scripts and other features.

---

### Post by Johnsie on 2006-07-25
Thanks,  I think that prolly what I was looking for. Not too happy about having to disable .htaccess but I'm sure I can find some kind of replacement solution for the times I'm using .htaccess.

---

### Post by LordHunter317 on 2006-07-25
You don't have to disable .htaccess.

You can't use those tricks, they're essentially the same as doing what I've suggsted.  Just at a higher level, and harder to do.

You're going to have to run a second apache instance with no loaded stuff for your other users, or similiar trickery.

---

