---
title: "How much power does your PC/ Server use?"
date: 2008-06-19
forum: The Cafe
---

### Post by Twizzle on 2008-06-19
I have just built my first home server with 8.04 server edition as my OS. The system is based on an Athlon XP 2400 underclocked to 1800Mhz, 1Gb RAM and 2 HDD. The mother board has onboard video and there are no other cards, accessories plugged in.

I am a bit worried about how much my bills will increase by leaving it running 24/7 so bought a power meter to test it.

Running idle, my server is using around 80 - 90 Watts. This to me seems loads for something that is pretty low powered.

Does any one else have any figures I can compare this to? Do you think my PSU needs replacing with a newer one that will be more efficient? (is that a possibility?)

Im interested to know other peoples views as at this level, I am tempted to unplug it as my bills will rocket!

---

### Post by drumsticks on 2008-06-19
Most generic desktops I've measured uses about 60-70W idle, so you're not that far off. My old PowerMac G5 dual cpu 2GHz used 130W idle, and 40W in the so-called "off" mode. A friend of mine has a Mac Pro octo core. That uses about 400W idle (insane!), and also 40W in the "off" mode. I've lost my respect for Apple's green-ness...

My Dell XPS M1530 laptop now uses about 20-30W plugged into the wall, and I couldn't be happier.

---

### Post by WiFi Ed on 2008-06-19
Not as much as Al Gore's apparently...

[http://www.cbsnews.com/stories/2007/02/28/politics/main2522844.shtml]("http://www.cbsnews.com/stories/2007/02/28/politics/main2522844.shtml")

"The Gores used about 191,000 kilowatt hours in 2006, according to bills reviewed by The Associated Press spanning the period from Feb. 3, 2006, to Jan. 5. That is far more than the typical Nashville household, which uses about 15,600 kilowatt-hours per year."

---

### Post by Tom Jaeger on 2008-06-20
You should probably be able to cut power consumption by 30-40W using athcool.

---

### Post by richardjennings on 2008-06-20
If you want low power consumption, buy an air cooled via mini itx board.

---

### Post by Twizzle on 2008-06-21
Well, I have changed my PSU from an old 450W to a Hiper 350W and that reduced idle consumption by around 10 - 15W, I then ran athcool and it instantly dropped to around 50W when idle!

Im very impressed with athcool - Thanks! (just need to figure out / ensure it runs everytime at boot)

Now I am going to see what effect under clocking it even more makes!

---

### Post by ghindo on 2008-06-21
How can you tell how much power you're using?  I just started running a 24/7 server and really want it to run cool

Under/overclocking is all done through the BIOS, right?

---

### Post by Twizzle on 2008-06-21
I bought one of [these]("http://www.maplin.co.uk/Module.aspx?ModuleNo=223573&C=Maplin&U=SearchTop&T=plugin%20power%20meter&doy=21m6") to measure my power use (also quite interesting to see what else round the house runs my bills up!)

Any yes the under / over clocking is done through the bios although I have not found it made as much difference as a better psu and athcool (only a Watt or so really - I have not doen a huge ammount of testing yet though)#

As for running cool - underclocking reduced my cpu temp to around 30C. I was a bit worried when I first set the server up as it was running around 45 - 50 and in a cupboard under the stairs.

---

