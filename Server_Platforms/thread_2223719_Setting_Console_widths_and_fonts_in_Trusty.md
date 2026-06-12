---
title: "Setting Console widths and fonts in Trusty"
date: 2014-05-12
forum: Server Platforms
---

### Post by m-dw on 2014-05-12
My server has onboard VGA, and I'm running it without X.  I mostly access it over SSH, but I occasionally like to watch it boot  (e.g. after making any hardware changes), so I've connected it to an analogue port on my 2" wide-screen monitor.

Booting happens in two stages:
[LIST]
[*]First stage has what I assume to be a time in square brackets on the left margin, and the messages appear to relate to hardware detection.  This displays across the width of the screen, and doesn't wrap.
[*]Second stage is where all the services start (or fail to start) and has an OK or FAIL in square brackets on the right of the screen.  This wraps after the first square bracket, about half-way across the screen leaving OK] sitting on the next line.
[/LIST]

I've tried setting various options in /etc/default/grub modifying the following line, settling on the following.

```

GRUB_GFXPAYLOAD_LINUX=1920x1200

```

This gives me a wider console for the second stage of booting when Linux takes over, but the furst stage is messy, suggestive of 640x480.  vbeinfo suggests that 1920x1200 isn't a supported resolution and that the default resolution is 1600x1200.  Other supported text mode resolutions are 0x160 to 0x171 but I have no idea what they represent.

Is there a way of setting the console width that I'm missing?

---

