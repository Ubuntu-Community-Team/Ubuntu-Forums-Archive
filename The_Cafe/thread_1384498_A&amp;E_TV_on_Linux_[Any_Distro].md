---
title: "A&amp;E TV on Linux [Any Distro]"
date: 2010-01-18
forum: The Cafe
---

### Post by Dark Aspect on 2010-01-18
Has anyone here regardless of what form of Linux your using managed to get any of the video streams off A&E's [website]("http://www.aetv.com/") working?

For example on the [frist 48]("http://www.aetv.com/the_first_48/video/") the video just loads for ever, I have flash installed and it does this with Ubuntu, Arch and Puppy. I have to boot into a very small windows partition to get the videos to work, is there some kind of codec I am missing or is the flash on Linux limited?

---

### Post by Excedio on 2010-01-18
No dice...

---

### Post by lovinglinux on 2010-01-18
Although A&E is included in my satellite subscription plan, I can't access the videos on the site because I don't live in US, just like Hulu. Well, I'm not losing anything superb anyway, since A&E is not a good channel here, but that really pisses me off.

---

### Post by false_apology on 2010-01-19
I'll throw a "me too" into this - using Mythbuntu 8.04, I get the same result... any suggestions would be great. I am using flash v10,0,42,34

---

### Post by Dark Aspect on 2010-01-20
> **false_apology said:**
> I'll throw a "me too" into this - using Mythbuntu 8.04, I get the same result... any suggestions would be great. I am using flash v10,0,42,34

Well depending on how fast your hardware is, I can confirm that the videos work on virtualbox. However that way out is too slow of a solution for me on my hardware.

I am guessing it’s either a missing codec or A&E hates the Linux version of flash. IE via wine works, so I am going to try Firefox through wine.

---

### Post by wyth on 2010-01-31
Just happened across this thread googling the same question.  

I'm nearly positive this is a flash issue; it's the same for all of that network group -- A&E, Biography, History, History International.  I know about six months ago I was able to stream videos from History; but like with A&E, no videos will load for me on that site now (or any of the sites).

It worked for me on Windows via virtual box, but failed on both 64 and 32 bit versions of linux flash.  However, when I loaded up a video page in VirtualBox, Firefox spit all kinds of script errors -- which makes me think the sites themselves are not coded all that well.

They're using Brightcove for their video; I haven't had trouble with any other Brightcove videos.

---

### Post by sports fan Matt on 2010-02-01
Same Result--Karmic 9.10 with all codecs.

---

### Post by darco on 2010-02-01
Im on Linux Mint, tried Opera 10.5, Chromium and Namoroka and none were able to play these vids....that sad.

---

### Post by Ralob on 2010-02-01
Probably uses Move Networks codecs which are not compatible with Linux. This is a common problem for sites like Fox and ABC as well. Apparently they have plans for a Linux port... that was announced 2 years ago.

---

### Post by tom957 on 2010-02-05
I've been periodically trying to watch The First 48 on A&E's site for a few months with no luck. Brightcove FTL.

---

### Post by earthpigg on 2010-02-05
nope, and no luck digging through ~/.mozilla/firefox/*.default/. either.

(for those who dont know what im talking about, that's where you can get a 'permanent' copy of whatever you recently watched on youtube, etc... just sort the files by recently modified, find the file, and copy/paste it somewhere else. no need for any firefox addon.)

---

