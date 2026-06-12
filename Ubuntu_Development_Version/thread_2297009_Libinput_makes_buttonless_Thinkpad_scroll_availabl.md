---
title: "Libinput makes buttonless Thinkpad scroll available"
date: 2015-09-30
forum: Ubuntu Development Version
---

### Post by fthx on 2015-09-30
Hi,

FYI I just installed xserver-xorg-input-libinput and it makes scrolling with trackpoint on my T440s simply work. Great !

---

### Post by fthx on 2015-10-04
Ok, I'm answering myself...

The only config I need to change (excepted those from Gnome UI settings) is clicking method. I want to do 1-2-3 fingers clicks for left-right-middle buttons, instead of right top or bottom click. To do that, place this line in a file in ~/.config/autostart :
[B]xinput set-prop "SynPS/2 Synaptics TouchPad" "libinput Click Method Enabled" 0 1

[/B]All the libinput settings are described in libinput documentation, of course.
Note that you can use only trackpoint while turning off touchpad. That is impossible with Synaptics driver since it removes buttons...

---

### Post by Luka_Pavelic on 2015-11-04
I was troubling with this problem on my ThinkPad L540 for a year now. Thank you so much. It was working immediately after installation and restart.

---

