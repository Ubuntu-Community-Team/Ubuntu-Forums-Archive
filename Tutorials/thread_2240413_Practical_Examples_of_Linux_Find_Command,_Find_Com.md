---
title: "Practical Examples of Linux Find Command, Find Command Examples for Ubuntu"
date: 2014-08-19
forum: Tutorials
---

### Post by rousseau09 on 2014-08-19
In Unix-like and some other operating systems, find is a command-line utility (Find Command Examples here) can be used to search through one or more directory trees of a file system, locates files based on some user-specified criteria and applies a user-specified action on each matched file. The possible search criteria include a pattern to match against the file name or a time range to match against the modification time or access time of the file. By default, find returns a list of all files below the current working directory.

The related locate programs use a database of indexed files obtained through find (updated at regular intervals, typically by cron job) to provide a faster method of searching the entire filesystem for files by name.


Link to complete post:

[Practical Examples of Linux Find Command, Find Command Examples for Ubuntu]("http://www.blackmoreops.com/2014/08/18/practical-examples-linux-find-command/")


Following is the table of contents for the post: 

```
**Table of Contents:**

Find Command for Finding Files with Names

    1. Find and list all files in current and sub directories
    2. Search and list specific directory or path
    3. Find Files Using Name and Ignoring Case
    4. Find Directories Using Name
    5. Use find to limit depth of directory search
    6. Find all PHP Files in Directory

Find Files Based on their Permissions

    7. Find Files With 777 Permissions
    8. Find Files Without 777 Permissions
    9. Find SGID Files with 644 Permissions
    10. Find Sticky Bit Files with 551 Permissions
    11. Find SUID Files
    12. Find SGID Files
    13. Find Read Only Files
    14. Find Executable Files
    15. Find Files with 777 permissions and change permissions to 644
    16. Find Directories with 777 permissions and permissions to 755
    17. Find and remove single File
    18. Find and remove Multiple File
    19. Find all Empty Files and directories
    20. File all Hidden Files

Search Files Based On Owners and Groups

    21. Find Single File Based on User
    22. Find all Files Based on User
    23. Find all Files Based on Group
    24. Find Particular Files of User

Find Files and Directories Based on Date and Time

    25. Find Last 50 Days Modified or Accessed Files
    26. Find Last 50-100 Days Modified Files
    27. Find Changed Files in Last 1 Hour
    28. Find Modified or Accessed Files in Last 1 Hour

Find Files and Directories Based on Size

    29. Find 15MB Files
    30. Find Size between 50MB – 100MB
    31. Find and Delete 100MB Files
    32. Find Specific Files and Delete

Conclusion:
```

In Unix-like and some other operating systems, find is a command-line utility (Find Command Examples here) can be used to search through one or more directory trees of a file system, locates files based on some user-specified criteria and applies a user-specified action on each matched file. The possible search criteria include a pattern to match against the file name or a time range to match against the modification time or access time of the file. By default, find returns a list of all files below the current working directory.

The related locate programs use a database of indexed files obtained through find (updated at regular intervals, typically by cron job) to provide a faster method of searching the entire filesystem for files by name.


Find Command for Finding Files with Names

 
1. Find and list all files in current and sub directories

Find and list all files on your current directory.

```
root@kali:~# find | head
.
./dir777
./.lock
./.ICEauthority
./FindCommandExamples.txt
./.mozilla
./.mozilla/extensions
./.mozilla/firefox
./.mozilla/firefox/9n757kmh.default-1407199852988
./.mozilla/firefox/9n757kmh.default-1407199852988/urlclassifierkey3.txt
root@kali:~#
```

 

You can also use it to find a specific file, for example find all the files whose name is FindCommandExamples.txt in a current working directory.

 
```

root@kali:~# find /root -name FindCommandExamples.txt
/root/FindCommandExamples.txt
root@kali:~#
```

 
2. Search and list specific directory or path

