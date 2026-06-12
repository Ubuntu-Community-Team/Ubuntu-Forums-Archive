---
title: "devede install removes libavformat52 and plenty others"
date: 2010-01-10
forum: Ubuntu Studio
---

### Post by dannyboy79 on 2010-01-10
sudo aptitude install devede
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following NEW packages will be installed:
  devede imagemagick{a} libavcodec-extra-52{a} libavformat-extra-52{a} libavutil-extra-49{a} libdirac0c2a{a} libiso9660-5{a} libopenal1{a} 
  libopenjpeg2{a} libpostproc-extra-51{a} libsvga1{a} libswscale-extra-0{a} libvcdinfo0{a} mencoder{a} mplayer-nogui{a} vcdimager{a} 
The following packages will be REMOVED:
  libavcodec52{a} libavformat52{a} libavutil49{a} libpostproc51{a} libswscale0{a} 
0 packages upgraded, 16 newly installed, 5 to remove and 24 not upgraded.
Need to get 12.1MB of archives. After unpacking 16.2MB will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse libavutil-extra-49 4:0.5+svn20090706-2ubuntu3 [97.1kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe libdirac0c2a 1.0.2-0ubuntu1 [410kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe libopenjpeg2 1.3+dfsg-4 [79.3kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse libavcodec-extra-52 4:0.5+svn20090706-2ubuntu3 [4,004kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse libavformat-extra-52 4:0.5+svn20090706-2ubuntu3 [708kB]                                                   
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe libopenal1 1:1.8.466-2 [94.1kB]                                                                             
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse libpostproc-extra-51 4:0.5+svn20090706-2ubuntu3 [69.5kB]                                                  
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe libsvga1 1:1.4.3-27ubuntu1 [312kB]                                                                          
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse libswscale-extra-0 4:0.5+svn20090706-2ubuntu3 [172kB]                                                     
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse mplayer-nogui 2:1.0~rc3+svn20090426-1ubuntu10.1 [2,090kB]                                        
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse mencoder 2:1.0~rc3+svn20090426-1ubuntu10.1 [1,657kB]                                             
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe libiso9660-5 0.78.2+dfsg1-3 [112kB]                                                                        
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe libvcdinfo0 0.7.23-4ubuntu1 [129kB]                                                                        
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe vcdimager 0.7.23-4ubuntu1 [540kB]                                                                          
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main imagemagick 7:6.5.1.0-1.1ubuntu3 [95.6kB]                                                                      
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse devede 3.14.0-0ubuntu5 [1,555kB]                                                                         
Fetched 12.1MB in 19s (610kB/s)                                                                                                                             
dpkg: libpostproc51: dependency problems, but removing anyway as you requested:
 transcode depends on libpostproc51 (>= 3:0.svn20090303-1) | libpostproc-extra-51 (>= 3:0.svn20090303-1); however:
  Package libpostproc51 is to be removed.
  Package libpostproc-extra-51 is not installed.
 ffmpeg depends on libpostproc51 (>= 4:0.5+svn20090706) | libpostproc-extra-51 (>= 4:0.5+svn20090706); however:
  Package libpostproc51 is to be removed.
  Package libpostproc-extra-51 is not installed.
 ffmpeg depends on libpostproc51 (<< 4:0.5+svn20090706-99) | libpostproc-extra-51 (<< 4:0.5+svn20090706-99); however:
  Package libpostproc51 is to be removed.
  Package libpostproc-extra-51 is not installed.
 ffmpeg depends on libpostproc51 (>= 4:0.5+svn20090706) | libpostproc-extra-51 (>= 4:0.5+svn20090706); however:
  Package libpostproc51 is to be removed.
  Package libpostproc-extra-51 is not installed.
 ffmpeg depends on libpostproc51 (<< 4:0.5+svn20090706-99) | libpostproc-extra-51 (<< 4:0.5+svn20090706-99); however:
  Package libpostproc51 is to be removed.
  Package libpostproc-extra-51 is not installed.
(Reading database ... 158776 files and directories currently installed.)
Removing libpostproc51 ...
dpkg: libavutil49: dependency problems, but removing anyway as you requested:
 libavformat52 depends on libavutil49 (>= 4:0.5+svn20090706) | libavutil-extra-49 (>= 4:0.5+svn20090706); however:
  Package libavutil49 is to be removed.
  Package libavutil-extra-49 is not installed.
 libavformat52 depends on libavutil49 (<< 4:0.5+svn20090706-99) | libavutil-extra-49 (<< 4:0.5+svn20090706-99); however:
  Package libavutil49 is to be removed.
  Package libavutil-extra-49 is not installed.
 libavformat52 depends on libavutil49 (>= 4:0.5+svn20090706) | libavutil-extra-49 (>= 4:0.5+svn20090706); however:
  Package libavutil49 is to be removed.
  Package libavutil-extra-49 is not installed.
 libavformat52 depends on libavutil49 (<< 4:0.5+svn20090706-99) | libavutil-extra-49 (<< 4:0.5+svn20090706-99); however:
  Package libavutil49 is to be removed.
  Package libavutil-extra-49 is not installed.
 libavfilter0 depends on libavutil49 (>= 4:0.5+svn20090706) | libavutil-extra-49 (>= 4:0.5+svn20090706); however:
  Package libavutil49 is to be removed.
  Package libavutil-extra-49 is not installed.
 libavfilter0 depends on libavutil49 (<< 4:0.5+svn20090706-99) | libavutil-extra-49 (<< 4:0.5+svn20090706-99); however:
  Package libavutil49 is to be removed.
  Package libavutil-extra-49 is not installed.
 libavfilter0 depends on libavutil49 (>= 4:0.5+svn20090706) | libavutil-extra-49 (>= 4:0.5+svn20090706); however:
  Package libavutil49 is to be removed.
  Package libavutil-extra-49 is not installed.
 libavfilter0 depends on libavutil49 (<< 4:0.5+svn20090706-99) | libavutil-extra-49 (<< 4:0.5+svn20090706-99); however:
  Package libavutil49 is to be removed.
  Package libavutil-extra-49 is not installed.
 libavdevice52 depends on libavutil49 (>= 4:0.5+svn20090706) | libavutil-extra-49 (>= 4:0.5+svn20090706); however:
  Package libavutil49 is to be removed.
  Package libavutil-extra-49 is not installed.
 libavdevice52 depends on libavutil49 (<< 4:0.5+svn20090706-99) | libavutil-extra-49 (<< 4:0.5+svn20090706-99); however:
  Package libavutil49 is to be removed.
  Package libavutil-extra-49 is not installed.
 libavdevice52 depends on libavutil49 (>= 4:0.5+svn20090706) | libavutil-extra-49 (>= 4:0.5+svn20090706); however:
  Package libavutil49 is to be removed.
  Package libavutil-extra-49 is not installed.
 libavdevice52 depends on libavutil49 (<< 4:0.5+svn20090706-99) | libavutil-extra-49 (<< 4:0.5+svn20090706-99); however:
  Package libavutil49 is to be removed.
  Package libavutil-extra-49 is not installed.
 libswscale0 depends on libavutil49 (>= 4:0.5+svn20090706) | libavutil-extra-49 (>= 4:0.5+svn20090706); however:
  Package libavutil49 is to be removed.
  Package libavutil-extra-49 is not installed.
 libswscale0 depends on libavutil49 (<< 4:0.5+svn20090706-99) | libavutil-extra-49 (<< 4:0.5+svn20090706-99); however:
  Package libavutil49 is to be removed.
  Package libavutil-extra-49 is not installed.
 libswscale0 depends on libavutil49 (>= 4:0.5+svn20090706) | libavutil-extra-49 (>= 4:0.5+svn20090706); however:
  Package libavutil49 is to be removed.
  Package libavutil-extra-49 is not installed.
 libswscale0 depends on libavutil49 (<< 4:0.5+svn20090706-99) | libavutil-extra-49 (<< 4:0.5+svn20090706-99); however:
  Package libavutil49 is to be removed.
  Package libavutil-extra-49 is not installed.
 ffmpeg depends on libavutil49 (>= 4:0.5+svn20090706) | libavutil-extra-49 (>= 4:0.5+svn20090706); however:
  Package libavutil49 is to be removed.
  Package libavutil-extra-49 is not installed.
 ffmpeg depends on libavutil49 (<< 4:0.5+svn20090706-99) | libavutil-extra-49 (<< 4:0.5+svn20090706-99); however:
  Package libavutil49 is to be removed.
  Package libavutil-extra-49 is not installed.
 ffmpeg depends on libavutil49 (>= 4:0.5+svn20090706) | libavutil-extra-49 (>= 4:0.5+svn20090706); however:
  Package libavutil49 is to be removed.
  Package libavutil-extra-49 is not installed.
 ffmpeg depends on libavutil49 (<< 4:0.5+svn20090706-99) | libavutil-extra-49 (<< 4:0.5+svn20090706-99); however:
  Package libavutil49 is to be removed.
  Package libavutil-extra-49 is not installed.
 libavcodec52 depends on libavutil49 (>= 4:0.5+svn20090706) | libavutil-extra-49 (>= 4:0.5+svn20090706); however:
  Package libavutil49 is to be removed.
  Package libavutil-extra-49 is not installed.
 libavcodec52 depends on libavutil49 (<< 4:0.5+svn20090706-99) | libavutil-extra-49 (<< 4:0.5+svn20090706-99); however:
  Package libavutil49 is to be removed.
  Package libavutil-extra-49 is not installed.
 libavcodec52 depends on libavutil49 (>= 4:0.5+svn20090706) | libavutil-extra-49 (>= 4:0.5+svn20090706); however:
  Package libavutil49 is to be removed.
  Package libavutil-extra-49 is not installed.
 libavcodec52 depends on libavutil49 (<< 4:0.5+svn20090706-99) | libavutil-extra-49 (<< 4:0.5+svn20090706-99); however:
  Package libavutil49 is to be removed.
  Package libavutil-extra-49 is not installed.
Removing libavutil49 ...
dpkg: libavformat52: dependency problems, but removing anyway as you requested:
 transcode depends on libavformat52 (>= 3:0.svn20090303-1) | libavformat-extra-52 (>= 3:0.svn20090303-1); however:
  Package libavformat52 is to be removed.
  Package libavformat-extra-52 is not installed.
 libavdevice52 depends on libavformat52 (>= 4:0.5+svn20090706) | libavformat-extra-52 (>= 4:0.5+svn20090706); however:
  Package libavformat52 is to be removed.
  Package libavformat-extra-52 is not installed.
 libavdevice52 depends on libavformat52 (<< 4:0.5+svn20090706-99) | libavformat-extra-52 (<< 4:0.5+svn20090706-99); however:
  Package libavformat52 is to be removed.
  Package libavformat-extra-52 is not installed.
 libavdevice52 depends on libavformat52 (>= 4:0.5+svn20090706) | libavformat-extra-52 (>= 4:0.5+svn20090706); however:
  Package libavformat52 is to be removed.
  Package libavformat-extra-52 is not installed.
 libavdevice52 depends on libavformat52 (<< 4:0.5+svn20090706-99) | libavformat-extra-52 (<< 4:0.5+svn20090706-99); however:
  Package libavformat52 is to be removed.
  Package libavformat-extra-52 is not installed.
 ffmpeg depends on libavformat52 (>= 4:0.5+svn20090706) | libavformat-extra-52 (>= 4:0.5+svn20090706); however:
  Package libavformat52 is to be removed.
  Package libavformat-extra-52 is not installed.
 ffmpeg depends on libavformat52 (<< 4:0.5+svn20090706-99) | libavformat-extra-52 (<< 4:0.5+svn20090706-99); however:
  Package libavformat52 is to be removed.
  Package libavformat-extra-52 is not installed.
 ffmpeg depends on libavformat52 (>= 4:0.5+svn20090706) | libavformat-extra-52 (>= 4:0.5+svn20090706); however:
  Package libavformat52 is to be removed.
  Package libavformat-extra-52 is not installed.
 ffmpeg depends on libavformat52 (<< 4:0.5+svn20090706-99) | libavformat-extra-52 (<< 4:0.5+svn20090706-99); however:
  Package libavformat52 is to be removed.
  Package libavformat-extra-52 is not installed.
Removing libavformat52 ...
dpkg: libavcodec52: dependency problems, but removing anyway as you requested:
 transcode depends on libavcodec52 (>= 3:0.svn20090303-1) | libavcodec-extra-52 (>= 3:0.svn20090303-1); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 libavfilter0 depends on libavcodec52 (>= 4:0.5+svn20090706) | libavcodec-extra-52 (>= 4:0.5+svn20090706); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 libavfilter0 depends on libavcodec52 (<< 4:0.5+svn20090706-99) | libavcodec-extra-52 (<< 4:0.5+svn20090706-99); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 libavfilter0 depends on libavcodec52 (>= 4:0.5+svn20090706) | libavcodec-extra-52 (>= 4:0.5+svn20090706); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 libavfilter0 depends on libavcodec52 (<< 4:0.5+svn20090706-99) | libavcodec-extra-52 (<< 4:0.5+svn20090706-99); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 libavdevice52 depends on libavcodec52 (>= 4:0.5+svn20090706) | libavcodec-extra-52 (>= 4:0.5+svn20090706); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 libavdevice52 depends on libavcodec52 (<< 4:0.5+svn20090706-99) | libavcodec-extra-52 (<< 4:0.5+svn20090706-99); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 libavdevice52 depends on libavcodec52 (>= 4:0.5+svn20090706) | libavcodec-extra-52 (>= 4:0.5+svn20090706); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 libavdevice52 depends on libavcodec52 (<< 4:0.5+svn20090706-99) | libavcodec-extra-52 (<< 4:0.5+svn20090706-99); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 ffmpeg depends on libavcodec52 (>= 4:0.5+svn20090706) | libavcodec-extra-52 (>= 4:0.5+svn20090706); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 ffmpeg depends on libavcodec52 (<< 4:0.5+svn20090706-99) | libavcodec-extra-52 (<< 4:0.5+svn20090706-99); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 ffmpeg depends on libavcodec52 (>= 4:0.5+svn20090706) | libavcodec-extra-52 (>= 4:0.5+svn20090706); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 ffmpeg depends on libavcodec52 (<< 4:0.5+svn20090706-99) | libavcodec-extra-52 (<< 4:0.5+svn20090706-99); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 libquicktime1 depends on libavcodec52 (>= 3:0.svn20090303-1) | libavcodec-extra-52 (>= 3:0.svn20090303-1); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
Removing libavcodec52 ...
dpkg: libswscale0: dependency problems, but removing anyway as you requested:
 ffmpeg depends on libswscale0 (>= 4:0.5+svn20090706) | libswscale-extra-0 (>= 4:0.5+svn20090706); however:
  Package libswscale0 is to be removed.
  Package libswscale-extra-0 is not installed.
 ffmpeg depends on libswscale0 (<< 4:0.5+svn20090706-99) | libswscale-extra-0 (<< 4:0.5+svn20090706-99); however:
  Package libswscale0 is to be removed.
  Package libswscale-extra-0 is not installed.
 ffmpeg depends on libswscale0 (>= 4:0.5+svn20090706) | libswscale-extra-0 (>= 4:0.5+svn20090706); however:
  Package libswscale0 is to be removed.
  Package libswscale-extra-0 is not installed.
 ffmpeg depends on libswscale0 (<< 4:0.5+svn20090706-99) | libswscale-extra-0 (<< 4:0.5+svn20090706-99); however:
  Package libswscale0 is to be removed.
  Package libswscale-extra-0 is not installed.
 libquicktime1 depends on libswscale0 (>= 3:0.svn20090303-1) | libswscale-extra-0 (>= 3:0.svn20090303-1); however:
  Package libswscale0 is to be removed.
  Package libswscale-extra-0 is not installed.
Removing libswscale0 ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously deselected package libavutil-extra-49.
(Reading database ... 158711 files and directories currently installed.)
Unpacking libavutil-extra-49 (from .../libavutil-extra-49_4%3a0.5+svn20090706-2ubuntu3_i386.deb) ...
Selecting previously deselected package libdirac0c2a.
Unpacking libdirac0c2a (from .../libdirac0c2a_1.0.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package libopenjpeg2.
Unpacking libopenjpeg2 (from .../libopenjpeg2_1.3+dfsg-4_i386.deb) ...
Selecting previously deselected package libavcodec-extra-52.
Unpacking libavcodec-extra-52 (from .../libavcodec-extra-52_4%3a0.5+svn20090706-2ubuntu3_i386.deb) ...
Selecting previously deselected package libavformat-extra-52.
Unpacking libavformat-extra-52 (from .../libavformat-extra-52_4%3a0.5+svn20090706-2ubuntu3_i386.deb) ...
Selecting previously deselected package libopenal1.
Unpacking libopenal1 (from .../libopenal1_1%3a1.8.466-2_i386.deb) ...
Selecting previously deselected package libpostproc-extra-51.
Unpacking libpostproc-extra-51 (from .../libpostproc-extra-51_4%3a0.5+svn20090706-2ubuntu3_i386.deb) ...
Selecting previously deselected package libsvga1.
Unpacking libsvga1 (from .../libsvga1_1%3a1.4.3-27ubuntu1_i386.deb) ...
Selecting previously deselected package libswscale-extra-0.
Unpacking libswscale-extra-0 (from .../libswscale-extra-0_4%3a0.5+svn20090706-2ubuntu3_i386.deb) ...
Selecting previously deselected package mplayer-nogui.
Unpacking mplayer-nogui (from .../mplayer-nogui_2%3a1.0~rc3+svn20090426-1ubuntu10.1_i386.deb) ...
Selecting previously deselected package mencoder.
Unpacking mencoder (from .../mencoder_2%3a1.0~rc3+svn20090426-1ubuntu10.1_i386.deb) ...
Selecting previously deselected package libiso9660-5.
Unpacking libiso9660-5 (from .../libiso9660-5_0.78.2+dfsg1-3_i386.deb) ...
Selecting previously deselected package libvcdinfo0.
Unpacking libvcdinfo0 (from .../libvcdinfo0_0.7.23-4ubuntu1_i386.deb) ...
Selecting previously deselected package vcdimager.
Unpacking vcdimager (from .../vcdimager_0.7.23-4ubuntu1_i386.deb) ...
Selecting previously deselected package imagemagick.
Unpacking imagemagick (from .../imagemagick_7%3a6.5.1.0-1.1ubuntu3_i386.deb) ...
Selecting previously deselected package devede.
Unpacking devede (from .../devede_3.14.0-0ubuntu5_all.deb) ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for desktop-file-utils ...
Processing triggers for doc-base ...
Processing 1 added doc-base file(s)...
Registering documents with scrollkeeper...
Setting up libavutil-extra-49 (4:0.5+svn20090706-2ubuntu3) ...

Setting up libdirac0c2a (1.0.2-0ubuntu1) ...

Setting up libopenjpeg2 (1.3+dfsg-4) ...

Setting up libavcodec-extra-52 (4:0.5+svn20090706-2ubuntu3) ...

Setting up libavformat-extra-52 (4:0.5+svn20090706-2ubuntu3) ...

Setting up libopenal1 (1:1.8.466-2) ...

Setting up libpostproc-extra-51 (4:0.5+svn20090706-2ubuntu3) ...

Setting up libsvga1 (1:1.4.3-27ubuntu1) ...

Setting up libswscale-extra-0 (4:0.5+svn20090706-2ubuntu3) ...

Setting up mplayer-nogui (2:1.0~rc3+svn20090426-1ubuntu10.1) ...

Setting up mencoder (2:1.0~rc3+svn20090426-1ubuntu10.1) ...
Setting up libiso9660-5 (0.78.2+dfsg1-3) ...

Setting up libvcdinfo0 (0.7.23-4ubuntu1) ...

Setting up vcdimager (0.7.23-4ubuntu1) ...
Ignoring install-info called from maintainer script
The package vcdimager should be rebuild with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package vcdimager should be rebuild with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package vcdimager should be rebuild with new debhelper to get trigger support

Setting up imagemagick (7:6.5.1.0-1.1ubuntu3) ...

Setting up devede (3.14.0-0ubuntu5) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done


Any thoughts on this? I am trying to figure out why brasero isn't seeing either of my 2 dvd writers. So I thought I'd install my favoritre dvd maker and burner which is devede and to my surprise it resulted in removing tons of packages. One  of the dvd writers is at /dev/scd0 and the other at /dev/scd1. I have created fstab entries and I don't know what else to do?  I am in the cdrom group also.

lrwxrwxrwx  1 root   root           3 2010-01-08 23:16 scd0 -> sr0
lrwxrwxrwx  1 root   root           3 2010-01-08 23:16 scd1 -> sr1
crw-rw----  1 root   cdrom    21,   0 2010-01-08 23:16 sg0
crw-rw----  1 root   cdrom    21,   1 2010-01-08 23:16 sg1
brw-rw----+ 1 root   cdrom    11,   0 2010-01-08 23:16 sr0
brw-rw----+ 1 root   cdrom    11,   1 2010-01-08 23:16 sr1

---

