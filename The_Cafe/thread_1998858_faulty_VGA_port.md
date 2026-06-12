---
title: "faulty VGA port"
date: 2012-06-07
forum: The Cafe
---

### Post by luismgl on 2012-06-07
Good day,

i have a HP g62 laptop and I wanted to connect it to a screen I have via the available VGA port. Everything connects fine but on darker colors I see horizontal lines that move in a vertical manner. I tried cleaning the port using compressed air but even after this the problem maintained. It's nothing wrong with the screen, since with other devices, including laptops, it works just fine, I even tried a new set of cables, but the problem persists. My graphics chip is fully up to date.
On that particular laptop I am using Windows 7 PRO 64 bit. 

Any ideas of what might be causing those lines and how to fix it? :)

---

### Post by mips on 2012-06-07
Boot the laptop from a linux livecd and see if the problem persists, if it does then it could potentially be faulty hardware of sorts.

---

### Post by luismgl on 2012-06-07
booted from a ubuntu 12.04 live cd and the problem was still there. This vga port is right on top of the fan, could the heat have killed this port? Or just basically it´s position, and since we are talking about an analog port, be incraesing the noise of the signal?

Anything I can do about this? 
I have a hdmi port on the laptop, but the screen is vga only, and with prices for a singal converter, I would almost buy a new screen with hdmi port.

---

### Post by sdowney717 on 2012-06-07
see if any errors show up in xorg.0.log when booting with the external vga monitor connected.

---

### Post by MisterGaribaldi on 2012-06-07
@**luismgl:** Hmm... well, by booting the system up off of a different OS installation and getting the same problem, you've just proven it's hardware.

My bet is that it's either a strictly mechanical issue (attached cable has at some point pried the connector in part up off the mobo, thus severing some connections), or it's a thermal "expansion-contraction cycle" type of failure.

In some cases, and assuming we're talking about severed connections, it is possible to re-solder whatever has been damaged. However, for the most part, you can't fix these things with a soldering job because motherboards are multi-layered, and the connection point that's damaged is not one that's visually exposed, or even if it is, something else is going to get damaged in the process of trying to service it.

If the laptop is still under warranty, you can attempt to pursue this as a warranty-related issue. If not, well... don't bother getting the laptop serviced out-of-warranty because it'll likely cost you as much as buying a new one, or cost so much that it just wouldn't be worth it.

Best of luck to you, though!

---