Find all the files under /tmp directory. It lists out all files by default.
```

root@kali:~# find /tmp  | head
/tmp
/tmp/.ICE-unix
/tmp/.ICE-unix/2899
/tmp/btdADJLclI
/tmp/.X0-lock
/tmp/pulse-Izwfn0i4P8La
/tmp/pulse-Izwfn0i4P8La/dbus-socket
/tmp/pulse-Izwfn0i4P8La/native
/tmp/pulse-Izwfn0i4P8La/pid
/tmp/mutt-kali-0-23824-9061537041904758789
root@kali:~#
```


3. Find Files Using Name and Ignoring Case

Find all the files whose name is FindCommandExamples.txt and contains both capital and small letters in / directory.

```
root@kali:~# find  / -iname findcommandexamples.txt
/root/FindCommandExamples.txt
root@kali:~#
```


4. Find Directories Using Name

Find all directories whose name is root in / directory.

```
root@kali:~# find / -type d -name root
/opt/metasploit/apps/pro/ui/vendor/bundle/ruby/1.9.1/gems/fssm-0.2.10/spec/root
/root
/usr/share/nvidia-visual-profiler/plugins/org.eclipse.ui.intro.universal_3.2.500.v20110510/themes/purpleMesh/graphics/root
/usr/src/linux-headers-3.14-kali1-amd64/include/config/usb/ehci/root
/run/udev/links/root
root@kali:~#
```


5. Use find to limit depth of directory search

Find command searches all files and folders all the way upto the last depth. This maybe time consuming and resource hungry when you're searching a big directory or if you have too many small files broken into multiple directory. It is possible to to limit find command to search only upto 1 levels down (or 2 or 3 or anything you'd wish for) of subdirectories. This can be done using the maxdepth option.

```
root@kali:~# find /etc -maxdepth 1 -name "*.conf" | tail
/etc/miredo.conf
/etc/uniconf.conf
/etc/pam.conf
/etc/mke2fs.conf
/etc/arpwatch.conf
/etc/chkrootkit.conf
/etc/ca-certificates.conf
/etc/insserv.conf
/etc/colord.conf
/etc/gai.conf
root@kali:~#
```

Now the above example show all .conf files in /etc folder.

If you want to go down 1 depth below use 2 instead of 1.
```

root@kali:~# find /etc -maxdepth 2 -name "*.conf" | tail
/etc/arpwatch.conf
/etc/chkrootkit.conf
/etc/ca-certificates.conf
/etc/insserv.conf
/etc/colord.conf
/etc/gai.conf
/etc/cisco-torch/torch.conf
/etc/nvidia/nvidia-blacklists-nouveau.conf
/etc/nvidia/nvidia-modprobe.conf
/etc/gdm3/daemon.conf
root@kali:~# 
```

The second example uses maxdepth of 2, which means it will not go lower than 2 level deep, either only in the current directory.

You can also use  mindepth which works the other way around.

 
6. Find all PHP Files in Directory

Find all php files in a directory.

```
root@kali:~# find . -type f -name "*.php"
./blackmoreops.php
root@kali:~#
```


Find Files Based on their Permissions

 
7. Find Files With 777 Permissions

Find all the files whose permissions are 777.

```
root@kali:~# find . -type f -perm 0777 -print
./0777.txt
root@kali:~#
```

 
8. Find Files Without 777 Permissions

Find all the files without permission 777.

```
root@kali:~# find . -type f ! -perm 777 | head
./.lock
./.ICEauthority
./FindCommandExamples.txt
./.mozilla/firefox/9n757kmh.default-1407199852988/urlclassifierkey3.txt
./.mozilla/firefox/9n757kmh.default-1407199852988/cookies.sqlite
./.mozilla/firefox/9n757kmh.default-1407199852988/localstore.rdf.original
./.mozilla/firefox/9n757kmh.default-1407199852988/permissions.sqlite
./.mozilla/firefox/9n757kmh.default-1407199852988/extensions.ini
./.mozilla/firefox/9n757kmh.default-1407199852988/extensions.sqlite
./.mozilla/firefox/9n757kmh.default-1407199852988/bookmarkbackups/bookmarks-2014-08-07.json
root@kali:~#
```

 
9. Find SGID Files with 644 Permissions

