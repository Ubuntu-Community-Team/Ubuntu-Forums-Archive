---
title: "[Report] Ubuntu 11.10 on HP Pavilion dv7"
date: 2011-10-16
forum: Testimonials &amp; Experiences
---

### Post by Deltik on 2011-10-16
[CENTER][COLOR=Orange][SIZE=6]Ubuntu 11.10 Oneiric Ocelot[/SIZE]
[COLOR=Black][SIZE=1]on an[/SIZE]
[SIZE=5][COLOR=RoyalBlue]HP Pavilion dv7t[/COLOR][/SIZE]
[/COLOR][/COLOR][SIZE=3]Compatibility Report[/SIZE]
[SIZE=2]by [Deltik]("http://www.deltik.org/")[/SIZE]

_**[SIZE=2][COLOR=Red]UPDATE (02 MAY 2012): Report on Ubuntu 12.04 LTS Precise Pangolin [here]("http://ubuntuforums.org/showthread.php?p=11900678")[/COLOR][/SIZE]**_
[/CENTER]

_**In Short**_
This independent report outlines many new issues Ubuntu 11.10 introduces that Ubuntu 10.10 and even Ubuntu 11.04 did not have.  My poor HP Pavilion dv7 laptop computer is suffering.  My 2006 Toshiba Satellite laptop computer performs better. :(


_**Recommendations (issued 15 October 2011)**_
If you are satisfied with Ubuntu 11.10, stay on Ubuntu 11.10, but you are probably *not* satisfied, so I recommend that you downgrade to Ubuntu 10.04 Lucid Lynx.  On [26 April 2012]("https://wiki.ubuntu.com/PreciseReleaseSchedule"), Ubuntu 12.04 Precise Pangolin will be released.  This is the next long-term support release after Ubuntu 10.04 Lucid Lynx, and upgrading to it directly is supported.  Historically, Ubuntu LTS releases have been very good.  Let's hope that Ubuntu 12.04 LTS will also be very good.

Okay, so Ubuntu 11.10 has been a disappointment.  What if Ubuntu disappoints us again when Ubuntu 12.04 comes out?  I now fear that it may happen because of the worsening condition of new releases of Ubuntu.  Unfortunately, if the next LTS is ruined (which I really, really hope doesn't happen), Ubuntu might not recover (in the foreseeable future).

In that case, I have no choice but to recommend you a different distribution of Linux.  Try [Linux Mint]("http://linuxmint.com").  You might like it because it's similar to Ubuntu.  I liked it when I tried it in 2009 (but not with an HP Pavilion laptop).  If Linux Mint doesn't appeal to you, consider [Fedora]("http://fedoraproject.org/"), which is targeted at more advanced users.  Fedora uses RPM packages rather than DEB packages, so if you're dependent on Debian packages, you shouldn't switch to Fedora.

Last fallback: What if you don't like Ubuntu or any other distributions of Linux?  As much as I hate to say it, you have to switch to [Microsoft Windows]("http://www.microsoft.com/windows/buy/default.aspx") ($219.99 retail price).  Since you don't like Unity (I think), [Apple Mac]("http://www.apple.com/mac/") OS X (corresponding hardware starts at $999) won't work for you because Unity highly resembles the Mac OS X interface.


_**OMGWTFHTMBBQ?!**_
I started typing this post on 15 October 2011, but on the morning of 16 October 2011, I found another issue in Ubuntu 11.10 that tips the balance.  If you're like me, you would trash Ubuntu 11.10 Oneiric Ocelot for Ubuntu 10.04 Lucid Lynx.

So... I have a *complete* list of "pros" and an *incomplete* list of "cons" of Ubuntu 11.10.


_**Pros (complete)**_

[LIST]
[*][Core temperature problem]("https://bugs.launchpad.net/ubuntu/oneiric/+source/linux/+bug/760131") resolved for the most part
[*]Battery indicator works now
[/LIST]

_**Cons (incomplete)**_

[LIST]
[*]Battery indicator doesn't work properly
[LIST]
[*]For me, oftentimes, if I unplug my laptop, Ubuntu would "feel" a decrease in power feeding and go into standby mode because it fears that my computer will run out of battery power.
[*]At first, Ubuntu estimated about 33 minutes of battery power remaining at 100% charge.  After recharging it, Ubuntu indicated 9 minutes.  What's happening?
[/LIST]
 
[*]New graphics problems
[LIST]
[*]Desktop environment frame rate not improved noticeably after installation of ATI/AMD proprietary FGLRX graphics driver and reboot
[LIST]
[*]... if the ATI/AMD proprietary FGLRX graphics driver would install properly the first time... :-x
[/LIST]
 
[*]Failed to transfer my GNOME 2 settings.  Now, the Ambiance theme is ruined with the "close" button on the right side instead of the left side.
[/LIST]
 
[*]Right-mouse click on touchpad still not supported by default (This might not apply to the later 2011 HP Pavilion dv7 laptops; I haven't tested the touchpad on them.)
[*]Increased startup time
[LIST]
[*]I don't remember logging in taking so long in Ubuntu 10.10...
[/LIST]
 
[*]Decreased performance
[LIST]
[*]Programs take longer to start up.
[*]Everything feels sluggish.  Everything.
[/LIST]
 
[*]Ubuntu One memory leak
[LIST]
[*]Sync daemon using up 4.6 GiB of RAM (out of 7.8 GiB)?  That's crazy!  Did I mention that it was just uploading 6.5 KiB of data?
[/LIST]
 
[*]Mozilla Firefox memory leak
[LIST]
[*]Firefox 7 was created to improve performance.  Nope.
[*]The program is graying out (not responding) as I'm typing this.
[/LIST]
 
[*]Sound volume controls disabled after standby
[LIST]
[*]I have no control over audio output after a standby occurs.  Ubuntu seems to forget that a sound card is present, even though audio still plays normally.
[/LIST]
 
[*]Decreased customizability
[LIST]
[*]I cannot install themes no matter what guide/tutorial I try.  I have Adwatia, Ambiance, Radiance, HighContrast, and HighContrastInverse.
[*]Unity is totally inflexible.
[*]No pretty Compiz effects. :(
[*]I miss my GNOME Panel applets. :(
[/LIST]
 
[*]Unity & Desktop Environment
[LIST]
[*]Simply said, Unity decreases productivity.  You probably know what I mean if you don't like Unity.
[*]Oh, the window title bar [never updates]("http://ubuntuforums.org/showthread.php?p=11455189") unless one switches from maximized to not maximized and vice-versa.
[/LIST]
 
[*]Banshee Media Player
[LIST]
[*]The "close" button quits the program.  Last time I used Banshee, the "close" button hid the program, which was what it was intended to do.
[/LIST]
 
[*]Ubuntu Software Center
[LIST]
[*]The Software Center has made a shift towards paid applications.  I'm not sure what it's accomplishing because it surely isn't attracting professional software companies like Adobe or Sony.
[*]Takes forever to start up
[*]The longer the queue for APT actions, the slower and less responsive (gray out) Ubuntu Software Center is
[*]Does not seem to be able to load DEB packages when it's not already open
[*]Cannot install Google Chrome. You have to use the Terminal to install Google Chrome:
[LIST]
[*]amd64 instructions:
```
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo dpkg -i google-chrome-stable_current_amd64.deb
sudo apt-get install -f
rm google-chrome-stable_current_amd64.deb
```
[*]i386 instructions:
```
wget https://dl.google.com/linux/direct/google-chrome-stable_current_i386.deb
sudo dpkg -i google-chrome-stable_current_i386.deb
sudo apt-get install -f
rm google-chrome-stable_current_i386.deb
```
[/LIST]
 
[/LIST]
 
[*]GNOME 3 does not work.
[LIST]
[*]Text does not display readably except for the logout screen.
[/LIST]
 
[*]GNOME 2 does not work properly.
[LIST]
[*]I installed the GNOME 2 fallback package.  The GNOME Classic interface hardly works, and the GNOME Classic (no effects) interface is ugly.  GNOME Classic (no effects) doesn't look like GNOME in Ubuntu 10.10.
[/LIST]
 
[*]PHP *does not* work.
[LIST]
[*]This is the turning point for me.  I run a small personal Web server from Ubuntu, and PHP is very important to me.  When I installed LAMP and Webmin, any PHP file I tried to load returned a blank page.
```
sudo a2enmod php5
```"Module php5 already enabled"
Still no PHP.
[LIST]
[*]By the way, the Web server is *not* causing the temperature and performance problems.
[/LIST]
 
[*]I've already taken actions to try to make PHP work.  As a result, aptitude says that I have to remove completely unrelated packages that I need, including Flash Player and my Qt development tools.
[/LIST]
 
[/LIST]


_**Am I Okay?**_
No!  I am *not* okay!  If Ubuntu 12.04 Precise Pangolin follows the failure trend set by Ubuntu 11.04 Natty Narwhal and Ubuntu 11.10 Oneiric Ocelot, computers as we know them... ahh! ](*,)


_**Contradictions**_
I said that Unity was amazing in my previous report, [[Report] Ubuntu 11.04 on HP Pavilion dv7]("http://ubuntuforums.org/showthread.php?t=1765283").  I may have been a little too quick to judge.  When I returned to Ubuntu 10.10, I remembered how much I liked the GNOME Classic interface.

Now, when I see Unity, I'm somehow reminded of [Microsoft Windows 8]("http://img192.imageshack.us/img192/3097/windowsfail.png").  The big icons... the lack of text... the oversimplification... it reminds me of a giant mobile phone.  Ubuntu is not a mobile phone operating system!

I don't know if there's something wrong with me or if I'm too old (although I was born in the 1990s), but mobile interfaces, especially on desktops and laptops, do not appeal to me.

I look back to the screengrabs of my desktop I took years ago like they're a photo album, and I think: "*This is why I switched to Ubuntu in the first place.*"


_**Gallery**_
[[IMG]http://img687.imageshack.us/img687/8640/screenshotsgg.th.png[/IMG]]("http://img687.imageshack.us/img687/8640/screenshotsgg.png") [[IMG]http://img267.imageshack.us/img267/6311/screenshotdebuntu.th.png[/IMG]]("http://img267.imageshack.us/img267/6311/screenshotdebuntu.png") [[IMG]http://img829.imageshack.us/img829/4328/screenshotdebuntu0.th.png[/IMG]]("http://img829.imageshack.us/img829/4328/screenshotdebuntu0.png")


_**More Information**_
For more information from me or if you have information for me, just ask  me either through this forum topic or by my many methods of contact in  my Ubuntu Forums profile.

---

### Post by Deltik on 2012-05-03
[CENTER][[SIZE=7][FONT="Impact"]UPDATE[/FONT][/SIZE]]("http://ubuntuforums.org/showthread.php?p=11900678")
[/CENTER]

I wrote a review for Ubuntu 12.04 LTS Precise Pangolin on computers like my HP Pavilion dv7t-4100 laptop. Click [here]("http://ubuntuforums.org/showthread.php?p=11900678") to see the updated report.

---

