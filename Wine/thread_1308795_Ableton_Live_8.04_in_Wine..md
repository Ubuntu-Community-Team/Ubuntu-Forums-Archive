---
title: "Ableton Live 8.04 in Wine."
date: 2009-10-31
forum: Wine
---

### Post by Vigh on 2009-10-31
Hey guys I've managed to get Ableton Live 8 authorized and working in wine.

First install the latest version of wine.

Second install audacity if you havent already.

Install jack and rt-kernel. Configure jack server.

Install ableton 8.04 through wine.

Authorize offline mode. Save authorization file to desktop. Open with- custom command- browse to .wine folder and open with ableton-8.0.4.exe

All instruments work, VST works, saving works, exporting doesnt, which is easily fixed via setting up JACK to record the audio output through audacity. I havent figured out how to work usb midi yet through wine.

You need to run JACK server in order to get sound output through ableton.

I am going to attempt to set up my native instruments audio kontrol 1 in Ubuntu and will let you know how I go.

---

### Post by Vigh on 2009-10-31
You can install additional live packs such as latin percussion, by copying live packs from cd to hdd. Then within the program going to file, install live packs. It may use slightly more CPU but if you have the CPU power, things will run smoother than on windows. Testing VSTs Arturia VSTs work with some graphical display issues. NI Komplete 5 VSTs work. Set buffer high = 5, and frames/period low = 64 and set the appropriate driver error compensation within ableton to remove crackling noises. Xruns = 0.

---

### Post by linoshi on 2010-01-29
How can i open the authorization file on Ubuntu? It is .auz extension and change some values in register of Windows, i mean. Thanks

---

### Post by rfchamusca on 2010-05-04
linoshi, I've followed Vigh instructions and it works. If you double click the .AUZ file it will ask for the program to run, then you should copy+paste the command provided by your Live launcher. Mine was like this:

**env WINEPREFIX="/home/xxxxxx/.wine" wine "C:\\Program Files\\Ableton\\Live 8.0.10\\\\Program\\Live 8.0.10.exe"**

Of course, you'll need to change the **xxxxxx** value to your login name.

I believe that if you open Live and choose the .AUZ as a session it might work as well.

---

### Post by Vigh on 2010-09-10
Just a quick note, if you do not own Ableton!!! Then go and buy it!!! It is $1000 software and should not be pirated!!!

---

### Post by cosmolee on 2010-12-09
Ubuntu 10.04, Wine 1.2

Did you have to do any special configuration of Wine?  I have Ableton Live Lite (Akai Professional Edition), which came with my Akai keyboard.

Installation seems to go fine, but when I run Ableton I get the following error:

"A serious error has occurred.  Live will shutdown after this message box is closed"

Thanks for any help...

---

### Post by KasuKu on 2011-01-11
I am going to attempt to set up my native instruments audio kontrol 1 in Ubuntu and will let you know how I go.[/QUOTE]

):P  Any joy with NI AK1 installation?

---

### Post by Vigh on 2011-01-20
Haven't tested it yet. Will give it a go at some stage. I am using vmware at the moment, but will test it out with the AK1 when I find some time.

---

