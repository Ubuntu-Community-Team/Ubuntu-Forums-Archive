---
title: "rpm to deb convert error"
date: 2012-06-03
forum: Ubuntu Studio
---

### Post by ravipupp on 2012-06-03
hi.. all

 I am a new user of linux, I had install ubuntustudio 12.04. I am trying to install a rpm file in ubuntustudio but it giving me a error as follow:

[COLOR=Red]Warning: Skipping conversion of scripts in package "NAME OF PACKAGE": postinst postrm prerm
Warning: Use the --scripts parameter to include the scripts.
Unpacking of 'PACKAGE NAME.rpm' failed at /usr/share/perl5/Alien/Package/Rpm.pm line 168.[/COLOR]


if anyone know please help
thanks

ravi

---

### Post by Cheesemill on 2012-06-03
Which package are you trying to install?

Alien should only really be used as a very last resort, if you let us know what you are trying to install we can probably come up with a better solution.

---

### Post by keithdlee2011 on 2012-06-25
I tried the following -- 
alien -k --script RealPlayerGOLD11.rpm

Here are the results --
Unpacking of 'RealPlayer11GOLD.rpm' failed at /usr/share/perl5/Alien/Package/Rpm.pm line 168.


Any answers?

Keith D. Lee

---

### Post by Cheesemill on 2012-06-25
If you can do without the Gold version then there is a .deb file for RealPlayer 11 on their website:

[http://uk.real.com/realplayer/other-versions](http://uk.real.com/realplayer/other-versions)

---

