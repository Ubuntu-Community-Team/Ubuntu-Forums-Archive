---
title: "Themes in Lubuntu 12.04"
date: 2011-11-21
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by LarsKongo on 2011-11-21
Not sure where I would put this. Maybe not worth doing a new thread about.

I read earlier in the thread (or some other thread) that Adwaita/Clearlooks would be faster than Murrine and Unico engines. The default theme in Lubuntu is slower after doing some test. (It's based on my Zukitwo theme btw.) But is clearlooks really faster than my optimized Murrine theme? I got bored and tried to see how different themes would perform. Note that this is for GTK2 only. (Tested with GtkPerf.) I have currently no way of testing the GTK3 themes except watching memory usage in lxtask.

(Lower = better.)

**_Adwaita gtk3/Clearlooks gtk2_**

GtkPerf 0.40 - Starting testing: Mon Nov 21 16:16:17 2011

GtkEntry - time:  0,03
GtkComboBox - time:  0,77
GtkComboBoxEntry - time:  0,52
GtkSpinButton - time:  0,12
GtkProgressBar - time:  0,10
GtkToggleButton - time:  0,14
GtkCheckButton - time:  0,09
GtkRadioButton - time:  0,15
GtkTextView - Add text - time:  0,60
GtkTextView - Scroll - time:  0,17
GtkDrawingArea - Lines - time:  0,42
GtkDrawingArea - Circles - time:  0,68
GtkDrawingArea - Text - time:  0,39
GtkDrawingArea - Pixbufs - time:  0,03
 --- 
Total time:  4,22

**_LxDesign gtk2 (Clearlooks)_**

GtkPerf 0.40 - Starting testing: Mon Nov 21 16:16:36 2011

GtkEntry - time:  0,03
GtkComboBox - time:  0,71
GtkComboBoxEntry - time:  0,50
GtkSpinButton - time:  0,12
GtkProgressBar - time:  0,10
GtkToggleButton - time:  0,14
GtkCheckButton - time:  0,09
GtkRadioButton - time:  0,15
GtkTextView - Add text - time:  0,60
GtkTextView - Scroll - time:  0,16
GtkDrawingArea - Lines - time:  0,41
GtkDrawingArea - Circles - time:  0,73
GtkDrawingArea - Text - time:  0,39
GtkDrawingArea - Pixbufs - time:  0,03
 --- 
Total time:  4,17

**_Lubuntu-default gtk2 theme (Murrine/Unico)_**

GtkPerf 0.40 - Starting testing: Mon Nov 21 16:16:58 2011

GtkEntry - time:  0,03
GtkComboBox - time:  0,85
GtkComboBoxEntry - time:  0,45
GtkSpinButton - time:  0,11
GtkProgressBar - time:  0,44
GtkToggleButton - time:  0,67
GtkCheckButton - time:  0,58
GtkRadioButton - time:  1,25
GtkTextView - Add text - time:  0,58
GtkTextView - Scroll - time:  0,19
GtkDrawingArea - Lines - time:  0,43
GtkDrawingArea - Circles - time:  0,71
GtkDrawingArea - Text - time:  0,41
GtkDrawingArea - Pixbufs - time:  0,04
 --- 
Total time:  6,76

**_My optimized theme - Zukitwo-lxde (Murrine/Unico)_**

GtkPerf 0.40 - Starting testing: Mon Nov 21 16:17:14 2011

GtkEntry - time:  0,04
GtkComboBox - time:  0,67
GtkComboBoxEntry - time:  0,43
GtkSpinButton - time:  0,10
GtkProgressBar - time:  0,07
GtkToggleButton - time:  0,14
GtkCheckButton - time:  0,07
GtkRadioButton - time:  0,19
GtkTextView - Add text - time:  0,58
GtkTextView - Scroll - time:  0,19
GtkDrawingArea - Lines - time:  0,42
GtkDrawingArea - Circles - time:  0,70
GtkDrawingArea - Text - time:  0,40
GtkDrawingArea - Pixbufs - time:  0,03
 --- 
Total time:  4,04

I did have a GTK3 app (gedit) open too and tried to switch between themes to see if there were any memory usage difference between the Adwaita engine and the Unico engine. Result: I could find no difference at all. (Neither with the gtk2 themes.) :)

As you can see the difference between Clearlooks and my optimized Zukitwo theme is minimal, but my theme wins by a couple of milliseconds. ;) So I will say - don't consider using Adwaita and Clearlooks. Those engines are much less configurable and more amateurish (if I can say that :p ) than Murrine and Unico. And the performance difference is minimal with Murrine winning by a small shot.

**You can download my optimized theme here:** [http://lassekongo83.deviantart.com/art/Zukitwo-optimized-for-LXDE-270180608](http://lassekongo83.deviantart.com/art/Zukitwo-optimized-for-LXDE-270180608)
I've removed some pixmaps, changed some gradients and murrine settings to keep it snappy for lower end computers. Now I have currently no idea where I can submit patches and stuff to the artwork team. Can anyone point me to the right location if there is one? (I also have some ideas on how the interface can be polished and improved.)

---

