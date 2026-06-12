---
title: "Installing mod_rewrite After apache installation OR re-installing Apache?"
date: 2009-06-09
forum: Server Platforms
---

### Post by swraman on 2009-06-09
hi,

I downloaded apache2 from their website's links, and have it up and running along with PHP on an ubuntu box.

I thought mod_rewrite was installed by default but it looks like it wasnt as mod_rewrite.so is not in my /modules directory.

So:  is there any way to install the rewrite module now without re-installing Apache2?

If not:  how do I properly reinstall Apache2?  last time I didnt remove it properly and had 2 installations of apache running on my machine, not good.
And, if I reinstall apache2 with the rewrite module, would I have to reconfigure/reinstall PHP as well?

Thanks

---

### Post by bluefrog on 2009-06-10
sudo a2enmod rewrite   to check that if it is installed

---

### Post by LepeKaname on 2009-06-10
> I downloaded apache2 from their website's links

Why didn't you used the repositories?

Just install "apache2" and make a symlink from 
/etc/apache2/mods-available/rewrite.load to /etc/apache2/mods-enabled/

That will do it.

---

### Post by swraman on 2009-06-10
Hi,

a2enmod is an unrecognized command.

I installed it from their website b/c I want this test server to be as similar to the actual server im using, which isnt running on Ubuntu.

So is there no way to install the mod without reinstaling apache?

How do I re-install Apache, without ending up with 2 installations?

---

### Post by apel_2804 on 2009-06-10
I still don't get why you not just use the repository... Who cares about the distribution. But maybe here is something you can use:

[http://httpd.apache.org/docs/2.0/mod/mod_rewrite.html](http://httpd.apache.org/docs/2.0/mod/mod_rewrite.html)

---

### Post by swraman on 2009-06-11
i want it to be like the production server im using as much as possible.

for example, since I have to manually install this mod on apache, I now know that it has to be installed on the production server as well.  If I didnt use it, i would still be under the impression that the rewrite module came preinstalled.

Thanks again, and any info on how to properly reinstall it would be appreciated.

---

### Post by LepeKaname on 2009-06-12
Search if you have already mod_rewrite.so in your system. If so, add this to your apache conf:

LoadModule rewrite_module modules/mod_rewrite.so

If you don't have it, you may need to do it as DSO. Check this page:

[http://httpd.apache.org/docs/2.0/dso.html](http://httpd.apache.org/docs/2.0/dso.html)

I hope this can point you in the right direction.

---

### Post by swraman on 2009-06-12
Hi,
It looks like modules have to be compiled at install..I cant find anywhere that shows how to install the module after apache is installed.

I ended up re-compiling apache and reinstallng it.

Can you answer one thing though pls?  To remove the old installation I just deleted the apache2 directory.  Is this the correct way to uninstall it?  I installed it by downloading the source from apache's website and compiling/installing, NOT from the repositories.

Thanks.

---

### Post by LepeKaname on 2009-06-29
You can uninstall any compiled application if you use "checkinstall". If you still have your compiled sources (where you did make install), then, you can still do it:

1. install checkinstall.
2. run checkinstall in that directory
- It will generate a .deb file
3. install that .deb file

Anytime you want, you can remove it from aptitude/synaptic/dpkg and will remove all the files that were installed.

---

