---
title: "[SOLVED] PHP5/LAMP issue"
date: 2008-10-09
forum: Server Platforms
---

### Post by TomB19 on 2008-10-09
I'm having PHP5 issues with Kubuntu 8.04/apache2/php5/mysql


I have a file "testphp.php":

<?php phpinfo(); ?>

When I point my browser at the file, I get a blank white page.  When I point my browser at a CMS that worked on another system, I get a screen full of mostly code with the odd popup.

A test.html static page displays fine.


I installed the environment with: "# tasksel install lamp-server" and it completed with no errors.

"# a2enmod php5
This module is already enabled!"

So I dunno...

I'd appreciate any ideas or help.

---

### Post by TomB19 on 2008-10-09
For what it's worth, I thought I scoured the web prior to posting this question.  Everything was installed.  The module was enabled.

It turned out, I was able to find the solution on the web.

It was the bug that causes the requirement to use "AddHandler" instead of "AddType", as installed in the php5.conf module.

I hope the patch gets integrated into the distribution package soon as it would be nice for it to work properly as installed out of the box.


... and to all a good night.  :)

---

### Post by benoybose on 2008-10-09
> **TomB19 said:**
> I'm having PHP5 issues with Kubuntu 8.04/apache2/php5/mysql


I have a file "testphp.php":

<?php phpinfo(); ?>

When I point my browser at the file, I get a blank white page.  When I point my browser at a CMS that worked on another system, I get a screen full of mostly code with the odd popup.

A test.html static page displays fine.


I installed the environment with: "# tasksel install lamp-server" and it completed with no errors.

"# a2enmod php5
This module is already enabled!"

So I dunno...

I'd appreciate any ideas or help.


Since being display a blank white page, obeviously the apache has properly configured with the handlers. You please modify the code like
<?php echo phpinfo(); ?>
Save the file and try again!

All the best!

---

