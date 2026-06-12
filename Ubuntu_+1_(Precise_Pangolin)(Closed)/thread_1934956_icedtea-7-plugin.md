---
title: "icedtea-7-plugin"
date: 2012-03-03
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by zika on 2012-03-03
```
:~$ sudo aptitude upgrade
Resolving dependencies...                
The following partially installed packages will be configured:
  icedtea-7-plugin 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
Setting up icedtea-7-plugin (1.2~pre3-1ubuntu1) ...
/var/lib/dpkg/info/icedtea-7-plugin:amd64.postinst: 46: /var/lib/dpkg/info/icedtea-7-plugin:amd64.postinst: Syntax error: Unterminated quoted string
dpkg: error processing icedtea-7-plugin (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 icedtea-7-plugin
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up icedtea-7-plugin (1.2~pre3-1ubuntu1) ...
/var/lib/dpkg/info/icedtea-7-plugin:amd64.postinst: 46: /var/lib/dpkg/info/icedtea-7-plugin:amd64.postinst: Syntax error: Unterminated quoted string
dpkg: error processing icedtea-7-plugin (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 icedtea-7-plugin
``````
:~$ cat /var/lib/dpkg/info/icedtea-7-plugin:amd64.postinst
#!/bin/sh -e

PATH=/sbin:/bin:/usr/sbin:/usr/bin

multiarch=x86_64-linux-gnu
priority=1060
browser_dirs="mozilla"
PLUGIN=IcedTeaPlugin.so
basedir=/usr/lib/jvm/java-7-openjdk-amd64
old_basedir=/usr/lib/jvm/java-7/openjdk
PLUGINPTH=$basedir/jre/lib/amd64/$PLUGIN
OLD_PLUGINPTH=$old_basedir/jre/lib/amd64/$PLUGIN

case "$1" in
    configure)
        for browser_dir in $browser_dirs; do
            if [ $browser_dir = xulrunner-addons ]; then
                browser=xulrunner-1.9
            else
                browser=$browser_dir
            fi

            if [ -n "$multiarch" ] && [ "$DPKG_MAINTSCRIPT_ARCH" != $(dpkg --print-architecture) ]; then
                priority=$(expr $priority - 1)
            fi

            if [ -n "$multiarch" ] && [ -n "$2" ]; then
                if [ -n $(update-alternatives --list $browser-javaplugin.so 2>/dev/null | grep ^$old_basedir/)" ]; then
                    update-alternatives --remove $browser-javaplugin.so $OLD_PLUGINPTH || true
                fi
            fi

            if [ -z "$(update-alternatives --list $browser-javaplugin.so 2>/dev/null | grep ^$basedir/)" ]; then
                update-alternatives --quiet --install \
                    /usr/lib/$browser_dir/plugins/libjavaplugin.so \
                    $browser-javaplugin.so \
                    $PLUGINPTH \
                    $priority
            fi
        done
esac



exit 0
``````
:~$ update-alternatives --list mozilla-javaplugin.so
/.../JDK/jre/lib/amd64/libnpjp2.so
/usr/lib/jvm/java-6-openjdk-amd64/jre/lib/amd64/IcedTeaPlugin.so
:~$ sudo update-alternatives --install /usr/lib/mozilla/plugins/libjavaplugin.so mozilla-javaplugin.so /usr/lib/jvm/java-7-openjdk-amd64/jre/lib/amd64/IcedTeaPlugin.so 1060
:~$ update-alternatives --list mozilla-javaplugin.so
/.../JDK/jre/lib/amd64/libnpjp2.so
/usr/lib/jvm/java-6-openjdk-amd64/jre/lib/amd64/IcedTeaPlugin.so
/usr/lib/jvm/java-7-openjdk-amd64/jre/lib/amd64/IcedTeaPlugin.so
:~$ update-alternatives --config mozilla-javaplugin.so
There are 3 choices for the alternative mozilla-javaplugin.so (providing /usr/lib/mozilla/plugins/libjavaplugin.so).

  Selection    Path                                                              Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/java-6-openjdk-amd64/jre/lib/amd64/IcedTeaPlugin.so   1061      auto mode
* 1            /.../JDK/jre/lib/amd64/libnpjp2.so                1         manual mode
  2            /usr/lib/jvm/java-6-openjdk-amd64/jre/lib/amd64/IcedTeaPlugin.so   1061      manual mode
  3            /usr/lib/jvm/java-7-openjdk-amd64/jre/lib/amd64/IcedTeaPlugin.so   1060      manual mode

Press enter to keep the current choice
[*], or type selection number:
```That did not help...
Not of any importance for me, just annoying... ;)

After all these Java's imposed (by force) on my PP install I feel like Java-collector... ;)

---

