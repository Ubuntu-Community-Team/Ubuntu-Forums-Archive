---
title: "iFolder server &amp; problem with Simias server"
date: 2011-01-30
forum: Server Platforms
---

### Post by mr.interested on 2011-01-30
Hello,

I'm using this guide ([https://help.ubuntu.com/community/iFolderInstall](https://help.ubuntu.com/community/iFolderInstall)) to install IFolder Server on Ubuntu 10.10 on VPS via ssh. I have to problems when installing Simias server. First, I successfully ran through compiling and installing Simias server. When I executed the command:

> dpkg-reconfigure simias-serverI've got error that Simias server was not installed or corrupted. OK, I repeated the steps several times, with the very same error. Finally, I started everything from scratch, but now I have problems when executing the command that worked before:

> bzr-buildpackageThis is what happens:

> root@faeaa:/tmp/simias# bzr-buildpackage
Building using working tree
Running in merge mode
Purging the build dir: /tmp/build-area/simias-1.8.3.10200.0
Looking for a way to retrieve the upstream tarball
Upstream tarball already exists in build directory, using that
Building the package in /tmp/build-area/simias-1.8.3.10200.0, using debuild
 dpkg-buildpackage -rfakeroot -D -us -uc
dpkg-buildpackage: warning: using a gain-root-command while being root
dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): 
dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package simias
dpkg-buildpackage: source version 1.8.3.10200.0-9
dpkg-buildpackage: source changed by csights <csights@ifolder-debian-ubuntu-google-group>
 dpkg-source --before-build simias-1.8.3.10200.0
dpkg-buildpackage: host architecture amd64
dpkg-source: warning: patches have not been applied, applying them now (use --no-preparation to override)
dpkg-source: info: applying use_system_gsoap.patch
dpkg-source: info: applying use_wsdl_not_wsdl1.patch
dpkg-source: info: applying use_mono_webserver2.patch
dpkg-source: info: applying use_lib_as_libdir_on_amd64.patch
dpkg-source: info: applying use_libdir_for_executables.patch
dpkg-source: info: applying SimiasLib.dll.config-use-systemwide-FlaimWrapper.so.patch
dpkg-source: info: applying www-data_apache.patch
dpkg-source: info: applying mod_mono_path.patch
dpkg-source: info: applying mod_mono_SimiasServerSetup_cs.patch
dpkg-source: info: applying mod_mono_iFolderAdminSetup_cs.patch
dpkg-source: info: applying mod_mono_iFolderWebSetup_cs.patch
dpkg-source: info: applying convert_relative_path_to_webbindir_variable.patch
dpkg-source: info: applying ifdata.patch
dpkg-source: info: applying SimiasServerSetup_use_simiasconfdir_in_SetupDefaultConfigPath.patch
dpkg-source: info: applying use_webbindir_variable_configurein.patch
dpkg-source: info: applying separate_client_server_dirs.patch
dpkg-source: info: applying serverpaths_from_configure_v2.patch
dpkg-source: info: applying dont_download_deleted_nodes.patch
dpkg-source: info: applying remove_nodesFromServer.patch
dpkg-source: info: applying home_never_network_drive.patch
dpkg-source: info: applying DEBUG_log_default.patch
 fakeroot debian/rules clean
dh clean
   dh_testdir
Unknown option: with
dh_testdir: warning: ignored unknown options in DH_OPTIONS
   debian/rules override_dh_auto_clean
