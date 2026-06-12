---
title: "A request for all ncmpcpp users (using visualizer)"
date: 2009-12-16
forum: The Cafe
---

### Post by PurposeOfReason on 2009-12-16
I moved to an ati card, so I'm not sure if that is the problem or simply the size of the terminal. Running nmcpcpp at a screen size of ~1050x600 pixels with the spectrum visualizer it takes one core (@4000mhz) 40% usage. I wouldn't expect that from a ncurses app unless the visualizer is coded poorly so could you all run some tests at similar sizes and say your usage w/ frequencies.

Oh, but on the upside the drivers are now awesome with fglrx IMO, I'm running 2 (soon to be 3) monitors in portrait mode.

---

### Post by crimesaucer on 2009-12-17
> **PurposeOfReason said:**
> I moved to an ati card, so I'm not sure if that is the problem or simply the size of the terminal. Running nmcpcpp at a screen size of ~1050x600 pixels with the spectrum visualizer it takes one core (@4000mhz) 40% usage. I wouldn't expect that from a ncurses app unless the visualizer is coded poorly so could you all run some tests at similar sizes and say your usage w/ frequencies.

Oh, but on the upside the drivers are now awesome with fglrx IMO, I'm running 2 (soon to be 3) monitors in portrait mode.

never mind, I read this wrong.

---

### Post by PurposeOfReason on 2009-12-17
Is that on the visualization screen? Because on the default song list I use almost nothing. I use my own kernel that is very minimal so I doubt it is that.

---

### Post by crimesaucer on 2009-12-17
> **PurposeOfReason said:**
> Is that on the visualization screen? Because on the default song list I use almost nothing. I use my own kernel that is very minimal so I doubt it is that.

I'm sorry..... I read your post wrong. I didn't build it with --enable-visualizer


I could re-build it that way and check it out for you it you want.

---

### Post by PurposeOfReason on 2009-12-17
It's all good, I think it's a X thing because if I have it on a non-shown workspace usage drops back to normal.

---

### Post by crimesaucer on 2009-12-17
> **PurposeOfReason said:**
> It's all good, I think it's a X thing because if I have it on a non-shown workspace usage drops back to normal.

Got it already compiling. (I wanted to see it anyways)

EDITED: just finished building, now to upload it and check it out!

---

### Post by crimesaucer on 2009-12-17
So after building/installing/configuring, I got to test this out.


First thing is that it looked pretty bad for me using the default settings from the example config.


Second thing is that it definitely USES WAY TOO MUCH CPU! My BFS patch might have helped to even out the CPU usage, but upper 30% on both cores is way to much for a crappy visualization (which I might of not done correctly?).


Here are my screenshots to show the CPU difference using htop:

With Visualization:
[[IMG]http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-ncmpcpp5-1.png[/IMG]](http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-ncmpcpp5.jpg)

Without Visualization:
[[IMG]http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-ncmpcpp-reg2.jpg[/IMG]](http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-ncmpcpp-reg2-1.jpg)

---

### Post by PurposeOfReason on 2009-12-17
Thank you, thats what I'm getting (though I use the spectrum visualizer). I really don't get what could be causing it.

---

### Post by crimesaucer on 2009-12-17
> **PurposeOfReason said:**
> Thank you, thats what I'm getting (though I use the spectrum visualizer). I really don't get what could be causing it.

I should of tried the 'spectrum' cause the default 'wave' one just wasn't worth it. Maybe I'll reinstall and configure it later to see what it looks like since I've already went back to my regular ncmpcpp package and configuration.

---

### Post by PurposeOfReason on 2009-12-17
> **crimesaucer said:**
> I should of tried the 'spectrum' cause the default 'wave' one just wasn't worth it. Maybe I'll reinstall and configure it later to see what it looks like since I've already went back to my regular ncmpcpp package and configuration.
Here's a shot to save you some trouble.

---

### Post by crimesaucer on 2009-12-17
> **PurposeOfReason said:**
> Here's a shot to save you some trouble.

Cool. It's better than the wave visualization but not cool enough for 30% for core 1 and core 2.

---

### Post by PurposeOfReason on 2009-12-17
> **crimesaucer said:**
> Cool. It's better than the wave visualization but not cool enough for 30% for core 1 and core 2.
Agreed. I'm just using the one monitor ATM, but I really want to run it large without killing CPU cycles.

---

