---
title: "Dependency issues."
date: 2012-08-02
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by vinay_wagh on 2012-08-02
While pulling the daily updates, I had  "libexttextcat-data" available for upgrade. However the upgrade suggests removal of several packages including  libreoffice-core, libreoffice-calc, libreofice-writer, etc. 

Upon  proceeding further, it is not possible to install any of these packages. 
When I tried to  install "libreoffice-base", I got the following:

libreoffice-base:
 Depends: libreoffice-core but it is not going to be installed
 Depends: libreoffice-base-core but it is not going to be installed
 

Now I dont have libreoffice at all. How can I install the same?


I also found a bug [here]("https://bugs.launchpad.net/ubuntu/+source/tasksel/+bug/1031779"). Thanks in advance for the help.

 

VInay

---

### Post by vinay_wagh on 2012-08-02
Forgot to mention similar issue with one more package: "xserver-xorg-core". Although it didnt remove much ``important`` package.

Here is a brief log:

Removed the following packages:
xserver-xorg-input-all
xserver-xorg-input-vmmouse
xserver-xorg-video-all
xserver-xorg-video-geode
xserver-xorg-video-vmware

Upgraded the following packages:
xserver-xorg-core (2:1.12.1.902-1ubuntu1) to 2:1.12.99.902-0ubuntu1


VInay

---

### Post by dino99 on 2012-08-02
you need some more patience to wait for additional missing packages updates :guitar:

or read the other related threads here (already been discussed )

---

### Post by Harry33 on 2012-08-02
> **vinay_wagh said:**
> Forgot to mention similar issue with one more package: "xserver-xorg-core". Although it didnt remove much ``important`` package.

Here is a brief log:

Removed the following packages:
xserver-xorg-input-all
xserver-xorg-input-vmmouse
xserver-xorg-video-all
xserver-xorg-video-geode
xserver-xorg-video-vmware

Upgraded the following packages:
xserver-xorg-core (2:1.12.1.902-1ubuntu1) to 2:1.12.99.902-0ubuntu1

VInay

Those packages removed are really not generally needed. From those vmware has been uploaded into repos. The *-all packages ensure that all input and video drivers are installed, even though you practically need only *-input-evdev and possibly *-synaptics plus *-video-vesa and the one correct driver according to your graphics card.

Remember that xserver 1.13 + its drivers are currently still in the  proposed repository. That is not recommended to be enabled, exactly for  the reason you are experiencing right now.

---

### Post by Harry33 on 2012-08-02
> **vinay_wagh said:**
> While pulling the daily updates, I had  "libexttextcat-data" available for upgrade. However the upgrade suggests removal of several packages including  libreoffice-core, libreoffice-calc, libreofice-writer, etc. 

Upon  proceeding further, it is not possible to install any of these packages. 
When I tried to  install "libreoffice-base", I got the following:

libreoffice-base:
 Depends: libreoffice-core but it is not going to be installed
 Depends: libreoffice-base-core but it is not going to be installed
 
Now I dont have libreoffice at all. How can I install the same?

I also found a bug [here]("https://bugs.launchpad.net/ubuntu/+source/tasksel/+bug/1031779"). Thanks in advance for the help.

VInay

The issue is due to the fact that libreoffice-core depends on libexttextcat0.
That packages has now a different name (libexttextcat-1.0-0) and thus libreoffice needs to be rebuilt against it first.
Do not try to upgrade the version 3.2.0-2ubuntu1.

---

### Post by vinay_wagh on 2012-08-02
@Harry,
Thanks for your reply.  Currently I do not have any problem with the xserver-* packages. My main problem is I have lost my libreoffice due to  "libexttextcat-data" and not able to reinstall it. In fact I also tried  forcing the lower version of dependency packages, but didnt help much.

@Dino,
I couldnt find "other" threads ,except [this]("http://ubuntuforums.org/showthread.php?t=2035795") one. Can you please point them out to me?

Thanks
VInay

---

### Post by Harry33 on 2012-08-02
> **vinay_wagh said:**
> @Harry,
Thanks for your reply.  Currently I do not have any problem with the xserver-* packages. My main problem is I have lost my libreoffice due to  "libexttextcat-data" and not able to reinstall it. In fact I also tried  forcing the lower version of dependency packages, but didnt help much.

@Dino,
I couldnt find "other" threads ,except [this]("http://ubuntuforums.org/showthread.php?t=2035795") one. Can you please point them out to me?

Thanks
VInay

See above, only use the earlier version of libexttextcat (3.2.0-2ubuntu1)

---

### Post by vinay_wagh on 2012-08-02
> **Harry33 said:**
> Again, you should not keep proposed repo enabled.

The issue is due to the fact that libreoffice-core depends on libexttextcat0.
That packages has now a different name and thus libreoffice needs to be rebuild against it first.
Do not try to upgrade this.

Thanks. I guess I tried to reply to your earlier post and missed this one. 

Unfortunately I have now already proceeded with the update of this package. So is there any solution or workaround, other than waiting for the rebuild?

VInay

---

