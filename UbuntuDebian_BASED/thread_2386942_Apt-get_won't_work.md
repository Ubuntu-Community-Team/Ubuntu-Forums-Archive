---
title: "Apt-get won't work"
date: 2018-03-12
forum: Ubuntu/Debian BASED
---

### Post by alarewyn on 2018-03-12
Well,i have just intalled an older version of Kali on my pc with dualboot.So I want to use apt-get but i get this error : ```
Ign:2 http://security.kali.org/kali-security kali/updates InRelease            
Ign:3 http://http.kali.org/kali kali InRelease                         
Err:4 http://repo.kali.org/kali kali-bleeding-edge InRelease                   
  403  Forbidden
Err:5 http://security.kali.org/kali-security kali/updates Release              
  404  Not Found
Err:6 http://http.kali.org/kali kali Release                                   
  404  Not Found
Get:1 http://kali.mirror.garr.it/mirrors/kali kali-dev InRelease [30.4 kB]  
Err:1 http://kali.mirror.garr.it/mirrors/kali kali-dev InRelease
  The following signatures were invalid: EXPKEYSIG ED444FF07D8D0BF6 Kali Linux Repository <devel@kali.org>
Reading package lists... Done
E: The repository 'http://security.kali.org/kali-security kali/updates Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://http.kali.org/kali kali Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: http://kali.mirror.garr.it/mirrors/kali kali-dev InRelease: The following signatures were invalid: EXPKEYSIG ED444FF07D8D0BF6 Kali Linux Repository <devel@kali.org>
E: The repository 'http://http.kali.org/kali kali-dev InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```
Thanks for reading :)

---

### Post by deadflowr on 2018-03-12
*Thread moved to **Ubuntu/Debian BASED***

---

### Post by alarewyn on 2018-03-12
Thanks for correcting.:)

---

### Post by Frogs Hair on 2018-03-12
Is the release still supported ? If not the repositories may be closed .

---

### Post by #&amp;thj^% on 2018-03-12
> **Frogs Hair said:**
> Is the release still supported ? If not the repositories **_may be closed_** .

+1 They are! (Closed)

---

### Post by alarewyn on 2018-03-13
It's the 2017.2 release.And what can I do?Since the newer version won't work for me.

---

### Post by #&amp;thj^% on 2018-03-13
Kali is going the rolling update route which explains why older builds source lists do not work.

[http://http.kali.org/README.mirrorlist](http://http.kali.org/README.mirrorlist)

**_You may find it "wise" to **first ask here**_: [https://forums.kali.org/forum.php](https://forums.kali.org/forum.php)

---

### Post by hrsetrdr on 2018-03-13
Here's a good read:  [https://docs.kali.org/general-use/kali-linux-sources-list-repositories](https://docs.kali.org/general-use/kali-linux-sources-list-repositories)

---

### Post by oldos2er on 2018-03-18
> **alarewyn said:**
> Well,i have just intalled an older version of Kali on my pc with dualboot.

Not sure why you would do that--have you seen [https://docs.kali.org/introduction/should-i-use-kali-linux](https://docs.kali.org/introduction/should-i-use-kali-linux) ?

---

### Post by tinylagarto on 2018-04-29
I would suggest you install a recent copy of Kali and all your problems will be gone. ;)

---

