---
title: "Background is black with a custom solid color (13.04 &amp; current 13.10"
date: 2013-05-03
forum: Ubuntu Development Version
---

### Post by mc4man on 2013-05-03
By default there is 1 solid color Background available with 2 gradient choices & they should work fine.
However is one chooses a custom color for the solid color (primary) & or a custom gradient (secondary) then very quickly they may end up with a black background & no way to change from that from the Appearances panel

The issue seems to be that customs colors are set using rgb(xxx,xxx,x) which will only produce black

To 'fix' - 
open dconf-editor > org.gnome.desktop.background & reset the primary & if altered secondary colors back to defaults, this will re-enable the 3 default blue choices.
To set a custom solid color - 
Enter the color(s) desired directly in dconf-editor using #XXXXXX, If wanting to use a gradient then set desired in secondary color & edit the color-shading-type key as desired

---

### Post by dino99 on 2013-05-03
Thanks for the memo  :)

As you speak about the "Appearances", when i open the System Settings, there are two missing icons : Appearance & Additional Drivers . I cant find why they are missing, and when i check the ubuntu-desktop meta-list, nothing is waiting for installation. So if you have an idea about that, i will take it  :P

---

### Post by mc4man on 2013-05-03
> **dino99 said:**
> Thanks for the memo  :)

As you speak about the "Appearances", when i open the System Settings, there are two missing icons : Appearance & Additional Drivers . I cant find why they are missing, and when i check the ubuntu-desktop meta-list, nothing is waiting for installation. So if you have an idea about that, i will take it  :P

If you're using a gnome session the 'Appearances' is in 'Backgrounds' & when choosing a solid color background there it will be set as #XXXXXX so will work ok.
Add. drivers is & remains in software-updater

---

### Post by dino99 on 2013-05-03
Sadly "backgrounds" only display the list of backgrounds, nothing about the Appearance option (adwaita/radiance/...)

---

### Post by mc4man on 2013-05-03
> **dino99 said:**
> Sadly "backgrounds" only display the list of backgrounds, nothing about the Appearance option (adwaita/radiance/...)
I didn't mean :Apppearances" verbatim, but in the gnome Background panel is a Colors option. It is decidedly low rent compared to the Ubuntu panel & only displays X number of colors with no customize option or gradient. 
(though the gnome session will use any manually inputed custom color & or gradient

---

