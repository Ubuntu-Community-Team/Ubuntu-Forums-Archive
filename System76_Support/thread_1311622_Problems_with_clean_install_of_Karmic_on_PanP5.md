---
title: "Problems with clean install of Karmic on PanP5?"
date: 2009-11-02
forum: System76 Support
---

### Post by samalex on 2009-11-02
Hi Everyone,

I've seen a few people reporting problems with Karmic on their PanP5 laptops, but is this from a clean install or upgrade?  I'm leaning more towards a clean upgrade, but I'd like to know what problems have been found going this route as opposed to an upgrade.  Or are most to all of the problems with an upgrade?

The only thing stopping me from doing a clean install now is having someplace to back-up my data to. 

Thanks --

Sam

---

### Post by tschlemmer on 2009-11-02
I just did the update from 9.04 to 9.10. It took awhile to download all of the updates but other than losing my link to the system76 device driver repository and have sound issues my update was relatively painless. The other thing that I did notice was that the fingerprint reader cannot be opened after I did the update.

Tony

---

### Post by samalex on 2009-11-02
> **tschlemmer said:**
> I just did the update from 9.04 to 9.10. It took awhile to download all of the updates but other than losing my link to the system76 device driver repository and have sound issues my update was relatively painless. The other thing that I did notice was that the fingerprint reader cannot be opened after I did the update.


Hmmm, those might not be show stoppers for me after all because I've seen fixes for the sound issue and I've never even setup the fingerprint reader software --- heck the reader still has the little blue sticker over it that came with the laptop :)  But all and all did all the software update correct?  Like OpenOffice 3.1, Firefox 3.5, Empathy, etc?

Also I read that the modem driver was one of the problems with the sound, which sucks because I hoped the modem would work with Karmic. 

Take care --

Sam

---

### Post by tschlemmer on 2009-11-02
I rebooted and now the fingerprint reader is working. Not sure why it couldn't open the device before as I rebooted a couple of times after completing the upgrade.

Tony

---

### Post by robtg on 2009-11-02
I did a clean install on my PanP5.  No sound; I'm having erratic mouse pointer movement using the touchpad; wireless connectivity sometimes works, sometimes doesn't, and Flash is acting flaky.  Tonight I'm "upgrading" back to 9.04 which was working fine.

Canonical's 6-month upgrade cycle is nuts.  Less new "features" and more stability would be a good thing.

---

### Post by tschlemmer on 2009-11-02
> **samalex said:**
> Hmmm, those might not be show stoppers for me after all because I've seen fixes for the sound issue and I've never even setup the fingerprint reader software --- heck the reader still has the little blue sticker over it that came with the laptop :)  But all and all did all the software update correct?  Like OpenOffice 3.1, Firefox 3.5, Empathy, etc?

Also I read that the modem driver was one of the problems with the sound, which sucks because I hoped the modem would work with Karmic. 

Take care --

Sam

OpenOffice and Firefox ran just fine after the update was done and I rebooted.

Tonyl

---

### Post by marshmallow1304 on 2009-11-02
I formatted my / partition to ext4 and did a clean install while leaving my /home partition intact as ext3.  Worked like a charm; no problems except the sound issue, but removing the driver for the software modem took care of that.

---

### Post by miniyak on 2009-11-02
I have so many odd settings that i just decided to dual boot and use karmic every now and then till the settings are the same. 

here are the problems i noticed
-error modifying/creating swap during partition process... what ever that means... seems to work any ways...
-ubuntu "software store" was missing install buttons at first, not a big deal, just frustrating that it wont reload the repos itself on initial boot 
- keyring manager is still a pain in the @$$ maybe more so
- system 76 driver seemed to do nothing... but that could just be me being dumb

good things I noticed
-1680*1050 right off the live cd, i dont even think that the nvidia drivers even installed yet 
-Understandable sound preferences, and by the looks of it audio over hdmi is going to work when i test it out 
- ubuntu one

there maybe more things to add to ether of those list but i havent used it enough yet. From what i saw everything seems to be ok in regards to deal breaking bugs. Im sure issues like the one i had with the swap are localised, meaning it only happened to me for some odd reason.

---

### Post by thomasaaron on 2009-11-03
I'm seeing a number of problems, almost all of which are due to corrupted online upgrades. (Happens every release. Nothing new.)

Sound, touchpads, loss of gdm, etc...

Your best bet is either to wait a while and let things calm down, or download a fresh image, disk-check it, and then do a fresh install.

Haste makes waste.

---

### Post by samalex on 2009-11-03
> **thomasaaron said:**
> I'm seeing a number of problems, almost all of which are due to corrupted online upgrades. (Happens every release. Nothing new.)

Sound, touchpads, loss of gdm, etc...

Your best bet is either to wait a while and let things calm down, or download a fresh image, disk-check it, and then do a fresh install.

Haste makes waste.

Hi Thomas,

Good advice.  When I made the post I was pretty much ready to do a clean install, but now that I've seen all the problems reported (not only on S76 systems but all over) I'll probably hold off.  

I agree with some of the other posters that Ubuntu needs to release new versions less frequently and stick with trying to make the distro as solid as possible.  It's hard to try and 'sell' Ubuntu to non-Linux users when it's this buggy out of the gate.

Sam

---

### Post by HotShotDJ on 2009-11-03
> **samalex said:**
> I agree with some of the other posters that Ubuntu needs to release new versions less frequently and stick with trying to make the distro as solid as possible.The 6 month releases are for those of us who like to have the latest software, and can/will tolerate a bit of debugging to get it.  What you are asking for is something like a "Long-Term Support" distribution.  Ubuntu could do something like that -- maybe stick the letters "LTS" after the name so that everybody would know what it was...

