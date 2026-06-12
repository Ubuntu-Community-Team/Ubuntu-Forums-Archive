---
title: "Windows 10 'asleep', 'unsafe'..."
date: 2017-12-31
forum: Windows
---

### Post by Annigma on 2017-12-31
Hi Folks.

I'm struggling to fix my Win10 HDD which seems to have become corrupted. It coincides with trying to add a DVI monitor, but I don't think it's actually the monitor: I think messing about between VGA/DVI/HDMI/display settings/etc. has caused some driver issues and now Windows won't load properly (everything's working well here which supports that too) 
So, I had the bright idea to dig out my ubuntu discs and see what I could do. I'm typing this from a Trusty Tahr live CD :) 

**Windows current behaviour:**
When trying to load 'normally', internet, volume, USBs are disabled.
Task bar inaccessible, as is right-click
Can open command prompt
Ctrl R to open e.g. device manager results in some kind of error
Can get into Safe mode with networking
Windows update doesn't want to know
Loads up VERY slowly
If I leave it for a while, the screensaver comes on, which links to pictures on my other internal HDD
Basically, can just about get into it, but seem unable to do anything that may help..


The **current issue** is trying to perform some kind of repair on the windows HDD. I get the following when trying to open it:

> Unable to access “249 GB Volume”
Error mounting /dev/sda1 at /media/ubuntu/01CD6FCC63B23F90: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=999,gid=999,dmask=0077,fmask=0177" "/dev/sda1" "/media/ubuntu/01CD6FCC63B23F90"' exited with non-zero exit status 14: Windows is hibernated, refused to mount.
Failed to mount '/dev/sda1': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.

I have shut it down fully, and disabled 'Quick boot', I wanted to try and delete hiberfile.sys but have read that's a really bad idea...... I don't think I'd be deleting anything really important or that I couldn't fix though..

I don't want to mess about with ISOs if possible: I just did that for the PC I've built my OH for Christmas so he can finally play Arma (III). I don't yet have a working DVD Rom/burner in that machine, and mine won't recognise USB atm.

What I did wonder though was... I could take my HDD out, plug it into his via USB (have a converter with IDE/SATA/USB) and maybe see if windows update could sort it out or something...?

Or, if there's something I can do from this live CD...

Any help would be appreciated as I thought all this was over at Christmas, and now my PC's misbehaving.. maybe it's jealous..? lol

---

### Post by yancek on 2017-12-31
The message you posted regarding trying to access your windows system from Ubuntu means you have left it hibernated with fast boot on so you will need to get into windows to turn that off.  From the information you have posted, that is the least of your problems and I dont' think there is any point in trying to access your windows 10 from Ubuntu.  The source of the problem you describe is highly unlikely to be resolved from an outside OS (Ubuntu/Linux) so I would suggest you use your notes to describe whatever changes you made and post at a windows forum or thee support.microsoft site.

You could check back here periodically just in case some Ubuntu user is familiar with your windows problem, might get lucky.

---

### Post by Annigma on 2017-12-31
Ok thanks yancek. I will try again in windows and do the other things you suggest.
Thank you for replying
:)

---

