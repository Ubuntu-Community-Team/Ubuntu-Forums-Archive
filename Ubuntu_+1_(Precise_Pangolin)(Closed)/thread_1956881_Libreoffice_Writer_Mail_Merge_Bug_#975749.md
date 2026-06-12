---
title: "Libreoffice Writer Mail Merge Bug? #975749"
date: 2012-04-11
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by terrykiwi83 on 2012-04-11
Basically am just checking to see if anybody else is experiencing this bug?

When starting the Mail Merge Wizard in LibreOffice Writer. I get to  stage 3 (select address list). When I click the Select Address List  button I presented with the following error:
 Loading Component Library Failed:
file:///usr/lib/libreoffice/program/.../program/libdbalo.so


 I was hoping to be able to select an address list, but it never happened.


 Version Details:
LibreOffice 3.5.1.2 (Also happens on 3.5.2)
Build ID: 350m1(Build:102)
 OS: Ubuntu 12.04 beta 2 x64


LaunchPad Link to Bug ([https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/975749](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/975749))


If you have writer installed please test it, am wondering if its just a 12.04 bug? If you are affected please click "This Bug Effects You" at Launchpad.


Thanks

---

### Post by ubuntu27 on 2012-04-12
I was able to reproduce this bug with LibreOffice 3.5 in Ubuntu Precise.


For everyone else, the Mail Merge Wizard can be found at Tools menu ---------> Mail Merge Wizard.

---