make[1]: Entering directory `/tmp/build-area/simias-1.8.3.10200.0'
[ ! -f Makefile ] || /usr/bin/make clean
find . -name Makefile.in | xargs rm -f
find . -name Makefile | xargs rm -f
find . -name .libs | xargs rm -fr
find . -name .deps | xargs rm -fr
find . -name *.resources | xargs rm -f
find . -name *.dll -type f | xargs rm -f
rm -rf install-sh INSTALL missing aclocal.m4 configure \
           ltmain.sh m4 config.sub config.guess depcomp compile \
           config.cache libtool config.log config.status \
           src/webservices/iFolderAdminLocalProxy.cs \
           src/webservices/iFolderWebLocalProxy.cs \
           src/utils/usercmd/simias-create-user \
           src/utils/usercmd/simias-delete-user \
           src/utils/usercmd/simias-user \
           src/webaccess/Log4Net.config \
           src/server/Simias.config \
           src/server/setup/novell-ifolder3.conf \
           src/setup/apache/default/ifolder_admin.conf \
           src/setup/apache/default/ifolder_webaccess.conf \
           src/setup/apache/default/simias_server.conf \
           src/setup/apache/example.com/ifolder_admin.conf \
           src/setup/apache/example.com/ifolder_webaccess.conf \
           src/setup/apache/example.com/simias_server.conf \
           src/setup/apache/ifolder_apache.conf \
           src/core/SimiasClient/SimiasSetup.cs \
           src/core/SimiasClient/simias-client-c.pc \
           src/core/SimiasClient/simias-client.pc \
           src/core/libsimias/libsimias.h \
           src/admin/Log4Net.config \
           src/admin/iFolderAdminWebProxy.cs \
           src/client/SimiasDirectoryMapping \
           src/client/simias \
           src/core/Common/MyDns.cs \
           src/core/Common/Simias.config \
           src/core/Common/defaults.config \
           src/core/SimiasLib.dll/AssemblyInfo.cs \
           src/core/SimiasLib.dll/SimiasLib.dll.config \
           src/core/SimiasLib.dll/simias.pc \
               src/admin/AssemblyInfo.cs \
               src/webservices/AssemblyInfo.cs \
               src/utils/usercmd/AssemblyInfo.cs \
               src/webaccess/AssemblyInfo.cs \
           duplicatesource/
make[1]: Leaving directory `/tmp/build-area/simias-1.8.3.10200.0'
   dh_clean
Unknown option: with
dh_clean: warning: ignored unknown options in DH_OPTIONS
    rm -f debian/libsimias0.substvars
    rm -f debian/libsimias0.*.debhelper
    rm -f debian/libsimias0.debhelper.log
    rm -rf debian/libsimias0/
    rm -f debian/libsimias-dev.substvars
    rm -f debian/libsimias-dev.*.debhelper
    rm -f debian/libsimias-dev.debhelper.log
    rm -rf debian/libsimias-dev/
    rm -f debian/simias-server.substvars
    rm -f debian/simias-server.*.debhelper
    rm -f debian/simias-server.debhelper.log
    rm -rf debian/simias-server/
    rm -f debian/simias-client.substvars
    rm -f debian/simias-client.*.debhelper
    rm -f debian/simias-client.debhelper.log
    rm -rf debian/simias-client/
    rm -f debian/ifolder3-server.substvars
    rm -f debian/ifolder3-server.*.debhelper
    rm -f debian/ifolder3-server.debhelper.log
    rm -rf debian/ifolder3-server/
    rm -f debian/files
    find .  \( \( -type f -a \
            \( -name '#*#' -o -name '.*~' -o -name '*~' -o -name DEADJOE \
         -o -name '*.orig' -o -name '*.rej' -o -name '*.bak' \
         -o -name '.*.orig' -o -name .*.rej -o -name '.SUMS' \
         -o -name TAGS -o \( -path '*/.deps/*' -a -name '*.P' \) \
        \) -exec rm -f {} \; \) -o \
        \( -type d -a -name autom4te.cache -prune -exec rm -rf {} \; \) \)
    rm -f *-stamp
 dpkg-source -b simias-1.8.3.10200.0
