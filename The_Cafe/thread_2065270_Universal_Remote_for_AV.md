---
title: "Universal Remote for A/V"
date: 2012-10-01
forum: The Cafe
---

### Post by Cool Javelin on 2012-10-01
Hello good people:

I would like a device I can attach to my computer that can control my audio/video equipment via infrared (TV, cable box, TIVO, etc.)

I have searched and searched and found very little information on this exact product so I am posting on as many forums as I belong in hopes someone can lead me to what I seek.

The method of connect to my computer is unimportant. It can use the serial port, USB, or parallel port, or even have a special plug in card.

I am hoping for a very low cost device, but my desire for flexibility is great.

My vision is to have a simple box with an IR transmitter (maybe a receiver so it can "learn" from my existing remoter) and be able to let the computer do all the work of scheduling, switching stations on the cable box, and starting recordings on the TIVO as well as be able to run macros to switch my stereo from CD to TV.

I have looked into several home brew projects but I am hoping to get something a little more professional

The Harmony/Logitech Harmony 1100 looks very attractive, ([http://www.logitech.com/en-us/remotes/universal-remotes/harmony-1100](http://www.logitech.com/en-us/remotes/universal-remotes/harmony-1100))  but is way too expensive. I would like that kind of control but without the expensive touch screen and stand alone box.

Thanks for your help,
Mark.

---

### Post by Statia on 2012-10-01
I was trying to find something similar.
I had a remote and a serial IR-receiver from an old TV-card, but after a lot of fiddling found out that (most likely) my serial port does not work.

I then came across this:

[http://www.minigadgets.nl/index.php?action=article&aid=1728&group_id=10000017&lang=NL](http://www.minigadgets.nl/index.php?action=article&aid=1728&group_id=10000017&lang=NL)

(In the unlikely event you don't speak Dutch you can use Google translate ;-) )
As you can see it's a lot cheaper. Unfortunately, it's also out of stock and been out of stock for weeks. (Does not stop them from advertising with "everything in stock")

They claim it will work on any OS without needing any drivers, as it should be recognised as a keyboard and mouse.
Even if that is true, that will have disadvantages:
- will only work for programs that have keyboard shortcuts
- will only work if that program has focus

You might however also be able to get it to work with lirc, but that might warrant a lot of fiddling.

---

### Post by dcstar on 2012-10-02
> **Cool Javelin said:**
> Hello good people:
.......
People, this is an UBUNTU support forum, not your household help page.

---

### Post by Grenage on 2012-10-02
I've got one of the Harmony remote controls (standard, not touch-screen), which was quite cheap; it's awesome.  Unfortunately the PC-based configuration is via a web GUI, designed for Windows.  That said, last time I had to configure it, I noted that someone had written a module to get it working on Linux - I just used a windows install.

---

### Post by Elfy on 2012-10-02
*Thread moved to **The Community Cafe**.*

---

### Post by JustinR on 2012-10-02
The Logitech Harmony 1100 hasn't been updated in a few years. It definitely shows its age, and it's very slow. It's also less intuitive than a regular, non-touch remote, theres a noticeable lag between button presses. I would advise against purchasing it - it seems as Logitech won't be updating it anytime soon.

---

### Post by effenberg0x0 on 2012-10-03
I have a Media Server at home (Ubuntu) running xbmc to three TVs in different rooms and 3 Streamzap USB Receivers at the top of each TV. 

The USB Receivers are automatically recognized:

```
[ 7256.462641] usb 2-1.3: new low-speed USB device number 4 using ehci_hcd
[ 7256.610651] IR NEC protocol handler initialized
[ 7256.613752] IR RC5(x) protocol handler initialized
[ 7256.618028] IR RC6 protocol handler initialized
[ 7256.621283] IR JVC protocol handler initialized
[ 7256.624695] IR Sony protocol handler initialized
[ 7256.628036] IR MCE Keyboard/mouse protocol handler initialized
[ 7256.631921] lirc_dev: IR Remote Control driver registered, major 249 
[ 7256.632876] IR LIRC bridge handler initialized
[ 7256.638174] Registered IR keymap rc-streamzap
[ 7256.638396] input: Streamzap PC Remote Infrared Receiver (0e9c:0000) as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/rc/rc0/input15
[ 7256.638627] rc0: Streamzap PC Remote Infrared Receiver (0e9c:0000) as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/rc/rc0
[ 7256.638881] input: MCE IR Keyboard/Mouse (streamzap) as /devices/virtual/input/input16
[ 7256.639289] rc rc0: lirc_dev: driver ir-lirc-codec (streamzap) registered at minor = 0
[ 7256.639344] streamzap 2-1.3:1.0: Registered Streamzap, Inc. Streamzap Remote Control on usb2:4
[ 7256.642637] IR RC5 (streamzap) protocol handler initialized
[ 7256.642948] usbcore: registered new interface driver streamzap
```

And you can point any IR remote you want to it, grab the code sent by the remote and associate that to any keyboard key, mouse or even script. In this case, I customized the IR-keymap for each receiver so it adapts to each of the 3 IR remotes. 

In parallel, I have one of this ([http://www.usbuirt.com/overview.htm](http://www.usbuirt.com/overview.htm)) with which I conducted successful experiments some months ago using Ubuntu 12.04. My idea was the same as yours. 

Lirc and irsend worked perfectly. I tried some bash scripts using irrecord and irsend to control all A/V devices and even other electronics, everything  went fine. 

I gave it up because it was not really portable. I wanted something portable to control at least the TVs/xbmc. When I plugged it to my desktop the IR signal wouldn't reach other rooms. And when I plugged it to my notebooks, well, it was just ugly.  So now I use the official xbmc remote in my android phone.

Regards,
Effenberg

**EDIT:** By the way, do you remember handheld/PDAs, like Palm and HP iPAQ? Many of them had embedded IR receivers/transmitters, had touchscreen and IR configurable remote control software. Many people used them to control IR devices. You can get one of these PDAs almost for free nowadays.

---

