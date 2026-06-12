---
title: "Configure 2nd monitor with P-5 laptop?"
date: 2009-11-02
forum: System76 Support
---

### Post by bro brian on 2009-11-02
Hello all - I want to watch hulu videos on my television using my Pangolin Performance (PAN-P5) laptop.
  Once I hook up a pc to tv converter, I have to tell the laptop that I want to use a second monitor (which is the tv). Can anyone help me on the protocol for carrying out this step?
  Any instruction is much appreciated! Bro Bri
PS..I hope I explained this in simple enough terms.

---

### Post by gamerchick02 on 2009-11-02
You should be able to hook up the monitor via HDMI or standard monitor hookup.  Then go over to your nVidia settings and set the graphics card for your setup (twinview, resolution, etc).

Compiz doesn't work for me when I have a second monitor set up, so that's just something to keep in mind.

Amy

---

### Post by bro brian on 2009-11-02
> **gamerchick02 said:**
> You should be able to hook up the monitor via HDMI or standard monitor hookup.  Then go over to your nVidia settings and set the graphics card for your setup (twinview, resolution, etc).

Compiz doesn't work for me when I have a second monitor set up, so that's just something to keep in mind.

Amy

Thanks for the instruction there, Amy. I will try this out tomorrow, and - if need be, I'll give Tom (with sys76) a call, and see if he can further explain this protocol that you've lined out.
Can you explain the steps on getting into the HDMI?

---

### Post by miniyak on 2009-11-02
If your not looking to mess with too many settings all you have to do is hook-up via vga or hdmi cable (whatever cable you have lying around, both work well as far as video is concerned) 
then press the blue "fn" key in combination with the "f7" key

if i remember correctly doing this once = twin view 
and doing it twice = only external
and a third is back to normal

---

### Post by ctsdownloads on 2009-11-02
Another option is is using a VGA cable, if your TV supports it. I use [Boxee]("http://www.boxee.tv/homepage/") with both my notebook and tower with a VGA cable. My Samsung HD Plasma does great with my Gazelle Value (gazv5) notebook's VGA port. The immediate downside is the need for audio, which I use a cable and splitter to connect direct to the TV. 

HDMI is definitely the best solution, if it works. :)

---

### Post by bro brian on 2009-11-03
> **ctsdownloads said:**
> Another option is is using a VGA cable, if your TV supports it. I use [Boxee]("http://www.boxee.tv/homepage/") with both my notebook and tower with a VGA cable. My Samsung HD Plasma does great with my Gazelle Value (gazv5) notebook's VGA port. The immediate downside is the need for audio, which I use a cable and splitter to connect direct to the TV. 

HDMI is definitely the best solution, if it works. :)

  Ok - I got it up on the tv (Hoorah). Like I said earlier, I am using a "pc to tv" converter as my tv is an analog tv. For some reason, if I try to go full screen on hulu, the picture reverts back to the lap top's lcd screen. Might be some sort of glitch. I was using the Nvidia x server settings to configure the 2nd monitor (tv) instead of the fn & f7 keys. So maybe I'll mess around with it a little more, and see if I can figure out how to get around that problem, but I did get it onto the tv.
 May I thank you all for your assistance! It great to have this support on the forums.
Bri

---

### Post by bro brian on 2009-11-19
> **miniyak said:**
> If your not looking to mess with too many settings all you have to do is hook-up via vga or hdmi cable (whatever cable you have lying around, both work well as far as video is concerned) 
then press the blue "fn" key in combination with the "f7" key

if i remember correctly doing this once = twin view 
and doing it twice = only external
and a third is back to normal

  Sorry it took me 2 weeks to get back to this. Yes, the fn & F7 keys worked good. The picture on the tv wasn't perfectly centered, however. I guess this is where the "NVIDIA X server settings" come in. I guess they both go hand in hand in a sense.

 I am looking at the tv screen as I type this. I can hardly make out the words, but it looks almost perfect when I'm viewing a movie on hulu.

 With my P-5 laptop, my sequence was:
Doing it once = only external
Doing it twice= twin view
and a third is back to normal

  Thanks for the input on this. I may never have even got it onto the tv screen without everyone's input.

---

### Post by bro brian on 2009-11-26
Just a quick follow-up post explaining the NVIDIA X server settings deal.
 
 I probably wouldn't have had to mess with the NVIDIA X server settings (found on my Pangolin Performance P-5 by going to: System>Administration>NVIDIA X server settings) had I not been trying to hook it up to my **ANALOG** tv - which has more of a "square" screen on it, and the movies were way off center on the tv screen.

  As it was, I had to go into NVIDIA X server settings>X Server Display Configuration, and - in the "Resolution" section - change the resolution of both my laptop's screen (monitor) & the ANALOG tv screen from 1280 x 800 to 1024 x 768. This made the image on my laptop much bigger, but it looked pretty good on the tv screen. When I was finished with the movie, I went back, and changed the resolution on my laptop monitor back to 1280 x 800.

Someone who is using an **LCD** or **plasma** tv will most likely not have to mess with this at all, as these newer tv's have the same dimensional "look" as the laptop's monitor. Note that my ANALOG tv has a 32 inch screen if that makes any difference.

---

### Post by gamerchick02 on 2009-11-26
> **gamerchick02 said:**
> You should be able to hook up the monitor via HDMI or standard monitor hookup.  Then go over to your nVidia settings and set the graphics card for your setup (twinview, resolution, etc).

Compiz doesn't work for me when I have a second monitor set up, so that's just something to keep in mind.

Amy

Update; I got my laptop fixed and now I have compiz on both monitors if I choose to have it hooked up.

[QUOTE=bro brian]With my P-5 laptop, my sequence was:
Doing it once = only external
Doing it twice= twin view
and a third is back to normal[/QUOTE]

I will have to try out that key combination.  Thanks for the hint!

Amy

---

### Post by samalex on 2009-11-26
I actually use my PanP5 laptop with our HDTV with Hulu quite often, and I use the VGA port on the TV instead of HDMI since audio over HDMI on Ubuntu 9.04 isn't working -- at least not on the PanP5.  

So I connect the audio cable through the earphone jack, VGA cables, then change the video settings in the nVidia Server Settings to disable the laptop LCD monitor and enable the VGA port.  Works like a champ...

If/When I move up to 9.10 hopefully audio via HDMI will work, but for me it's just as easy to do VGA since either way I'd need a separate audio cable as it stands now.

Hope this helps --


Sam

---

### Post by betrunkenaffe on 2009-11-29
> **bro brian said:**
> For some reason, if I try to go full screen on hulu, the picture reverts back to the lap top's lcd screen.

As far as I can tell, full screen goes to your main window instead of staying on the one you are currently on when you hit the button.

Swap the main window (in nVidia settings), your menu will move but should be able to full screen.

---

