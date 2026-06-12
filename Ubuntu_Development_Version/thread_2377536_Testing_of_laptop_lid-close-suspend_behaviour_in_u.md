---
title: "Testing of laptop lid-close-suspend behaviour in unity 18.04"
date: 2017-11-14
forum: Ubuntu Development Version
---

### Post by ventrical on 2017-11-14
Khurdish Alam

Recently Ubuntu removed code for  laptop-lid-close-suspend-behavior from gnome-settings-daemon saying it’s  buggy and creates problems when you attach a external monitor.
Bug: [https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/17161601]("https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1716160")
Changelog: [https://launchpad.net/ubuntu/+source/gnome-settings-daemon/3.26.1-0ubuntu31]("https://launchpad.net/ubuntu/+source/gnome-settings-daemon/3.26.1-0ubuntu3")

 This made unity-settings-daemon failed, so they patched back only  gsettings schema part without the code. I am yet to find regressions on  Unity because of this on my machines, so I am starting this thread.
 On Unity  laptop-lid-close-suspend-behavior is configurable. You can  do it from Unity control center unlike in Gnome-Shell where you need  tweak-tool. It is located at settings -> power-panel.
  [h=2]**How-To-Test:**[/h] 
[LIST=1]
[*]Install unity-session on fresh machine. Log in .
[*]Go to the power panel , set "when lid is closed" == "Do Nothing"
[*]Reboot. Close the laptop lid.
[/LIST]
 What happens ?
 
[LIST=1]
[*]Does it still suspend the laptop or does it simply blank the screen?
[/LIST]
 [HR][/HR] 
[LIST=1]
[*]Now change it back to  “when lid is closed” == “Suspend”`.
[*]Connect a external monitor
[*]Reboot. And login keeping external monitor open.
[*]Colse the laptop lid
[/LIST]
 What happens ?
 
[LIST=1]
[*]Does it suspend the laptop ? (External monitor will go blank)
[/LIST]
 [HR][/HR] 
[LIST=1]
[*]Install gnome-tweak-tool.
[*]sudo sed -i "s/NoDisplay=true/NoDisplay=false/g" /etc/xdg/autostart/*.desktop
[*]Reboot.
[/LIST]
 What happens ?
 
[LIST=1]
[*]Check autostart applications. Is there something like “ignore-lid-switch-tweak” auto-starting with boot for Unity session?
[*]If it is then repeat  laptop-lid-close-suspend-behavior tests.
[/LIST]
 [If we are going to use our own unity.iso, then tweak-tool won’t be there and we don’t have to deal with it.]

---

