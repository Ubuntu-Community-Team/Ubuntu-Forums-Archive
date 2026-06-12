---
title: "Some ubuntu packages need to be protected"
date: 2010-07-02
forum: The Cafe
---

### Post by sandyd on 2010-07-02
I believe that there should be some packages in ubuntu that **should** be protected, meaning that the user will have to comfirm the removal, after reading its possible effects.
This can probably stop the amount of people from removing network-manager &like

1. Synaptic/Software Center should emit warnings to users if they  attempt to remove a package that could possibly cripple their system,  along with the possible effects of removing it. This warning can be  turned off through the editing of synaptic settings or from a config  file if the user doesn't find them useful. 

2. Cache Network-Manager/Other important apps in the apt-archives as  part of the postrm script 

A lot of users want to try another networking manager such as Wicd  to see if it would fix their networking problems. However, if it  doesn't, and they are left with no internet, they will have to manually  copy over network-manager on to the computer. This is highly non-user  friendly behaviour. If network-manager is in the apt-cache, reinstalling  it should be a breeze. The network-manager takes up less than 1mb here,  so there shouldn't be problems regarding space 

3. Synaptic/Software Center should have a "undo changes" option.  

I have seen a lot of users simply click "ok" even though they were  unintentionally removing tons of packages. In the end, they would have  to look through the logs for the packages, which is also highly  user-unfriendly behaviour. The "undo changes" button would allow users  to undo changes "a step at a time", without jumping around, in order to  prevent them from making a bigger mess. This also allows users to remove  packages that may have fried their system without them needing to  remember the packagename 
 [[...]]("http://brainstorm.ubuntu.com/idea/25328/") 
    
All of this may seem like a long haulover, but it is better for  newcomers to Linux (Most of this stuff won't affect experienced users  anyway because of the option to turn these warnings off)

Vote Here -> [http://brainstorm.ubuntu.com/idea/25328/](http://brainstorm.ubuntu.com/idea/25328/)

---

### Post by chessnerd on 2010-07-02
Agreed.

I actually uninstalled the network manager to install the LX Network Manager and, when I had trouble with the LXNM, I couldn't reinstall it. Eventually, I got the LXNM working, but still, I could have broken my system.

---

### Post by 3rdalbum on 2010-07-02
Some people purposely remove Network Manager, although I do question their reasons to.

Python should definitely be protected. Lots of people install Python 2.5 and remove 2.4, ignoring the warnings that 200 packages will be removed, and then their system is borked.

---

### Post by earthpigg on 2010-07-02
this is all already possible, but only for nerds like us and those willing to become nerds like us.

general outline of your idea, assuming the user is using default/intended/noobfriendly ubuntu methods of doing stuff:

1) 
any package that is a dependency of ubuntu-desktop, when removed in the software center, will automatically be first downloaded to /var/cache/apt/archives.

2) 
the software center needs some new functionality that we shall call "undo software changes" or something like that. it looks at the log files in /var/log/apt, an streamlines the process of undoing things. a good start could be a simple list of things done/undone that have been noted in the /var/log/apt log files, with little check boxes next to them. right click and "undo this" or "redo this". i would advocate that it only allow the user to do these things in reverse-chronological order, and disallow skipping things. if you did stuff that screwed ur computer up, then installed wesnoth, then want to undo the stuff that screwed ur computer up... reverse order. so: first you must "undo" installing wesnoth wesnoth, then you can undo whatever it was you did.

sounds annoying, but since all mistakes can obviously not be anticipated, it will make "undo software changes" less-likely to be as damaging as the current "computer janitor" is when used by non-nerds. if you let people jump around and undo package changes, they will do themselves more harm than good. someone that is knowledgeable enough to exactly identify what they did that screwed things up by reading the apt history logs... wont be using ubuntu software center to repair his/her system, anyways. so, for everyone else, ubuntu software center could let you undo all the package changes one set at a time in reverse chronological order.

leave dotfiles in place, of course, unless the user selects "***completely*** undo this change".

---

