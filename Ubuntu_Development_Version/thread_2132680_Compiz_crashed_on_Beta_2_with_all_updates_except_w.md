---
title: "Compiz crashed on Beta 2 with all updates except what was held back."
date: 2013-04-05
forum: Ubuntu Development Version
---

### Post by kevpan815 on 2013-04-05
Bug Report Filed. Not sure what the Bug Report # is however.

---

### Post by jerrylamos on 2013-04-06
2 installs of 2 April raring amd64 so far, both compiz crashes and recovers.  Launchpad bug #1164157.  Seems to me the compiz in 2 April (Beta 2) is way way down level.

One install on a 10.1" netbook (drives 20" 1600x900 external monitor USB 2 SSD is running fine thank you) the other a notebook with 1280x1024 external monitor which I like better than the native 1366x768.

---

### Post by Dark_Horizon on 2013-04-09
I've just loaded the Beta 2 at first things went more or less ok I had  less crashes and error reports than I got with 12.10, I noticed a few  niggles like Cairo dock having problems so I assumed Hmmm must  be the graphics driver, so I called up software sources and additional  drivers and noted that there were no propritory drivers in use just some  sort of generic x.org server  thing, so i tootled off and changed it for a nice  tested Nividia one, that will fix it and everything will be lovely in  the garden.... or so I thought.
Then I rebooted. on boot I noticed the text was all big and thought fair  enough seen this happen in windows many a time, fix that when I log  in... everything was a mess, I called up system settings and noted I  could only get 1280x1024 so naturally I assumed that changing the driver  back to the original would fix things. NO! what it did was give me  something close to the fall of vallhalla my screenlets corrupted no  unity and most of the graphics jumbled up my family and other animals. Luckily Cairo dock was  working  I got online to find a way of either restarting Unity or  reinstalling it. what I did after thinking about it was this, I'd done  this before in 12.10. So it was either this or a reinstall

Ctrl+Alt+T open terminal

"sudo apt-get install dconf-tools"

ran this command to reset Unity and Compiz

"dconf reset -f /org/compiz/"

Followed by

"setsid unity"

Which  worked well after a reboot or two, it seems that Compiz is in a bit of a  fragile state. This was already an issue in 12.10 one would have  thougth they would have worked on it by now but apparently not! They can't surely be putting this out in 15 days, I can see the issue date getting pushed back or things will just get worse. If you get problems with compiz try what I did

---

