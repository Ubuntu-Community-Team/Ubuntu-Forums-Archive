---
title: "First time experiences and concerns with Ubuntu 13.10"
date: 2014-02-06
forum: Ubuntu, Linux and OS Chat
---

### Post by Evert_Wiesenekker_ on 2014-02-06
This posting is related to Ubuntu Ubuntu 13.10 64 Bit running on a core i7-3770S, Ivybridge Desktop graphics, 16 Gb of Ram, 256 Gb Kingston SSD.

After having switched from OS X to CentoOS (which I found too minimalistic) and now Ubuntu I want to share some first time experiences/concerns:

This is an amazing effort for a free product! I especially like the Unity desktop from a usability perspective and even the design struck me! I now have ZFS running (of course not Ubuntu related but this is an amazing filsystem), DropBox, Spotify, VirtualBox (which I last week replaced with a trial of VMWare due to memory problems. This is not related to Ubuntu because it also happened on CentOS). I am a Windows/Apple guy i have to admit, but thanks to Linux I a finally discovered the power of a terminal session, like rsync and grep (with Windows/Apple you normally do not get pushed in the direction to use a terminal).
I am so enthousiastic that I yesterday even replaced a (slow) running Windows 7 installation on a Intel Core i3 laptop (80 Gb SSD, 4 Gb Ram) of a friend (an absolute beginner regarding PC's) of mine. It outperforms Windows 7! Lets wait if this installation survives 2014.

What I like most is I finally got rid of the COMMAND on Apple versus CTRL on Windows confusion. I work a lot on Windows inside a Virtual Machine. The keyboard differences always drove me crazy. And believe it or not one of the main reasons for abandoning Apple (besides the costs).

The LibreOffice I found less bloated (I like minimalistic designs) than Office 2013 but it is a problem it can not open my docx files out of the box (it even crashes with 4.1.2.3 and shows and empty doc when opening with 4.2). I know of course this can be converted to doc but for a beginner this could be problematic.

But I like to express some concerns which I really hope will be fixed in the future:
I get the idea Ubuntu is not stable. During out of box installation I got, especially on the i3, errors which I chose to ignore (or restart and the errors magically dissappeared). This gives me an uncomfortable feeling. And now after working daily for about a month with Ubuntu I sometimes get errors reports, a tmp file system which today got unavailable (although df -h showed usages around 1% to 60% for the different mount points). My machine refuses to restart sometimes or go into suspend mode. 
Last week my system even froze and needed to restart it by pulling the plug.

Although it seems to work if I ignore the errors and live with the crashes (about 1 time per week) I do not get the feeling I am working on a stable environment.

The Ubuntu Software Center App store is great but I hope, just like Apple does, there will be some certification of apps regarding stability (version related) because I noticed some apps won't install or crash. For me this is no problem but for a beginner it will.

Evert

PS
I did an overnight memtest, ran 'sudo badblocks -sv  /dev/sda' and 'sudo zpool scrub ...' in order to check if it is hardware  related my crashes.

---

### Post by Elfy on 2014-02-06
*Thread moved to **Ubuntu, Linux and OS Chat**.*

If you need specific help for issues, please start threads for those - using one thread per issue.

Welcome to Ubuntu and the Forum :)

---

### Post by robin7 on 2014-02-06
I would say that the latest releases are "unstable" (meaning that they're always updating and fixing things, plugging holes and squashing bugs, lots of changes going on, frequent updates), and the older Long Term Support (LTS) releases are "more stable" (meaning that the majority of bugs have been squashed, holes plugged, not a lot of ongoing changes).  Ubuntu 12.04 LTS is almost 2 years old now and still has another three years of support!  It will actually overlap the next LTS release.  I think that those who want the "most stable" experience of Ubuntu should use the LTS releases all the way to the end of their support life, then upgrade only to the next LTS release - which by then will have had most or all of the bugs squashed, and will still have years of support remaining.  For new users especially I think it's important.  The latest-and-greatest Ubuntu releases are effectively *testing* releases for the more adventurous, tech-savvy folks who use them on spare computers for playing around with.  Users like me who have only one computer that is "mission critical" and needed to function reliably should not use the latest-and-greatest Ubuntu.

But thank God for those who *do* use the latest-and-greatest releases, because they spot and report the bugs and glitches so they can be fixed, for the rest of us common ordinary mortals with only one computer, who can't afford to test new stuff.

---

### Post by Evert_Wiesenekker_ on 2014-02-06
I feel like a blind mole... I rechecked the download page and eagerly clicked on the 13.10 download without reading the the LTS section (which for my situation should have been the right download). I guess I have worked too long with Win/Mac and forgot to what it is to read text ;-) Well I will keep on testing 13:10.

---

### Post by tdawgf on 2014-02-08
I really have to second robin7. My first Linux distro was back in the Mandrake 9 days, so by that standard every release in Ubuntu feels tremendously stable to me. That being said, I have noticed that the LTS releases tend to be more stable. I used to stick to them, but recently moved to Lubuntu 13.10. I really like it but I think that I will be heading back to Kubuntu or Xubuntu when 14.04 releases.

---

### Post by Evert_Wiesenekker_ on 2014-02-12
Well I have 'downgraded' to 12.04 and this seems to run stable. The first day I got problems with some lost keys (CTRL) not working sometimes, but after updating the Intel HD 4000 drivers I do not have any problems anymore! A major plus was it is extremely easy to reinstall linux, I only needed to be very carefull not to delete my existing partitions.

---

### Post by mastablasta on 2014-02-12
still your experience points to some hardware issue. i never had any errors on install. granted i only installed 2 computers with new hardware and 3 older maschines. yet no errors during install on either of them.

errors are there to tell you something is not setup right or working correctly. linux logs them. if you want to troubleshoot them open new threads in appropriate forums. it might help other users with similar setup.

14.04 LTS is coming out in April. wait for a month or so and then you can upgrade to it from 12.04 LTS.

---

