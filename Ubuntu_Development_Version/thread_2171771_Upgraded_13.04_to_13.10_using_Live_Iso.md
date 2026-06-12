---
title: "Upgraded 13.04 to 13.10 using Live Iso"
date: 2013-09-01
forum: Ubuntu Development Version
---

### Post by craig10x on 2013-09-01
I did the upgrade using the live 13.10 daily build iso and it seems to have transferred everything over (except my Google Chrome which i will have to re-download)...but i just noticed that i am missing my scroll bar on nautilus and also when i try to scroll up and down on a web page in firefox, it does not scroll on the web page itself (unless i use the side scroll bar that is on firefox)....I can scroll a web page with my computer's up and down buttons but not with my mouse...

Anyone know how to restore it? 
Otherwise, everything seemed to transfer over remarkable well...though i will still have to check everything over...some settings went back to defaults but i already changed those back....

Edit: I found the problem...apparently when i was upgraded, the setting for 2 finger scroll was checked (which it should not have been in)....once i unchecked it, then i got my web page and nautilus (mouse) scrolling back!
Sorry to confuse things...wasn't a scroll bar missing it was touchpad mouse scrolling that was missing...
So i solved my own problem... :D

I must comment that i was surprised that the upgrade went as smooth and complete as it did....the method i used was doing it from the actual live iso, it seems to work very well and it is fast...only took maybe 5 minutes more then an normal ubuntu clean install would take...

I will have to check my programs over, but looks like that other then Google Chrome getting uninstalled, everything else appears to have transferred over...
Looks like i am back on Ubuntu development again....;)

Edit: I just re-downloaded Chrome and as soon as i installed it and opened it, it came right up with all my original settings, extensions, web page caches, etc...like it was never gone....wow...i am impressed....i would say based on this experience, that if you are going to attempt an upgrade...do it off the live iso itself...it works remarkably well...

---

### Post by craig10x on 2013-09-02
The one thing i can't figure out is when someone asks about the best way to upgrade, it is almost always suggested they either do it in the software updater or using the terminal...I never tried those methods and this is the first time i did an upgrade instead of a clean install, but it seemed to me that using the upgrade option on the actual iso made more sense...no internet needed (installs right from the iso directly) much faster and very smooth....in fact, it looks just like when you do a clean install except certain different things go on...like toward the end when it restores all the data and programs you have in your old install...

I checked everything over today and it is all as it was on my 13.04 install except for just 2 items that got knocked out, and that was Google Chrome and Microsoft Core Fonts (which very likely had to do with the fact that they are the only apps i was running that requires saying yes to a license agreement)...It was easy enough to add them back on...

I was really amazed how fast it went...usually a clean install takes around 20 minutes i have found...this took like maybe 25 minutes...I am sure if done through the updater or terminal it would not doubt have taken much much longer...
I think my biggest surprise was how WELL it worked in terms of the results... :)

---

### Post by craig10x on 2013-09-03
I was just curious...has anyone else here used the "upgrade from the live iso" method and did you have a similiar experience like i did?  I was wondering if i was just lucky or has it really become a very reliable way of upgrading? :D

---

### Post by Aenima99x on 2013-09-04
I just did an upgrade from the live iso yesterday and mine didn't go quite as good as yours. All of my apps were uninstalled during the upgrade (with no warning)....however like you, once I reinstalled them all the settings were the same as before.

---

### Post by craig10x on 2013-09-04
Sorry to hear that...that is a bit surprising (that all the apps you installed were lost)...As i mentioned, my Google Chrome and MS Core fonts were knocked out but i attributed those to having license agreements that you have to say "yes" to...At least you didn't have to restore the settings in the apps...so at least we know that settings do get retained it would seem...
All my apps were originally installed using the ubuntu software center....the only outside app was Chrome (though i used the Software Center to actually install the deb file)...

Also, it is a good idea to turn off any extra ppas that you have (i unchecked mine prior to the upgrade)...maybe i was just super-lucky...I went into knowing that in case things went badly i could always do a clean install though in my case, that was unnecessary...I would imagine it still saved you some extra work though (over doing a clean install)...

