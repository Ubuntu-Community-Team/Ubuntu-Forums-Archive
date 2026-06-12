---
title: "[Ubuntu_Mate] Caja-dropbox installation"
date: 2014-10-04
forum: Ubuntu/Debian BASED
---

### Post by linuxyogi on 2014-10-04
Hi. 

I am using Ubuntu Mate. When I click on the dropbox icon caja opens but I want the 

dropbox right click context menu so that I can copy the links for sharing files.

I read that installing caja-dropbox will add this feature. 

[This is the caja-dropbox page.]("https://github.com/mate-desktop/caja-dropbox")

I am getting this error 

```
 configure: error: Package requirements (libcaja-extension >= 1.1.0) were not met:

No package 'libcaja-extension' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables CAJA_CFLAGS
and CAJA_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


```

```
$ sudo apt-get install libcaja-extension
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libcaja-extension1' instead of 'libcaja-extension'
libcaja-extension1 is already the newest version.
```

```
$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Utopic Unicorn (development branch)
Release:    14.10
Codename:    utopic


```

Googled a lot didn't find a single PPA.

---

### Post by Bucky Ball on 2014-10-04
*Thread moved to **Other Operating Systems and Projects**.*

Sorry, but General Help, as most areas of the forums, are "... for your questions regarding Ubuntu, Kubuntu, Xubuntu, Edubuntu, Lubuntu, UbuntuGnome, Ubuntu Studio, and Mythbuntu."

Ubuntu Mate, as far as I can tell, and disregarding the heresay, is not supported officially here. Good luck and thanks for posting in a support area. While you should feel free to post here, have you tried posting in the Mate forums, too? You might get some response ...

---

### Post by linuxyogi on 2014-10-04
> **Bucky Ball said:**
> 
Ubuntu Mate, as far as I can tell, and disregarding the heresay, is not supported officially here. Good luck and thanks for posting in a support area. While you should feel free to post here, have you tried posting in the Mate forums, too? You might get some response ...

Okay I will post this in the Mate forums but the situation is bit complicated.

[This user]("http://forums.mate-desktop.org/viewtopic.php?f=17&t=224#p1710") had installed caja-dropbox by doing a simple

```
apt-get install caja-dropbox
```

which most probably means he is using Debian or Ubuntu with 

the Mate repos. 

Since I am using Ubuntu Mate afaik the packaging and all

is handled by the Ubuntu Mate team. So I don't think I will

be able to add the vanilla Mate repo.

I will post there and if I get a solution I will write back.

Thanks.

---

### Post by buzzingrobot on 2014-10-04
A libcaja-extension package is available in the Utopic repos: [http://packages.ubuntu.com/utopic/libcaja-extension1](http://packages.ubuntu.com/utopic/libcaja-extension1). There's no caja-dropbox package, nor is there one in Debian backports.

---

### Post by linuxyogi on 2014-10-04
> **buzzingrobot said:**
> A libcaja-extension package is available in the Utopic repos: [http://packages.ubuntu.com/utopic/libcaja-extension1](http://packages.ubuntu.com/utopic/libcaja-extension1). There's no caja-dropbox package, nor is there one in Debian backports.

Yes, but libcaja-extension1 is installed but still the compilation is still failing  

```
configure: error: Package requirements (libcaja-extension >= 1.1.0) were not met:

No package 'libcaja-extension' found 
```

```
$ aptitude show libcaja-extension1 |grep State
State: installed 
```

```
$ aptitude show libcaja-extension1 |grep Version
Version: 1.8.1-2
```

---

### Post by linuxyogi on 2014-10-04
I have emailed two maintainers of caja-dropbox, requesting for a Ubuntu PPA.

If they create one soon then its good news and if they don't I guess I will have 

to wait for the Ubuntu Mate team for them to add that package with required 

deps.

In the meantime I have installed Mate over my existing Manjaro LXDE installation

and installed caja-dropbox from AUR.

---

### Post by Bucky Ball on 2014-10-05
Glad you got it sorted and thanks for sharing how. Would you consider this thread resolved, if not exactly solved? If so, please mark the thread as solved to help others. :)

Unfortunately, we don't have a 'resolved' option.

---

