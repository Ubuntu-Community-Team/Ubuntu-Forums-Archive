---
title: "Computer randomly freezes up: Hardware or software?"
date: 2007-10-16
forum: Windows
---

### Post by Malh on 2007-10-16
I just built this desktop with parts from newegg.  Specs: AMD Athlon 64 X2 5600+, 2GB RAM, ATI Radeon x1950pro, 250GB HDD, 500W PSU.  I installed XP on it because I made it specifically for gaming.  It worked perfectly fine for the first 2 months I had it, but it now frequently freezes up, about once every 2 hours on average.  The problem is, it doesn't just freeze up and cause me to have to reboot.  It instead freezes up for 3 seconds, usually causing my dialup connection to be lost.  During the 3 seconds that it is frozen, the mouse doesn't move and if I'm watching a movie or listening to music, the audio repeats itself for the 3 seconds and makes a glitchy noise.  After it freezes, everything returns to normal and I have to reconnect to the internet, which is a big problem if I'm playing a game online or downloading something.  What's causing this problem and how do I fix it?  Thanks in advance.

---

### Post by sayuki288 on 2007-10-16
like i have the same problem as you :lolflag: think i fixed it with chkdsk and when i defragment my drive  :)

---

### Post by Malh on 2007-10-16
> **sayuki288 said:**
> like i have the same problem as you :lolflag: think i fixed it with chkdsk and when i defragment my drive  :)

I hope so, will try it when I get home...I thought I fixed it yesterday when I reinstalled my video drivers and MoBo software, but it started back.

---

### Post by digital_exhaust on 2007-10-16
Heat could be an issue... what type of hsf are you using, and psu details would help, brand and model... and if you can check the voltages....and ram specifics would help as well... brand, type and timings...

---

### Post by Malh on 2007-10-17
> **digital_exhaust said:**
> Heat could be an issue... what type of hsf are you using, and psu details would help, brand and model... and if you can check the voltages....and ram specifics would help as well... brand, type and timings...

I was thinking heat could be a problem...I sorta jerry-rigged my machine.  The locking mechanism on my stock hsf is broken so I wedged a piece of plastic where the locking mechanism used to be and it's attached but it's not as tight as it would be if the locking mechanism was there.  I should probably order a better hsf...I already tried to buy a socket AM2 hsf at a local computer store but the fools sold me a socket A hsf and they refuse to give a refund.  A warning to people in the SC area: don't shop at Compuzone, they're idiots and have no return policy.

---

### Post by disasm on 2007-10-17
> **Malh said:**
> I just built this desktop with parts from newegg.  Specs: AMD Athlon 64 X2 5600+, 2GB RAM, ATI Radeon x1950pro, 250GB HDD, 500W PSU.  I installed XP on it because I made it specifically for gaming.  It worked perfectly fine for the first 2 months I had it, but it now frequently freezes up, about once every 2 hours on average.  The problem is, it doesn't just freeze up and cause me to have to reboot.  It instead freezes up for 3 seconds, usually causing my dialup connection to be lost.  During the 3 seconds that it is frozen, the mouse doesn't move and if I'm watching a movie or listening to music, the audio repeats itself for the 3 seconds and makes a glitchy noise.  After it freezes, everything returns to normal and I have to reconnect to the internet, which is a big problem if I'm playing a game online or downloading something.  What's causing this problem and how do I fix it?  Thanks in advance.

Try a linux live cd. Run cpuburn from it. Also, try memtest86. If both of those don't have any problems, well, it's probably the OS. You could also try a factory hard disk test from The Ultimate Boot CD, just make sure you don't choose the destructive option.

Sam

---

### Post by digital_exhaust on 2007-10-17
> **Malh said:**
> The locking mechanism on my stock hsf is broken so I wedged a piece of plastic where the locking mechanism used to be and it's attached but it's not as tight as it would be if the locking mechanism was there

That's going to be the source of your problems... and the unavoidable death of your CPU if you don't remedy the problem asap..... Correct contact between the HSF and CPU is extremely important...

---

### Post by Malh on 2007-10-19
> **digital_exhaust said:**
> That's going to be the source of your problems... and the unavoidable death of your CPU if you don't remedy the problem asap..... Correct contact between the HSF and CPU is extremely important...

yeah I meant to fix the problem when it occured but i spent my last $20 on the socket A HSF

---

### Post by Malh on 2007-10-19
> **disasm said:**
> Try a linux live cd. Run cpuburn from it. Also, try memtest86. If both of those don't have any problems, well, it's probably the OS. You could also try a factory hard disk test from The Ultimate Boot CD, just make sure you don't choose the destructive option.

Sam

I'll definitely run every test on Hiren's Boot CD when I get home.

---

### Post by digital_exhaust on 2007-10-19
> **Malh said:**
> I'll definitely run every test on Hiren's Boot CD when I get home.

Isn't Hirens warez:confused:

Just curious.... anyhow, don't do anything that's going to stress your CPU until you replace your HSF.... seriously....your going to kill it if you keep overheating it....

---

### Post by Malh on 2007-10-19
> **digital_exhaust said:**
> Isn't Hirens warez:confused:

Just curious.... anyhow, don't do anything that's going to stress your CPU until you replace your HSF.... seriously....your going to kill it if you keep overheating it....

Yeah...Not turning it on until I get a new HSF

---

### Post by Malh on 2007-10-20
Ok I replaced my HSF, applied more thermal compound, I tested the RAM, HDD, CPU, MoBo and everything passed.  I still have the problem though.

---

### Post by Malh on 2007-10-21
Also just reinstalled xp using a different disc and it still freezes up.

---

### Post by digital_exhaust on 2007-10-21
Alright.... you are obviously having a hardware problem. I know this is a pain, but the only advice I can offer at this point is to tear it down and start over... 

Pull everything out of your case, put the mobo on a piece of cardboard, and start with the basics, cpu/hsf, one stick of ram, video card and psu, keyboard, mouse and your display. Make sure you have a case speaker attached and see if it will post. If it does, add your other components, one at a time until you find the culprit. If it doesn't post with just the basics, listen for beeps and report them here... I imagine it will indeed post, but you never know. Once you have everything reinstalled, before trying to install your OS, run memtest on each stick separately for a minimum of four hours, 24 if you can be patient enough... and see what you get.. I see you stated you "tested" your ram already, and if you let the test run for an adequate amount of time, skip it, but most people don't let memtest run long enough to provide reliable results... and even one error is enough to cause problems... 

Good luck man, and I hope you can get your machine running... broken boxes are no fun.....

---

### Post by Malh on 2007-10-21
Everytime I boot it up, it beeps once which means everything should be fine.  It just happened again about 30 minutes ago and I noticed my internet connection was cut off again.  It wasn't freezing for a while until I installed my PCI modem, could my modem be causing this problem?

---

### Post by kulturloseramerikaner on 2007-10-22
OK, so just to clarify, you *did* have it torn down, and were doing fine until putting the modem back in?  If so, I'd say you answered your own question.  Considering you can them new for $15 or used for even cheaper, it'd definitely be worth your trouble to pick up a second and give it a try.

---

### Post by Malh on 2007-10-22
> **kulturloseramerikaner said:**
> OK, so just to clarify, you *did* have it torn down, and were doing fine until putting the modem back in?  If so, I'd say you answered your own question.  Considering you can them new for $15 or used for even cheaper, it'd definitely be worth your trouble to pick up a second and give it a try.

Yeah right after I installed said modem it started happening again.

---

### Post by kulturloseramerikaner on 2007-10-23
I'd say it's time to add said modem to the round file.

---

