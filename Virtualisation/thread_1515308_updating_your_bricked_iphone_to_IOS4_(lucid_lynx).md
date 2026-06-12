---
title: "updating your bricked iphone to IOS4 (lucid lynx)"
date: 2010-06-22
forum: Virtualisation
---

### Post by revolverXD on 2010-06-22
well i tried to updated the IOS 4 yesterday and got it bricked twice 
so to save other cluless ppl like me the trouble of trying to fix that for 
6 hours i will just post what worked to me:

1.download VMplayer:[http://www.vmware.com/products/player/](http://www.vmware.com/products/player/) (fill in what they as k and they will send you the link)
2.find the file you downloaded and put it in the /desktop directory
3.open the command line and run the following command :

sudo sh VMware-Player-3.1.0-261024.i386.bundle

4.get yourself an iso of your windows of choice or cd if you have it
5.after VMplayer finished installing it will ask to setup a new machine 
follow the really easy and self explaining orders to create the machine(you might wana go to smoke or make a coffee cause the installation took very long for me at least)
6.once the windows is working download and install the latest itune
7.plug in your iphone and make it availbale for the VM by right-clicking at the icon at the right side of the VMplayer and connecting it 
8.the update process should start at that point

and btw the reason you need VMplayer and not VM virtualbox is cause itunes 9.2 dosent run in virtualbox and even if you update it with older version of itune you will be left with iphone in emergency call state because itunes older then 9.2 just wont activate the phone.

for comparison what i did was installing VM virtualbox->installing itune 9.0.3->running update->iphone keeps changing usb id->iphone ends up bricked(first time)->searching the net yeilded the fact that i need to setup a filter to the usbin virtual box-> i made a filter->iphone started the recovery mode and updated->iphone bricked(second time) cause only itunes 9.2 can activate it->i download VMplayer after i learned it could run itunes 9.2 easily-> installed windows 7->installed itunes->  pluged in iphone-> iphone activates.

at the last part i smoked already 11 cigarettes and was really pissed of on apple with all it closeness .

hope it will save some one else the trouble of piecing it all toghter.

---

### Post by Brock Samson on 2010-08-10
thanks man, you saved my bacon, I thought the missus was going to kill me after I told her I bricked it!!

Much Appreciated!:D

---

### Post by glomboi on 2010-12-03
VirtualBox does work!
See this tutorial:
[http://www.flyingpenguin.com/?p=5878](http://www.flyingpenguin.com/?p=5878)

However, this guy misses out adding the user to the "audio" group (see comments on tutorial page).

I am now happily running IOS 4 on my iphone 3GS!

---

