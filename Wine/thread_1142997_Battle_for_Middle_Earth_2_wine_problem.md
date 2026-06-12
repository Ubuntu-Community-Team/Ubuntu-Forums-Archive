---
title: "Battle for Middle Earth 2 wine problem"
date: 2009-04-29
forum: Wine
---

### Post by Questioneer on 2009-04-29
Hello-
2 days ago I installed Ubuntu 9.04.
Then, I installed wine-1.0.1 from the ubuntu repositories.
Then, I put in my "The battle for Middle Earth 2" CD, and went through the installation.
Next, I loaded up the program, as it installed fine. It loaded fine, and all of the menus worked properly. In fact, everything seems to work perfectly EXCEPT when actually playing the game the entire map(minus buildings and units) is pitch black. Something is obviously wrong with the graphic settings in wine or something.

I'm wondering if I should install propitiatory video drivers. I remember having to do so in earlier versions of ubuntu, but there wasn't an option in my "Restricted Drivers" section in 9.04.

Here are my stats:
wine-1.0.1
Ubuntu 9.04
Radeon X600 graphics card, using default drivers
No wine modifications
Wine running as "Windows XP"
I get this error hundreds of times when running the game in the terminal:
```
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 269
```

Here's a screenshot of the error.
[http://img401.imageshack.us/img401/7563/gamescreenshot.png]("http://img401.imageshack.us/img401/7563/gamescreenshot.png")

Can anyone help me out with what may be wrong?

Thanks,
Questioneer

---

### Post by surj08 on 2009-04-29
I would defiatly install the drivers! Ive never had a game work in wine without them.

But sadly never used ATI drivers so maybe some one else can help you with that or you can check the website/repos

---

### Post by Questioneer on 2009-04-29
Exactly how would I install the drivers? They aren't in the Hardware Drivers application.

---

### Post by u235sentinel on 2009-04-30
> **Questioneer said:**
> Exactly how would I install the drivers? They aren't in the Hardware Drivers application.

I've had a lot of issues with ATI cards and Linux.  They have improved over the years but still I'd recommend Nvidie whenever running into problems like this.

There is a proprietary ati driver you can try out and see if it improves things a bit.   xorg-driver-fglrx I think it's called.  Perhaps this will help you out.

---

### Post by ralph.p on 2010-09-25
I have exactly the same problem using Wine 1.2, **when I disable Vertex shader** 

graka: Intel 965 mobile.

it works with:

vertex shader: hardware
pixel shader: enabled
useGLSL: disabled

but it lags anyway

---

### Post by markackerman8@gmail.com on 2011-02-13
I am trying to get BFME2 working for my first time, and keep getting the splash screen and then the freezing grey situation.   Has anyone solved this?

using 1.06 w nocd patch

Thanks, mark

---

