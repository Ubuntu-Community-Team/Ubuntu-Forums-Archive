---
title: "No Clue how to use Proftpd"
date: 2005-08-27
forum: Server Platforms
---

### Post by Linux_Noobie on 2005-08-27
Well i have proftp installed because of Xampp (Google it) on my Linux (Ubuntu) Pc You can see the homepage here. [jman888.1.vg](http://jman888.1.vg) And it seems to work pretty well but i want to host a few of my freinds's Websites. But have no clue how to do Ftp. I searched google so much but cannot find out how to use Something to add new ftp accounts like i want a account to be like
> LilJon123
Pass : 0984556
And be able to accsess /opt/lampp/htdocs/host/liljon 
and all folders under it
How could i do that?

---

### Post by defkewl on 2005-08-28
Your FTP user is your Linux user account.
Create it with adduser command from the command line.

---

### Post by Linux_Noobie on 2005-08-28
[QUOTE=defkewl]Your FTP user is your Linux user account.
Create it with adduser command from the command line.[/QUOTE]
But my Problems are if i make a new account they have accsess to /opt/lampp/htdocs and everything under it i want to lock them into one folder. And is making new accounts the ONLY way to have more Ftp accounts  ](*,)

---

### Post by invalid on 2005-08-28
search for a package named "gproftpd" (it's not in synaptic).
I believe it is available in a .rpm format - which you can convert to a .deb

This is a graphical frontend made for proftpd that lets you control users and directories.

Cheers,
Cb

---

### Post by Linux_Noobie on 2005-08-30
[QUOTE=invalid]search for a package named "gproftpd" (it's not in synaptic).
I believe it is available in a .rpm format - which you can convert to a .deb

This is a graphical frontend made for proftpd that lets you control users and directories.

Cheers,
Cb[/QUOTE]
 I dont know how to install it. When i try to cd it and Do ./Autoconfigure or whatever in the terminal i get this.> checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for OS type... Linux (i686-pc-linux-gnu) found.
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for pkg-config... /usr/bin/pkg-config
checking for gtk+-2.0 >= 1.3.13... Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found

configure: error: Library requirements (gtk+-2.0 >= 1.3.13) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.

I need some help.

---

### Post by rmrf on 2005-08-31
To keep a certain user in a directory, and not let them go out of that directory, you need to chroot them.

[http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-Chroot.html](http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-Chroot.html)

When a user is chrooted, the directory that they are set to acts as the root directory, and they are not allowed to go above that.

Hope this helps.

---

### Post by invalid on 2005-08-31
If you downloaded the rpm like I suggested, let's do this:

First convert it to a deb file:
sudo alien -d package_name.rpm

Then let's install it:
sudo dpkg -i new_package_name.deb
(most times, when you convert it between types, the name of the file will change slightly - make sure you are using the right one)

Then is should be all set to go, unless you have some dependencies left (if so, just open synaptic and choose "repair broken packages")

I personally don't use this, so I can't comment on it's official operation, but should start with just:
gproftpd

Cheers,
Cb

---

