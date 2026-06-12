---
title: "Can't find PHP configure file"
date: 2006-09-05
forum: Server Platforms
---

### Post by kday33 on 2006-09-05
Installed PHP 4.4.0 on Breezy desktop 8 months ago along with LAMP (through the directions on ubuntu.org), and everything works fine.

Now, I'm trying to add the cURL library for PHP, but I can't find the configure file for PHP so that I can rebuild it to include cURL.  I have looked in a lot of directories, searched several times, but I can't find it at all.  Not surprisingly, the configure settings don't show up when I run phpinfo().

How do I reconfigure PHP?

Thanks in advance.

---

### Post by kidders on 2006-09-05
I may be misunderstanding, but can't you achieve the same effect with...

```

sudo apt-get install php4-curl

```

---

### Post by kday33 on 2006-09-05
Thanks for the reply.  I hadn't tried that. Here's the result:
```
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  php4-curl
0 upgraded, 1 newly installed, 0 to remove and 56 not upgraded.
Need to get 0B/17.9kB of archives.
After unpacking 98.3kB of additional disk space will be used.

Preconfiguring packages ...
Selecting previously deselected package php4-curl.
(Reading database ... 98149 files and directories currently installed.)
Unpacking php4-curl (from .../php4-curl_4%3a4.4.0-3ubuntu2_i386.deb) ...
Setting up php4-curl (4.4.0-3ubuntu2) ...
```
Looks fine, but phpinfo() still doesn't show curl and the php/curl examples I've found online come up with fatal errors due to undefined curl functions.  cURL works just fine when I use it from the command line though.  Any suggestions?

---

### Post by kidders on 2006-09-05
One (albeit a bit hair-brained) ... did you remember to restart apache? Dumb suggestion, I know.

Darn it ... I felt sure that would work! I'm still willing to bet that the right "apt-get install" will do it for you though.

---

### Post by kday33 on 2006-09-06
Actually, I hadn't restarted apache.  I just restarted it now, and there was no change.  Also rebooted my machine and no change.

I'm not sure what else to try. I've done a ton of searching and haven't found many people who have trouble getting curl to work.  What other sorts of apt-get installs might work?

---

### Post by kday33 on 2006-09-06
I discovered that I can get this to work:
```
<?php
echo shell_exec("/usr/bin/curl -L http://www.zend.com");
?> 
```
But I still get a "fatal error, undefined function" for curl_init().
I might be able to make do with the shell_exec() for my immediate needs, but I'm still confused why libcurl isn't working.

---

### Post by kidders on 2006-09-06
Damn... Sorry about that.

I'm a PHP5 user, so I'm not really in a position to mess around with it myself :-( Are there any references to curl in /etc/php4/cli/php.ini that aren't in /etc/php4/apache/php.ini or /etc/php4/apache2/php.ini?

If not, it seems like we're back to your original question, which is about reconfiguring + recompiling PHP. I've never done such a thing with Ubuntu, but isn't there a way you can specifically ask apt-get to compile something from source for you, rather than just fetching the binaries? Assuming there is, it's *gotta* let you tinker with the configure switches ... otherwise there'd almost be no point in doing it!

Jeez... I'm not sure I could have been of any *less* help to you!!

---

