---
title: "desktop icons - labels"
date: 2022-03-16
forum: Ubuntu Development Version
---

### Post by Claus7 on 2022-03-16
Hello,

there are two issues I would like to mention. The first one has to do with the labels' color and text-shadow of desktop icons, and the other has to do with the labels' behavior under mouse selection/hovering.

1) text label color and shade
Under flashback, desktop icons having a white text color in combination to a light background result in a non-discernible label, whereas, under plain ubuntu the label is too shady.  

For flashback, in order to fix this (it can be done globally too I guess, but I will post a theme specific solution), go to
/usr/share/themes/your_theme/gtk-3.20/apps and as root change the file gnome-flashback.css by adding the line in bold:
> gf-icon label {
  color: white; 
  **text-shadow: 1px 1px 2px black;**
}
that way you have added a nice shade, so as to be able to discern the labels both in dark and light backgrounds.

For plain ubuntu and the extension desktopiconsng, have in mind that every time you get an update the change will be lost.
Go to /usr/share/gnome-shell/extensions/ding@rastersoft.com and at the top of the stylesheet.css you will notice:
> .file-label, label.file-label:backdrop {
[B]    text-shadow: 1px 1px 2px black; 
[/B]    color: white;
}
remove the original line of text shadow, with the one presented here.

2) text-label expansion
In both cases of ubuntu, when the desktop icon is selected, there isn't the ability to see the entire label of the file/folder, if that expands in more that two lines. The rest remains hidden. On the contrary, if nemo desktop is chosen in order to handle the desktop, the expansion of label text happens both on mouse hovering and selection. 

Regards!

---

### Post by RogerDavis on 2022-06-20
I don't suppose it could be so simple to change the actual text color as to change "color: white;" to " color: black; "   ?

---

### Post by Claus7 on 2022-06-20
Hello,

> **RogerDavis said:**
> I don't suppose it could be so simple to change the actual text color as to change "color: white;" to " color: black; "   ?

yes it is. A little bit trickier is to change the background of the text color: it can be different upon hovering, selecting the text and when another window is open on desktop beside the desktop icons. I noticed for example that when trying to empty the recycle bin, the background text was taking a different color which I changed. The text is much easier, yet I left the default. You could experiment by changing it the way you mention, log out and back in and see the change to take effect. If you do not like it you can revert back to the original.

Regards!

---

