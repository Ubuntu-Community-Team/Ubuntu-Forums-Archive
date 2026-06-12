---
title: "Please help with this driver for Edirol UA-4FX"
date: 2009-01-18
forum: Ubuntu Studio
---

### Post by lameiro on 2009-01-18
Hello, i have an Edirol UA-4FX that I want to use with ubuntu, but this USB audio/MIDI interface isn't completely supporte, it has a davanced mode that I need to make an interactive musical performance.
I have found a webpage that has some patch to the driver, but I am completely lost with it since it doesn't explain how to make the same thing on my pc. I leave here the link to the wiki page hoping some soul can help me ;)

[http://alsa.opensrc.org/index.php/Edirol_UA-4FX#Getting_Advanced_mode_to_work]("http://alsa.opensrc.org/index.php/Edirol_UA-4FX#Getting_Advanced_mode_to_work")

Thankyou in advance

---

### Post by mtriston on 2009-01-28
Dude, I just got mine to work in advanced mode w/ rosegarden.  I'll try to have a howto up in a couple of days for you.  Just trying to get it work with ardour right now with no success but when that happens I'll be sure to post.

---

### Post by binger on 2009-01-29
I have a UA-4fx as well and would love to get advanced mode working!  Let us know your result lameiro and we can test it out.

---

### Post by mtriston on 2009-01-30
In order to get the Edirol UA-4FX to work alsa must be compiled from source with the [patch]("http://alsa.opensrc.org/index.php/Edirol_UA-4FX#Getting_Advanced_mode_to_work") given on the opensrc.org website.  Copy the file they give and save as a .diff file.  I saved mine as UA4FX.diff.  Now find out which kernel you are running.  You can do this by typing 'uname -r' in the terminal.  Once you have that info you can get started. Open up your terminal and get to work.

```
sudo apt-get install build-essential linux-headers-2.6.24-23-rt alsa-source
```

note: the linux-headers-2.6.24-23-rt is the headers for the kernel I'm running. Be sure to get the correct kernel headers for your kernel.

Now unpack the alsa-source package.  Should be in the /usr/src directory.

```
cd /usr/src
sudo tar xjf alsa-driver.tar.bz2  
```

Now that that is unpacked copy and apply the UA4FX.diff patch you have saved already to the directory where compiling will be done.

```
sudo cp UA4FX.diff /usr/src/modules/alsa-driver 
sudo patch -p0 < UA4FX.diff
sudo ./configure
```

I then removed the old alsa drivers from my system.
 
```
rm -rf /lib/modules/2.6.24-23-rt/ubuntu/sound/*
```

Then I did an sudo make && make install.

After a reboot I thought the drivers would have been installed in the directory that I removed but I had no sound and I had no directory where I had deleted. I solved this by:

```
sudo cp -R /usr/src/modules/* /lib/modules/2.6.24-23-rt/ubuntu/sound
```

I then did a reboot with the UA-4FX hooked up in advanced mode.  Opened up the terminal
```
cat /proc/asound/cards
```

My output:

```
 2 [UA4FX          ]: USB-Audio - UA-4FX
                      EDIROL UA-4FX at usb-0000:00:0a.0-1, full speed
```

Success!!


It now works perfectly w/ midi in Rosegarden but I have yet to have the midi work in Ardour.  If any Ardour experts have gotten it to work I would appreciate some help w/ that.  Thanks,

mtriston

---

### Post by binger on 2009-02-03
I am not really sure what happened.  But I followed your guide and I got advanced mode to work the day I did it.  Though my /proc/asound/card1/stream0 only showed the currently selected sample rate, not all three.  Also 96 didn't seem to playback correctly, but 48 was fine which is what i care about.  
So I tried it again today and it would not load snd-usb-audio when I plugged it in.  
```
[  120.805589] usb 1-1: new full speed USB device using uhci_hcd and address 2
[  120.982717] usb 1-1: configuration #1 chosen from 1 choice

```
There are some oddities in my lsusb -v:
```
Bus 001 Device 003: ID 0582:00a3 Roland Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass         0 
  bDeviceProtocol       255 
  bMaxPacketSize0         8
  idVendor           0x0582 Roland Corp.
  idProduct          0x00a3 
  bcdDevice            1.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          202
    bNumInterfaces          3
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              360mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      2 
      bInterfaceProtocol      2 
      iInterface              0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      2 
      bInterfaceProtocol      2 
      iInterface              0 
      ** UNRECOGNIZED:  07 24 01 01 00 01 00
      ** UNRECOGNIZED:  0b 24 02 01 02 03 18 01 80 bb 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            9
          Transfer Type            Isochronous
          Synch Type               Adaptive
          Usage Type               Data
        wMaxPacketSize     0x0140  1x 320 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       2
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      2 
      bInterfaceProtocol      2 
      iInterface              0 
      ** UNRECOGNIZED:  07 24 01 02 00 01 20
      ** UNRECOGNIZED:  0b 24 02 03 02 03 18 01 80 bb 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            9
          Transfer Type            Isochronous
          Synch Type               Adaptive
          Usage Type               Data
        wMaxPacketSize     0x0138  1x 312 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      2 
      bInterfaceProtocol      1 
      iInterface              0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      2 
      bInterfaceProtocol      1 
      iInterface              0 
      ** UNRECOGNIZED:  07 24 01 07 00 01 00
      ** UNRECOGNIZED:  0b 24 02 01 02 03 18 01 80 bb 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0140  1x 320 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      3 
      bInterfaceProtocol      0 
      iInterface              0 
      ** UNRECOGNIZED:  06 24 f1 02 01 01
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      3 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               1
cannot read device status, Operation not permitted (1)

```

I switch it back to non-advanced mode and it is working fine.

I am debugging as I am typing this, and I tried all the USB ports on my laptop and in advanced mode when it doesn't work, gnome-device-manager displays a warning on the USB HUb that it is connected to saying "Insufficient power to operate USB device."
I then did a sudo modprobe snd-usb-audio and the device came to life.  My lsusb -v output still has those UNRECOGNIZED lines in it, and device-manager still says insufficient power, but the device works.  I am wondering what isn't getting enough power?  I tried all the usb ports again, watching that power message and I realized, that entry in devicemanager is always there, even when I don't have it plugged in.  When I plug the device in and works and no warnings on the actual device.  Somehow I have a ghost device.  I am going to reboot and see how it goes.

---

### Post by binger on 2009-02-03
Okay, I rebooted.  Ghost device is gone.  I plugged in the UA-4fx in advanced mode and the USB Device with insufficent power showed up.  snd-usb-audio did NOT load.  I did a manual modprobe and the UA-4fx sound drivers loaded under that USB device with insufficent power and the device seems to be working great in 48Khz mode.  

When I am in non-advanced mode the Insufficent power message does not appear.  Also, Under the USB Device it shows 3 USB interfaces in Advanced mode, but in non-advanced mode it shows one Audio Control Interface and two Audio Streaming Interfaces.

Anyone else experiencing something like this know if this is driver, device or laptop usb hub related?

---

### Post by rlameiro on 2009-02-04
Man, you gave very good news!!!! I was thinking in selling the UA-4FX, well at the moment I'm not at home, but tomorrow I will test it and put the results. THANKS!!!!!!!!!!!

binger, is it possible that your problem is related to the fact that you use the device in the laptop, maybe you were running on batteries and the laptop cant give enough current to the UA-4FX.Try to use a good usb hub with external power source, that will maybe solve your problem.

---

### Post by rlameiro on 2009-02-07
Hello.
well I tried to applied the patch, and when I try to do the "make" comand, this is the final result. after this I tried make install and also gave me errors. This is a fresh ubuntustudio install 8.10 with the rt kernel  2.6.27-3-rt.
Can someone tell-me what is going on here? some help?

```
make[2]: Leaving directory `/usr/src/modules/alsa-driver/misc'
make[1]: Leaving directory `/usr/src/modules/alsa-driver'
make -C /lib/modules/2.6.27-3-rt/build SUBDIRS=/usr/src/modules/alsa-driver  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-3-rt'
  CC [M]  /usr/src/modules/alsa-driver/acore/info.o
/usr/src/modules/alsa-driver/acore/info.c: In function ‘resize_info_buffer’:
/usr/src/modules/alsa-driver/acore/info.c:90: error: implicit declaration of function ‘PAGE_ALIGN’
make[3]: *** [/usr/src/modules/alsa-driver/acore/info.o] Error 1
make[2]: *** [/usr/src/modules/alsa-driver/acore] Error 2
make[1]: *** [_module_/usr/src/modules/alsa-driver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-3-rt'
make: *** [compile] Error 2

```

---

### Post by binger on 2009-02-07
Alright, so I went through the build and patch process twice just to make sure.  When I plug in my UA-4fx in advnaced mode it shows up fine as a USB device, but does not load snd-usb-audio module properly.  So after I plug it in, i just have to run sudo modprobe snd-usb-audio and then it works great in 44.1/48 and with MIDI.  Is this have to do with my modprobe.d or hardware Ids maybe?

Running that little command is pretty easy and I'm glad that it works.  In non-advanced mode it works by just plugging it in still.

---

### Post by rlameiro on 2009-02-08
Ok, after asking at the programming talk, eightmillion directed me to udev.[uDEV]("http://reactivated.net/writing_udev_rules.html#why")
So I was here looking and reading, and finally made it to work. I made a rule to load the module (modprobe). 
How to make that?
```
 sudo gedit /etc/udev/rules.d/90-modprobe.rules

```
an there add between some of the other rules
```
# UA-4fx load sound driver 

ATTR{manufacturer}=="EDIROL" , ATTR{product}=="UA-4FX" , RUN+="/sbin/modprobe -Qba snd-usb-audio"
```

save and test it, if you ear the sond, it is working!!!

I would like to know what do you think about making a script that automates all this process of patching, compiling, patching, crating rules etc? do you think it is worth the effort?

---

### Post by mtriston on 2009-02-09
I would think ppl would appreciate such a script.  BTW has anyone gotten MIDI to work w/ Ardour yet?

---

### Post by rlameiro on 2009-02-10
I will try this weekend in my keyboard, I will try to see that
I dont work with ardou, but I will test. If it works with rosegarden
it should work with ardour. Ok I will try to make that script, I dont have to muchtime, but I will try
:)

