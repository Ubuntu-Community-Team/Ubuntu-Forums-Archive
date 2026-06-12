---
title: "Ubuntu 18.04 libosmesa6 depends libglapi-mesa (= 18.0.0~rc5-1ubuntu1) but 18.0.5-0ubu"
date: 2018-09-04
forum: System76 Support
---

### Post by jasonjasonjason on 2018-09-04
[COLOR=#242729][FONT=Arial]Quite a few people encounter this issue, especially those who want to use Gym and Mujoco for reinforcement learning. The installation process is frustrating, but luckily [some people]("https://askubuntu.com/questions/667416/how-can-i-safely-revert-libglapi-mesa-version") spot part of the issue[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I want to post this problem, so hopefully the Ubuntu developers could see, as the [instruction]("https://askubuntu.com/questions/1068937/how-can-i-submit-a-bug-report-on-18-04-update") doesn't lead me to any dialog box to write something.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]The problem is happened as followed:[/FONT][/COLOR]

[LIST=1]
[*][FONT=inherit]I want to use Mujoco, so I follow the installation instruction, but when I implement import mujoco_py in python3.5/3.6, it gives the following error:[/FONT]
```
[FONT=inherit]>>> import mujoco_py[/FONT]
[FONT=inherit]Import error. Trying to rebuild mujoco_py.[/FONT]
[FONT=inherit]running build_ext building 'mujoco_py.cymj' extension[/FONT]
[FONT=inherit]...[/FONT]
[FONT=inherit]/home/username/.local/lib/python3.6/site-packages/mujoco_py/gl/osmesashim.c:1:10: fatal error: GL/osmesa.h: No such file or directory #include <GL/osmesa.h>          ^~~~~~~~~~~~~[/FONT]
```
[*][FONT=inherit][Quite a few people]("https://github.com/openai/mujoco-py/issues/96") suggest to install libosmesa-dev by running sudo apt-get install libosmesa6-dev, so I tried it. But the error is:[/FONT]
```
[FONT=inherit]The following packages have unmet dependencies:libosmesa6-dev : 
[/FONT]Depends: libosmesa6 (= 18.0.0~rc5-1ubuntu1) but it is not going to be installedE: Unable to correct problems, you have held broken packages.
```
[*][FONT=inherit]Then I think this sudo apt-get install libosmesa6 would solve it, but unfortunately:[/FONT]
```
[FONT=inherit]The following packages have unmet dependencies:libosmesa6 : Depends: libglapi-mesa (= 18.0.0~rc5-1ubuntu1) but 18.0.5-0ubuntu0~18.04.1 is to be installed
E: Unable to correct problems, you have held broken packages.[/FONT]
```
[*][FONT=inherit]It looks like it's the **version** of current **libglapi-mesa** (18.0.5-0ubuntu0~18.04.1) is incompatible with what mesa really needs(18.0.0~rc5-1ubuntu1)

[/FONT]
[*][FONT=inherit]I am confused about how to downgrade it, because it seems like there are tons of packages depending on the current version of libglapi-mesa. For example, when I tried to correct the version, using sudo apt-get install libglapi-mesa=18.0.0~rc5-1ubuntu1 , the warning is going crazy:[/FONT]
```
[FONT=inherit]The following additional packages will be installed: policykit-1-gnomeThe following packages will be REMOVED:apturl cheese deja-dup gdm3 gir1.2-gst-plugins-base-1.0 
gir1.2-mutter-2gir1.2-rb-3.0 gir1.2-totem-1.0 gir1.2-webkit2-4.0 gnome-calendargnome-control-center gnome-getting-started-docs gnome-initial-setupgnome-online-accounts 
gnome-session-bin gnome-shellgnome-startup-applications gnome-todo gnome-user-docs gnome-user-guidegstreamer1.0-clutter-3.0 gstreamer1.0-gl gstreamer1.0-vaapi gvfsgvfs-backends 
gvfs-daemons gvfs-fuse libcheese-gtk25 libcheese8libclutter-1.0-0 libclutter-gst-3.0-0 libclutter-gtk-1.0-0libcogl-pango20 libcogl-path20 libcogl20 libedataserverui-1.2-2 libgl1libgl1-mesa-glx 
libglu1-mesa libglx-mesa0 libglx0 libgoa-backend-1.0-1libgstreamer-gl1.0-0 libmutter-2-0 libtotem0 libwebkit2gtk-4.0-37libyelp0 mutter nautilus nautilus-share rhythmbox-plugins 
shotwell totemtotem-plugins ubuntu-desktop ubuntu-docs ubuntu-release-upgrader-gtkubuntu-session update-manager update-notifier x11-utils xorgxserver-xephyr xserver-xorg xserver-xorg-core 
xserver-xorg-input-allxserver-xorg-input-libinput xserver-xorg-input-wacomxserver-xorg-video-all xserver-xorg-video-amdgpu xserver-xorg-video-atixserver-xorg-video-fbdev 
xserver-xorg-video-intelxserver-xorg-video-nouveau xserver-xorg-video-qxlxserver-xorg-video-radeon xserver-xorg-video-vesaxserver-xorg-video-vmware xwayland yelp zenity[/FONT]
```
[*][FONT=inherit]Now when I looked back to the Ubuntu 18.04 USB installation driver, I noticed that the version of current libglapi-mesa (**18.0.5-0ubuntu0~18.04.1**) is already there (**pre-installed**) on this Ubuntu 18.04 version. I am a newbie to Ubuntu, I already reinstall the system for few times due to following different people's post. I really hope Ubuntu team or MESA team could fix this issue soon. If you know how to solve this (other than install Ubuntu 14/16), please leave your comment, I really appreciate it![/FONT]
[/LIST]

---

