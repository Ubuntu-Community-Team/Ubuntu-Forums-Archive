---
title: "Graphics integrated/card not recognized."
date: 2012-01-31
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by MourningsEnd on 2012-01-31
I am running Ubuntu 12.04.

I have an Core i7 and Nvidia GT 525M with Optimus.

It will not recognize my graphics, and the Nvidia driver does not show up in proprietary drivers.

Help?

---

### Post by overdrank on 2012-01-31
Moved to Ubuntu +1 (Precise Pangolin)

---

### Post by 23dornot23d on 2012-02-01
I am running Ubuntu 12.04.

I have a Core i7 and Nvidia GT 540M with Optimus.

Mine stops too before having to manually get it running ......

**ironhide** really should be built in for users on this new version .... or something similar.

nouveau seems to set up .... and will run in a fashion.

Ctrl + Alt + F1 

when it seems to stop.

> apt-get update
apt-get install E17
startx enlightenment_startGets me a working desktop ..... 

I am only another user  .... so this is not the proper way to go ..... 
but may get you to a position where at least you can see a desktop
to work from.

Hopefully someone else will let you know a better way.

---

### Post by ventrical on 2012-02-01
> **MourningsEnd said:**
> I am running Ubuntu 12.04.

I have an Core i7 and Nvidia GT 525M with Optimus.

It will not recognize my graphics, and the Nvidia driver does not show up in proprietary drivers.

Help?

Go to a terminal and enter:

sudo apt-get purge nvidia*

then

sudo apt-get install nvidia-current

then

sudo update-grub

---

### Post by 23dornot23d on 2012-02-01
Interesting .... looking at what will be removed


```

keith@keith-K53SV:~$ sudo apt-get purge nvidia*
[sudo] password for keith: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'nvidia-173-updates' for regex 'nvidia*'
Note, selecting 'nvidia-current' for regex 'nvidia*'
Note, selecting 'nvidia-libvdpau-ia32' for regex 'nvidia*'
Note, selecting 'nvidia-libvdpau1' for regex 'nvidia*'
Note, selecting 'nvidia-glx-dev' for regex 'nvidia*'
Note, selecting 'nvidia-173' for regex 'nvidia*'
Note, selecting 'nvidia-96-updates-dev' for regex 'nvidia*'
Note, selecting 'nvidia-settings-updates' for regex 'nvidia*'
Note, selecting 'nvidia-libopencl1-dev' for regex 'nvidia*'
Note, selecting 'nvidia-settings' for regex 'nvidia*'
Note, selecting 'nvidia-vdpau-driver' for regex 'nvidia*'
Note, selecting 'nvidia-96-dev' for regex 'nvidia*'
Note, selecting 'nvidia-cg-toolkit' for regex 'nvidia*'
Note, selecting 'nvidia-96' for regex 'nvidia*'
Note, selecting 'nvidia-libvdpau1-ia32' for regex 'nvidia*'
Note, selecting 'nvidia-173-updates-dev' for regex 'nvidia*'
Note, selecting 'nvidia-96-updates' for regex 'nvidia*'
Note, selecting 'nvidia-180-modaliases' for regex 'nvidia*'
Note, selecting 'nvidia-current-updates' for regex 'nvidia*'
Note, selecting 'nvidia-current-updates-dev' for regex 'nvidia*'
Note, selecting 'nvidia-opencl-icd' for regex 'nvidia*'
Note, selecting 'nvidia-libvdpau' for regex 'nvidia*'
Note, selecting 'boinc-nvidia-cuda' for regex 'nvidia*'
Note, selecting 'nvidia-current-dev' for regex 'nvidia*'
Note, selecting 'nvidia-va-driver' for regex 'nvidia*'
Note, selecting 'nvidia-current-modaliases' for regex 'nvidia*'
Note, selecting 'nvidia-173-modaliases' for regex 'nvidia*'
Note, selecting 'nvidia-185-modaliases' for regex 'nvidia*'
Note, selecting 'nvidia-common' for regex 'nvidia*'
Note, selecting 'nvidia-tegra' for regex 'nvidia*'
Note, selecting 'nvidia-cuda-dev' for regex 'nvidia*'
Note, selecting 'nvidia-cuda-toolkit' for regex 'nvidia*'
Note, selecting 'nvidia-libvdpau-dev' for regex 'nvidia*'
Note, selecting 'nvidia-96-modaliases' for regex 'nvidia*'
Note, selecting 'nvidia-glx' for regex 'nvidia*'
Note, selecting 'nvidia-173-dev' for regex 'nvidia*'
Note, selecting 'vdpau-va-driver' instead of 'nvidia-va-driver'
Package nvidia-173 is not installed, so not removed
Package nvidia-173-dev is not installed, so not removed
Package nvidia-173-updates is not installed, so not removed
Package nvidia-173-updates-dev is not installed, so not removed
Package nvidia-96 is not installed, so not removed
Package nvidia-96-dev is not installed, so not removed
Package nvidia-96-updates is not installed, so not removed
Package nvidia-96-updates-dev is not installed, so not removed
Package nvidia-current-dev is not installed, so not removed
Package nvidia-current-updates is not installed, so not removed
Package nvidia-current-updates-dev is not installed, so not removed
Package nvidia-settings-updates is not installed, so not removed
Package boinc-nvidia-cuda is not installed, so not removed
Package nvidia-cg-toolkit is not installed, so not removed
The following packages were automatically installed and are no longer required:
  virtualgl acpi-call-dkms easybashgui
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  ironhide* kubuntu-desktop* nvidia-common* nvidia-current* nvidia-settings*
0 upgraded, 0 newly installed, 5 to remove and 68 not upgraded.
After this operation, 103 MB disk space will be freed.
Do you want to continue [Y/n]? y


```just thought to run it to see ..... mine is not a clean install though ... using the kubuntu one from the wayland thread ....
also added ironhide ... which I am working from as I post ..... so if I do this will the new driver work for the integrated graphics
because nothing seemed to work prior to it .... will see ..... as I am running from enlightenment .....

