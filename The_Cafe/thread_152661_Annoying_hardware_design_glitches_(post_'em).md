---
title: "Annoying hardware design glitches (post 'em)"
date: 2006-03-30
forum: The Cafe
---

### Post by blueturtl on 2006-03-30
*The idea of this thread is for you to post annoying hardware design glitches and flaws that you've come across, explain how you stumbled on them, and explain their significance to yourself or people involved. Do not post experiences on so called bad apples, only something that can be generalized and confirmed by others as well. Bonus points for stuff that isn't that common knowledge (even among geeks). Consider this an opportunity to educate others.*

I'll start:

**FACT:** Around the time Pentium's were top of the line, did you know that system's with more than 64 megabytes of RAM would suffer from degraded performance? The early Intel chipsets with the exeption of the 430HX "Triton II" were unable to cache any RAM beyond the 64 meg boundary! Read [this link]("http://www.pcguide.com/ref/mbsys/cache/charCacheability-c.html") for the full technical details and background info...

**EVIDENCE:** I had an old Pentium 166 at the time with 64 megabytes of memory. I remember I had a Voodoo board installed to enhance the gaming. However 64 megs just wasn't enough at times, and some more demanding games of the time like Half-Life or Unreal would show a lot of swapping at first before running smoothly. I bought me an extra 32 megabytes of RAM to get rid of the swapping. After installing more RAM there was less swapping, but the games now ran at a noticeably lower framerate than before! I remember being really really puzzled about that.:confused: 

**IMPLICATIONS:** More memory actually equals less performance! Intel left Pentium owners in a very poor position where they had to gamble between memory amount and memory speed! :-k Before someone mentions AMD I'd like to point out that AMD chips before the K7 really took a beating from all Intel based offerings, so there generally were no options if you wanted something better performancewise!

Ok... your turn.

---

### Post by mcduck on 2006-03-30
[QUOTE=blueturtl]
Ok... your turn.[/QUOTE]
Ok. I just lately found out that some iPods report their size to be a bit bigger than what they really are.. So when your system tries to read the last sectors of the disk, the iPod will stop responding, because those sectors don't even exist :rolleyes: 

I found this out when I tried to resolve my problems with my iPod Mini and Dapper.. The EFI partition support that is enabled in Dapper kernel causes Linux to try to read those last sectors to check if it's EFI partition instead of FAT.. And then the iPod stops responding, corrupting the database and most of the audio files on it :) (some iPods just won't mount because of this, but that would sure be nicer than the thing freezing when transfering music to it)

I think that this counts as annoying hardware design glitch :D

---

### Post by majikstreet on 2006-03-30
well the dell dimension 2350 has something wierd.. you can't actually disable the onboard video card, so you can't upgrade to another card (and it doesn't have AGP..)

---

### Post by Brunellus on 2006-03-30
[QUOTE=majikstreet]well the dell dimension 2350 has something wierd.. you can't actually disable the onboard video card, so you can't upgrade to another card (and it doesn't have AGP..)[/QUOTE]
hey, kid, that's how it used to be back in the day.

actually, I lie.  When I first started using computers (not so long ago, compared to some of the other guys here) the hot graphics card was a Hercules.

---

### Post by towsonu2003 on 2006-03-30
I won't be getting any bonus for this [-( 

Hardware: HP Pavilion Laptop

Glitches:
1. Fan system does not allow for more air to come in efficiently, because fan is underneath the laptop and the laptop is not far enough from the ground to get enough air
2. Fan collects more dirt than it should due to the closeness between ground (read: dirt sucked in) and laptop fan

Workarounds:
1. Put laptop on lap, spread legs so fan will suck up air in between your legs
2. Open up heat sink and clean with air every 4-6 months or so. 

Results: 
1. Average temp will drop by 2-3C
2. Average temp will drop by 10C if done every 6 months (assuming you have dirty house) or 15C if done once a year (assuming your house stinks as per above). 

Disclaimer: Don't try 1 with a desktop pc (ouch regardless of gender), don't try 2 without an excellent manual that describes this (available from HP site of your laptop or via email support). 

Solution: Put the fan grids (??, where the air is sucked in and blown out) only to the sides of the laptop. 

Experience: With 2, i once got a piece of dirt the size of my finger out of the fan grid (my house truely stinks). And a piece of paper (blank post-it) from inside the heat sink. No gremlins ](*,) as of now...

---

### Post by drizek on 2006-03-30
[QUOTE=majikstreet]well the dell dimension 2350 has something wierd.. you can't actually disable the onboard video card, so you can't upgrade to another card (and it doesn't have AGP..)[/QUOTE]

My old compaq didnt have the option to disable it in the BIOS but i was still able to use a PCI card with no problems.

---

### Post by rfruth on 2006-03-30
It bugs me that CRT monitors count the glass under the plastic bezel in the screen size so a 17 inch monitor is actually 16.4 which rounds to 16 so 17 inch monitors are 16 in my book.  :(

---

### Post by benplaut on 2006-03-30
My friend's laptop, an Ibuypower Battalion, is a heat whore.

5 minutes into playing a game comes the familiar "beep beep beep ssshhhooooooooooop." as it shuts off.

Solution: Suspend it on books for better air flow, or (the best) place it on top of ice packs (in plastic bags for condensation). 

He sent it back to ibuypower this morning, i doubt they'll fix it :P

---

### Post by drizek on 2006-03-30
What kind of CPU does it have?

If its a pentium m then you can undervolt it to reduce the cpu heat quite a bit.

---

