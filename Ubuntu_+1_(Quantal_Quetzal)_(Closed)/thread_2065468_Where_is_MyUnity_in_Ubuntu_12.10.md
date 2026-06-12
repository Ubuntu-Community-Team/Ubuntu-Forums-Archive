---
title: "Where is MyUnity in Ubuntu 12.10?"
date: 2012-10-02
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by mmasroorali on 2012-10-02
Dear All,
Just upgraded to Quantal Quetzal, Ubuntu 12.10. Still trying to find out what is new in it. 

Among other things, I find that my 8 workspaces have been reduced to 4. I find all those posts regarding MyUnity which should be used to control the number of workspaces among other things. 

However, I fail to find MyUnity. It is not in System Settings. I can not find a way to lauch it. It is not in Dash.

Also, the following were not helpful either.

```
masroor@MasroorOfficeDell:~$ apt-cache search myunity
masroor@MasroorOfficeDell:~$ apt-cache search MyUnity

```

Any hints will be appreciated.

---

### Post by cariboo on 2012-10-02
Myunity has been removed from the repositories, pending an update, or re-write.

---

### Post by mmasroorali on 2012-10-02
> **cariboo907 said:**
> Myunity has been removed from the repositories, pending an update, or re-write.

Thanks. Is there any other way I can control the number of workspaces now?

---

### Post by effenberg0x0 on 2012-10-02
> **mmasroorali said:**
> Dear All,
Just upgraded to Quantal Quetzal, Ubuntu 12.10. Still trying to find out what is new in it. 

Among other things, I find that my 8 workspaces have been reduced to 4. I find all those posts regarding MyUnity which should be used to control the number of workspaces among other things. 

However, I fail to find MyUnity. It is not in System Settings. I can not find a way to lauch it. It is not in Dash.

Also, the following were not helpful either.

```
masroor@MasroorOfficeDell:~$ apt-cache search myunity
masroor@MasroorOfficeDell:~$ apt-cache search MyUnity

```

Any hints will be appreciated.

I could find it normally. I'll look into my sources in a while, but I believe I'm using default repos only.

```
[02:20:41] ahsl@AL-DESK01:[~]: apt-cache search --names-only '^(M|m){1,1}(y){1,1}(U|u){1,1}(nity){1,1}.*'
myunity - Unity configurator

[02:21:41] ahsl@AL-DESK01:[~]: sudo apt-cache showpkg myunity
[sudo] password for ahsl: 
Package: myunity
Versions: 
3.1.5-0ubuntu1 (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/dpkg/status
                  MD5: 24aa67e17f299eeb2babd31706947952


Reverse Depends: 
  ubuntu-defaults-it,myunity
Dependencies: 
3.1.5-0ubuntu1 - gambas2-runtime (0 (null)) gambas2-gb-gtk (0 (null)) gambas2-gb-form (0 (null)) gambas2-gb-gtk-ext (0 (null)) unity (0 (null)) 
Provides: 
3.1.5-0ubuntu1 - 
Reverse Provides: 
```

Regards,
Effenberg

PS: Btw, the regexp usage of {} was a joke for the pure joy of obfuscation :)

---

### Post by mc4man on 2012-10-02
> **mmasroorali said:**
> Thanks. Is there any other way I can control the number of workspaces now?
Install compizconfig-settings-manager (ccsm) & set in General Options > Desktop Size

Other than a select few options only options/plugins that have been changed from the defaults will be available in dconf & only those options whose setting that have been changed from the default
( - in other words you can't edit there until they've been changed by other means like ccsm

---

