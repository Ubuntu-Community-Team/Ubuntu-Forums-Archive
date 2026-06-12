---
title: "How to install DIB engine."
date: 2009-09-21
forum: Wine
---

### Post by ElevenWarrior on 2009-09-21
I know it can be done, does anyone know how to do it?
(I hear rumors for doing it through the git-clone? what is that?)
This is a Fairly common problem, and I think many wine users would be grateful of the more knowable could share the idea instructions. :KS

---

### Post by ElevenWarrior on 2009-09-22
update, heres some info I found on the bug...
[http://wiki.winehq.org/DIBEngine](http://wiki.winehq.org/DIBEngine)
[http://bugs.winehq.org/show_bug.cgi?id=421](http://bugs.winehq.org/show_bug.cgi?id=421)

here's some of the instructions, but It didn't make sense to me..
   1.

      Grab a copy of Wine's source, either from git or from a tarball (extract it into some directory).
   2.

      Get the latest copy of the DIB Engine from bug 421. Look at the list of attachments (there are a lot) for the latest DIB engine patches. Extract the archive, and put the patches somewhere.
   3. 'cd' to the Wine source code and run 'rm -rf dlls/winedib.drv' to remove any old DIB engine stuff. If using git, be sure to run 'git checkout -f' as well as cleanup your git tree.
   4. Patch your source code. In the root directory, use 'patch -p1 /path/to/patch' for each patch, successively. Currently, there are 10 patches, but there may be more in later versions of the DIB engine.
   5. Run 'autoconf' to make a new configure file.
   6.

      Finally, build Wine: './configure && make depend && make'.
   7. Optionally, install Wine with 'sudo make install'.
   8. You can then use 'WINEDIB=ON wine program.exe' to run your program with the DIB engine enabled. Now you can run 'export WINEDIB=ON' in the terminal to enable it for all commands executed in that terminal, or edit the registry, as described above.

---

### Post by ElevenWarrior on 2009-09-25
so no one has any ideas??:confused:

---

### Post by Meow27 on 2009-09-26
to compile wine, you must do the following

open up the terminal and type
"sudo apt-get build-dep wine"

after that you must cd into the wine source folder and do ./configure

after that you need to do "make"

that was a crash course on compiling wine in ubuntu
edit------------------------
im gonna try doing this myself with max's dib patch... let me try doing it myself

---

### Post by Meow27 on 2009-09-26
ok im stumped as well, not sure how to automatically patch it

i get this 
```
root@Phrozen-box:~/Program_Files/wine-1.1.30# patch -p0 < dib_patch/0001-dib-engine-hook-the-engine-bet.patch 
can't find file to patch at input line 16
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|DIB Engine: Hook the engine between GDI32 and Display driver
|
|From: Massimo Del Fedele <max@veneto.com>
|
|
|---
|
| dlls/gdi32/driver.c |  139 +++++++++++++++++++++++++++++++++++++++++++++------
| 1 files changed, 123 insertions(+), 16 deletions(-)
|
|
|diff --git a/dlls/gdi32/driver.c b/dlls/gdi32/driver.c
|index 20d3f36..95a69c7 100644
|--- a/dlls/gdi32/driver.c
|+++ b/dlls/gdi32/driver.c
--------------------------
File to patch: 

```the last line is asking me to input something...not sure what though

---

### Post by ElevenWarrior on 2009-09-26
Did you download the patch file? (from the git tree I guess?)
looks like you did... I know there are more than one copy of the dib engine.

---

### Post by Meow27 on 2009-09-26
[http://bugs.winehq.org/attachment.cgi?id=21242](http://bugs.winehq.org/attachment.cgi?id=21242)

this is the one i used

---

### Post by ElevenWarrior on 2009-09-27
I can't even get it to patch..

---

### Post by k4fros on 2010-08-03
**+ Get the DIBEngine patch package**
 
**1.** Start a console window
**2.** Create a directory to upload the patch files
```
mkdir /usr/local/dibpatch
```
**3.** Download the engine patch files [http://bugs.winehq.org/attachment.cgi?id=28187](http://bugs.winehq.org/attachment.cgi?id=28187) in /usr/local/dibpatch/ directory 
*NOTE:The main page of the patch package is *[*http://bugs.winehq.org/show_bug.cgi?id=421*]("http://bugs.winehq.org/show_bug.cgi?id=421")* (we make use of the "DIB Engine - Fixed for wine-1.2-rc1" package which does work for Wine version 1.3.0)*
**4.** Browse to the patch package location
```
cd /usr/local/dibpatch
``` 
**5.** Uncompress the DIBEngine package
```
unzip dibeng-max.zip
```
**6.** Edit using your preferred editor the "series" file under /usr/local/dibpatch and delete the first line (# This series applies.....)
 
 
**+ Get wine and prepare for patching**
 
**1.** Start a console window
**2.** Download the latest wine source package (as of today version 1.3.0; replace accordingly) from [http://sourceforge.net/projects/wine/files/Source/](http://sourceforge.net/projects/wine/files/Source/) in /usr/local 
**3.** Browse to the wine source package location
```
cd /usr/local
```
**4.** Uncompress the wine source file
```
tar -jxvf wine-1.3.0.tar.bz2
```
**5.** Link the wine source directory to a generic name
```
ln -s wine-1.3.0 wine
```
**6.** Browse into the wine source directory
```
cd wine
```
**7.** Patch wine source with the DIBEngine patches
```
for i in `cat /usr/local/dibpatch/series` ; do patch -p1 < /usr/local/dibpatch/$i ; done
```
**8.** Compile & Install wine
```
./configure;make depend && make;make install
```
*NOTE:If you have a multi-core system (i.e. quad core) use **make depend && make -j5** to compile on all 4 cores at the same time (-j3 for dual etc.) ;)*
 
 
**+ Wrap up**
 
According to the DIBEngine information from the official Wine WiKi page ([http://wiki.winehq.org/DIBEngine](http://wiki.winehq.org/DIBEngine)):
To permanently enable the engine use [COLOR=black]regedit and create in [/COLOR]"HKEY_CURRENT_USER\Software\Wine\DIB Engine" a string named "Enabled" with value "Y".
*NOTE:Create the "HKEY_CURRENT_USER\Software\Wine\DIB Engine" key as well if does not exist*
 
 
I hope this help...
K4fros

---

