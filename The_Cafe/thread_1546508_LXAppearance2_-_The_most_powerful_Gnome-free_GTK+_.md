---
title: "LXAppearance2 - The most powerful Gnome-free GTK+ theme selector"
date: 2010-08-05
forum: The Cafe
---

### Post by PCMan on 2010-08-05
In gnome, you can change the look and feel by using the gnome-appearance-properties. However, if you want to do the same outside gnome, the options are editing gtkrc-2.0 file manually or to use a gtk theme switcher. LXAppearance used to be one of these tools. However, now it becomes one of the most feature-rich complete solutions for a Gnome-free environment.

Let's see some screenshots:
[IMG]http://blog.lxde.org/wp-content/uploads/2010/07/lxappearance1-480x405.png[/IMG]

[IMG]http://blog.lxde.org/wp-content/uploads/2010/08/lxappearance-colors-480x392.png[/IMG]

[IMG]http://blog.lxde.org/wp-content/uploads/2010/07/lxappearance2-480x405.png[/IMG]

[IMG]http://blog.lxde.org/wp-content/uploads/2010/07/lxappearance3-480x405.png[/IMG]

[IMG]http://blog.lxde.org/wp-content/uploads/2010/07/lxappearance4-480x405.png[/IMG]

Later, LXAppearance2  will replace LXAppearance and move to lxappearance git repository.

Main features of LXApppearance2:

   1. Depends on gtk+ only. Can work completely without gnome.
   2. Friendly and Gnome HIG compliant user interface
   3. Provides real-time preview of the selected themes
   4. Changes icon theme
   5. Changes cursor theme in a almost desktop independent way.
   6. Supports color schemes. You can change the color used by themes if the themes support gtk color scheme.
   7. Able to install/remove icon and cursor themes in a user-friendly way
   8. Provides additional options for gtk toolbars
   9. Able to turn off event sound provided by libcanberra-gtk-module.
  10. Changes default font used by gtk+ applications
  11. Although this is a LXDE component, it works perfectly well outside LXDE and it has no LXDE dependencies.

To get the latest source code in development:
```
git clone git://lxde.git.sourceforge.net/gitroot/lxde/lxappearance2
```
(This repo will become invalid once the code is moved to master branch of the original lxappearance repo.)

If you’re a happy user and you want to donate, my PayPal account is [email]pcman.tw@gmail.com[/email].

Please get it heavily tested and give some feedbacks. Patches is also welcomed.
Cheers!

---

### Post by Tibuda on 2010-08-05
Nice.  I use LXAppearance on Openbox. Thanks for the work, this new version looks amazing.

Something I miss, and I don't see on this new version, is a box to hide icons from buttons and menus. This is what I have on my ~/.gtkrc-2.0.mine:
```
gtk-button-images=0
gtk-menu-images=0
```

---

### Post by nerdy_kid on 2010-08-05
vs kde's appearance and colors modules...no thanks :D

---

### Post by Tibuda on 2010-08-05
> **nerdy_kid said:**
> vs kde's appearance and colors modules...no thanks :D

that's gnome-free too :lolflag:

---

### Post by kerry_s on 2010-08-05
thats great. now if you can give lxlauncher some love, i'd be really happy. all it needs is a transparent background instead of that blue color, so it can show what ever wallpaper or color set as the background. it could use a menu editor, like gnomes main menu editor, but that's not as important. :D

---

### Post by Lucradia on 2010-08-05
Last time I used LXappearance, I changed my looks successfully, but couldn't change the icons, so I had to edit the gtkrc-mine file directly, manually each time I changed the theme.

---

### Post by PCMan on 2010-08-06
> **Lucradia said:**
> Last time I used LXappearance, I changed my looks successfully, but couldn't change the icons, so I had to edit the gtkrc-mine file directly, manually each time I changed the theme.
If you edited gtkrc.mine file to set your icon theme, then things won't work. Your customized values will overwrite what's set by lxappearance in .gtkrc-2.0.

