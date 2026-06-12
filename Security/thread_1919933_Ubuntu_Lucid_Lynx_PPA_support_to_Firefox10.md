---
title: "Ubuntu Lucid Lynx PPA support to Firefox10"
date: 2012-02-03
forum: Security
---

### Post by bala150985 on 2012-02-03
Hi 

I have installed Firefox 9.0.1 on Ubuntu system using PPA and now I see that Firefox 10 is released to address multiple vulnerabilities.  Any idea as to when Firefox 10 would be available for Ubuntu 10.04 ?

[http://www.mozilla.org/en-US/firefox/10.0/releasenotes/](http://www.mozilla.org/en-US/firefox/10.0/releasenotes/)

---

### Post by uRock on 2012-02-03
I believe ubuntu 10.04 is still using Firefox 3.*, which is recieving security patches. You will have to wait for the stable PPA, which I think you are likely using, to get the upgrade. That PPA is maintained by Mozilla, not Canonical.

---

### Post by bala150985 on 2012-02-03
The problem why I had to upgrade is because I went to [https://browsercheck.qualys.com](https://browsercheck.qualys.com) It reported my browser as insecure version, that is why I had to make the upgrade.

---

### Post by uRock on 2012-02-03
There are instructions here for upgrading to the testing versions of Firefox. [http://ubuntuforums.org/showthread.php?t=1712247](http://ubuntuforums.org/showthread.php?t=1712247)

---

### Post by bala150985 on 2012-02-03
I am little concerned about using testing versions in production network.

---

### Post by uRock on 2012-02-03
If you have the mozilla stable PPA installed, then run updates.

Just booted 10.04 with that repo and it is upgrading to Firefox 10.*

---

### Post by claracc on 2012-02-04
> I believe ubuntu 10.04 is still using Firefox 3.*, which is recieving security patches. You will have to wait for the stable PPA, which I think you are likely using, to get the upgrade. That PPA is maintained by Mozilla, not Canonical. 

About one week ago, more or less, my ubuntu 10.04 received a recommended update with firefox 9.0.1 (no ppas, but current security updates ubuntu repositories), before, I had ff 3.6.24.

So, I think now ff 9.0.1 is the "oficial" release in 10.04.

About obtaining ff 10, I think you can find some useful information in this thread:[http://ubuntuforums.org/showthread.php?t=1712247](http://ubuntuforums.org/showthread.php?t=1712247)

---

### Post by claracc on 2012-02-04
I have just received as an important update ff 10.0 in my ubuntu 10.04.

You don't need to use ppas, you'll receive it as "normal" update.

I have noted it quicker than 9.0.1 release.

---

### Post by bala150985 on 2012-02-04
You are correct,  I did sudo apt-get update & sudo apt-get upgrade  wola my firefox got upto 10 :-); Issue resolved thanks to everyone's help.

---

