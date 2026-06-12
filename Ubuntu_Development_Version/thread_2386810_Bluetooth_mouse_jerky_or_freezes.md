---
title: "Bluetooth mouse jerky or freezes"
date: 2018-03-10
forum: Ubuntu Development Version
---

### Post by NZjelle on 2018-03-10
I'm using a Logitech M557 bluetooth mouse with a Google Pixel Chromebook  version from 2013. Occassionally the mouse movements will become very  jerky or freeze altogether. I have not been able to identify anything  specific that triggers it. Sometimes it will be fine for hours,  including time spent away from the machine, and then suddently freezes  up. The only strange clue I have is that I can remedy it by using the  trackpad to open the blueman-manager applet. I don't actually have to do  anything in the applet. Just opening it usually gets the mouse to  respond again.

I have been using Bionic since the daily build of 24 Feb. I'm finding it  very stable and reliable on my laptop, except for this strange quirk.  It seemed to get worse after the large number of updates about two weeks  ago, although in recent days it's slightly better; i.e. the freezes are  less frequent now.

I have disabled the touchscreen function of the Pixel Chromebook, so  only the touchpad is available as alternative to mouse input.

I have not been able to identify any pattern to these bluetooth mouse  freezes. At this stage I'm just wondering if anyone else has experienced  the same?

---

### Post by kerry_s on 2018-03-10
i read from other posts that there could be issues with bluetooth on *ubuntu 18, suggest waiting it out, i'm sure a fix will come done the line.

---

### Post by flocculant on 2018-03-11
> **NZjelle said:**
> I'm using a Logitech M557 bluetooth mouse with a Google Pixel Chromebook  version from 2013. Occassionally the mouse movements will become very  jerky or freeze altogether. I have not been able to identify anything  specific that triggers it. Sometimes it will be fine for hours,  including time spent away from the machine, and then suddently freezes  up. The only strange clue I have is that I can remedy it by using the  trackpad to open the blueman-manager applet. I don't actually have to do  anything in the applet. Just opening it usually gets the mouse to  respond again.

I have been using Bionic since the daily build of 24 Feb. I'm finding it  very stable and reliable on my laptop, except for this strange quirk.  It seemed to get worse after the large number of updates about two weeks  ago, although in recent days it's slightly better; i.e. the freezes are  less frequent now.

I have disabled the touchscreen function of the Pixel Chromebook, so  only the touchpad is available as alternative to mouse input.

I have not been able to identify any pattern to these bluetooth mouse  freezes. At this stage I'm just wondering if anyone else has experienced  the same?
I would be inclined to report this as a bug. 

ubuntu-bug bluez

