---
title: "uninstall seems incomplete"
date: 2008-04-07
forum: Ubuntuzilla
---

### Post by AptlyNamed on 2008-04-07
I recently did a fresh install of Hardy beta5 and used it with my original (Feisty) home partition. After installing Thunderbird from the Hardy repositories I discovered that Lightning wasn't working: It showed no events and the 'new event' and 'new calendar' menu-items were greyed out. 

So I installed Ubuntuzilla and Lightning was working again, but now the fonts  in the Thunderbird UI were too large and blurry. I uninstalled Ubuntuzilla , removed everything in /opt/, restored the original .mozilla-thunderbird, deleted the .thunderbird symlink and reinstalled Thunderbird from the Hardy repos.

But Lightning kept working. It does make me wonder: what else has been changed/installed by the script that is still there?  Any libraries?

---

### Post by nanotube on 2008-04-07
> **AptlyNamed said:**
> 

But Lightning kept working. It does make me wonder: what else has been changed/installed by the script that is still there?  Any libraries?

yes, libraries :)
if you look at the dependencies of the ubuntuzilla deb, you'll see them. there's libnotify-bin, libstdc++5, python, libgtk-2.0.0, gdebi. of these only the first two are not present by default, and only the second one could possibly have anything to do with lightning working.

not sure whether that is actually the case... but there's your answer. :)

---

### Post by AptlyNamed on 2008-04-07
> **nanotube said:**
> yes, libraries :)
if you look at the dependencies of the ubuntuzilla deb, you'll see them. there's libnotify-bin, libstdc++5, python, libgtk-2.0.0, gdebi. of these only the first two are not present by default, and only the second one could possibly have anything to do with lightning working.

not sure whether that is actually the case... but there's your answer. :)

Thanks. I'm glad my calendar is back! I knew the info should be in the sourcecode but I couldn't figure it out. Maybe you could add some details to the wiki what actually gets installed and changed. I think for most people scrips like these look a bit risky because it's hard to determine wether they will break something.

---

### Post by nanotube on 2008-04-07
> **AptlyNamed said:**
> Thanks. I'm glad my calendar is back! I knew the info should be in the sourcecode but I couldn't figure it out. Maybe you could add some details to the wiki what actually gets installed and changed. I think for most people scrips like these look a bit risky because it's hard to determine wether they will break something.

well, when you install the .deb, it should tell you "the following packages need to be installed" or something to that effect. but maybe you're right, adding the list of dependencies to the website can't hurt. :)

---

