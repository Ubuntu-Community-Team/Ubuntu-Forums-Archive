---
title: "System not working properly after an update"
date: 2012-09-09
forum: Ubuntu Studio
---

### Post by loopinaloop on 2012-09-09
I barely can post messages after the last update. I have only 1 workspace and I cannot set more. My right-click button doesn't allow me to scroll down the list because after I move past the first line, menu disappears. Finally, I don't have an upper bar with drop-down menus and it's impossible for me to close down my browers.

It's yet another time when my system is broken after an update. It wasn't an issue 2 years before but nowadays issues do more harm then good. I would like to repair my system without another re-formating of my computer... at least tenth this year :(

---

### Post by sgx on 2012-09-09
Now that reality has spoken, and you will wisely not trust
full system updates, make a separate /home partition
as part of a new install, so reconfiguration will be simplified
by not reformatting /home. Installing new releases to
external drives, or usb/cd/dvd media, is the safe productive way
to test the future.
Cheers

---

### Post by loopinaloop on 2012-09-10
I was thinking about that but I'm not sure how big system partition do I need to feel comfortably, how to configure system to recognize another partition as home directory and many more questions that follows... I will search for additional help on the net but if people can give me more advices or just post links to good & trusted tutorials then I would be more the happy!

Thank you for your support! Full and free technical support with volunteers ready to help the newcomers is something that makes maintaining Linux system really worthy. Although I relay on the community, I feel more independent then on Windows.

---

### Post by smartboyhw on 2012-09-12
Hmm strange I have performed at least hundreds of times of updates and never a workspace problem.

But then yes follow sgx's advice. Sometimes there may be issues with updates:)

---

### Post by HomeOnThePlains on 2012-10-05
Just out of curiosity, had you installed K9copy? I was having the same issue earlier this yr or late last yr (can't rmbr). I'd trash my desktop config files and it would appear to work briefly again, but then go back to the symptoms you described, mainly the missing title bars and unreliable mouse functions. Seems like I tried a diff user account and didn't have the prob then. Perhaps create a new user to have some access until you work it out.

Anyway, I've found 20G to be big enough for a / partition with plenty to spare. Not sure how it would play out over time tho.

To back up your home dir you can simply copy the files to another parition or external drive, etc. Ex: cp -r /home/you <newdevice> or <newpartion>.

Hope things worked out.

---

