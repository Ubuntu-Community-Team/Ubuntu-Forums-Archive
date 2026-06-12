---
title: "vmware server2.02 workaround for karmic 9.10"
date: 2009-10-30
forum: Virtualisation
---

### Post by sdowney717 on 2009-10-30
still working for 2.02 vmware server
there are 3 issues to get this to work like it should,

1. one is getting it installed, 
2. the mouse issue where you must export the setting, so it uses vmware shipped  version of gtk
3. make sure kvm modules are not loaded or the virtual machines will hang
4. setting up shared folders, you can use drive maping in the windows guest to see ubuntu host shares. Sharing windows files in the guest will let ubuntu host see them as well. setup the network as bridged


for the mouse and kvm module issue, simply make a text file named launchVM.sh and make it executable with this inside. 
After you get your VM working in the wmware server from the browser, you can launch it at any time by running launchVM.sh and it will present a list of machines to start. The web browser does not have to be even running.

> gksudo /etc/init.d/libvirt-bin stop
sudo modprobe -r kvm_intel
sudo modprobe -r kvm
#!/bin/bash
################################################################################
# Call VMWare Server's Remote Console in a clean GTK setup.
################################################################################

# Clean GTK setup for VMWare
export VMWARE_USE_SHIPPED_GTK=yes

# Find console executable in Firefox plugins.
vmrc="$(find "$HOME/.mozilla/firefox" -name vmware-vmrc -type f -perm -111 | tail -1)"
[ -x "$vmrc" ] || exit 1

set -x
cd "$(dirname "$vmrc")" && "$vmrc" -h 127.0.0.1:8333


for the installation issue 

