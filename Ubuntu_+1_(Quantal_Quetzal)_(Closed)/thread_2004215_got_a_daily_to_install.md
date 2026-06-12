---
title: "got a daily to install"
date: 2012-06-15
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ronacc on 2012-06-15
well I finally got a daily to actually install , yeah , but there are problems , boo . nautilus has no preferences that I can find , see SS's  , 1st is as it was , 2nd is as it is . Very sluggish to go from login to DT unity or G-S. network sometimes don't come up automatically even when plugged into a cable , works ok when it does.

---

### Post by jppr on 2012-06-15
Today I did fresh daily-live installation and I don´t have any problems, system works and run just fine :popcorn:

---

### Post by VMC on 2012-06-15
The only way I found to edit preferences was to use dconf-editor:
org/gnome/nautilus/preferences

Then change to your liking.

---

### Post by ronacc on 2012-06-15
thanks VMC , I had tried gconf-editor .

---

### Post by ventrical on 2012-06-15
The 'daily-live' finally works with ATi cards and has done a flawless install. The opening screen is still distorted but I just waited and then 'Install Ubuntu'.  The 'alternate' has worked good also.

---

### Post by ventrical on 2012-06-15
> **ronacc said:**
> well I finally got a daily to actually install , yeah , but there are problems , boo . nautilus has no preferences that I can find , see SS's  , 1st is as it was , 2nd is as it is . Very sluggish to go from login to DT unity or G-S. network sometimes don't come up automatically even when plugged into a cable , works ok when it does.


sorry .. what desktop are you running?

---

### Post by mc4man on 2012-06-15
nautilus preferences is now an app menu (gnome) so you need to do as in screen
(not yet available in unity*

---

### Post by ronacc on 2012-06-15
@ ventrical  gnome-shell ( although unity is there by default ) sys is amd64+nvidia .

@ mc4man  thanks . although as per VMC dconf-editor will get it , the menu is easier and I'm lazy .

---

### Post by balloons on 2012-06-15
Glad to hear you've had success! I am planning on trying to get a feel for any brokenness next week by asking folks to take a daily for a spin at some point next week in preparation for the alpha 2 iso testing. Reporting your result (pass or fail, with bugs) helps me out. If it goes in the tracker I can monitor it and follow the bug reports, etc. Plus it lets me know what shape the iso's are in. As such, I really appreciate reports in the tracker. And of course, I am happy to hear comments on making it easier to report -- we got good feedback from the "call for testing" qatracker build and changes are coming next week with some enhancements towards that. So feel free to speak up ;-)


[http://iso.qa.ubuntu.com/qatracker/milestones/219/builds](http://iso.qa.ubuntu.com/qatracker/milestones/219/builds)

P.S. If you put the result it in the tracker already thanks ;-) It's hard to know what lp name = forum username, so I'm just making sure :-)

---

### Post by ventrical on 2012-06-15
I,m trying the daily now on an older nVidia adapter card , 2,2GHz Gigabyte MoBo. Alternate worked good but previous attempts at 'live' daily did not. Looks good so far.

  @guitara,

I'll try those  iso trackers again.

EDIT:

That was a good install.

Had to settle for Unity 2D because this adapter card is old. 

  I haven't used GNOME shell in a while .. hmmm..

---

### Post by jerrylamos on 2012-06-15
> **ventrical said:**
> The 'daily-live' finally works with ATi cards and has done a flawless install. The opening screen is still distorted but I just waited and then 'Install Ubuntu'.  The 'alternate' has worked good also.

Not with this ATI:

Advanced Micro Devices [AMD] nee ATI Wrestler [Radeon HD 6310]

Systems Settings Displays bombs out bug #1007588:

GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such interface `org.gnome.SettingsDaemon.XRANDR_2' on object at path /org/gnome/SettingsDaemon/XRANDR

So I get partial recovery with command line xrandr to set screen resolution....

15 June daily build the following problem fixed:  On another one, ATI radeon xpress 200, the startup disk "Try Ubuntu..." only works if the startup disk is booted with "nomodeset".  Shades of old Intrepid bugs.  Once installed running O.K. for an Alpha 1.

Jerry

---

### Post by ventrical on 2012-06-18
@ Jerrylamos,

had you tried the alternate iso?

edit: probably you have .. just checking.

---

### Post by jerrylamos on 2012-06-20
Thanks, they just fixed bug #1007588 probably some bug(s) in the scripts.  Fix released and it is in the updates. Running fine now (for an Alpha 1).

After update I can set resolutions on the laptop display 1366x768 and the external monitor 1280x1024 and on reboot comes up with the laptop display hidden and the external monitor set right.

laptop monitor still coming on "full bright" with no brightness setting possible in the Systems Settings Brightness and Lock.  Acer Aspire 5253 widescreen notebook.  Hammer on the keyboard to get to reasonable display.

Jerry

---

