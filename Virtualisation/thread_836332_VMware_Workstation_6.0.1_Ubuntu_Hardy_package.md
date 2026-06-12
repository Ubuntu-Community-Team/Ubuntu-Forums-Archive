---
title: "VMware Workstation 6.0.1 Ubuntu Hardy package"
date: 2008-06-21
forum: Virtualisation
---

### Post by zolero on 2008-06-21
_**Introduction:**_

Some time ago I've had created a **VMware Workstation Ubuntu DEB package** for personal use. My package worked flawlessly and smoothly on my laptop, and now it is in use on my brand new Asus desktop box with Ubuntu Hardy too. I've think that it would be helpful to share it with the community, and after few retouches **here it is:**

[http://rapidshare.com/files/121776701/vmwarews_zbt_full.part1.rar](http://rapidshare.com/files/121776701/vmwarews_zbt_full.part1.rar)
[http://rapidshare.com/files/121776702/vmwarews_zbt_full.part2.rar](http://rapidshare.com/files/121776702/vmwarews_zbt_full.part2.rar)
[http://rapidshare.com/files/121779148/vmwarews_zbt_full.part3.rar](http://rapidshare.com/files/121779148/vmwarews_zbt_full.part3.rar)
[http://rapidshare.com/files/121781952/vmwarews_zbt_full.part4.rar](http://rapidshare.com/files/121781952/vmwarews_zbt_full.part4.rar)
[http://rapidshare.com/files/121784281/vmwarews_zbt_full.part5.rar](http://rapidshare.com/files/121784281/vmwarews_zbt_full.part5.rar)
[http://rapidshare.com/files/121787506/vmwarews_zbt_full.part6.rar](http://rapidshare.com/files/121787506/vmwarews_zbt_full.part6.rar)
[http://rapidshare.com/files/121788685/vmwarews_zbt_full.part7.rar](http://rapidshare.com/files/121788685/vmwarews_zbt_full.part7.rar)

_**This package includes:**_

- original tarballs for vmware-workstation-6.0.1 (don't remember the build version number)
- Ubuntu Hardy package for the same version, already patched with any-any-116
- latest update patches from VMware (115, 116 and 117)
- description, install instructions, tips in textfiles and other handy stuffs, you know... ;)

If something misses, please let me know, and I'll add them...

_**Additional info:**_

**1.)** - **DO NOT install the deb package with GDebi**, because this way you'll be unable to interact with the scripts included, and properly install it on your box. Use **"sudo dpkg -i"** instead.
**2.)** - if you don't want to bother later with **configuring internet connection in** your installed **guest OS**, here is a little help on this:

When install script prompts, answer this way (correct answers in UPPERCASE):
```
-----------------------------------------------------------------------------------------
Do you want networking for your virtual machines? (yes/no/help) [yes] YES

Configuring a bridged network for vmnet0.

The following bridged networks have been defined:

    vmnet0 is bridged to eth0

All your ethernet interfaces are already bridged.

Do you want to be able to use NAT networking in your virtual machines? (yes/no)
[yes] NO

Do you want to be able to use host-only networking in your virtual machines?
[no] NO
-----------------------------------------------------------------------------------------
```Now you're ABLE TO CONNECT TO WEB DIRECTLY from guest OS via host OS's network connection.

**3.)** - alternatively **you can** build a newer version of VMware Workstation based on my work. Just study a bit, to figure out how I've made it, and **build your own**...;)

Feel free to post here your problems on using this (if any :-D  ), and we'll see what could help to manage it correctly... Have a nice big time with VMware Workstation Linux on Ubuntu Hardy. :)


_**PS:   Some (useful) addition:**_

Instructions for rebuilding the DEB pakage with latest available patch (perhaps newer versions?)

1.) Obtain the newest available update patch (vmware-any-any-updateXXX tarball, where XXX indicates
    the patch version) and unpack it wherever on the HDD.

2.) Unpack the Ubuntu DEB package hierarchy from the TAR.BZ2 tarball( included here with same name as
    the package itself, but ready for building).

3.) Copy/write over VMBLOCK, VMMON and VMNET tarballs from patch directory into DEB package hierarchy
    /usr/lib/vmware/modules/source directory.

4.) Recalculate MD5SUM for the package, and replace old /DEBIAN/md5sums with the new one.

5.) Go up one folder level and build the newly patched Ubuntu DEB package with the build-script or by
    issuing in the console:

    # (sudo) dpkg --build <deb_directory_name>

That's it.

NOTE:  Don't change ANYTHING ELSE in the package. If you change my scripts, it may be possible to NOT
       work as expected. Do that only if you are really capable to improve them correctly, and please
       drop me an email to taking knowledge about this. Cheers...

---

### Post by atlas95 on 2008-06-21
Thanks for this ! But the hosting ban me after one download part :(
Could you host it on another website?

Best regards

---

### Post by gajukutty on 2009-06-10
tell how to convert this into deb..

---

### Post by zolero on 2009-07-09
> **gajukutty said:**
> tell how to convert this into deb..

You do not have to convert it. Download all parts, and unpack the RAR. You'll get a deb package (amongst some other things). Go and install it...

---

### Post by mani20 on 2009-07-09
hi

My system doesnt support ubuntu can anyone tell me the system configuration required for this ubuntu

[personal defense alarms](http://www.totalsecurityforyou.com/products.asp?categoryid=53)
[Commercial Lawyers Melbourne](http://www.rosendorff.com.au/)

Thanks in advance.......

---

### Post by zolero on 2009-07-11
> **mani20 said:**
> hi

My system doesnt support ubuntu can anyone tell me the system configuration required for this ubuntu

Thanks in advance.......

Hey **mani20** ... I won't flame, you, but this is not true. Ubuntu supports even very old systems, but I guess that this is not your case. :p

---

### Post by 830.patrickd on 2009-10-02
now do sudo upt-get install -f

---

### Post by 830.patrickd on 2009-10-02
ok the fist one you shoud do is sudo apt-get -f install

---

