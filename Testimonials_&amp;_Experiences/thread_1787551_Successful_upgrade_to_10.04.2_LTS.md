---
title: "Successful upgrade to 10.04.2 LTS"
date: 2011-06-21
forum: Testimonials &amp; Experiences
---

### Post by dethorpe on 2011-06-21
Just upgraded my server (32bit AMD Athalon XP, Radeon) and laptop (64bit Intel Core2 Duo, Nvidia Mobile 7950GTS) from 9.10 to 10.04.2 LTS, very successful
and an easy/pleasent experience.
 
A bit of tidying first up by removing anything i didn't use or need, clearing out caches and temp areas, shuting down servers (apache, MySql etc).
 
Full partition backups 1st with FSArchiver just in case :-)
 
Then hit the button !
 
Only a few small hicups.
 
On server mediatomb stopped working as was referencing old MySQL v5.0 lib. MySQL had been upgraded to v5.1, but wasn't convinced it was OK as had originally installed that from downloaded package not repository. So uninstalled and re-installed it from repository. Then as i'd originally build Mediatomb from source myself just saved config, removed it and then re-installed from repository instead, restored the config and reloaded library and worked fine. Everything else running on it was OK, Apache2, TeamSpeak2, RSync, CVS, Funambol SyncML server, SSH, Samba, Synergy, VNC.
 
On Laptop, the upgrade to thunderbird 3 lost the lightning extension so had to re-install that, the Funumbol plug-in was incompatible with v3, so removed that and installed the correct version for TBv3 (even though beta, development code as not yet offically supported) which worked fine. Synced up to my Funambol SyncML server no problems. 
 
All in all, a pleasent experience, well done Ubuntu. :p

---

### Post by mastablasta on 2011-06-21
how is such a server handling your tasks? is it fast? what do you use it for?

---

### Post by wolfen69 on 2011-06-21
You rolled the dice and won!!! Ding Ding Ding, Bells and whistles!!!
[IMG]http://3.bp.blogspot.com/-1eVRBjByINM/Tasekv5KcmI/AAAAAAAAE5A/z43mTj4WILk/s1600/winner.jpg[/IMG]
You're braver than I am by "upgrading". Only clean installs for me. But anyway, glad to hear it worked out for you.

---

### Post by Tamlynmac on 2011-06-21
Always good to hear from a satisfied user. I must agree with wolfen69, it's best to do a clean install - but glad it worked for you.

10.04 is an awesome platform, I'm still using it with zero problems. Hope you continue enjoying the experience.

Good Luck

---

### Post by Bucky Ball on 2011-06-21
> **wolfen69 said:**
> 
You're braver than I am by "upgrading". Only clean installs for me. But anyway, glad to hear it worked out for you.

No bravery involved. I've upgraded four machines like this and every one has been great and (99%) problem free (latest being my mother-in-law's machine yesterday). Better, in some ways, than a clean install because you don't then have to spend time tweaking to get settings the way you like them/had them in the last install. You also don't need to get a million updates/upgrades when you finish installing from CD.

Safest with an ethernet cable but have done it with solid wireless connection also. ;)

ps: and yea, 10.04 LTS rocks ...

---

### Post by dethorpe on 2011-06-22
Yup, Don't know if i'm lucky or just carefully enough but upgrades have always worked for me. From 8.04 upwards. Saves all that tedious reinstalling and setingup applications :)
 
_Mastablaster to answer your question:_
 
Server is an old windows PC I upgraded, installed Ubuntu on, stuck big disk in and use as a home server. 
 
Runs mediatomb for streaming to PS3 and TV. Acts as backup and file server for my laptop and other family PC's via rsync and Samba shares. 
 
I use it as development/test machine hence Apache2, MySQL, CVS, SSH to run website i operate for dev/test. (develop/test on laptop then deploy on server) 
 
Runs Funambol SyncML server to sync contacts & calander between laptop and phone (N95), and act as backup for contacts. 
 
Fast Enough for all that, but don't generally have it all going at once. Although would propably struggle if I got into HD video streaming, currently just audio, images and Low Def home movie video.

---

### Post by mastablasta on 2011-06-22
cool. when i have money i plan to do something similar minus the website (as i pay for hosting). but i dont' know when that will be :-P
 
still i was thinking to do it with my computer which is similar to yours. that's why i was aksing... at the moment i have it also to backup files from arround network and to play some videos via DVI/HDMI to TV. it can handle HD videos well. but was htinkign if i used it for some other stuff and as server. only i would need money then for a new desktop maschine and also UPS would be cool to have.

---

