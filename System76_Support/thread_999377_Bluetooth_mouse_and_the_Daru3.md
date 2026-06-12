---
title: "Bluetooth mouse and the Daru3"
date: 2008-12-01
forum: System76 Support
---

### Post by Spr0k3t on 2008-12-01
I've just received my lovely Darter.  Now I've got a question regarding the bluetooth module.

I can't seem to get bluetooth to load by default.  Also, I've got a bluetooth mouse I'm trying to get the system to use by default.

The system was shipped with 8.10.  The mouse is a logitech V470.  Ultimately I'd like to shut off the touchpad and use only the mouse without having to hit the key combination every time.

Any suggestions?

---

### Post by Lee_Machine on 2008-12-02
It's not turned on by default to save battery life. You can change that via a config file but I wouldnt as you will forget about it and loose battery time.

/etc/default/bluetooth is the file.

Press Fn F12 and bluetooth will activate. Then you can go to System > Preference > Bluetooth and choose Always display Icon. 

Then on the upper right corner right click the bluetooth icon and choose add new device.

The Wizard will start to add your mouse.

When ever you log in again just press Fn F12 again move the mouse around and it will work. Fn F1 will disable the trackpad. A nice thing since you will hit it while typing and screw things up.

Im looking for a way to configure the trackpad to stop working while typing so this wont happen and then have a delay of 1 second for the trackpad to turn on.

Anyone know how?

---

### Post by Spr0k3t on 2008-12-02
It must be a bug with the bluetooth stack.  I have to delete and re-add my mouse every single time I want to use it.  If the laptop is put in suspend, I have to delete and re-add the mouse.  If I reboot, same thing.

Now then, what about shutting off the touchpad by default so I don't have to Fn-1 every time?

---

### Post by thomasaaron on 2008-12-02
The command from the terminal to disable the touchpad is...

sudo modprobe -r psmouse

So, it may work to blacklist the psmouse module in /etc/modprobe.d/blacklist

If that didn't work, I'm sure you could add a start-up script to disable it.

Here is some good info for configuring bluetooth...
[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

I'm not aware of a way to bypass having to push Fn-F12 after every start-up.

---

