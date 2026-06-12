---
title: "VCC compiler throws undefined symbol error on varnish initialisation"
date: 2016-01-03
forum: Server Platforms
---

### Post by Ian_Tan on 2016-01-03
Hi everyone, I've been trying to install varnish on a pretty barebones box running precise pangolin and have been getting this error:

```
Setting up varnish (4.1.0-1~trusty) ... * Starting HTTP accelerator varnishd                                                                                                                                         [fail] 
Error:
Message from VCC-compiler:
/usr/sbin/varnishd: symbol lookup error: /usr/lib/varnish/libvarnish.so: undefined symbol: pcre_free_study
Running VCC-compiler failed, exited with 127
VCL compilation failed
invoke-rc.d: initscript varnish, action "start" failed.
dpkg: error processing varnish (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 varnish
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I've installed libpcre3 and libpcre3-dev as well as all related pcre libraries, so I'm not sure what could be causing this issue. I've tried posting on serverfault with no help.

My lsb_release is as follows:

```
Distributor ID:	UbuntuDescription:	Ubuntu 12.04.5 LTS
Release:	12.04
Codename:	precise
```

Any help would be greatly appreciated!

---

### Post by steeldriver on 2016-01-03
Hello and welcome to the forums

How are you trying to install it? did you add a PPA or modify your sources somehow? the version (4.1.0-1~trusty) doesn't seem to belong to 12.04 (precise)

---

### Post by Ian_Tan on 2016-01-03
> **steeldriver said:**
> Hello and welcome to the forums

How are you trying to install it? did you add a PPA or modify your sources somehow? the version (4.1.0-1~trusty) doesn't seem to belong to 12.04 (precise)

Hello. I followed the instructions on the varnish website:

[https://www.varnish-cache.org/installation/ubuntu](https://www.varnish-cache.org/installation/ubuntu)

I didn't notice that version line. That might be the issue!

---

