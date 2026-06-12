---
title: "Just put android on my HP Touchpad"
date: 2011-10-18
forum: The Cafe
---

### Post by u-noob-tu on 2011-10-18
i was getting impatient waiting for the final release of the Android port to the HP Touchpad, so i went ahead and installed the alpha. Went off without a hitch, and the first boot into android was faster than booting into webOS. The android version is only Gingerbread 2.3.7, but even so, it works great. it may be an alpha, but the CyanogenMod team is not far off from a final release. The only major bugs i encountered were the settings app would sometimes crash and the device would sometimes go to sleep and not wake up. Has anyone else tried this on their touchpad? Has it worked well for you?

---

### Post by IWantFroyo on 2011-10-18
I haven't tried it, but I've followed the TouchDroid team and silently cheered them on. I've considered installing the alpha, but never had the guts.

I also held off because of ICS. It's being released today at 10pm EST, so I'm just going to stick with webOS 3.4 right now, and wait for an Ice Cream Sandwich.

:popcorn:

---

### Post by IWantFroyo on 2011-10-19
I decided to try the Cyanogenmod Alpha 2 a day after updating to WebOS 3.4. The tablet is stuck on the HP screen. Because this is what it did while updating to 3.4, I'm going to give it about 20 minutes. If it doesn't work, I'm manually injecting ClockworkMod.

In other words, if you updated your WebOS, the Alpha might not be a good idea.

---

### Post by forrestcupp on 2011-10-19
Seeing how the name of this alpha is "Lower Your Expectations", I probably would wait. I was thinking about buying a Touchpad even at $250. But I might go for a Thrive.

---

### Post by IWantFroyo on 2011-10-19
Nevermind. I got it working. I had to take the ACMEInstaller script out of the folder, apparently. :roll:

---

### Post by IWantFroyo on 2011-10-19
> **forrestcupp said:**
> Seeing how the name of this alpha is "Lower Your Expectations", I probably would wait. I was thinking about buying a Touchpad even at $250. But I might go for a Thrive.

Cyanogenmod always overhypes how dangerous installing the alpha is. I suppose it is dangerous, but I've been installing development versions since the old Cyanogenmod 6 betas, and I've never had problems on my good old HTC Aria.

---

### Post by u-noob-tu on 2011-10-19
> **IWantFroyo said:**
> Cyanogenmod always overhypes how dangerous installing the alpha is. I suppose it is dangerous, but I've been installing development versions since the old Cyanogenmod 6 betas, and I've never had problems on my good old HTC Aria.
interesting, because i have had almost no issues whatsoever using Android on my touchpad, even though they clearly (and repeatedly) say its an alpha. Theres the odd application crash here and there, and a few compatibility issues with apps, but all in all, it works fantastically.

---

### Post by IWantFroyo on 2011-10-19
> **u-noob-tu said:**
> interesting, because i have had almost no issues whatsoever using Android on my touchpad, even though they clearly (and repeatedly) say its an alpha. Theres the odd application crash here and there, and a few compatibility issues with apps, but all in all, it works fantastically.

The development releases are actually very stable. I suppose it just depends what you're doing on it. For example, the youtube app has problems playing while the tablet is in portrait mode. Other than that, I really like it.

To be honest, I have to say I actually like WebOS more on the TouchPad than Android right now. I use my TouchPad to study Japanese, so I have my PDF reader with a textbook in it on one card, and the tracks from the cd in the music app. It's so much more convenient just keeping these open all the time and keeping an eye on them than doing it in Android.

Android is better for the occasional game and for when I feel like using an RSS reader (I'm too cheap to buy one of the WebOS ones).

All in all, I'm pretty satisfied with the alpha. I think WebOS will stay my main OS for right now, but that may change when ICS gets CM'd.

---

### Post by forrestcupp on 2011-10-20
> **IWantFroyo said:**
> 
To be honest, I have to say I actually like WebOS more on the TouchPad than Android right now.

From what I've heard, WebOS is actually about the best OS for tablets there is, especially after the latest update. It's the app situation that makes Android better, that and the fact that there won't be anymore hardware running it. ;)

I heard HP is going to try to still license it to 3rd party hardware vendors.

---

### Post by u-noob-tu on 2011-10-22
Just an update on how my android experience is going: ive updated to the newest alpha and the biggest improvement has been battery life, which was bad. I have found that a lot of apps from the market work pretty well, including firefox and an office suite. Youtube works great, and video and music playback is good as well, though it doesn't seem to be as loud as it would be in webos, oddly. I've even got a few decent games that look quite good (sometimes the resolution looks odd, but that's understandable). I haven't booted into webos in awhile, because android has worked so well.

---

### Post by markp1989 on 2011-10-22
I have android running on mine too :) I started with the "lower your expectations" release and upgraded to "don't link directly the the files". You gotta love these strange release names.

Over all I'm very happy with it, I haven't had any crashes or anything like that, on alpha 1 I had problems that if i plugged headphones I would get sound from both headphones and the speakers, but the alpha 2 seems to have fixed that. 

Its a shame with webos, I really liked the "card" method of task switching. but shortage of quality apps was a problem for me, not to mention initial release of webos was pretty slow for me, I read something about excess logging or something, I never really looked in to it properly.

I did buy the touchpad purely to put android on it, so it didn't get used very often till the alpha release of CM, as I already had my Asus Transformer set up to my liking. 

My sisters also been playing with it since the alpha release and now and is thinking of buying one, but getting them from 3rd parties looks expensive.

---

### Post by johnaaronrose on 2012-05-09
The instruction that I've seen for ICS onto a HP Touchpad all involve a Windows PC (from which to run novacom & ACME2). Has anyone done it using a Ubuntu PC? If so, what changes are needed from the Windows instructions?

---

### Post by u-noob-tu on 2012-05-09
> **johnaaronrose said:**
> The instruction that I've seen for ICS onto a HP Touchpad all involve a Windows PC (from which to run novacom & ACME2). Has anyone done it using a Ubuntu PC? If so, what changes are needed from the Windows instructions?
its pretty much the same in Ubuntu. just navigate to the directory which has ACME2 and type the command the instructions say to run (goes something like "novacom boot mem: << ACMEInstaller2"). Either Windows or Ubuntu, the command is the same. make sure you have all the files needed to install ICS on your touchpad before running the command (the .zip files, such GAPPS and update-CM9-something-something.zip)

---

### Post by Jolicoeur on 2012-07-18
I can't install novacom in which to put the ACMEInstaller2.  It there a trick to this?  Please help.  Unless I can do this there will be no Android on my pad.

> **u-noob-tu said:**
> its pretty much the same in Ubuntu. just navigate to the directory which has ACME2 and type the command the instructions say to run (goes something like "novacom boot mem: << ACMEInstaller2"). Either Windows or Ubuntu, the command is the same. make sure you have all the files needed to install ICS on your touchpad before running the command (the .zip files, such GAPPS and update-CM9-something-something.zip)

---

