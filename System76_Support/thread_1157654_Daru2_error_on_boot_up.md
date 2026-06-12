---
title: "Daru2 error on boot up"
date: 2009-05-12
forum: System76 Support
---

### Post by bmannering on 2009-05-12
I recently updated my laptop and after trying to restart it it no longer boots up. The first thing that comes up as failed is
upsplash: Setting mode 1280x1024 failed
Then it trys to mount and everything fails. Im not too sure of what to do especially bc i have a lot of important info on my laptop i dont want to wipe it. Thanks.

---

### Post by thomasaaron on 2009-05-13
Can you boot into recovery mode? Here are instructions...

> To boot into recovery mode, restart your machine and press the "Esc" key when you see the grub countdown (i.e. grub...3...2...1...). This will bring you to a list of available kernels. Highlight the first line that has "Recovery Mode" in its title and press enter. You will then be presented with a GUI that offers you a list of options. Select "Drop to Root Shell Prompt."

If so, boot into recovery mode and try running...

> sudo dpkg-reconfigure xserver-xorg

...and choose ALL default options. No exceptions.

Then reboot your computer with...

> sudo reboot -h now

---

