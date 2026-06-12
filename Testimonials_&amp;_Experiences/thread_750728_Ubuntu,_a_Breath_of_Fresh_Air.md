---
title: "Ubuntu, a Breath of Fresh Air"
date: 2008-04-09
forum: Testimonials &amp; Experiences
---

### Post by krinderlin on 2008-04-09
This is a bit of a long story, but it's a good one.

Linux was this cool toy that the elite computer geeks had laying around to show off to their friends.  I'm not sure if stuff like Compiz was around back in the days of Fedora Core 2, but I certainly wasn't aware of it.

I installed Fedora Core 2, my first Linux distro, back when everyone was talking about how crazy and awesome it was.  It recongized most of my hardware, but as typical of Linux at the time, my video card was granted a generic VESA driver.  After a bit of rummaging and what not, I found a binary NVIDIA driver and followed a tutorial or two and at least had a decent desktop resolution.

Then came the steady stream of updates.  Within two days I had recieved 3 new kernel builds, 5 new builds of related lib packages, and a few other updates to my libraries.  Then things started breaking.

I don't blame Fedora, it was simply the fact that I had installed a distribution that (at the time, not sure if it's still true) that was all about the latest and greatest of everything.  The goal, I concluded, was to have people complain about things breaking and fix them before moving them up into Red Hat.

So I wandered off into Gentoo.  Much gnashing of teeth, cursing of inanimate objects, and a few blood curdling screams that brought the neighbors over to see if they should call an ambulance, I finally had a terminal login prompt.  Three days later X finally started talking to me.  Four more days and I had a KDE desktop.  All through out this process, I'd get random kernel panics, X would magically disappear with cryptic errors not made for human repetition.  I finally found out from a Linux Guru friend of mine, that I was compiling everything with optimizations that my AMD processor didn't support, so the whole OS would need to be rebuilt again.

I scrapped the whole thing and tried one last distribution, Debian.  The install was nice, but the pre-packaged Desktop/Server/Programming package choices were insufficient for my tastes, because my computer use is dynamic enough that I can cover all three domains on one computer within a days tinkering.  Needless to say, after hours of selecting packages in the curses installer, I got an installation that took many more hours.

Finally, I got a desktop.  Yet again, I had no video card, but now I had no ethernet adapter, and even my processor was a mystery to Debian.  After much more gnashing of teeth, cursing of inanimate objects, and the near destruction of one computer tower, I got some cooperation.

After all of that, I somehow ended up with conflicting repositories (I was rather noob-ish at the time), and hosed my whole system.  I made the trek back to Windows XP and forgot about Linux as anything other than a nifty server.

I was realatively satisfied with Windows and Microsoft until Windows Vista.  I bought a new Gateway C140-X with an ATI Radeon Mobility HD 2300, Dual Core Intel Centrino T7300, 2 gigs of RAM, and a 160 GB hard drive, and most of all, a spiffy tablet screen.

I paid the extra money for Windows Vista Ultimate, because I was promised a computer capable of a bunch of multi-media tasks, and I wanted the business edition administration tools that gave me a little more control over my computer.

I began the semester at University and NOTHING worked.  Every time I installed anything, even things from Microsoft, there were 20 different tweaks/updates/etc. I had to go through to get it working.  Windows pushed down a few updates that fragged my computer, and after two new installations I was fed up.

I was talking to a friend about my issues and commented that I was just going to get a MacBook next year.  He convinced me to try Ubuntu.  I figured it was free, came on a live CD, and it couldn't hurt.

Clicking around the live CD, I found that my ATI graphics card would run if I downloaded a restricted driver.  I found some commented lines in my xorg.conf that would activate my tablet.  I even found that the Add/Remove had most of the software I needed, and Synaptic found even more. The thing that stunned me the most, was that my wireless worked out of the box.

The last thing that made me jump for joy was that not only could I read/write to NTFS, but gparted could resize my NTFS partition.

I'm about a month in, and I have mac-ish windows with the solid slate grey I like.  However, I have a task bar, which I like much better than Mac's weird dock.  I also have my minimize/maximize/close buttons in a different order from Mac.  I have wobbly windows of doom (though it's all going through the Mesa library, so I get a bit of issues if my effects are set to a high duration).

I have GnuCash for my checkbook.  OpenOffice takes care of my project logs and etc.  BlueJ (my professor makes us use it), which is a Java program runs just fine.  Java runs nice.  FireFox does everything it did on windows.  I'm running everything just fine.

In fact, the only reason I boot into Vista anymore is when I need to grab a PDF of some of my old OneNote Calculus notes to work on some homework in Xournal.

I finally remembered why I liked Linux back then, and why I was sad that I came back to Windows.  Linux makes my computer...well...MY computer.  I want mac windows?  Sure.  I want cool desktop effects?  Sure.  Even better, if those weird desktop effects cause Xournal to act weird in full screen mode, a few clicks and special effects are gone.  Need to group windows on multiple desktops so you can flip between you're IDE, Documentation, and google searches without minimizing or alt-tabbing?  No problem.  Want to run a special script that changes your desktop background on every quarter hour?  All up to you.

There are only two things I had in Vista that I don't have in Ubuntu. The direct rendering is still not working on my card. Now that I've hosed X twice attempting to get it up and running, I'll let Ubuntu work out itself.  Also, I can't rotate my screen, which is a bit annoying since I have a 12-cell battery and the screen tilts away from me in tablet mode.

I like having my laptop back.  I also like the fact that at the very least, Ubuntu knows my hardware, even if I can't get all of the features out of it right now.

So thank you.  Thank you for making Linux usable on laptops.  You have no idea how nice it's been to finally have complete control over my laptop.

Now, if I can just learn not to let my inner power user get the best of me and stop mucking about in my xorg.conf...

P.S.

Of course the nice thing is that the first time I hosed X, I had to reinstall, but I was able to use the Live CD to back up my home directory over to a USB stick.  After the reinstall, I migrated my home directory back over, ran apt-get upgrade, and everything was just as it was, minus a few applications.

The second time, I just copied my xorg.conf_backup back over the new xorg.conf, rebooted out of recovery mode and voila!  All was well.

I've never been able to do that when I hosed crap up in windows.  It was hell just to get into the hard drive to back up data.

---

### Post by armandh on 2008-04-10
todays linux and ubuntu in particular is ready for desktop/laptop noobs such as my self. 
but I am a convert from xp post 7.04   Early linux was not ready for prime time use.
today Ubuntu leads or is in a close race with PClinuxOS
and I like ubuntu better.

---

