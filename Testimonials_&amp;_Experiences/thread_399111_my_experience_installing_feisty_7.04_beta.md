---
title: "my experience installing feisty 7.04 beta"
date: 2007-04-01
forum: Testimonials &amp; Experiences
---

### Post by RogerTa on 2007-04-01
Hi all,

As many others on this forum, I am trying ubuntu (xubuntu more specifically) for the first after getting fed up with the poor (and constantly degrading) performance of windows xp.  I decided to try the 7.04 beta and therefore I am posting this as my experience installing it.  Just so you know, I am a very experienced Windows user (s/w developer by profession) but have only dipped my toes in the Unix world until now.

The computer I am upgrading is an old IBM A20m laptop (about 8 years old), with 256mb of memory, a 400mhz piii, and built-in ati mobile graphics.  This is the "kitchen" computer and is used mainly by my wife for web browsing, email (gmail), light word/excel use, and by my kids to play online flash games.

I started by doing a complete image of the disk, as well as separately backing up my wife's data.  While the latter is always a good thing before upgrading a machine, the former turned out to a a real pita, although a very educational experience :-)

I first tried running 7.04 from the live cd to evaluate it.  Unfortunately it runs far too slowly for proper evaluation purposes.  I mean, it made the existing windows installation look like a speed deamon :-)  However, I was able to determine using the live cd that my wireless card worked (d-link g650), I could install the flash player and play games with the default firefox, and that the audio system worked fine.

Note that for the wireless network, it seems that I had to set the channel as well as the essid before I was connected.  My network does not use a password;  it uses mac address filtering.

So I decided to install xubuntu to the hard disk.  It's then that I discovered the migration tool and decided to use it.  The entire hard disk was partitioned as one NTFS volume, and I was really impressed with the installer's ability to resize the volume in order to make room for its own partitions (one for the system, the other for swap).  Very nice!  I was also pleasantly surprised to find that the installer left my machine with the possibility to dual boot into windows, very very nice!  (So all that pita disk imaging was for naught :-) ) I will eventually get rid of this but during the evaluation I think this is great.

The migration tool brought over all the IE bookmarks, again very nice!  As for the documents, it brought over all the documents except those in one particular subfolder used by my wife.  So basically, it missed all the most important documents :-)  I can't explain what happened.

To fix the document issue, I decide to try and mount the NTFS volume under xubuntu.  I did some searching in the forums and found ntfs-3g.  The howto was easy to follow, and very quickly I had the NTFS volume mounted (read-only) as /mnt/windows.  The only issue I had was that I needed to use the force option to get it to mount.  I suspect the resizing done by the installed left the volume in a questionable state, and I had not rebooted into Windows yet.  I was able to copy over my wife's missing documents and load them into the installed word processor and spreadsheet without problem.

Next I tried to access the other Windows machines I have on my home network.  After more searching on the forums, I incorrectly thought samba was what I needed.  After configuring it half way I realized I was setting things up so that my Windows machines would be able to access this laptop.  However, I wanted this functionality anyway, so I finished the configuration and everything worked just fine.  Again I found the howtos on the forum very useful and easy to follow.

Once samba was installed, I thought I would have been able to access my windows machines.  It turns out I had to install another package for this.  Solving this was just as before: a little reading on the forums, installed and configured the package, and all was fine.

My suggestion here would be that the smb client be installed out-of-the-box.  I'm sitting on the fence as to whether I think samba should also be installed out-of-the-box (then again, maybe they are, I used xubuntu and not ubuntu proper).  One thing that confused me was that the config files for them did exist in /etc, even though the packages were not installed.  Don't know if this is desired or not.

I also installed a few other tools, like the graphical disk partition tool, and a process explorer thing.  This is the first time I have used a package system like apt-get, but it is easy to use and it seems to work well.

I decided to use the Windows XP skin of xfce to keep things familiar to the user's of this machine.

At this point, the only thing left is to figure out is how to print from this xubuntu system to my windows-based printer.  I need to do some more searching/reading in the forums.

Overall, I am very impressed with ubuntu, and very happy so far.  It has surprised me in many ways, all pleasantly.  The performance is much better than Windows, which was the reason for this trial in the first place.  I now hope it stays that way;  Windows XP ran OK after it was initially installed but degraded after that.

Thanks ubuntu team!

---

### Post by Michaelt74 on 2007-04-01
Good to know your experience has been positive so far, keep us informed as to how you're progressing. I'm keen to try out Feisty but not in the beta stage.

Good luck!

---