---

### Post by m.letcher on 2009-02-13
**A script would be lovely!!**

I have been patiently waiting to get the MIDI working on my UA4FX with Studio. Audio has been OK, but I'd really like to get the MIDI working. Usually, I route a DX11 into it, but I just got a Axiom25 ( USB midi with knobs and pads ) and silly me, I didn't check for linux/Ubuntu support. Even my MOTU midi-lite is driverless in Ubuntu. However, I could route the Axiom into the UA4FX if its midi ports are supported and be very happy. I'll probably try the process above this weekend ( and look around for Axiom support some more ). Its been a while since I compiled stuff, but this doesn't appear more complicated than a custom kernel ( which I used to do way back when). I saw one msg where somebody had a Axiom49 working, so maybe there's an Axiom25 patch path out there.

I may try Wine this weekend as well to import some VST's from Vista. I just got some more drive space ( ~150 GB for Ubuntu) and am torn between going back to Hardy, staying with Intrepid, or just waiting for Jaunty. Will depend on how well Nvidia support works out this weekend. 

But MIDI support would be great to get Jack/Studio going and start playing with Rosegarden and Renoise.

---

### Post by m.letcher on 2009-02-13
I forgot to mention that I'm a willing volunteer beta tester for a script. I'll probably be doing a re-install anyway shortly to see if I can boot to a USB drive this weekend and need to re-DL Studio anyway. First, I'll try to get my Nvidia driver straightened out ( again ). Compile from Nvidia site worked OK in Gutsy, but Intrepid hasn't worked with Envy, Intrepid installers, NVidia, etc ( so far, and its not a dual video card system with new X.org issues ). If you don't find the time this weekend that's fine.  

