---
title: "matrix desktop"
date: 2005-06-15
forum: The Cafe
---

### Post by vega44 on 2005-06-15
i seen techtv do it on linux? does anyone know how to do that? or anything like that? like have IM chat right on the desktop or somthing crazzy like that??

---

### Post by desdinova on 2005-06-15
If you run some of the xscreensavers with the right options you can have animated desktop backgrounds...

[http://alien2thisworld.net/sitePages/tutorials/animatedWallpaper.html](http://alien2thisworld.net/sitePages/tutorials/animatedWallpaper.html)

[i] 	4) Running the screensaver as your wallpaper

 	If you have multiple versions of Xscreensaver, make sure you know where each is installed. 	I ran /usr/local/bin/xscreensaver-demo;  and browsed through the available screensavers. 	When you find one that you like, click "Settings", then "Advanced >>".  Look at the 	"command line" box to see what is actually executed. In my case, I decided on Strange. 	I messed with the settings until I like how fast it moves and how it looks.  Then, from a 	terminal execute what is printed in the "Advanced >>" command line box.
 	I typed:   ~/xscreensaver-4.13/hacks/strange -root -delay 15000 -ncolors 255&
 	I minimize the terminal window and sit back to watch.  When you close some terminals, 	the screensaver is killed with it, but you can just start up your screensaver from ~/.xinitrc (or ~/.xsession) when X starts.
 Example ~/.xinitrc:


 ~/xscreensaver-4.13/hacks/strange -root -delay 15000 -ncolors 255&
 wmcpumon &
 wmnetmon &
 fluxbox[/i]

---

### Post by sonny on 2005-06-15
Wow... that is so cool... I'm gonna try it this weekend, cuz I think it will take a while to make it work in Gnome... thanks for the link, good tweak.

---