[http://blog.mymediasystem.net/uncategorized/vmware-server-2-0-1-installation-howto-for-karmic-koala-x86_64/](http://blog.mymediasystem.net/uncategorized/vmware-server-2-0-1-installation-howto-for-karmic-koala-x86_64/)
> VMware-server 2.0.1 Installation HOWTO for Karmic Koala (x86_64)
October 10th, 2009 by acmelab68

I was trying to install the VMware server 2.0.1 x86_64 on my new Karmic Koala (Ubuntu 9.10, kernel 2.6.31-13) server, but I&#8217;ve got a bunch of errors. Looking for an any-any patch haven&#8217;t been successful, but I&#8217;ve found an discussion thread, where the problem was solved. Unfortunately it sucks a bit going through the links and threads. That&#8217;s why here is a short and clear HOWTO with an already fixed patch:

First time installation

* Download or get VMware-server-2.0.1-156745.x86_64.tar.gz and unpack it.
* go into vmware-server-distrib and run vmware-install.pl.
* the process stops with an error. (... wait.h:78: error: conflicting types ... ).
Download and unpack this vmware-server.2.0.1_x64-modules-2.6.30.4-fix.tgz into the vmware-server-distrib directory.
Invoke vmware-server.2.0.1_x64-modules-2.6.30.4-fix.sh
* remove this directory: /usr/lib/vmware/modules/binary
* start vmware-config.pl
* This should leave you with a working VMware installation. Go now with your browser to [https://localhost:8333](https://localhost:8333) and enter your Serial Number under &#8220;Applications->Enter Serial Number&#8220;.

Reinstallation
If anything goes wrong, you can do the installation again. In order to do so, you need to do some steps manually on your console.

* first, delete the vmware modules

rm -rf /usr/lib/vmware/modules/

and if necessary (you&#8217;ll be told, if so):

rm -rf /lib/modules/2.6.31-13-server/misc/vm*

* If the vmware-config.pl aborts, because it can&#8217;t accomplish to shut down all vmware processes, kill all vmware processes manually.

kill -9 $( grep -i vm | awk '{ print $2 }' )

* rerun vmware-config.pl
* if somewhere in the installation process you should be asked:

&#8220;/usr/bin/vmware-config.pl&#8220;. Do you want this
program to invoke the command for you now? [yes]

you should answer: no
then run the patch vmware-server.2.0.1_x64-modules-2.6.30.4-fix.sh.
After this you run /usr/bin/vmware-config.pl

Empty Browser Remote Console Problem

Sometime it happens, my Firefox 3.5.3 doesn&#8217;t show anything, if I try to start [https://localhost:8333](https://localhost:8333). If I should take a wild *** guess, this is all due to my multiple installation attempts of the VMware server itself. Or is it just buggy?
I noticed, that actually three different approaches (sometimes in combination) lead to a relief.

* Don&#8217;t use hostnames, but IPs only in your browser. E.g: [https://127.0.0.1:8333/ui](https://127.0.0.1:8333/ui) instead of [https://localhost:8333/ui](https://localhost:8333/ui)
* Restart the vmware-hostd (your running VM&#8217;s won&#8217;t be affected <- bold statement, don&#8217;t you think?).

/etc/initd.d/vmware-mgmt restart

If the process number stays unchanged, and a log entry in /var/log/vmware/hostd-x.log indicates an already running vmware-hostd, kill the process manually, because it seams to hang:

killall -9 vmware-hostd

* Uninstall the VMware remote console Plug-in:

Menu: Tools -> Add-ons -> Tag:Extentions -> &#8220;VMware remote console Plug-in&#8221; -> Button:Uninstall

and reinstall it again. Perform the first step.

* Remove the VMware&#8217;s SSL-Certificate:

Menu: Edit -> Preferences -> Section:Advanced -> Tab:Security ->Tab:Encryption -> Button:View Cerfiticates -> Authorities.

Scroll down, until VMware shows up. Select and delete all entries. Perform the first step
* Or follow a completely different approach described here

You can read a more complete error log of the failed VMWare server installation here.

make[1]: Entering directory `/usr/src/linux-headers-2.6.31-13-server'
CC [M] /tmp/vmware-config1/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.c:31:
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:78: error: conflicting types for &#8216;poll_initwait&#8217;
include/linux/poll.h:70: note: previous declaration of &#8216;poll_initwait&#8217; was here
In file included from /tmp/vmware-config1/vmmon-only/./include/vmware.h:38,

use a social bookmark, e-mail or print this story

* Digg
* del.icio.us
* MisterWong
* StumbleUpon
* Google Bookmarks
* Technorati
* Facebook
* MySpace
* Live
* email
* Print

Tags: 9.10, error, HOWTO, istallation, karmic, koala, problem, server, ubuntu, vmware, x86_64.
1 Response to &#8220;VMware-server 2.0.1 Installation HOWTO for Karmic Koala (x86_64)&#8221;

1. Daniele

Works perfectly, thanks a ton!! 

---

### Post by LittleLebowski on 2009-10-30
Followed the instructions exactly on a new install of 2.0.2 on a fresh install of Koala 64b and it still fails.

```
Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config4/vmmon-only'
make -C /lib/modules/2.6.31-14-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /tmp/vmware-config4/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config4/vmmon-only/linux/driver.c:31:
/tmp/vmware-config4/vmmon-only/./include/compat_wait.h:78: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:70: note: previous declaration of ‘poll_initwait’ was here
In file included from /tmp/vmware-config4/vmmon-only/./include/vmware.h:38,
                 from /tmp/vmware-config4/vmmon-only/linux/driver.c:99:
/tmp/vmware-config4/vmmon-only/./include/vm_basic_types.h:108:7: warning: "__FreeBSD__" is not defined
In file included from /tmp/vmware-config4/vmmon-only/./include/vcpuset.h:103,
                 from /tmp/vmware-config4/vmmon-only/./include/modulecall.h:37,
                 from /tmp/vmware-config4/vmmon-only/./common/vmx86.h:33,
                 from /tmp/vmware-config4/vmmon-only/linux/driver.h:29,
                 from /tmp/vmware-config4/vmmon-only/linux/driver.c:101:
/tmp/vmware-config4/vmmon-only/./include/vm_atomic.h:329:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config4/vmmon-only/./include/vm_atomic.h:333:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config4/vmmon-only/./include/vm_atomic.h:401:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config4/vmmon-only/./include/vm_atomic.h:407:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config4/vmmon-only/./include/vm_atomic.h:460:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config4/vmmon-only/./include/vm_atomic.h:506:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config4/vmmon-only/./include/vm_atomic.h:551:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config4/vmmon-only/./include/vm_atomic.h:595:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config4/vmmon-only/./include/vm_atomic.h:640:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config4/vmmon-only/./include/vm_atomic.h:684:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config4/vmmon-only/./include/vm_atomic.h:729:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config4/vmmon-only/./include/vm_atomic.h:773:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config4/vmmon-only/./include/vm_atomic.h:775:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config4/vmmon-only/./include/vm_atomic.h:816:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config4/vmmon-only/./include/vm_atomic.h:860:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config4/vmmon-only/./include/vm_atomic.h:862:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config4/vmmon-only/./include/vm_atomic.h:903:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config4/vmmon-only/./include/vm_atomic.h:945:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config4/vmmon-only/./include/vm_atomic.h:947:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config4/vmmon-only/./include/vm_atomic.h:986:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config4/vmmon-only/./include/vm_atomic.h:1028:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config4/vmmon-only/./include/vm_atomic.h:1030:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config4/vmmon-only/./include/vm_atomic.h:1069:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config4/vmmon-only/./include/vm_atomic.h:1223:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config4/vmmon-only/./include/vm_atomic.h:1227:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config4/vmmon-only/./include/vm_atomic.h:1313:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config4/vmmon-only/./include/vm_atomic.h:1536:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config4/vmmon-only/./include/vm_atomic.h:1663:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config4/vmmon-only/./include/vm_atomic.h:1796:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config4/vmmon-only/./include/vm_asm_x86_64.h:39,
                 from /tmp/vmware-config4/vmmon-only/./include/vm_asm.h:41,
                 from /tmp/vmware-config4/vmmon-only/linux/driver.c:103:
/tmp/vmware-config4/vmmon-only/./include/vm_asm_x86.h:486:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config4/vmmon-only/./include/vm_asm_x86.h:779:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config4/vmmon-only/./include/vm_asm_x86.h:820:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config4/vmmon-only/./include/vm_asm_x86.h:922:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config4/vmmon-only/./include/vm_asm.h:41,
                 from /tmp/vmware-config4/vmmon-only/linux/driver.c:103:
/tmp/vmware-config4/vmmon-only/./include/vm_asm_x86_64.h:56:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config4/vmmon-only/linux/driver.c:119:
/tmp/vmware-config4/vmmon-only/./common/hostif.h:53:7: warning: "WINNT_DDK" is not defined
/tmp/vmware-config4/vmmon-only/linux/driver.c: In function ‘LinuxDriverSyncCallOnEachCPU’:
/tmp/vmware-config4/vmmon-only/linux/driver.c:1423: error: too many arguments to function ‘smp_call_function’
/tmp/vmware-config4/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config4/vmmon-only/linux/driver.c:1987: error: ‘struct task_struct’ has no member named ‘euid’
/tmp/vmware-config4/vmmon-only/linux/driver.c:1987: error: ‘struct task_struct’ has no member named ‘uid’
/tmp/vmware-config4/vmmon-only/linux/driver.c:1988: error: ‘struct task_struct’ has no member named ‘fsuid’
/tmp/vmware-config4/vmmon-only/linux/driver.c:1988: error: ‘struct task_struct’ has no member named ‘uid’
/tmp/vmware-config4/vmmon-only/linux/driver.c:1989: error: ‘struct task_struct’ has no member named ‘egid’
/tmp/vmware-config4/vmmon-only/linux/driver.c:1989: error: ‘struct task_struct’ has no member named ‘gid’
/tmp/vmware-config4/vmmon-only/linux/driver.c:1990: error: ‘struct task_struct’ has no member named ‘fsgid’
/tmp/vmware-config4/vmmon-only/linux/driver.c:1990: error: ‘struct task_struct’ has no member named ‘gid’
/tmp/vmware-config4/vmmon-only/linux/driver.c:2007: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vmware-config4/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config4/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config4/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/go/unsup-linux-products" and 
"http://www.vmware.com/go/unsup-linux-tools".

Execution aborted.

```

---

### Post by sdowney717 on 2009-10-30
did you do 3, 4, 5, 6?
looks like you did 1 and 2 

1 * Download or get VMware-server-2.0.1-156745.x86_64.tar.gz and unpack it.
2 * go into vmware-server-distrib and run vmware-install.pl.
* the process stops with an error. (... wait.h:78: error: conflicting types ... ).
3 Download and unpack this vmware-server.2.0.1_x64-modules-2.6.30.4-fix.tgz into the vmware-server-distrib directory.
4 Invoke vmware-server.2.0.1_x64-modules-2.6.30.4-fix.sh
5 * remove this directory: /usr/lib/vmware/modules/binary
6 * start vmware-config.pl
* This should leave you with a working VMware installation. Go now with your browser to [https://localhost:8333](https://localhost:8333) and enter your Serial Number under “Applications->Enter Serial Number“.

---

### Post by doug-M on 2009-10-31
> **sdowney717 said:**
> 
for the mouse and kvm module issue, simply make a text file named launchVM.sh and make it executable with this inside. 
After you get your VM working in the wmware server from the browser, you can launch it at any time by running launchVM.sh and it will present a list of machines to start. The web browser does not have to be even running.


I tried this but I get:
extensions/VMwareVMRC@vmware.com/plugins/bin/vmware-vmrc: error while loading shared libraries: libexpat.so.0: cannot open shared object file: No such file or directory

libexpat.so.0 is in /usr/lib/vmware/lib/ so I added:
export LD_LIBRARY_PATH=/usr/lib:/usr/lib/vmware/lib/

Now I get:
extensions/VMwareVMRC@vmware.com/plugins/bin/vmware-vmrc: error while loading shared libraries: /usr/lib/vmware/lib/libexpat.so.0: cannot read file data: Error 21

The file wrapper-gtk24.sh in /usr/lib/vmware/lib jumps through lots of hoops to get an LD_LIBRARY_PATH.

Any ideas? All help appreciated.

My windows XP guest won't notice a ctrl-alt-ins to let me login as it is right now.

---

### Post by sdowney717 on 2009-10-31
not sure why it does not work

i put a couple screen shots in showing how it brings up a server window for the vm's.

running the shell script in a terminal window for me shows this

> scott@scott-desktop:~$ export VMWARE_USE_SHIPPED_GTK=yes
scott@scott-desktop:~$ vmrc="$(find "$HOME/.mozilla/firefox" -name vmware-vmrc -type f -perm -111 | tail -1)"
scott@scott-desktop:~$ [ -x "$vmrc" ] || exit 1
scott@scott-desktop:~$ 
scott@scott-desktop:~$ set -x
scott@scott-desktop:~$ cd "$(dirname "$vmrc")" && "$vmrc" -h 127.0.0.1:8333 
++ dirname /home/scott/.mozilla/firefox/37a1mahz.default/extensions/VMwareVMRC@vmware.com/plugins/vmware-vmrc
+ cd /home/scott/.mozilla/firefox/37a1mahz.default/extensions/VMwareVMRC@vmware.com/plugins
+ /home/scott/.mozilla/firefox/37a1mahz.default/extensions/VMwareVMRC@vmware.com/plugins/vmware-vmrc -h 127.0.0.1:8333
Gtk-Message: Failed to load module "canberra-gtk-module": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory



---

### Post by sdowney717 on 2009-10-31
that libpat file is in vmware only
perhaps vmware is still not installed properly for you?

"My windows XP guest won't notice a ctrl-alt-ins to let me login as it is right now."
i think any ctrl-alt key combination will not work since that takes away the mouse focus out of the vm.

---

### Post by doug-M on 2009-10-31
Maybe yours has an LD_LIBRARY_PATH set in your shell.
If you type env what does it show for LD_LIBRARY_PATH?

---

### Post by sdowney717 on 2009-10-31
here is entire env

> scott@scott-desktop:~$ env
ORBIT_SOCKETDIR=/tmp/orbit-scott
SSH_AGENT_PID=3195
TERM=xterm
SHELL=/bin/bash
XDG_SESSION_COOKIE=c5cf650c106dab20f6fd38f74ab47905-1257005239.566305-1827298449
GTK_RC_FILES=/etc/gtk/gtkrc:/home/scott/.gtkrc-1.2-gnome2
WINDOWID=73400324
GTK_MODULES=canberra-gtk-module
USER=scott
LS_COLORS=rs=0:di=01;34:ln=01;36:hl=44;37:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.axv=01;35:*.anx=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.axa=00;36:*.oga=00;36:*.spx=00;36:*.xspf=00;36:
SSH_AUTH_SOCK=/tmp/keyring-o3zGLP/socket.ssh
GNOME_KEYRING_SOCKET=/tmp/keyring-o3zGLP/socket
SESSION_MANAGER=local/scott-desktop:@/tmp/.ICE-unix/3156,unix/scott-desktop:/tmp/.ICE-unix/3156
USERNAME=scott
DESKTOP_SESSION=gnome
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
PWD=/home/scott
GDM_KEYBOARD_LAYOUT=us
LANG=en_US.UTF-8
GNOME_KEYRING_PID=3141
GDM_LANG=en_US.UTF-8
GDMSESSION=gnome
SPEECHD_PORT=7560
SHLVL=1
HOME=/home/scott
GNOME_DESKTOP_SESSION_ID=this-is-deprecated
LOGNAME=scott
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-X76veIgudd,guid=f1e6425071884500bda49e964aec60b8
XDG_DATA_DIRS=/usr/share/gnome:/usr/local/share/:/usr/share/
LESSOPEN=| /usr/bin/lesspipe %s
DISPLAY=:0.0
LESSCLOSE=/usr/bin/lesspipe %s %s
COLORTERM=gnome-terminal
XAUTHORITY=/var/run/gdm/auth-for-scott-vI6xPO/database
_=/usr/bin/env
scott@scott-desktop:~$ 


---

### Post by doug-M on 2009-10-31
hmm so you have no ld-library-path
sry messing with vmware breaks my shift alt and ctrl keys right now so no caps.

so i found that /usr/lib/vmware/lib/libexpat.so.0 is actually a directory not a file, so adding /usr/lib/vmware/lib/libexpat.so.0 to the ld-library-path got it farther, after adding about 6 more paths to it, some in the firefox extensions directory, allowed it to start.

unfortunately no success.

i did notice one thing, it appears to be happier in the upper left corner of the console, i saw other people mentioning they have a 640x480 window where the mouse works. that might be what is happening to me.

also my firefox profile just got moved from 32bit to 64 bit, perhaps some old 32 bit stuff got left in there and not cleaned up.

any idea how to reinstall the 64bit plugin, i could try blowing away all the vmware stuff in my profile and re-installing.

---

### Post by sdowney717 on 2009-10-31
the mouse issue is because our new linux gtk does not play right with vmware.
SO, vmware ships gtk's that do work. but you have to tell your application to use the vmware versions of gtk and not our standard 2.18 version of gtk.

the little script does that with vmware servers console.
there might be other ways to do thi and then you mouse will work properly.


follow the links in this thread to read up on it
[http://ubuntuforums.org/showthread.php?t=1298781](http://ubuntuforums.org/showthread.php?t=1298781)

[http://communities.vmware.com/thread/235572?tstart=0](http://communities.vmware.com/thread/235572?tstart=0)
> rustynail 7 posts since
Jun 25, 2008
7. Re: Serious Problem with KDE4 and Vmware Server (plugin) Oct 20, 2009 2:27 AM
in response to: F4bi1

[http://www.pclinuxos.com/index.php?option=com_smf&Itemid=26&topic=63219.0](http://www.pclinuxos.com/index.php?option=com_smf&Itemid=26&topic=63219.0)

Apparently there is some sort of change in these packages that cause problems with the plugin. This problem is effected by Kubuntu 9.10 as well (after all updates).

Apparently rolling back fixes the mouse focus problem.

gtk+2.0 (version 2.18.1-1pclos2009) downgraded to version 2.16.6-3pclos2009
libgdk_pixbuf2.0_0 (version 2.18.1-1pclos2009) downgraded to version 2.16.6-3pclos2009
libgtk+-x11-2.0_0 (version 2.18.1-1pclos2009) downgraded to version 2.16.6-3pclos2009
libgtk+2.0_0 (version 2.18.1-1pclos20092.16.6-3pclos2009) downgraded to version 2.16.6-3pclos2009

However I think your problem is something else. In Ubuntu -> Ubuntu a down arrow activates the "print screen" or whatever activate the screen capture tool. There is a quick fix floating around the net for the remote Ubuntu client (probably all Debian).


Re: Serious Problem with KDE4 and Vmware Server (plugin) Oct 20, 2009 3:25 AM
in response to: rustynail
Click to view rustynail's profile Novice rustynail 7 posts since
Jun 25, 2008
8. Re: Serious Problem with KDE4 and Vmware Server (plugin) Oct 20, 2009 3:25 AM
in response to: rustynail

Here is a temporary solution:

+#!/bin/bash ################################################################################ # Call VMWare Server's Remote Console in a clean GTK setup. ################################################################################ # Clean GTK setup for VMWare export VMWARE_USE_SHIPPED_GTK=yes # Find console executable in Firefox plugins. vmrc="$(find "$HOME/.mozilla/firefox" -name vmware-vmrc -type f -perm -111 | tail -1)" || exit 1 set -x cd "$(dirname "$vmrc")" && "$vmrc" -h 127.0.0.1:8333+



---

### Post by doug-M on 2009-11-01
I am using that script. That is what was failing to find the libraries. I managed to fix the script by adding an LD_LIBRARY_PATH.

However even with using that script mine is still broken.
I also tried:
export VMWARE_USE_SHIPPED_GTK=force
  (instead of =yes)

I'm using a fresh install of 2.6.31-14-generic x86_64 GNU/Linux and VMware-server-2.0.2-203138.x86_64 installed using the script vmware-server-2.0.x-kernel-2.6.31-14-install.sh

Current behavior:
ctrl-alt-ins - no response from guest
ctrl-alt-del - no response from guest
ctrl-alt-. - (the . and del key on the numeric keypad) does work!
   (BUT of course this is a a laptop and only when I am docked to I have a numeric keypad, so I'll be unable to login to a guest most of the time).

Sometimes it comes up in 640x480 (well it did once just now, not sure why), in which case the mouse seems to work.
If it comes up in the normal 1024x768 then the mouse only works in the upper left corner (presumably 640x768 ).

---

### Post by sdowney717 on 2009-11-01
i had the exact same mouse problem. 640 by 480 is all you can go unless you can get it to use the other gtk.

now i can run full screen and the mouse is fine all the way to all the screen edges.
this problem is also in vmware server!
[http://www.rootloot.de/blog/vmware_in_ubuntu_karmic](http://www.rootloot.de/blog/vmware_in_ubuntu_karmic)
>  Vmware in ubuntu karmic
09. Oct 2009
2

After recently upgrading to Ubuntu 9.10 Karmic Beta I noticed some problems when installing VMware Workstation or VMware Player. After installing and following the steps mentioned in the VMware forums to compile the modules for the new kernel, the Application finally started.

However, there still seems to be a problem with mouse and keyboard focusing in the guest OS. Apperently this is caused by a new version of GTK+. The good news is, that newer Versions of VMware ship with their own compatible version GTK+.

In order to use these shiped versions, just set the according environment variable

export VMWARE_USE_SHIPPED_GTK=yes
 or
export VMWARE_USE_SHIPPED_GTK=force

You may append this to /etc/vmware/bootstrap for example to automate the setting before starting VMware Workstation or VMware Player. The ony downside of this sollution is that your application now does not use the system default GTK+ style, so it might pop out a bit from your other windows.

Edit: It seems as this has been fixed with Version 6.5.3 of VMware Workstation. 

---

### Post by doug-M on 2009-11-01
Alright I think I have a partial solution, as I mentioned earlier all the scripts I have seen for launching the web console do not help me.

I had to go into:
/home/username/.mozilla/firefox/df34789dfgj/extensions/VMwareVMRC@vmware.com/plugins/lib

Then edit the file:
wrapper-gtk24.sh

I added the following lines near the top:
VMWARE_USE_SHIPPED_GTK='force'
export VMWARE_USE_SHIPPED_GTK="force"

So now the mouse appears to work correctly.

However ctrl-alt-del does not work correctly.
I was expecting ctrl-alt-ins to work instead:
ctrl-alt-ins - no response from guest
ctrl-alt-del - no response from guest
ctrl-alt-. - (the . and del key on the numeric keypad) does work!
(BUT of course this is a a laptop and only when I am docked to I have a numeric keypad, so I'll be unable to login to a guest most of the time).

---

### Post by doug-M on 2009-11-01
Ah, ctrl-alt-ins has been changed to ctrl-alt-prntScrn

So on my laptop keyboard these work:
ctrl-alt-prtScrn
ctrl-alt-Fn-.  (Fn is a special key to overlay the numberic keyboard on the regular keys on a laptop. so the key > . is also Fn. (if that makes sense) )

---

### Post by fjgaude on 2009-11-01
Crazy, but **vmware player 3.0** from the vmware.com download site and it works perfectly with Ubuntu 9.10.

I downloaded the latest servers 1.0.10 and 2.0.2 and they both gave CRC errors on trying to extract them. I feel that both of these likely have the same update code installed within them to run 9.10 without issue. But, why the CRC error? Can't say.

And I noticed with **player 3.**0 you can create VMs... I think this may be a new thing for players, eh?

---

### Post by sdowney717 on 2009-11-02
hi doug, i tried modifying my firefox file and that does work for me also.

the developers ought to somehow do this for us all, instead we have to pull out our hair figuring this out. this is a quality of user experience issue.

---

### Post by doug-M on 2009-11-02
I just realized all sorts of other key mappings in the VM seem to be off.

Down arrow opens the start menu.
PgUp is /
etc

---

### Post by sdowney717 on 2009-11-03
the arrow keys work off the numeric keypad, just turn off numlock.
you might be able to reassign these keys in the windows vm.

---

### Post by mtschaef on 2009-11-03
VMPlayer 3.0 worked for me.  Opened up my existing VM that was created under VMWare Server 2.02.

---

### Post by fjgaude on 2009-11-03
VMplayer 3.0 worked for me too, opening by VMs created with 1.0.9 servers.

I hope the new 1.0.10 will install on Ubuntu 9.10 the way VMplayer 3.0 does!

I think VMware site may have new downloads that fix the 9.10 issues. The reason I say this is last week the 2.0.2 and 1.0.10 downloads had CRC erros and couldn't be used, but now the same files are okay. A new download of 2.0.2 may solve all the problems everyone is having, as the Player 3.0 does.

---

### Post by doug-M on 2009-11-03
Fix for the key mapping problem:

Edit the file: /etc/vmware/config

Add the line:
xkeymap.nokeycodeMap = true

See these links for more details:

Vmware Server 2.0 breaks keyboard mapping on Ubuntu 8.10
[http://blogs.unbolt.net/index.php/brinley/2008/11/12/vmware-server-2-0-breaks-keyboard-mappin-10](http://blogs.unbolt.net/index.php/brinley/2008/11/12/vmware-server-2-0-breaks-keyboard-mappin-10)

Some keys does not work on in the guest
[http://communities.vmware.com/thread/177010](http://communities.vmware.com/thread/177010)

---

### Post by stuartsiegler on 2009-11-04
> **sdowney717 said:**
> not sure why it does not work

i put a couple screen shots in showing how it brings up a server window for the vm's.

running the shell script in a terminal window for me shows this


I also had this fail similarly, but solved it by setting and launching ff like:

```
export VMWARE_USE_SHIPPED_GTK=force; firefox [https://127.0.0.1:8333](https://127.0.0.1:8333)
```

It still throws the errors, but launches correctly *and* fixes the mouse issue

-Stuart

---

### Post by ManfredU on 2009-11-04
> **doug-M said:**
> hmm so you have no ld-library-path
sry messing with vmware breaks my shift alt and ctrl keys right now so no caps.

so i found that /usr/lib/vmware/lib/libexpat.so.0 is actually a directory not a file, so adding /usr/lib/vmware/lib/libexpat.so.0 to the ld-library-path got it farther, after adding about 6 more paths to it, some in the firefox extensions directory, allowed it to start.

unfortunately no success.

i did notice one thing, it appears to be happier in the upper left corner of the console, i saw other people mentioning they have a 640x480 window where the mouse works. that might be what is happening to me.



I had to do two things to solve these issues for me:

1. I added 'xkeymap.nokeycodeMap = true' to /etc/vmware/config. This fixed the keyboard problems.

2. The mouse issue: Just adding 'export VMWARE_USE_SHIPPED_GTK=yes' caused the library issue for me as well. The following script makes vmware use it's own GTK libs and adds the missing libraries to the LD_LIBRARY_PATH, so that they are found:

```
#!/bin/bash
################################################## ##############################
# Call VMWare Server's Remote Console in a clean GTK setup.
################################################## ##############################

# Clean GTK setup for VMWare

export VMWARE_USE_SHIPPED_GTK=yes
export GDK_NATIVE_WINDOWS=true

# Find console executable in Firefox plugins.
vmrc="$(find "$HOME/.mozilla/firefox" -name vmware-vmrc -type f -perm -111 | tail -1)"
[ -x "$vmrc" ] || exit 1

VMLIB=$(dirname "$vmrc")
VMLIB=$(dirname "$VMLIB")/lib

export LD_LIBRARY_PATH=$VMLIB/libexpat.so.0:$VMLIB/libsexymm.so.2:$VMLIB/libview.so.2:$VMLIB/libvmwarebase.so.0:$VMLIB/libvmwareui.so.0:$VMLIB/libgvmomi.so.0

set -x
cd "$(dirname "$vmrc")" && "$vmrc" -h 127.0.0.1:8333
```

This works for me. :-)

---

### Post by digital_sabine on 2009-11-09
> **ManfredU said:**
> I had to do two things to solve these issues for me:

1. I added 'xkeymap.nokeycodeMap = true' to /etc/vmware/config. This fixed the keyboard problems.

2. The mouse issue: Just adding 'export VMWARE_USE_SHIPPED_GTK=yes' caused the library issue for me as well. The following script makes vmware use it's own GTK libs and adds the missing libraries to the LD_LIBRARY_PATH, so that they are found:

```
#!/bin/bash
################################################## ##############################
# Call VMWare Server's Remote Console in a clean GTK setup.
################################################## ##############################

# Clean GTK setup for VMWare

export VMWARE_USE_SHIPPED_GTK=yes
export GDK_NATIVE_WINDOWS=true

# Find console executable in Firefox plugins.
vmrc="$(find "$HOME/.mozilla/firefox" -name vmware-vmrc -type f -perm -111 | tail -1)"
[ -x "$vmrc" ] || exit 1

VMLIB=$(dirname "$vmrc")
VMLIB=$(dirname "$VMLIB")/lib

export LD_LIBRARY_PATH=$VMLIB/libexpat.so.0:$VMLIB/libsexymm.so.2:$VMLIB/libview.so.2:$VMLIB/libvmwarebase.so.0:$VMLIB/libvmwareui.so.0:$VMLIB/libgvmomi.so.0

set -x
cd "$(dirname "$vmrc")" && "$vmrc" -h 127.0.0.1:8333
```

This works for me. :-)

This combination worked for me, too, except the VM launches in its own window and not through the web console.  I'll take what I can get though. :D

sandra

---

### Post by doug-M on 2009-11-09
> **digital_sabine said:**
> This combination worked for me, too, except the VM launches in its own window and not through the web console.  I'll take what I can get though. :D

sandra

You can use this to get the mouse problem fixed when launching from the main VMWare web console.

(change username to your account name)

/home/username/.mozilla/firefox/df34789dfgj/extensions/VMwareVMRC@vmware.com/plugins/lib

Then edit the file:
wrapper-gtk24.sh

Add the following lines near the top of the wrapper-gtk24.sh file:
```
VMWARE_USE_SHIPPED_GTK='force'
export VMWARE_USE_SHIPPED_GTK="force"
```

Note this will probably get overwritten next time you update VMWare.

---

### Post by sdowney717 on 2009-11-09
I am switching over to vmware 3 player.
you can create, edit and play vm machines 
so far i think the networking is faster than vmware server. I know this because i am streaming video over the network using tversity in xp.
there was no pain in installing it and no mouse issues

I dont think you can create snapshots, but then what you will have to do is make a copy of the vm.

---

### Post by forbzie22 on 2009-11-11
Have successfully installed vmware server.

Ive run the script to start the vmware console but nothing happens ?

Same happens when i use sudo as well, script is executable too.

Do i need to manually donload the firefox vmware plugin ? If so where from ?

$ cat ./start-VMware-console.sh 
#!/bin/bash
################################################################################
# Call VMWare Server's Remote Console in a clean GTK setup.
# Author: Holger
# URL: [http://shellack.de/info/content/vmware-server-20-console-failure](http://shellack.de/info/content/vmware-server-20-console-failure)
################################################################################

# Clean GTK setup for VMWare
export VMWARE_USE_SHIPPED_GTK=yes

# Find console executable in Firefox plugins.
vmrc="$(find "$HOME/.mozilla/firefox" -name vmware-vmrc -type f -perm -111 | tail -1)"
[ -x "$vmrc" ] || exit 1

set -x
cd "$(dirname "$vmrc")" && "$vmrc" -h 127.0.0.1:8333

laptop:~$ sh start-VMware-console.sh 
laptop:~$

---

### Post by doug-M on 2009-11-11
> **forbzie22 said:**
> 
Do i need to manually donload the firefox vmware plugin ? If so where from ?


(from memory)

Try opening the vmware server console
[http://localhost:8222/](http://localhost:8222/)

Then start a vmware machine and go to the console tab.
When you click on the console area it should prompt you to install the plugin into your browser.

---

### Post by jules98 on 2009-11-16
I have found 2 ways to fix the "mouse grab" bug:

1. Edit the VMware GTk wrapper script:

```
Open the script for editing:

~$ vi $(find ~ -name 'VMwareVMRC@vmware.com')/plugins/lib/wrapper-gtk24.sh

Add the following lines after the first blank line

# Fix "mouse grab" bug
VMWARE_USE_SHIPPED_GTK='force'
export VMWARE_USE_SHIPPED_GTK="force"

```

After that you can start Firefox and goto "https://127.0.0.1:8333"

2. Or modify the "start-VMware-console.sh" given further in this thread:

```
Replace the following line
vmrc="$(find "$HOME/.mozilla/firefox" -name vmware-vmrc -type f -perm -111 | tail -1)"

by this one:
vmrc="$(find "$HOME/.mozilla/firefox" -name vmware-vmrc -type f -perm -111 | head -1)"

```

And start the script...


The disavantage of 2nd is that it starts the web console directly, without the browser...

---

### Post by ajane on 2009-11-16
Problem in my console "Operating system not found"

I have just installed VMware _windows server 2003_ and received this error message!

My Ubuntu is release Intripid 8.10, I have got 2 processor 2*2Ghz and 4 GB Ram.

When I have created my virtual Machine, I power on the VM and install windows tools but same PB and I didn't find any subject on that one!
If you cannot help me just tell me where will I find some good information?

my computer disposition:
CD-RW/DVD-ROM Drive
Floppy Drive
160 GB Media
Filesystem(all VMware install)

Thanks.

---

### Post by RazorV on 2009-12-03
> **doug-M said:**
> Alright I think I have a partial solution, as I mentioned earlier all the scripts I have seen for launching the web console do not help me.

I had to go into:
/home/username/.mozilla/firefox/df34789dfgj/extensions/VMwareVMRC@vmware.com/plugins/lib

Then edit the file:
wrapper-gtk24.sh

I added the following lines near the top:
VMWARE_USE_SHIPPED_GTK='force'
export VMWARE_USE_SHIPPED_GTK="force"

So now the mouse appears to work correctly.

However ctrl-alt-del does not work correctly.
I was expecting ctrl-alt-ins to work instead:
ctrl-alt-ins - no response from guest
ctrl-alt-del - no response from guest
ctrl-alt-. - (the . and del key on the numeric keypad) does work!
(BUT of course this is a a laptop and only when I am docked to I have a numeric keypad, so I'll be unable to login to a guest most of the time).


Okay can I call you GOD!?!  That fixed the mouse issue perfectly.  I have been fighting with this since i don't know how long.  Thank so much for the fix!

Cheers,
Greg
Sarasota, FL

---

### Post by dcstar on 2009-12-04
> **doug-M said:**
> Fix for the key mapping problem:

Edit the file: **/etc/vmware/config**

Add the line:
**xkeymap.nokeycodeMap = true**

See these links for more details:

Vmware Server 2.0 breaks keyboard mapping on Ubuntu 8.10
[http://blogs.unbolt.net/index.php/brinley/2008/11/12/vmware-server-2-0-breaks-keyboard-mappin-10](http://blogs.unbolt.net/index.php/brinley/2008/11/12/vmware-server-2-0-breaks-keyboard-mappin-10)

Some keys does not work on in the guest
[http://communities.vmware.com/thread/177010](http://communities.vmware.com/thread/177010)

That also fixed the client keymapping issue in VMware Server 1.0.10 installs.

---

### Post by davekenny on 2009-12-27
finally..
I think the adding the changes the file under the .mozilla directory
and the changes to the .vmx file fixed vmware server 2.0.2 and karmic..well at least on my laptop..

1 machine down 1 to go..

I'm just happy that it works :):):):):):):):)

thanks

-DaveKenny

---

### Post by robertco on 2010-05-30
Post your working combination / setup / configuration

This mean
kernel version 64 or 32 bit
vmware server version 64 or 32 bit and build
guests

steps patched scripts and so on.

Thank you for sharing

R.

---

### Post by djkadu on 2011-08-16
Sry, posted on the wrong thread. can this be deleted pls

---

