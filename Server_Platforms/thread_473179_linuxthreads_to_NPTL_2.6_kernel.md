---
title: "linuxthreads to NPTL 2.6 kernel"
date: 2007-06-13
forum: Server Platforms
---

### Post by TripleE on 2007-06-13
Yes, I have done it.  I have somehow screwed up my Zimbra server (personal server).  It will not start.  When i tried to reinstall/upgrade Zimbra it failed at "NPTL...MISSING".  Now I am blaming the Xen install that I did on the same server, but I cannot confirm that even though it was the last thing I installed before Zimbra stopped working.  After some looking around, I was recommended to check:
```
$ getconf GNU_LIBPTHREAD_VERSION
linuxthreads-0.10

$ uname -r
2.6.15-28-686
```

Now a 2.6 kernel should be showing NPTL not linuxthreads.  NPTL is required for zimbra to run.  So after some tinkering around.  I uninstalled all the packages that I installed for Xen:
```
sudo aptitude remove binutils    bridge-utils    debootstrap    python-crypto    python-pam    Python-pyopenssl    python-serial    python-soappy    python-twisted    python-twisted-conch    python-twisted-core    python-twisted-lore    python-twisted-mail    python-twisted-names    python-twisted-news    python-twisted-runner    python-twisted-web    python-twisted-words    python-zopeinterface    python2.4-crypto    python2.4-pam    python2.4-pyopenssl    python2.4-soappy    python2.4-twisted    python2.4-twisted-bin    python2.4-twisted-conch    python2.4-twisted-core    python2.4-twisted-lore    python2.4-twisted-mail    python2.4-twisted-names    python2.4-twisted-news    python2.4-twisted-runner    python2.4-twisted-web    python2.4-twisted-words    python2.4-xml    python2.4-zopeinterface
```

Then I uninstalled/removed Xen as root:
```
sudo -s
[ -d /etc/xen ] && mv -f /etc/xen /etc/xen.old-`date +%s` || true
          rm -rf /etc/init.d/xend*
          rm -rf /etc/hotplug/xen-backend.agent
          rm -f  /etc/udev/rules.d/xen-backend.rules
          rm -f  /etc/udev/xen-backend.rules
          rm -f  /etc/sysconfig/xendomains
          rm -rf /var/run/xen* /var/lib/xen*
          rm -rf /boot/*xen*
          rm -rf /lib/modules/*xen*
          rm -rf /usr/bin/xen* /usr/bin/lomount
          rm -rf /usr/bin/cpuperf-perfcntr $(D)/usr/bin/cpuperf-xen
          rm -rf /usr/bin/xc_shadow
          rm -rf /usr/bin/pygrub
          rm -rf /usr/bin/setsize /usr/bin/tbctl
          rm -rf /usr/bin/xsls
          rm -rf /usr/include/xenctrl.h /usr/include/xenguest.h
          rm -rf /usr/include/xs_lib.h /usr/include/xs.h
          rm -rf /usr/include/xen
          rm -rf /usr/$(LIBDIR)/libxenctrl* /usr/$(LIBDIR)/libxenguest*
          rm -rf /usr/$(LIBDIR)/libxenstore*
          rm -rf /usr/$(LIBDIR)/python/xen /usr/$(LIBDIR)/python/grub
          rm -rf /usr/$(LIBDIR)/xen/
          rm -rf /usr/lib/xen/
          rm -rf /usr/local/sbin/setmask /usr/local/sbin/xen*
          rm -rf /usr/sbin/xen* /usr/sbin/netfix /usr/sbin/xm
          rm -rf /usr/share/doc/xen
          rm -rf /usr/share/xen
          rm -rf /usr/share/man/man1/xen*
          rm -rf /usr/share/man/man8/xen*
```

Next is getting back to NPTL:
```
sudo aptitude reinstall libc6
```

Now after a reboot, this worked for me.  So I thought I would share it with you.  I am not an expert.  So please feel free to correct me.

---

