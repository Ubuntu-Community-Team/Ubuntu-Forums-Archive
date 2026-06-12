---
title: "What Happened to All the Goodies for Studio?"
date: 2016-08-03
forum: Ubuntu Studio
---

### Post by Rick St. George on 2016-08-03
After upgrade from v14.04 to v16.04 I don't have many programs I am used to, like Office, PulseAudio, KdenLive.

Upon attempt to Re-Install KdenLive, it says the following have to be remvoed;
   libmovit2; libopencv; libopencv-highgui; libopencv-imgproc2.4; libopencv-objdetect2.4; libopenimageio1.3

Why would I want to do that when obviously it must be related to this new version 16.04 LTS? Is there another alternative? Comparable to KdenLive?

There is no other program showing in the Menu under Video Production except DVDstyler (it doesn't do the job).
Another example- under Photography there are a couple organizers, but only GIMP which is extremely complicated. What happened to Ristretto Image Viewer? Oh ... Software Center shows it is installed, but I can't find it anywhere! Not even in Accessories / Main Menu.

Are the software developers behind the 8-ball in getting them ready for Ubuntu v16.04 LTS? Or What ? ? ?
Not Bitching ... just Curious as to how I should proceed from here.
Thanks!
Rick

---

### Post by vteve on 2016-08-03
I just downloaded and installed 16.04 AMD64 yesterday and all the programs you mention are installed by default. Not sure what could be happening with yours. Maybe do a checksum on your downloaded image.

---

### Post by yoshii on 2016-08-03
if you happened to accidentally do an apt-get autoremove, often it gets confused and offers to remove tons of needed items.  So I never use that command.

---

### Post by Rick St. George on 2016-08-03
Thats what I did - "autoremove". But after adding some PPA's, doing an "update" and "dist-upgrade" it seemed to have all come back.
For anyone else that doesn't know what I'm talking about ...

                        **DISTRIBUTION UPGRADE and to SOLVE UPDATE/UPGRADE ISSUES**
   (Run ALL for Upgrade)
 
```

sudo apt-get autoclean
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```
 You must run the above commands (at least update, upgrade, dist-upgrade) prior to upgrading your OS to a newer release. Also, switch off any third-party PPAs you have installed manually. You want the machine as 'vanilla' as possible. Be aware that if you have installed third-party drivers from anywhere other than the repos they may break after the upgrade. This generally applies to wireless and graphics.

 
Peace!
Rick

---

### Post by Bucky Ball on 2016-08-03
Just a note. Do a full update/upgrade and disable any manually added PPAs prior to doing a release upgrade. This will avoid a lot of the issues you have come across. At an educated guess, it appears you left 14.04 PPAs enabled during the upgrade and now you've added the correct ones (and disabled the old ones?) things have come good.

---

### Post by david-daking on 2016-08-05
I am also wondering the same thing. I was on Ubuntu Studio 14.04 but it stopped working properly. Had to do a clean install of 16.04.1 in a newly formatted partition. I had all the boxes ticked for the extras, but nothing seems to be there. In 14.04 there were lots of good programs in the main menu, now I have very few items, nothing specific to Ubuntu Studio. If I search for an item like gimp or scribus, there are no menu entries. But if I go into Synaptic, it lists them as being installed.
So how do I access all these programs? Why are they not in the menus?

---

### Post by david-daking on 2016-08-05
I installed Cairo Dock, this I see has the extras on its Applications menu, but not in the main menu for Ubuntu Studio?

---

### Post by mook765 on 2016-08-09
There might be a left-over from the former distribution.
Check if there is a file named "xfce-applications.menu"  in /home/my name/.config/menus.
Rename this file (e.g. "xfce-applications.menu.old") or move it to the trash.
If this doesn't help, the file is not deleted yet, you can rename it back or restore it from the trash.
I am not sure if this helps, but it's a simple thing to do and worth a try.

---