### Post by earthpigg on 2010-07-02
> **3rdalbum said:**
> Python should definitely be protected. Lots of people install Python 2.5 and remove 2.4, ignoring the warnings that 200 packages will be removed, and then their system is borked.

i have the controversial opinion that Linux should allow multiple versions of the same package in cases like this. i don't give a damn if it is theoretically "less elegant", nor do i care how much it bothers OCD types. 

it's practical.

the package manager needs to ask itself: "are there any packages installed that claim to require this ***specific*** version of this package?"

if the answer is yes, than install the new package while keeping the old one. (instead of uninstalling 200 packages and then installing the new version of _____).

---

### Post by Dustin2128 on 2010-07-02
I do think it should be disabled by default, but to be completely unremovable, that's wrong. And is the system janitor really suggesting removal of vital packages? If so, I don't think it should be included in 10.10/11.04 (unless/until its fixed).

---

### Post by sandyd on 2010-07-03
> **Dustin2128 said:**
> I do think it should be disabled by default, but to be completely unremovable, that's wrong. And is the system janitor really suggesting removal of vital packages? If so, I don't think it should be included in 10.10/11.04 (unless/until its fixed).

it doesnt actually remove network-manager. It just removed one of network-manager's dependencies which caused network-manager to be removed as well. this is what we call "dependency hell". as for the unremovable section, were not really making it non-removable. were just caching the app, so we can install it later even if there are distasterous consequences associated with the app removal (if you remove network-manager, you will have no internet, and downloading each individual package and its dependencies becomes a pain in the ***)

---

### Post by sandyd on 2010-07-03
> **earthpigg said:**
> i have the controversial opinion that Linux should allow multiple versions of the same package in cases like this. i don't give a damn if it is theoretically "less elegant", nor do i care how much it bothers OCD types. 

it's practical.

the package manager needs to ask itself: "are there any packages installed that claim to require this ***specific*** version of this package?"

if the answer is yes, than install the new package while keeping the old one. (instead of uninstalling 200 packages and then installing the new version of _____).

some of the newer versions of python, such as the one in lucid, depreciate a hell lotta stuff. we are definately looking for trouble if we try to install the new version of python. but then again, why can't we make the two versions of python coexist peacefully?

---

### Post by NightwishFan on 2010-07-03
Part of the reasons is that currently Debian/Ubuntu treat programs classified "recommend" as dependencies. You can turn this off in Synaptic. Go to Settings -> Preferences, and uncheck "Consider recommended packages as dependencies." It becomes much easier to trim programs this way. You can re-enable it when you are done. It requires a bit more expert-ness though.

---

### Post by Dustin2128 on 2010-07-03
> **earthpigg said:**
> 
[IMG]http://www.synthstuff.com/mt/archives/medtees-ocd.jpg[/IMG]

Must..... resist... urge.. to... straighten.... pencil... 8-[

---

### Post by NightwishFan on 2010-07-03
I couldn't I have this problem. :)

---

### Post by sandyd on 2010-07-03
bump

---

### Post by Rubi1200 on 2010-07-03
> **carlee said:**
> I actually believe that some packages on the system should be prevented from being removed.

One of the fatal mistakes that occurs a lot of times is removing network-manager, either through dependency hell, computer janitor, or by some other means. A good idea would be to for the apps that are important, and removal will become a fatal mistake, the postrm script should download a copy of the deb into /var/cache/apt/archives along with all its install dependencies. This may use more space, but will prevent newbies from banging their heads against the wall whenver something like this occurs. Since the deb and its dependencies are already in the apt cache, reinstalling network-manager should be a breeze with no harm done.

> I actually believe that some packages on the system should be prevented from being removed.

Personally, I am not sure if this is a good idea for the simple reason that it a) takes power out of the hands of the user, and, b) who decides what stays and what goes?

> One of the fatal mistakes that occurs a lot of times is removing network-manager, either through dependency hell, computer janitor, or by some other means.
I am seeing this more and more on the forums. I do not understand, or agree, with Computer Janitor being included on the default install. The problems it can potentially cause far outweigh the few MB of space it *might* free up. But again, who decides if it goes? I edit the menus and remove it; what you don't see won't tempt you right? ;)

