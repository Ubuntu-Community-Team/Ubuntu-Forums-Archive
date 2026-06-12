---
title: "Grub2 starfield theme not used"
date: 2012-10-08
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by dino99 on 2012-10-08
I does not care that much, but grub2 does not automaticaly set the installed  starfield theme. Should not it does ?

---

### Post by cecilpierce on 2012-10-08
The new grub-emu is not working with starfield theme either and still has black on black text you can't see, have to change that, mine is:

+ boot_menu {
        left = 10%
        width = 80%
        top = 20%
        height = 50%
        item_font = "DejaVu Sans Regular 12"
        item_color = "#6ac"
        selected_item_font = "DejaVu Sans Bold 14"
        selected_item_color= "#fff"
        selected_item_pixmap_style = "blob_*.png"
        icon_height = 25
        icon_width = 25
        item_height = 26
        item_padding = 0
        item_icon_space = 0
        item_spacing = 1
        scrollbar = true
        scrollbar_width = 20
        scrollbar_thumb = "slider_*.png"
        menu_pixmap_style = "boot_menu_*.png"
}

---

### Post by funicorn on 2012-10-09
Because it can not work normally with nvidia-current, Just like plymouth. All these stuff only work with nouveau. I just tried, works ugly. If you use vt.handoff, the transition from gfxterm to plymouth is ok, however plymouth goes bad. If you don't use vt.handoff, the transition is ugly and you have to implement plymouth output with vesa mode, which makes gfxterm looks ugly.

---

