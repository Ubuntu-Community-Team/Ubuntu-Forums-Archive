---
title: "used wine screwed up my computer can someone help?"
date: 2009-05-25
forum: Wine
---

### Post by jcm1107 on 2009-05-25
Hi I used wine to try and run a game and I think it is what screwed everything up. Well not that bad but no sound now and when I ran that game with dosbox I got a wine error message just one time but that is enuff to show me that wine is running when it is not supposed to be. I tried removing the wine package in synaptic but there is still a wine folder under applications and I still have no sound in that game with dosbox. Please help I don't want to have to log into windows to play that game and I would like to learn to use wine better so I don't ever have to log into windows. I am using Ubuntu 8.04 hardy. Thanks!!

---

### Post by Duskao on 2009-05-26
It's hard to help you out right now cause your being very vague. What was the game, what was the error. What version of wine. We need to know all this to be able to help you out a bit more I think.

---

### Post by hikaricore on 2009-05-26
There's nothing that WINE could have done to affect your sound systemwide.  Nothing.

---

### Post by jcm1107 on 2009-05-26
I forget what the error was I only got it once and I thought I could reinstall whine or go into dosbox and fix it. But that didn't work. I have tried more than one version of wine also so I can't give that either but I have wine removed right now sort of (there is still a folder that says wine under aplications) and still have no sound with the game in dosbox. The game was working with all sounds I really don't know the exact cause of my problem I need someone to help point me in the right direction.

---

### Post by jcm1107 on 2009-05-26
> **hikaricore said:**
> There's nothing that WINE could have done to affect your sound systemwide.  Nothing.

Mabe it was something else I did then. I need someone to point me in the right direction.

---

### Post by rCXer on 2009-05-26
Does the sound work in other applications?  Are you sure the volume isn't muted?

---

### Post by Duskao on 2009-05-26
rCXer, thats what I was going to say. That actually happened to me today. It was the oddest thing. I started watching a movie on my computer (legend of drunken master {classic :D}) and when it started up all my sound was at lowest but everything was turned up to my knowlege. So I checked out volume control and voiala I had to turn up master front, but front was all the way up. Hmmm. odd eh.

---

### Post by jcm1107 on 2009-05-26
> **rCXer said:**
> Does the sound work in other applications?  Are you sure the volume isn't muted?

yes the sound works in rythmbox but I have had unknown errors with it also lately but just close it and it usually works or that didn't work one time and I ended every process that was music related and restarted the computer and it is working now.

---

### Post by jnewl on 2009-05-26
I have problems with pulseaudio when running Windows games. Since you say your sound came back after you rebooted, I suspect that's the culprit here.

In order to get sound in some games, you may have to kill pulseaudio. To do that, first go uncheck the Pulseaudio Session Manager box in System->Preferences->Sessions (otherwise it keeps loading itself back up), and then kill the pulseaudio process in System Monitor. 

After you're done playing, you may or may not have sound in Ubuntu. If not, you can either try to reload pulseaudio manually (I have trouble getting it to load properly, but I've never tried all that hard, either) or just do a quick reboot. One thing I just thought of but have never tried: try rechecking the Session Manager Box and let the system reload it for you.

---

### Post by jcm1107 on 2009-05-26
> **jnewl said:**
> I have problems with pulseaudio when running Windows games. Since you say your sound came back after you rebooted, I suspect that's the culprit here.

In order to get sound in some games, you may have to kill pulseaudio. To do that, first go uncheck the Pulseaudio Session Manager box in System->Preferences->Sessions (otherwise it keeps loading itself back up), and then kill the pulseaudio process in System Monitor. 

After you're done playing, you may or may not have sound in Ubuntu. If not, you can either try to reload pulseaudio manually (I have trouble getting it to load properly, but I've never tried all that hard, either) or just do a quick reboot. One thing I just thought of but have never tried: try rechecking the Session Manager Box and let the system reload it for you.

I just tried unchecking pulseaudio and it didn't help, thanks though! I am glad you tried to help!

---

### Post by jcm1107 on 2009-05-27
> **Duskao said:**
> rCXer, thats what I was going to say. That actually happened to me today. It was the oddest thing. I started watching a movie on my computer (legend of drunken master {classic :D}) and when it started up all my sound was at lowest but everything was turned up to my knowlege. So I checked out volume control and voiala I had to turn up master front, but front was all the way up. Hmmm. odd eh.

THANKS!!!!!!!!!!! This fixed my problem!!!! I checked my volume and thought it was up because I have a icon in the panel for volume and it was up, but that was if I left clicked on it. Just now I right clicked on it and everything except one was at the lowest setting. I don't know how it changed itself because I know I didn't change it but it's fixed now so I am happy. I now have sound in my game. Thank you!!!

---

### Post by adamericmurray on 2011-01-29
I cant type and menu bars are invisible and my close bar is missing I am using a eeepc  help!!:sad::sad:

---

### Post by lisati on 2011-02-01
> **adamericmurray said:**
> I cant type and menu bars are invisible and my close bar is missing I am using a eeepc  help!!:sad::sad:

Please start a new thread.

---

