---
title: "Ubuntu Studio Karmic running great!  Some steps for newbies"
date: 2009-11-01
forum: Ubuntu Studio
---

### Post by texla on 2009-11-01
Just did a fresh install of Ubuntu Studio 9.10 from Studio 9.04 and it's really looking good.  I now have a realtime kernel that runs fast and smooth and there have ben no crashes as of yet with any programs from Firefox to Gimp to Ardour and Songbird.  Thanks for all that helped make this a smooth ride!:KS

 Just in case it can save other newbies like myself out there a little time in the install, this is just a list of a few steps I had make with my system setup.  I'm using a dual boot system with a separate home partition.

For the install from the DVD:
Format one partition as root /
Set other partition as /home - do not format 
do not touch the other partitions
(I don't have a partition available for SWAP so I created a swap file later instead)

Then, after my first boot, for the audio/video codecs to work, I added ubuntu-restricted formats:
sudo apt-get install ubuntu-restricted-extras

and reboot

then added back some of my favorite programs (evolution, tomboy notes, openoffice.org, kdenlive, k3b, songbird (have deb downloaded already)

Created my SWAP File (2GB) just like it says to do here without fail:
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

and reboot

Then started Ubuntu Studio Controls and activated the memlock at 50%, nice and 1394
(much easier than all the steps for Studio preparation I had to find out about and take for Jaunty)

Everything looks good so far and I'm really just amazed at how much better this already is than the Jaunty install I've been working with - not sure if this is because I did the fresh install over the upgrade or if the realtime kernel is just that much better or what but I'm cool with it.  Again, thanks for all those who put out the time and effort for Karmic Studio - and please let me know if I'm missing anything important in my steps above because I'm still pretty new at this.  :p

---

### Post by trulan on 2009-11-01
Very good!  One step I would add:

Users and Groups settings:
Go into System/administration/Users and Groups.  Click the keyring and enter your password to unlock.  Click on your username, then click the 'User Privileges' tab.  At the very least, check the 'Use audio devices' box.  If you will be using firewire, also check the 'Use video devices' box.

One more thing:  Could you do me a favor?

On both my machines Ubuntu Studio Controls fails to write the NICE settings.  Check /etc/security/limits.conf and see if the line is there.
```
@audio - nice -10
```If it isn't, I have filed a bug about this and I'll post a link to it.

If yours works maybe I'll try a fresh install (both my 9.10 installs survived the alpha ride and an inordinate amount of my own tinkering ;) )

---

### Post by crosspicker on 2009-11-01
I have my setup almost exactly like texla accept for the Swap partition, after I set up Ubuntu Studio Controls _@audio -nice -10_ did not write to /etc/security/limits.conf. 

Is this something that should be added manually? And if it is not there what will that effect?

---

### Post by trulan on 2009-11-01
nice is basically a priority setting.  Setting it to a negative number (-10 is very common) essentially makes your CPU treat that process as more important.  Likewise, setting a positive nice value gives the process a lower priority.

The idea is to keep other processes your system may be running from grabbing your processor power, thus causing x-runs in Jack (glitches/pops in your audio).

Until Ubuntu Studio Controls is fixed, you can manually set nice by running, in a terminal:
```
sudo su -c 'echo @audio - nice -10 >> /etc/security/limits.conf'
```or
```
gksudo gedit /etc/security/limits.conf
```and manually edit the information.

I was running my system for around a month on Karmic without the nice value set, with no issues.  It's just that once I know it's supposed to be there, it bugs me to no end if it isn't.

Edit:  Here's my bug for the nice issue in ubuntustudio-controls:
[https://bugs.launchpad.net/ubuntu/+source/ubuntustudio-controls/+bug/454082](https://bugs.launchpad.net/ubuntu/+source/ubuntustudio-controls/+bug/454082)

---

### Post by texla on 2009-11-02
> **trulan said:**
> Very good!  One step I would add:

Users and Groups settings:
Go into System/administration/Users and Groups. Click the keyring and enter your password to unlock. Click on your username, then click the 'User Privileges' tab. At the very least, check the 'Use audio devices' box. If you will be using firewire, also check the 'Use video devices' box. 

Trulan - I forgot, I did do that step, too - thanks for adding it here!  I think audio was checked off but I had to check the video. 

As for the nice setting in limits.conf, you're right again - it is missing from mine, too! Added it manually - thanks for the heads up on this!

---

### Post by AutoStatic on 2009-12-01
My findings after having used Ubuntu Studio Controls: [https://bugs.launchpad.net/ubuntu/+source/ubuntustudio-controls/+bug/454082/comments/5](https://bugs.launchpad.net/ubuntu/+source/ubuntustudio-controls/+bug/454082/comments/5)

---

### Post by trulan on 2009-12-01
Believe me, if I was a programmer, Ubuntu Studio Controls would be my next project!  Hopefully somebody makes it a priority for Lucid - I don't expect to see much action for Karmic.

As far as the NICE line not being added, I am beginning to seriously doubt whether Karmic pays any attention to it even if it is there, so Studio Controls may not be totally to blame.  Audio processes run at NICE=0, at least that's how they show up in System Monitor, no matter what is in limits.conf.

---

