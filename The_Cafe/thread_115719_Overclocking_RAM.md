---
title: "Overclocking RAM"
date: 2006-01-11
forum: The Cafe
---

### Post by jon_z on 2006-01-11
I have Twin sticks of PC3200CL Pro Ram by Corsair.  Everyone says that this is one of the best overclocking rams to have, im just not sure how to accomplish this in the bios.  Andy information would be awesome.

Thans in advance
-Jon

---

### Post by Lovechild on 2006-01-11
I urge you not to do that, overclocking can lead to random errors and degrade product lifetime. There are several examples around the various project bugzillas of people blaming overclocking induced hardware failure on software. 

Please for your sake, and for the sake of the Ubuntu developers, I swear the speed gain you'll get isn't remotely meassurable in real life (in most cases) the degration in reliability however is quite certain. Take my 1600+ Athlon-XP, when running at FSB +7 (the highest "stable" overclock I can get) Ubuntu will hard lock under certain loads - now what does this 7MHz bump mean in real world terms around 100MHz which most certainly isn't meassurable in any scenerio I've come across.

That being said, you will be looking to bump the FSB, there are good guides on sites like HardOCP.com and overclockers.com.au.

---

### Post by jon_z on 2006-01-11
Thank you very much. I guess I will  just keep it the same then.. I cant complain too much with a AMD athlon 3200 and a gig of ram.. No sense in breaking anything.  Thank you very much.

---

### Post by mstlyevil on 2006-01-11
[QUOTE=jon_z]Thank you very much. I guess I will  just keep it the same then.. I cant complain too much with a AMD athlon 3200 and a gig of ram.. No sense in breaking anything.  Thank you very much.[/QUOTE]

Instead of overclocking at first, boot into your Bios and make sure your timings are voltage are set according to your rated specs. Most motherboards will not do this for you and set the timings much higher than the RAM is rated. To do this you need to consult your manual on your motherbard and find out where the timings are located in the bios. Then take the documentation you have with your RAM and check to see what all the timing setings are supposed to be. If they are different then just adjust the bios to reflect your rated timings and voltage and you will see a huge increase in RAM speed without overclocking.

If you have a AMD Athlon 64 processor there is really no need to overclock the RAM considering stock DDR1 RAM on this platform runs faster than an Intel with DDR2. I believe Hypertransport uses 95% of the memory's bandwidth so you will not see much of a speed increase with overclocking. Intel CPU's are a different matter altogether. Because they rely on the Front Side Bus, you have to ovcerclock in order to get the memory speed close to the levels that AMD systems have at stock. If your computer has plenty of power either way, I would not worry about overclocking.

---

### Post by Zodiac on 2006-01-11
Ha! Buffalo NY in the HIZZY!!

P.S. - Don't overclock your RAM... I did once... it was an unspeakable nightmare.

---

### Post by mcduck on 2006-01-11
[QUOTE=Lovechild]I urge you not to do that, overclocking can lead to random errors and degrade product lifetime. There are several examples around the various project bugzillas of people blaming overclocking induced hardware failure on software. 

Please for your sake, and for the sake of the Ubuntu developers, I swear the speed gain you'll get isn't remotely meassurable in real life (in most cases) the degration in reliability however is quite certain. Take my 1600+ Athlon-XP, when running at FSB +7 (the highest "stable" overclock I can get) Ubuntu will hard lock under certain loads - now what does this 7MHz bump mean in real world terms around 100MHz which most certainly isn't meassurable in any scenerio I've come across.

That being said, you will be looking to bump the FSB, there are good guides on sites like HardOCP.com and overclockers.com.au.[/QUOTE]
In my experience overclocking doesn't effect product lifetime, at least compared to normal lifetime of pc hardware :D

Not every CPU overclocks well, and some models are not worth overclocking at all. AthlonXP 2500 overclocks well, but 3200 is not worth the trouble.

My current desktop is slightly overclocked AthlonXP 2800, running at 2300MHz compared to default 2080MHz. Sure, there's no noticeable difference when surfing the net, but in more CPU-intensive tasks it's worth the required 2 minutes of BIOS tweaking and some hours of stability testing with prime95. After all, that's 10% extra speed, and now it's running faster than AXP2300 (2200MHz) that costed over 100€ more at the time..

Anyway, I do 3D animations, and if I can cut 2 seconds per frame in rendering time that's over 4 hours of saved time per 5 minutes of rendered 25fps video.. (and 4 hours less time I have to spend running windows ;))

---

### Post by mgmiller on 2006-01-11
What Mcduck says about cpu overclocking is very true, however, the original post was in reference to overclocking his RAM.   In my experience, I will mildly overclock my cpu and video card, but not the ram.  I buy the fastest memory I can afford and make sure the bios is set to use it at its rated speed.  I have had excellent results using Mushkin memory with the main timings at 2,2,2.  I currently use 2 x 1 gig sticks running dual channel with my amd 64 3200+ with the bios in the Asus A8V deluxe mobo set to "mild" 5% cpu overclock, but the ram timings set to rated speeds.   It's rock solid stable in Ubuntu 5.10 with excellent frame rates in UT2k4.

---

