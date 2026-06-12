---
title: "No Ubuntu Daily Live?"
date: 2014-06-04
forum: Ubuntu Development Version
---

### Post by Yahoé on 2014-06-04
There is no utopic-desktop-amd64.iso since 20th May. Do we know why?

---

### Post by grahammechanical on 2014-06-04
It could be that the ISO image is seriously broken. Two days ago I used a superseded ISO image from 20th May because images from 27th, 28th, 31st and 2nd June would not run the installer (Ubiquity). The two icons on the live session desktop would not load the installer and pressing Enter twice and selecting Install from the first purple screen did not load the installer either. So, that is my guess.

I do see an image on the QA tracker from today, 20140604. I have not tested it so I cannot say if it will download or if it will install.

Regards.

---

### Post by oldfred on 2014-06-04
I just zsync'd my image, but old one was almost a month old. It was only 60% current, so updated 40%.

zsync [http://cdimage.ubuntu.com/daily-live/current/utopic-desktop-amd64.iso.zsync](http://cdimage.ubuntu.com/daily-live/current/utopic-desktop-amd64.iso.zsync)

Read utopic-desktop-amd64.iso. Target 57.8% complete.      
downloading from [http://cdimage.ubuntu.com/daily-live/current/utopic-desktop-amd64.iso:](http://cdimage.ubuntu.com/daily-live/current/utopic-desktop-amd64.iso:)

Have  not tried booting it yet.

---

### Post by Elfy on 2014-06-04
All images are apparently fubar currently.

> [15:00] <cjwatson> I can't vouch for whether the images actually *work* with syslinux 6, but I guess we'll find out
[15:00] <cjwatson> elfy: queued

From a day or two ago.

---

### Post by PaulW2U on 2014-06-04
> **Yahoé said:**
> There is no utopic-desktop-amd64.iso since 20th May. Do we know why?

I've been zsyncing images dated 2nd, 3rd and 4th June for all Ubuntu flavours.

I haven't had the opportunity to see if any of the images that I have downloaded actually work but there were obviously problems during the last week of May as previous posts imply.

For today, Ubuntu, Kubuntu, Xubuntu and Ubuntu GNOME are all _downloadable_. I think Lubuntu will probably be ok when it's made available in a couple of hours time.

---

### Post by Elfy on 2014-06-04
All the results for the autopilot testing of installs for all versions tested are currently RED. 

I can get past the non-appearance of the language window, boots past the non-appearing Try or Install choice, but falls at the last hurdle - running the installer. [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1325632](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1325632)

---

### Post by PaulW2U on 2014-06-04
I have tried both the Kubuntu and Xubuntu images for 4th June and I am seeing the following on booting my USB drive:

```
gfxboot.c32: not a COM32R image
boot:
```

I don't understand what this means so I'll be staying well clear of ISO testing for the time being. :)

---

### Post by ventrical on 2014-06-06
********************************************************************************Read utopic-desktop-amd64.iso. Target 100.0% complete.      
verifying download...checksum matches OK
used 1024458752 local, fetched 0
dale@dale-desktop:~/Desktop$ 


There's nothing except from May 20.

---

### Post by Elfy on 2014-06-06
> **ventrical said:**
> ********************************************************************************Read utopic-desktop-amd64.iso. Target 100.0% complete.      
verifying download...checksum matches OK
used 1024458752 local, fetched 0
dale@dale-desktop:~/Desktop$ 


There's nothing except from May 20.

I'd check what you're targetting with zsync - they are building daily still, still red across the board though.

---

### Post by sparker256 on 2014-06-06
The current is what has a issue.

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

This is what current should look like

[http://cdimage.ubuntu.com/daily-live/20140606/](http://cdimage.ubuntu.com/daily-live/20140606/)

Not sure where to report this?

Bill

---

### Post by Elfy on 2014-06-06
> **sparker256 said:**
> The current is what has a issue.

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

This is what current should look like

[http://cdimage.ubuntu.com/daily-live/20140606/](http://cdimage.ubuntu.com/daily-live/20140606/)

Not sure where to report this?

Bill

Not sure what it is you're saying needs reporting :)

---

### Post by mc4man on 2014-06-06
> **Elfy said:**
> All the results for the autopilot testing of installs for all versions tested are currently RED. 

I can get past the non-appearance of the language window, boots past the non-appearing Try or Install choice, but falls at the last hurdle - running the installer. [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1325632](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1325632)

edit: no longer an issue, may not of been with 06/06 as I may not of waited long enough..

---

### Post by ventrical on 2014-06-06
> **Elfy said:**
> I'd check what you're targetting with zsync - they are building daily still, still red across the board though.

```

zsync -i ./utopic-desktop-amd64.iso http://cdimage.ubuntu.com/daily-live/current/utopic-desktop-amd64.iso.zsync


```

---

### Post by ventrical on 2014-06-06
> **sparker256 said:**
> The current is what has a issue.

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

This is what current should look like

[http://cdimage.ubuntu.com/daily-live/20140606/](http://cdimage.ubuntu.com/daily-live/20140606/)

Not sure where to report this?

Bill


ahhhhh .. yes... sheesh..thxs

---

### Post by startas on 2014-06-07
Well, no, the problem is broken daily images. While there exists isos in [http://cdimage.ubuntu.com/daily-live/20140606/](http://cdimage.ubuntu.com/daily-live/20140606/) kind of folders, it isnt in [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/) because these iso files are broken.

---

### Post by sparker256 on 2014-06-07
I used this zsync command.

zsync -i utopic-desktop-amd64-20140606.iso [http://cdimage.ubuntu.com/daily-live/20140607/utopic-desktop-amd64.iso.zsync](http://cdimage.ubuntu.com/daily-live/20140607/utopic-desktop-amd64.iso.zsync) -o utopic-desktop-amd64-20140607.iso

I then used 14.04 Startup Disk Creator because 14.10 would not work and could boot the USB thumb drive.

 I am thinking the iso must be ok just something in how current is looking is the issue.

Bill

---

### Post by mc4man on 2014-06-07
> **sparker256 said:**
>  and could boot the USB thumb drive.

 I am thinking the iso must be ok just something in how current is looking is the issue.

Bill
The current issue isn't whether one can boot to live session, it's whether the installer will run.
Have you tried that on the 06/07  image?

---

### Post by kansasnoob on 2014-06-07
> **mc4man said:**
> I would think this will be fixed shortly
Trying the june 6 iso from QA it appears ubiquity fails to acquire_lock(), failing at 

if 'DEBIAN_HAS_FRONTEND' not in os.environ:
        # Do a quick check to see if the debconf database is locked by
        # something else.
.....
If I remove that if section from the script (totally, 100%  not recommended), then the installer will launch & proceed

I'm not quite following what file to edit :redface:

I'd like to do a fresh install of Ubuntu GNOME Utopic because I'm making some comparisons against minimal installs (adding various desktop environments via a chroot) and actual packages installed in a default out-of-box install via live image.

---

### Post by mc4man on 2014-06-07
> **kansasnoob said:**
> I'm not quite following what file to edit :redface:

I'd like to do a fresh install of Ubuntu GNOME Utopic because I'm making some comparisons against minimal installs (adding various desktop environments via a chroot) and actual packages installed in a default out-of-box install via live image.

Just tried the current 'Ubuntu' iso & it works fine, takes a little while to actually open the installer
So maybe get the current ubuntu gnome iso from here & see

[http://iso.qa.ubuntu.com/qatracker/milestones/315/builds](http://iso.qa.ubuntu.com/qatracker/milestones/315/builds)

---

### Post by kansasnoob on 2014-06-08
> **mc4man said:**
> Just tried the current 'Ubuntu' iso & it works fine, takes a little while to actually open the installer
So maybe get the current ubuntu gnome iso from here & see

[http://iso.qa.ubuntu.com/qatracker/milestones/315/builds](http://iso.qa.ubuntu.com/qatracker/milestones/315/builds)

I got hung up on the netboot images anyway:

[https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/1327825](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/1327825)

Probably just being impatient :biggrin:

---

### Post by PaulW2U on 2014-06-09
> **PaulW2U said:**
> I have tried both the Kubuntu and Xubuntu images for 4th June and I am seeing the following on booting my USB drive:

```
gfxboot.c32: not a COM32R image
boot:
```

I don't understand what this means so I'll be staying well clear of ISO testing for the time being. :)

I'm still seeing the same error message with today's Kubuntu image.

It seems all I needed to do was to press 'TAB' and then type 'live'.

Kubuntu's live images are configured slightly differently to the other flavours so I don't ever get to see the desktop. The boot process just hangs at the point just before where I would expect the installer to offer the 'Try' or 'Install' options.

---

