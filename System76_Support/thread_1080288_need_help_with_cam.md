---
title: "need help with cam"
date: 2009-02-25
forum: System76 Support
---

### Post by eddietours on 2009-02-25
am trying to use the cam l have the gazelle ultra l try to turn it on with fn/f10 but no luck do l need to load the Drivers thanks

---

### Post by thomasaaron on 2009-02-25
INSTALLING THE WEBCAM DRIVER
Your computer should arrive with any necessary drivers already installed. However, if you've run any updates, particularly kernel updates, since getting the computer, there is a chance the webcam driver will need to be recompiled. To do that, simply run your System76 Driver (System > Administration > System76 Driver > Install (tab) > Install (button)) and then reboot your computer.

TURNING YOUR WEBCAM ON
Knowing if your webcam is on can be a little tricky, as there is no LED or icon indicating its state. To find out if it is on, open a terminal (Applications > Accessories > Terminal) and run this command...
lsusb
...and then press the Fn-F10 buttons and run lsusb again. Your output from both runs of lsusb should differ by a single line. Here is my output from running lsusb, pressing Fn-F10, and then running lsusb again...

oem@ubuntu:~$ lsusb
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

...I pressed Fn-F10 here...

oem@ubuntu:~$ lsusb
Bus 008 Device 002: ID 5986:0300 Acer, Inc
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Notice that after I press Fn-F10 and run lsusb again, I see this line (which was not present on the first run of lsusb)...
Bus 008 Device 002: ID 5986:0300 Acer, Inc

That is the line that indicates my webcam is turned on. If I press Fn-F10 again and run lsusb, that line will be gone, indicating my webcam is turned off. Your line may differ slightly. The point is, if it appears and disappears when you press Fn-F10, it is your camera line.

APPLICATIONS THAT WORK WITH YOUR WEBCAM
Here are the applications that are known to work with your webcam:
1. Ekiga Softphone: It's already installed on your system (Applications > Internet > Ekiga Softphone)
2. Skype: Install via this tutorial: [http://knowledge76.com/index.php/Installing_Restricted_Formats](http://knowledge76.com/index.php/Installing_Restricted_Formats)
3. Cheese: Install by running this command in a terminal: sudo apt-get install cheese

USING YOUR WEBCAM WITH A SUPPORTED APPLICATION
I recommend getting your webcam going with Ekiga Softphone first. Ekiga has always worked well, whereas Cheese has be broken a couple of times and Skype may require some internal configuration.

1. First turn off all applications that use the webcam. If the application (like Ekiga and Skype) creates an icon in the upper toolbar, right-click that icon and select "Quit" in the resulting submenu. Just shutting the application window sometimes isn't good enough. If multiple applications are trying to connect with the webcam, it probably won't work.
2. Turn on your webcam per the instructions above.
3. Open your application. If you're using Ekiga, you probably will need to click the webcam icon on the left side of the Ekiga control panel.

You should now see yourself on the Ekiga control panel.

---

### Post by eddietours on 2009-02-25
will try that ones l get home thanks

---

### Post by steelbloo on 2009-02-25
Hi 
I have an old pc which I have installed ubuntu 8.1 onto.  Everything is working great.  I can get on the net and use skype2.  I want to use my phillips spc 300nc webcam.  The computer knows its 'there' because in the skype when i click 'test' it switches on, but the picture is like something out of the movie halloween !

I would really appriacte some help, but talk slowly as I am new to this and already realise theres lots of new pc terms I never knew exsisted !!  

Thanks for your help in advance.
Vicky

---

### Post by thomasaaron on 2009-02-25
Hi, Steelbloo. 

This forum is for supporting System76 computers. Not that I wouldn't help you if I could, but I don't have your particular hardware in my shop to test with.

---

### Post by steelbloo on 2009-02-25
Hi Thomasaaron
Thanks for your message.

Told you the new lingo would confuse me...!
System 76 !!!  LOL  ouch!

I'd love to get this old beasty working !  I really want to give it a go, I love the idea of not using windows!.
Again, thanks for your message.

If anyone else out there has been able to use a webcam in my situation, I'd love to hear from you.

Many thanks
Steelbloo
;)

---

### Post by eddietours on 2009-02-26
Hi thomasaaron l ran the system76 drivers then use the command on the terminal and l was able to see that cam is on , but ones l start ekiga it say's something problem with Bison pro cam l also try Cheese but nothing

---

### Post by thomasaaron on 2009-02-26
Try running this command...

echo options uvcvideo quirks=2 | sudo tee -a /etc/modprobe.d/uvc 

Then reboot.

Then, give it another try.

---

### Post by eddietours on 2009-02-26
yesss it works now thank you

---

### Post by Rasylver on 2009-02-27
Hi,

I have a Clevo laptop that seems to use the same webcam (I ran lsusb and googled the device ID which seems to be identical to the one above -  ID 5986:0300 Acer Inc and the Fn/F10 command turns it on/off too). I was wondering if it was possible for me to get a driver for my webcam from here or if they are system specific?

I seem to have the webcam working in a few applications (aMSN for one) but others such as ekiga and Cheese fail to use it. ekiga detects a USB 2.0 Camera but whatever channel I choose it just says it's unable to use it. Maybe if I get a proper driver for it, then it'll be more compatible than it is at the moment.

This is for Ubuntu 8.10 32-bit.

Thanks in advance.

---

### Post by thomasaaron on 2009-03-02
You can download and crack open the System76 driver and see how we compile the UVC code. However, if it is working for you already, that's probably not necessary.

Try turning off all other web cam apps before starting other apps (that means *completely* killing them... if they have an icon in the upper panel, right-click that icon and kill it). Otherwise, the cam might already be in use.

---

