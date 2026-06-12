---
title: "Display Problem"
date: 2011-04-11
forum: System76 Support
---

### Post by daniel.cotter on 2011-04-11
I am not sure how to describe the problem accurately, but when I boot up recently, I have no video, just a tiny, corrupted patch of color where the cursor is.

It was about a month ago when I changed a video setting, but try as I might, I cannot find that setting to change it back.  I changed "Desktop video resolution", or something like that, from 8 bit to 24 bit color.  It made no apparent difference, except that occasionally, it would flash a garbled pattern right before the login screen appeared.  I did not pay much attention to it, until yesterday, when it stopped refreshing and went black instead of presenting the desktop.  I can poke around and click my username and log in, but the screen stays blank, with the exception of the tiny patch of colors where the cursor is.

This brings up a few questions:  First, how do I get the color changed to a lesser setting? Secondly, how do I restart properly when I can't see anything on the display. Thirdly, which of the nearly 40 log files will give me info on what is happening?

Excerpt from lshw:
*-display
                description: VGA compatible controller
                product: M92 [Mobility Radeon HD 4500 Series]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:46 memory:d0000000-dfffffff ioport:2000(size=256) memory:cfef0000-cfefffff memory:cfe00000-cfe1ffff

I am sure I am not supplying complete information. Hopefully this is enough to know where to start looking.  For now, I am not shutting down or restarting.

Thanks in advance for any help you can offer.

---

### Post by ajgreeny on 2011-04-11
Try the command ```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.confbak
```to rename your xorg.conf file, then logout and back in again.  You may then need to install the ATI driver you were using again, but it looks as if you are using the OS radeon driver, so that may not be needed.

If it makes no difference, you can rename the file back with ```
sudo mv /etc/X11/xorg.confbak /etc/X11/xorg.conf
```and you are back where you were.

---

### Post by daniel.cotter on 2011-04-11
> **ajgreeny said:**
> ... rename your xorg.conf file, then logout and back in again. 

Just log out and back in, or reboot?

---

### Post by daniel.cotter on 2011-04-11
It doesn't look like that .conf file is there:

<code>
/etc/X11$ ls -al
total 88
drwxr-xr-x  10 root root  4096 2011-04-11 15:54 .
drwxr-xr-x 151 root root 12288 2011-04-11 03:37 ..
drwxr-xr-x   2 root root  4096 2011-04-10 09:36 app-defaults
drwxr-xr-x   2 root root  4096 2011-03-05 20:01 cursors
-rw-r--r--   1 root root    14 2011-03-12 22:39 default-display-manager
drwxr-xr-x   6 root root  4096 2010-10-07 11:11 fonts
-rw-r--r--   1 root root 17394 2010-05-27 20:59 rgb.txt
lrwxrwxrwx   1 root root    13 2011-03-04 13:04 X -> /usr/bin/Xorg
drwxr-xr-x   3 root root  4096 2010-10-07 11:16 xinit
drwxr-xr-x   2 root root  4096 2010-04-15 07:12 xkb
-rwxr-xr-x   1 root root   709 2010-08-09 05:20 Xreset
drwxr-xr-x   2 root root  4096 2010-10-07 11:01 Xreset.d
drwxr-xr-x   2 root root  4096 2010-10-07 11:01 Xresources
-rwxr-xr-x   1 root root  3730 2010-08-09 05:30 Xsession
drwxr-xr-x   2 root root  4096 2011-04-10 09:18 Xsession.d
-rw-r--r--   1 root root   265 2010-05-27 20:59 Xsession.options
-rw-------   1 root root   601 2010-10-07 11:01 Xwrapper.config

</code>

---

### Post by ajgreeny on 2011-04-11
No, it's not, so I suspect you are definitely using the open source driver.

Rethink needed!  Try to remember what changes you made and undo them if possible.  many text files, if that is what you edited with gedit, may have backup files made by default, but I can't remember if that setting is the gedit default or not.  Look for filenames ending with tilda (~) meaning they are backups.

If that rings no bells, or you uninstalled or installed some packages there will be some record of it in the log files, or in synaptic's File ->History dialog.

---

### Post by daniel.cotter on 2011-04-11
I will look into it.  I have installed quite a few packages in the 2 months that I've owned it, and since my reinstall.  I'll look through the install history and see if removing anything helps.

Do you know which log will show the X errors at the time the display was blank?

---

### Post by isantop on 2011-04-12
It looks like you have a PanP7, right?Do you know where you made the setting change to go from 8-bit to 24-bit, or why it was at 8-bit in the first place? It should be 24-bit by default.

---

### Post by daniel.cotter on 2011-04-12
That's what I thought when i found it, and I am still looking for that screen I found.

PanP7, yes.

I have restarted a couple of times successful, but I still see shades of the color corruption.

I just woke up, and I have to go to work, but I will pursue it again in the morning.  Thanks for checking.

---

### Post by daniel.cotter on 2011-04-17
> **daniel.cotter said:**
> This brings up a few questions:  First, how do I get the color changed to a lesser setting? Secondly, how do I restart properly when I can't see anything on the display. Thirdly, which of the nearly 40 log files will give me info on what is happening?



I need to bump this post, because this is now a regular occurrence, and I have shut down with the power button a couple times, something I am loathe to do.

I am able to [Ctrl] +[Alt] + [F2}, etc... and run init 6 to restart, but if it is ever locked, I would like to be reminded of the keystroke sequence that can be used to shut down.  I used it while on the phone with Tech Support one day, but never recorded it or committed it to memory.  So if you can remind me of it, I would be thankful to you.

Also, while in command mode, I had an error message concerning my Radeon graphics hardware, but I couldn't record it to paste it in. I have been combing the .log files, but really don't know where to start.  any suggestions?

Thanks,
Daniel

---

### Post by isantop on 2011-04-18
Can you try activating the Proprietary ATI Driver? That will help single out a software/hardware issue.

---

### Post by daniel.cotter on 2011-04-19
> **isantop said:**
> Can you try activating the Proprietary ATI Driver? That will help single out a software/hardware issue.
I have successfully activated the ATI driver, and have rebooted many times, and it seems to have worked.  I thank you heartily, friend!

I have also managed to find the setting I changed originally: it is in the startup-manager, under Display Resolution.  It had been set to 8 bit, and I changed it to 24 bit.  I am leaving it at 24 bit for now, since it appears to have been fixed.

I also wonder now what driver it had been using.  But it is working well now -- thanks again.

---