---

### Post by Bachstelze on 2010-07-03
Apt already does that for important packages, it just doesn't think NetworkManager is important, and I agree with that. An Ubuntu system can function very well without it.

---

### Post by earthpigg on 2010-07-03
> **Bachstelze said:**
> Apt already does that for important packages, it just doesn't think NetworkManager is important, and I agree with that. An Ubuntu system can function very well without it.

i would agree that many (most?) ubuntu desktop systems "in the wild" can function very well without it, but perhaps the folks that decide such things should take into account that many (most?) ubuntu netbook or laptop systems "in the wild" aren't very useful with out it -- even if it is only for the briefest of moments between uninstalling network-manager and installing wicd.

---

### Post by Warpnow on 2010-07-03
Can't you just reinstall it from the CD? Popping in the CD usually brings up a menu asking you if you want to load packages off of it. Does it not still do that?

---

### Post by -grubby on 2010-07-03
> **carlee said:**
> some of the newer versions of python, such as the one in lucid, depreciate a hell lotta stuff. we are definately looking for trouble if we try to install the new version of python.

Python stuff, when deprecated, still works until they break backwards compatibility. Actually, Python 3 is their first such break in compatibility, and I expect stuff in Python 3, when deprecated, will still work until Python 4.

I can see the rationale though; one particularly nasty situation is one where, for example, an application that was designed with Python 2.4 in mind required a Python library when installed that was put in /usr/lib/python2.4/dist-packages/, but then you upgraded to Python 2.5, the app was run with the default version of Python (2.5, now), and it's library wasn't present in /usr/lib/python2.5/dist-packages.

[quote=carlee]
 but then again, why can't we make the two versions of python coexist peacefully?[/QUOTE]

On my Ubuntu server, I have Python 2.6 and Python 3.1 co-existing peacefully. However, when I try to install 2.5, it gives me a the no installation candidate error. It would definitely be nice if apt was less picky about these kinds of things. As far as the user in my example above is concerned, Python 2.5 isn't really an upgrade when their app is broken on it.

---

### Post by Warpnow on 2010-07-03
Some packages have new versions, and some versions have new packages. You can only install the ones with new packages side by side.

GCC, for instance, usually has new packages.

---

### Post by koenn on 2010-07-04
In a Debian/Ubuntu type environment, you should never get this type of trouble, if you install from official repositories for the release you're running. Inconsistencies in dependency handling shoud be filed as bugs against the offending packages. Or the release manager really screwed up.
In my experience, this is extremely rare. 

If you get "dependency hell" from installing/upgrading to software that is not native to the release you're running, maybe you've chosen the wrong distro, or release, or ...

Otoh, maybe the release-centric approach of Debian (and even more so Ubuntu) is not an adequate solution anymore. But in that case, ad-hoc stop gap solutions such as 'protecting packages' is just a workaround that will produce maintnance hell for the package maintainers/release managers as the number of packages that need protection, grows.  An overhaul of the release and software distribution approach might be a better idea.

---

### Post by davec64 on 2010-07-04
> **earthpigg said:**
> i have the controversial opinion that Linux should allow multiple versions of the same package in cases like this. i don't give a damn if it is theoretically "less elegant", nor do i care how much it bothers OCD types. 

it's practical.

the package manager needs to ask itself: "are there any packages installed that claim to require this ***specific*** version of this package?"

if the answer is yes, than install the new package while keeping the old one. (instead of uninstalling 200 packages and then installing the new version of _____).

I was reading up on Fedora the other day, and they now have a system which allows you to install Python 3 along side Python 3. Perhaps something along these lines will spread!

---

### Post by Noz3001 on 2010-07-04
"UNIX was not designed to stop its users from doing stupid things, as that would also stop them from doing clever things." – Doug Gwyn

---

