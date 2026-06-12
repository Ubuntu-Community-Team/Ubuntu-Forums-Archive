---
title: "So I'm Building a Custom Handheld..."
date: 2007-10-14
forum: The Cafe
---

### Post by klange on 2007-10-14
I've been thinking about this for a while and cooked up a parts list Friday night.
Parts:
[7" TFT 800x480 touchscreen LCD](http://cgi.ebay.com/_W0QQitemZ180167156098QQcmdZViewItem) - $200
[VIA PicoITX 4"x3" Mobo w/ 1Ghz x86-compatible processor](http://www.logicsupply.com/products/px10000g) - $230
[1gb DDR2 RAM stick](http://www.newegg.com/Product/Product.aspx?Item=N82E16820134129) - $28
[picoPSU-120 120W, 12v DC-DC power supply](http://www.mini-box.com/picoPSU-120-power-kit?sc=8&category=13) - $55
[120gb SATA notebook drive](http://www.newegg.com/Product/Product.aspx?Item=N82E16822149065) - $68
[TrendNet WiFi-G USB adapter](http://www.newegg.com/Product/Product.aspx?Item=N82E16833156152) - $18
[SD Card reader](http://www.newegg.com/Product/Product.aspx?Item=N82E16820162014) - $6
[12v 5A LiIon Battery Pack](http://www.spytown.com/12vpk4-5a.html?productid=12vpk4-5a&channelid=FROOG) - $60
[USB Squid 4-port USB hub](http://www.thinkgeek.com/computing/accessories/93ad/) - $20
Total Cost: $685 (USD)

Features:
- 1ghz x86-compatible processor
- Integrated 7" TFT touchscreen LCD (800x480 estimated)
- 120gb SATA hard drive
- 4 USB ports
- Integrated WiFi G
- Internal SD/MMC/MS Mini card reader
- DVI video, PS/2 keyboard + mouse, and serial-COM through external expansion cable

And what Linux distro will it run? Ubuntu of course, or my own custom distro based on Ubuntu (we'll see) I checked out all the hardware and Linux support seems to be a-ok. The plan is to remove the case from the LCD and move the LVDS so that it sits near the VGA port on the Pico board. They'll be soldiered together directly with enough gap to redirect the Ethernet port (and the LEDs) All audio ports will be redirected (I'm not sure how they're on there, but I believe they use a cable, so I should be fine) The hard drive will sit atop the heatsink on the mobo. All the USB devices will have their cases removed and will be fixed in place and wired with as little cable as possible. The last USB port (as the touchpad, wireless, and SD card reader all require one) will be attached to the USB hub.  The entire thing will be put in a case around 10"x6"x2" (probably thinner) [that's 25.5x15.2x5.1cm for everyone using superior measurement units (I envy you...)]

The case will be custom built from plastic (I have the tools to get the job done)

Anyone, on to why I'm posting this here:
I'm looking for any comments / suggestions / help you guys can offer.
(Especially when it comes to the battery, which is just a "it's the only thing I can find" sort of deal)

---

### Post by aimran on 2007-10-14
2 inches :D :D :D!

Oh well I can't complain! If you get this done kudos to you! And do you have pics of the casing planned? 

Edit: Only 1 comment - apart from your choice of distro, do you have the necessary apps to make all of it work together? Would linux support the touch screen for example. Or do you have an on screen keyboard software?

---

### Post by klange on 2007-10-14
I'm stilling working on designs, but I may have one up during the week.
The width estimate is just that - an estimate. Hopefully I can it to be a lot thinner, but it's not like I'm working with specially-made chips here.

EDIT: The LCD comes with drivers (not sure what state they're in, but I should be able to get them to work). The other devices either come with source drivers or work out of the box.
For an onscreen keyboard, I was considering writing my own (as the only one I've been able to find through minimal searching was onBoard, which is annoying in both interface and operation)

---

### Post by Steveway on 2007-10-14
How about the Gp2X?
The new version comes with a touchsreen!
It's not as powerfull but it only costs about 170$.
[http://gp2x.com/](http://gp2x.com/)

---

### Post by klange on 2007-10-14
> **Steveway said:**
> How about the Gp2X?
The new version comes with a touchsreen!
It's not as powerfull but it only costs about 170$.
[http://gp2x.com/](http://gp2x.com/)
Because the GPX is an open-source portable *gaming* device. My aim was for a cheap, custom, linux-based UMPC (which go for $1000+ and have limited Linux support)

---

### Post by ronaldstewart on 2007-11-29
I built a similar version that you are proposing in 2005.  An 'off the shelf' kludge prototype has its problems, especially quality issues.  Battery is a tough one.  Additionally, your 12V power solution will be difficult to achieve.  A step down circuit to 5V with consideration for 3.3V could bode better if you desire to achieve true performance benchmarks with a battery.  I would use polymer lithium-ion bateries.  Unless supported correctly, ACPI could be a tough task as well.  I suggest egalax evtouch screen kit for touch screen solution.  It's supported in Linux and works well.  Depending on your application there are a few screen solutions.  LVDS is a bit more difficult than TTL.  I think you could do TTL yourself with the proper screen kits.

I've built a few of these custom handhelds now and could help you steer away from possible problems and pitfalls which are bound to occur .

Just let me know.

If you need any parts or onesies chances are that I have it!

Thank you 

Ronald Stewart
Creative Director
Trinity Audio Group Inc.
9854 National Blvd. #322
Los Angeles Ca. 90034
[www.trinityaudiogroup.com](www.trinityaudiogroup.com)
[email]ronaldjstewart@gmail.com[/email]
310.733.9285

[http://youtube.com/watch?v=Wu7sMvpcmb0](http://youtube.com/watch?v=Wu7sMvpcmb0)

[http://www.youtube.com/watch?v=fiwxRSQGE7U](http://www.youtube.com/watch?v=fiwxRSQGE7U)

[http://youtube.com/watch?v=rEcFrjRf4No](http://youtube.com/watch?v=rEcFrjRf4No)

[http://youtube.com/watch?v=U04JSwWfcKI](http://youtube.com/watch?v=U04JSwWfcKI) 

pics and vids:
[http://proaudionews.blogspot.com/](http://proaudionews.blogspot.com/)

---