You could try - immediately after a freeze - seeing if anything blue related stands out in logs in /var/log , also  ```
journalctl | grep blue*
``` in a terminal (I'm not completely sure if all the logs go to journalctl) . Further check .xsession-errors in your home folder.

> **kerry_s said:**
> i read from other posts that there could be issues with bluetooth on *ubuntu 18, suggest waiting it out, i'm sure a fix will come done the line.

That's a very specific boot issue (assuming you mean the one I posted yesterday ;) ) - it could possibly be related, but I'd prefer the op reported it - unfortunately it's rather late in the day if it's something Xubuntu ish - not much time to release, not many devs ...

---

### Post by NZjelle on 2018-03-11
Thank you for that advice. My mouse just froze again. After unfreezing it by starting the blue-man applet, I followed your suggestions.

A potentially relevant line in my /var/log/syslog was:
```
Mar 12 14:23:11 CrPix1804 gvfsd-metadata[3597]: g_udev_device_has_property: assertion 'G_UDEV_IS_DEVICE (device)' failed
```

The journalctl comand in the terminal did not provide anything that looked relevant.

The .xsession-errrors file had the following lines:
```
(mousepad:10222): Gtk-WARNING **: 14:23:37.432: Theme parsing error: <data>:2:29: The style property GtkButton:default-border is deprecated and shouldn't be used anymore. It will be removed in a future version

(mousepad:10222): Gtk-WARNING **: 14:23:37.432: Theme parsing error: <data>:3:37: The style property GtkButton:default-outside-border is deprecated and shouldn't be used anymore. It will be removed in a future version

(mousepad:10222): Gtk-WARNING **: 14:23:37.432: Theme parsing error: <data>:4:27: The style property GtkButton:inner-border is deprecated and shouldn't be used anymore. It will be removed in a future version

(mousepad:10222): Gtk-WARNING **: 14:23:37.432: Theme parsing error: <data>:5:31: The style property GtkWidget:focus-line-width is deprecated and shouldn't be used anymore. It will be removed in a future version

(mousepad:10222): Gtk-WARNING **: 14:23:37.432: Theme parsing error: <data>:6:28: The style property GtkWidget:focus-padding is deprecated and shouldn't be used anymore. It will be removed in a future version
```

I'm not sure if any of that is relevant, but hopefully it can provide a clue for someone.

---

### Post by NZjelle on 2018-03-16
Just to add that today's updates, including the kernel update, have made the interruptions substantially worse. My mouse is now jerking around most of the time, and I have not been able to find a way to get a consistently smooth response.

---

### Post by flocculant on 2018-03-16
> **NZjelle said:**
> Just to add that today's updates, including the kernel update, have made the interruptions substantially worse. My mouse is now jerking around most of the time, and I have not been able to find a way to get a consistently smooth response.

Bug number?

---

### Post by NZjelle on 2018-03-16
I haven't filed a formal bug report (yet) because right now I cannot even reproduce the problem myself. Today, for example, everything is fine and I'm not having problems. I haven't found any pattern when it may arise, which is why my original question was only whether anyone else was experiencing the same trouble with bluetooth mouses.

---

### Post by flocculant on 2018-03-17
> **NZjelle said:**
> J... have made the interruptions substantially worse. My mouse is now jerking around most of the time, and I have not been able to find a way to get a consistently smooth response...

> **NZjelle said:**
> I haven't filed a formal bug report (yet) because right now I cannot even reproduce the problem myself. ...

Maybe try this. Open a terminal - run ```
journalctl -f
``` in it. Leave the terminal open - minimize it maybe or something if you want - but don't close it. Go about your business - if you see the issue - check what the last few lines of journalctl show.

---

### Post by NZjelle on 2018-03-18
Thank you for that suggestion. I have followed it. I did not have any problems yesterday, but the mouse just froze again today. Last lines from journalctl were:

Mar 19 09:54:46 CrPix1804 dbus-daemon[771]: [session uid=1000 pid=771] Activating via systemd: service name='org.gtk.vfs.Metadata' unit='gvfs-metadata.service' requested by ':1.80' (uid=1000 pid=868 comm="Thunar --daemon " label="unconfined")
Mar 19 09:54:46 CrPix1804 systemd[746]: Starting Virtual filesystem metadata service...
Mar 19 09:54:46 CrPix1804 dbus-daemon[771]: [session uid=1000 pid=771] Successfully activated service 'org.gtk.vfs.Metadata'
Mar 19 09:54:46 CrPix1804 systemd[746]: Started Virtual filesystem metadata service.

I also got lines in the .xsession-errrors file that were practically the same as I listed previously.

I have no idea why starting a virtual file system would or could freeze my mouse, but it's the only clue I have.

---

### Post by NZjelle on 2018-03-19
I just got a hard crash of bluetooth. This is what syslog shows:

Mar 19 17:05:51 CrPix1804 kernel: [29152.236197] usb 1-1.2: Failed to suspend device, error -110
Mar 19 17:06:17 CrPix1804 kernel: [29178.762000] Bluetooth: hci0: command 0x1405 tx timeout
Mar 19 17:06:19 CrPix1804 kernel: [29180.778017] Bluetooth: hci0: command 0x1403 tx timeout
Mar 19 17:06:21 CrPix1804 kernel: [29182.794149] Bluetooth: hci0: command 0x0c2d tx timeout
.... REPEATING ...

I will reboot now because bluetooth has frozen up completely

---

### Post by flocculant on 2018-03-19
Do you have a crash report in /var/log/crash for it?

Please report it with ubuntu-bug ...

---

### Post by erkiha on 2018-03-19
I recently had also bluetooth issues, described in this bug report: [https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1756824](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1756824) if you have intel wifi/bluetooth hardware then possibly this is the fix.

---

### Post by NZjelle on 2018-03-20
No. It did not give a log in crash.

---

### Post by NZjelle on 2018-03-20
I don't think I have the same issue because Bluetooth connects without problems on startup. I haven't found any pattern why it occassionally drops out and then comes back again.

The strange thing in my syslog from yesterday about usb device disconnecting makes no sense because I do not have any USB devices connected to my laptop.

---

