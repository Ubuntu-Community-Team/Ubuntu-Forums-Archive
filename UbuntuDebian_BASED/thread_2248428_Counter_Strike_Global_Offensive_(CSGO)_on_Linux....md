---
title: "Counter Strike Global Offensive (CSGO) on Linux..."
date: 2014-10-14
forum: Ubuntu/Debian BASED
---

### Post by jlassesen on 2014-10-14
Hi.

 Fairly new to the Linux world. I the sence, i have a buddy who has been around it for along time, but i can't rely on his help 24/7... And he's no gamer like i am... I've been on and off the wagon several times through out the years, but it never really took due to two main reasons. 1 - Bloody, if not impossible to get games working even fairly well through Wine (All there were last i were around, a couple years back) - And 2 - Constant hardcore OS crashes, that required a reinstall... Took to long to constantly reinstall, and i am far from a patient man in that reguard... I need my games to keep me calm and focused...

So... I turn to the community for answers and help, and hopefully help others in the process... - I know, if i can get a working Linux running with CS:GO, that performs better than anything i've seen so far on a windows platform, i can get more people onboard the Linux wagon...

 Now... There's several aspects to it, where most are obvious, for obvious reasons... Graphics... Mainly high FPS (Frames Per Second) are required... But also proper mouse handling, which incl. (At least for CSGO) disabling the mouse acceleration, and being able to set DPI on the mouse... (Not just the cursor speed under mouse settings, which has no effect in the applications... Games)...

 I've been trying to read up and learn alot over the past days, but it seems like i either end up not "getting it" because im a newbie at the Linux world... My knowledge is still only fair at best... And most things i need to know about, just aren't "out there" on the web...

 But also sound... I know there's good sound on Linux for medias... Music and movies... But alas... No real way to tweak, or improve it for gaming purposes... How come ?

 So yea... My question (s) are well, how do i best setup my OS for CSGO, would it be prudent to learn more about streamlining my kernel for it ? (With a high risc of having to reinstall my OS over and over) - How do i choose the right driver for a performance gaming computer, in reguards to graphics and sound ? - And last but not least... How do i "tweak" my mouse, so acceleration is disabled, and DPI is set the way i need it to be ?

 Reguarding mouse acceleration, i've read [https://wiki.archlinux.org/index.php/Mouse_acceleration](https://wiki.archlinux.org/index.php/Mouse_acceleration) - But for a newb, all this about X-this and X-that put me hanging with more questions than answers...

 Anyone ever considdered maybe making more step by step guides for utter newbs and retards like me ? - Especially in reguards to gaming ?

 Oh right... My own computer...

 Well its a couple years old, running an i7, 16 gigs memory, Asus HD 5770 1 Gigz graphics, SSD harddrive (90 gigz), and a Creative sound card (Model name eludes me at present)... And my OS is Linux Zorin OS 8 Gaming...

 I know my post is abit "all over the place" but i feel like i been put back on the school bench and my head's hurting from all the learning... :P

---

### Post by kurja on 2014-10-15
So... if I understand correctly, you're a self-proclaimed 'linux newb' and want step by step instructions for making your own custom kernel with which you could run a game with better performance than what it has on the more gaming-friendly windows platform?

Should be easy :roll:

Running anything with wine always has a performance penalty and it's often rather severe.

As for mouse acceleration, afaik xinput set-prop <yourdevicenumber> 'Device Accel Profile' -1 should work?

---

### Post by coffeecat on 2014-10-15
Zorin, not Ubuntu.

*Thread moved to **Ubuntu/Debian BASED**.*

---

