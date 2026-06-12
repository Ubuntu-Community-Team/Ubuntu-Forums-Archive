---
title: "Ubun-student: Enhance your system and learn enhancement tricks behind."
date: 2009-11-24
forum: The Cafe
---

### Post by homer.xing on 2009-11-24
Dear all, 

    I would like to recommend a GPL application. It is [Ubun-student]("http://tdt.sjtu.edu.cn/ubun-student/"). It can install/remove some applications which are not in official repository, such as GnomeArtNG. It can change system settings. Moreover, it explains secret tricks behind enhancement. You can learn tricks in "Tip of the day" window.

    Source code tar-ball and Debian packages can be [downloaded from here]("http://groups.google.com/group/ubun_student_user/files"). [This page is about installing this application from PPA repository.]("http://tdt.sjtu.edu.cn/ubun-student/?page_id=3")

[Screenshots]("http://tdt.sjtu.edu.cn/ubun-student/?page_id=9")

---

### Post by ZankerH on 2009-11-24
> **homer.xing said:**
> Dear all, 

    I would like to recommend a GPL application. It is [Ubun-student]("http://tdt.sjtu.edu.cn/ubun-student/"). It can install/remove some applications which are not in official repository, such as GnomeArtNG. It can change system settings. Moreover, it explains secret tricks behind enhancement. You can learn tricks in "Tip of the day" window.

    Source code tar-ball and Debian packages can be [downloaded from here]("http://groups.google.com/group/ubun_student_user/files"). [This page is about installing this application from PPA repository.]("http://tdt.sjtu.edu.cn/ubun-student/?page_id=3")

[Screenshots]("http://tdt.sjtu.edu.cn/ubun-student/?page_id=9")

As of two years ago, you no longer need to add deb lines and keys to add a ppa repo. The command is

```
$sudo add-apt-repository ppa:ubun-student
$sudo apt-get update
$sudo apt-get install ubun-student
```

edit: A pretty neat program, not much stuff in there I didn't already know about, but the nautilus addon is pretty cool. Also, it failed to notice the fact that I already have a flash plugin installed.

---

### Post by homer.xing on 2009-11-25
Dear ZankerH, "add-apt-repository" method has been added into the [web page]("http://tdt.sjtu.edu.cn/ubun-student/?page_id=3").

---

