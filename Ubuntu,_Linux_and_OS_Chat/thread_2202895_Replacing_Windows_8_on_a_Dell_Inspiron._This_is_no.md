---
title: "Replacing Windows 8 on a Dell Inspiron. This is not a problem."
date: 2014-01-31
forum: Ubuntu, Linux and OS Chat
---

### Post by wamses2 on 2014-01-31
I'm writing this in case others in the same boat are wondering about doing this.  I bought my wife a  Dell Inspiron 15 recently with Windows 8, unsurprisingly she hated it.  So I thought I would try replacing Windows 8 with Ubuntu (12.04.3)

I'm not that au fait, but had a Ubuntu based machine some time back.
Couple of small problems (mine), namely I hadn't realised that the downloaded iso file needed to go through another process and initially tried just copying it to a CD, doh, disc not quite big enough (actually a bit of luck else I'd have wasted more time through not reading how to do things properly).  Then I saw it (the iso file) needed processing so downloaded unetbootin, then pointed it at the iso.  This gave me a usb data stick with the bootable files on, I faffed around with the Dell boot options, and got to the Ubuntu menu.  Strangely for me, I took the option to check the disc for defects.  One missing file reported, but I thought I would try anyway and see how the install looked.  It failed quite swiftly with a ubi-partman exit code 10 error.
I thought about this overnight, as the solutions I had seen mentioned other options being available from the ubuntu install menu, that were not visible on my system, possibly indicative of a disc format problem.  I seemed to have two things to check out, they were the missing file error, and whether I should try and format the disc pre-install (I didn't want anything from Windows 8 that wasn't already backed up).
I tried running unetbootin again, this time letting it obtain the files rather than me downloading one.  Once it had completed, I tried the boot again from the usb, again checking for disc errors first, there were none.  Then I took the Install Ubuntu option, this time shortly into the build, I was offered an Installation Type configuration choice, and the installation completed successfully.
On rebooting the newly built system I came across two problems.  One was that usb data sticks were not being recognised, and the other was that I couldn't get wireless connection with my router, or my extension router.  I looked through the forum entries, but nothing seemed to fit the bill too closely, so I then installed the outstanding system upgrades (250).  As they were being downloaded and applied, I noticed that my wireless connection was automatically picked up.  Once the updates had finished I also tried the usb data stick approach again, and that too worked.
So, if you are thinking about ditching Windows 8, go ahead, I stumbled around a bit, but anyone with a lick more sense than I have would probably have knocked the whole job off in a couple of hours.  Thanks to all concerned with developing Ubuntu and sharing their experiences and help on this forum.  It does give us newbies the confidence to try and do things like this, knowing there is a good chance (eventually) of succeeding.

---

### Post by bc.haynes on 2014-01-31
Welcome to the Ubuntu Forums, if you have never been here.

Your post was informative though not applicable to me.

Thank you for spending the time to post it. I hope your wife enjoys Ubuntu.

---

### Post by howefield on 2014-01-31
Not really a support thread, moved to the "*Ubuntu, Linux and OS Chat*" forum.

---

### Post by Don_Stahl on 2014-01-31
Good job! 

Just a note to anyone installing Linux for someone unable or unwilling to learn an interface that varies much from Win XP -- try Zorin. It's Ubuntu with a Windows-like interface. Except better.

---

