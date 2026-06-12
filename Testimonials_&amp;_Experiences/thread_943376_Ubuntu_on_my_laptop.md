---
title: "Ubuntu on my laptop"
date: 2008-10-10
forum: Testimonials &amp; Experiences
---

### Post by aaargh486 on 2008-10-10
A couple of weeks ago, I bought myself a laptop. I decided to go for a portable, small but potent one.
So I bought the Sony Vaio VGN-FZ31E. The specs are:

Intel C2D 1.66 GHz
2 GB RAM
200 GB Hard disk
Intel Wireless 4965 card
15.4" screen
nVidia GeForce 8400M GT
Intel HDA sound card

I started Windows once, but it told me to restart after 5 minutes and gave me some more ********, so I gave up and took my Ubuntu CD's.

[COLOR=green]
What worked out of the box:
[LIST]
[*]Screen resolution
[*]Sound
[*]Multimedia keys
[*]Suspend
[*]Wireless card
[*]Ethernet card
[*]CD/DVD drive
[*]Keyboard/Touchpad
[*]USB ports
[*]Wireless kill switch
[/LIST]
[/COLOR]
Thank you, Linux kernel team and Ubuntu developers to make all this work flawlessly.:guitar::guitar:

[COLOR=orange]
What worked after some minor fiddling:
[LIST]
[*][Webcam](http://wiki.mediati.org/R5u870)
[*]Microphone
[*]Bluetooth
[*]User-customizable hotkeys (using ACPI. Naturally, Sony did not provide an utility for Linux)
[*]Graphics card support (proprietary drivers :sad: )
[/LIST]
[/COLOR]

[COLOR=red]
What still doesn't work:

Altering the screen brightness. This is a flaw on nVidia's side. For some reason, they refuse to add power management to their drivers. Not Ubuntu's fault, but it is enormously annoying. This costs me 50% of my battery life and is quite hard on the eyes.

[Convincing gnome-power-manager of ACPI events. ]("https://bugs.launchpad.net/bugs/271944") I have to restart HAL after (un)plugging my AC adapter. ACPI recognizes it, HAL does, only g-p-m doesn't want for some reason. This is just a stupid software bug, but nobody seems to see my bug report.

[/COLOR]

All and all I'm really happy with my lappie and I'm really glad a lot of things works out of the box and almost everything after 30 minutes of fiddling.

---

### Post by UsTBo8U on 2008-10-11
**[[color=red]Buy Ads[/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)**Test drive our brand new real-time traffic estimator and create your campaign. Choose text, banner, or interstitial ads. Target by site, keyword, demographic. Create or upload multiple ads. **[[color=red]Sell Ads[/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)**Find out how we can help you generate more revenue from your ad space. Customize ads to match your site Approve and reject ads for your site Works alongside other ad programs [**[size=3][color=red]Make money online,now![/color][/size]**[color=#0000cc][/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)

---

### Post by koteskie on 2009-01-04
Hi,

Can you please tell me how you got the following to work ?

    * Webcam
    * Microphone
    * Bluetooth
    * User-customizable hotkeys (using ACPI. Naturally, Sony did not provide an utility for Linux)
    * Graphics card support (proprietary drivers )

I'm pretty new to linux and need some guidance on how to get my not out of the box working hardware to work.

Thx, grt. Frank

---

### Post by aaargh486 on 2009-01-04
> **koteskie said:**
> Hi,

Can you please tell me how you got the following to work ?

    * Webcam
    * Microphone
    * Bluetooth
    * User-customizable hotkeys (using ACPI. Naturally, Sony did not provide an utility for Linux)
    * Graphics card support (proprietary drivers )

I'm pretty new to linux and need some guidance on how to get my not out of the box working hardware to work.

Thx, grt. Frank

We will have to use the command-line to do this. If you have never used this before, just copy the command I post exactly as I put them here.

I assume you are using Ubuntu 8.10. Other distributions might have some files in other places, if so, post it here and we will help you further.

* Webcam

I'm afraid I can't get it to work now. The dude who fixed it, dropped his support. I might have a look at it later, but now I'm having a lot to do.

* Microphone

Easy. Open a terminal (Applications -> Accessories -> Terminal ).
In the terminal, type
```

sudo gedit /etc/modprobe.d/alsa-base

```
It'll ask for your password. A text editor will popup. Scroll completely down and insert the following line at the bottom of the file:
```

options snd-hda-intel model=vaio

```
After a reboot, everything should be working.

* Bluetooth

Doesn't it work from the start now? I don't remember tweaking anything in 8.10. But I don't use it anyways. If it doesn't wok, post it here and we'll look into it together.

* Hotkeys

The only key I changed was the S1 key. It used it to make the computer go into suspend mode. It's really easy fo me, if you care for it, open a terminal and type
```

sudo gedit /etc/acpi/events/sony-sleep

```

Change the text in the file to
```

# /etc/acpi/events/sony-sleep

event=sony/hotkey SNC 00000001 00000090
action=/etc/acpi/sleepbtn.sh 

```

That way, it should work as a suspend button.

* Graphics card

Go to System -> Administration -> Hardware drivers and Activate the recommended driver.

I hope this helps.

Kasper

---

