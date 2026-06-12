---
title: "Errors compiling libffado in Ubuntu Studio 11.10"
date: 2012-06-25
forum: Ubuntu Studio
---

### Post by OccamsChainsaw on 2012-06-25
Hi all. I am fairly new to linux, and i've been struggling trying to install FFADO with the mixer control utility in Ubuntu Studio 11.10.  I've consulted the instructions here:  [http://ffado.org/?q=node/613/](http://ffado.org/?q=node/613/) and installed all of the packages listed (where applicable--some of these are obsolete now according to synaptic and I'm guessing aren't required for the latest release of libffado. Also I'm using python-qt4 instead of 3). The readout I get is as follows:

```
scons: Reading SConscript files ...

scons: warning: The Options class is deprecated; use the Variables class instead.
File "/home/jmb/FFADO/libffado-2.0.0/SConstruct", line 38, in <module>

scons: warning: The BoolOption() function is deprecated; use the BoolVariable() function instead.
File "/home/jmb/FFADO/libffado-2.0.0/SConstruct", line 43, in <module>

scons: warning: The PathOption() function is deprecated; use the PathVariable() function instead.
File "/home/jmb/FFADO/libffado-2.0.0/SConstruct", line 45, in <module>

scons: warning: The EnumOption() function is deprecated; use the EnumVariable() function instead.
File "/home/jmb/FFADO/libffado-2.0.0/SConstruct", line 65, in <module>
Checking for a working C-compiler (cached) yes
Checking for a working C++-compiler (cached) yes
Checking for pkg-config (at least version 0.0.0)... (cached) yes
Checking for C header file expat.h... (cached) yes
Checking for XML_ExpatVersion() in C library expat... (cached) yes
Checking for libraw1394 (1.3.0 or higher)...     (cached) yes
Checking for dbus-1 (1.0 or higher)...     (cached) yes
Checking for libxml++-2.6 (2.13.0 or higher)...     (cached) yes
Checking for libiec61883 (1.1.0 or higher)...     (cached) yes
Checking for lrint(3.2) in C library m... (cached) yes
Checking for lrintf(3.2) in C library m... (cached) yes
Checking whether 'which pyuic4' executes (cached) no
Checking whether 'which pyuic' executes (cached) no
Checking whether 'xdg-desktop-menu --help' executes (cached) yes

I couldn't find all the prerequisites ('pyuic' / 'pyuic4' and the python-modules 'dbus' and
'qt' / 'PyQt4', the packages could be named like dbus-python and PyQt) to build the mixer.
Therefor neither the qt3 nor the qt4 mixer will get installed.

Trying to find the system triple: (cached) i686-pc-linux-gnu
Detected DIST_TARGET = i686
Doing a 32-bit build
sh: svnversion: not found
scons: done reading SConscript files.
scons: Building targets ...
g++ -o src/libavc/general/avc_extended_plug_info.os -c -O2 -m32 -DENABLE_BEBOB -DENABLE_FIREWORKS -DENABLE_MOTU -DENABLE_GENERICAVC -fPIC -DNDEBUG -DDBUS_HAS_THREADS_INIT_DEFAULT -I. -Isrc -I/usr/local/include -I/usr/local/include/glib-2.0 -I/usr/local/lib/glib-2.0/include -I/usr/include/libxml++-2.6 -I/usr/lib/libxml++-2.6/include -I/usr/include/libxml2 -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -Iexternal/libconfig src/libavc/general/avc_extended_plug_info.cpp
src/libavc/general/avc_extended_plug_info.cpp:131:1: error: ‘AVC::ExtendedPlugInfoPlugNameSpecificData::ExtendedPlugInfoPlugNameSpecificData’ names the constructor, not the type
src/libavc/general/avc_extended_plug_info.cpp:167:1: error: ‘AVC::ExtendedPlugInfoPlugNumberOfChannelsSpecificData::ExtendedPlugInfoPlugNumberOfChannelsSpecificData’ names the constructor, not the type
src/libavc/general/avc_extended_plug_info.cpp:240:1: error: ‘AVC::ExtendedPlugInfoPlugChannelPositionSpecificData::ExtendedPlugInfoPlugChannelPositionSpecificData’ names the constructor, not the type
src/libavc/general/avc_extended_plug_info.cpp:298:1: error: ‘AVC::ExtendedPlugInfoPlugChannelNameSpecificData::ExtendedPlugInfoPlugChannelNameSpecificData’ names the constructor, not the type
src/libavc/general/avc_extended_plug_info.cpp:345:1: error: ‘AVC::ExtendedPlugInfoPlugInputSpecificData::ExtendedPlugInfoPlugInputSpecificData’ names the constructor, not the type
src/libavc/general/avc_extended_plug_info.cpp:421:1: error: ‘AVC::ExtendedPlugInfoPlugOutputSpecificData::ExtendedPlugInfoPlugOutputSpecificData’ names the constructor, not the type
src/libavc/general/avc_extended_plug_info.cpp:483:1: error: ‘AVC::ExtendedPlugInfoClusterInfoSpecificData::ExtendedPlugInfoClusterInfoSpecificData’ names the constructor, not the type
src/libavc/general/avc_extended_plug_info.cpp: In member function ‘virtual bool AVC::ExtendedPlugInfoInfoType::serialize(Util::Cmd::IOSSerialize&)’:
src/libavc/general/avc_extended_plug_info.cpp:634:63: warning: ignoring return value of ‘int asprintf(char**, const char*, ...)’, declared with attribute warn_unused_result [-Wunused-result]
scons: *** [src/libavc/general/avc_extended_plug_info.os] Error 1
scons: building terminated because of errors.

```When I try the workaround listed in the link above (commenting out the part in the SConstruct script where it checks for pyuic-4) I get the same error, minus the bit about not finding the prereqs obviously.  I have done a little research into the problem and it seems that there are known problems compiling ffado with gcc 4.5 (i am using 4.6.1 according to dpkg), but I haven't found what I need to do with the libavc source code to fix this. Any tips would be hugely appreciated. Thanks in advance.

---

### Post by OccamsChainsaw on 2012-06-28
I can't exactly say that I solved the problem, but I did manage to get libffado to compile by trying the latest stable (afaik) beta version available through svn. I'm marking this as solved in case someone else runs into the same issue, this workaround might be useful to them as well.

---

