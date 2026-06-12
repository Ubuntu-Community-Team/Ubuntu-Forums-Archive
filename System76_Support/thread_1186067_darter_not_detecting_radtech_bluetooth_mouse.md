---
title: "darter not detecting radtech bluetooth mouse"
date: 2009-06-13
forum: System76 Support
---

### Post by tessk on 2009-06-13
hellooooo

just got a radtech bt550 bluetooth mouse. the bluetooth device wizard isn't listing it when i try to set it up. i'm on a new darter with jaunty.

when i first tried to set up the mouse, the wizard didn't detect it. but then after running
```
/etc/init.d/bluetooth start
```the wizard did list the device, and i paired it successfully. i used the mouse for a bit just fine. next time, and every time after, i haven't been able to get the mouse going again.

i tried running the same 'start' command as before, but that didn't work. i saw a recommendation to remove the mouse from the list of paired devices, but when i go to System > Preferences > Bluetooth , where that list is supposed to be, all I see is the attached screenshot (no list of paired devices).

where do i go from here?? please and thanks :D

tess

---

### Post by tessk on 2009-06-13
also: 1. i've made sure to have the mouse turned on and to have pushed the 'discoverable' button, 2. i've paired the mouse successfully with a macbook several times

---

### Post by drewbenn on 2009-06-13
That screenshot should have another tab.  The fact that it isn't there makes me guess that the Bluetooth daemon isn't running.  I did:
```
$ ps aux | grep blue
root      2901  0.0  0.0  28356  1856 ?        Ss   Jun12   0:03 /usr/sbin/bluetoothd
drewbenn  3584  0.0  0.7 175416 14756 ?        S    Jun12   0:00 bluetooth-applet
drewbenn 10847  0.0  0.0   7528   908 pts/0    S+   02:05   0:00 grep blue
$
```
If you do the same, I would guess that the /usr/sbin/bluetoothd process isn't running (I killed that process and the other tab in the Bluetooth properties went away; I restarted it and that tab came back; '/etc/init.d bluetooth stop' didn't affect that process, for me).

---

### Post by tessk on 2009-06-13
well the process seems to be running fine:

```

$ ps aux | grep blue
root      3423  0.0  0.0  28356  1668 ?        Ss   07:39   0:00 /usr/sbin/bluetoothd
tess      4030  0.0  0.3 175304 14456 ?        S    07:39   0:00 bluetooth-applet
tess      4551  0.0  0.0   7528   908 pts/1    R+   07:46   0:00 grep blue

```then i checked out System Monitor ... there is a bluetooth-applet shown to be running, but no mention of the bluetoothd process. see screenshot. is it jut me or is that strange?

tx

---

### Post by thomasaaron on 2009-06-13
1. Set the bluetooth preferences to show the icon "Only when device is present." Then click Fn-F12. This turns on your bluetooth -- and the icon should appear.

2. Then pair your mouse.

You have to press Fn-F12 whenever you start your computer. I've not found a way to automatically turn on the bluetooth adapter despite putting several hours into it.

---

### Post by tessk on 2009-06-13
alright a little improvement :) the device appeared, but then i received the message "Pairing with BT550 failed" from the Device Wizard

---

### Post by tessk on 2009-06-13
alright ... the system > preferences > bluetooth finally has the list of paired devices! so i was able to trash the bt550, and then pair to it successfully.

i am using the mouse as i post this :D

do i have to do this every time?

---

### Post by tessk on 2009-06-13
and thanks so much for helping drew & thomas

---

### Post by tessk on 2009-06-18
follow up question on this.
 
if i start up my computer, pressing fn-f12 isn't enough to get the mouse working. even if the mouse is set to be detectable or if it's just on. every time i start up i have to go into the bluetooth prefs, trash the mouse and then add it again.
 
once i've done that, i can turn the mouse off and on using fn-f12. the problem is only on a restart or fresh start.
 
is there a way to avoid the trash/add that i keep doing?
 
please&thanks :)

---

### Post by thomasaaron on 2009-06-18
I think this might help...
[http://www.ubuntugeek.com/howto-setup-bluetooth-keyboard-and-mouse-in-ubuntu.html](http://www.ubuntugeek.com/howto-setup-bluetooth-keyboard-and-mouse-in-ubuntu.html)

---

### Post by tessk on 2009-06-18
i don't have the file /etc/bluetooth/hcid.conf ! all i have in that directory is:

audio.conf  input.conf  main.conf  network.conf  rfcomm.conf

i guess they must have changed the package since that article was written in '07 ... can i apply the advice from the article to another file?

tx
tess

---

### Post by thomasaaron on 2009-06-19
Oops, sorry. I didn't notice how dated that was. Unfortunately, I don't have a bluetooth device here to test with, so I'm kind of shooting in the dark.

This is a similar bug (although it pertains more to bluetooth issues with suspend/resume). They have to delete and re-add the mouse.

[https://bugs.launchpad.net/ubuntu/+source/bluez-gnome/+bug/285007](https://bugs.launchpad.net/ubuntu/+source/bluez-gnome/+bug/285007)

There are some visibility settings mentioned that you can try.

Also, make sure the mouse is configured as a trusted device.

---

