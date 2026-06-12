---
title: "Xubuntu 12.04 Change width of scroll bars"
date: 2012-03-25
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by bob-linux-user on 2012-03-25
How can I change the default width of the scroll bars (vertical and horizontal) in the xubuntu greybird theme please? (I would like to double the width)

---

### Post by brainwash on 2012-03-25
Hey,

just add following lines to ~/.gtkrc-2.0:

```
style "scrollbar"
{
    GtkScrollbar::slider-width = 18
}
class "Gtk*Scrollbar" style "scrollbar"

style "resize-grip"
{
    GtkWindow::resize-grip-height = 24
    GtkWindow::resize-grip-width = 24
}
class "GtkWindow*" style "resize-grip"
```

They default width of the greybird scrollbar is 9.

edit:
The resize grip area needs to be resized to match the new appearance.

---

### Post by bob-linux-user on 2012-03-25
Thanks Brainwash! It worked on most applications. However it did not work on Nautilus or Synaptic. I am not using overlay scrollbars in case that makes a difference.

---

### Post by brainwash on 2012-03-25
Just logout and login again. :)

---

### Post by bob-linux-user on 2012-03-26
Thanks Brainwash

That is a microsoft solution isn't it :-) ?

I tried logging out and in. The scrollbars on Synaptic and Nautilus are the same default width. The edit had no effect.

?

Regards

bob-linux-user

---

### Post by brainwash on 2012-03-26
Synaptic gets started with root privileges, so there has to be a copy of .gtkrc-2.0 in the /root/ dir. You can link the file to the root folder:

```
sudo ln -s /home/<username>/.gtkrc-2.0 /root/.gtkrc-2.0
```

Not sure about Nautilus though.

---

### Post by LewisTM on 2012-03-26
Nautilus and Synaptic are GTK 3.0 apps and thus will ignore .gtkrc-2.0

Not sure how to set custom styles though. Here's a nice [starting point ]("http://mail.gnome.org/archives/gtk-list/2011-March/msg00108.html")for custom GTK 3.0 config files.

I think the settings you are looking for are in /usr/share/themes/greybird/gtk-3.0/gtk-bars.css
if you can modify this file and don't mind the system-wide changes. If you go for it, you might as well modify the gtkrc file in [..]/greybird/gtk-2.0

Cheers!

---

### Post by bob-linux-user on 2012-03-30
Thanks LewisTM and Barainwash. Not looked on the forum recently as have been ill. Did not suceed with altering the files as sugested but decided to use the "Clearwaita" them which I found on Gnome look.

I think a graphical application that enables the user to tweak colors and scrollbars would be useful, especially with more people turning to xfce as has been sugested in some circles.

---

### Post by oldos2er on 2012-03-30
Thread moved to Ubuntu +1 (Precise Pangolin).

---

