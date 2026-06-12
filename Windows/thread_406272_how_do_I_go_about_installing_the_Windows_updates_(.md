---
title: "how do I go about installing the Windows updates (XP)?"
date: 2007-04-10
forum: Windows
---

### Post by billdotson on 2007-04-10
First off this is a brand new Windows install and I have already installed all of my programs and gotten everything configured the way I want it.  So then I decided to go and download the automatic updates (w/ the exception of WGA!). I told it to automatically find and install updates, but no updates would show that they were available.

Then I went to windows update (the site) and hit express install.  It AUTOMATICALLY started downloading the updates AND THE WGA UPDATE!  I cancelled it as soon as I saw the WGA update.  So.. I had a backup of my install I made on another partition using dd (in Linux) and have started a restore of the partition before I started downloading and installing the updates.  

So after it gets restored in about an hour, how do I go about downloading the Windows updates without any of the WGA update getting downloaded or installed?  After I cancelled the download when WGA was downloading I went back and tried to click on custom but it just went back to the express install screen and didn't give me a choice to choose which ones I wanted to use or not.

Thanks.  Ubuntu and dd saved the day.. or else I would have nasty WGA on my Windows install!

---

### Post by jpeddicord on 2007-04-10
> **billdotson said:**
> First off this is a brand new Windows install and I have already installed all of my programs and gotten everything configured the way I want it.  So then I decided to go and download the automatic updates (w/ the exception of WGA!). I told it to automatically find and install updates, but no updates would show that they were available.

Then I went to windows update (the site) and hit express install.  It AUTOMATICALLY started downloading the updates AND THE WGA UPDATE!  I cancelled it as soon as I saw the WGA update.  So.. I had a backup of my install I made on another partition using dd (in Linux) and have started a restore of the partition before I started downloading and installing the updates.  

So after it gets restored in about an hour, how do I go about downloading the Windows updates without any of the WGA update getting downloaded or installed?  After I cancelled the download when WGA was downloading I went back and tried to click on custom but it just went back to the express install screen and didn't give me a choice to choose which ones I wanted to use or not.

Thanks.  Ubuntu and dd saved the day.. or else I would have nasty WGA on my Windows install!Just use the install all option. When it comes time for WGA to be installed, it will ask you if you want to. Make sure to hit I Do Not Accept.

I'm not 100% sure on this, but I believe that Microsoft is required to let you deny it since it phones home with your information.


(By the way, see the [Windows sub-forum]("http://ubuntuforums.org/forumdisplay.php?f=170") if you want more Windows-oriented support.)

---

### Post by BoyOfDestiny on 2007-04-10
> **jacobmp92 said:**
> Just use the install all option. When it comes time for WGA to be installed, it will ask you if you want to. Make sure to hit I Do Not Accept.

I'm not 100% sure on this, but I believe that Microsoft is required to let you deny it since it phones home with your information.


(By the way, see the [Windows sub-forum]("http://ubuntuforums.org/forumdisplay.php?f=170") if you want more Windows-oriented support.)

It still phones home that you denied WGA though.
See here: 
[http://www.heise-security.co.uk/news/86429](http://www.heise-security.co.uk/news/86429)

Maybe try [http://www.microsoft.com/downloads/](http://www.microsoft.com/downloads/) 
and avoid windows update?

Seriously though, when using Windows, you really can't be sure what is going on under the hood. You've got to trust MS (unfortunately.)

P.S. Yep, this thread should definitely be moved to Windows Discussions.

---

### Post by billdotson on 2007-04-10
I am about to install the automatic updates but when I go to the windows update site it asks me if I want to install "Windows Update" from Microsoft publisher.  Should I install that?  I don't recall it asking for that before (I just used dd to restore my Windows partition that I had backed up right before attempting to install the updates)

Thanks

---

### Post by rsambuca on 2007-04-12
You can go ahead with the Windows Update thing.  If I recall correctly, it needs some ActiveX stuff to work.  After you are running Windows Update, just click on the "Custom" update.  It will then just list every update that is available, and you can click and chose which ones you want to download and install.

As far as the Genuine Advantage thing, what's the big deal?

---

### Post by wylie98 on 2007-04-12
If you use firefox you can update win xp from [http://windowsupdate.62nds.com/](http://windowsupdate.62nds.com/). This allows you to choose which updates to install or not.

---

### Post by james016 on 2007-04-13
[www.autopatcher.com](www.autopatcher.com) and you can install all the updates and some other bits offline. You don't have to install the WGA. 

Very useful IMO.

---