### Post by Harry33 on 2012-08-02
> **vinay_wagh said:**
> Thanks. I guess I tried to reply to your earlier post and missed this one. 

Unfortunately I have now already proceeded with the update of this package. So is there any solution or workaround, other than waiting for the rebuild?

VInay

You can manually download the correct packages from here:
[https://launchpad.net/ubuntu/quantal/+source/libexttextcat/3.2.0-2ubuntu1](https://launchpad.net/ubuntu/quantal/+source/libexttextcat/3.2.0-2ubuntu1)
Note, that the package libexttextcat-data is the section quantal i386.
Then choose the correct section (quantal i386 or quantal amd64) for the package libexttextcat0.
After downloading those two, open terminal and go to the directory where they are and run this command (be sure there are no other*.deb packages):
```

sudo dpkg -i *.deb

```

Then install the removed libreoffice packages back.

---

### Post by vinay_wagh on 2012-08-02
> **Harry33 said:**
> You can manually download the correct packages from here:
[https://launchpad.net/ubuntu/quantal/+source/libexttextcat/3.2.0-2ubuntu1](https://launchpad.net/ubuntu/quantal/+source/libexttextcat/3.2.0-2ubuntu1)
Note, that the package libexttextcat-data is the section quantal i386.
Then choose the correct section (quantal i386 or quantal amd64) for the package libexttextcat0.
After downloading those two, open terminal and go to the directory where they are and run this command (be sure there are no other*.deb packages):
```

sudo dpkg -i *.deb

```Then install the removed libreoffice packages back.

I will try to install it as suggested above and let you know.

---

### Post by vinay_wagh on 2012-08-02
> **Harry33 said:**
> You can manually download the correct packages from here:
[https://launchpad.net/ubuntu/quantal/+source/libexttextcat/3.2.0-2ubuntu1](https://launchpad.net/ubuntu/quantal/+source/libexttextcat/3.2.0-2ubuntu1)
Note, that the package libexttextcat-data is the section quantal i386.
Then choose the correct section (quantal i386 or quantal amd64) for the package libexttextcat0.
After downloading those two, open terminal and go to the directory where they are and run this command (be sure there are no other*.deb packages):
```

sudo dpkg -i *.deb

```Then install the removed libreoffice packages back.

Yes it worked. Thanks a lot!

I am just wondering when I tried to force the lower version of "libexttextcat-data" via synaptic (I am still a fan of synaptic!), it gave me dependency error, howeverdpkg -i *.deb had no problem!

VInay

---

### Post by Harry33 on 2012-08-02
> **vinay_wagh said:**
> Yes it worked. Thanks a lot!

I am just wondering when I tried to force the lower version of "libexttextcat-data" via synaptic (I am still a fan of synaptic!), it gave me dependency error, howeverdpkg -i *.deb had no problem!

VInay

That dependency error with synaptic is due to the fact that both libexttext-data nad libexttextcat0 should be installed at the same time. And the new libexttextcat-1.0-0 must be removed at that same time, if installed. Synaptic cannot handle this kind of multitasking.

---

### Post by Harry33 on 2012-08-02
The new libreoffice will soon hit the QQ repos, if there will be no failures building it.

Here:
[https://launchpad.net/ubuntu/quantal/+source/libreoffice/1:3.6.0~rc4-0ubuntu2](https://launchpad.net/ubuntu/quantal/+source/libreoffice/1:3.6.0~rc4-0ubuntu2)

This build will depend on the new libexttextcat-1.0-0.

---

### Post by vinay_wagh on 2012-08-03
> **dino99 said:**
> you need some more patience to wait for additional missing packages updates :guitar:


It seems the wait is over. I just now Upgraded the following packages:

libexttextcat-data, libreoffice-base, libreoffice-base-core,  libreoffice-calc, libreoffice-common, libreoffice-core, libreoffice-java-common, libreoffice-style-human, libreoffice-writer, uno-libs3, ure

It also installed "libexttextcat-1.0-0" and removed "libexttextcat0".


I guess now everything is in order.

VInay

---

### Post by Harry33 on 2012-08-03
Yes it is, for libexttextcat.
For xserver 1.13 it is another story,, though.

---

### Post by vinay_wagh on 2012-08-03
> **Harry33 said:**
> Yes it is, for libexttextcat.
For xserver 1.13 it is another story,, though.

Yeah. Thats true. Another issue is with webapps. I dont know what has gone wrong, I have lost "Online Accoutns" icon from system settings. I am yet to figure out. May be will do that over the weekend.

---

### Post by somnoliento on 2012-09-05
It still fails for me, from Lucid, using the LibreOffice PPA.

---

### Post by dino99 on 2012-09-06
> **somnoliento said:**
> It still fails for me, from Lucid, using the LibreOffice PPA.

might be time to purge that ppa

---

### Post by sorochan on 2012-09-23
> **dino99 said:**
> might be time to purge that ppa

best advice ever!  I did just that and now all is better that before the libexttextcat conflict with the ppa

1. purge the ppa with ppa-purge (do everything it says), apt-get update, apt-get dist-upgrade

2. install libreoffice from a downloadable package

---

