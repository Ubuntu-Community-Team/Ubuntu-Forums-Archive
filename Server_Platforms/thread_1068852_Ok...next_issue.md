---
title: "Ok...next issue"
date: 2009-02-13
forum: Server Platforms
---

### Post by mistypotato on 2009-02-13
php5.

It says it's installed and it appears to be running, but.......

When I try to open a php page in a browser, it seems to completely ignore the php script.

the library is also installed for php5.
I tried re-installing both components and I do have a test page....with html at the bottom and it only displays the html AFTER the php.

No errors, just no apparent processing of the php :confused:


Suggestions?

---

### Post by hyper_ch on 2009-02-13
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by LPomfrey on 2009-02-13
You possibly need to add the following to /etc/apache2/sites-available/<site>

```

AddType text/html .php .phps
AddHandler application/x-httpd-php .php
AddHandler application/x-httpd-php-source .phps

```

Also, check that you've got a symlink in /etc/apache2/mods-enabled that points to /etc/apache2/mods-available/php5.load

---

### Post by mistypotato on 2009-02-13
Thanks LPomfrey.

Seems I broke the rules so I moved my question to a hopefully more acceptable thread.

Will try what you suggested.  :)

---

### Post by mistypotato on 2009-02-13
Yes, the sym link is there that points to php5.load

---

