---
title: "Can't change login screen background after installing XFCE! Please Help!"
date: 2015-11-28
forum: System76 Support
---

### Post by apteryx2 on 2015-11-28
Hi everybody,

I am using Ubuntu 14.04.4 LTS x64 and after installing xfce (**sudo apt-get install xfce4 xfce-goodies**), the login screen background turned to the XFCE default wallpaper (A blue screen with rat on the middle), I have searched on the internet and found some solutions throughout CLI:

First was to install dconf-editor and run the following commands:

[B]sudo apt-get install dconf-editor

[/B][B]sudo -i

[/B][B]sudo xhost +SI:localuser:lightdm

[/B][B]sudo su lightdm -s /bin/bash

[/B]**dconf-editor**

When I run the following commands above, I get the following error:

[B]No protocol specified

** (dconf-editor:4795): WARNING **: Could not open X display
No protocol specified
error: XDG_RUNTIME_DIR not set in the environment.

(dconf-editor:4795): Gtk-WARNING **: cannot open display: :0

[/B]I have no idea why this is happening, some other users have indicated to install Ubuntu Tweak ([http://ubuntu-tweak.com](http://ubuntu-tweak.com)), after installing, setting to a new login screen background and rebooting, the damned xfce default wallpaper persists to appear! I've already tried to reinstall lightgdm (**sudo apt-get --reinstall install lightgdm**)

I also have ran the commands to remove the white dots on the background:

[B]sudo xhost +SI:localuser:lightdm

 sudo su lightdm -s /bin/bash

 gsettings set com.canonical.unity-greeter draw-grid false[/B]

But I get the following message error:

**(process:4836): dconf-WARNING **: failed to commit changes to dconf: Error spawning command line 'dbus-launch --autolaunch=724b52f8e49049a311e8ed175656f9a5 --binary-syntax --close-stderr': Child process exited with code 1**

I don't know what to do anymore!

---

### Post by apteryx2 on 2015-11-30
I have searched through out internet and found the solution:

simply type:

$sudo xhost +

It will enable access to all users from any host.

---

