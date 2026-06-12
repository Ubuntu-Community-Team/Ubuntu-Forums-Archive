---
title: "Swissonic Firewire Audio Interface"
date: 2009-11-20
forum: Ubuntu Studio
---

### Post by radocool on 2009-11-20
[SIZE=3][FONT=Book Antiqua][FONT=Arial]Hello fellow Ubuntu users,

I have a problem getting a firewire interface to work in ubuntu. The make and model of the interface is
[/FONT][B][FONT=Arial]Swissonic Easy Firewire[/FONT]
[/B][/FONT][/SIZE][http://images.thomann.de/pics/prod/218447.jpg](http://images.thomann.de/pics/prod/218447.jpg)

[SIZE=3][FONT=Arial]I did a fresh install yesterday of the new Ubuntu 9.10. Now, I plugged in the device and the indicator light lit as expected, then I restarted ubuntu. When it loaded again, I opened the terminal and did the following:
[/FONT][/SIZE]> 
sudo chmod o+rw /dev/raw1394
jackd -d freebob
[SIZE=3][FONT=Arial]The first line changes the access rights for the firewire port and the second starts the jack server with the freebob driver( I saw that libfreebob was already installed). Now here's the output:
[/FONT][/SIZE]> 
JACK compiled with System V SHM support.
loading driver ..
Freebob using Firewire port 0, node -1
LibFreeBoB ERR: Dropped packets on connection 1
LibFreeBoB ERR: Dropped packets on connection 1
[SIZE=3][FONT=Arial]The problem comes from this error:
[/FONT][/SIZE]> LibFreeBoB ERR: Dropped packets on connection 1[SIZE=3][FONT=Arial]which occurs every 2 seconds or so. Can anyone tell me what's causing this?
I continued investigating further. I wanted to know if the device is recognized at all by linux. So I came across a neat little shell script called **ls1394** (many thanks to the author, Stefan Richter)[/FONT][/SIZE][SIZE=3][FONT=Arial]. What this script does, is to show information regarding the connected firewire devices, pretty much what **lsusb** does for USB devices. And here's the output:
[/FONT][/SIZE]> 
0:ffc0 0014960000000713 Phonic Corp. 'EasyFw'
[SIZE=3][FONT=Arial] 
so this means good news - it is recognized. The vendor of the chipset is supposedly **Phonic corp.** . So I searched the net and found on the ffado/freebob (I'm not sure which) site some info on supported devices and there were quite a few from **phonic**. Does this mean that most devices from this vendor are supported? Please tell me if there's hope to get this interface to work. Thank you in advance!
[/FONT][/SIZE]

---

### Post by AutoStatic on 2009-11-20
Hello radocool, looks like it's this one:
[http://www.phonic.com/en/audio-interface/firefly-202.html](http://www.phonic.com/en/audio-interface/firefly-202.html)

But I don't see it here:
[http://ffado.org/?q=devicesupport%2Flist&filter0=phonic&filter1=&op2=OR](http://ffado.org/?q=devicesupport%2Flist&filter0=phonic&filter1=&op2=OR)

Did you install *libffado0*? And did you try this guide:
[https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)

And do you know what kind of Firewire card you have in your PC? What does **lspci** in a terminal say?

---

### Post by radocool on 2009-11-20
Hello AutoStatic,

Yes, the resemblance is stunning. I guess the guys from swissonic just changed the name. Actually I got help from a user named adi in the #ffado channel on freenode. I managed to get it up and running thanks to him. It even works seamlessly with real-time settings on jackd. I didn't expect that such a cheap audio interface (it costs only 29 euros) would get full support in linux with such great sound quality. If anyone is interested I can give a step-by-step guide how to get it started. Oh, by the way - does anybody have access to the ffado site's supported devices database? If you do, add this device to the list(I registered but I don't have rights to add). Or you can pm me the e-mail of someone involved in the project so that I can e-mail him.

regards,
radocool

---

### Post by kayosiii on 2009-11-22
Supported in the FFado database means two things...
1) The FFado devs have been delivered documentation on any deviations from the functionality supplied from the base chipset.
2) The FFado deves have been supplied with the soundcard model to test issues with.

Reported to work means that somebody has managed to get it work, but the manufacturer hasn't provided anything to the ffado devs. You want the later :)

---

### Post by markus888 on 2010-01-03
Hello radocool,
I planning to buy this Audio Interface for my computer. I would be nice if you could give a shot summery how to get it started.

---

