---
title: "Battery life comparison of Ubuntu 12.04 and Lubuntu 12.04"
date: 2012-03-20
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by shin kai on 2012-03-20
I am a beginner with Linux. I have used Ubuntu 10.10 about a year ago for a while but only for the casual web surfing and mp3. I was impressed by the responsiveness of the OS then. I am interested in finding out the difference in battery life so far in the betas of Ubuntu 12.04 (specifically Gnome Classic without special effects) and Lubuntu 12.04.

My machine that I will be receiving soon is a used HP ProBook 5310m. It is of the Core 2 Duo generation (2.26 Ghz and 4 Gb DDR3 RAM) and has only a 4 cell battery on it. It already has Windows 7 installed on it but I wish to dual boot with Linux.

I narrow down the choices between Ubuntu 12.04 (specifically Gnome Classic w/o special effects) and Lubuntu 12.04 because I want to see if there is indeed a significant difference in battery life of the mainstream Ubuntu desktop and the lightweight derivative of Ubuntu. I have tried Lubuntu for a couple of months and while I am also impressed by the responsiveness of the Lubuntu system especially on older hardware, I have not seen anything that mentions of battery life of Lubuntu vs Ubuntu Gnome Classic.

If I were to use either of the 2 Linux OSs, I would always have the screen on lowest settings with features I do not use (ie Bluetooth and wireless network) disabled unless I need it. I am keen on knowing maximum potential battery for my new notebook because from what I have seen, HP has not provided a battery with higher capacity for this model.

If indeed the battery life on a notebook with Lubuntu 12.04 is significantly longer time length than Ubuntu 12.04 (Gnome Classic without special effects), I may decide to use Lubuntu. However, if the difference is negligible, then I would use Ubuntu with Gnome Classic (no special effects) for the customization it offers.

Any advice or inputs would be greatly appreciated. Thank you for your time.

---

### Post by MG&amp;TL on 2012-03-20
I don't think you are going to notice the difference if you are using gnome classic, that's not going to take a lot of CPU time. But try charging your laptop up all the way, and run either until it dies, and see which one takes longer. I think Lubuntu will probably take a little longer, but not much. It's more down to your personal preference, which is a good thing.

---

### Post by TenPlus1 on 2012-03-20
Try this: [http://www.planetwatt.com/](http://www.planetwatt.com/)

---

### Post by howefield on 2012-03-20
Thread moved to the "*Ubuntu +1 (Precise Pangolin)*" forum.

---

### Post by gunksta on 2012-03-20
Install and run powertop when using both Ubuntu-2D, Ubuntu-3D, Lubuntu and any other desktop / software combination you want to test.

Powertop measures how much power your computer is using. It can even break it down by application. To make the tests rigorous, I would
1) Enter each desktop from a cold boot, to make sure you are testing the system as it truly is and not some artefact from another desktop.
2) Actually do something with the desktop. Allowing the desktop to sit there idly is a test, I just don't think it is a good one. Start up an app or two and use it them, in a structured and reproducible way. Browse to a website and open an email for example.

Powertop runs from the console, so you won't see a menu entry. Obviously, a terminal and powertop should be the first two things you open on the desktop so you can watch for power spikes and power problems as you go. Because this gives you ongoing, nearly live information it is much easier to perform than starting to desktops on a fully charged battery and then running it until it dies. That is a test although one with lots of natural variance and would have to be re-run several times to have confidence in the results. In contrast, powertop re-runs itself every few seconds (I think 5 is the default) and provides a new reading, presenting you with a wealth of information, not a single number (which would be time in the battery test but wattage with powertop).

sudo apt-get install powertop

---

### Post by shin kai on 2012-03-20
Thank you all for your help. I now understand what to do to yield best results for testing. I shall test soon and see. Would using the betas be sufficient to test or may there be an update on another beta that may change the results?

---

### Post by MG&amp;TL on 2012-03-20
I doubt it now, (we should have hit feature freeze) but feel free to wait as long as you can.

---

