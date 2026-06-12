---
title: "Key Status Monitor Alternatives?"
date: 2008-05-13
forum: The Cafe
---

### Post by saundesj on 2008-05-13
I'm trying to find an app to display keystrokes in my screencasts. Something similar to [KeyCastr]("http://stephendeken.net/wiki/software/keycastr/") on OS X. I found [Key Status Monitor]("http://programmer-art.org/projects/keystatus/") but couldn't get it running on Hardy. Can anyone recommend alternatives?

**Update: I got the Key Status Monitor to display keystrokes by changing my device location in the key-status file. Unfortunately, my touchpad refuses to play nice. It's bound to /dev/psaux but this throws an error when I put it in the config. Also, tried my mouse (/dev/mouse3 and /dev/mice) but it results in the same outcome. Looking for a solution.**

```
Traceback (most recent call last):
  File "./key-status", line 415, in <module>
    App = KeyStatusApp(decorated)
  File "./key-status", line 253, in __init__
    self.ms = Device(MOUSE_LOCATION)	#mouse
  File "/home/saundesj/Desktop/key-status-5/evdev.py", line 93, in __init__
    self.readMetadata()
  File "/home/saundesj/Desktop/key-status-5/evdev.py", line 109, in readMetadata
    self.name = ioctl(self.fd, EVIOCGNAME_512, buffer)
IOError: [Errno 25] Inappropriate ioctl for device
```

---

### Post by jorgecabral on 2008-05-31
Key Status works fine for me with this device locations:

```

# Device locations
KEYBOARD_LOCATION = "/dev/input/event1"
MOUSE_LOCATION 	  = "/dev/input/event5"

```

---

### Post by mayeulk on 2008-06-19
I have problem running key-status on Kubuntu 64 bits, Hardy Heron.
I've changed the events this way:

KEYBOARD_LOCATION = "/dev/input/event1"
MOUSE_LOCATION 	  = "/dev/input/event5"

Here is the error:


$ sudo ./key-status
[sudo] password for user:
Traceback (most recent call last):
  File "./key-status", line 316, in update
    self.ms.poll()
  File "/home/mk/bin/mouse/key-status-5/key-status-5/evdev.py", line 102, in poll
    self.update(Event(unpack=buffer))
  File "/home/mk/bin/mouse/key-status-5/key-status-5/evdev.py", line 509, in __init__
    self.unpack(unpack)
  File "/home/mk/bin/mouse/key-status-5/key-status-5/evdev.py", line 535, in unpack
    secs, usecs, packedType, packedCode, self.value = struct.unpack(self.format, s)
  File "/usr/lib/python2.5/struct.py", line 87, in unpack
    return o.unpack(s)
struct.error: unpack requires a string argument of length 32

---

### Post by secundar on 2008-10-28
Bump! Anyone have success? I'm also using Hardy 64bit.

---

### Post by Daniel G. Taylor on 2008-10-28
Hey guys. This issue has been bugging me for a while and every couple months I get request for a fix. I spent a while today digging around looking for a solution to this issue and couldn't find one, so I did the next best thing - dig into the kernel source! Here is what I found:

input.h defines an input_event struct which contains a time value (defined later in asm/posix_types_64.h as two longs) and two unsigned 16 bit integers followed by a single 32 bit signed integer. This means that the first two longs are system-dependant while the last three values are not, which in turn means we cannot just tell struct to unpack only system-dependant values as is done now. I've updated evdev.py to unpack the proper sizes now but I need some testers. Can anybody grab this updated version and test? It works perfectly for me here (64-bit).

