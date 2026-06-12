---
title: "Raspbery PI &amp; Ubuntu OS"
date: 2013-04-09
forum: Ubuntu, Linux and OS Chat
---

### Post by heldemanpieter on 2013-04-09
Is it possible to install Ubuntu on the Raspberry. Wen you connect a HDMI to VGA converter you can use a monitor, to change the resulution you have to do some coding.):P

---

### Post by ppv on 2013-04-09
> **heldemanpieter said:**
> Is it possible to install Ubuntu on the Raspberry.
Ubuntu...likely no...because it dropped support for ARM version on which Raspberry PI is based. Check out the link below.
[http://en.wikipedia.org/wiki/Raspberry_Pi](http://en.wikipedia.org/wiki/Raspberry_Pi)

But, some other distros like Debian and Arch can be installed.
> **heldemanpieter said:**
> Wen you connect a HDMI to VGA converter you can use a monitor, to change the resulution you have to do some coding.):P
The OS running on the board should be able to take care of it.

---

### Post by cortman on 2013-04-09
You can get [Raspbian]("http://www.raspbian.org/") (A version of Debian complied for ARM and the pi specifically).
I've encountered a lot of problems trying to install it to an SD card though; it's nowhere near as straightforward as various tutorials floating about the web would have you think.

---

### Post by MichealH on 2013-04-09
You can't - Ubuntu's ARM target is ARMv7. The Raspberry Pi uses ARMv6, so If you tried to install it, Ubuntu would most likely not run due to this difference. I have, however, been using [Raspbian]("http://www.raspbian.org/"). Raspbian is based from the same base Ubuntu is based on, so there should be very minor differences behind the scenes, such as apt-get is the same, and package names are generally the same.

---

### Post by heldemanpieter on 2013-04-09
When you use a monitor the OS on the board can not do it automatically, do the following:
All you need is an inexpensive (around £10 -    £15 online) HDMI to VGA adaptor, which connects between the Raspberry and    the TV. Some work straight out of the box but on others you may need to    modify a file called config.text, which is on the SD card that contains the    Pi&#8217;s operating system. It is easiest to do this on a PC using a memory card    reader; open config.txt with Notepad or WordPad and &#8216;uncomment&#8217; or remove    the hash (#) symbol on the lines &#8216;hdmi_force_hotplug=1&#8217; and &#8216;hdmi_drive=2.    This enables the adaptor and VGA output mode and sets the screen resolution    to 640 x 480. You will probably want to increase resolution to 1024 x 768,    say, if so uncomment the lines &#8216;hdmi_group=1&#8217; and &#8216;hdmi_mode= 4&#8217;, then    change the group setting to 2 and the mode to 16, save the file and pop the    card back into the Pi. It is a brilliant learning tool and to get the most    from it I suggest that you work your way through one of the many online    tutorials and learn how to write simple programs. From there you can    progress to creating your own software, and even use the Pi to control other    devices with plug-in modules.
Got this from: telegraph.co.uk/technology/advice

---