dpkg-source: info: using source format `3.0 (quilt)'
dpkg-source: info: building simias using existing ./simias_1.8.3.10200.0.orig.tar.gz
dpkg-source: info: building simias in simias_1.8.3.10200.0-9.debian.tar.gz
dpkg-source: info: building simias in simias_1.8.3.10200.0-9.dsc
 debian/rules build
dh build
   dh_testdir
Unknown option: with
dh_testdir: warning: ignored unknown options in DH_OPTIONS
   debian/rules override_dh_auto_configure
make[1]: Entering directory `/tmp/build-area/simias-1.8.3.10200.0'
rsync -r . duplicatesource
ERROR: out of memory in map_ptr [sender]
rsync error: error allocating core memory buffers (code 22) at util.c(117) [sender=3.0.7]
rsync: writefd_unbuffered failed to write 78 bytes to socket [generator]: Broken pipe (32)
make[1]: *** [override_dh_auto_configure] Error 22
make[1]: Leaving directory `/tmp/build-area/simias-1.8.3.10200.0'
make: *** [build] Error 2
dpkg-buildpackage: error: debian/rules build gave error exit status 2
debuild: fatal error at line 1337:
dpkg-buildpackage -rfakeroot -D -us -uc failed
bzr: ERROR: The build failed.
Any ideas how to fix this? Many thanks.

Best

---

### Post by druhboruch on 2011-01-30
You may consider installing from ppa.
[https://launchpad.net/~marceloshima/+archive/ifolder](https://launchpad.net/~marceloshima/+archive/ifolder)
It works great with lucid and maverick.

---

### Post by mr.interested on 2011-01-30
> **druhboruch said:**
> You may consider installing from ppa.
[https://launchpad.net/~marceloshima/+archive/ifolder]("https://launchpad.net/%7Emarceloshima/+archive/ifolder")
It works great with lucid and maverick.

Thanks druhboruch. But how did you add this to ppa?

I've added the following lines
> deb [http://ppa.launchpad.net/marceloshima/ifolder/ubuntu](http://ppa.launchpad.net/marceloshima/ifolder/ubuntu) maverick main
deb-src [http://ppa.launchpad.net/marceloshima/ifolder/ubuntu](http://ppa.launchpad.net/marceloshima/ifolder/ubuntu) maverick main
using
> sudo vi /etc/apt/sources.list
but then after
> sudo apt-get updateI'm getting the following errors:
> W: Failed to fetch [http://ppa.launchpad.net/marceloshima/ifolder/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/marceloshima/ifolder/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
W: Failed to fetch [http://ppa.launchpad.net/marceloshima/ifolder/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/marceloshima/ifolder/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  404  Not Found

---

### Post by Thirtysixway on 2011-01-30
Doesn't look like maverick is on there. Try changing your source to lucid and see if it works.

---

### Post by druhboruch on 2011-01-30
You may add repo by apt-add-repository command. It will also install the key for you.

In this case you will have to change your sources to lucid afterwards as Thirtysixway suggested.

This ppa works great with maverick.
If you install on maverick, you may install apache first and then stop it before installation of ifolder.
On lucid installation is flawless.

---

### Post by mr.interested on 2011-02-04
Many thanks for your replies. OK, so by issuing the command

```
vi /etc/apt/sources.list
```

I add the following lines

```
deb http://ppa.launchpad.net/marceloshima/ifolder/ubuntu lucid main
deb-src http://ppa.launchpad.net/marceloshima/ifolder/ubuntu lucid main 
```

and then update repository:

```
sudo apt-get update
...
W: GPG error: http://ppa.launchpad.net lucid Release: The following  signatures couldn't be verified because the public key is not available:  NO_PUBKEY ED649F97DE6BFD99
```

I update the key by issuing the following command:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys ED649F97DE6BFD99
```

and then again I update the depository:

```
sudo apt-get update
...
Ign http://ppa.launchpad.net/marceloshima/ifolder/ubuntu/ lucid/main Translation-en
Ign http://ppa.launchpad.net/marceloshima/ifolder/ubuntu/ lucid/main Translation-en_IE

```

Looks fine, but then when I try to install iFolder, I get the following error:

```

sudo apt-get install ifolder
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ifolder
```

---