... wait a second... hmmmmm..... LOL

(Just some good natured ribbing.  ):P)

---

### Post by robtg on 2009-11-03
> **HotShotDJ said:**
> The 6 month releases are for those of us who like to have the latest software, and can/will tolerate a bit of debugging to get it.  What you are asking for is something like a "Long-Term Support" distribution.  Ubuntu could do something like that -- maybe stick the letters "LTS" after the name so that everybody would know what it was...

... wait a second... hmmmmm..... LOL

(Just some good natured ribbing.  ):P)

Nobody likes the latest software more than I do but I'd also like for it to work.  There's nothing I'd like more than to see various Linux distributions blow Windows out of the water but for that to happen, people need to feel confident that they're installing an operating system that they don't need to debug, or worse, back-out.  I've used Windows from way back in the 3.1 days all the way up to XP.  For all of its warts, I've never had to back it out to a previous release.  As someone else said, buggy releases of Ubuntu are not going to do anything for its popularity except amongst geeks who enjoy a challenge.  I'm just using my PanP5 for recreational purposes but I'd be mighty annoyed if a computer I depended upon needed to have its OS backed out.  If they're not careful, Canonical may have to change it's description of Ubuntu to "It just works...kinda...eventually!"

---

### Post by HotShotDJ on 2009-11-03
> **robtg said:**
> I've used Windows from way back in the 3.1 days all the way up to XP.  For all of its warts, I've never had to back it out to a previous release.  As someone else said, buggy releases of Ubuntu are not going to do anything for its popularity except amongst geeks who enjoy a challenge.Just for the record, I never drank the Windows Kool-Aid.  I only used Windows for a few years before I had my fill of it.  I learned how to use computers in the mid-late '70s -- with OS/2 being my first GUI oriented OS sometime in the mid '90s.  I did use Windows from 1999 until the winter of 2001 -- and complained bitterly the entire time.  Now, I only use Windows if I absolutely have to because of work, and even then, only in a VM and only if the software is provided for me under a site license by the university.

Having said that, I have never, EVER, heard of an MS Windows OS that was not horribly buggy on release.  And this is after years of development and millions of dollars invested in the releases (along with every major hardware vendor ALSO investing millions of dollars to make sure that their hardware is compatible with the new release and that they have drivers available by the release date).  And even THEN, users often have to buy new hardware in order to use the next "great" version of Windows.  Some people suggest that one should never upgrade to a new Windows release at least until the first major service pack.  Yet, on a shoe-string budget and without the support of many of the hardware vendors -- and even outright hostility from some of them -- we get a FREE OS that is upgraded every 6 months (and is sometimes buggy for some hardware) and when it is less than perfect, we hear all this craziness about how Linux will never be popular unless it quits releasing buggy software.  I am constantly amazed by the blatant double-standard.  By this logic, Microsoft would have been out of business sometime in the mid-1980's.

I fully, and whole-heartedly agree with you that the 6 month releases are not for everybody.  For the people who don't want to spend a lot of time tweaking and enduring the growing pains that inevitably come with the open source philosophy of "release early - release often," then they are well advised to stick with Ubuntu's LTS releases.  And for the more adventurous "early adopters" out there, the 6 month releases of Ubuntu are well worth the effort.  And for the real hobbyist/geek/hacker, there are the ppa's.  There's something for everybody, as long as the users choose wisely.

And finally, I'm a firm believer that a person who upgrades without first testing the new software (whether its Linux, Windows, Open Source, Proprietary... whatever) deserves exactly what they get. And trust me, I've gotten what I've deserved more than once -- and been pleasantly surprised at least as often. Samalex is being very wise.  He's asking a lot of questions, and I'm sure that he will do quite a bit of testing before he upgrades his Jaunty system.  And this is just as it should be for everybody.

---

### Post by samalex on 2009-11-04
[QUOTE="HotShotDJ"]And finally, I'm a firm believer that a person who upgrades without first testing the new software (whether its Linux, Windows, Open Source, Proprietary... whatever) deserves exactly what they get. And trust me, I've gotten what I've deserved more than once -- and been pleasantly surprised at least as often. Samalex is being very wise. He's asking a lot of questions, and I'm sure that he will do quite a bit of testing before he upgrades his Jaunty system. And this is just as it should be for everybody.[/QUOTE]

HotShotDJ, you're completely correct...  Given my laptop is my primary computer which I depend on for work and school, I can't afford to guinea pig it with a botched upgrade unless I know it'll work.  Also it took some time to get Firefox tweaked to work with Shockwave and Sun Java for my online college courses so I'm not eager to throw all that out the window just yet.

I've gone back and forth on upgrade vs clean install and now vs next month when my current online class is over.  At this point my plan is to backup my data and resize the home partition to make room for a new partition large enough to load 32-bit Ubuntu 9.10.  This'll leave my current system as-is and let me test Ubuntu 9.10.  If it works as expected I can reclaim the space used by 64-bit Ubuntu 9.04 later or keep that available for another OS.

The reason for 32-bit is two fold... firstly I really want a stable version of Flash and the Flash wrapper on 64-bit Ubuntu just isn't cutting it and I've had zero luck getting alpha 64-bit Flash working.  And secondly moving to 32-bit Ubuntu hopefully will allow me to run some of the 32-bit applications I just can't get working under 64-bit Ubuntu.  

Anyway, that's my goal at this point.  I'll post updates as I go.

Sam

---

