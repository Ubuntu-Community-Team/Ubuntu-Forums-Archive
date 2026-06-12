---
title: "Microsoft Habu mouse"
date: 2006-11-29
forum: The Cafe
---

### Post by Super King on 2006-11-29
[http://www.microsoft.com/hardware/gaming/productdetails.aspx?pid=092](http://www.microsoft.com/hardware/gaming/productdetails.aspx?pid=092)

The Habu is MS's newish-"gaming" mouse, made by them and Razer. Looks pretty slick, and has customizable left side buttons (ie you can swap the plate so the buttons are further up the mouse or closer to the bottom).

Anyone have one of these? I'm wondering how easily this would work with Ubuntu.

---

### Post by addicted68098 on 2006-11-29
It looks like the same as a regular Microsoft mouse only with bigger clickers (or whatever you call them) and some cosmetic changes.

---

### Post by Kristen Lucas on 2006-11-29
I like my boomslang.

When they come up with a mouse above 9600dpi then i'll change, current is 800 max.

---

### Post by Engnome on 2006-11-29
> **Kristen Lucas said:**
> current is 800 max.

Umm no it's not, my razer has 2000dpi. More than that starts getting unneccesary (unless you are pro gamer) as your hand won't be able to move so small, or you will have to turn down the sense so much it's ridicoulus.

---

### Post by Kristen Lucas on 2006-11-29
> **Engnome said:**
> Umm no it's not, my razer has 2000dpi. More than that starts getting unneccesary (unless you are pro gamer) as your hand won't be able to move so small, or you will have to turn down the sense so much it's ridicoulus.

No it does not, it has 800xoptical zoom which is worthless in a camera and wothless in a mouse.

And let's get this straight, NO mouse has a real dpi that does not multiply with 4, that is 400, 800, 1200, 1600 and the boomslang which is 9600 and it is not optical (which isn't 2000 it's 800), the optical isn't really a razer, it's just a cute copy.

---

### Post by xopher on 2006-11-29
Looks nice -- if you're 12-years-old. All those led-things are growing out of  fashion, fast.. I can't imagine what good they do. Maybe they have a healing effect? Lets you play longer without getting tired ;)

Ok, Im sure its adequate, but really, is it better than eg. the Logitechs alternative? I've just never liked m$ products, not the hardware, not the software, and yes - this answer might be a little subjective.

Oh, and did m$ buy Razer?

---

### Post by Kristen Lucas on 2006-11-29
> **xopher said:**
> Looks nice -- if you're 12-years-old. All those led-things are growing out of  fashion, fast.. I can't imagine what good they do. Maybe they have a healing effect? Lets you play longer without getting tired ;)

Ok, Im sure its adequate, but really, is it better than eg. the Logitechs alternative? I've just never liked m$ products, not the hardware, not the software, and yes - this answer might be a little subjective.

Oh, and did m$ buy Razer?

My son told me to get a boomslang, it's why i know, nag, nag nag. i eventually gave in and bought one.

It doesn't say MS on the mouse or in the documentation so i think not.

---

### Post by Beamerboy on 2006-11-29
System Requirements: Internet Connection

???

It's a frelling mouse, why is internet connection a requirement, can't you buy anything nowadays without being tracked via online registration?

Retarded in my opinion.

Paladine

---

### Post by d3v1ant_0n3 on 2006-11-29
I wonder if microsoft have released a Linux version of their (somewhat bloaty ) Intellimouse software? I like their mice, but tend to prefer Logitech. And for general use,(rather than gaming) a $10 mouse is as useful as a $50 one. I have 100-odd keys on my keyboard, don't need more on my mouse.

---

### Post by Kristen Lucas on 2006-11-29
> **d3v1ant_0n3 said:**
> I wonder if microsoft have released a Linux version of their (somewhat bloaty ) Intellimouse software? I like their mice, but tend to prefer Logitech. And for general use,(rather than gaming) a $10 mouse is as useful as a $50 one. I have 100-odd keys on my keyboard, don't need more on my mouse.