### Post by mr.interested on 2011-02-04
OK, great. The following command should be:

```
sudo apt-get install ifolder[COLOR=Red]3-enterprise[/COLOR]
```I've missed "3-enterprise" in the name of ifolder. Will see how the installation goes.

---

### Post by mr.interested on 2011-02-04
This is rather strange. During the installation, it stops on restarting Apache:

```

...
Setting up mono-xsp-base (2.6.5-2) ...
Setting up mono-xsp2-base (2.6.5-2) ...
Setting up mono-apache-server2 (2.6.5-2) ...
 * Reloading web server config apache2                                   [ OK ] 
 * Restarting web server apache2                                                 
... waiting                                                             [ OK ]

```I've left this for more than 20 minutes and nothing happens. However, there are still four running processes when I check them on my admin panel (Webmin):
```

15768     root     22:20     apt-get install ifolder3-enterprise
21578     root     22:22     /usr/bin/dpkg --status-fd 19 --configure x11-common libpixman-1-0 libxcb-render0 ...
22292     root     22:22     /usr/bin/perl -w /usr/share/debconf/frontend /var/lib/dpkg/info/mono-apache-serv ...
22299     root     22:22     [mono-apache-ser] <defunct>
```I know that there's a lot to install, but is it normal that it takes so long?

---

### Post by druhboruch on 2011-02-04
As I wrote before, if you install on maverick just stop apache2 before installation.

---

### Post by mr.interested on 2011-02-04
> **druhboruch said:**
> As I wrote before, if you install on maverick just stop apache2 before installation.

Thank you, I've overlooked this. OK, so I've installed this successfully, however, I can't access the admin page. Do I have to configure something manually trough ssl before I run website? This site ([https://help.ubuntu.com/community/iFolderInstall](https://help.ubuntu.com/community/iFolderInstall)) says at the very bottom:

> iFolder is configured through [http://yourserver/admin](http://yourserver/admin) .  Add at least one user, then connect using iFolderClient. However, the page doesn't exist. I've tried using domain and IP address. None of them works.

**EDIT:** The installation ended on the following:

```
Enabling module mod_mono.
Run '/etc/init.d/apache2 restart' to activate new configuration!
Setting up ifolder3-enterprise (3.8.0.9328.1-0ubuntu1~ppa14~lucid1) ...
Restart the apache server '/etc/init.d/apache2 restart'
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

However, Simias server doesn't seem to be installed there. When I issue the following command:

```
dpkg --get-selections
```

it doesn't appear on the list. So obviously when I want to reconfigure it, I get the following message:

```
dpkg-reconfigure simias-server
Package `simias-server' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: simias-server is not installed
```

I've also configured Apache as the above-mentioned site mentions. I've issued the following commands:

```
sudo make-ssl-cert generate-default-snakeoil
sudo a2enmod ssl
sudo a2enmod rewrite
```

and added the following to */etc/apache2/sites-available/default* at its top:```
<VirtualHost _default_:443>
        SSLEngine on

        SSLOptions +StrictRequire

        SSLCertificateFile /etc/ssl/certs/ssl-cert-snakeoil.pem
        SSLCertificateKeyFile /etc/ssl/private/ssl-cert-snakeoil.key
</VirtualHost>
```Then I made sure that mod_mono is enabled, and restarted Apache. No results. What am I doing wrong?

---

### Post by druhboruch on 2011-02-04
You will find all the post-installation instructions in /usr/share/doc/ 
Good luck

---

### Post by mr.interested on 2011-02-04
> **druhboruch said:**
> You will find all the post-installation instructions in /usr/share/doc/ 
Good luck

Great! Many thanks for your help. Everything now works :)

---

### Post by mr.interested on 2011-02-05
The very last question: how can I change admin's password?

In the file /usr/share/doc/ifolder3-enterprise/README.Debian it states:

```
$ simias-user modify --url http://localhost --admin-name admin --admin-password simias --user admin --password <NEWPASSWORD>
```

