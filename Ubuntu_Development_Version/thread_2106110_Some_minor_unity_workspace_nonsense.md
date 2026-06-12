---
title: "Some minor unity workspace nonsense"
date: 2013-01-18
forum: Ubuntu Development Version
---

### Post by mc4man on 2013-01-18
With the newer unity/compiz/gnome-control-center-unity you can remove the WS icon from the launcher, however this little 'tidbit' creates some issues.

When the icon is removed you can only have 1x1
With the icon in launcher you get 2x2, removing then adding back icon will reset 2x2

So now 1 is disallowed if the icon is present (from either vsize or hsize

Also if one opens "Appearances" with the icon in the launcher then 2x2 will be set if using anything else.

For those using/wanting 1x4 it will only allow 2x4. 

To get 1x4 then ATM you need to edit a file - /usr/share/compiz/core.xml, line 3147 & set the default to 2, as in 
<default>2</default>

(- also note that the use of sudo gedit, while in past ok is no longer a smart option, can easily be seen if you customize your user gedit, sudo gedit now uses that one.
Also seen with 
"(gedit:4751): IBUS-WARNING **: The owner of /home/doug/.config/ibus/bus is not root!"
So back to gksudo or 
sudo -i
gedit <whatever>

[https://bugs.launchpad.net/bugs/1101060](https://bugs.launchpad.net/bugs/1101060)
[https://bugs.launchpad.net/bugs/1101063](https://bugs.launchpad.net/bugs/1101063)

---

