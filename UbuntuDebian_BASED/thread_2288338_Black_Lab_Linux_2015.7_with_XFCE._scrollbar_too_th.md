---
title: "Black Lab Linux 2015.7 with XFCE. scrollbar too thin"
date: 2015-07-26
forum: Ubuntu/Debian BASED
---

### Post by classacted on 2015-07-26
hello,


I am currently using an ubuntu related distro, Black Lab Linux 2015.7 with XFCE, and the scrollbar on the right side is too thin for my liking.  here is what I have tried to fix this:


```

leafpad ~/.gtkrc-2.0
```



copy the following into the bottom of the file:
```

style \"scroll\"
{
    GtkScrollbar::slider-width        = 20
}


class \"*\" style \"scroll\"
```



it's still the same width, even after I have rebooted the computer.
I have also looked throughout the settings, to no avail.  I have been all over google.
any advice or expertise would be appreciated.

edit:  yes, the file survived a reboot, so it was successfully saved.

---

### Post by howefield on 2015-07-26
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by Toz on 2015-07-26
Not sure why you're escaping the quotes in a text file, but...

For gtk2 apps, add the following snippet to ~/.gtkrc-2.0:
```

style "myscrollbar"
{
     GtkScrollbar::slider-width=20
}
class "GtkScrollbar" style "myscrollbar"

```

And for gtk3 apps, add the following snippet to ~/.config/gtk-3.0/gtk-widgets.css:
```
.scrollbar {
        -GtkRange-slider-width: 20;
}

```

---

### Post by classacted on 2015-07-26
hello Toz,


IT WORKS!  I can't begin to tell you how much better the computing experience is with that wide bar. 

**Not sure why you're escaping the quotes in a text file, but...**
I was following the instruction I received from a good person from here:
[https://bbs.linuxdistrocommunity.com/discussion/984/scrollbar-too-thin](https://bbs.linuxdistrocommunity.com/discussion/984/scrollbar-too-thin)
perhaps, for some reason, his instruction doesn't work for this computer, and for certain computers (like the one he was helping me with), it didn't, but strangely, for some, it WOULD work.

also, I need to mention that I previously created the ~/.gtkrc-2.0 file as root.  that may have been an error.  all I have to go on is that it didn't work before and it does now.  I thought I had to be root to save the file because when I tried to use my regular user I received an error message 'you do not have the necessary permissions to save this file', but strangely this time that didn't happen.  I WAS able to save the file as regular user.  I hope my computer is not malfunctioning.

what is the difference between using gedit versus leafpad to make the file?  I didn't think there was any.

what is the significance of the quotes?

since I actually like the bar at a width of 40 I will add this to the post to make it easy to copy and paste for future use:
```

style "myscrollbar"
{
     GtkScrollbar::slider-width=40
}
class "GtkScrollbar" style "myscrollbar"
```

and
```

.scrollbar {
        -GtkRange-slider-width: 40;
}
```

thank you so much.

---

