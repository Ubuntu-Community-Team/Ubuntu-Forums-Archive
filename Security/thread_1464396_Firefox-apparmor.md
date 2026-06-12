---
title: "Firefox-apparmor"
date: 2010-04-28
forum: Security
---

### Post by ubuchignome on 2010-04-28
Anyone set up an Apparmor profile for Firefox?

---

### Post by wojox on 2010-04-28
Already there. Just need to enable it [https://help.ubuntu.com/community/AppArmor#How%20can%20I%20enable%20AppArmor%20for%20Firefox?](https://help.ubuntu.com/community/AppArmor#How%20can%20I%20enable%20AppArmor%20for%20Firefox?)

---

### Post by lovinglinux on 2010-04-28
I'm not sure if it was bodhi.zazen who created the default profile shipped with Ubuntu (probably yes), but [here is his collection](http://bodhizazen.net/aa-profiles/).

---

### Post by Soul-Sing on 2010-04-28
> **lovinglinux said:**
> I'm not sure if it was bodhi.zazen who created the default profile shipped with Ubuntu (probably yes), but [here is his collection](http://bodhizazen.net/aa-profiles/).

jamie strandboge.

---

### Post by ubuchignome on 2010-04-28
It is installed but disabled, will not enable. Any ideas as to why? 
 
Thanks much

---

### Post by wojox on 2010-04-28
I'm on 9.10

```

wojox@wojox-desktop:~$ sudo aa-enforce /etc/apparmor.d/usr.bin.firefox-3.5
[sudo] password for wojox: 
Setting /etc/apparmor.d/usr.bin.firefox-3.5 to enforce mode.
wojox@wojox-desktop:~$

```

---

### Post by ubuchignome on 2010-04-28
Thanks much, will try that.

---

### Post by jeffdacosta on 2010-04-28
[http://www.dtschmitz.com/dts/2009/07/how-to-install-apparmor-profile-for-firefox-351-in-ubuntu-904.html](http://www.dtschmitz.com/dts/2009/07/how-to-install-apparmor-profile-for-firefox-351-in-ubuntu-904.html), here you can find a lot of information about, thanks for sharing.

---

### Post by bodhi.zazen on 2010-04-28
> **lovinglinux said:**
> I'm not sure if it was bodhi.zazen who created the default profile shipped with Ubuntu (probably yes), but [here is his collection]("http://bodhizazen.net/aa-profiles/").

No, I did not write the default profile for Ubuntu.

In my aa profile collection I *try* to stay as close to the default profiles as I can or only add a profile if there is not one already a default profile in existence.

I am in process of updating my aa profiles for Ubuntu 10.04. My goal is now to make them as quiet as possible so that one can use apparmor-notify without excessive noise.

---

### Post by ubuchignome on 2010-04-29
Thanks all,

Be well

---