Find all the SGID bit files whose permissions set to 644.

```
root@kali:~# find . -perm 0644 | head
./.lock
./FindCommandExamples.txt
./.mozilla/firefox/9n757kmh.default-1407199852988/urlclassifierkey3.txt
./.mozilla/firefox/9n757kmh.default-1407199852988/cookies.sqlite
./.mozilla/firefox/9n757kmh.default-1407199852988/localstore.rdf.original
./.mozilla/firefox/9n757kmh.default-1407199852988/permissions.sqlite
./.mozilla/firefox/9n757kmh.default-1407199852988/extensions.ini
./.mozilla/firefox/9n757kmh.default-1407199852988/extensions.sqlite
./.mozilla/firefox/9n757kmh.default-1407199852988/places.sqlite-wal
./.mozilla/firefox/9n757kmh.default-1407199852988/indexedDB/chrome/idb/2588645841ssegtnti.sqlite
root@kali:~#
```

 
10. Find Sticky Bit Files with 551 Permissions

Find all the Sticky Bit set files whose permission are 551.

```
root@kali:~# find / -perm 0551
```

 
11. Find SUID Files

Find all SUID set files.

```
root@kali:/bin# find . -perm /u=s | head
./mount
./su
./ping
./umount
./ping6
./fusermount
root@kali:/bin#
```

 
12. Find SGID Files

Find all SGID set files.

```
root@kali:/var# find . -perm /g+s | head
./lib/tor
./lib/libuuid
./cache/man
./cache/man/ja
./cache/man/ja/cat5
./cache/man/ja/cat8
./cache/man/ja/cat1
./cache/man/cat5
./cache/man/pa
./cache/man/pa/cat5
root@kali:/var#
```

 
13. Find Read Only Files

Find all Read Only files.

```
root@kali:~# find / -perm /u=r | head
/
/etc
/etc/logcheck
/etc/logcheck/ignore.d.workstation
/etc/logcheck/ignore.d.workstation/mysql-server-5_5
/etc/logcheck/ignore.d.workstation/lirc
/etc/logcheck/ignore.d.server
/etc/logcheck/ignore.d.server/mysql-server-5_5
/etc/logcheck/ignore.d.server/iodined
/etc/logcheck/ignore.d.server/lirc
```

 
14. Find Executable Files

Find all Executable files.

```
root@kali:/bin# find . -perm /a=x | head
.
./tailf
./ntfswipe
./dir
./dd
./true
./mountpoint
./ypdomainname
./zmore
./stty
root@kali:/bin#
```

 
15. Find Files with 777 permissions and change permissions to 644

Find all 777 permission files and use chmod command to set permissions to 644.

```
root@kali:~# find / -type f -perm 0777 -print -exec chmod 644 {} \;
/root/blackmoreops.php
root@kali:~#

```
 
16. Find Directories with 777 permissions and permissions to 755

Find all 777 permission directories and use chmod command to set permissions to 755.

```
root@kali:~# find . -type d -perm 777 -print -exec chmod 755 {} \;
./dir777
root@kali:~# 
```

 
17. Find and remove single File

To find a single file called FindCommandExamples.txt and remove it.

```
root@kali:~# find . -type f -name "FindCommandExamples.txt" -exec rm -f {} \;
```

 
18. Find and remove Multiple File

To find and remove multiple files such as .mp3 or .txt, then use.

```
root@kali:~# find . -type f -name "*.txt" -exec rm -f {} \;
```

OR

