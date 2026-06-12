---
title: "how to install gimp"
date: 2016-05-02
forum: Ubuntu/Debian BASED
---

### Post by yazeed2 on 2016-05-02
hello everyone 

hope you all fine 


I'm trying to install gimp 
but this what happen 

```
The following packages have unmet dependencies:
 gimp : Depends: libgegl-0.2-0 (>= 0.2.0) but it is not going to be installed
        Depends: libwebkitgtk-1.0-0 (>= 1.3.10) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


```

i searched and i didnt find any solution works
I hope to find a solution here
many thank

---

### Post by T.J. on 2016-05-02
> **yazeed2 said:**
> hello everyone 

hope you all fine 


I'm trying to install gimp 
but this what happen 

```
The following packages have unmet dependencies:
 gimp : Depends: libgegl-0.2-0 (>= 0.2.0) but it is not going to be installed
        Depends: libwebkitgtk-1.0-0 (>= 1.3.10) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


```

i searched and i didnt find any solution works
I hope to find a solution here
many thank


Did you try *sudo apt-get install gimp*?

Assuming that failed, your repository sources might be incorrect or incomplete:

/etc/apt/sources.list
```

 #deb cdrom:[Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1)]/ xenial main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ xenial main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial universe
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu xenial partner
# deb-src http://archive.canonical.com/ubuntu xenial partner


deb http://security.ubuntu.com/ubuntu xenial-security main restricted
# deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
deb http://security.ubuntu.com/ubuntu xenial-security universe
# deb-src http://security.ubuntu.com/ubuntu xenial-security universe
deb http://security.ubuntu.com/ubuntu xenial-security multiverse
# deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse



```

---

### Post by gnusci on 2016-05-02
Did you tried:

sudo apt-get install -f

If it does not fix your issue, then try with:

[http://www.iasptk.com/ubuntu-fix-broken-package-best-solution/](http://www.iasptk.com/ubuntu-fix-broken-package-best-solution/)

---

### Post by deadflowr on 2016-05-02
Which version of Ubuntu are you running?

---

### Post by yazeed2 on 2016-05-03
> **gnusci said:**
> Did you tried:

sudo apt-get install -f

If it does not fix your issue, then try with:

[http://www.iasptk.com/ubuntu-fix-broken-package-best-solution/](http://www.iasptk.com/ubuntu-fix-broken-package-best-solution/)

when i tried this Command in bage you gave me :
[B]```
sudo apt-get update –fix-missing
E: The update command takes no arguments
```

i tried everything and nothing works

[/B]


> **T.J. said:**
> Did you try *sudo apt-get install gimp*?

Assuming that failed, your repository sources might be incorrect or incomplete:

/etc/apt/sources.list
```

 #deb cdrom:[Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1)]/ xenial main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ xenial main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial universe
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu xenial partner
# deb-src http://archive.canonical.com/ubuntu xenial partner


deb http://security.ubuntu.com/ubuntu xenial-security main restricted
# deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
deb http://security.ubuntu.com/ubuntu xenial-security universe
# deb-src http://security.ubuntu.com/ubuntu xenial-security universe
deb http://security.ubuntu.com/ubuntu xenial-security multiverse
# deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse



```


Sorry I did not understand  well when I put this[COLOR=#ff0000]** /etc/apt/sources.list **[/COLOR]in terminal 
this what gives me
```
bash: /etc/apt/sources.list: Permission denied
```



i
> **deadflowr said:**
> Which version of Ubuntu are you running?

i run distro based on * Ubuntu* 14.04 LTS

---

### Post by deadflowr on 2016-05-03
Try:
```
sudo apt-get update
sudo apt-get upgrade
```
Post any errors if any exist.

> i run distro based on Ubuntu 14.04 LTS

What exactly?

---

### Post by yazeed2 on 2016-05-03
> **deadflowr said:**
> Try:
```
sudo apt-get update
sudo apt-get upgrade
```
Post any errors if any exist.



What exactly?

update & upgrade works well no errors 
i run 
elementary os freya

---

### Post by deadflowr on 2016-05-03
*Thread moved to **Ubuntu/Debian BASED**.*
(And changed prefix to Elementary) 

Now what happens when you try to install gimp?
Same as before?

If so, did you try the *sudo apt-get install -f* command again?

---

### Post by yazeed2 on 2016-05-03
> **deadflowr said:**
> *Thread moved to **Ubuntu/Debian BASED**.*
(And changed prefix to Elementary) 

Now what happens when you try to install gimp?
Same as before?

If so, did you try the *sudo apt-get install -f* command again?

thanks for moveing it 

,,

same as before and i tryd this command [COLOR=#ff0000][I]sudo apt-get install -f 
[/I][/COLOR][COLOR=#000000][I]and install gimp again 
The same problem Nothing happened[/I][/COLOR][COLOR=#ff0000][/COLOR]

---

### Post by yazeed2 on 2016-05-03
i solved The problem 
go to; software updater / settings / other software 
and mark on gimp ppa
you will find 2 of them 
  and then update 
and install gimp 
enjoy

thanks

---

### Post by oldrocker99 on 2016-05-03
If your problem is solved, please mark it as [SOLVED] in the Thread Tools at the upper right. Thank you.

---

