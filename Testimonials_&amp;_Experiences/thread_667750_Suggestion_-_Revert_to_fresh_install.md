---
title: "Suggestion - Revert to fresh install"
date: 2008-01-14
forum: Testimonials &amp; Experiences
---

### Post by alapidas on 2008-01-14
I have a suggestion for Ubuntu, but I'm not quite sure where to put it, here seems most appropriate.

A feature that allow users to completely revert back to the status of a fresh install, erasing users and data (NOT using a cd).  Maybe allow the option of keeping users or data.  

Does anyone know of a more appropriate place to post this?

Thanks

---

### Post by some_random_noob on 2008-01-14
You mean like System Restore in Windows XP? If so, then I'd say screw it. A "System Restore" isn't enough in my opinion. Maybe it would be better to have the installer create an invisible recovery partition?

p.s. I have no idea where to post this either :confused: ... but I'm pretty sure there's a suggestions forum some place. Chances are this will be moved anyway.

---

### Post by alapidas on 2008-01-15
I mean a button I can click that will make the install look as if it were brand new JUST installed.  This could be part of a system restore also, I suppose.

---

### Post by nfox on 2008-01-27
That would be a good idea. An easy app like Automatix would be spiffy.

Here's the options that I know:

1.)   You can repair (with the CD unless the kids today have another method) and do not repartition your /home partition (if you had the forethought to separate / and /home). The other option (and closer to your goal) would be as follows:

2.)   Follow this guide with some exceptions/personal suggestions noted below.
[http://ubuntuforums.org/showthread.php?t=35087]("http://ubuntuforums.org/showthread.php?t=35087")

Install Ubuntu into a virtual machine as you want it. If VMWare is out of the question, just reinstall it normally and follow this guide for the next time.
Put the apps you want, wallpaper, etc. but nothing that's profile-related since it will most likely be erased.
Save the extracted directories on a DVD for the quickness next time.



**Summary:**
With a fresh install, customize your setup how you would like it including drivers, etc.
Copy the root partition on the install to an archive (**carefully:** you have to do it just like the guide I linked to shows or chaos will ensue)
Boot into your current installation (why the virtual machine way is king)
Paste the contents of the archive over the original files in your root partition (please, please read the notes below about that)
That's it.

** I don't make a warranty/guarantee. The details will/have worked on my setup and the guide's author but that's all that it means. Do not copy files without preserving permissions and other measures outlined in the guide. If you are creating a virtual machine testbed to make the archive, make sure you replace the xorg.conf file among others. The virtual install will be set up to use virtual hardware and must be configured when restored accordingly. That's beyond the scope of this post though.



Let me know if you have troubles, I was planning on making an image like this for distribution. Anybody with app-skills feel free to hit me up so we can make this for (hopefully) the next release. I want it fully compatible-- KDE, Gnome, etc.

---

