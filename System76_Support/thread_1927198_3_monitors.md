---
title: "3 monitors?"
date: 2012-02-17
forum: System76 Support
---

### Post by nullvariable on 2012-02-17
Love my new Gazelle, tried using the nvidia display manager to run three displays but I'm having no luck and keep crashing it. Running two displays just fine (*though I broke unity 3d, no tool bars or anything for some reason, thoughts?*) but when I try to add on a third display it freezes up if I select Twinview and refuses to load any display settings if I set it to Seperate X Screens modes. Anyone else have any luck running three displays? 

Would love to get this working!

---

### Post by nullvariable on 2012-02-17
ok so now based on what I've read twinview only works with two monitors. When I configure it with separate x servers nothing works at all. I have to reboot and clean out the xorg.conf file in order to get anywhere.

---

### Post by haqking on 2012-02-17
> **nullvariable said:**
> ok so now based on what I've read twinview only works with two monitors. When I configure it with separate x servers nothing works at all. I have to reboot and clean out the xorg.conf file in order to get anywhere.

the clue is in the word twin ;-)

Try xinerama

---

### Post by nullvariable on 2012-02-17
no dice. will only give me mirror image on the HDMI port even with setting all three to separate x displays and checking the Xinerama box for each

---

### Post by haqking on 2012-02-17
> **nullvariable said:**
> no dice. will only give me mirror image on the HDMI port even with setting all three to separate x displays and checking the Xinerama box for each

does your card support 3 displays ?

is it a single card with 3 outputs ? all hdmi ? DVI? DP ?

---

### Post by nullvariable on 2012-02-17
I have no idea if it supports all three. It's an Nvidia M560 with an HDMI output and a DVI output. The video card detects all three no problem (see attached).

As you suggested I tried the Xinearama route but it won't allow the third monitor to be run as a Separate X server (see attached).

---

### Post by haqking on 2012-02-17
so your system is a gazelle ?

that has the Nvidia GTX 460m right ?

That wont run 3 monitors

---

### Post by chriscross93 on 2012-02-17
I do not believe that the Gazelles are capable of supporting more than one external display.  Though the graphics card may support it, laptops generally only have one "media changer" to translate the graphics card output into the signals that travel over VGA,DVI,etc.

---

### Post by haqking on 2012-02-17
> **nullvariable said:**
> I have no idea if it supports all three. It's an Nvidia M560 with an HDMI output and a DVI output. The video card detects all three no problem (see attached).

As you suggested I tried the Xinearama route but it won't allow the third monitor to be run as a Separate X server (see attached).

you cant run 3 monitors on a single gpu with Nvidia

---

### Post by nullvariable on 2012-02-17
darn. well it was worth a shot :) thanks for the ideas. maybe I'll just run another machine with a connected X server. That should keep me busy all weekend :D

---

### Post by jschall1 on 2012-02-17
> **haqking said:**
> you cant run 3 monitors on a single gpu

I beg to differ.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814150574](http://www.newegg.com/Product/Product.aspx?Item=N82E16814150574)

---

### Post by haqking on 2012-02-17
> **jschall1 said:**
> I beg to differ.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814150574](http://www.newegg.com/Product/Product.aspx?Item=N82E16814150574)

beg harder.

he is using a Nvdia 560M, last time i checked no single GPU nvidia card supports 3 monitors

only a couple of Nvidia cards support 3 monitors but they are not single GPU, ATI was not mentioned here

---

### Post by jschall1 on 2012-02-17
> **haqking said:**
> beg harder.

he is using a Nvdia 560M, last time i checked no single GPU nvidia card supports 3 monitors

only a couple of Nvidia cards support 3 monitors but they are not single GPU, ATI was not mentioned here
No, ATI was not mentioned in your sweeping statement. Neither was nVidia.

---

### Post by haqking on 2012-02-17
> **jschall1 said:**
> No, ATI was not mentioned in your sweeping statement. Neither was nVidia.

the thread is about the OP Nvidia card and 3 monitors

It was not sweeping, it was in context to the thread.

But i have added it to my statement just for you ;-)

---

### Post by isantop on 2012-02-20
The GTX 590 does support triple-header mode, thus can run three monitors simultaneously on one card. That said, we don't currently offer the GTX 590, and it's a desktop card anyway.

We did recently find out that the Gazelle, Serval, and Bonobo can run two external monitors with the internal display disabled. Previously we didn't know this was possible. However, three monitors are not possible on our laptops.

---

### Post by haqking on 2012-02-20
> **isantop said:**
> **The GTX 590 does support triple-header mode, thus can run three monitors simultaneously on one card. That said, we don't currently offer the GTX 590, and it's a desktop card anyway.**




True but in context of the discussion which was a single GPU from nvidia running 3 monitors, the 590 is a Dual GPU and not single.

I mention this not to be picky but to clarify for the OP in the interest of completeness ;-)

Peace

---

