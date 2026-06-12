---
title: "TTY doesn't display correctly"
date: 2010-09-06
forum: System76 Support
---

### Post by Phayder92889 on 2010-09-06
Whenever my Serval Professional boots into 10.4, the TTY/Console screen is just multicolored single-pixels on the top 1/5th of the screen. Dunno how to fix this.

This is what it looks like: [http://bayimg.com/OAOMhAACm](http://bayimg.com/OAOMhAACm)

---

### Post by Phayder92889 on 2010-09-09
Bump for great justice? I used to use the TTYs to write, because VIM isn't nearly as distracting as other programs.

---

### Post by CharlesA on 2010-09-09
Running Ubuntu Desktop?

I seem to recall having a similar problem with that on a virtual machine, but I cannot recall how I fixed it.

Be a good bet to see if turning off desktop effects does anything.

Do you have any hardware drivers installed?

---

### Post by isantop on 2010-09-10
Hmm, we've had a few issues with TTYs and displays on the Serval. Perhaps this is related. You should try our fix:

Open a terminal (Applications > Accessories > Terminal) and run the following command:
```
gksudo gedit /etc/default/grub &
```
Which will open a file in the text editor. Under the line "#GRUB_GFXMODE=640x480" add
```
GRUB_GFXMODE=1600x900x32
GRUB_GFXPAYLOAD_LINUX=1600x900x32
```
Then save and close the file. Next, from that terminal, run:
```
sudo update-grub
```
and reboot. See if that fixes it.

---

### Post by Phayder92889 on 2010-09-12
> **isantop said:**
> Hmm, we've had a few issues with TTYs and displays on the Serval. Perhaps this is related. You should try our fix:

Open a terminal (Applications > Accessories > Terminal) and run the following command:
```
gksudo gedit /etc/default/grub &
```
Which will open a file in the text editor. Under the line "#GRUB_GFXMODE=640x480" add
```
GRUB_GFXMODE=1600x900x32
GRUB_GFXPAYLOAD_LINUX=1600x900x32
```
Then save and close the file. Next, from that terminal, run:
```
sudo update-grub
```
and reboot. See if that fixes it.
Did as you said, didn't work. I have everything up-to-date and current. Grub has never had an issue, just the screen that's normally covered with the ubuntu splash page and all of the virtual terminals

---

### Post by Phayder92889 on 2010-09-21
[http://ubuntuforums.org/showthread.php?t=1446132](http://ubuntuforums.org/showthread.php?t=1446132)

fixed because of that.

---

