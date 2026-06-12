---
title: "Cheese starts upon resume"
date: 2008-11-06
forum: System76 Support
---

### Post by stewpac on 2008-11-06
Since I upgraded to 8.10 I've noticed suspend works great but whenever I resume from it cheese (webcam app) is running automatically. Any thoughts as to how I can get it to stop doing that? Cheese works fine, by the way. I'm on a gazp5 (with the Nvidia-webcam option, obviously) with the latest sys76 driver.

Thanks in advance.

---

### Post by thomasaaron on 2008-11-06
I just tried to duplicate that, and it's not happening for me.

Is cheese listed in System > Prefs > Sessions?
It must be in a start-up script somewhere.

---

### Post by stewpac on 2008-11-06
No it's not listed there. Sorry, I should have mentioned that. I should also mention that it doesn't come up at startup - only when resuming from suspend. Where is the file which stores the information in the Sessions box? Where are the suspend scripts? Long ago (on another distribution and a different computer) I remember having problems with usb ports being dead when resuming. A friend of mine fixed that for me by editing the resume script to shut them down and restart them. The camera here is listed as a usb device - are there any such commands in the sys76 driver to make suspend and resume work?

---

### Post by thomasaaron on 2008-11-06
Look in /etc/acpi/resume.d/

You might want to grep all of those files for "cheese" with something like...

cat /etc/acpi/resume.d/* | grep -i cheese

It won't tell you where it is, but it should tell you if it's there anywhere. (i.e. it's just a place to start).

---

### Post by stewpac on 2008-11-06
Yeah...I ran that but got nothing. I also tried looking for init.d and video0 but got nothing there as well. Where is the file where sessions apps are stored?

Actually I found that file: ~.gnome2/sessions. As suspected no extra cheese entry.

---

### Post by thomasaaron on 2008-11-06
I've not been able to find it. It may not be a file, per se. It may create start up programs that go in the /etc/init.d

Try un-installing cheese,
then restart your computer,
then re-install cheese

---

### Post by stewpac on 2008-11-06
No dice on the reinstall. This is really quite strange. Could it have something to do with a setting in Nvidia X server settings? I'm grasping at straws now.

---

### Post by thomasaaron on 2008-11-07
Probably not.

Go to System > Prefs > Sessions > Preferences
and make sure "Remember running apps when logging out" is not checked.

---

### Post by stewpac on 2008-11-07
No, that's not checked. Any other ideas?

---

### Post by thomasaaron on 2008-11-07
Running out of them pretty quickly, actually.

It would have to be started by a script in /etc/acpi/resume.d or a cron job, or something.

After resuming, run...
cat /var/log/messages | grep -i cheese
cat /var/log/syslog | grep -i cheese
dmesg | grep -i cheese

See if any of those record cheese being launched. If they do, we can take it from there.

**LAST-DITCH LAME HACK**
You could create a script in resume.d that kills cheese as a last matter of business after resuming.

Save a text file on your desktop (name it... 99-cheesekiller.sh) that has this in it...

```
#!/bin/sh
killall cheese
```

Then run these commands from a terminal...

```
cd Desktop
install 99-cheesekiller.sh /etc/acpi/resume.d
```

Now, REBOOT.
THEN, try to suspend and resume.

---

### Post by stewpac on 2008-11-08
Ok...even weirder. I checked to see if those logs record cheese launching. They don't. I tried the "lame hack." I don't know what to say...it still starts!

Update: I thought the only thing left would be if cheese started just before suspending and was just resumed normally. I tried putting the script above in /etc/acpi/suspend.d however, that didn't work either

---

### Post by jdb on 2008-11-08
> **stewpac said:**
> Ok...even weirder. I checked to see if those logs record cheese launching. They don't. I tried the "lame hack." I don't know what to say...it still starts!

Update: I thought the only thing left would be if cheese started just before suspending and was just resumed normally. I tried putting the script above in /etc/acpi/suspend.d however, that didn't work either

Open a terminal & type:

ps -ef

Look for the entry for cheese.
The PPID is the PID of the process that started it.
If the PPID is not 1, it may give you a hint.

jdb

---

### Post by stewpac on 2008-11-08
Thanks for the idea:

stew@bender:~$  ps -ef |grep -i cheese
stew      7886     1  0 23:40 ?        00:00:00 /bin/sh -c cheese --hal-device=/org/freedesktop/Hal/devices/usb_device_4f2_b018_SN0001_if0_video4linux
stew      7887  7886 37 23:40 ?        00:00:07 cheese --hal-device=/org/freedesktop/Hal/devices/usb_device_4f2_b018_SN0001_if0_video4linux


so I guess that means the PPID is 1.

---

### Post by jdb on 2008-11-09
> **stewpac said:**
> Thanks for the idea:

stew@bender:~$  ps -ef |grep -i cheese
stew      7886     1  0 23:40 ?        00:00:00 /bin/sh -c cheese --hal-device=/org/freedesktop/Hal/devices/usb_device_4f2_b018_SN0001_if0_video4linux
stew      7887  7886 37 23:40 ?        00:00:07 cheese --hal-device=/org/freedesktop/Hal/devices/usb_device_4f2_b018_SN0001_if0_video4linux


so I guess that means the PPID is 1.

Some script somewhere has "/bin/sh -c cheese" or some string of variables that equates to that in it.
The script would probably either be  in your home directory or in /etc .


A brute force method of looking around is:

grep -R cheese /etc 2>/dev/null
grep -R cheese ~/ 2>/dev/null

The "2>/dev/null" filters out grep error messages, it makes the output much easier to read.

jdb

---

### Post by Thomaseov on 2008-11-19
> **stewpac said:**
> Since I upgraded to 8.10 I've noticed suspend works great but whenever I resume from it cheese (webcam app) is running automatically. Any thoughts as to how I can get it to stop doing that? Cheese works fine, by the way. I'm on a gazp5 (with the Nvidia-webcam option, obviously) with the latest sys76 driver.

Thanks in advance.

I've got the same thing going on.  Cheese just launches whenever I resume from suspend.  I'm not positive, but i seem to recall this happening in Hardy as well.  (Intrepid, Nvidia geforce 7600 graphics, Phillips webcam)  This doesn't happen on  my three other computers running intrepid, just the main one.  So its going to be hardware specific in some way.  

Thomas

---

### Post by korvus81 on 2008-11-20
I should point out that I'm not using 8.10 and I never use suspend, so take this with a grain of salt. :)

I wonder if Cheese isn't considered the "run this when I plug in a webcam" program?  Much like F-Spot tries to run when I plug in a digital camera, Cheese may try to run when you plug in a webcam.  And when you come out of suspend, all your USB devices typically act like they've just been plugged in.  

If this is the case, I'd expect if you went into a Nautilus window, went to Edit->Preferences, and went to Media, it would have an option there for it.  I know that's typically more for devices that show up as drives, but maybe in 8.10 they added support for other devices....

Just a thought.

---

### Post by sistoviejo on 2008-12-31
The same thing happens to my laptop upon resume. Is there a known fix to this?
This might be a generic issue.
It's certainly not specific to System76 laptops because my laptop is an HP Pavilion tx1215nr.

---

### Post by EnderEcho on 2008-12-31
Just out of curiosity did you put it in suspend and then resume after uninstalling?

Did you --purge?

Just want to be clear on the process.

---

### Post by stewpac on 2008-12-31
I didn't do a --purge, I uninstalled through synaptic and did "complete removal." I also don't have the problem anymore but only because I don't have the computer anymore. I never did find a fix...

---

