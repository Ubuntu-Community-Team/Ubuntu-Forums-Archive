---
title: "Meizu Pro 5 low and poor sound with headphones"
date: 2016-08-26
forum: Ubuntu Phone and Tablet
---

### Post by mily2 on 2016-08-26
Hi Community,

The sound with headphones is too low compared with others phones (Nokia high end). I tried to use alsamixer command; but not works: "cannot load mixer controls: Operation not permitted".
How I can turn up the sound level?

The sound quality, with headphones, is very average. It is supposed to take the best sound of market. [http://www.meizu.com/en/products/pro5/hifi.html](http://www.meizu.com/en/products/pro5/hifi.html)
[http://headphoniaks.com/blog/smartphone-iphone-6s-htc-10-meizu-pro5/](http://headphoniaks.com/blog/smartphone-iphone-6s-htc-10-meizu-pro5/)
[http://www.gsmarena.com/meizu_pro_5-review-1336p6.php](http://www.gsmarena.com/meizu_pro_5-review-1336p6.php)

Is this a bug? I suspect that ESS Technology es9018k2m DAC and Texas  Instruments OPA1612 op-amp are disabled, using only the Wolfson WM8998 audio  codec IC. 
[http://www.anandtech.com/show/10402/the-meizu-pro-5-review/7](http://www.anandtech.com/show/10402/the-meizu-pro-5-review/7)

---

### Post by dumazdamaz on 2016-09-09
only the wolfson card? really? the MX4 was marketed as having a 4K video camera. A year after its release it still does not do 4k and the bug is marked as "low prioirity". Newsflash:it never will and "only wolfson audio card" is 10x lower priority for Ubuntu developers. Are you an audiofile or something, because listen to what a2dp audio sounds on ubuntu touch and compare it to Android. Only some one that is deaf could not notive how bad the quality is. You need to stop complaining or read one of the threads on how to install android or flyme on your device.

---

### Post by krusty8 on 2016-09-10
Is there a launchpad bugreport for this?

---

### Post by mily2 on 2016-09-11
Dumazamaz, not only, obviously. I reported and confirmed some bugs in lauchpad for turbo. I know there are too many bugs for developers number, and their time is very limited. About 4K bug (is marked as "medium priority" [https://bugs.launchpad.net/canonical-devices-system-image/+bug/1471666](https://bugs.launchpad.net/canonical-devices-system-image/+bug/1471666)): I understand your comment, but I prefer infinitely ESS Technology es9018k2m DAC and Texas  Instruments OPA1612 op-amp enabled. I don't have 4k display or intention to buy it. About Android: I prefer UT with bugs; although I do not rule out the use dual boot UT - Flyme in the future, if necessary to use these components or other functionalities that could not be implemented, despite the admirable efforts of the UT Developer Team. I don't need to stop complaining, we need UT evolves and bugs are corrected; if the problems are not listed, How will they be solved? 

> **krusty8 said:**
> Is there a launchpad bugreport for this? There is this bugreport: [https://bugs.launchpad.net/canonical-devices-system-image/+bug/1594024](https://bugs.launchpad.net/canonical-devices-system-image/+bug/1594024).

---

### Post by krusty8 on 2016-09-12
> **mily2 said:**
> I tried to use alsamixer command; but not works: "cannot load mixer controls: Operation not permitted".


Did you try with sudo? On the N7, though I am able to change controls with alsamixer/amixer without sudo.

You could also try pulse audio. I think pacmd or pactl or something like that. Have no personal experience with that, but it was mentioned in some bug reports.

Or maybe you can extract something from here: 
https://lists.launchpad.net/ubuntu-phone/msg03881.html

---

### Post by mily2 on 2016-09-13
Thanks Krusty8.

Yes, I tried with sudo: reports: "cannot load mixer controls: Operation not permitted". Can you use almixer gui in N7?
I will tray level sound up with amixer and pulse audio.

Interesting link.

---

### Post by krusty8 on 2016-09-14
> **mily2 said:**
> Thanks Krusty8.

Yes, I tried with sudo: reports: "cannot load mixer controls: Operation not permitted". Can you use almixer gui in N7?.

So, just to be clear. I guess almixer is a typo, I dont know of a tool of that name. What I used is alsamixer, which well I guess you can call it GUI, but there is no X involved, right? Its just uhm "console graphics". You can move left,right between controls and up,down to change them. I used that successfully. There's many many controls though. So I figured two out that affect the volume of the speakers and use these in a script with amixer. Something like this:


```

$ amixer | grep -A 5 "RX[34] Digi"
Simple mixer control 'RX3 Digital',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 124
  Mono: 84 [68%] [0.84dB]
--
Simple mixer control 'RX4 Digital',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 124
  Mono: 84 [68%] [0.84dB]

amixer set "RX4 Digital" 90
amixer set "RX3 Digital" 90

```

I don't dare to go higher because the sound gets distorted and Im afraid it might damage the hardware.

---

### Post by dumazdamaz on 2016-09-14
> **mily2 said:**
> Dumazamaz, not only, obviously. I reported and confirmed some bugs in lauchpad for turbo. I know there are too many bugs for developers number, and their time is very limited. About 4K bug (is marked as "medium priority" [https://bugs.launchpad.net/canonical-devices-system-image/+bug/1471666](https://bugs.launchpad.net/canonical-devices-system-image/+bug/1471666)): I understand your comment, but I prefer infinitely ESS Technology es9018k2m DAC and Texas  Instruments OPA1612 op-amp enabled. I don't have 4k display or intention to buy it. About Android: I prefer UT with bugs; although I do not rule out the use dual boot UT - Flyme in the future, if necessary to use these components or other functionalities that could not be implemented, despite the admirable efforts of the UT Developer Team. I don't need to stop complaining, we need UT evolves and bugs are corrected; if the problems are not listed, How will they be solved? 

 There is this bugreport: [https://bugs.launchpad.net/canonical-devices-system-image/+bug/1594024](https://bugs.launchpad.net/canonical-devices-system-image/+bug/1594024).


I didn't bring up the 4k issue because I want to use it. I also do not have a 4k display. I brought it up because it was a big selling point of the MX4 ubuntu edition and the bug was reported right away. Yet, it has not been fixed even though the bug was confirmed a year a go. There are other worse complaints, like that simple menus and programs take several seconds to open even though the MX4 was at it's release the fastest phone out there. On Android stuff like that just does not happen. Another selling point was convergence, but now it looks like Canonical are not going to support it at all on the MX4! The camera and media hub crash every now and then. The calendar puts events in wrong places. Making video calls is impossible, sharing photos and other stuff with other people is hard because the only app that others have and you have is email, but the email client is buggy etc. etc. I realistically don't think that this issue that you report will be fixed ever. If it will be fixed, it will be years from now. If you look on the internet you will find long threads where many many people are flashing android on these phones. Users are running away. These forums get 3 posts on average/week. It was a nice idea to have an alternative OS and we should be happy that the developers are doing what they are doing, but I fear this project is not going to survive. Developers don't want to develop for Touch since you need to rewrite everything and there are 3 users...

---

### Post by mily2 on 2016-09-14
OK. Thanks Krusty8. I was referring to this: [https://duckduckgo.com/?q=alsamixer+gui&t=canonical&iax=1&ia=images&iai=http%3A%2F%2Fi.stack.imgur.com%2FrxKMa.png](https://duckduckgo.com/?q=alsamixer+gui&t=canonical&iax=1&ia=images&iai=http%3A%2F%2Fi.stack.imgur.com%2FrxKMa.png)

Dumazdamaz, true. Some times I ask me how many users are with Meizu Pro 5 (counting developers), 500, 600?. But I think that here would be many more if Meizu had spare the stock; I myself had bought another. Although my complaints might seem otherwise, I am generally happy with the OS; if UT had Firefox, SMPlayer, Google Earth and continue with current developments, is great for me. We have OTAs frequently, with many bugs fixed (the work of Developer Team is laudable). We must not lose hope.

---