Did your data come through ok?  (you know like mp3s, videos, photos, documents, etc...stuff you had in your file manager)....mine came through 100% perfect...

---

### Post by VMC on 2013-10-14
First time I read about upgrading system from a live ISO. Some research I found _**[these interesting answers]("http://superuser.com/questions/591116/upgrade-to-ubuntu-13-04-from-12-04-with-iso-image")**_.

---

### Post by philinux on 2013-10-14
> **VMC said:**
> First time I read about upgrading system from a live ISO. Some research I found _**[these interesting answers]("http://superuser.com/questions/591116/upgrade-to-ubuntu-13-04-from-12-04-with-iso-image")**_.

Yes I've seen that too.

---

### Post by craig10x on 2013-10-14
I took a look a the link...don't understand what they are referring to...all i know is...i popped in a dvd iso of 13.10 daily build when i had 13.04 installed on my system, and ran it in live session first, then selected to install to see what options were offered...one was to replace my 13.04 with 13.10 (by erasing it totally) and the other was to UPGRADE my 13.04 to 13.10 and that is the one i used..and it brought over all my apps and data (with the exception of Chrome and Ms Fonts)...and cleaned out all the 13.04 stuff...essentially it felt like a clean install to me, except it saved me all the bother of having to restore my data and apps from 13.04 :D

Even now that i am running 13.10, if i run a live iso it offers the option to upgrade rather then clean install it...so the option is there and easy to use...and in fact on thursday when the final is released, i am going to use that option again to clean my system and make essentially a clean install of 13.10 final...

This method seems to be a superior method of upgrading to using the popularly used software updater method of upgrading...True i never used that other way to compare but i am just basing it on lots of negative experiences i have read from people who used it...

As a point of reference, i have a friend that used the upgrade using the iso installer method to move from 12.10 to 13.04 and it has similar results to mine...in other words, excellent results...

edit: oh, i think i understand now...but i am a bit surprised that the live installer doesn't offer the upgrade option normally unless you only have ubuntu installed alone...and that you have to use the workaround to get it if you have multiple systems installed...
      
Perhaps someone who has multiple systems on their drive can just run the live installer iso and see and confirm whether that is the case, and let us know?

---

### Post by craig10x on 2013-10-15
So...Just out of curiousity, i was wondering if the upgrade option is offered on the live cd iso installer if one is multi-booting but only has 1 ubuntu in the "mix"....
Any combination really...even with other linux distros...but again with only 1 ubuntu....If someone has the arrangement and can check it on the live installer and report here...would be appreciated!

Even if you are running 13.10 currently, you can check it...because i can tell you that when i check it (i am just running ubuntu 13.10 by itself) by popping in a live iso of 13.10 and check the installer,
it gives me 2 automatic options...replace 13.10 with (clean install) or Upgrade to 13.10...

---

### Post by ventrical on 2013-10-15
The option to upgrade was there about 2 and 1/2 months ago.  I did a successful upgrade back then. haven't tried it since then. maybe  I will again... it works though ..

---

### Post by craig10x on 2013-10-15
Very cool, ventrical! So, i guess i can make the suggestion to anyone whether single booting or multi booting as long as they are only running ONE ubuntu on their drive...

I'm going to upgrade my 13.10 again with the final iso (just to clean things out and get essentially a fresh install) right after the 17th when the final comes out and will report on my results...
It's my last "test" before i go the Final to Final Rolling using Iso Upgrades method that i am planning from this point on...:D
It will be interesting to see if upgrading on a regular basis (to each new final ubuntu version when available) is at this point in time, reliable enough to use it that way...

---

### Post by ventrical on 2013-10-15
> **craig10x said:**
> Very cool, ventrical! So, i guess i can make the suggestion to anyone whether single booting or multi booting as long as they are only running ONE ubuntu on their drive...

