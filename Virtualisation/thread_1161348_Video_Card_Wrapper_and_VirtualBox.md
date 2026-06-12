---
title: "Video Card Wrapper and VirtualBox"
date: 2009-05-16
forum: Virtualisation
---

### Post by kc3 on 2009-05-16
Okay, I know there's no way to virtualize a GPU so running Windows does not have the greatest graphics, however I'd imagine it'd still be CAPABLE of running the same graphics (as the home system but I might be wrong) just doesn't because the lack of drivers, but does anyone have any experience using a graphic card wrapper to make the guest Windows think it's using a different video card other than mine only picking up an Intel VGA driver?

---

### Post by nolliecrooked on 2009-05-16
not unless you wanna write a .inf from scratch

---

### Post by kc3 on 2009-05-16
Well, I know there's software that'll make Windows THINK it has a different video card, if the virtualized Windows is still capable of running the Host computer's graphics (just doesn't because of driver issues) making it think it has a better video card won't make it go ahead and turn on certain things that would normaly be off? Thanks for the input, I'll probably give it a shot after I get home just out of curiosity, any other input?
 
Or are the graphics actualy not used because it's totaly incompatible, not just because of drivers?

---

### Post by nolliecrooked on 2009-05-16
> **kc3 said:**
> Well, I know there's software that'll make Windows THINK it has a different video card, if the virtualized Windows is still capable of running the Host computer's graphics (just doesn't because of driver issues) making it think it has a better video card won't make it go ahead and turn on certain things that would normaly be off? Thanks for the input, I'll probably give it a shot after I get home just out of curiosity, any other input?
 
Or are the graphics actualy not used because it's totaly incompatible, not just because of drivers?

ok, ok. what virtualisation software are you using?

---

### Post by kc3 on 2009-05-16
I'm using VirtualBox

---

### Post by nolliecrooked on 2009-05-16
> **kc3 said:**
> I'm using VirtualBox

your graphics card is ati/nvidia/intel....?

---

### Post by kc3 on 2009-05-16
It's an NVidia Geforce 8800GT

---

### Post by nolliecrooked on 2009-05-16
ummm ok. you are aware that Windows in Virtualbox only has opengl acceleration arent you?

---

### Post by kc3 on 2009-05-17
No I am not lol, I haven't used any linux tools in a long time and I'm very new to virtualization lol

---

