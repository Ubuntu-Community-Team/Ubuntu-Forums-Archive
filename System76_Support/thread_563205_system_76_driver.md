---
title: "system 76 driver?"
date: 2007-09-29
forum: System76 Support
---

### Post by Marty McFly on 2007-09-29
I saw on another thread about losing sound to run System 76 Driver.

I went to System>Administration like instructed by I don't have it in there.  How do I turn it on, do I have to install it?

---

### Post by Sef on 2007-09-30
Moved to  System76 Support.

---

### Post by TheBuzzSaw on 2007-09-30
Installing the Gutsy Gibbon beta made my sound work without the system76 driver. If you are not afraid of beta testing, I highly recommend it. It runs fine. ^_^

---

### Post by tedrampart on 2007-10-01
> **TheBuzzSaw said:**
> Installing the Gutsy Gibbon beta made my sound work without the system76 driver. If you are not afraid of beta testing, I highly recommend it. It runs fine. ^_^

when I reinstall, and lose sound, I have to run alsamixer from bash, and mute the external speaker channel.. once its muted I have sound.. not sure if that would fix it for you, but its worth investigating I suppose..

---

### Post by thomasaaron on 2007-10-01
To install the System 76 Driver:

Make sure you're connected to the Internet.

From a command line, enter:
sudo wget [http://planet76.com/repositories/system76-driver-2.0.9.deb](http://planet76.com/repositories/system76-driver-2.0.9.deb)
sudo dpkg -i system76-driver-2.0.9.deb

Then go to System > Administration > System 76 Driver
Click the restore tab and restore button.

Reboot your computer.

---

### Post by TheBuzzSaw on 2007-10-01
You may want to disable URL parsing, TA. :P

---

### Post by thomasaaron on 2007-10-01
Hmmm. Good point. Thanks.

---

### Post by steveneddy on 2007-10-01
> **thomasaaron said:**
> To install the System 76 Driver:

Make sure you're connected to the Internet.

From a command line, enter:
sudo wget [http://planet76.com/repositories/system76-driver-2.0.9.deb](http://planet76.com/repositories/system76-driver-2.0.9.deb)
sudo dpkg -i system76-driver-2.0.9.deb

Then go to System > Administration > System 76 Driver
Click the restore tab and restore button.

Reboot your computer.

I just installed the 64 bit version of Feisty. Can I use this method to install the System76 driver?

Actually, all that I'm having trouble with at the moment is the wired ethernet connection. Wireless worked out of the box. USB and sound all work, and with the codecs installed, it plays DVD's very well.

Do I need the System76 Driver?

Will there be a 64 bit version of Gutsy?

---

### Post by thomasaaron on 2007-10-02
Well, right now the driver doesn't support gutsy anyway. (It will run under Gutsy, but it won't do anything). The new driver will be released when Gutsy is. So, to answer your question, it really doesn't matter at this point anyway.

---

### Post by Marty McFly on 2007-10-07
I'm running Feisty and got this error message:

This driver is designed for System76 machines running Ubuntu version 6.06, 6.10, 7.04 or 7.10.  If you have a System76 machine running one of the above Ubuntu versions, please file a bug report at [https://launchpad.net/system76](https://launchpad.net/system76)

Any ideas?  I'm running 7.04

---

### Post by thomasaaron on 2007-10-08
What is your System 76 model number? Are you using a System 76 machine?

Also, are you running 64-bit? If so, the driver is not set up to run with it.

---

### Post by Marty McFly on 2007-10-08
sorry i saw so many people referring to this driver with the new sound issues that are coming out, i assumed it was for anyone...not for a specific computer.

---

### Post by thomasaaron on 2007-10-09
Well, it is open source.

You can have a look under the hood and see what we have done.
It may provide some hints as to how to get your sound up and running.

Most likely, the problem can be solved by upgrading to the latest ALSA and entering the correct model in the /etc/modprobe.d/alsa-base file.

Or, you might want to just wait for Gutsy to come down the pike in a couple of weeks. It contains the latest stable release of ALSA, which may
well fix your problem.

Best,
Tom

---

