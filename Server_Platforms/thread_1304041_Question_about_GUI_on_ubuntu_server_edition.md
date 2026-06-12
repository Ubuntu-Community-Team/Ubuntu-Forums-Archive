---
title: "Question about GUI on ubuntu server edition"
date: 2009-10-28
forum: Server Platforms
---

### Post by Bobbywhiskey on 2009-10-28
Hi
I want to install ubuntu server edition to set up a server.
Since i am kind of new to linux i wanted to install a GUI on it and i got some question.

First, will it affect the performance of the server? Of course when i finish to set up the server i will turn off the GUI. Even turned off, can it affect the performance?

Also, i know there are a lot of GUI made to use less resources. I was wondering which one would be better, for the moment i think i would use Fluxbox. Is it easy to use/install?

If when i turn off the GUI it doesn't affect the performance, should i just stick with gnome? Will that save me a lot of time for the installation?

One last thing, when i want to install a GUI, do i just have to install the package (like gnome-desktop) and the GUI will boot the next time i restart the computer? Or is there something more to do?

Thanks.

---

### Post by druhboruch on 2009-10-28
> **Bobbywhiskey said:**
> Hi
I want to install ubuntu server edition to set up a server.
Since i am kind of new to linux i wanted to install a GUI on it and i got some question.

First, will it affect the performance of the server? Of course when i finish to set up the server i will turn off the GUI. Even turned off, can it affect the performance?

Also, i know there are a lot of GUI made to use less resources. I was wondering which one would be better, for the moment i think i would use Fluxbox. Is it easy to use/install?

If when i turn off the GUI it doesn't affect the performance, should i just stick with gnome? Will that save me a lot of time for the installation?

One last thing, when i want to install a GUI, do i just have to install the package (like gnome-desktop) and the GUI will boot the next time i restart the computer? Or is there something more to do?

Thanks.

I run several servers with GNOME and have no performance issues.  On modest hardware you will most likely not see any decrease in performance.

Once your server is setup you may add gnome-desktop, but you also may want simpler setup.

To get your desktop you will need at least xorg gnome-core and gdm.
Adding ubuntu-artwork and usplash would make your server look much nicer...

---

