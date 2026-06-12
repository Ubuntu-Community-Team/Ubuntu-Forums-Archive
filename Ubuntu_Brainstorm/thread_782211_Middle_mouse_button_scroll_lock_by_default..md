---
title: "Middle mouse button scroll lock by default."
date: 2008-05-04
forum: Ubuntu Brainstorm
---

### Post by animaniac on 2008-05-04
EDIT:Apparently some people really like the paste feature,so to those people read my sugesion 2 posts down.

I seriously doubt having it as paste is more practical than scroll.
For copy/paste you already have Ctrl+c/v, Left hold + drag, and right click menu, While for scrolling only the wheel which can be a bit slow, also older 3 button mice(without the scroll wheel) would find this function very useful.


Therefore i sugesst the following change in xorg.conf by default:
[B]
From:[/B]

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection


**To:**
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "EmulateWheel"  "true"
        Option          "EmulateWheelButton"    "2"
EndSection

---

### Post by smartboyathome on 2008-05-04
I actually use it a lot for pasting. I think it is great, and also wish windows had something like this. I use the scrollwheel, home/end, arrow keys, and page up/down for scrolling.

---

### Post by animaniac on 2008-05-04
"home/end, arrow keys, and page up/down for scrolling." unfortunately they arent that good to use when working with pics. also as i mentioned, older mice.

it would atleast be good to include a checkbox in the mouse preferences to enable such an option, no? (think of the noobs).

---

### Post by smartboyathome on 2008-05-04
I do think it would be good to include a checkbox, and it doesn't currently have that function outside of web browsers and word processors. I wouldn't use it in gimp anyway, just hover over the bottom scroll for scrolling horizontally.

---

### Post by lamalex on 2008-05-04
You can take my middle click paste when you pry it from my cold dead hands! If you read peoples' lists of things they LOVE about Linux, that windows doesn't have, middle click paste is almost always one of them. Use it more and you will learn to love it. It is by far one of the handiest things ever. If you don't know, you don't need to Control+C or select copy to use copy paste, just highlight middle click. If you need to scroll, just use the wheel or the side of your touchpad, or page-up/page-down, or the other 100 ways you can scroll.

---

### Post by mirceade on 2009-01-05
There should definitely be a check box for this. I've thought until now that firefox under linux can't do that. I always use the "scroll lock" feature on windows when I want the page to auto-scroll.

---

### Post by bunty on 2009-01-06
Dont touch my middle mouse button!

This is probably THE biggest time saver in modern computing. On the rare and sad occassions I have to look at a windows machine having to fart around with of the control keys or context menus to do such a simple and recurrent task gets me screaming in 30s.

This even works beautifully between any text window and a terminal for commands and vice versa for pasting command output into forum discussions.

Pas toucher!!

---

