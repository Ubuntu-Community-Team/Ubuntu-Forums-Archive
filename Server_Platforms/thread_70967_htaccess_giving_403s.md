---
title: "htaccess giving 403s"
date: 2005-10-01
forum: Server Platforms
---

### Post by KrakHT on 2005-10-01
HI! I just installed Ubuntu about a week ago, and I have to say Im loving it. I tried FC2 before and hated it, didnt take to it too well. But this is great.

Anyways, I am using Breezy, and installed Apache2, PHP4, and MySQL. They are all working except Im having some troubles with Apache. At first I couldnt get .htaccess files to work, but dug through the forum and found out I needed to edit my /etc/apache2/sites-available/default file. So I changed AllowOverride from none to all. And now any folder with a .htaccess file gives a 403. Even if its blank. I tried to add Order Allow, Deny - allow from all, and I still get the 403. If I remove the .htaccess file, the 403 goes away...

I havent touched the apache2.conf, or httpd.conf, just the default file.

Is there a setting I missed?

The apache2 stuff I have are:

apache2 2.0.54-5ubuntu1
apache2-common 2.0.54-5ubuntu1
apache2-mpm-prefork 2.0.54-5ubuntu1
apache2-utils 2.0.54-5ubuntu1

Thanks!

---

### Post by KrakHT on 2005-10-01
Hahaha, I figured it out...I never thought to think about permissions. When I create a htaccess its at 600, changed to 644, bam worked.
I just remembered to check the system logs...haha....Newbie mistake.
Great 1st post eh? Oh and Krak, you stole my name ;-)

---

