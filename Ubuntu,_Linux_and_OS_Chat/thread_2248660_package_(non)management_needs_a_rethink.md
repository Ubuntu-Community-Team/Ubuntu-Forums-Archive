---
title: "package (non)management needs a rethink"
date: 2014-10-16
forum: Ubuntu, Linux and OS Chat
---

### Post by mastablasta on 2014-10-16
no, seriously it does. while there is an experimental Linux distro that installs apps in their own folder, PC-BSD already has something like that. and though the size of such packages might be bigger at least there shouldn't be any problem when you remove them.

I just finished a second battle with Debian and apt-get. 
the thing is the CLi interface is quite uninformative. what happened is that I needed partman. after finding out it shouldn't be installed I though it is partition manager. so sudo apt-get install... many thing will be installed are you sure. yes I guess so and it installs partition manager and half of KDE with it. darn.

ok no problem apt-get remove... after some time mini dependency problem (hell). after spending almost an hour on google (as various force remove option didn't work) and IRC someone there suggested to try to remove some KDE stuff instead. that got me forward a bit. until some more googling revealed some other packages and after checking what they are I uninstalled them and thus finished the saga.

It is ridiculous! you install a program and when you remove/uninstall it, it should remove all the stuff that the app brought with it and not also the one used by other programs. instead it makes a mess. and then people say how windows is bad as registry need cleaning. well apt-get is even worse as it leave the files on the system!!!! if someone says disk space is cheap these days - well yes it kind of it, so it doesn't make sense to organise package management in such a way.

second battle - Openmediavault did way too much logging. even after solving the bug issue by turning off some logging, it logged the log error of the errors and of the turned off log. anyway I had RAID disks spinning up every 10 or 15 minutes. in 2 days it accumutaled over 300 MB of logs. that's just not what I want. i will wait for them to fix this issue. there are other issues in interface (my config would need editing config files which I can do inCLI only just as well). right so let's remove it the same way as we installed it...

apt-get remove openmediavault

but that removed only small part of it and now logs went into overdrive. every second error, error, error. ah so only small thing was removed. collectd monitor that omv brought in stayed (note here that OMV was installed onto netinstall AKA minimal). idiotic. let's remove it...
ok now the error logs are toned down a bit but still calling for various monitors and such and writing errors. then I remember how about autoremove.

so I run it - stuff get's removed. in the meantime I put my kid to bed. I come back and I see there is only one logging being done a chron job. another leftover. right... ssh into server using key, sudo nano...

no sudo? what? yes autoremove removed sudo..... now what? moving the box to the screen, re-pluging the cables and all that?!?! well luckily the web interace I used has a terminal inside and I can go root there (hmm not sure how safe is this option yet) but anyway installed sudo and continued with clearing chron jobs and scripts left there by the omv.


**remove and purge do not remove only the necessary previously installed components**.[B] I think this is way worse than having an unnecessary line in the windows registry.
[/B]
**When they are removing apps they can remove components needed in other part of the system. this is no management to me.**

oh yeah and aptitude is a mess. is there a synaptic with text only interface? 

also I am starting to really dislike Debian. stable "schmable" .... and thinking about switching the server to Ubuntu LTS. still it deserves a fifth chance I guess.

---

### Post by buzzingrobot on 2014-10-16
Package managers in Linux are so closely coupled with the shared library approach that changing one without changing the other might be impossible.  The intramural political difficulties would be huge.

Still, something is clearly wrong when the removal of a package can trigger the removal of previously installed packages. That should not happen.

I've seen this happen on my own systems with Ubuntu meta-packages, in particular. Trying to remove a major component of, say, a KDE meta-package installed on a Unity base, very often triggers the removal of previously installed packages.  Forum posts from users who have been victimized by this are not uncommon.

It's not rare, either, to run into a situation where some mundane little package triggers cascading dependencies that bring in dozens of other packages. That's the get "half of KDE" syndrome.   While those dependencies are real, created by different developers at different times working on their own efforts independently of each other, that scenario seems to me one obvious instance where the current approach to dependency resolution really needs to be rationalized.

---

### Post by grahammechanical on 2014-10-16
loading ...... an advertisement for Ubuntu's new Click packaging method and Ubuntu's proposed image updates instead of package updates.

---

### Post by Tadaen_Sylvermane on 2014-10-17
I know this isn't what anyone wants to hear. Run Arch. Pacman is a dream come true. Much superior to apt*

---

### Post by QIII on 2014-10-17
It's not that it isn't something nobody wants to hear... it's that it's off topic and "use something else" does not address the problem.

---

### Post by mastablasta on 2014-10-17
I get it that they are linked with shared libraries. However, as I know windows also use shared libraries. And just in case a newer version is needed the program drags it in it's own folder. upon removal it removes it's own libraries but doesn't touch the ones that could be shared. This has two implicaitons - one is that that removal/uninstall is safe and doesn't break the system. Second one is that it creates additional bloat as sometimes programs would add libraries in shared folder. that's how I get it. and that's how windows folder grows over time... the issue is disk space. windows folder can grow a lot. programs are also much bigger. but on the other hand removing such an app does not cause system wide malfunction.

a middle approach is needed. I realise this is difficult and will be solved somewhere else rather than on this forum. I just felt the need to point this out to the community as maybe someone could get more involved. Not searching for a solution here (though if someone has it it would be very welcome) but I am point out to experts and beginners alike what is in my opinion quite a big fundamental flaw in the system and very user un-friendly. 

while the process does warn what libraries will get removed a beginner would not know if they are relevant to any other part of the system or not.

furthermore in my opinion it is not good to have programs you do not need installed. let's say a php is installed as some dependency. that is not a problem in itself on a desktop, but on server it needs to be hardened.

which is another topic... reading about how you can easily install services (even in G+ posts and videos from Mr. Shuttleworth) is all good. It makes Ubuntu really easy to use. but what I find disturbing is that you need to actually do a second reading ("hidden on the internet") on how to secure these easily deployed services (I am not talking about paranoid mode, but basic security). it's just not there out of the box. package management should run setup with basic security in mind. I am not sure an 8 letter password will do without some basic stuff like fail2ban, apache/ngnix hardening in place during the easy app install. default SSH is still password, eventhough it is not deemed very secure. ok for LAN this actually ok, but for server opened to internet?

Desktop GUI installer is fantastic - few steps, easy to manage.  a similar thing should pop out when installing webservices. in CLI or textbased.

---

### Post by buzzingrobot on 2014-10-17
> **mastablasta said:**
> ... windows also use shared libraries. And just in case a newer version is needed the program drags it in it's own folder. upon removal it removes it's own libraries but doesn't touch the ones that could be shared.

This comes with implications for security and updates. When an application dumps its own version of its own supporting libraries in its own directory, users become dependent on that app vendor for updates. If the app lacks an automated update checker/reminder, the user needs to remember to check for updates manually, assuming the vendor has implemented some kind of updating mechanism in the first place.

The security implications rest in the potential proliferation of multiple modified versions of core components. Users are dependent on each individual vendor applying patches and alerting users to their existence. Many, many apps litter the Windows world that no longer receive any updates at all, but remain available for use.

In the long term, I think we will see increased adoption of the model Apple uses for phones and tablets:  Hardware is essentially inalterable; all software and all software updates are channelled through a single, vetted, source. This runs counter to the "freedom" many Linux users expect to have to do with their systems as they see fit. But, the near-total dominance of locked-down laptops and small devices, and increasing sales of similar all-in-one desktops, demonstrates that kind of "freedom" has little appeal for most people. People lack the expertise to provide for their own internet security.  And it isn't reasonable to expect them to acquire it. So, we will do what we all do today, anyway:  Decide to trust someone else to provide that security.

---

### Post by mastablasta on 2014-10-19
> **buzzingrobot said:**
> This comes with implications for security and updates. When an application dumps its own version of its own supporting libraries in its own directory, users become dependent on that app vendor for updates. If the app lacks an automated update checker/reminder, the user needs to remember to check for updates manually, assuming the vendor has implemented some kind of updating mechanism in the first place.


portable apps on windows (various version i think there are at least two good ones) - they will do "apt-get update" when you plugin the USB (if you set it up like that) . so no this is not really an issue. not if you have all packages downloaded from same repositories like in ubuntu. those app still have their own folder each and can be removed from the USB without messing up the windnows instalation (or even touching it).

Libre office, Firefox, Thunderbird... various opensource apps available in ubuntu work just fine on those USBs as portable apps. i am not saying the whole system should be designed like that (well maybe that would also work...)  but at least keep the separated from the OS yet at the same time connected.

---