Cheers. Best of luck.

---

### Post by binger on 2009-02-14
I tried out those UDev rules and my UA-4fx in advanced mode now loads up like a charm with snd-usb-audio.

---

### Post by rlameiro on 2009-02-16
> **mtriston said:**
> ... BTW has anyone gotten MIDI to work w/ Ardour yet?

Well, this weekend I tested midi, and it worked with rosegarden, ZynAddSub, and even with PureData, I really dont know to much about ardour, so i do not understand why you need midi there,   is it for start controllers? or to sincronise with sequencers? because I see the midi in connections in jack, so it should work also with ardour. The script is like in standby for some days, I need to play with my UA-4FX first :):popcorn:

---

### Post by mtriston on 2009-02-17
I was just curious about trying out ardour and its different features.  I have never used it before and just wanted to experiment a bit.  I see midi in jack as well but for some reason I don't see it in ardour or audacity.  Just wondering if there was an easy set up for them such as rosegarden's 'manage midi devices' program.

---

### Post by rlameiro on 2009-02-18
I think that you can assign midi controllers to the mixers. I saw that in some ardour tutorial

---

### Post by mtriston on 2009-02-21
For anyone interested I've just stumbled across some video tutorials for beginners of ardour [here]("http://vimeo.com/2867399").  And BTW do we think we can now mark this thread as solved?

---

### Post by rlameiro on 2009-02-22
wait, for the script. when i  make the script, then is solved :)

