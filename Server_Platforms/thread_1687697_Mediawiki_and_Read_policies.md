---
title: "Mediawiki and Read policies"
date: 2011-02-14
forum: Server Platforms
---

### Post by gnagnibu on 2011-02-14
Hi all!
I've installed mediawiki on an Ubuntu Server 10.04 and I set the view of the wiki trought login.
My question is: is it possibile to insert a category and relative tree (subcategory and pages) in the $wgWhitelistRead option of the /etc/mediawiki/LocalSettings.php ??
I noticed that if I put only the category in this way

```

...
$wgWhitelistRead =  array("Pagina_principale", "Special:Userlogin", "Help:Contents", "Category:Test");
...

```I can reach Category:Test without authentication, but NOT subcategories and pages.

Any ideas?

---

