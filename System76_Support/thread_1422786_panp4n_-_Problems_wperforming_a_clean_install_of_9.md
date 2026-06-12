---
title: "panp4n - Problems w/performing a clean install of 9.10"
date: 2010-03-05
forum: System76 Support
---

### Post by jeffran on 2010-03-05
Hi All,

I've tried, twice now, to perform a clean install of 9.10 on my Pangolin (panp4n). Each time I attempted the install, the previous OS was 9.04 - also a clean install that worked perfectly. The first attempt the 9.10 install seemed to go well until I restarted, at which time a bootable device couldn't be found. The second attempt, just yesterday, resulted in a I/O error 59% into the install. But, even this install seemed to work until the first restart, at which time I had 'Error 15'.

After each of these attempts, I've been able to go back to 9.04 without any problems whatsoever - no hardware or software issues. Is there something special about the panp4n that would cause this issue? Any similar problems with other systems?

Thank you - Jeff

---

### Post by miniyak on 2010-03-06
in my experience this is the result of a bad live cd. Either from a bad iso download or cd write

since you have that cd already written there is a error checking option right after the language selection dialogue in the first menus of the live cd. This takes a while but if you want to confirm that a bad write is the issue you can use this.

Actually the first thing i would do is grab the karmic torrent. download it. I've never really understood the md5 checksum thing but you should grab the hash for karmic, get the hash from your iso then compare the two cause it say so in the ubuntu wikis.. lol. Then once that checks out write the iso to the disc again, this time make sure it is at the slowest possible speed setting if its not already. 

bad cds make good decorative craft materials

---

### Post by thomasaaron on 2010-03-08
miniyak might be right.

Also, that "Error 15" means it can't find your boot files. When imaging did you select the "Use Entire Disk" option? Or did you manually partition?

And if you manually partitioned, did you make the root partition bootable?

---

### Post by jeffran on 2010-03-08
Thanks for the input guys. Thomas - I used the entire disk, no manual partitioning. I will try to download an image again, and make sure the checksums match.

---

### Post by jeffran on 2010-03-08
It looks like miniyak was right - I downloaded a new image, made sure the checksums matched, and successfully installed. I also verified that the image I burned last week did not have the correct checksum. Thank you for your help!

---

### Post by Lee_Machine on 2010-03-09
> **miniyak said:**
> in my experience this is the result of a bad live cd. Either from a bad iso download or cd write

since you have that cd already written there is a error checking option right after the language selection dialogue in the first menus of the live cd. This takes a while but if you want to confirm that a bad write is the issue you can use this.

Actually the first thing i would do is grab the karmic torrent. download it. I've never really understood the md5 checksum thing but you should grab the hash for karmic, get the hash from your iso then compare the two cause it say so in the ubuntu wikis.. lol. Then once that checks out write the iso to the disc again, this time make sure it is at the slowest possible speed setting if its not already. 

bad cds make good decorative craft materials


miniyak,

MD5 is used for file integrity checks. In other words it creates a unique hash for that file. If anythings changes with the file its hash will be different. 

Further reading...

[http://en.wikipedia.org/wiki/Md5sum](http://en.wikipedia.org/wiki/Md5sum)

---

### Post by miniyak on 2010-03-09
haha, thanks lee, I do have vague idea of what md5 does. I Guess some fail of text sarcasm slipped because i have always messed up comparing the checksums somehow (anxious bout a new install) and skipped it all together. As a result i have ran into this issue a couple of times blissfully unaware the iso was already borked. Love to learn the hard way.

Glad your up and running jeff

---

### Post by riseringseeker on 2010-03-10
> **jeffran said:**
> It looks like miniyak was right - I downloaded a new image, made sure the checksums matched, and successfully installed. I also verified that the image I burned last week did not have the correct checksum. Thank you for your help!

Might be good if you marked this solved then...

---

### Post by jeffran on 2010-03-10
I'm not seeing how I mark this issue as 'SOLVED'. Thanks - Jeff

---

### Post by miniyak on 2010-03-10
i agree the "solved ma-bob" is way too difficult to find for new members. And a email subscription my default would be a good idea too... though i guess i can see why not also..

anyhow... up at the top of the thread there is drop down option in red labeled thread tools, "mark as solved" should be right under there.

wait... looks like you got it.

oh well... remember to recycle those useless cds! They'll look better on your own diy project then they will in a landfill. Looks like someone was trying to make a roof out of them on [instructables]("http://www.instructables.com/id/CDDVD-Roofing-Concept/").  Ive made a parabolic dish with em' once, lmao... it could have worked better... but it was interesting to say the least.

---

