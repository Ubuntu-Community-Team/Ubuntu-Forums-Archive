---
title: "Window, menu, keystrokes very slow on Unity"
date: 2014-07-05
forum: Ubuntu Development Version
---

### Post by jerrylamos on 2014-07-05
Just installed the July 4 Utopic 32 bit on 2 gHz Pentium 4 
I've got unity tweak tool  and supposedly turned window animations off.

Windows and menus open v e r y   s l o w l y.  Keystroke response is s l o w.

BTW, I've got Lubuntu  tahr in another partition running just fine, thank you.

How do I turn off the very slow jerky opening and closing of windows?  
select something, gradually opens in jerky stages gradually increasing in brightness.  Closing is the reverse

How do I get back to the ubuntu snap?  

 I'm interested in applications, not sluggish animations when they interfere with speed of operation.   I've been on Ubuntu since Dapper Drake Beta and this is the slowest response I've seen.

Thanks for any ideas.

---

### Post by grahammechanical on 2014-07-05
What video driver is being used? Ubuntu has a fall back video driver called llvmpipe. It is used when we select Recovery>Resume. It definitely has a slow response to windows opening and closing. If the graphic adapter is not capable of running Unity 3D then we get llvmpipe.

Regards.

---

### Post by jerrylamos on 2014-07-05
It's been a while since I've tried to find video  driver in use.  I looked in Xorg.0.log and saw "vesa"  and Dri2  I think.

VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01

What Unity is doing when I select a window  or menu is to show the window maybe 4 or 5 times in gradually increasing brightness.  Any way to get Unity to show the window or menu once in final brightness  instead of gradually creeping up or gradually fading away in 4 or 5 steps?

I'm no fan of XFCE I do run Lubuntu mostly checking for bugs.

I've got utopic on a netbook, notebook, and tower haven't noticed this problem but it's been a month or so since I've installed utopic on htem.

Thanks

Update - I'm using the on-board video.  The motherboard does have an AGP slot if I want to try that, else run lubuntu.

---