And here ([http://wiki.inisec.com/index.php/Ifolder-ola#Admin_User](http://wiki.inisec.com/index.php/Ifolder-ola#Admin_User)), which is referred to in the above file, it states:

```
mono /usr/lib/simias/bin/UserCmd.exe modify --url [http://localhost]("http://localhost/") --admin-name admin --admin-password simias --user admin --password <NEWPASSWORD>

```

I've tried both commands and I get the following errors:

```
-bash: syntax error near unexpected token `newline'
```

Is there any other way to change the password?

---

### Post by druhboruch on 2011-02-05
The method from /usr/share/doc/ worked for me.

---

### Post by mr.interested on 2011-02-05
> **druhboruch said:**
> The method from /usr/share/doc/ worked for me.

It worked now. I had to delete brackets (stupid I'm). Thanks for your help.

---

### Post by Cybertrash on 2011-02-07
Hey, I've followed the methods in this thread, and I can access the [http://myserver.com/admin](http://myserver.com/admin) panel without problem, however, I can *not* log in with the "admin/simias" usrname/pw combo, nor can I change the admin password using the "simias-user modify" command, it spits out a "Failed - Invalid admin credentials" error. What do I do?

---

### Post by emnu on 2011-02-15
> **Cybertrash said:**
> Hey, I've followed the methods in this thread, and I can access the [http://myserver.com/admin](http://myserver.com/admin) panel without problem, however, I can *not* log in with the "admin/simias" usrname/pw combo, nor can I change the admin password using the "simias-user modify" command, it spits out a "Failed - Invalid admin credentials" error. What do I do?

dafualt user/password is admin/admin. you can find the default configuration at  /var/lib/simias/Simias.config

---

### Post by gube on 2011-03-03
Everything seems to work fine using the 'ppa:marceloshima/ifolder' by executing 'apt-get install ifolder3-enterprise'

And i also did 'ln -sf /etc/ifolder-server/apache/ifolder_apache.conf /etc/apache2/conf.d/'
and 'a2ensite default-ssl' and '/etc/init.d/apache2 restart'.

But when I try to access the 'http://my_server_adress/admin/' I get this error:
[I][COLOR=Navy]Server Error in '/admin' Application

An exception was thrown by the type initializer for Novell.iFolderWeb.Admin.Global

Description: HTTP 500. Error processing request.

Stack Trace:

System.TypeInitializationException: An exception was thrown by the type initializer for Novell.iFolderWeb.Admin.Global
  at ASP.global_asax..ctor () [0x00000] 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 

Version information: Runtime: Mono 2.4.4; ASP.NET Version: 2.0.50727.1433[/COLOR][/I]

Any clues what this is all about?

Many thanx in advance
G

---

### Post by gube on 2011-03-03
> **gube said:**
> Everything seems to work fine using the 'ppa:marceloshima/ifolder' by executing 'apt-get install ifolder3-enterprise'

And i also did 'ln -sf /etc/ifolder-server/apache/ifolder_apache.conf /etc/apache2/conf.d/'
and 'a2ensite default-ssl' and '/etc/init.d/apache2 restart'.

But when I try to access the 'http://my_server_adress/admin/' I get this error:
[I][COLOR=Navy]Server Error in '/admin' Application

An exception was thrown by the type initializer for Novell.iFolderWeb.Admin.Global

Description: HTTP 500. Error processing request.

Stack Trace:

System.TypeInitializationException: An exception was thrown by the type initializer for Novell.iFolderWeb.Admin.Global
  at ASP.global_asax..ctor () [0x00000] 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 

Version information: Runtime: Mono 2.4.4; ASP.NET Version: 2.0.50727.1433[/COLOR][/I]

Any clues what this is all about?

Many thanx in advance
G

Problem Solved!

[COLOR=Navy]*apt-get install liblog4net1.2-cil*[/COLOR]

did the trick.

"Me very happy man" :D

/G

---

