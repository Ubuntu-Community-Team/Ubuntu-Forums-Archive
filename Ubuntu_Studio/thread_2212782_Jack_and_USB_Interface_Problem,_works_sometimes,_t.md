---
title: "Jack and USB Interface Problem, works sometimes, then doesn't."
date: 2014-03-23
forum: Ubuntu Studio
---

### Post by nreynolds2121 on 2014-03-23
I have a Zoom H4N Recorder, which has the ability to be a usb interface. It works well for this purpose...when it works. Here is my problem, which I have encountered on both a standard ubuntu install with the studio metapackages , the lowlatency & realtime kernels installed, and now, Ubuntu Studio 13.10, which I thought would solve my problem. Sometimes I will start jack and the everything starts just fine, 2 buffers, 32 frame, the usb interface selected. Then sometimes, the server won't even start. Also, sometimes it will start, but as I play there will eventually be a noticeable delay coming from the capture, more then the few milliseconds jack says it should. I've tried changing to 3 buffers, changing frames from 32, 64, 128, 1024, switching the device & jack to a sample rate of 48000  yet still this problem occurs regularly. Sometimes things will work right off the bat, sometimes it won't work at all saying it can't initialize the driver. When it doesn't work, I will go through the sets of frames, until one works, then I can switch it back to 32 frames and have near realtime instrument effects at about 2 m/s. This is very frustrating when your trying to concentrate on a the music your trying to create. i've tried switching usb cords, switching usb ports, removing connected devices in the usb ports. Any help will be greatly appreciated.

---

### Post by jejeman on 2014-03-23
For H4N I use 48000KHz, 3 periods, 64 buffers which gives 4ms. Enough for recording.
Ubuntu Studio 12.04.

---

### Post by nreynolds2121 on 2014-03-23
I've used those settings as well, the three buffers necessary I read due to the math required for the interface, something about needing even latency. I will try those settings again, but swear I eventually ran into the aforementioned problems. Just don't understand why sometimes things work just fine with 2 buffers, 64 or 32 frames, and nearly realtime ability for instrument effects, then sometimes they fail. Just having the ability to record without glitches would still be an improvement but to utilize the high quality connection of the usb interface and the realtime DSP effects of studio would be great. Ideally aiming for 2 m/s, the same delay that occurs in purpose built DSP's pedals. I'm starting to think this may be impossible for the ZOOM which seems to have more then enough proccessing power to just send the audio signal across usb, yet I can't get it to work with jack. Even with only a 4 m/s delay, I still hear it between the time I strike my instrument, then hear the processed sound come out. Windows ASIO drivers can do 2 m/s, but I'm not going back to that.  Also thank you for your response :)

update: ok, for just recording I got no xruns. When I used guiatrx, I don't seem to have any problems so far but when I try to use the DSP functions in rakarrack, I get xruns in the thousands per second, also noticed effects don't sound quite right. I also have the same DSP problem with certain effects in jack-rack that are realtime for certain. I'm certain this is a problem with the jack server and not a limitation of the usb interface.

---

### Post by jejeman on 2014-03-24
What is your CPU?

---

### Post by nreynolds2121 on 2014-03-24
Intel® Pentium(R) 4 CPU 3.40GHz running on ubuntu studio 13.10 64 bit

---

### Post by jejeman on 2014-03-25
You didn't write the exact model of CPU, but that is a very weak CPU. Minimum for lowlatency is Core2Duo 2GHz in my experience, specially with DSP processing.

---

### Post by nreynolds2121 on 2014-03-28
I've had reliable realtime DSP with far weaker systems, both with lowlatency & realtime kernel. This has something to do the fact it is usb. I could just turn on the monitor feature and run a stereo cable from the interface to my systems onboard line-in. Still, was hoping to use it all by itself.

---

### Post by Clockmender on 2014-04-18
Switch to an E-MU 0404 PCIe card, this should remove the problems. Audio in is not too hard to configure, all is explained on my web pages at [http://www.lafavinie.com/Music](http://www.lafavinie.com/Music) I don't know what you are using to control Jack, but I found Claudia from KX Studio to be the best option, all is revealed in my web pages - see the Studio page, QjackCtl can be a pain and makes random unrequired connections all the time, Gladish, which comes with Ubuntu studio tends to crash Jack on my setup whereas Claudia, which is effectively a refined LADI wrapper, does not. I started off with QjackCtl and moved on to others as my knowledge and requirements increased. Make sure you are actually using the low latency kernal, as it will not necessarily be the latest one in your grub list. My pages explain how to make sure you use this kernal. I can run many synths and DAWs together along with either Rakarrack or Guitarix with low DSP usage and no xruns. I found the reported latencies in ASIO to be very unreliable when I used it in the oldern days! One point to note - in my experience the latency quoted on ASIO is the best you will get, on Linux its the worst you achieve, in other words you may get a theoretical value of 20msec reported by Jack, but in reality with the right sound card and processors you will get somewhere near 2msec when you actually play the thing. My benchmark is to play the violin lead from Eine Kleine Nachtmusik on the keyboard without losing my way!

The only USB device I ever use is an IK Multimedia iRig PRO on my MacBook Pro running Reason from Propellerheads in Sweden, (google it) but then again Mac's have near zero latency sound processors anyway. In my experience, USB audio/midi interfaces do not work reliably and fast on anything other than a Mac.

And as a last thought - disable your screen saver if you are pushing sound processing to the max - it tends to crash Jack!

My music PC has a 4.6GHz quad core AMD processor with 8Gb RAM and two 500Gb SATA disks running on a Gigabit mother board with the biggest graphics card I could get my hands on.....

---

### Post by Clockmender on 2014-04-24
One last point - you say you are aiming for 2msec delay - sound travels at 1,100ft/second so if you sit 2.2 feet away from your speakers you have a 2msec delay in the sound leaving your speakers and entering your ears, 6ft away and the delay is 5.45msec, think about it.........

Xruns are caused by you driving your system beyond it's capabilities, often the only answer is to use a bigger processor, faster sound card, prederably a PCI or PCIe device and a low latency realtime kernal setup.

---