No, but no matter how many buttons, most DE's will handle it, if they don't, there is linakd.

Now that might sound really hard, but if you can follow instructions and you only have to do it once, that isn't so hard, right?

---

### Post by chaosgeisterchen on 2006-11-30
I use the Mircosoft wheel mouse optical wireless at home and its functions (scrollwheel) are fairly sufficient. For what do I need six mouse buttons when I have a keyboard and the infinite keyboard shortcut options that KDE provide?

---

### Post by dbbolton on 2006-11-30
the blueprint for the habu was actually just a tracing of a hammerhead shark.

"that has to be true. i mean, it's on the internet."

---

### Post by H0PE on 2009-04-27
I got this mouse and I would appreciate any help in order to get the maximum refresh rate out of this mouse under linux.

I know, I dont see any linux drivers :(

Any gamer tweaks you aware of guys?
What gamers do with special hardware such as this under linux if no drivers available? :S

---

### Post by Methuselah on 2009-04-27
When I was a couple years younger and stupider I bought a microsoft intellimouse. It died within a short time and I then swore off all microsoft hardware.

---

### Post by faopvnc on 2009-04-30
> **H0PE said:**
> I got this mouse and I would appreciate any help in order to get the maximum refresh rate out of this mouse under linux.

I've only just ordered this mouse, don't have it yet. So none of this is based on anything other than what other people have said. First, it looks like everyone recommends you very much want to be sure to update the firmware to the latest 2.03 from Razer's website. The official reflashing process is apparently involved and painful, and requires a 32-bit Windows machine. But it works alright if you follow the instructions exactly and don't make any sort of unreversable (seriously!) mistake like plugging the mouse in before installing the drivers (unreversable on that copy of Windows, not unreversable to your mouse).

I suspect that once you set the polling rate (that's what you're looking for?) in a profile, it should store it on-board and always use that polling rate no matter what it's plugged into. So it should be possible to set and save it at 1000 Hz on a windows machine and then the mouse should carry that setting with it no matter what you plug it into, including your Linux box. But I'm not sure about this -- the onboard memory might only be storage for the drivers, in which case profiles will not have any effect unless razer drivers are present.

[Razertool]("http://razertool.sourceforge.net/") 0.0.7 supports the Habu apparently, letting you adjusting the DPI and Hz in the on-board profile and also lets you upgrade the firmware, though I'm not sure how solid the Habu firmware upgrading support is. Though if it does work, it's probably a lot nicer than using the Windows flasher sounds to be. And it seems odd that someone would write a Linux utility for adjusting the profile's stored polling frequency if it didn't have any effect under Linux, so I'm guessing this does work and would be the easiest method for you.

And finally, if you google [linux mouse polling]("http://www.google.com/search?q=linux+mouse+polling"), it looks like you can set the polling rate as an option to the usbhid module, without having to care about what specific mouse you own at all. Remember to convert from polling rate to polling delay if you're doing it this way (so 1ms is 1000Hz and 2ms is 500Hz).

Good luck, and I hope it's an enjoyable mouse since I'll have one soon too!

EDIT: I've received my MS Habu, updated the firmware, and it does indeed apply profile settings independent of the drivers. So if you set the polling rate (and any other preferences you like) in Windows (or with Razertool), it will save them to the selected profile and will apply them when you plug in the mouse on any other computer/OS. If you use a profile other than number 1, the unlabelled, round button on the bottom of the mouse seems to cycle through them, flashing the LEDs to indicate the count of the current profile.

When I plug my MS Habu, firmware v2.03, into my Linux laptop with no drivers, it maintains the 1000Hz poll rate, the 1600 DPI, the buttons mapped to DPI+/DPI- (which continue to work), and the LED settings from my Windows desktop with drivers. I haven't tried Razertool yet.

---

### Post by garythegoth on 2009-04-30
"Internet access required"

Do you have to register it?

---

