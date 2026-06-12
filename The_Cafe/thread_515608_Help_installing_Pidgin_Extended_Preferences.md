---
title: "Help installing Pidgin Extended Preferences"
date: 2007-08-02
forum: The Cafe
---

### Post by ajmedfor on 2007-08-02
I am very new to Linux, and am trying to install the extended preferences plugin for Pidgin. I got the tarball from [http://packages.ubuntu.com/gutsy/net/pidgin-extprefs](http://packages.ubuntu.com/gutsy/net/pidgin-extprefs), but couldn't figure out how to get a .deb package. I extracted the pidgin-extprefs-0.7 folder to my desktop, and tried to follow the instructions in the install file. When I type /.configre I get the error

> 
checking pkg-config is at least version 0.9.0... yes
checking for PURPLE... configure: error: Package requirements (purple >= 2.0.0) were not met:

No package 'purple' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PURPLE_CFLAGS
and PURPLE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


And when I try to type make afterwards I get 

> 
make: *** No targets specified and no makefile found.  Stop.


I think I installed Pidgin in the default directory, and have no idea where to check the PKG_CONFIG_PATH variable to see. Can anyone help?

---

### Post by cleefa on 2007-09-23
I had this problem when try to install Guifications and other plugins. 

I had installed Pidgin with ./configure --prefix=/opt option.

The following change when configuring the plugins worked for me: 

> PKG_CONFIG_PATH= /opt/lib/pkgconfig ./configure --prefix=/opt

The path will need to be changed to reflect where you installed purple -  and its pkgconfig dir.

Sorry if this doesn't help, I just know it worked for me. :-?

---

### Post by Polygon on 2007-09-23
you should just be able to install it from the repos, thats what that means when you find it in the packages.ubuntu.com site

---

### Post by bruce89 on 2007-09-23
pidgin-extprefs in Gutsy.

---

### Post by kevdog on 2007-09-24
Here is a tutorial:

[http://ubuntuforums.org/showthread.php?t=558197&highlight=pidgin](http://ubuntuforums.org/showthread.php?t=558197&highlight=pidgin)

---

