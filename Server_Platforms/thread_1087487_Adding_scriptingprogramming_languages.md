---
title: "Adding scripting/programming languages"
date: 2009-03-05
forum: Server Platforms
---

### Post by josephmo on 2009-03-05
I started out with kubuntu (desktop 64bit). I added the Apache Web server, and the MySql server. Can I assume that by addiing Perl and PHP from my Ubuntu Package Manager, that they are added as interpreted platforms for my Apache server as well, or is there something else I need to do? I also just installed webmin, but have not had a chance to familiarize myself with it yet. Would anyone know if webmin has facilities to manage Perl, PHP, etc?

Any other administration packages you recommend (beside webmin)? anything in the free domain that resembles WHM and CPanel?

---

### Post by kaivalagi on 2009-03-05
Look for the libapache2-* packages for the support you need

You may also need to add the modules into apache using a2enmod

Not sure on admin frontends...I tend to use the cli or linux apps on the box itself

---

