---
title: "Sound Ati Realtek HD ALC 892 Front Jack."
date: 2012-02-04
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by bash321 on 2012-02-04
Hello, I am currently using ubuntu 12.04, because my headphone jack on the front panel of my AMD 955 GIGABYTE 880GM-USB3 Motherboard ALC892 Alsa sound driver that i am currently using, doesn't work on ubuntu with front panel of my machine.
It did work on windows 7. I have also checked my MB they are plugged in!
It has not worked on ubuntu since i installed 11.04. I was wondering if there was a way to fix this problem?
to get the headphone jack to work?
If i need to post any logs, it would be great if i had some instructions on knowing how.
I have also done some research on the internet but that has not helped. I also installed the driver from Realtek and that disabled sound on my whole system on ubuntu, so i reinstalled the alsa drivers, and my back panel is fully operational now with sound.
So what I Would like is also to have sound through the headphone jack on the front of my pc.
If my thread is in the wrong place, please put in the place where it could get fixed.

bash321.

---

### Post by effenberg0x0 on 2012-02-04
> **bash321 said:**
> Hello, I am currently using ubuntu 12.04, because my headphone jack on the front panel of my AMD 955 GIGABYTE 880GM-USB3 Motherboard ALC892 Alsa sound driver that i am currently using, doesn't work on ubuntu with front panel of my machine.
It did work on windows 7. I have also checked my MB they are plugged in!
It has not worked on ubuntu since i installed 11.04. I was wondering if there was a way to fix this problem?
to get the headphone jack to work?
If i need to post any logs, it would be great if i had some instructions on knowing how.
I have also done some research on the internet but that has not helped. I also installed the driver from Realtek and that disabled sound on my whole system on ubuntu, so i reinstalled the alsa drivers, and my back panel is fully operational now with sound.
So what I Would like is also to have sound through the headphone jack on the front of my pc.
If my thread is in the wrong place, please put in the place where it could get fixed.

bash321.


It was fixed a while ago. I know because I reported and tested for David Henningsson. The fix hasn't made it to kernel yet AFAIK, but if you follow the instruction on the Launchpad report and get the DKMS, it will work (worked for me in two different machines with this model, at least)

See here: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/871582](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/871582)

A tip: Make sure your front panel jacks and wiring are capable of auto-muting speakers. It requires special wiring that is not common in most PC Cases. See #[22]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/871582/comments/22") for example. I had to buy a better audio front panel in order to test this bug. But I remember finding schemes for correct wiring online back then (if you're into welding and electronics).

Regards,
Effenberg

EDIT: And thanks, I had totally forgot about this bug and to provide feedback to the developer. Just added it.

---

### Post by bash321 on 2012-02-05
hello effenberg,
I would just like to say it was wiring problem.
I just checked where the wires went for the front panel, and they were in the wrong place.
so...
Sound works now!!!! I did install your DKMS fix. I had that installed before I checked the wiring.
It should be in the kernel for future releases of ubuntu!
that works really well!!
its fantastic to have audio from the front of your computer.
Just a note to anybody, who has audio problems, always check that your sound connectors are in the right place of your motherboard! read the instructions from the motherboard manufacturer ( in my case Gigabyte)
thank you for resolving my situation and making me think twice!
bash321

---

### Post by effenberg0x0 on 2012-02-05
> **bash321 said:**
> hello effenberg,
I would just like to say it was wiring problem.
I just checked where the wires went for the front panel, and they were in the wrong place.
so...
Sound works now!!!! I did install your DKMS fix. I had that installed before I checked the wiring.
It should be in the kernel for future releases of ubuntu!
that works really well!!
its fantastic to have audio from the front of your computer.

That's great, I'm glad you got it working!
> **bash321 said:**
> 
Just a note to anybody, who has audio problems, always check that your  sound connectors are in the right place of your motherboard! read the  instructions from the motherboard manufacturer ( in my case Gigabyte)
thank you for resolving my situation and making me think twice!

bash321


These new motherboards have too many audio, video, data connections, embedded switches, a lot of new BIOS settings, etc. I never thought motherboard's manuals would get to have almost 60 pages. It's a geek paradise :) The bad side of it all is that I've been seeing commercial desktops that use them come from factory with wrong BIOS settings, wiring and connections, installed in inadequate cases, etc. It's really important that users read their manuals and check all this stuff. 

Regards,
Effenberg

---

