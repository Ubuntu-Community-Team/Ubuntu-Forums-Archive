---
title: "VMWare in Fedora"
date: 2009-08-04
forum: Virtualisation
---

### Post by DouglasAWh on 2009-08-04
I imagine this is similar to the way things work on Fedora and I've had some bad experiences on their forum, so I'm going to try here.  I obviously would be fine if someone felt it necessary to move this to the Community Cafe section.

I am having to install VMWare to install a virtual appliance.  I am not happen that this vendor has not given an open option for virtualization, but I won't call out any names.

The best instructions I have found are [http://fedorasolved.org/post-install-solutions/vmplayer-install](http://fedorasolved.org/post-install-solutions/vmplayer-install) but those are for 2.0.0 and I have 2.5.2.  There's a patch that I don't think I need.  

I supposedly have VMWare installed, but since I'm not a Fedora person (that's a long story, don't get me started) I'm not sure how to figure out what all that RPM did.  I tried the following.

```

[root@lh /]# locate -i vmware
/etc/selinux/targeted/modules/active/modules/vmware.pp
/home/dwhitfie/Download/VMware-Player-2.5.2-156735.i386.rpm
/usr/lib/xorg/modules/drivers/vmware_drv.so
/usr/share/hwdata/videoaliases/vmware.xinf
/usr/share/man/man4/vmware.4.gz
/usr/share/selinux/devel/include/apps/vmware.if
/usr/share/selinux/targeted/vmware.pp.bz2
/var/cache/vmware
/var/lib/yum/yumdb/V/17173c09acb98a4cad66a63f2af8a334a998cc96-VMware-Player-2.5.2-156735-i386
/var/lib/yum/yumdb/V/17173c09acb98a4cad66a63f2af8a334a998cc96-VMware-Player-2.5.2-156735-i386/from_repo
/var/lib/yum/yumdb/V/17173c09acb98a4cad66a63f2af8a334a998cc96-VMware-Player-2.5.2-156735-i386/reason
/var/lib/yum/yumdb/V/17173c09acb98a4cad66a63f2af8a334a998cc96-VMware-Player-2.5.2-156735-i386/releasever

```

None of that looks like a script I would run to this thing more properly installed.  Is there a .deb version that is similar that I could try to translate such instructions?  I just don't know what file I'm looking for, but I think there is a configuration file I should run.

Thanks!

---