### Post by irish_flu on 2007-04-01
Hey buddy, that's awesome!  So many of us just post here when we have problems; thank you so much for taking the time to post what sounds like a great experience with installation.

---

### Post by wrycatcher on 2007-04-04
Always fun to read stories like yours!  You also seem to be savvy enough to be able to figure things out with tips from Ubuntu forums.  Enjoy shaping Ubuntu (XUbuntu, in your case) into precisely what you want...and, more importantly, what you **DON'T** want... ;)

On a side note, I am eager for the latest version (Feisty Fawn -- 7...) to be released.  I've heard a lot of good things about it in beta.  Apparently, it is a huge improvement over what I run (Edgy).  I am quite curious...  However, there are just enough potential problems to make me hesitate to install it yet.  At this time,  I just don't want my Ubuntu to suddenly be dead in the water...so I'm tempering my enthusiasm.  Hopefully my patience will be rewarded with a fairly painless update process.

Generally, I don't mind living on the bleeding edge to a point.  I don't need the ultra-conservative stability of Dapper, for instance.  I'm willing to accept *some* risk and occasional problems in exchange for the *latest and greatest* features.

Keep us posted on your foray into Ubuntu Linux land.  I'm relieved to hear that Feisty didn't end up scaring off a potential Linux convert...

---

### Post by Bafflerog Rumplewhisker on 2007-04-07
Actually, I find that 6.10 stable is far more unstable than 7.04 beta. :)

But that's just me.

Haven't had ANY problems with 7.04 so far ( since day 1 of its release ), yet I had problems with 6.10 as soon as I installed it.

Oh well.

7.04 is by FAR the best OS experience I've had. Can't wait for stable!

---

### Post by RogerTa on 2007-04-07
Hi all,

Thanks for all the encouragement :-)  Here is some more of my experience, as promised.  The next step was to get the printer working.  This has not gone as well as the previous steps.

I have an Epson Stylus Color 880 connected to an XP machine.  I found this article that explains how to connect an ubuntu system to an XP printer:

[https://help.ubuntu.com/community/WindowsXPPrinter](https://help.ubuntu.com/community/WindowsXPPrinter)

The instructions did not apply at all though, maybe because I am using xubuntu and not ubuntu proper.  I had to use the menu item "Applications / Settings / Printing".  I then did the following:

[LIST]
[*]clicked on "new printer" icon
[*]set the name, description, and location, pressed forward
[*]chose "windows printer via samba", pressed forward
[*]entered computer name, share name, username, and password.  Pressed verify and it was successful.  Pressed forward
[*]chose "Epson", pressed forward
[*]chose "Stylus Color 880", pressed forward
[*]I used the recommended driver, pressed forward
[/LIST]

I got an error that the package "gutenprint-foomatic" had to be installed first.  I tried to search for this package using the package manager and synaptic, but it was not to be found.  I installed some other packages with the name "foomatic" and "gutenprint", but still to no avail.

I tried a couple of the other choices, and got this error message:

```
Cups server error, there was an error during the cups operation:
'server-error-internal-error'
```

I finally chose the driver called "gutenprint v5.0.0.99.1", and the printer was finally installed.

I then started abiword with a landscape-formatted documented (a document initially created with MSWord), fixed up the margins a bit, and printed.  The page was printed portrait.  I double checked the page layout in abiword and it was definitely set to landscape.  I then checked the printer properties and they were set to portrait.  It seems there is a problem transferring the portrait/landscape setting from abiword to the printer.

I changed the printer property to landscape and printed again.  This time the page was printed landscape, but it seems the right hand margin was set for 8 1/2 and not 11.  Unfortunately, this may be a know bug:

[https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/6735](https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/6735)
[https://bugs.launchpad.net/ubuntu/+source/libgnomeprint/+bug/24785](https://bugs.launchpad.net/ubuntu/+source/libgnomeprint/+bug/24785)

I got the same result trying to print to pdf.

So I installed openoffice 2.2, it was a little better.  Printing to pdf worked, but trying to print the pdf from the generic document viewer that comes with xubuntu gave me the same results.  I tried all sorts of combinations, portrait, landscape, custom portrait, custom landscape, setting width and height manually, etc, nothing seemed to work.  I need more investigation…

I'll keep posting with more as I discover it.

---

### Post by BlackHero on 2007-04-12
good work friend congratulations =)

---

### Post by miguev on 2007-04-15
Nice post, but is there any way to skip the migration tool?
[I cannot install Feisty because the migration tool gets stuck!]("http://ubuntuforums.org/showpost.php?p=2456786&postcount=514")
Thanks!

---

