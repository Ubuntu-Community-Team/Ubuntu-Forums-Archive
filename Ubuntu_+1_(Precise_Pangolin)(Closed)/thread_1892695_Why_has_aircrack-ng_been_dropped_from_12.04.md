---
title: "Why has aircrack-ng been dropped from 12.04?"
date: 2011-12-08
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by portis on 2011-12-08
Anyone knows? Thanks.

---

### Post by clivejo on 2011-12-08
How do you mean dropped?

---

### Post by mc4man on 2011-12-08
This  - 
> Removal requested on 2011-12-07.
Deleted on 2011-12-07 by Martin Pitt

(From Debian) RoQA; unmaintained, RC-buggy, NPOS

---

### Post by ronacc on 2011-12-08
you can get the source here and build it yourself . [http://www.aircrack-ng.org/](http://www.aircrack-ng.org/)

---

### Post by fdrake on 2011-12-08
aircrack-ng does not belong to the ubuntu development team.... you can build it from source like the previous post said

---

### Post by cariboo on 2011-12-09
I'd suggest using [BackTrack]("http://www.backtrack-linux.org/")

---

### Post by wgarcia on 2011-12-09
The most likely to reason to drop a package I believe it is because of a dependency that does not get updated and stops the package from being built for a specific release.

---

### Post by portis on 2011-12-10
> **mc4man said:**
> This  -

Thanks for the info.
I think I will put aircrack-ng into my ppa.

---

### Post by portis on 2011-12-10
> **wgarcia said:**
> The most likely to reason to drop a package I believe it is because of a dependency that does not get updated and stops the package from being built for a specific release.

No. It's because this package has not been maintained for a long time.

---

### Post by sammiev on 2011-12-10
> **cariboo907 said:**
> I'd suggest using [BackTrack]("http://www.backtrack-linux.org/")

+1 I am also a member there and have been using BackTrack for years from a DVD or USB when needed.

---

### Post by jbicha on 2011-12-10
If you're really interested, here's the Debian bug [report]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=642934"). aircrack-ng was not in the latest Debian stable release nor had it been in Debian testing for the past year. More recently, it was also removed from Debian unstable but there might be a new maintainer for it so it could come back.

---

### Post by portis on 2011-12-11
Thanks for the info.

> **jbicha said:**
> If you're really interested, here's the Debian bug [report]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=642934"). aircrack-ng was not in the latest Debian stable release nor had it been in Debian testing for the past year. More recently, it was also removed from Debian unstable but there might be a new maintainer for it so it could come back.

---

### Post by gidiara on 2012-02-09
Whan I try to compilation aircrack-ng it need a dependancies. If i try install dependancies by synaptic, it kill all the system and remove cernel. Ubuntu command must  die.
  &#1069;&#1090;&#1080; &#1087;&#1080;&#1076;&#1086;&#1088;&#1099; &#1076;&#1086; &#1090;&#1086;&#1075;&#1086; &#1080;&#1079;&#1074;&#1088;&#1072;&#1090;&#1080;&#1083;&#1080; &#1091;&#1105;&#1073;&#1080;&#1097;&#1085;&#1099;&#1081; 12.04, &#1095;&#1090;&#1086; &#1090;&#1091;&#1076;&#1072; &#1085;&#1080; &#1087;&#1086;&#1076; &#1082;&#1072;&#1082;&#1080;&#1084; &#1074;&#1080;&#1076;&#1086;&#1084; &#1085;&#1077; &#1089;&#1090;&#1072;&#1074;&#1080;&#1090;&#1089;&#1103; aircrack-ng. &#1063;&#1090;&#1086;&#1073; &#1080;&#1084; &#1085;&#1077; &#1080;&#1082;&#1072;&#1083;&#1086;&#1089;&#1100;, &#1089;&#1091;&#1082;&#1072;&#1084;! &#1057;&#1086;&#1088;&#1088;&#1080; &#1092;&#1086;&#1088; &#1084;&#1072;&#1081; &#1092;&#1088;&#1072;&#1085;&#1094;&#1091;&#1079;&#1089;&#1082;&#1080;&#1081;.

---

### Post by nothingspecial on 2012-02-09
Use the backtrack forums for aircrack-ng support. It is not supported here.

Closed.

---

