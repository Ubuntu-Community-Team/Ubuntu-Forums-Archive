---
title: "CentOS 5.5 Service Disabler Bash Script"
date: 2010-09-09
forum: The Cafe
---

### Post by EMCGFX on 2010-09-09
I’ve wrote small script that will automatically disable unneeded services for you. Very useful for system administrators to due fast deployment. Its every easy to modify, just add or remove services from array called service. (make sure you use spaces between defined services)

By default it will disable this following services.
```
NetworkManager acpid anacron apmd atd avahi-daemon avahi-dnsconfd bluetooth capi conman cpuspeed cups dnsmasq dund firstboot gpm hidd ibmasm ip6tables irda isdn mcstrans mdmonitor mdmpd microcode_ctl multipathd netconsole netfs netplugd nfs nfslock nscd oddjobd pand pcscd portmap psacct rawdevices rdisc readahead_early readahead_later rpcgssd rpcidmapd rpcsvcgssd saslauthd smartd tcsd wpa_supplicant ypbind yum-updatesd
```

Download: [http://coderbytes.com/files/bash/coskill.sh]("http://coderbytes.com/files/bash/coskill.sh")

---