### Post by dino99 on 2012-03-03
as often, purged them all then reinstall

---

### Post by zika on 2012-03-03
> **dino99 said:**
> as often, purged them all then reinstall
As often, that did not help at all...
```
:~$ sudo aptitude purge icedtea-7-plugin
The following packages will be REMOVED:  
  icedtea-7-plugin{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
Need to get 0 B of archives. After unpacking 278 kB will be freed.
Do you want to continue? [Y/n/?] 
(Reading database ... 249208 files and directories currently installed.)
Removing icedtea-7-plugin ...
:~$ sudo aptitude install icedtea-7-plugin
The following NEW packages will be installed:
  icedtea-7-plugin 
0 packages upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 87.7 kB of archives. After unpacking 278 kB will be used.
Get: 1 http://us.archive.ubuntu.com/ubuntu/ precise/universe icedtea-7-plugin amd64 1.2~pre3-1ubuntu1 [87.7 kB]
Fetched 87.7 kB in 0s (286 kB/s)       
Selecting previously unselected package icedtea-7-plugin.
(Reading database ... 249205 files and directories currently installed.)
Unpacking icedtea-7-plugin (from .../icedtea-7-plugin_1.2~pre3-1ubuntu1_amd64.deb) ...
Setting up icedtea-7-plugin (1.2~pre3-1ubuntu1) ...
/var/lib/dpkg/info/icedtea-7-plugin:amd64.postinst: 46: /var/lib/dpkg/info/icedtea-7-plugin:amd64.postinst: Syntax error: Unterminated quoted string
dpkg: error processing icedtea-7-plugin (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 icedtea-7-plugin
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up icedtea-7-plugin (1.2~pre3-1ubuntu1) ...
/var/lib/dpkg/info/icedtea-7-plugin:amd64.postinst: 46: /var/lib/dpkg/info/icedtea-7-plugin:amd64.postinst: Syntax error: Unterminated quoted string
dpkg: error processing icedtea-7-plugin (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 icedtea-7-plugin
 :~$ 
```

---

### Post by dino99 on 2012-03-03
try:

sudo rm  /var/lib/dpkg/info/*

then update again

---

### Post by mc4man on 2012-03-03
I only guess at such stuff - maybe this line in the postinst
```
if [ -n [COLOR="Red"]"[/COLOR]$(update-alternatives --list $browser-javaplugin.so 2>/dev/null | grep ^$old_basedir/)" ]; then
```

So extracting the .deb, adding red to the postinst, then repacking (dpkg -b /path/to/extracted/folder

> sudo dpkg -i  icedtea-7-plugin_1.2~pre3-1ubuntu1_i386.deb
Selecting previously unselected package icedtea-7-plugin.
(Reading database ... 130333 files and directories currently installed.)
Unpacking icedtea-7-plugin (from icedtea-7-plugin_1.2~pre3-1ubuntu1_i386.deb) ...
Setting up icedtea-7-plugin (1.2~pre3-1ubuntu1) ...

---

### Post by zika on 2012-03-03
> **mc4man said:**
> I only guess at such stuff - maybe this line in the postinst
```
if [ -n [COLOR=Red]"[/COLOR]$(update-alternatives --list $browser-javaplugin.so 2>/dev/null | grep ^$old_basedir/)" ]; then
```So extracting the .deb, adding red to the postinst, then repacking (dpkg -b /path/to/extracted/folderGreat catch! It worked.

```
sudo nano /var/lib/dpkg/info/icedtea-7-plugin:amd64.postinst
(correct what mc4man suggested)
sudo aptitude upgrade
```
Thank You!

---

### Post by waspinator on 2012-03-04
> **zika said:**
> Great catch! It worked.

```
sudo nano /var/lib/dpkg/info/icedtea-7-plugin:amd64.postinst
(correct what mc4man suggested)
sudo aptitude upgrade
```
Thank You!

I have this problem too, but I don't understand what mc4man suggested. help?

---

### Post by Irihapeti on 2012-03-04
> **waspinator said:**
> I have this problem too, but I don't understand what mc4man suggested. help?

A new version has been released with the problem corrected. Just upgrade (assuming your mirror is up to date).

---

### Post by waspinator on 2012-03-05
> **Irihapeti said:**
> A new version has been released with the problem corrected. Just upgrade (assuming your mirror is up to date).

You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 icedtea-7-plugin : Depends: icedtea-netx (= 1.2~pre3-1ubuntu1) but 1.2~pre3-1ubuntu2 is installed
E: Unmet dependencies. Try using -f.

aftrer trying using -f

Errors were encountered while processing:
 icedtea-7-plugin
E: Sub-process /usr/bin/dpkg returned an error code (1)

EDIT:
removed it in synaptic, and upgrade works now

---

