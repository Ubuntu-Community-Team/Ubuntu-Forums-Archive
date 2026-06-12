---
title: "HOW TO: Webcam on the DarU3, GazU1, PanP4, SerP5"
date: 2009-02-17
forum: System76 Support
---

### Post by thomasaaron on 2009-02-17
Folks seem to be having a lot of difficulty using their webcam on the DarU3, GazU1, PanP4, and SerP5. Here is a brief tutorial explaining how to get it working...

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

