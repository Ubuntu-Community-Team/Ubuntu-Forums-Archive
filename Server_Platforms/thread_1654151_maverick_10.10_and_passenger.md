---
title: "maverick 10.10 and passenger"
date: 2010-12-27
forum: Server Platforms
---

### Post by danran on 2010-12-27
I'm trying to get Passenger working with Ubuntu 10.10 and I'm running into a problem. It seems that the passenger installer is not recognizing the virtual package. I'm getting this error:
```

passenger-install-apache2-module
...
* OpenSSL support for Ruby... not found
...
```

And then it says, run this:
```
* To install OpenSSL support for Ruby:
   Please run apt-get install libopenssl-ruby as root.
```

When I run the above command, it refers to the libruby package:
```
sudo apt-get install libopenssl-ruby
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libruby' instead of 'libopenssl-ruby'
libruby is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 43 not upgraded.
```

When I look at the details for libruby, it says it provides libopenssl-ruby:
```
Provides: libbigdecimal-ruby, libcurses-ruby, libdbm-ruby, libdl-ruby, libdrb-ruby, liberb-ruby, libgdbm-ruby, libiconv-ruby, libopenssl-ruby, libpty-ruby, libracc-runtime-ruby, libreadline-ruby, librexml-ruby, libsdbm-ruby, libstrscan-ruby, libsyslog-ruby, libtest-unit-ruby, libwebrick-ruby, libxmlrpc-ruby, libyaml-ruby, libzlib-ruby
```

And when I rerun the passenger installer, it gives the same error:
```
passenger-install-apache2-module
...
* OpenSSL support for Ruby... not found
...
```

Let me know if you need more info. How do I fix this?

---