Please try it again. I rewrote every bit of lxappearance and focused on correctness this time. If things still don't work, I'll help you track it down.

---

### Post by PCMan on 2010-08-06
> **danielrmt said:**
> Nice.  I use LXAppearance on Openbox. Thanks for the work, this new version looks amazing.

Something I miss, and I don't see on this new version, is a box to hide icons from buttons and menus. This is what I have on my ~/.gtkrc-2.0.mine:
```
gtk-button-images=0
gtk-menu-images=0
```
Thanks. This has been done about three minutes ago. Please update from git to get it.

---

### Post by Spice Weasel on 2010-08-06
Thanks for this, I've been following LXDE a lot lately and I love LXAppearance and PCManFM. It's a great desktop environment, one thing that's stopping me from switching over though is the panel.. The config utility for it is just a pain to use.

I'm looking forward to this replacing LXAppearance, especially since most distributions mouse cursors are complicated to change without GNOME (yeah, yeah, I know update-alternatives, but that doesn't list all available options.)

---

### Post by Warpnow on 2010-08-06
That looks almost identical to the the appear setting menu in xfce.

---

### Post by andrek on 2010-08-06
This is a very handy tool, especially for folks who use light wm's like pekwm and so on.
One thing I'm really missing - fonts hinting settings. Like in the Gnome appearance tool.

---

### Post by sertse on 2010-08-06
Still needs font settings for hinting/aliasing/rgb and it;ll be perfect.

---

### Post by PCMan on 2010-08-07
Now we've got support for Openbox integration as an optional plugin.
Full blog post:
[http://blog.lxde.org/?p=788](http://blog.lxde.org/?p=788)

Screenshot:
[img]http://blog.lxde.org/wp-content/uploads/2010/08/lxappearance-obconf1-480x390.png[/img]
[img]http://blog.lxde.org/wp-content/uploads/2010/08/lxappearance-obconf2-480x390.png[/img]

---

### Post by jeffCC on 2010-09-02
Now if only this would be available for 10.04 (probably asking too much for 9.10)

---

### Post by urukrama on 2010-09-04
> **PCMan said:**
> Now we've got support for Openbox integration as an optional plugin.
Full blog post:
[http://blog.lxde.org/?p=788](http://blog.lxde.org/?p=788)

Screenshot:
[img]http://blog.lxde.org/wp-content/uploads/2010/08/lxappearance-obconf1-480x390.png[/img]
[img]http://blog.lxde.org/wp-content/uploads/2010/08/lxappearance-obconf2-480x390.png[/img]

This is really neat! I've been hoping someone would so something like this for a long time. Thanks a lot.

---

### Post by VCoolio on 2010-09-04
> **jeffCC said:**
> Now if only this would be available for 10.04 (probably asking too much for 9.10)

[seems you're out of luck](http://blog.lxde.org/?p=788):
"Note: Ubuntu 10.04 users cannot get this correctly compiled and linked due to a bug of Ubuntu 10.04. The bug will be fixed in Ubuntu 10.10."

---

### Post by samwyse on 2010-09-04
So what's in the Misc. tab?

---

### Post by jeffCC on 2010-09-08
> **VCoolio said:**
> [seems you're out of luck]("http://blog.lxde.org/?p=788"):
"Note: Ubuntu 10.04 users cannot get this correctly compiled and linked due to a bug of Ubuntu 10.04. The bug will be fixed in Ubuntu 10.10."


But if you read further down in the comments Kendall (Peppermint, Linux Mint LXDE, Linux Mint Fluxbox) got it to compile in 10.04

---

### Post by handy on 2010-09-11
Thanks PCMan. :)

I've been using LXappearance with Openbox for sometime; it looks like your new version will dramatically improve the theme management situation for many of us WM users.

GTK theme management outside of Gnome at least, has been a total pita. It is great that you have finally gone such a long way towards addressing this problem for us. :D

---