Removing kubuntu-deskop will not be a problem for me ...... but it may be for the original poster .....

**MourningsEnd**

 if the user gets a similar list ,,,,

[http://ubuntuforums.org/showthread.php?t=1906762](http://ubuntuforums.org/showthread.php?t=1906762)

> 
Do you want to continue [Y/n]? y
(Reading database ... 219060 files and directories currently installed.)
Removing ironhide ...
_PS0 Enabling nVidia Card Succeded.
DGPS Enabling nVidia Card Succeded.
Purging configuration files for ironhide ...
dpkg: warning: while removing ironhide, directory '/usr/share/ironhide/data' not empty so not removed.
Removing kubuntu-desktop ...
Removing nvidia-common ...
Purging configuration files for nvidia-common ...
Removing nvidia-current ...
Removing all DKMS Modules
Done.
Purging configuration files for nvidia-current ...
Removing nvidia-settings ...
Purging configuration files for nvidia-settings ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for man-db ...
keith@keith-K53SV:~$ sudo apt-get install nvidia-current
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  virtualgl acpi-call-dkms easybashgui
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  nvidia-settings
The following NEW packages will be installed:
  nvidia-current nvidia-settings
0 upgraded, 2 newly installed, 0 to remove and 68 not upgraded.
Need to get 0 B/34.4 MB of archives.
After this operation, 101 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously unselected package nvidia-current.
(Reading database ... 218788 files and directories currently installed.)
Unpacking nvidia-current (from .../nvidia-current_290.10-0ubuntu2_i386.deb) ...
Selecting previously unselected package nvidia-settings.
Unpacking nvidia-settings (from .../nvidia-settings_285.05.09-0ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up nvidia-current (290.10-0ubuntu2) ...
update-alternatives: using /usr/lib/nvidia-current/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
Loading new nvidia-current-290.10 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-12-generic
Building for architecture i686
Building initial module for 3.2.0-12-generic
Done.

nvidia_current:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-12-generic/updates/dkms/

depmod....

DKMS: install completed.
Setting up nvidia-settings (285.05.09-0ubuntu1) ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
keith@keith-K53SV:~$ 

Tried that and no difference to my setup ... still no clean start into kdm

May need to do a ......
**apt-get update**

then your commands .... but not sure why the grub-update ..... if only setting up a new nvidia driver .... the 
boot menu and listing should not change !!! ( unless there is something I am missing here )

I have opted to go for

aptitude update
aptitude safe-upgrade

To see what the current state of play is .....

It still appears to be the same PRECISE is not yet setting the screen display ,,,, to work with integrated graphics cards.

Unless someone else has sorted a way to do this other than the one 

I mentioned earlier in the thread .....

[IMG]http://img507.imageshack.us/img507/183/weylandinstalledsnapsho.jpg[/IMG]

Just lets hope Wayland gets sorted soon - as that works ok ,,,,,, just needs refining.

---

### Post by ventrical on 2012-02-01
The OP never mentioned anything about Walyland or Enlightenment.

  I am using Ubutnu Precise alpha with Unity 3D desktop. .. (no PPAs)

 Last I looked , Wayland was broken in the repos.

---

### Post by ventrical on 2012-02-01
> **23dornot23d said:**
> Interesting .... looking at what will be removed


```

keith@keith-K53SV:~$ sudo apt-get purge nvidia*
[sudo] password for keith: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'nvidia-173-updates' for regex 'nvidia*'
Note, selecting 'nvidia-current' for regex 'nvidia*'
Note, selecting 'nvidia-libvdpau-ia32' for regex 'nvidia*'
Note, selecting 'nvidia-libvdpau1' for regex 'nvidia*'
Note, selecting 'nvidia-glx-dev' for regex 'nvidia*'
Note, selecting 'nvidia-173' for regex 'nvidia*'
Note, selecting 'nvidia-96-updates-dev' for regex 'nvidia*'
Note, selecting 'nvidia-settings-updates' for regex 'nvidia*'
Note, selecting 'nvidia-libopencl1-dev' for regex 'nvidia*'
Note, selecting 'nvidia-settings' for regex 'nvidia*'
Note, selecting 'nvidia-vdpau-driver' for regex 'nvidia*'
Note, selecting 'nvidia-96-dev' for regex 'nvidia*'
Note, selecting 'nvidia-cg-toolkit' for regex 'nvidia*'
Note, selecting 'nvidia-96' for regex 'nvidia*'
Note, selecting 'nvidia-libvdpau1-ia32' for regex 'nvidia*'
Note, selecting 'nvidia-173-updates-dev' for regex 'nvidia*'
Note, selecting 'nvidia-96-updates' for regex 'nvidia*'
Note, selecting 'nvidia-180-modaliases' for regex 'nvidia*'
Note, selecting 'nvidia-current-updates' for regex 'nvidia*'
Note, selecting 'nvidia-current-updates-dev' for regex 'nvidia*'
Note, selecting 'nvidia-opencl-icd' for regex 'nvidia*'
Note, selecting 'nvidia-libvdpau' for regex 'nvidia*'
Note, selecting 'boinc-nvidia-cuda' for regex 'nvidia*'
Note, selecting 'nvidia-current-dev' for regex 'nvidia*'
Note, selecting 'nvidia-va-driver' for regex 'nvidia*'
Note, selecting 'nvidia-current-modaliases' for regex 'nvidia*'
Note, selecting 'nvidia-173-modaliases' for regex 'nvidia*'
Note, selecting 'nvidia-185-modaliases' for regex 'nvidia*'
Note, selecting 'nvidia-common' for regex 'nvidia*'
Note, selecting 'nvidia-tegra' for regex 'nvidia*'
Note, selecting 'nvidia-cuda-dev' for regex 'nvidia*'
Note, selecting 'nvidia-cuda-toolkit' for regex 'nvidia*'
Note, selecting 'nvidia-libvdpau-dev' for regex 'nvidia*'
Note, selecting 'nvidia-96-modaliases' for regex 'nvidia*'
Note, selecting 'nvidia-glx' for regex 'nvidia*'
Note, selecting 'nvidia-173-dev' for regex 'nvidia*'
Note, selecting 'vdpau-va-driver' instead of 'nvidia-va-driver'
Package nvidia-173 is not installed, so not removed
Package nvidia-173-dev is not installed, so not removed
Package nvidia-173-updates is not installed, so not removed
Package nvidia-173-updates-dev is not installed, so not removed
Package nvidia-96 is not installed, so not removed
Package nvidia-96-dev is not installed, so not removed
Package nvidia-96-updates is not installed, so not removed
Package nvidia-96-updates-dev is not installed, so not removed
Package nvidia-current-dev is not installed, so not removed
Package nvidia-current-updates is not installed, so not removed
Package nvidia-current-updates-dev is not installed, so not removed
Package nvidia-settings-updates is not installed, so not removed
Package boinc-nvidia-cuda is not installed, so not removed
Package nvidia-cg-toolkit is not installed, so not removed
The following packages were automatically installed and are no longer required:
  virtualgl acpi-call-dkms easybashgui
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  ironhide* kubuntu-desktop* nvidia-common* nvidia-current* nvidia-settings*
0 upgraded, 0 newly installed, 5 to remove and 68 not upgraded.
After this operation, 103 MB disk space will be freed.
Do you want to continue [Y/n]? y


```just thought to run it to see ..... mine is not a clean install though ... using the kubuntu one from the wayland thread ....
also added ironhide ... which I am working from as I post ..... so if I do this will the new driver work for the integrated graphics
because nothing seemed to work prior to it .... will see ..... as I am running from enlightenment .....

Removing kubuntu-deskop will not be a problem for me ...... but it may be for the original poster .....

**MourningsEnd**

 if the user gets a similar list ,,,,

[http://ubuntuforums.org/showthread.php?t=1906762](http://ubuntuforums.org/showthread.php?t=1906762)

Tried that and no difference to my setup ... still no clean start into kdm

May need to do a ......
**apt-get update**

then your commands .... but not sure why the grub-update ..... if only setting up a new nvidia driver .... the 
boot menu and listing should not change !!! ( unless there is something I am missing here )

I have opted to go for

aptitude update
aptitude safe-upgrade

To see what the current state of play is .....

It still appears to be the same PRECISE is not yet setting the screen display ,,,, to work with integrated graphics cards.

Unless someone else has sorted a way to do this other than the one 

I mentioned earlier in the thread .....

[IMG]http://img507.imageshack.us/img507/183/weylandinstalledsnapsho.jpg[/IMG]

Just lets hope Wayland gets sorted soon - as that works ok ,,,,,, just needs refining.

  I use the  sudo update-grub  just by habit now. Especially after a new kernel update.

---

### Post by 23dornot23d on 2012-02-02
> 
Last I looked , Wayland was broken in the repos.


Thats a shame .... 

I thought that was a direction Mr Shuttleworth was heading in ....  quote below from the
Wayland Wiki

> **Planned adoption**

  [[IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/7/7e/Wayland_demo_2.png/220px-Wayland_demo_2.png[/IMG]]("http://en.wikipedia.org/wiki/File:Wayland_demo_2.png")  [[IMG]http://bits.wikimedia.org/skins-1.18/common/images/magnify-clip.png[/IMG]]("http://en.wikipedia.org/wiki/File:Wayland_demo_2.png")
 Wayland demonstration
 
 
 [Ubuntu]("http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29")[Mark Shuttleworth]("http://en.wikipedia.org/wiki/Mark_Shuttleworth") announced plans to eventually replace [X]("http://en.wikipedia.org/wiki/X_Window_System") with Wayland as the primary [Ubuntu]("http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29") display server with their [Unity desktop]("http://en.wikipedia.org/wiki/Unity_%28desktop_environment%29").[[]("http://en.wikipedia.org/wiki/Wayland_%28display_server_protocol%29#cite_note-12")

[http://en.wikipedia.org/wiki/Wayland_%28display_server_protocol%29](http://en.wikipedia.org/wiki/Wayland_%28display_server_protocol%29)

from reading the wiki .... obviously for a later release then with Wayland ......

Might become a good solution to some of the graphics problems at sometime in the future then. :confused: once it gets fixed ... lets hope the OP can get up and running with the new Nvidia driver though .

---

### Post by cariboo on 2012-02-02
We won't see any real work done on Wayland until after Precise is released. This is an LTS releases, so there shouldn't be anything bleeding edge included this time around.

---

### Post by 23dornot23d on 2012-02-02
Ok cheers cariboo907 ... will look forward to the next release after Precise for some work and testing on it.

---

### Post by lucazade on 2012-02-02
Original post was about Optimus support in Precise (Nvidia+Intel hybrid support).

Answers are about wayland, E17 and wrong nvidia-* purge commands... :???:

---

### Post by ventrical on 2012-02-02
> **lucazade said:**
> Original post was about Optimus support in Precise (Nvidia+Intel hybrid support).

Answers are about wayland, E17 and wrong nvidia-* purge commands... :???:

"
and the Nvidia driver does not show up in proprietary drivers.
"

  I just seen that now..

But the nvidia purge commands were not wrong.

Can you point out where they were wrong lucazade?

---

### Post by 23dornot23d on 2012-02-02
@lucazade
look at post 3 ......

> 
I am running Ubuntu 12.04.

I have a Core i7 and Nvidia GT 540M with Optimus.

Mine stops too before having to manually get it running ......

**ironhide** really should be built in for users on this new version .... or something similar.

nouveau seems to set up .... and will run in a fashion.

Ctrl + Alt + F1 

when it seems to stop.
Ironhide is the answer because I have done it and up and running ...... 
I gave Enlightenment as a desktop .... because UNITY would not run 
( reason for mentioning wayland was that too is running on my system and I was not sure
if you - the developers had got any further along with it - as it may have been another direction to go in )

[http://linux-hybrid-graphics.blogspot.com/2011/08/ironhide-branch-first-release-including.html](http://linux-hybrid-graphics.blogspot.com/2011/08/ironhide-branch-first-release-including.html)

[IMG]http://img254.imageshack.us/img254/183/weylandinstalledsnapsho.jpg[/IMG]

My system is almost the same as the OP .... mine works ....

---

### Post by lucazade on 2012-02-03
I have optimus lappy as well, a dell l702x (nvidia 555+intel 3000, 6gb ram, 2x750gb hd, i7)... so what I would expect in this thread is the status of bumblebee / ironhide in precise.. plans for its inclusion in the distro, no OT stuff like a DE or wrong info about nvidia driver installation (nvidia driver are installed automatically via ironhide and not via restricted hardware tool...)

---

### Post by ventrical on 2012-02-03
> **lucazade said:**
> I have optimus lappy as well, a dell l702x (nvidia 555+intel 3000, 6gb ram, 2x750gb hd, i7)... so what I would expect in this thread is the status of bumblebee / ironhide in precise.. plans for its inclusion in the distro, no OT stuff like a DE or wrong info about nvidia driver installation (nvidia driver are installed automatically via ironhide and not via restricted hardware tool...)


  I stand corrected .. I am not familiar with the newer ironhide and Optimus by nvidia. I thought it was a standard install.

---

### Post by calanor on 2012-02-05
Hi,

I have an optimus enabled laptop too. The current state of optimus in linux is that its unsupported (well some hacks exist but they are no good if you are looking for battery life improvement). Your nvidia card will only be recognized if you disable Optimus from BIOS. You can reach BIOS by pressing F12, F2 some other function key (just search for it), then see if there is any option to disable Optimus and disable it. If that option is not there, I can't help you. 

If it is, cheers.

---

