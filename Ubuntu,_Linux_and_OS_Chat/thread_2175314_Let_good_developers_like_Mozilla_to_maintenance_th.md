---
title: "Let good developers like Mozilla to maintenance their packages"
date: 2013-09-18
forum: Ubuntu, Linux and OS Chat
---

### Post by hyz2 on 2013-09-18
[CENTER][SIZE=5]**Let good developers like Mozilla to maintenance their packages**[/SIZE]
[/CENTER]
 
If we have a look at the maintainers of the packages in the Pool, we will find none of the maintainers are the software developers themselves.

May be the purpose of this strategy is to ensure software quality, because all of the software are tested, modified(if needed), and rebuild by the Ubuntu Community. 

But, as for good developers like Mozilla, they have the ability to ensure the quality. I think it's not a good idea to assume that their softwares have bugs and need to be fixed by the Ubuntu Community. We are cooperated to bring the world a good OS, so we work on different fields and trust each other.

What is more important is that, they know a lot more about their code than us. If a large project like Firefox contain bugs in their code and can't work well in Ubuntu, we have to waste a lot of time to learn the code tree, learn the algorithm in the program and finally find where the bug is, and fix it. But the Mozilla developers are familiar with the code and is possible to fix it within five minutes!This will happen if only Mozilla maintenance Firefox packages themselves, because they will develop on Ubuntu, build on Ubuntu, test on Ubuntu. Bugs will become less and less,  and less time will be wasted on things just like reinventing the wheel!

The new strategy has many additional good points:
              Let the software provide maintenance packages themselves can encourage them to pay more attention to Ubuntu, make the software more fit with Ubuntu. 
              Always have 0-day support for new release.  That's for obvious!
              Software developers will officially support Ubuntu, and may recommand users to choice Ubuntu.

I think a lot of good developers have the ability to maintenance packages themselves.   Mozilla, LibreOffice, Gnome, Apache, php, MySQL, phpMyAdmin, Gimp, Inkscape, Scribus, Filezilla, Boinc, WordPress, etc. They contribute a lot and make excellent software, and we should trust them.

It is in urgent need to accept  the new strategy because many software like LibreOffice are not update in time. This shows we do not have enough staff to  maintenance the packages. So it is time to change!

