---
title: "CMake Error /.../FindX11.cmake:362 (MESSAGE):      Could not find X11"
date: 2009-11-17
forum: Server Platforms
---

### Post by jp.hendrix on 2009-11-17
On a clean Ubuntu server 9.10 x86_64 install, I am receiving an X11 not found message. I am having trouble to find out which exact package I mis. Not sure if it is an Ubuntu, CMake, KDE or khtml2png problem.

[COLOR=DarkRed]Update: Same problem on full 9.10 Kubuntu desktop install.[/COLOR]

Please advice: 
```
$ sudo apt-get install virtualbox-ose-guest-source virtualbox-ose-guest-utils
$ sudo apt-get install xvfb x11-apps netpbm openssh-server imagemagick cmake gcc g++ \
kdelibs 
### kdebase-runtime ?????????

$ Xvfb :0 -br &
$ DISPLAY=:0 xclock &
$ xwd -display localhost:0 -root | xwdtopnm > /tmp/dump.pmm
$ convert /tmp/dump.pmm /tmp/dump.jpg

<snapshot.1>
$ cd
$ wget http://dfn.dl.sourceforge.net/sourceforge/khtml2png/khtml2png-<latest-version>.tar.gz
$ tar xzf khtml2png-2.7.6.tar.gz
$ cd khtml2png-<latest-version>

$ sudo -i
# cd ~jhendrix/khthml2png-<latest-version>
# ./configure
rm: cannot remove `cmake_install.cmake': No such file or directory
rm: cannot remove `Doxyfile': No such file or directory           
rm: cannot remove `*.moc': No such file or directory              
rm: cannot remove `khtml2png2': No such file or directory         
rm: cannot remove `*.kdevelop': No such file or directory         
rm: cannot remove `khtml2png2.kdevelop.filelist': No such file or directory
rm: cannot remove `khtml2png2.kdevses': No such file or directory          
-- The C compiler identification is GNU                                    
-- The CXX compiler identification is GNU                                  
-- Check for working C compiler: /usr/bin/gcc                              
-- Check for working C compiler: /usr/bin/gcc -- works                     
-- Detecting C compiler ABI info                                           
-- Detecting C compiler ABI info - done                                    
-- Check for working CXX compiler: /usr/bin/c++                            
-- Check for working CXX compiler: /usr/bin/c++ -- works                   
-- Detecting CXX compiler ABI info                                         
-- Detecting CXX compiler ABI info - done                                  
CMake Error at /usr/share/cmake-2.6/Modules/FindX11.cmake:362 (MESSAGE):   
  Could not find X11                                                       
Call Stack (most recent call first):
  /usr/share/cmake-2.6/Modules/FindKDE3.cmake:92 (FIND_PACKAGE)
  CMakeLists.txt:6 (find_package)


-- Configuring incomplete, errors occurred!
CMake Error at /usr/share/cmake-2.6/Modules/FindX11.cmake:362 (MESSAGE):
  Could not find X11
Call Stack (most recent call first):
  /usr/share/cmake-2.6/Modules/FindKDE3.cmake:92 (FIND_PACKAGE)
  CMakeLists.txt:6 (find_package)


-- Configuring incomplete, errors occurred!
```

---

### Post by jp.hendrix on 2009-11-18
Using strace, I figured out that I was missing header files. So I installed some extra development packages:

```
 $ sudo apt-get install kdelibs4-dev libkde3-java libkde3-jni
```

And now configure/cmake runs fine.

SOLVED

---

### Post by astraluxkl on 2011-10-15
Thanks it works

in **Kubuntu 11.10**

 $ sudo apt-get install kdelibs5-dev

---

