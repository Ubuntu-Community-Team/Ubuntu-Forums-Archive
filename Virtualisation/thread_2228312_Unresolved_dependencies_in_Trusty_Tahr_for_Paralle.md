---
title: "Unresolved dependencies in Trusty Tahr for Parallels Workstation 6"
date: 2014-06-06
forum: Virtualisation
---

### Post by Robertjm on 2014-06-06
Hi all,

After doing searches on how to resolve this, I've decided to resort to the assembled masses for help. :-)

Recently upgraded my desktop to Ubuntu 14.04 Trusty Tahr (64bit version). Seems to be working, until I went to install Parallels Workstation 6 back to the machine. When running the .run file from Parallels, it throws up an error with three dependencies, which cannot be satisfied.

lib32asound2 = I can find plenty of msgs about multi-arch and this causing problems for TeamViewer. However, it seems like the workaround is to use a different .deb file from TeamViewer. Obviously that's not going to work for PW6.

linux-headers-3.13.0-29-generic = This one puzzles me because when I run sudo apt-get install linux-headers-3.13.0-29-generic I get the message that the latest verison is ALREADY installed on my computer.

Emailing Parallels is worthless because they've pretty much dropped the linux and Windows versions of their virtual world to concentrate on the OSX version. 

If I didn't need to install it so I can extract some stuff from my parallels drives, I wouldn't worry about it. 

Can anyone PLEASE tell me how to resolve these conflicts? Either that, or point me to a place which has specific instructions that are applicable to my case? I've looked to no availe.

Thanks!

Robert

---

### Post by Tadaen_Sylvermane on 2014-06-07
I don't know about installing it but I'm pretty sure Virtualbox can run parallels hard drives / vms.

---

### Post by Robertjm on 2014-06-07
Unless things have recently changed, they can read Parallels drives up to version 2. But, not version 6.

> **Tadaen_Sylvermane said:**
> I don't know about installing it but I'm pretty sure Virtualbox can run parallels hard drives / vms.

---

### Post by bobmalina on 2014-07-03
Hi Robert, 
I've got the same issue with Parallels workstation 6. I've  managed "to cheat" parallels installer in case of linux-headers with  command 
```
sudo ln -s /usr/src/linux-headers-$(uname -r)/include/generated/uapi/linux/version.h  /usr/src/linux-headers-$(uname -r)/include/linux/version.h
```

Alsa lib dependency still not fixed...Did you find something new?

---

### Post by Robertjm on 2014-07-03
I actually ended up installing TeamViewer 9, following some instructions I found on the Web. Turns out there's a problem installing it normally because of Team Viewer not playing nice with multi-arch. 

[http://askubuntu.com/questions/362951/install-teamviewer-using-a-64-bits-system-but-i-get-a-dependency-error](http://askubuntu.com/questions/362951/install-teamviewer-using-a-64-bits-system-but-i-get-a-dependency-error)

Once that happened, it resolved all the problems, except the header problem. Somehow, it started running the installer, and it actually created shortcuts and thinks the problem is installed. However, when I try and run it, it fails.

I will try your suggestion and see if that resolves the issue.

Thanks!!

Robert

> **bobmalina said:**
> ...Alsa lib dependency still not fixed...Did you find something new?

---

### Post by bobmalina on 2014-07-04
It did the trick in my case too...
```
dpkg --add-architecture i386
apt-get update
apt-get install libasound2:i386
```
but installer fails at around 70%... Log file says:
> /tmp/.JJjyJbCax/parallels-kernel-modules/src/drivers/../host.Linux/lin_hyp_api.c: In function &#8216;hypapi_map&#8217;:/tmp/.JJjyJbCax/parallels-kernel-modules/src/drivers/../host.Linux/lin_hyp_api.c:389:22: error: &#8216;KM_SOFTIRQ0&#8217; undeclared (first use in this function)
  rv = kmap_atomic(p, KM_SOFTIRQ0);
                      ^
/tmp/.JJjyJbCax/parallels-kernel-modules/src/drivers/../host.Linux/lin_hyp_api.c:389:22: note: each undeclared identifier is reported only once for each function it appears in
/tmp/.JJjyJbCax/parallels-kernel-modules/src/drivers/../host.Linux/lin_hyp_api.c:389:2: error: too many arguments to function &#8216;kmap_atomic&#8217;
  rv = kmap_atomic(p, KM_SOFTIRQ0);
  ^
In file included from /tmp/.JJjyJbCax/parallels-kernel-modules/src/drivers/../host.Linux/lin_hyp_api.c:19:0:
include/linux/highmem.h:66:21: note: declared here
 static inline void *kmap_atomic(struct page *page)
                     ^
/tmp/.JJjyJbCax/parallels-kernel-modules/src/drivers/../host.Linux/lin_hyp_api.c: In function &#8216;hypapi_unmap&#8217;:
/tmp/.JJjyJbCax/parallels-kernel-modules/src/drivers/../host.Linux/lin_hyp_api.c:402:33: error: macro "kunmap_atomic" passed 2 arguments, but takes just 1
  kunmap_atomic(addr, KM_SOFTIRQ0);
                                 ^
/tmp/.JJjyJbCax/parallels-kernel-modules/src/drivers/../host.Linux/lin_hyp_api.c:402:2: error: &#8216;kunmap_atomic&#8217; undeclared (first use in this function)
  kunmap_atomic(addr, KM_SOFTIRQ0);
  ^
make[3]: *** [/tmp/.JJjyJbCax/parallels-kernel-modules/src/drivers/../host.Linux/lin_hyp_api.o] Error 1
make[2]: *** [_module_/tmp/.JJjyJbCax/parallels-kernel-modules/src/drivers] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-3.13.0-24-generic'
make[1]: *** [prl_hypervisor] Error 2
make[1]: Leaving directory `/tmp/.JJjyJbCax/parallels-kernel-modules/src/drivers'
make: *** [all] Error 2
I'm not programmer, there seems to be something wrong in lin_hyp_api.c file...

---