```
root@kali:~# find . -type f -name "*.mp3" -exec rm -f {} \;
```

 
19. Find all Empty Files and directories

To file all empty files under certain path.

```
root@kali:~# find /tmp -type f -empty
/tmp/mutt-kali-0-23824-9061537041904758789
/tmp/mutt-kali-0-23410-1906773975188079418
/tmp/qtsingleapp-flareg-bcdb-0-lockfile
root@kali:~# 
```



To file all empty directories under certain path.

```
root@kali:~# find /tmp -type d -empty
/tmp/pulse-PKdhtXMmr18n
/tmp/tracker-root
/tmp/orbit-root
/tmp/plugtmp
root@kali:~# 

```
 
20. File all Hidden Files

To find all hidden files, use below command.

```
root@kali:~# find /tmp -type f -name ".*"
/tmp/.X0-lock
root@kali:~# 
```

 
Search Files Based On Owners and Groups

 
21. Find Single File Based on User

To find all or single file called FindCommandExamples.txt under / root directory of owner root.

```
root@kali:~# find / -user root -name FindCommandExamples.txt
/root/FindCommandExamples.txt
root@kali:~# 

```
 
22. Find all Files Based on User

To find all files that belongs to user root under / directory.

```
root@kali:~# find / -user root | head
/
/etc
/etc/logcheck
/etc/logcheck/ignore.d.workstation
/etc/logcheck/ignore.d.workstation/mysql-server-5_5
/etc/logcheck/ignore.d.workstation/lirc
/etc/logcheck/ignore.d.server
/etc/logcheck/ignore.d.server/mysql-server-5_5
/etc/logcheck/ignore.d.server/iodined
/etc/logcheck/ignore.d.server/lirc
root@kali:~# 
```

 
23. Find all Files Based on Group

To find all files that belongs to group root under / directory.

```
root@kali:~# find / -group root | head
/
/etc
/etc/logcheck
/etc/logcheck/ignore.d.workstation
/etc/logcheck/ignore.d.workstation/mysql-server-5_5
/etc/logcheck/ignore.d.workstation/lirc
/etc/logcheck/ignore.d.server
/etc/logcheck/ignore.d.server/mysql-server-5_5
/etc/logcheck/ignore.d.server/iodined
/etc/logcheck/ignore.d.server/lirc
root@kali:~#
```


24. Find Particular Files of User

To find all .txt files of user root under / directory.
```

root@kali:~# find / -user root -iname "*.txt" | head
/etc/X11/rgb.txt
/etc/bluemaho/handbook.txt
/etc/unicornscan/ports.txt
/etc/unicornscan/oui.txt
/etc/siege/urls.txt
/boot/extlinux/boot.txt
/var/lib/inetsim/data/tftp/tftproot/sample.txt
/var/lib/inetsim/data/quotd/quotd.txt
/var/lib/inetsim/data/ftp/ftproot/sample.txt
/var/lib/inetsim/data/http/fakefiles/sample.txt
root@kali:~#
```

 
Find Files and Directories Based on Date and Time

 
25. Find Last 50 Days Modified or Accessed Files

To find all the files which are modified 50 days back.

```
root@kali:~# find / -mtime 50 
/opt/metasploit/apps/pro/ui/scripts/ctl.rb
/opt/metasploit/apps/pro/ui/scripts/worker_ctl.rb
```

To find all the files which are accessed 50 days back.

```
root@kali:~# find / -atime 50
```

 
26. Find Last 50-100 Days Modified Files

To find all the files which are modified more than 50 days back and less than 100 days.
```

root@kali:~# find / -mtime +50 -mtime -100 | head
/etc/chatscripts/provider
/etc/profile
/etc/ssh/sshd_config
/etc/host.conf
/etc/console-setup/Uni2-Fixed16.psf.gz
/etc/default/ntfs-3g
/etc/default/saned
/etc/default/atftpd
/etc/default/exim4
/etc/network/if-up.d/wpasupplicant
root@kali:~# 

```
 
