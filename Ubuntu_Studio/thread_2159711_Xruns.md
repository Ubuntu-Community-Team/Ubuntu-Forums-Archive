---
title: "Xruns"
date: 2013-07-04
forum: Ubuntu Studio
---

### Post by Almuzura on 2013-07-04
Hello everybody! I'm an Ubuntu newbie.

I shifted from Windows to Ubuntu 12.04 (64 bit) six months ago. Now I've just upgraded my system to Ubuntu Studio following the Selective Upgrade guide ([https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu#Selective_Upgrade](https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu#Selective_Upgrade)).

Everything went well until I tried to install the Real Time Kernel as instructed in the previously mentioned guide. I got an issue when executing the command: 
[B]
sudo apt-get install linux-rt linux-headers-rt
[/B]
I got the following message:

```
sudo apt-get install linux-rt linux-headers-rt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-rt
E: Unable to locate package linux-headers-rt

```
I decided to give a try to my new system anyway. I connected my Alesis io2 interface, launched Jack and Ardour, and tried to record some stuff. I got horrible cracks while recording a new track and when playing it back. I tried to change various parameters in Jack (frames/period, sample rate, periods/buffer etc.) without any results.

Do you think the cracks depends on the lack of a real time kernel? Are those cracks caused by xruns? How can I install a real time kernel?

Thank you very much for your patience and kind support.

---

### Post by jejeman on 2013-07-04
There is no RT kernel in 12.04. Use lowlatency instead.
Something like
```
sudo apt-get install linux-lowlatency
```
etc.

Hard to say. Check your CPU speed is on performance.

---

### Post by luctor on 2013-07-04
ubuntu(studio) 12.04 doesn't have any linux-rt
I advise you to give the packages from kx-studio a try ([http://kxstudio.sourceforge.net/](http://kxstudio.sourceforge.net/)), I've got very good results with it.
Read on how to upgrading here [http://kxstudio.sourceforge.net/Documentation:Ubuntu:Upgrade](http://kxstudio.sourceforge.net/Documentation:Ubuntu:Upgrade)
I  didn't install the full desktop package , just the low-latency kernel and the apps I needed

---

### Post by Almuzura on 2013-07-05
Thank you, Jejeman!
It worked. Now I can set latency as low as 10 ms without getting cracks.

Thank you, Luctor, too.
I will browse that page on KXStudio anyway; I might find something helpful!

Bye!

---

### Post by Almuzura on 2013-07-07
Hello everybody,

the problem with xruns appeared again.

Maybe it's due to the fact that I have reached a certain number of tracks and the system resources are insufficient?

---

### Post by CraigPid on 2013-07-09
Just raise your latency if it's getting too much for the system.Unless you're doing midi recording or you are monitoring your instrument through the system rather that an amp or something then you're better off with a higher latency to give the system more time to process the audio data.

---

### Post by Almuzura on 2013-07-12
Thank you, CraigPid.
That's what I actually did. The point is that I have to raise the latency up to 40ms or more to avoid or at least lessen the chances to get xruns. But 40ms it's not tolerable. In the end I had to temporarily move the tracks that I had recorded, which is also a non ideal situation. Do you think that the audio interface is also responsible for latency issues or it all depends on the computer? I'm using an Alesis io2. Maybe I just need to upgrade my system.

---

### Post by CraigPid on 2013-07-12
40 ms would really suck. I'm not familiar with that audio interface but a lot of factors in the system can contribute to latency. That said ... if the system is set up properly there shouldn't really be a problem even on an older system. Do you have other programs or services running that are using cpu cycles? You said you upgraded from 12.04 to Ubuntu Studio. Did you try doing a clean install of Ubuntu Studio and disable the startup services that you don't need. If you have compositing disabled that makes a big difference.

---

### Post by su:bhatta on 2013-07-15
CraigPid, Thanks for the suggestion of 'disabling compositing' ... helped me a little...

---

### Post by Almuzura on 2013-07-16
No, I don't have any other program running apart from Ardour. How can I disable compositing? I wanna try this. If it doesn't work, I'll try a clean install of Ubuntu Studio. Thank you anyway for your priceless suggestions!

---

### Post by su:bhatta on 2013-07-16
You are using Ubuntu 12.04 with Unity or Xfce?

Did you install Xfce in that selective Upgrade? 

If yes, then go to Settings Manager--> Window Manager Tweaks--> Compositor(Last Tab) & deselect 'Enable Compositing'

---

### Post by su:bhatta on 2013-07-16
Also, I suggest you stop these applications from loading on StartUP:
1) Blue Tooth Manager (if any, & provided you dont use it often)
2) ScreenSaver
3) Zeitgeist Datahub

Go to, Settings--> Session & StartUP--> Application Autostart Tab and deselect these or any other autostart that you may have added but you do not require.
 It all adds to the system load...

In case you are logging in with Unity DE, then try using Xfce, which is what Ubuntu Studio comes with, 
Because Xfce is Medium weight DE which does not use as much system resources as Unity.

Edit: WOW! Just read through that 'selective upgrade guide' & they dont even talk about Xfce ! Thats strange...
I believe you will be better off with  a clean Ubuntu Studio 12.04.2/13.04 installation...
(Ubuntu Studio 12.04 had some issues with jack and all i read, but i believe most of it has been sorted out now, i shouldn't comment, i use 13.04)

---

