---
title: "Console shows up at bottom after running X"
date: 2010-07-11
forum: Server Platforms
---

### Post by bennyfofenny on 2010-07-11
I'm running Ubuntu Server 10.04. I installed ubuntu-desktop and then installed Nvidia graphics drivers. This caused the console resolution to go to 640x480. So I fixed it using this: [http://ubuntuforums.org/showthread.php?p=8581667](http://ubuntuforums.org/showthread.php?p=8581667). The server boots into console mode with the correct resolution, but now, after running startx and then logging out, my console is the correct resolution but shows up at the bottom of the screen. I can only see the first line of text right at the bottom. Any ideas on how to fix this?
Thanks!

edit:
I was able to fix it by adding GRUB_GFXPAYLOAD_LINUX = 1680x1050 in /etc/default/grub

---

