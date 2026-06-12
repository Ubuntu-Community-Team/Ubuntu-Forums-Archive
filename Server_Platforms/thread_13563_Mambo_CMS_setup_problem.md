---
title: "Mambo CMS setup problem"
date: 2005-02-01
forum: Server Platforms
---

### Post by mtron on 2005-02-01
Hi! 

I am working for a NGO and we are planning to relaunch our Homepage.  due to our financial situation (and why paying for a CMS when you can have something like Mambo under GLP) i want to use Mambo for our System

My setup icludes Ubuntu 4.10, Apache2, php & mysql running without a problem.
The Mambo setup was also not difficult, and it worked nice when i tested it on my Ubuntu box. I wanted to show my boss the nice system, but over the LAN i experienced some (for me) strange problems.
The text was displayed ok, but no formatting, graphics ect.
I went on her Computer to the admin section, and surprise, there was everything working good.

I really can't figure out where the problem may be. Permissions are ok, apache was also running ok with my old HP and on my computer everything seems to work fine but as soon as i try to connect via the LAN to the HP (index.php) i experience these problems (and again, the Admin Interface is working good) 

Could someone give me a hint where the mistake may be?

Thanks Michael

---

### Post by mtron on 2005-02-01
ok. Problem solved...

in the file "configuration.php"
replace in the line
[B]
$mosConfig_live_site = 'http://localhost';[/B]

with the real host - name of your box  (e.g.)
**$mosConfig_live_site = 'http://michael';**

Hope this helps sb.

---

### Post by az on 2005-02-01
Classic.

I banged my head over this for a week when I set up drupal, another cms.
Some guy on IRC helped me out - took him three seconds flat.

---

### Post by bgz on 2005-02-03
hello, 

u have to allow to group and others to read your template directory.

---

