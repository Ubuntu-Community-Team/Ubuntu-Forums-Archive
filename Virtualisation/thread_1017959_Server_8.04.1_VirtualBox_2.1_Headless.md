---
title: "Server 8.04.1 VirtualBox 2.1 Headless"
date: 2008-12-21
forum: Virtualisation
---

### Post by kihjin on 2008-12-21
Has anyone been able to install virtualbox 2.1 without xorg? I'm running Ubuntu Server and I'd like to run virtualbox headless, but to install I need various X dependencies and qtgui4. This seems silly to be since I don't plan on running a GUI.

[edit]
I'm currently on the virtualbox.org forum, and I've found this [http://forums.virtualbox.org/viewtopic.php?t=11633](http://forums.virtualbox.org/viewtopic.php?t=11633)
Not sure yet if it is what I need, but it looks promising.
[/edit]

---

### Post by thornomad on 2008-12-22
I don't mean to hijack your thread, but I wanted to chime in and say that I, too, am curious how to run a headless virtual machine.  

I run a NAS server using Ubuntu and wanted to add a LAMP virtual machine -- seems like most folks are using Virtual Box to do it ... (but I wouldn't mind using any headless variety).

Did you try the script in the link you provided?

---

### Post by kihjin on 2008-12-22
Hey no problem. I have been working on my "problem" ever since I posted yesterday. I am working closer to a solution, so far so good!

The script was useful. I ended up writing my own script for virtualbox 2.1. It is completely headless and doesn't require Qt, SDL or X at all. 

It should work for any of the 2.1 releases, just update the source and dest before you run it. 

I'm not entirely sure, but I think there's a bug in this script dealing with file ownership. After you dpkg -i the deb, the files installed might be owned by someone other than root. In my experience with it, the files were owned by the user that created the deb. I haven't investigated on how to resolve this. Here's a post-install work-around to resolve the problem:

chown -R root. /usr/lib/virtualbox /usr/bin/{VBoxHeadless,VBoxManage,VBox}
chmod u+s /usr/lib/virtualbox/VBoxHeadless

```

#!/bin/bash
# virtualbox-2.1-repack.sh
# Author kihjin@ubuntuforums, based on work done here
# http://forums.virtualbox.org/viewtopic.php?t=11633

source=virtualbox-2.1_2.1.0-41146_Ubuntu_hardy_amd64.deb
dest=virtualbox-headless-2.1_2.1.0-41146_Ubuntu_hardy_amd64.deb

tmp=`mktemp -d`

dpkg-deb --extract $source "$tmp"
dpkg-deb --control $source "$tmp/DEBIAN"

pushd $tmp

rm -f -- usr/{bin,lib/virtualbox}/{VirtualBox,VBoxSDL}

libs="libQtGui libX11 libSDL"
for F in $(find usr/lib/virtualbox -type f); do 
 out=`ldd "$F"`
 for L in $libs; do
  echo $out | grep $L 2>&1 >/dev/null
  if [ $? -eq 0 ]; then
   rm -f -- "$F"
   break
  fi
 done
done

# VBoxHeadless still tries to access this lib
# this seems to get it running...
touch usr/lib/virtualbox/VBoxSharedClipboard.so

sed -i -r -e 's|Package: virtualbox|&-headless|' 		\
 -e 's|(Conflicts: )(virtualbox)|\1\2-headless, \2|' 	\
 -e 's|Replaces: virtualbox|&-headless|' 		\
 -e 's|Provides: virtualbox|&-headless|' 		\
 -e 's|libx11-6(, )?||g'				\
 -e 's|libxext6(, )?||g'				\
 -e 's|libxt6(, )?||g'					\
 -e 's|libxmu6(, )?||g'					\
 -e 's|libpulse0(, )?||g'				\
 -e 's|libgl1(, )?||g'					\
 -e 's|libsdl-ttf([^,]*)(, )?||g'			\
 -e 's|libqt4-gui ?(\([^\)]*\))?(, )?||g'		\
 -e 's|libqt4-core ?(\([^\)]*\))?(, )?||g'		\
 -e 's|libxcursor1 ?(\([^\)]*\))?(, )?||g'		\
 -e 's|libsdl1.2debian ?(\([^\)]*\))?(, )?||g'		\
 -e 's|libxslt1.1 ?(\([^\)]*\))?(, )?||g'		\
 DEBIAN/control

popd

dpkg-deb --build "$tmp" $dest

```

---

### Post by thornomad on 2008-12-23
Hey - thanks for posting your success (or near success!) -- I will definitely have to try that script out when I have a chance and will post back with results.  Thanks again.

---

### Post by jcvsilva on 2009-01-16
I installed VirtualBox in a Ubuntu Server with this script, but I cannot create a VM:

/usr/lib/virtualbox/VBoxSVC: error while loading shared libraries: libxslt.so.1: cannot open shared object file: No such file or directory

Is there something I can do to fix it?

---

### Post by kihjin on 2009-01-16
My Script has an error in it.

You need to install libxslt1.1
**sudo apt-get install libxslt1.1**

Here is an updated script that should reflect this dependency.

```

#!/bin/bash
# virtualbox-2.1-repack.sh
# Author kihjin@ubuntuforums, based on work done here
# http://forums.virtualbox.org/viewtopic.php?t=11633

source=virtualbox-2.1_2.1.0-41146_Ubuntu_hardy_amd64.deb
dest=virtualbox-headless-2.1_2.1.0-41146_Ubuntu_hardy_amd64.deb

tmp=`mktemp -d`

dpkg-deb --extract $source "$tmp"
dpkg-deb --control $source "$tmp/DEBIAN"

pushd $tmp

rm -f -- usr/{bin,lib/virtualbox}/{VirtualBox,VBoxSDL}

libs="libQtGui libX11 libSDL"
for F in $(find usr/lib/virtualbox -type f); do 
 out=`ldd "$F"`
 for L in $libs; do
  echo $out | grep $L 2>&1 >/dev/null
  if [ $? -eq 0 ]; then
   rm -f -- "$F"
   break
  fi
 done
done

# VBoxHeadless still tries to access this lib
# this seems to get it running...
touch usr/lib/virtualbox/VBoxSharedClipboard.so

sed -i -r -e 's|Package: virtualbox|&-headless|' 		\
 -e 's|(Conflicts: )(virtualbox)|\1\2-headless, \2|' 	\
 -e 's|Replaces: virtualbox|&-headless|' 		\
 -e 's|Provides: virtualbox|&-headless|' 		\
 -e 's|libx11-6(, )?||g'				\
 -e 's|libxext6(, )?||g'				\
 -e 's|libxt6(, )?||g'					\
 -e 's|libxmu6(, )?||g'					\
 -e 's|libpulse0(, )?||g'				\
 -e 's|libgl1(, )?||g'					\
 -e 's|libsdl-ttf([^,]*)(, )?||g'			\
 -e 's|libqt4-gui ?(\([^\)]*\))?(, )?||g'		\
 -e 's|libqt4-core ?(\([^\)]*\))?(, )?||g'		\
 -e 's|libxcursor1 ?(\([^\)]*\))?(, )?||g'		\
 -e 's|libsdl1.2debian ?(\([^\)]*\))?(, )?||g'		\
 DEBIAN/control

popd

dpkg-deb --build "$tmp" $dest

```

---

### Post by jcvsilva on 2009-01-16
Thank you! It's working!:)

---

### Post by Name User on 2009-08-30
hi all.
after messing around vbox 3.0 for hours on a headless server i found your post and adapted your script to virtualbox 3.0.
thank you
you still have to install libxslt1.1 e.g. 
sudo apt-get install libxslt1.1
 
```
#!/bin/bash
# virtualbox-3.0-repack.sh
# Author kihjin@ubuntuforums,messed up by true1984 ;-) based on work done here
# http://forums.virtualbox.org/viewtopic.php?t=11633

source=virtualbox-3.0_3.0.4-50677_Ubuntu_jaunty_i386.deb
dest=virtualbox-headless-3.0_3.0.4-50677_Ubuntu_jaunty_i386.deb

tmp=`mktemp -d`

dpkg-deb --extract $source "$tmp"
dpkg-deb --control $source "$tmp/DEBIAN"

pushd $tmp

rm -f -- usr/{bin,lib/virtualbox}/{VirtualBox,VBoxSDL}

libs="libQtGui libX11 libSDL"
for F in $(find usr/lib/virtualbox -type f); do 
 out=`ldd "$F"`
 for L in $libs; do
  echo $out | grep $L 2>&1 >/dev/null
  if [ $? -eq 0 ]; then
   rm -f -- "$F"
   break
  fi
 done
done

# VBoxHeadless still tries to access this lib
# this seems to get it running...
touch usr/lib/virtualbox/VBoxSharedClipboard.so

sed -i -r -e 's|Package: virtualbox|&-headless|' 		\
 -e 's|(Conflicts: )(virtualbox)|\1\2-headless, \2|' 	\
 -e 's|Replaces: virtualbox|&-headless|' 		\
 -e 's|Provides: virtualbox|&-headless|' 		\
 -e 's|libx11-6(, )?||g'				\
 -e 's|libxext6(, )?||g'				\
 -e 's|libxt6(, )?||g'					\
 -e 's|libxmu6(, )?||g'					\
 -e 's|libpulse0(, )?||g'				\
 -e 's|libgl1(, )?||g'					\
 -e 's|libsdl-ttf([^,]*)(, )?||g'			\
 -e 's|libqt4-gui ?(\([^\)]*\))?(, )?||g'		\
 -e 's|libqt4-core ?(\([^\)]*\))?(, )?||g'		\
 -e 's|libxcursor1 ?(\([^\)]*\))?(, )?||g'		\
 -e 's|libpython2.6 ?(\([^\)]*\))?(, )?||g'		\
 -e 's|libqt4-network ?(\([^\)]*\))?(, )?||g'		\
 -e 's|libqtcore4 ?(\([^\)]*\))?(, )?||g'		\
 -e 's|libqtgui4 ?(\([^\)]*\))?(, )?||g'		\
 -e 's|libxslt1.1 ?(\([^\)]*\))?(, )?||g'		\
 -e 's|libsdl1.2debian ?(\([^\)]*\))?(, )?||g'		\
 DEBIAN/control

popd

dpkg-deb --build "$tmp" $dest
```

---

### Post by kihjin on 2009-08-30
Yes the script does adapt well from 2.x to 3.0.x. I had adapted my own but didn't bother posting since there wasn't any significant changes.

I've found that on Ubuntu server 9.04, installing Virtual Box 3.0.4 (headless variant) you will also need libcurl3 and libxml2:

sudo apt-get install libcurl3 libxml2

They might have been installed already if you did any prior apt-get'ing

---