27. Find Changed Files in Last 1 Hour

To find all the files which are changed in last 1 hour.
```

root@kali:~# find / -cmin -60 | head
/proc/asound
/proc/asound/NVidia
/proc/asound/MID
/proc/asound/card1
/proc/asound/card1/id
/proc/asound/card1/codec#0
/proc/asound/card1/codec#1
/proc/asound/card1/codec#2
/proc/asound/card1/codec#3
/proc/asound/card1/eld#0.0
root@kali:~# 
```


28. Find Modified or Accessed Files in Last 1 Hour

To find all the files which are modified in last 1 hour.

root@kali:~# find / -mmin -60

To find all the files which are accessed in last 1 hour.

```
root@kali:~# find / -amin -60
```

 
Find Files and Directories Based on Size

 
29. Find 15MB Files

To find all 15MB files, use.
```

root@kali:~# find / -size 15M
/var/lib/dkms/nvidia-current/331.67/3.14-kali1-amd64/x86_64/module/nvidia-current.ko
/opt/jdk1.7.0_60/lib/tools.jar
/opt/jdk1.7.0_60/jre/lib/amd64/server/libjvm.so
/opt/jdk1.7.0_60/jre/lib/jfxrt.jar
/root/Work/conky-manager/default-themes-extra-1.cmtp.7z
/usr/lib/python2.7/config/libpython2.7-pic.a
/usr/lib/python2.7/config/libpython2.7.a
/usr/lib/jvm/java-7-openjdk-amd64/jre/lib/amd64/server/libjvm.so
/usr/bin/multiforcer
/usr/bin/mono-sgen
/usr/share/zaproxy/lib/jfxrt.jar
root@kali:~# 

```
 
30. Find Size between 50MB – 100MB

To find all the files which are greater than 50MB and less than 100MB.

```
root@kali:~# find / -size +50M -size -100M
/var/cache/apt/archives/nvidia-visual-profiler_5.0.35-8~bpo70+1_amd64.deb
/var/cache/apt/archives/nvidia-cuda-doc_5.0.35-8~bpo70+1_all.deb
/var/cache/apt/archives/metasploit-framework_4.9.3-2014072301-1kali0_amd64.deb
/opt/jdk1.7.0_60/jre/lib/rt.jar
/opt/Teeth/units/CVE-2013-07-11.csv
/root/Downloads/cudaHashcat-1.21.7z
/usr/lib/chromium/chromium
/usr/lib/x86_64-linux-gnu/libcublas.so.5.0.35
/usr/lib/x86_64-linux-gnu/libwireshark.so.3.1.1
/usr/lib/x86_64-linux-gnu/libnpp.so.5.0.35
/usr/share/w3af/w3af/plugins/crawl/phishtank/index.xml
/usr/share/wordlists/rockyou.txt.gz
/run/shm/pulse-shm-1617702718
/run/shm/pulse-shm-543938446
/run/shm/pulse-shm-2061196650
/run/shm/pulse-shm-519747678
/run/shm/pulse-shm-5957035
/run/shm/pulse-shm-2279876097
root@kali:~# 
```


31. Find and Delete 100MB Files

To find all 100MB files and delete them using one single command.

```
root@kali:~# find / -size +100M -exec rm -rf {} \;
```

 
32. Find Specific Files and Delete

Find all .mp3 files with more than 10MB and delete them using one single command.

```
root@kali:~# find / -type f -name *.mp3 -size +10M -exec rm {} \;
```

 
Conclusion:

This was a small guide on how to use Linux Find Command. I gathered these info as much I could and found them useful. Hope this benefits you too.


Link to original post:

[Practical Examples of Linux Find Command, Find Command Examples for Ubuntu]("http://www.blackmoreops.com/2014/08/18/practical-examples-linux-find-command/")

I hope you will find it useful.

---

