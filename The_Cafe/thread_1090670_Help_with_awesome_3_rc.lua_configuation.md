---
title: "Help with awesome 3 rc.lua configuation"
date: 2009-03-08
forum: The Cafe
---

### Post by kernel_script on 2009-03-08
Hi, i installed **awesome 3.1.2** on my *Ubuntu 8.10* through a *PPA*, i already read the official Wiki and manpage, and also searched throughout the Web, but i still couldn't figure out how to setup the **wibox** *height* (formerly **statusbar** on the 2x series), here the beginning of my wibox session on rc.lua:

> -- {{{ Wibox
-- Create a textbox widget
mytextbox = widget({ type = "textbox", align = "right" })
-- Set the default text in textbox
mytextbox.text = "<b><small> " .. AWESOME_RELEASE .. " </small></b>"

Please, help.

---

### Post by etrash2000 on 2009-03-19
Hi, i'm also working on installing the awesome3 and had the same problem. 
I found out that the hight is set in the theme-file, not in the config file rc.lua. Check your variable "theme_path" in rc.lua to find the theme file. 

You can then change the the font size or some other relevant parameter to change the statusbar.

With regards,
etrash2000

---

### Post by kernel_script on 2009-04-01
> **etrash2000 said:**
> Hi, i'm also working on installing the awesome3 and had the same problem. 
I found out that the hight is set in the theme-file, not in the config file rc.lua. Check your variable "theme_path" in rc.lua to find the theme file. 

You can then change the the font size or some other relevant parameter to change the statusbar.

With regards,
etrash2000

Hi etrash2000, thanks for your reply, i found out it too, but still, i don't know how to add the statusbar height property on the theme file, you know of some theme that have it already set? Or just a example? So i can learn how to do it. There is something here saying "height 15", but the statusbar is far hight than that, if it is the thing, looks like it doesn't work.

---

### Post by tjwoosta on 2009-04-01
not sure if it helps you or not but when i change the text size it changes the size of the whole bar

i can make text really small and the bar gets really skinny

---

### Post by kernel_script on 2009-04-29
> **tjwoosta said:**
> not sure if it helps you or not but when i change the text size it changes the size of the whole bar

i can make text really small and the bar gets really skinny

Thanks tjwoosta : ]

I'm not using awesome anymore, if i use it again, I'll see if i can remember your tip and try it.

---