I'm going to upgrade my 13.10 again with the final iso (just to clean things out and get essentially a fresh install) right after the 17th when the final comes out and will report on my results...
It's my last "test" before i go the Final to Final Rolling using Iso Upgrades method that i am planning from this point on...:D
It will be interesting to see if upgrading on a regular basis (to each new final ubuntu version when available) is at this point in time, reliable enough to use it that way...


Nope .. wait ... I haven't tired it yet on a drive with multiple installs. I did the upgrade by editing /sources.list/ on a machine with multiple installs and that worked but I hadn't tried the *upgrade* on multiples with the "live" iso yet. I have been busy  most of the night cleaning malware off windows machines and now I am in an overclocking session .. so I'll try to get to in in  a bit. :)



Regards..

---

### Post by craig10x on 2013-10-15
Ok....thought you had....no problem...let me know when you have a chance...;)
For me, it will definitely be no problem (for what i plan to do on friday (after the final 13.10 release) since i only have ubuntu and nothing else on my drive...so it should be there...
But i was curious so i will know in case i mention it in the future to anyone here....

---

### Post by ventrical on 2013-10-15
Ok... Bravo !! It worked:)

Here's what happened.

I loaded up the live USB session and then chose  Install to disk from the Unity Panel.

Ubiquity came up and I went through regular routine until I got to the disk partitioner  section. Of course I did not have the option to *upgrade* over an exisitng install because I have multiple installs.. ** HOWEVER ** I chose a partition under the <somthing else> option, marked it as root  *but did not format the partiton!!

  I clicked <continue> and the installer began to install.  The orange indicator bar moved right to the end with the accompanying message "Saving Installed Packages"  then .. wait .. wait ... and the install continues with "Removing conflicting operating system files".

 After the installation routine it came to the section "restoring previously installed packages" with an error pop-up box  advising me that I might have to manually install some applications after reboot.

Well .. here I am with all my files and bookmarks in firefox working. The only problem was the network would not start up so I went to revovery mode and I am writing from there atm .. about to reboot.

Thing is , the saucy  rolling  release is a system restoration release! This is an absolute bonus. I don't think all the bugs are worked out of it yet but it is still a feat by the devs to pull this one off.

So.. item by item:

If you have multiple installs and are upgrading from Saucy live USB...

Choose <something else>:
Choose partiton you want to upgrade:
Change and select  "/" without quotes.
Do not change size of partiton.
Do not format partition.

Summary: It appears that Ubiquity will upgrade an installation as if it were a single install on a mutiple install hdd as long as you do not format the partition and make sure to mark it as root.

Regards..

---

### Post by craig10x on 2013-10-15
Excellent!...i will have to save a link to your report...you outlined it beautifully....
Of course, for myself...its even easier since in my case i will get the automatic option right on the first screen (both options will appear: wipe out the old one and install the new...or upgrade)

It is interesting...the stuff you saw going on during the upgrade was what i recall seeing when mine was being done... i especially recall seeing at the end "restoring your previously installed packages"...
and for me, everything came through perfectly except for having to re-install Google Chrome and MS Core fonts)....a few system settings went back to default, but that was quickly corrected...

With a reliable upgrade method like this...it now makes it pretty easy to "roll with ubuntu" whether you want to "roll" with development or "roll" with the finals...:D

---

### Post by ventrical on 2013-10-16
Network is restored .. etc... :)

Regards..

edit ... There was a defunct btrfs partition that does not come up any more on my GRub list .. but I had seen it while upgrading  the install I was working with ..so I am just curious if  would upgrade a btrfs install also on a multi-partioned drive.

edit:

  Do not try this on a production machine. Attempting this proceedure will cause  unpredictable results. I was able to restore the lost btrfs partition (which was a 12.04 experiemental install) but GRub will not load it but does list it. Secondly, and earlier networked upgrade to 13.10 had reverted back to  12.10 QQ ? and the most recent upgrade that I did using "live" saucy iso has converted from ext4fs to btrfs!!

Regards..

---

