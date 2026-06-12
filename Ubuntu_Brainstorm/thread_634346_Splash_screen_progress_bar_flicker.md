---
title: "Splash screen progress bar flicker"
date: 2007-12-07
forum: Ubuntu Brainstorm
---

### Post by BillyRay on 2007-12-07
Hi all!

Really simple thing this - but the progress bar on the boot splash screen flickers.  Which is a bit icky.

This could probably be resolved by waiting for the video card's vsync period in which to do the drawing.

I think if a card conforms to VGA/EGA it should be something like:

  // wait for the previous retrace to finish
  do
  {
    while (inp(0x3da) & 0x8);
  }
  // wait for next retrace
  do
  {
    while (!(inp(0x3da) & 0x8));
  }
  // draw now in less than refresh rate time!
  {
  }

BUT - I am still new in the ways of the bootloader and which mode the CPU is in etc. so this may have to be handled in a different way.

It's gotta be smooth :)

Cheers,
Will.
ps : actually I quite like the non-quiet, non-splashed boot ;)
pps : I would eventually possibly get to look at doing this myself - but I don't have a lot of time on my hands.

---

### Post by smartboyathome on 2007-12-07
Try using vga=791 when booting up. It may give you a smoother look.

---

### Post by BillyRay on 2007-12-07
does that switch to a mode that actually deals with vsync or where the timing is such that  'just seems to work'?

Thanks!
Will (vga=<mode> noob)

---

### Post by smartboyathome on 2007-12-07
I don't know about vsync, but I know that I used to have that problem, but using splashy and setting grub to boot up using that parameter fixed it.

---

### Post by BillyRay on 2007-12-07
Thanks SmartBoy .. I'll look into it in more detail ..

I feel it would be nice to have it work for all modes out of the box for that professional feel - I know it's a tiny tiny thing though ;)

W.

---

