---
title: "how to finally 100% get flash to not crash in 11.04"
date: 2011-09-26
forum: Tutorials
---

### Post by txlaw on 2011-09-26
I installed from a DVD  11.04 and had every single issue with flash you can imagine. 
ubuntu was fine, I love 11.04, i love the new Libre office vs open office, i liked banshee vs rhythm box, i liked it all...  it was just the POS Adobe Flash. 

Once i would do one fix flash would crash for some other reason. So i finally got the stupid awful POS flash to finally 100% work.  I am writing this short how-to because it took me hours searching google and this forum to get all the fixes working. they are not all listed in the same place.  Here were all the fixs i had to do.


this is for the newest flash - flash 10 - from adobe 
1.  flash seems to crash for lots of people, me included if it is not in 24 bit color. The answer is to edit your xorg.conf file.. WHICH IS NOT IN 11.04! you have to create one. I just copied one off google and used text edit and saved it in the proper /etc folder.  you can google how to create an xorg.conf with the instructions on making it 24 bit where to save it, etc. 
2.  Adobe's own website says that flash 10 has issues with pulseaudio. pulseaudio crashed all the time for me when i was using flash. I used  sudo apt-get purge pulseaudio  and then used sudo apt-get alsa*    I am sure that is not the proper way to do that but it fixed that issue. THIS WAS A BIG ISSUE WITH MY LAPTOP it took me a few crashes to figure out that pulseaudio was crashing and not firefox or flash.  
3.  Also make sure to install the Fire fox plugin called "flash aid"  google it. flash aid really makes adobe flash  85% less buggy and crappy. 
4. also make sure you have the libflashsupport which does help but remember as i learned the hard way libflashsupport does not work with pulseaudio!  

in conclusion it seems to me, a non computer person who has been using linux since redhat 5  that you have to deal with the fact as adobe admits that flash is meant to be seen in 32 bit color (24 bit) and that it as adobe says version 10 does not work with pulseaudio. 

I now have flash working 100% as well as mac os x, my droid phone, and even XP. 

I hope this helps.

jason

---

### Post by hubertofliege on 2012-04-30
Thank you so much.

---

