---
title: "Should I keep reloading the Catalyst video driver?"
date: 2012-02-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Gregory Lee on 2012-02-15
So far as I know there is not yet a free video driver that works well for my video chip, the ATI Radeon HD 6550D, but AMD does have a software package for Linux that is said to work well.  So I think I need to download the AMD proprietary video driver.  I've done that by using System Settings > Hardware, which lists 2 proprietary AMD FGLRX drivers, one characterized as "post-release".  I ask to "Activate" one of them, the system downloads it and tells me I have to reboot to use it.  There's a green button beside the line for the driver in the screen which is not lit up, but after I reboot, as directed, the button lights up to say the driver is now activated, and the screen shows a message saying that it is present and in use.  Also, if I examine /var/log/Xlog.0.log, I see that the X server has loaded various fglrx modules, so it seems to be using the AMD driver I've asked it to.

However, there are things about this that I don't understand, and I'm hoping some of you can clear them up for me:


[LIST]
[*]After using the system for a while, if I go back to System Settings > Hardware, I see that the green button is no longer lit up, suggesting that the fglrx driver might no longer be in use.  (I've reloaded it twice, but I think I'd better stop doing this.)
[*]If I try loading the other "post-release" version of the fglrx driver, I get an error message from "Jockey" that something went wrong.
[*]I can't tell by looking at my screen whether I'm actually getting 3D graphics.  It looks pretty much the same as before I loaded the fglrx driver, and so far, I haven't been able to see any of the special effects that Compiz is supposed to be capable of when it can use a 3D driver.  When I use CompizConfig Settings Manager to load or unload plugins, my desktop goes a little crazy.
[/LIST]

---

### Post by alphacrucis2 on 2012-02-15
I'm not sure what is going on there but maybe you should use a more up to date version of Catalyst than the one in the Ubuntu repos. AMD release a new version of Catalyst every month, so they are sure to have a later version via the amd website. Occasionally they release a dud but check out the ATI forum section at Phoronix and read the follow ups about the latest Catalyst/fglrx to check that there are no major problems. The best way to install using the download from AMD is the --buildpkg method. That creates deb files for you to install which means that your package management system keeps track of which version of Catalyst you have installed. There is a binary driver howto that explains the procedure: (read carefully you can easily bork your system)

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by Gregory Lee on 2012-02-16
> **alphacrucis2 said:**
> I'm not sure what is going on there but maybe you should use a more up to date version of Catalyst than the one in the Ubuntu repos. AMD release a new version of Catalyst every month, so they are sure to have a later version via the amd website. ...
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
There is a more recent version of Catalyst than the one I have from the repos.  However, I don't think I'll try to install Catalyst directly, for now, since I have no confidence in my ability to fix my system if I bork it.  The useful reference you gave says to run fglrxinfo, which I did, and it seems to be saying that fglrx is running okay on my system.  I can also run the AMD Catalyst Control Center, and I see no problem there.

I'm guessing that the strangeness I've run across is due to problems with Ubuntu.

Thanks for your help.

---

### Post by cariboo on 2012-02-16
Why are you checking Additional drivers after you have run the system for a while, are you running into a problem of some kind?

---

### Post by Gregory Lee on 2012-02-16
> **cariboo907 said:**
> Why are you checking Additional drivers after you have run the system for a while, are you running into a problem of some kind?
No problem that I associate with the fglrx driver.  I clicked Additional drivers to see whether the driver I had asked for was being used and to see whether there were other additional drivers.  Why did I try to download the version with "post-release updates"?  Well, there might have been reasons for the updates that might have affected me, whether or not I knew the reasons.  And I'm just curious about why I can't get the updated version of the driver.  Do you know?

---

### Post by cariboo on 2012-02-16
I refuse to use ATI/AMD graphic cards because of their poor drivers.

---

### Post by QIII on 2012-02-16
... and I've had good luck with them.

Admittedly, there is some work involved in getting hardware acceleration in Linux.

It's interesting to note that AMD is a member of the Linux Foundation when someone else isn't.  Strange world we live in.

---

### Post by cariboo on 2012-02-16
AMD was a member of the Linux Foundation long before they purchased ATI. I was hoping things would change after the buyout, but it's still the same old same old. :)

---

