---
title: "vst plugins"
date: 2010-05-07
forum: Ubuntu Studio
---

### Post by marco casto on 2010-05-07
Hello,
I installed vst plugins to use with Rosegarden. dssi-vst is installed, the plugins show up in the plugins menu, but when I try to launch them, Rosegarden crashes. They all worked the first time I put the .dll files in Home/user/vst, but now there's no way to make them start.
Any idea?? 
thanks

Casto

---

### Post by c00kie55 on 2010-05-07
if they work with vsthost /path to plugin/Plugin.dll
it should work but its a hit miss lots of vst's dont work or dont save state
also 64/32 bit seams to have a role to play here 

a good test plugin cut be [http://kunz.corrupt.ch/?Products:VST_TAL-Elek7ro](http://kunz.corrupt.ch/?Products:VST_TAL-Elek7ro)
its free and start in everything i have putted it in also it easy and fun to play with
i cant remember if it saves state 
i dont know if it true but you migth need dssi-32 bit if you are running Ubuntu 64 bit


i instaled dssi and lots of other good stuff from here (he is doing a real good job)
[https://launchpad.net/~falk-t-j/+archive/lucid/](https://launchpad.net/~falk-t-j/+archive/lucid/) 

anyway i like qtractor more as it got linux vst, windows vst (dssi vst) dssi and lv2 plugins

it might be better to run plugins outside qtractor or rosegarden be-course plug ins seams to make things unstable

anyway good luck

---

### Post by marco casto on 2010-05-08
QTractor looks like a good choice, I can make my vst's work on it! Not tested yet the audio and I need time to see how well it works.
Now, get used to it....after 2years on Rosegarden. 
thanks

---

### Post by marco casto on 2010-05-10
Qtractor wasn't very stable on my system, no way to set the grid in the clip edit, crashes sometimes. 
Finally I made Rosegarden to work with vst's by uninstalling dssi-vst. It semms that it isn't necessary anymore in Lucid and Rosegarden 10.xx.
Case resolved  -   :-({|=

---

