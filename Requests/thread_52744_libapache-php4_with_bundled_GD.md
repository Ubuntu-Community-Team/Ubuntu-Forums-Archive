---
title: "libapache-php4 with bundled GD"
date: 2005-07-28
forum: Requests
---

### Post by PeterB on 2005-07-28
Hi

There is a problem with the current build of libapache-php4, as it isn't built with the PHP group's bundled GD library enabled.

This is the official version of GD to use with PHP, as it fixes some bugs and has extra features added, such as alpha blending.  Since it became standard, libraries such as PEAR's Image_Transform rely on the bundled version being installed, not the Boutell version, as package php4-gd adds.

With the current PHP package being for 4.3.10 this would be an excellent opportunity to upgrade the PHP version while fixing a problem with the existing package.

---

### Post by myshoesrsolight on 2006-01-31
[QUOTE=PeterB]Hi

There is a problem with the current build of libapache-php4, as it isn't built with the PHP group's bundled GD library enabled.

This is the official version of GD to use with PHP, as it fixes some bugs and has extra features added, such as alpha blending.  Since it became standard, libraries such as PEAR's Image_Transform rely on the bundled version being installed, not the Boutell version, as package php4-gd adds.

With the current PHP package being for 4.3.10 this would be an excellent opportunity to upgrade the PHP version while fixing a problem with the existing package.[/QUOTE]

Yeah, just use apt-get or synaptic and get the php5-gd or php4-gd or php3-gd or php2-gd..... and there you go.
Have a good day.\\:D/

---

