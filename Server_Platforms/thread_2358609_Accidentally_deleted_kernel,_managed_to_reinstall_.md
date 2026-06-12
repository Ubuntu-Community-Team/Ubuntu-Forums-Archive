---
title: "Accidentally deleted kernel, managed to reinstall without extras ... what now?"
date: 2017-04-15
forum: Server Platforms
---

### Post by indystef on 2017-04-15
I maintained my Ubuntu server 16.04 installation today, and as ever so often, the /boot partition was full of kernels (why?). About 4 times a year I simply purge/remove those kernel images, and then complete the apt upgrade. This time, for whatever reason, I managed to remove the running kernel (4.4.70). I noticed my mistake, and re-installed it, but only the linux-image-4.4.70-generic. After a reboot, the system was no longer able to use any networking (the interfaces are all UNCLAIMED, because the drivers can't be located). I suspect the drivers would be in the linux-image-extra-4.4.70-generic package.
How can I install the missing package? I don't have network access on that server, so any solution would have to involve copying files via USB stick.

Thanks,

Stefan

PS: If somebody could also tell me how to make Ubuntu purge all but the last two kernels after an automatic update, I'd be thankful, too.

---

### Post by howefield on 2017-04-15
Moved to the "*Server Platforms*" for a better fit.

---

### Post by darkod on 2017-04-15
By saying /boot partition I assume it literary is separate partition. What's its size? If you used the guided LVM option during installation, unfortunately that creates rather small /boot of some 250MB only. If you want LVM during installation use manual partitioning and create a /boot of 1-2GB.

Then, by using 'sudo apt-get autoremove' it will clean up all older kernels it doesn't need. That would be the best way to do it...

And since you noticed your mistake by removing the latest kernel, you should not have rebooted until sure you have reinstalled all related packages.

Coming to the most important part, how to reinstall the kernel, am I correct in understanding there is no internet connection on this machine? And there is no easy way to connect it to the internet? Because that would be the easiest and most recommended way to reinstall the kernel and all needed packages.

Otherwise go to [http://packages.ubuntu.com](http://packages.ubuntu.com) and start chasing up all packages needed for the kernel, then their dependant packages, etc... But that's really not something I recommend, installing manually like that... Too easy to make a mistake and miss a package (or more).

---

### Post by indystef on 2017-04-15
Thanks for your help, Darko. I was able to boot into the Ubuntu server 16.04 installer, and used the rescue option to install the missing package (linux-image-extra-4.4.0-70-generic). After a reboot all was OK again.

Yep, I use rather small boot partition - I think that was the one the installer set up by itself. I had used autoremove in the past ... until it killed an OwnCloud installation I had on that server. Since then I used the manual method, using apt remove. I switched to NextCloud a few months ago. Hoping this fixed the autoremove issues, I tried it after I got the server working again - to my relieve there was no problem with any service I run on this box.

Thanks again,

Stefan

---

### Post by darkod on 2017-04-15
Great. Please mark the thread as solved, you can do that in Thread Tools above the first post.

---

