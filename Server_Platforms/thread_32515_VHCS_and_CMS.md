---
title: "VHCS and CMS"
date: 2005-05-08
forum: Server Platforms
---

### Post by jayd36108 on 2005-05-08
ok, i searched around here and can't seem to find this question.

what's the difference between vhcs and CMS? can i use a CMS like drupal combined with VHCS?

---

### Post by Gandalf on 2005-05-08
[QUOTE=jayd36108]ok, i searched around here and can't seem to find this question.

what's the difference between vhcs and CMS? can i use a CMS like drupal combined with VHCS?[/QUOTE]
 well there's nothing between VHCS and CMS, they are completely different
VHCS is Virtual Hosting Control System, it's a control panel for shared hosting (many domains on 1 server)
CMS is Content Management System, think like phpnuke, mambo etc.... it's a news editor, content and user management inside one domain
More info: [http://en.wikipedia.org/wiki/Content_management_system](http://en.wikipedia.org/wiki/Content_management_system)
see them live, [http://www.siemens-mobiles.org/](http://www.siemens-mobiles.org/) is CMS (mambo), [http://www.siemens-mobiles.org/vhcs2/](http://www.siemens-mobiles.org/vhcs2/) is VHCS 

so as you can see there's nothing between those two words :D

---

### Post by jayd36108 on 2005-05-08
[QUOTE=Gandalf]well there's nothing between VHCS and CMS, they are completely different
VHCS is Virtual Hosting Control System, it's a control panel for shared hosting (many domains on 1 server)
CMS is Content Management System, think like phpnuke, mambo etc....
More info: [http://en.wikipedia.org/wiki/Content_management_system](http://en.wikipedia.org/wiki/Content_management_system)


so as you can see there's nothing between those two words :D[/QUOTE]

thank you gandlaf,

by the way, i ran your scipt for vhcs and should it be stuck at "removing unneeded packages" after 2 hrs?

---

### Post by Gandalf on 2005-05-08
[QUOTE=jayd36108]thank you gandlaf,

by the way, i ran your scipt for vhcs and should it be stuck at "removing unneeded packages" after 2 hrs?[/QUOTE]
 yes could be, because it install a lot of packages (check the manual step in the tuto and see the package to install, you can also type in another menu,
sudo cp /root/vhcs_log.txt /root/tmp.txt
less /root/tmp.txt
and take a look to the end
BTW recheck my first post i edit it

---

### Post by defkewl on 2005-05-08
Could you please give me an example of vhcs please. All I know is cms and weblog :P

---

### Post by Gandalf on 2005-05-08
[QUOTE=defkewl]Could you please give me an example of vhcs please. All I know is cms and weblog :P[/QUOTE]
 man VHCS is a name of a product not a general name, [http://www.vhcs.net](http://www.vhcs.net)

---

