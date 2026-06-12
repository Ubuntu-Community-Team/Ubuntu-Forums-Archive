---
title: "Apache sending out default file wrongly"
date: 2005-11-09
forum: Server Platforms
---

### Post by Joh_ on 2005-11-09
I'm running apache2 with php5 from the repositories and I've got the strangest problem. I'm using phpmyadmin, and when I try to load it (localhost/phpmyadmin), I get a download file box that lets me download the php file without parsing. If I specify however that I want index.php (localhost/phpmyadmin/index.php) it loads and displays just fine. How come this happens and is there a way to solve it? :???:

---

### Post by Joh_ on 2005-11-09
:o All of a sudden it's working. I haven't changed anything at all. o.O

Ohh well, atleast it's working :p

---

### Post by hostile on 2005-11-09
Well.. it may have magically started working for you, but it's not for me.

I'm trying to get apache2 and php5 working, and I'm having the exact same issue.

It would seem that upon installing libapache2-mod-php5 it does not change any of apache2's conf files to enable php, and with apache2's confusing mods-enabled/activated way of doing things, instead of just through httpd.conf, I'm lost.

Anyone had this problem or can tell me how to light a fire under this thing's arse?

---

### Post by dbee on 2005-11-09
Your right, it is fairly confusing. 

For php4 I usually put my .so library files in httpd.conf
```

LoadModule php4_module /usr/lib/apache2/modules/libphp4.so

```
and then make the usual changes to apache.conf
```

addType application/x-httpd-php .php .phtml
addType application/x-httpd-php-source .phps

```

---

### Post by hostile on 2005-11-10
Thanks, that worked.

Any chance this will cause issues down the road since I'm not following apache2's convention by doing this?

---

### Post by MatthewMetzger on 2005-11-11
It only worked for me once I installed libapache2-mod-php4.  My guess is that most people have the trouble php files not parsing in apache is that they need to install this package.

---

### Post by SuperMike on 2005-11-25
You weren't having a problem with your libapache2-mod-php(x) file, were you? I was. I think there's a bug. I finally got it to work after multiple attempts to uninstall and reinstall. Here's my story and I hope it helps...

I think I'm seeing a pattern of an undocumented Ubuntu Breezy bug in PHP5 and PHP4 installs with the libapache2-mod-php4 or libapache2-mod-php5. If you uninstall and reinstall multiple times, you'll find that it just sort of works if you repeat the process several times. I had to repeat the same exact process like 5 times on my PC before it just worked. And when you uninstall PHP, it will warn you that libapache2-mod-php(x) didn't get installed in the first place, so it can't remove it.

My running theory here is that either there's a bug in the Canonical web farm with some of the mirror servers we're hitting. I cannot figure out any other reason why the libapache2-mod-php(x) would install one time and not another.

And if you do a search on ubuntuforums.org, you'll find that a lot of people are having this issue. The net effect of this is that even though you have installed Apache2, PHP(x), and libapache2-mod-php(x), and have cleared your Firefox cache, you find that Firefox still asks you what to do with the PHP file, instead of Apache2 pre-processing it at the server. This is because the libapache2-mod-php(x) is failing to be compiled and inserted properly into the Apache2 framework -- even though you can clearly see the various .conf files are properly updated and the libphp(x).so file is in the proper place.

I finally got my PHP4 to work in Breezy. A couple days ago, I also had my PHP5 working too. So it *can* be done. Just keep playing with Synaptic and the install, trying different ways to install it, or install just what you need first and add other extra PHP items you need as you go. You'll find if you keep fighting with it for like 4 hours, it finally just *works*, somehow.

I wish there was a way I could easily report this as a bug to be checked. If you all know where to post this, let me know. The bug can be easily reproduced. Just upgrade from Hoary (with a loaded PHP4 install) to Breezy, and then uninstall completely the PHP4 and/or PHP5. Then, reboot. Then, try to install PHP4 again with Universe option enabled. Or, for that matter, try on a separate PC to install PHP5 again. Both PHP4 and PHP5 will intermittently have the same issue of not compiling the libapache2-mod-php(x) file properly.

I'd also like to know how I can become a tester for Canonical's PHP installs. It sounds like they didn't test this very well and could stand to have a developer help them.

P.S. There's been some discussion about uncommenting some Mime type info in the /etc/apache2/apache2.conf file. You don't have to do that. Here's the real story...

If the Mime type is not uncommented in the apache2.conf file, there's another way to make the conf file look in another directory for adding extra stuff. You'll find the uncommented version in:

/etc/apache2/mods-enabled/php4.conf

or

php5.conf in the same dir.

The installer is supposed to do this for you. However, like I said, it only intermittently compiles the libphp4.so or libphp5.so file (libapache2-mod-php(x)) properly -- you have to fight with the process of uninstallation and reinstallation, along with reboots, until it finally just "takes".

---

### Post by hostile on 2005-11-25
I thought I should follow up on this...

I removed the entry from the httpd.conf file, which is deprecated in apache2, and simply issued the command:

```
a2enmod php5
```

... and I was golden.

hth.

---

