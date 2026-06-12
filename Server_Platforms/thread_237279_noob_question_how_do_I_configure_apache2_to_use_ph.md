---
title: "noob question: how do I configure apache2 to use php5?"
date: 2006-08-15
forum: Server Platforms
---

### Post by qiemem on 2006-08-15
I got apache2, php5, and mysql-server. I put some files in my /var/www/ and everything worked fine (sort of: I was having some permissions problems with php)... Then I tried some tutorials I found around the forums to get everything configured properly.  Notably, I installed webmin to help configuring things, but after that, my php files were no longer recognized as such. Since then, I've tried to undo everything and start over (including uninstalling webmin and the three previously mentioned packages). Any help would be greatly appreciated, and any suggestions on tutorials or whatnot to help me get started with running a LAMP server. Thanks!

---

### Post by 23meg on 2006-08-15
[https://help.ubuntu.com/community/ApacheMySQLPHP#head-e8ed2e2ff6335c860b38aab7d029cdff0bc6215a](https://help.ubuntu.com/community/ApacheMySQLPHP#head-e8ed2e2ff6335c860b38aab7d029cdff0bc6215a)

---

### Post by qiemem on 2006-08-15
Thanks very much! That's an awesome guide...

Unfortunately, PHP still isn't working...

---

### Post by 23meg on 2006-08-15
How exactly is it not working? Any errors, etc.? Maybe you should try undoing everything you did and following the guide from start.

You may also be interested in [XAMPP]("http://www.ubuntuforums.org/showthread.php?t=223410").

---

### Post by qiemem on 2006-08-15
Ya, already tried that... I have a feeling there's a left over config file lieing around somewhere or something. No, no errors, its just as if php5 isn't installed.

---

### Post by qiemem on 2006-08-15
Ya, already tried that... I have a feeling there's a left over config file lieing around somewhere or something. No, no errors, its just as if php5 isn't installed.

Ya, I've heard of XAMPP, but I haven't had a chance to check it out yet. Though I'd start with the usual stuff before I jump into anything else.

---

### Post by scxtt on 2006-08-15
how, specifically, is php5 "not working"? -- are you getting the "do you want to download this php file" problem?

---

### Post by 23meg on 2006-08-15
I haven't tried it myself but from what I read about it I can say that if you have little experience it should be quite suitable to start with XAMPP. 

If you prefer not to, completely uninstall everything you installed and start over with the guide.

---

### Post by LordHunter317 on 2006-08-15
I really which people would troubleshoot the problem instead of telling people, try this instead.

What exactly is happening?  What does error_log say?  What do you see in your browser?  No one can help you if you do not provide details.

---

### Post by qiemem on 2006-08-15
Sorry, I really am a complete noob at this stuff. Trying to learn it; that's why I'm running this server :)

Anyway, in the browser, looking at the apacha file browser thingy, the php file has a question mark icon and when I click on it, it asks me if I want to download it. Same thing if I type in the address directly. What's this error_log you speak of?

---

### Post by scxtt on 2006-08-15
how are you trying to access your php files?  meaning, in a browser are you typing **http://localhost/"path to php file"**?

other than that, here's all i have installed, php5 wise and it works fine:
```
[FONT="Courier New"]:> aptitude search php5
Password:
i A libapache2-mod-php5                                 - server-side, HTML-embedded scripting language (apache 2.0 modu
i   php5                                                - server-side, HTML-embedded scripting language (meta-package)
i A php5-common                                         - Common files for packages built from the php5 source[/FONT]
```

---

### Post by qiemem on 2006-08-15
>  	how are you trying to access your php files? meaning, in a browser are you typing http://localhost/"path to php file"?
yep

As far those php5 packages are concerned, I've got all those. But you gave me an idea. I poked around, and found a bunch of php4 packages lieing about. So I removed, but still nothing. I tried reinstalling all my apache stuff. Maybe that gives someone an idea.

---

