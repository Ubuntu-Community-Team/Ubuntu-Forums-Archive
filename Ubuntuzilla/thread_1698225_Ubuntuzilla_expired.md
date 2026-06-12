---
title: "Ubuntuzilla expired"
date: 2011-03-02
forum: Ubuntuzilla
---

### Post by witeshark17 on 2011-03-02
Has anyone had success changing from Ubuntuzilla FF to new releases from repos? I have tried all night to make the transition; I see the new FF 3.6.14 in Synaptic but all attempts to remove Ubuntuzilla and reinstall the update have not yet worked. What do I need to do? So no one anywhere seems to know... do i need to do a full remove of FF and redownload from scratch to get 2.6.14 to actually take the place of the old copy?

---

### Post by jasmines on 2011-03-02
I think the new version will be shortly uploaded in Ubuntuzilla Apt, so we have just to wait...

---

### Post by the.phantom on 2011-03-02
> I see the new FF 2.6.14 in Synaptic

hope that is a typo?
when ubuntuzilla started the official repo's were a week + late on getting the updates

now they seem to realize the priority
but been using this great way for several years and not ready to change as they are reliable
give him at least 24 hours to do it ;-D

---

### Post by witeshark17 on 2011-03-02
Yes I mean 3.6.14 Right now neither method is able to replace FF I'm not sure what to try next

---

### Post by the.phantom on 2011-03-02
ok
now did you install ff with ubuntuzilla scripts or just the using the repo's?

(scripts were used about 2 years ago)

my guess is repo's
if so when you tried to remove it did you do it exactly this way?

Removal

To uninstall the packages, uninstall the *-mozilla-build packages, using your favorite package manager. E.g., using apt-get:

sudo apt-get remove firefox-mozilla-build
sudo apt-get remove thunderbird-mozilla-build
sudo apt-get remove seamonkey-mozilla-build

If you no longer wish to have the Ubuntuzilla repository in your sources, you can edit it out of your /etc/apt/sources.list. 

then try and use the ubuntu to install the ubuntu version

---

### Post by witeshark17 on 2011-03-02
I used the Ubuntuzilla terminal script about a month ago. Now that scrpt returns an error, so I tried with the newer method: **ppa:mozillateam/firefox-stable** added to the Sofware Sources option in System menu. That download completed and applying changes seemed to as well. But the 3.6.13 is still in default for use. Looking in Synaptic Package Manager, I can see 3.6.14 13 and 10 as available, but only if I highlight 3.6.14 and view the package menu (3.6.14 is the only one listed in Synaptic Package Manager search). In /etc/apt/sources.list I don't see anything for Ubuntuzilla, but there is a general third party URL listed. -Thanks for the reply!

---

### Post by the.phantom on 2011-03-03
ok if you used the scripts
when you removed it
did you

> Old ubuntuzilla installer script users note: before installing these packages, run "ubuntuzilla.py -a remove -p packagename". Otherwise installation may fail due to the existence of a local diversion of /usr/bin/ links, placed there by the old ubuntuzilla script.

---

### Post by witeshark17 on 2011-03-03
> **the.phantom said:**
> ok if you used the scripts
when you removed it
did you I used a remover, but it didn't match what you posted. I suppose I'm in for a bit of work cleaning this up... Well I have downloaded Chrome for the interim, thanks for posting, and any more ideas, please feel free! I just tried replacing the script; the paths are gone... I will have to remove these directories and such manually; the base command ```
ubuntuzilla.py
``` is lost as the path set up by the original command ```
sudo dpkg -i /path/to/ubuntuzilla*.deb
``` This could be frustrating, but Chrome has put that at ease...

---

### Post by Ev1L on 2011-03-05
> **the.phantom said:**
> hope that is a typo?
when ubuntuzilla started the official repo's were a week + late on getting the updates

now they seem to realize the priority
but been using this great way for several years and not ready to change as they are reliable
give him at least 24 hours to do it ;-D

I am constantly refreshing the update manager and I am very surprised/scared by this Ubuntuzilla delay.
I am not sure what this means for the future. The whole point was to have updates immediately without waiting ages for Ubuntu repos...

---

