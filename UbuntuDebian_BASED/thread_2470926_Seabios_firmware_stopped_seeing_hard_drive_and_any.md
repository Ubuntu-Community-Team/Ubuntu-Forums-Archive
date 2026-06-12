---
title: "Seabios firmware stopped seeing hard drive and any other MMC devices. USB boot only."
date: 2022-01-16
forum: Ubuntu/Debian BASED
---

### Post by nzcxzz on 2022-01-16
A few days ago, I wasn't using my machine (Dell Chromebook, not new, we know each other well) at the moment but it was on, and it randomly shut off. Nothing happened (like impact or overheating) and it wasn't really even doing anything so I didn't notice. When I restarted I was devastated to see that the machine didn't see my internal hard drive OR my SD card (which I had been successfully using Tails from). My computer was kinda sorta bricked, I was stuck with a firmware that couldn't even recognize my devices. Or rather, it's Seabios that can't see them (idk much about it, just enough to get through.. probably why I'm here), which I installed using Mrchromebox (shout out! super helpful!).

Then I remembered a USB key with a Kali install that I had. (and I also remembered that the internal hard drive and the SD card are both MMC devices). Kali live booted! Hallelujah! The other drives are there, totally fine, I can see all my data! I know correlation does not mean causation, but maybe it only sees the Kali drive bc it's USB, and the issue is somehow with the firmware suddenly not seeing MMC devices? If so, why would it do that? How would it just "stop noticing" MMCs? When I boot, I see the idiot bright chrome screen, Ctrl+L to get to Seabios Mrchcromebox screen where it stops. No devices found. If the Kali disk is in, it immediately jumps from there to the unetbootin screen for Kali.

My knowledge of firmware, bios, etc is limited, although I am a seasoned Linux user in general. Not of the highest order tho idk.. I wasn't sure where exactly to post this bc I'm not sure what the problem even is. I really hope it's one of those very obvious fixes, a 'duh' moment. Thanks in advance for any help. I'm very desperate to get this machine back in order. I need it for work and I my only other device is my phone..

---

### Post by bobunderwood99 on 2022-01-17
Hello,

I suggest you post on MrChromebox's github:

[https://github.com/MrChromebox/firmware/issues](https://github.com/MrChromebox/firmware/issues)

---

### Post by nzcxzz on 2022-01-17
Thanks. I actually messaged him directly on reddit. He's was completely condescending and unwilling to help. Seemed like he was mostly just interested in making me look dumb... Too bad since he wrote that firmware upgrade thing that's super helpful :/

---

### Post by bobunderwood99 on 2022-01-17
Will it boot into Chrome OS?

---

### Post by nzcxzz on 2022-01-18
No I wiped chromeos a long time ago. I'm not interested in using it. Literally any other os is better imo

---

### Post by howefield on 2022-01-18
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

