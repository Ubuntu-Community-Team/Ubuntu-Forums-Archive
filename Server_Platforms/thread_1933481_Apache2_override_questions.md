---
title: "Apache2 override questions"
date: 2012-02-29
forum: Server Platforms
---

### Post by abickel on 2012-02-29
Hi everybody

I'm new to the world of LAMP, web servers, and scripting PHP in general, and I've installed LAMP package for the purpose of runing a browser based program called NolaPro.   (with the eventual plan of hosting it for a LAN.... if i ever get it up and running on my laptop)
Setup for apache and PHP was successful, the only trouble I'm having is that NolaPro tells me I need to set Auto_Detect_Line_Endings to ON, as it is currently off.  I have attempted to change this in both the php.ini file (i think i found a few of these, and changed it in each instance??) and have also tried editing all the .htaccess files i can find.  However, Apache will not recognize these changes, and the only place ive come close to finding an override to edit is in /etc/apache2/apache2.conf  editing this file has produced no results. 

If anybody has any pointers for me, it would be greatly appreciated.

---

### Post by turinglabs on 2012-02-29
auto_detect_line_endings is a PHP config option, so editing apache2.conf won't change the setting. You want to edit /etc/php5/apache2/php.ini, look for this line:

```

;auto_detect_line_endings = Off

```

Change it to (or add it if you don't see it in your php.ini file):

```

auto_detect_line_endings = On

```

and restart apache.

---

