---
title: "Focusrite scarlett 2i2 with wine usb issues"
date: 2012-03-06
forum: Ubuntu Studio
---

### Post by nicoldutoit on 2012-03-06
I use ubuntustudio 11.04 with a Focusrite Scarlett 2i2 audio interface. When I use Ardour, the audio interface seems to work fine.

I then installed Reaper using the Linreaper script, and proceded to install the latest Focusrite driver using winetricks.

When I try to open the Focusrite control panel, a message appears saying that no Focusrite USB 2.0 devices were found attached to the computor.

Is there some USB 2.0 support issue with wine 1.2.2, and how do I fix this?

Thanx
Nicol

---

### Post by sgx on 2012-03-08
Hi, try a fresh install of wine, install reaper to your
/home/username folder using the standard windows installer,
then in qjackctl, set Periods/Buffer in the Setup page,
to 3, which seems needed when using usb devices.

Stop and restart qjackctl, look at qjackctl Setup page

Input Device  >
Output Device > 

click the > and select your devices from the dropdown list.
If there are named entries for your Focusrite, use that instead
of a numeric hw:0,0 type of entry, which might change on reboot, if different devices are detected.

You should not need focusrite drivers or control panel to use the device in linux, as the support occurs in the kernel/modules.

Reaper has it's own extensive preferences, you'll need wineasio installed, select that
as your asio device, make the standard path to vsts: Program Files/Steinberg/VstPlugins
spelling accurate, as various installers need redirection to this exact path.
Cheers

---

