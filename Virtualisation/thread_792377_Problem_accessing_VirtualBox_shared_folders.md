---
title: "Problem accessing VirtualBox shared folders"
date: 2008-05-12
forum: Virtualisation
---

### Post by exactopposite on 2008-05-12
I installed VirtualBox OSE today for the first time. I'm using it to run xp in ubuntu. In VirtualBox i set some folders in ubuntu to be shared. I used the "map network drive" funtion in windows to map those shared folders. I was able to access them and use files from them with no problem. Then I went to access one of the shares and the display went haywire. After that, now every time I try to access  either of my shared folders I get the same problem. Here is a screenshot of what it looks like:

[http://i30.tinypic.com/xat2j9.png](http://i30.tinypic.com/xat2j9.png)

I tried removing the ose version and intalling the version from the virtualbox gutsy repo (even tho i'm using hardy), and it was the same thing, it worked for a while but I started getting that garbled screen. I have tried removing virtualbox and all it's settings including the virtual hard drive, but when I reinstall virtualbox and the guest OS it'll work for a period of time, but then i get that screen again. I have installed virtualbox 4-5 times today trying the non-free and ose versions. 

It seems pretty straight forward to use, but maybe I'm doing something wrong here. Any ideas?

My machine is a dell vostro 1400 (laptop) with a 2Ghz core2duo, 2 gigs of ram, intel x3100 graphics, and 160 gig hd. Running hardy 32.

---

### Post by heatpumpcontrol on 2008-05-12
It seems like you're having video driver issues. You might have too much video memory dedicated to the vm. Try reducing the the amount of shared video mem under the settings and try it again.

---

### Post by exactopposite on 2008-05-13
> **heatpumpcontrol said:**
> It seems like you're having video driver issues. You might have too much video memory dedicated to the vm. Try reducing the the amount of shared video mem under the settings and try it again.

It's only got 8 megs dedicated to it (that was the default). Could that really be too much? I tried increasing it to 32 before but it made no difference so I put it back to the default. Since I hadn't used it before I used the defaults for everything in an attempt to avoid conflicts.

---

### Post by heatpumpcontrol on 2008-05-13
open up the vm and hit the "machine" menu and insert cnt-alt-del to bring up the task manager. Look at the processes and keep an eye on the cpu usage when you attempt to access the shared folders. If it's spiking then maybe you might need to increase your video memory for the vm machine... 

Odd thing though is that I would just expect the vm machine to be unresponsive and not affect the host machine... ubuntu but hey it's worth a try.

let me know. I'm up and I'll keep an eye for your post

---

### Post by exactopposite on 2008-05-13
> **heatpumpcontrol said:**
> open up the vm and hit the "machine" menu and insert cnt-alt-del to bring up the task manager. Look at the processes and keep an eye on the cpu usage when you attempt to access the shared folders. If it's spiking then maybe you might need to increase your video memory for the vm machine... 

Odd thing though is that I would just expect the vm machine to be unresponsive and not affect the host machine... ubuntu but hey it's worth a try.

let me know. I'm up and I'll keep an eye for your post

It doesn't bother ubuntu. The host OS is fine, but the guest freezes and gives me that screen.

I'll try watching for cpu usage and tweaking the video ram 2moro. it's too late to bother with it for 2nite.

---

### Post by heatpumpcontrol on 2008-05-13
Oh OK, this morning I was reviewing your picture and I see that the vm window (guest OS xp) is the one that is the only one failing. I also noticed that you have a 800MHZ processor. Now is that being scaled back? You mention that you have a 2Ghz core2duo, 2 gigs of ram, intel x3100 graphics. It seems like to me, that you are having a lack of power/memory from either the processor or from the video. 

Try reinstalling the guest additions to make sure that correct video drivers are being used. Try this first. If this doesn't work then try making the ram and video memory adjustments. If this doesn't work then disable your laptop's processor scaling which may be under power savings and tell it not to use processor scaling so that it can run at full cpu.

Try it out and post your findings.

---

### Post by exactopposite on 2008-05-14
> **heatpumpcontrol said:**
> Oh OK, this morning I was reviewing your picture and I see that the vm window (guest OS xp) is the one that is the only one failing. I also noticed that you have a 800MHZ processor. Now is that being scaled back? You mention that you have a 2Ghz core2duo, 2 gigs of ram, intel x3100 graphics. It seems like to me, that you are having a lack of power/memory from either the processor or from the video. 

Try reinstalling the guest additions to make sure that correct video drivers are being used. Try this first. If this doesn't work then try making the ram and video memory adjustments. If this doesn't work then disable your laptop's processor scaling which may be under power savings and tell it not to use processor scaling so that it can run at full cpu.

Try it out and post your findings.

The cpu will scale back to 800mhz, but whenever I start dowing something in virtualbox it jumps back up to 2ghz. I uninstalled virtualbox and wiped out the .Virtualbox folder. I'm installing it all again right now. If i have the same problem i'll try tweaking the memory settings. If i need to turn the cpu scaling off to make it work, I just won't use virtualbox at all.

---

### Post by dRock1286 on 2008-05-14
Is the one in the Gutsy repos v1.6?

---

### Post by exactopposite on 2008-05-14
> **dRock1286 said:**
> Is the one in the Gutsy repos v1.6?
I was using the one in the gutsy repo, but I noticed after my last reply that there is a newer version availible from the sun website. I installed that one and it seems to be working much better now. I'll use it for a while to make sure it continues to work properly.

this is where i got the latest version:
[http://www.sun.com/download/index.jsp?cat=Operating%20Systems&tab=3&subcat=Virtualization](http://www.sun.com/download/index.jsp?cat=Operating%20Systems&tab=3&subcat=Virtualization)

---

