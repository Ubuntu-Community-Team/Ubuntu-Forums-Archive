---
title: "Ubuntuzilla script won't download"
date: 2009-09-13
forum: Ubuntuzilla
---

### Post by zamek on 2009-09-13
I tried to download the Ubuntuzilla script to update Firefox 2.0 but got this error: dependency is not satisfiable: libstdc++5 . Anything I can do to resolve this? I'm running Ubuntu 7.10, Gutsy Gibbon.

---

### Post by nanotube on 2009-09-13
that's strange - can you look up in synaptic libstdc packages?

---

### Post by nanotube on 2009-09-13
also note that gutsy is no longer supported - no more security updates, etc. 

so suggest you upgrade. :)

---

### Post by zamek on 2009-09-13
the Synaptic manager says I have "The GNU Standard C++ Library v3" and the package is libstdc++6.
 
I'm a rank beginner with Linux Ubuntu so I just wanted to do a quick upgrade to the latest version of Firefox because it wasn't displaying a web site properly the way Internet Explorer was in Windows. It seemed like a simpler, safer and easier option than upgrading the whole operating system, which I have never done. After fruitless searches on how to do this I came upon your page for doing this but it didn't work. Hence my frustration!

---

### Post by nanotube on 2009-09-13
well, libstdc++5 has been available on all ubuntu releases, including gutsy. it should be in the 'universe' repository - do you have that one enabled?

---

### Post by zamek on 2009-09-13
after a search I can only find libstdc++6 not libstdc++5

---

### Post by nanotube on 2009-09-13
> **zamek said:**
> after a search I can only find libstdc++6 not libstdc++5

do you have the universe repository enabled? libstdc++6 lives in main, libstdc++5 lives in universe.

---

### Post by zamek on 2009-09-15
I have all the repositories marked: main, universe, restricted, multi as well as source code but now can't even find libstdc++6 after reload. I do get an error box saying could not download all repositories (don't know how to copy this info here) so maybe that's the problem though have no idea how to fix it. I've tried reloading the repository several times and from different servers with no success. There is also a GPG warning about unable to verify a public key right after after the error box.

---

### Post by nanotube on 2009-09-16
well, gutsy is no longer supported, so they tookn the repositories offline. 

if you still want to use gutsy, you have to change your /etc/apt/sources.list, and replace archive.ubuntu.com with old-releases.ubuntu.com

see [http://packages.ubuntu.com/](http://packages.ubuntu.com/) for list of versions which are supported, and a link to old-releases server.

---

### Post by zamek on 2009-09-17
I ended upgrading Ubuntu Gutsy to Hardy Heron rather than try to jump through all the hoops to install a newer version of Firefox in Gutsy. Took about an hour but was basically all automatic except for a few query boxes which I wasn't exactly sure what to do with but hope I made the right choices. Everything seems to work OK though. The funny thing is that even after upgrading the OS I still was not seeing the web pages of a particular site  correctly (this was the reason I originally wanted to update Firefox). The page source showed that the images should be there but were not being displayed. Somehow by accident I stumbled upon the page info box (CTR i or under the tools menu tab) and under the permission tab I noticed that the images were blocked for this page. Don't know how this was activated but resetting this option to allow images to show solved this problem right away. All this time and work spent in trying to solve a problem that had such a simple solution (less than 1 minute). This is not the first time where I have gone on a wild goose chase to try and fix some problem that had a relatively simple solution. I can't help but think that in hindsight there must be a better system to help resolving problems in a more efficient way...

---

### Post by nanotube on 2009-09-18
> **zamek said:**
> I ended upgrading Ubuntu Gutsy to Hardy Heron rather than try to jump through all the hoops to install a newer version of Firefox in Gutsy. 

well, given that gutsy no longer gets security updates, it was a good thing to do, regardless.
> 
Don't know how this was activated but resetting this option to allow images to show solved this problem right away. 

nice :)

> 
All this time and work spent in trying to solve a problem that had such a simple solution (less than 1 minute). This is not the first time where I have gone on a wild goose chase to try and fix some problem that had a relatively simple solution. I can't help but think that in hindsight there must be a better system to help resolving problems in a more efficient way...

indeed there is - asking a question on these forums, or on the ubuntu irc channel, usually works. :) you just have to actually ask about what's bothering you. for example, if you'd asked specifically about your images problem, someone is sure to have suggested to check whether images are enabled for this site. :) since you never asked... nobody said anything.

---

### Post by zamek on 2009-09-19
You're absolutely right: had I described my initial problem without making any assumptions it would have been much better. I don't know why I mistakenly assumed that the problem laid with an outdated browser (in hindsight it seems ridiculous). Chalk it up to a newbie mistake I guess. When faced with a problem it seems more often than not that formulating the right question(s) to describe it is harder than finding a solution to the problem. Thanks for your help anyways, it's been a good learning experience!

---

### Post by nanotube on 2009-09-20
> **zamek said:**
> You're absolutely right: had I described my initial problem without making any assumptions it would have been much better. I don't know why I mistakenly assumed that the problem laid with an outdated browser (in hindsight it seems ridiculous). Chalk it up to a newbie mistake I guess. When faced with a problem it seems more often than not that formulating the right question(s) to describe it is harder than finding a solution to the problem. Thanks for your help anyways, it's been a good learning experience!

don't beat yourself up over it - we all make the same mistake every once in a while. :) 
enjoy your ubuntu experience - and always feel free to ask questions when you have any :)

---

