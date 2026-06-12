---
title: "Strip Ubuntu for custom need"
date: 2012-01-06
forum: Ubuntu Studio
---

### Post by viz3rd on 2012-01-06
Hi People, I know theres an app called reconstructor for ubuntu to add/remove apps and customize other things in ubuntu.
Well my need is similar, but a lot of customization. First of all I want the distro to be very secure. Secondly, I am developing an 3D graphics application that will be a native ubuntu. So basically that application will be the only thing on the entire OS. Also support for printer to print images rendered from the application.
Also the system will have to logins, Admin and User. Now user will not have access to any system files or file browser as well. User can only work on this Graphics Application and make prints. Thats all.
Can anyone suggest any solution to this please?

Thanks.

---

### Post by jejeman on 2012-01-06
> First of all I want the distro to be very secure.Ubuntu is already very secure by default.

You should learn how ubuntu works, to achive just a bare bones.
My suggestion is to instal from mini.iso. First install the base system and after that install just what you need.

---

### Post by viz3rd on 2012-01-06
> **jejeman said:**
> Ubuntu is already very secure by default.

You should learn how ubuntu works, to achive just a bare bones.
My suggestion is to instal from mini.iso. First install the base system and after that install just what you need.

Thanks! will try it.

---

### Post by viz3rd on 2012-01-11
Can you guys help me with stage 2 for this development pls.

[http://ubuntuforums.org/showthread.php?p=11600561#post11600561](http://ubuntuforums.org/showthread.php?p=11600561#post11600561)

---

### Post by CivilizationII on 2012-02-20
Maybe the simplest way of achieving this would be to use LTSP (various implementation including Ubuntu) [http://ltsp.org](http://ltsp.org)


Another way is to use a very simple desktop (Blackbox is here a candidate of choice, because you can easely block any addition on menu), _and_ make unable the script capacity (*) of every users (excepted admin, unless you really want problems).

(*) assigning /bin/nologin to script default, or redirecting /bin/bash to /dev/null are working, but there are multiple ways to do it. Obviously this solution require a _lot_ of Unix/Linux experience if you don't want to render your computer unavailable until complete reinstall.

---