---

### Post by m.letcher on 2009-03-31
In the meantime, I've been upgrading to the Jaunty Beta. Works well. I'm still hoping that you'll get a chance to finish a script to get the midi working with the UA-4FX ( I just got another MIDI controller ( an Axiom-25) and use the UA as primary midi input). I've pretty much given up on any support for the MOTU-microlite with Ubuntu. Jaunty does support it for audio without workarounds as much as I can tell so far and looks good, but I'm just starting to play with it today. If not, I'll re-read and try to recreate method in this thread. I did see several new threads on the UA and Ubuntu Studio today however and will be looking through them this week. I haven't played with Ardour too much either, but my understanding is that its like a Audacity on steroids ( kind of like Acid/FLS in WinDoze ). Apparently, several folks have been having good success running various VST instruments through Wine as well, but I haven't gotten that far in Ubuntu. Audio first ( appears done ), Midi next ( working on it ), then the VST's and maybe some Win programs depending how well Ubuntu is working today. In the long run, it will probably all be Ubuntu but that's a while from now.
Cheers.

---

### Post by Rackstar on 2009-06-18
Thanks for the howto! I gave up on my UA-4FX a long time ago, but when I read this, I decided to try it again.

I tried to do the patch but gave me this:
```

ruben@ruben-laptop:/usr/src/modules/alsa-driver$ sudo patch -p0 < UA-4FX.diff 
patching file sound/usb/usbaudio.c
Hunk #1 FAILED at 2930.
Hunk #2 FAILED at 2950.
2 out of 2 hunks FAILED -- saving rejects to file sound/usb/usbaudio.c.rej
patching file sound/usb/usbquirks.h
Hunk #1 succeeded at 1376 with fuzz 2 (offset 65 lines).

```

The first part of the patch did not work. Does anybody know what to do next?

Or can anybody suggest another usb audio card, in the same price category as this one, but with working midi on ubuntu?

---

### Post by hubbardd on 2009-06-18
Hi Rackstar,

I wrote the patch. It's cool to see people finally using it. Rackstar, if you are using Jaunty (Ubuntu 9.04) or can upgrade to kernel 2.6.28 or newer, the patch has been included in the kernel. Woohoo!

I updated the wiki page, [http://alsa.opensrc.org/index.php/Edirol_UA-4FX](http://alsa.opensrc.org/index.php/Edirol_UA-4FX), with that information. So it sounds like MIDI is working?

You should all know about the noise problem. When you switch to Advanced mode, the hardware adds noise in playback and recording, to deliberately reduce the quality. You are actually better off using the 16-bit 44kHz audio. Note that the Windows driver does not have this problem, so with some reverse engineering we could fix the linux driver.

- DHubbard

---

### Post by Rackstar on 2009-06-19
> **hubbardd said:**
> Hi Rackstar,

I wrote the patch. It's cool to see people finally using it. Rackstar, if you are using Jaunty (Ubuntu 9.04) or can upgrade to kernel 2.6.28 or newer, the patch has been included in the kernel. Woohoo!


Hi,

Thanks for your reply and your work!

I had tried the patch over a year ago, but gave up early because my lack of patch-knowledge. ;) I did find it strange that the sound playback worked in advanced mode (since Jaunty) :), but I did not manage to get jack running. 

If someone could point a good tutorial about setting up an environment to receive midi from the midi-controller and process it to rosegarden (or ardour), please do.

I'm not at my home so I don't have the card with me, so I can't try now.

Thanks!

---

### Post by rlameiro on 2009-06-20
Hi, I used midi in it worked.

Used it at least with rosegarden and Puredata.

Thanks for the work!!!!!!!!!!

---

### Post by binger on 2009-09-10
I am now using 64 Studio 3.0 beta 3 which runs on 2.6.29 kernel and my UA-4fx works great. :)

---

### Post by djxcon on 2009-09-10
For those people who have posted that the UA-4FX is working...are you finding that recording (not in advanced mode) causes noise in the background?  This noise was bad enough for me to basically stop using the UA-4FX in Linux and instead dual boot to Windows for recording.  In Windows, there is no background noise and it sounds fine. 

I am not too into midi but it's nice to hear that this is finally working for some!

---

### Post by 2benglish on 2009-12-15
As I understand the kernel with 9.10 doesn't need modifying. Yet the UA-4FX doesn't work out of the box in advanced mode. 
Could somebody explain where in this explanation I need to jump in running ubuntustudio 9.10.

Thanks.

---