====================
Original arcitlce Link: [http://blog.pillowsky.org ]("http://blog.pillowsky.org/why-not-let-good-developers-like-mozilla-to-maintenance-their-packages/")
I am a student in zhejiang University, China. 
May be my English is not so well:(

---

### Post by deadflowr on 2013-09-18
I thought they tried that before and found it was a lot worse.

---

### Post by monkeybrain20122 on 2013-09-18
Mozilla maintains a generic Linux build for Firefox which doesn't require installation (untar, open folder and click firefox-bin), the only thing you need to do is to manually create a .desktop file. I use it in Debian instead of iceweasel I suppose it would need some rebuilding and maintenance on canonical's part so that it would install in the system for all users and integrate with the system as the default browser.

---

### Post by cariboo on 2013-09-19
Most authors of applications do maintain them, the Debian/Ubuntu package maintainers just make sure the packages install properly on the respective distributions. There are a few programs that are no longer maintained, but still packaged, due to their popularity. My personal feeling is that these unmaintained programs should be removed from the repositories no matter how popular they are.

---

### Post by grahammechanical on 2013-09-19
A lot of us would be very happy if software programmers fixed the bugs in their software. As I understand it bugs are pushed upstream to these, Oh so, talented developers. Then what happens?

I do not have any problem with bugs being fixed in the next version of the software. I am always using the latest version of Ubuntu with the latest versions of applications like Firefox and Libreoffice. But many on an LTS release wait and wait for bugs to be fixed.

May I ask, have you sent this idea to the Mozilla developers? What did they say? Please see the Forwarding Upstream section in this wiki page

[https://wiki.ubuntu.com/Bugs/HowToTriage](https://wiki.ubuntu.com/Bugs/HowToTriage)

A lot of work is done on our behalf at the Ubuntu end of the Bug-Fixing process.

Regards.

---

### Post by monkeybrain20122 on 2013-09-19
> **grahammechanical said:**
> 

A lot of us would be very happy if software programmers fixed the bugs  in their software. As I understand it bugs are pushed upstream to these,  Oh so, talented developers. Then what happens?

I do not have any problem with bugs being fixed in the next version of the software. I am always using the latest version of Ubuntu with the latest versions of applications like Firefox and Libreoffice. But many on an LTS release wait and wait for bugs to be fixed.

...

 How is it upstream's fault that software in Ubuntu's repo (and Debian's) is many versions behind so that bugs fixed in new versions don't get filtered down? I can't believe that even default applications are not being upgraded in Ubuntu's point releases: Libreoffice is still at 3.6.5  (which has reached eol upstream) in Ubuntu 12.04.3. Gimp 2.8 has been released for a long time, but if you are on LTS you are still stuck at 2.6.  Since once released all software versions are frozen so you aren't going to get any bug fix for most software unless you get the latest versions from ppa. 

However, I do expect bug fixes for things like Unity to be backported to LTS, for which the upstream is Canonical, but that is not happening either, looks like Ubuntu 12.04 is going to be stuck with Unity 5  and whatever buggy Compiz version (fixed in 13.10) forever.

P.S. Some bugs are specific to Ubuntu and have nothing to do with upstream, e.g LibreOffice's integration with the global menu which has been an issue on and off for several Ubuntu releases. I expect more Ubuntu specific bugs when XMir/Mir becomes default.

---

### Post by cariboo on 2013-09-19
The problem of out-of-date packages rests with Debian, as the devs take a snapshot of the Debian repositories, just before starting development of a new version.

---

### Post by mikewhatever on 2013-09-19
The question is, do people at Mozilla or LibreOffice, and so on, have the will and man power to maintain their software for even the top 10 Linux distros. It's not that simple, and may be quite a work load, since differrent distros do things slightly differently. Also, I am not aware of anyone preventing Mozilla from taking on that work, in fact, Canonical will probably be happy to let them maintain Firefox and Thunderbird for Ubuntu.

---

### Post by grahammechanical on 2013-09-20
A user of the last LTS can get Unity 7 if they want it by upgrading to 14.04 LTS in a little over six months. A decision has been taken not to radically change an LTS version during the life time of that LTS version because people choose the LTS for the very reason that it is not going to change every six months. 

Those who want to keep up to date with Ubuntu developments can install the latest version every six months. Those who like to be at the very edge of Ubuntu development can run the development version. But even then they will not automatically get unstable versions of Upstream code but we can install it if we want the excitement of running such stuff. 

But the discussion is not about that.

The OP was saying the Mozilla developers should maintain Mozilla code as if it was the fault of Ubuntu developers that they were not maintaining it. And he was meaning bug fixing. The responsibility to fix bugs in upstream code rests with the developers of upstream code. The responsibility to maintain upstream code in a package format compatible with the distribution rests with the developers of that distribution. And that is the situation today. Call it division of labour.

For example, consider the much contentious decision to move the Max, Min and Closed buttons from right to left and to move the File, Edit, etc., panel from out of the application window and into the user interface top panel. Who has responsibility to maintain that decision? Mozilla or Ubuntu? In fact the conversion of the Firefox menu panel happened long after it did in Chromium. What stops these applications from reverting back with every new version of the application? Ubuntu maintainers.

Regards.

---

### Post by cariboo on 2013-09-21
It seems the op created a bit of a fire-storm on the ubuntu-devel-discuss mailing list. :-)

---

### Post by vasa1 on 2013-09-21
Here's an oldish comment by a contributor to the Mozilla project:
[http://blog.cornelius-schumacher.de/2011/10/demise-of-windows-platform.html?showComment=1318513290340#c41461139713206099](http://blog.cornelius-schumacher.de/2011/10/demise-of-windows-platform.html?showComment=1318513290340#c41461139713206099)

I agree that expecting Mozilla to maintain packages for individual distros is a bit of an ask. Even if they were to pick one, why would it be Ubuntu when there's recurring talk of having another browser as default, for whatever that's worth? Yes, we all know about sudo apt-get install.

---

