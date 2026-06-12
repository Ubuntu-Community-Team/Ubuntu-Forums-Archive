---
title: "UPnP/DLNA on Ubuntu Server 11.10"
date: 2011-10-21
forum: Server Platforms
---

### Post by Largoh on 2011-10-21
I've just come from FreeNAS because I was fed up of the limitations, so figured I'd try Ubuntu Server.

Everything I need is now setup and working perfectly apart from UPnP. I've spent 2 days solid now tyring to get it working and I just can't do it! It's getting on my nerves!

Firstly, I installed MediaTomb which worked great from the get go. The only problem is that it doesn't support Xbox 360.

I need UPnP/DNLA that will work for PS3, 360 and other devices (such as my Galaxy Tab). All of this was achieved with fuppes on FreeNAS, so I tried compiling that.

After countly errors, I gave up. I managed to get ./configure to work eventually but now when I try "make" I get:

> 
src/Makefile.am:6: Libtool library used but `LIBTOOL' is undefined
src/Makefile.am:6:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
src/Makefile.am:6:   to `configure.in' and run `aclocal' and `autoconf' again.
src/Makefile.am:6:   If `AC_PROG_LIBTOOL' is in `configure.in', make sure
src/Makefile.am:6:   its definition is in aclocal's search path.
make: *** [Makefile.in] Error 1


libtoolize --version tells me:
libtoolize (GNU libtool) 2.4

So I'm lost with that.

I then went on to try uShare (Which I had tried previously but it never did anything)

I followed this guide: [http://www.fscker.ca/rc/2010/10/25/create-an-ubuntu-upnpdnla-server/](http://www.fscker.ca/rc/2010/10/25/create-an-ubuntu-upnpdnla-server/)

Following the guide, it seemed to be working. I was able to get to the WEBUI, but anytime I tried to change a share or do anything in fact, it would tell me that the page can't be found.

So I rebooted, and since then I've not been able to get uShare to work. suing service ushare start just says that the service has started, but it's not working at all, I'm assuming that it's crashing somehow.

I tried ushare -x but it complains that eth0 is down. It isn't, everything else is using it fine.

This is really starting to get on my nerves tbh, all I want to do is share my media with my devices. Why is that so hard to achieve?!

I'd very much appreciate your help with this.

EDIT:

After running aclocal, I manage to move further, but am now getting stuck here:

> /bin/bash ../libtool  --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I/usr/include/taglib -D__STDC_CONSTANT_MACROS   -I/usr/include/libxml2         -g -O2 -MT UPnPAction.lo -MD -MP -MF .deps/UPnPAction.Tpo -c -o UPnPAction.lo `test -f 'lib/UPnPActions/UPnPAction.cpp' || echo './'`lib/UPnPActions/UPnPAction.cpp
../libtool: line 894: X--tag=CXX: command not found
../libtool: line 927: libtool: ignoring unknown tag : command not found
../libtool: line 894: X--mode=compile: command not found
../libtool: line 1060: *** Warning: inferring the mode of operation is deprecated.: command not found
../libtool: line 1061: *** Future versions of Libtool will require --mode=MODE be specified.: command not found
../libtool: line 1204: Xg++: command not found
../libtool: line 1204: X-DHAVE_CONFIG_H: command not found
../libtool: line 1204: X-I.: command not found
../libtool: line 1204: X-I/usr/include/taglib: No such file or directory
../libtool: line 1204: X-D__STDC_CONSTANT_MACROS: command not found
../libtool: line 1204: X-I/usr/include/libxml2: No such file or directory
../libtool: line 1204: X-g: command not found
../libtool: line 1204: X-O2: command not found
../libtool: line 1204: X-MT: command not found
../libtool: line 1204: XUPnPAction.lo: command not found
../libtool: line 1204: X-MD: command not found
../libtool: line 1204: X-MP: command not found
../libtool: line 1204: X-MF: command not found
../libtool: line 1204: X.deps/UPnPAction.Tpo: No such file or directory
../libtool: line 1204: X-c: command not found
../libtool: line 1255: XUPnPAction.lo: command not found
../libtool: line 1260: libtool: compile: cannot determine name of library object from `': command not found
make[1]: *** [UPnPAction.lo] Error 1
make[1]: Leaving directory `/home/largo/fuppes/src'
make: *** [install-recursive] Error 1


---

### Post by reddevil2064 on 2011-10-21
> **Largoh said:**
> I've just come from FreeNAS because I was fed up of the limitations, so figured I'd try Ubuntu Server.

Everything I need is now setup and working perfectly apart from UPnP. I've spent 2 days solid now tyring to get it working and I just can't do it! It's getting on my nerves!

Firstly, I installed MediaTomb which worked great from the get go. The only problem is that it doesn't support Xbox 360.

I need UPnP/DNLA that will work for PS3, 360 and other devices (such as my Galaxy Tab). All of this was achieved with fuppes on FreeNAS, so I tried compiling that.

After countly errors, I gave up. I managed to get ./configure to work eventually but now when I try "make" I get:



libtoolize --version tells me:
libtoolize (GNU libtool) 2.4

So I'm lost with that.

I then went on to try uShare (Which I had tried previously but it never did anything)

I followed this guide: [http://www.fscker.ca/rc/2010/10/25/create-an-ubuntu-upnpdnla-server/](http://www.fscker.ca/rc/2010/10/25/create-an-ubuntu-upnpdnla-server/)

Following the guide, it seemed to be working. I was able to get to the WEBUI, but anytime I tried to change a share or do anything in fact, it would tell me that the page can't be found.

So I rebooted, and since then I've not been able to get uShare to work. suing service ushare start just says that the service has started, but it's not working at all, I'm assuming that it's crashing somehow.

I tried ushare -x but it complains that eth0 is down. It isn't, everything else is using it fine.

This is really starting to get on my nerves tbh, all I want to do is share my media with my devices. Why is that so hard to achieve?!

I'd very much appreciate your help with this.

EDIT:

After running aclocal, I manage to move further, but am now getting stuck here:


Use the link below. Seems like your dependencies are missing. 

This link explains pretty simply how to get it up and running on 10.04, and the differences are probably minor (if non-existant) for installing FUPPES 0.660 on your server. I'm running it myself, and did pretty much everything the guide says (although I didn't *use* this guide). 

[Install Fuppes]("http://matthewm.boedicker.org/doc/installing-fuppes-on-ubuntu-10-04-lucid-lynx.html")

[Fuppes Wiki]("http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Compiling_on_Ubuntu_Linux")

---

### Post by Largoh on 2011-10-21
Thanks for those link.
I'd tried several different guides on the net, but the svn part of the one you posted worked.

I now have fuppes running and it runs at startup! Thanks very much!

---

