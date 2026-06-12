---
title: "Upgrading GD"
date: 2011-04-13
forum: Server Platforms
---

### Post by Isterklister on 2011-04-13
Hello,
I have Ubuntu 10.10 server and I need GD (php) version 2.0.1 or later. How can I upgrade the GD or the hole php ti 5.3.6?

I can only find info on upgrading Debian but that does not working for me.

Thanks,
Pelle

---

### Post by BkkBonanza on 2011-04-13
You can generally find package names like this,

aptitude search php5
(which will spit out a list of possible packages)

aptitude versions php5 
(will spit of the current version available)

Which seems to be 5.3.3 right now. From the first list above you can see the GD package is php5-gd.

If you really need a newer version than 5.3.3 then you would need to manually install it. Most likely using a deb package would be easiest if you can find one. Then you would just use,

dpkg -i php5-whatever.deb  (whatever filename you find)

Also, if a newer PPA is available on Launchpad then you can add that PPA to your sources list and apt-get update - then the new version should be listed as available and you can install in the normal way,

sudo apt-get install php5 php5-gd

---

### Post by Isterklister on 2011-04-13
Thanks, I can't find any .deb-file or PPA and I have problem to install php 5.3.6 from source. configure, make and make install works fine but it will not upgrade php. I do not know why.
I need a newer version of GD to use the imagecreatetruecolor function.

Any other solutions or anyone have a kink to a deb-file or PPA?

---

### Post by BkkBonanza on 2011-04-13
I haven't used GD recently. I did use it a few years ago and was able to use the true color functions even then. I'm sure it is available even in PHP 5.3.3. You really should not have to compile source to use that function.

According to my check of the deb packages even 5.3.3 is using GD 2.0.36 which is plenty new enough to have true color functions. 5.3.6 seems to be built on the same GD library anyway.

Even so you should be able to find the needed deb files and all version info here,

[http://packages.debian.org/search?searchon=names&keywords=php5](http://packages.debian.org/search?searchon=names&keywords=php5)

Find the desired package on that page, click on it, scroll to the bottom where architectures are listed and find the i386 or amd64 and click that. You get to a page with mirrors of that package and version.

Also, if you do "make install" it should replace the current version php with the new one. But you will have to restart apache / web server and perhaps make config changes for it to be used. If you're coming from an older php 4.* then there are significant changes in locations, paths and naming.

---

