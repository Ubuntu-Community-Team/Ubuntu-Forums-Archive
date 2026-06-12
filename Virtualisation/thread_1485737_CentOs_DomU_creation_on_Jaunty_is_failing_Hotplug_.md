---
title: "CentOs DomU creation on Jaunty is failing Hotplug scripts not working."
date: 2010-05-17
forum: Virtualisation
---

### Post by tapas_mishra on 2010-05-17
I finally downloaded CentOS 5.5 DVD for 64 bit.
Loop mounted the DVD to a local directory which is in document root of webserver.
So [http://localhost/centos/](http://localhost/centos/) is available to install.
Now comes the problem.
Searching on some of the blogs and forums for example 
[http://www.infohit.net/blog/adate/063009/archive/1.html](http://www.infohit.net/blog/adate/063009/archive/1.html)
found that add  three lines ```

nss
nspr
python-iniparse 
```to 
/etc/rinse/centos-5.packages
but these lines were already present.

I downloaded vmlinuz and initrd for CentOS
```

wget http://mirror.centos.org/centos/5/os/x86_64/images/xen/vmlinuz -O /boot/vmlinuz-xen-install
wget http://mirror.centos.org/centos/5/os/x86_64/images/xen/initrd.img -O /boot/initrd-xen-install
```

and then executed 
```

xen-create-image --hostname=centos --size=96GB --swap=4096Mb --ip=192.168.1.16 --memory=2048 --arch=amd64 --role=udev --force --install-method=rinse  --kernel=/boot/vmlinuz-xen-install --initrd=/boot/initrd-xen-install --install-source=http://localhost/centos/ 
```

but after it starts I get error.

```

WARNING
-------

  You appear to have a "dummy" vif-script, or network-script, setting
 in the Xen configuration file /etc/xen/xend-config.sxp.

  Please fix this and restart Xend, or your guests will not be able to
 use any networking!


  We're trying to configure an installation of centos5 in
  - but there is no hook directory for us to use.

  This means we don't know how to configure this installation.

  We'd expect the hook directory to be : /usr/lib/xen-tools/centos5.d

  Aborting.


Logfile produced at:
     /var/log/xen-tools/centos.log


```
The log file which the above error has  mentioned does not contain any thing.So what should  I check now.Is any of my methods wrong then let me know.

---