### Post by luismgl on 2012-06-09
Since I have a HDMI port on my laptop, a friend sugested this
[http://www.stocktogo.co.uk/belkin-dvii-female-male-adapter-bnib-p-1938.html](http://www.stocktogo.co.uk/belkin-dvii-female-male-adapter-bnib-p-1938.html)
[http://www.growing.pt/produto.php?id=46](http://www.growing.pt/produto.php?id=46)

Still he was not sure if it worked because he never tried, somehow I don't this is working out at all. What do you think?

---

### Post by mips on 2012-06-09
> **luismgl said:**
> Since I have a HDMI port on my laptop, a friend sugested this
[http://www.stocktogo.co.uk/belkin-dvii-female-male-adapter-bnib-p-1938.html](http://www.stocktogo.co.uk/belkin-dvii-female-male-adapter-bnib-p-1938.html)
[http://www.growing.pt/produto.php?id=46](http://www.growing.pt/produto.php?id=46)

Still he was not sure if it worked because he never tried, somehow I don't this is working out at all. What do you think?

Before buying anything maybe try and test it on someones lcd/tv that does have a hdmi port&cable. The problem might go further back to the output stage of the gpu etc.

---

### Post by luismgl on 2012-06-09
> **mips said:**
> Before buying anything maybe try and test it on someones lcd/tv that does have a hdmi port&cable. The problem might go further back to the output stage of the gpu etc.

the hdmi is fine, I tried on my own tv :)

---

### Post by Bandit on 2012-06-09
> **mips said:**
> Before buying anything maybe try and test it on someones lcd/tv that does have a hdmi port&cable. The problem might go further back to the output stage of the gpu etc.

This for sure.

I got an HDMI monitor, but running a VGA cable into causes horrible lines on darker colors, Its kinda causes a twinkling effect on many pixels. Very annoying. Fixed this by installing proper cable and adjusting scaling effect on the monitor via the video driver settings.

---

### Post by luismgl on 2012-06-09
> **Bandit said:**
> This for sure.

I got an HDMI monitor, but running a VGA cable into causes horrible lines on darker colors, Its kinda causes a twinkling effect on many pixels. Very annoying. Fixed this by installing proper cable and adjusting scaling effect on the monitor via the video driver settings.

As I said, my hdmi is working fine, it´s with the vga port the trouble comes. But do explain how you got yours fixed. What do you mean by "proper cable"

---

### Post by Bandit on 2012-06-09
> **luismgl said:**
> As I said, my hdmi is working fine, it´s with the vga port the trouble comes. But do explain how you got yours fixed. What do you mean by "proper cable"

I originally tried to put a DVI to HDMI connector. The resistance between the connection of the connectors caused the horrible twinkling lines on dark colors. I ordered a DVI to HDMI cable, full cable with DVI D Sub on the video card side and a standard HDMI connector for the HD Monitor. Which cleared up the connection.

---

### Post by mips on 2012-06-09
> **luismgl said:**
> the hdmi is fine, I tried on my own tv :)

Then you're good to go squire ;)

---

### Post by luismgl on 2012-06-09
> **Bandit said:**
> I originally tried to put a DVI to HDMI connector. The resistance between the connection of the connectors caused the horrible twinkling lines on dark colors. I ordered a DVI to HDMI cable, full cable with DVI D Sub on the video card side and a standard HDMI connector for the HD Monitor. Which cleared up the connection.

Did you order it online? Is so, could you share the link?
thanks

---

### Post by CharlesA on 2012-06-09
> **luismgl said:**
> Did you order it online? Is so, could you share the link?
thanks
Amazon should have those cables.

In any case, I've used hdmi --> dvi adapters with no problems.

---

### Post by Bandit on 2012-06-09
> **CharlesA said:**
> Amazon should have those cables.

In any case, I've used hdmi --> dvi adapters with no problems.

I tried that as well, tried to take the cheap way out first.. LOL but ended up having to get the cable to make it work. Interference and resistance caused the issue. Got mine from Newegg, think it was less then 10 USD.

---

### Post by CharlesA on 2012-06-09
> **Bandit said:**
> I tried that as well, tried to take the cheap way out first.. LOL but ended up having to get the cable to make it work. Interference and resistance caused the issue. Got mine from Newegg, think it was less then 10 USD.
Heh. I guess it happens.

I've been using a cheap-o HDMI cable from amazon that costs probably 4 bucks.

The adapter came with my mobo.

---

### Post by luismgl on 2012-06-10
I actually believe these lines are the product of a design flaw. The VGA port on this laptop is directly above the fan, making less than a 1 cm distance between each other, and VGA being analog, suffers from great interference from the outside, so it´s really no wonder that something like a fan (heat and vibration) cause problems. 
Here is a side view picture from my laptop
[img]http://cdn2.sulitstatic.com/images/2012/0414/032805920_032430728a4e9e069870ee5816119bd25bca760b52ff5611f.jpg[/img]

---

### Post by mips on 2012-06-10
If that's the case and you know what you are doing you could make your own shielding.

---

### Post by Bandit on 2012-06-10
> **luismgl said:**
> I actually believe these lines are the product of a design flaw. The VGA port on this laptop is directly above the fan, making less than a 1 cm distance between each other, and VGA being analog, suffers from great interference from the outside, so it´s really no wonder that something like a fan (heat and vibration) cause problems. 
Here is a side view picture from my laptop
[img]http://cdn2.sulitstatic.com/images/2012/0414/032805920_032430728a4e9e069870ee5816119bd25bca760b52ff5611f.jpg[/img]

Yes but the fans are brushless and are designed not to give off interference (marginal if any). Its true its analog port, but have you tried another VGA device with your monitor? Think your gonna find out its not the laptop or the monitor itself being faulty, but the fact your trying to run VGA (analog) into a HDMI (digital) port, sometimes they just dont work like they should. I bet good money you grab another computer running a regular VGA port and stick it to the monitor it will produce the same results. Besides you said you already tried the laptop out on the TV and it works fine. So its not the laptop.


EDIT:
Thought I would add. My ASUS 27" LCD is very nice, but it was quirky getting it to show correctly. It comes with 2 HDMI port in the back and one VGA (analog) port. My Video card has a mHDMI and 2 DVI ports. When I got the thing I didnt have any sort of HDMI cables or adapters for HDMI. I first tried a DVI cable with a DVI to VGA adapter. No dice, the monitor would scale out fine on its own, and looked usable with bright wallpapers. But you could tell something was just not right, dark wallpapers and themes were very unusable, lots of orange twinkling and stuff from pixles. Soo. I got a DVI to VGA cable from a friend. Still same effect. So round 3. I got a DVI to HDMI adapter and tried it, better, had to manually scale it up from the drivers, but still had interference. (possible just cheap adapter).. Lastly I purchased a DVI to HDMI cable from NewEgg and the video clarity was perfect and has been since. So even though my LCD has a VGA port, its not usable. Sometimes when you convert Analog to Digital and vice versa you just run into issues. Hope this helps.

- Joe

---

### Post by luismgl on 2012-06-11
The monitor is fine, I already tried with a desktop and another laptop and it was working with a nice crisp image without any lines or quality loss.
It´s really just this vga port on my laptop. 
Recently I have been looking at another alternative. A USB-VGA converter. They are about half-price when comparing to a HDMI-VGA converters, but what about the quality, I see that most only support 1600*1200?

---