[http://programmer-art.org/dropbox/evdev.py](http://programmer-art.org/dropbox/evdev.py)

If this works for others I will roll a new release.

---

### Post by secundar on 2008-10-28
Daniel! Thanks, so much for the update, it's working perfectly now (kernel 2.6.24-21-generic).

---

### Post by Daniel G. Taylor on 2008-10-28
That's great to hear. I just looked up how to use HAL through dbus and updated the code to automagically discover keyboard and mouse devices now as well, so no more messing with trying to find your devices by hand. New release is up on my site at:

[http://programmer-art.org/projects/keystatus](http://programmer-art.org/projects/keystatus)

Let me know if there are any issues.

---

### Post by Chrissss on 2008-11-22
Hello Daniel!

I just stumbled upon this thread. I try to use key-status6. I can start the program

$ sudo ./key-status 
Found multiple mouse devices, only using the last
Keyboard: /dev/input/event1
Mouse: /dev/input/event0

But when i hit any key or any mouse button nothing happens. Can you help me out?

Using Ubuntu Intrepid Ibex here.

CU
Christoph

---

### Post by aloyr on 2008-11-23
i am on the same boat as Chrissss, i see the exact same behavior on my intrepid box.

---

### Post by aloyr on 2008-11-23
dont know if it matters, but i am using kubuntu

---

### Post by Chrissss on 2008-12-13
[Here]("http://ubuntuforums.org/showthread.php?t=975281"), you'll find a thread with some infos, but it still doesn't work. To avoid the "autodetection" try to figure out the event ids of your mouse an keyboard. In my case it would be event10 for my mouse

```
$ sudo cat /proc/bus/input/devices
[...]
I: Bus=0005 Vendor=0000 Product=0000 Version=0000
N: Name="Bluetooth Mouse"
P: Phys=00:0B:5D:13:01:C2
S: Sysfs=/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/bluetooth/hci0/hci0:40/input35
U: Uniq=00:0A:94:C0:84:11
H: Handlers=mouse3 event10 
B: EV=17
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103
B: MSC=10

```

then open key-status inside a editor an change "dev.GetProperty("input.device")" into your device-ids... You'll finde these lines at about line 80 and 90


```
    #KEYBOARD_LOCATION = dev.GetProperty("input.device")
    KEYBOARD_LOCATION = "/dev/input/event1"
[...]
    #MOUSE_LOCATION = dev.GetProperty("input.device")
    MOUSE_LOCATION = "/dev/input/event10"

```

After this key-status will use the devices you entered, but still, it doesn't work here. Neither keyboard, nor my touchpad, nor my BT-mouse...

---

### Post by kagou on 2009-02-02
Same problem here :(

---

### Post by Daniel G. Taylor on 2009-02-02
Hey everyone, sorry this has taken me so long to look into. I've been busy with a move to the Netherlands and life in general but the issue has been tracked down to a problem with xserver and evdev. See the bug here, and feel free to leave comments if you'd like a fix backported. Currently the solution seems to be to update to jaunty.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/324382](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/324382)

---

### Post by aloyr on 2009-02-23
Daniel, 

Setting 'Option "AutoAddDevices" "false"' in the ServerFlags section like Timo suggested on LP and manually setting MOUSE_LOCATION as suggested by Chrissss worked for me! 

Thanks.

---

### Post by Kabeer on 2009-03-25
Hello there.
I don,t really know if this will help but I used a much simpler technique. I have wine installed on my Ubuntu, so I used skrommel's software called "Showoff". It is not as animated as key status monitor by programmer art.
I thought I might share this as you guys have helped me a lot.
The URL for the software is [http://www.donationcoder.com/Software/Skrommel/](http://www.donationcoder.com/Software/Skrommel/)
Have a nice day
Kabeer

---

### Post by Daniel G. Taylor on 2009-03-25
By the way, I believe this is entirely fixed in the next Ubuntu release. I'll be testing it soon and will post the results. Sorry about all the confusion *shakes hand at Xorg*

---

### Post by scott_kirkwood on 2009-11-27
Daniel's Key Status Monitor is pretty neat, I had some free time last weekend and thought I might be able to improve upon it.
I rewrote the program from scratch adding a few new features:

[LIST]
[*]I'm hosting the code on code.google.com so anyone can contribute or submit bug reports more easily.
[*]The dialog can be resized to any size, since I'm using SVG as the source and not bitmapped images.
[*]Support for the meta (aka Windows) key.
[*]Support for the scroll wheel.
[*]You can move the window more easily (click anywhere and drag).
[*]I have a right click menu for some features.
[*]You can add or remove the mouse and/or meta key if that's not required.
[*]It defaults to not having window chrome and defaults to being "Always on Top".
[/LIST]

Hope it proves useful.
[http://code.google.com/p/key-mon](http://code.google.com/p/key-mon)

I've blogged about it at:
[http://scottkirkwood.blogspot.com/2009/11/created-another-open-source-utility-key.html](http://scottkirkwood.blogspot.com/2009/11/created-another-open-source-utility-key.html)
and
[http://scottkirkwood.blogspot.com/2009/11/additions-to-key-mon.html](http://scottkirkwood.blogspot.com/2009/11/additions-to-key-mon.html)

---

### Post by Daniel G. Taylor on 2009-11-28
Very cool. I'm glad someone with more time is able to keep working on this kind of stuff. My only real complaint is defaulting to no chrome which is very inconsistent with all other applications, the rest of the app is fantastic! I really should have thrown my code on github a looong time ago. Either way I'll be updating my pages to push everyone to your new app!

I'm not entirely sure how Google Code works (I'm used to GitHub and can't figure out how to push a merge request to you via Google's site) but I attempted to clone and push some changes, see the diff here:

[http://code.google.com/r/danielgtaylor-keymon/source/detail?r=150658b00b7149ea379d48abcfca0b415a307213](http://code.google.com/r/danielgtaylor-keymon/source/detail?r=150658b00b7149ea379d48abcfca0b415a307213)

It adds support for dynamically plugging or unplugging any number of keyboards / mice while the application is running, which is useful on my laptop. The code is borrowed and modified from one of my newer projects and I've put it under an MIT license this time - do with it what you like. Feel free to merge that into your tree.

Some potential features to think about:

 * Allow resizing from the edges (or even just bottom right edge)
 * Allow disabling certain input devices without physically unplugging them
 * Windows support (my #1 support request with keyboard status monitor)
 * It should be trivial to add theme support for key images
 * It would be cool if we could somehow visualize single vs. double clicks

As for the theme:

 * IMO the mouse buttons could be larger so they are easier to see
 * Might be nice to choose a meta symbol that isn't Windows-specific

Also, what is this licensed under? "All rights reserved" means we cannot legally make copies of your software, even for our own use - you may want to look at the GPL/LGPL/BSD/MIT licenses and pick one of those. The WTFPL can be fun too :-P

Anyway none of this is meant in a negative way, your app is awesome! Keep up the great work.

---

### Post by Vadi on 2009-11-28
Glad this app has gotten attention, I use it frequently but having to start it in terminal w/ sudo was getting tedious.

---

