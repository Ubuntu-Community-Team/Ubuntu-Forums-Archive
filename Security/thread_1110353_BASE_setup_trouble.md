---
title: "BASE setup trouble"
date: 2009-03-29
forum: Security
---

### Post by FiberOptix on 2009-03-29
Hello,

I've been following following the IDS thread stickied at the top. When configuring BASE, after step 4 I see at the top of the page:

Warning: include_once(Mail.php) [function.include-once]: failed to open stream: No such file or directory in /var/www/base/includes/base_action.inc.php on line 29

Warning: include_once() [function.include]: Failed opening 'Mail.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/base/includes/base_action.inc.php on line 29

Warning: include_once(Mail/mime.php) [function.include-once]: failed to open stream: No such file or directory in /var/www/base/includes/base_action.inc.php on line 30

Warning: include_once() [function.include]: Failed opening 'Mail/mime.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/base/includes/base_action.inc.php on line 30

Warning: Cannot modify header information - headers already sent by (output started at /var/www/base/includes/base_action.inc.php:29) in /var/www/base/base_common.php on line 1077

I click continue to step 5 and get a blank page with just the warning shown above. This is the same page displayed whenever I try to navigate to .../base/

Can anybody help me out?

---

### Post by bodhi.zazen on 2009-03-29
If I recall correctly, this happens with base 1.4.x

Try base 1..3.9

It was hard to find a link to base, you can get it here:

[http://easynews.dl.sourceforge.net/sourceforge/secureideas/base-1.3.9.tar.gz](http://easynews.dl.sourceforge.net/sourceforge/secureideas/base-1.3.9.tar.gz)

---

### Post by FiberOptix on 2009-03-29
> **bodhi.zazen said:**
> If I recall correctly, this happens with base 1.4.x

Try base 1..3.9

It was hard to find a link to base, you can get it here:

[http://easynews.dl.sourceforge.net/sourceforge/secureideas/base-1.3.9.tar.gz](http://easynews.dl.sourceforge.net/sourceforge/secureideas/base-1.3.9.tar.gz)

Worked like a charm! Thanks very much.

---

### Post by bodhi.zazen on 2009-03-29
You are most welcome. I hope they fix that little problem with base 1.4.x soon, it has been problematic for some time now.

I did once "hack" the php code for 1.4.1 , it was not too hard, but base still did not work well.

The good news is, base 1.3.9 is rock solid and works just fine ;)

---

### Post by p0rkjello on 2009-05-04
> **FiberOptix said:**
> Hello,

I've been following following the IDS thread stickied at the top. When configuring BASE, after step 4 I see at the top of the page:

Warning: include_once(Mail.php) [function.include-once]: failed to open stream: No such file or directory in /var/www/base/includes/base_action.inc.php on line 29

Warning: include_once() [function.include]: Failed opening 'Mail.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/base/includes/base_action.inc.php on line 29

Warning: include_once(Mail/mime.php) [function.include-once]: failed to open stream: No such file or directory in /var/www/base/includes/base_action.inc.php on line 30

Warning: include_once() [function.include]: Failed opening 'Mail/mime.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/base/includes/base_action.inc.php on line 30

Warning: Cannot modify header information - headers already sent by (output started at /var/www/base/includes/base_action.inc.php:29) in /var/www/base/base_common.php on line 1077

I click continue to step 5 and get a blank page with just the warning shown above. This is the same page displayed whenever I try to navigate to .../base/

Can anybody help me out?

Same problem.. resolved with
```
pear install Mail Mail_mime
```

---

### Post by danstermeister on 2010-02-18
**Okay so the real problem is the php.ini** file and ***_it's_*** path setting. I just happen to use OpenBSD but ran across this thread in my troubleshooting, so I just thought I'd share my solution. 

In the section that looks like this...

[FONT="Courier New"];;;;;;;;;;;;;;;;;;;;;;;;;
; Paths and Directories ;
;;;;;;;;;;;;;;;;;;;;;;;;;

; UNIX: "/path1:/path2"
include_path = [/FONT]


make that last line equal whatever else is on the line and another location where your php files are (mail.php, mime.php, the ones BASE is erroring on.)

That's what did it for me. I had...

[FONT="Courier New"]include_path = ".:/pear/lib:/var/www/pear/lib"[/FONT]

... and I changed it to ...

[FONT="Courier New"]include_path = ".:/pear/lib:/var/www/pear/lib:/usr/local/share/php5"[/FONT]

And after restarting Apache, all was well. ***Good Luck***

---

### Post by reirracon on 2010-10-05
pear install **Mail **
+
pear install **Mail_mime **

and all "Warning: include_once(Mail/mime.php)" **disapeared**.

without the need to modify php.ini.

solved. thanks

---

