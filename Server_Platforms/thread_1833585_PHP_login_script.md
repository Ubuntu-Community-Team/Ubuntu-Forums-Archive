---
title: "PHP login script"
date: 2011-08-26
forum: Server Platforms
---

### Post by gameguy on 2011-08-26
I have found a login script I want to use for a website I am making. I have followed the instructions on here but don't know how to actually use the .php files properly. I open the .php file in my browser and it gives me the option of downlaoding it. How do I get it to work? I know you normally need to provide options to a php script, as far as I have seen, but I don't know how to. Thanks
[http://www.youtube.com/watch?v=p9DuG-J0OIE](http://www.youtube.com/watch?v=p9DuG-J0OIE)

---

### Post by BbUiDgZ on 2011-08-26
> **gameguy said:**
> I have found a login script I want to use for a website I am making. I have followed the instructions on here but don't know how to actually use the .php files properly. I open the .php file in my browser and it gives me the option of downlaoding it. How do I get it to work? I know you normally need to provide options to a php script, as far as I have seen, but I don't know how to. Thanks
[http://www.youtube.com/watch?v=p9DuG-J0OIE](http://www.youtube.com/watch?v=p9DuG-J0OIE)

assuming you have apache installed, you need to also install the php mod for it.

```
sudo apt-get install libapache2-mod-php5
```

EDIT: for more info than I could give see [HERE](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by SeijiSensei on 2011-08-26
> **gameguy said:**
> [http://www.youtube.com/watch?v=p9DuG-J0OIE](http://www.youtube.com/watch?v=p9DuG-J0OIE)
Just a heads up, but that script alone is hardly sufficient.  First you need the "include" files that have the session class.  They're referenced at the very top of the presentation.  You'll also need a database to store registered users' information.  I've written login systems like the one in that video, but they've involved not only PHP scripting, but browser session cookies, and a PostgreSQL database in the back end.  There must be more to this tutorial, no?

---

### Post by radiotehnika on 2011-08-27
> **gameguy said:**
> I open the .php file in my browser and it gives me the option of downlaoding it. How do I get it to work?
[http://www.youtube.com/watch?v=p9DuG-J0OIE](http://www.youtube.com/watch?v=p9DuG-J0OIE)

where is this php file located? Sounds like it doesnt run php. If you are using userdir, heres how to solve problem  [http://ubuntuforums.org/showthread.php?t=1478721](http://ubuntuforums.org/showthread.php?t=1478721)

---

### Post by gameguy on 2011-08-28
> **radiotehnika said:**
> where is this php file located? Sounds like it doesnt run php. If you are using userdir, heres how to solve problem  [http://ubuntuforums.org/showthread.php?t=1478721](http://ubuntuforums.org/showthread.php?t=1478721)

Thanks a heap. I just needed to install the mod and then comment out those things as per the link you gave me.

---

### Post by PierreRobiquet on 2011-08-28
Just also another heads up this script uses MD5 without a salt, not only is MD5 known to be cryptographically broken but not using a salt is also against security recommendations. You'll probably want to switch it to SHA256 and incorporate a salting mechanism for each user.

---