### Post by cb951303 on 2010-07-04
I agree. "sudo tasksel remove lamp-server" makes the system unusable because it removes every dependency. if the core packages were "protected", the whole system wouldn't crash because of a bug in a 3rd party application like tasksel (which comes preinstalled btw)

---

### Post by Half-Left on 2010-07-04
> **Noz3001 said:**
> "UNIX was not designed to stop its users from doing stupid things, as that would also stop them from doing clever things." &#8211; Doug Gwyn

Yep, it's all the rage these days. Stop people from doing this just in-case that happen.

You learn by mistakes, not by locking the system down until no one can do anything

---

### Post by sandyd on 2010-07-07
> **Half-Left said:**
> Yep, it's all the rage these days. Stop people from doing this just in-case that happen.

You learn by mistakes, not by locking the system down until no one can do anything
I am saying that it would be a good idea to add this functionality onto the ubuntu software center (only locking down the software center). you see, people who just want things to work, and want to keep it simple will use the ubuntu software center. the center will prevent them from doing idiotic stuff that will prevent them from making their lives difficult. If their a person who is going to actually tinker, their going to use synaptic, and  they can break their systems as much as they want.

---

### Post by samalex on 2010-07-07
> **carlee said:**
> I actually believe that some packages on the system should be prevented from being removed.

One of the fatal mistakes that occurs a lot of times is removing network-manager, either through dependency hell, computer janitor, or by some other means. 

I ran into this exact thing a few months ago where I installed a package and it uninstalled network-manager.  Yeah I probably would've caught it if I read all the messages :-/  I had to download the packages from my wife's laptop and copy them back to my laptop via Bluetooth to get back up and going.  

So though I don't think they should be prevented from being removed all together (I don't like my system telling me what I can/can't do), I do think there needs to be a huge warning message or something that tells you that removing X package will impact core functionality of the system.

Sam

---

### Post by aysiu on 2010-07-07
> **carlee said:**
> I actually believe that some packages on the system should be prevented from being removed.

One of the fatal mistakes that occurs a lot of times is removing network-manager, either through dependency hell, computer janitor, or by some other means. A good idea would be to for the apps that are important, and removal will become a fatal mistake, the postrm script should download a copy of the deb into /var/cache/apt/archives along with all its install dependencies. This may use more space, but will prevent newbies from banging their heads against the wall whenver something like this occurs. Since the deb and its dependencies are already in the apt cache, reinstalling network-manager should be a breeze with no harm done.
Post it on Brainstorm, and I'll vote it up.

---

### Post by sandyd on 2010-07-07
got it.
waiting for mods -> [http://brainstorm.ubuntu.com/idea/25328/](http://brainstorm.ubuntu.com/idea/25328/)

---

### Post by sandyd on 2010-07-09
bump

---

### Post by Rubi1200 on 2010-07-09
> **Noz3001 said:**
> "UNIX was not designed to stop its users from doing stupid things, as that would also stop them from doing clever things." – Doug Gwyn

I love this!! I am bookmarking this right now.

@ carlee: sorry for the off-topic post but I had to react. :)

---

### Post by Ceiber Boy on 2010-07-09
The first couple of ubuntu os I had a played with until distruction, so that I could learn what I could and could not do, when it went wrong I simply reinstalled it and started again.  I keep a copy in virtual that I use for experimental pourposes so I don't crash my main system.

This preventing people from removing stuff sounds very MS and I don't like it. Remember Linux assumes you know what your doing! If you don't know what your doing you should not be doing it.

---

### Post by Penguin Guy on 2010-07-09
I don't like this idea at all, users need to learn not to uninstall stuff unless they know what they're doing.

> cache the package locally
All packages are cached by default, you can find them in [FONT="Courier New"]/var/cache/apt/archives[/FONT].

---

### Post by aysiu on 2010-07-09
> **Ceiber Boy said:**
> 
This preventing people from removing stuff sounds very MS and I don't like it. Remember Linux assumes you know what your doing! If you don't know what your doing you should not be doing it. It's not preventing people. It's discouraging people.

If people want to remove packages, they still can, and even more easily using the CLI.

---

