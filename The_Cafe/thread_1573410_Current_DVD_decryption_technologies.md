---
title: "Current DVD decryption technologies"
date: 2010-09-12
forum: The Cafe
---

### Post by baddnady23 on 2010-09-12
Is there any word on when linux will be able to handle RipGuard or ARccOS encryption?  Any references to this I have found are dated and I cant sem to find any current discussions on it anywhere...  I didn't know if anyone know of anyone else working on it  :)

---

### Post by juancarlospaco on 2010-09-12
Real encryption technology need to be open source, by definition.

---

### Post by Dr. C on 2010-09-12
Depending which country one lives in breaking the DRM on DVDs is either a perfectly legitimate and legal activity or illegal.

---

### Post by baddnady23 on 2010-09-12
Correct.  I just wish it was easier to do from within ubuntu.  It doesn't seem to be an issue in windows :)

---

### Post by cariboo on 2010-09-12
When buying an OEM system you pay for the codecs needed to decrypt content, it's included in the purchase price. 

With a white box OEM copy on Windows 7 you don't get any of the crapware or codecs the other OEMs install, so you have to pay extra for the codecs.

---

### Post by mr clark25 on 2010-09-12
> **baddnady23 said:**
> Correct.  I just wish it was easier to do from within ubuntu.  It doesn't seem to be an issue in windows :)


everything seems to work just fine with handbreak....

i dont know if it will work with the new encryption. im hoping there will be an update. 

are there any movies out right now that use either one?

---

### Post by baddnady23 on 2010-09-12
> **mr clark25 said:**
> everything seems to work just fine with handbreak....

i dont know if it will work with the new encryption. im hoping there will be an update. 

are there any movies out right now that use either one?

I think so. I've been going through the very time consuming process of backing up my collection to iso format and occasionally I have been hitting on a disc that just would not copy, no matter what I did.

---

### Post by handy on 2010-09-12
> **baddnady23 said:**
> I think so. I've been going through the very time consuming process of backing up my collection to iso format and occasionally I have been hitting on a disc that just would not copy, no matter what I did.

On the very rare occasion I've struck a DVD that DVDShrink can't handle I use DVDfab Decrypter (also via Wine), it seems to handle anything you throw at it.

I recently went through my DVD collection using HandBrakeCLI & backed them all up onto HDD with subtitles (as my hearing isn't getting any better with age). Handbrake is absolutely brilliant, I was using the .svn versions as well, stable as can be, & never made a mistake. 

Though all of these disks were free of any kind of copy protection by this stage.

[I]**[Edit:]** Now that I think of it, there were a few out of the many, that HandBrakeCLI couldn't take from (copy protection free) DVD format to .mp4. 

A way around this is to use via Wine - SmartRipper.exe - (old though excellent freely available software) & turn the movie into one big .vob file. After this HandBrake can process it with no problems at all.

There is probably native software that can turn a DVDs content into one big .vob file.[/I]

---

### Post by cariboo on 2010-09-12
> There is probably native software that can turn a DVDs content into one big .vob file.

I used vobcopy, which is in the repositories, to rip my DVD collection. There were 6 or 7 that it wouldn't rip, but Handbrake did the job on those. The reason I used vobcopy, was I wasn't completely happy with the picture quality when using Handbrake, even on the highest quality settings.

---

### Post by handy on 2010-09-13
> **cariboo907 said:**
> I used vobcopy, which is in the repositories, to rip my DVD collection. There were 6 or 7 that it wouldn't rip, but Handbrake did the job on those. The reason I used vobcopy, was I wasn't completely happy with the picture quality when using Handbrake, even on the highest quality settings.

Currently we run a few computers with high quality 24" LCD monitors. We have never had a TV here (over 20 years); we do like a good story though (only the odd person doesn't it would seem). :)

So when it comes to video quality & HandBrake? I have to say that it is incredibly rare for me to pick-up any degradation of quality from the original. 
Which is great when considering the amount of compression I get when squashing a DVD to an .mp4 file of around 1GB.

I must say though, that on the rare occasion I have used a VCR to digital conversion, I have noticed the occasional red colour aberrations in the HandBrakeClI output file. Though it was never strong enough to cause me to reprocess the movie.

Anyway, all in all, after a LOT of use, I am so incredibly impressed with both the quality & the reliability of HandBrakeCLI. Once you learn how to use it, it becomes so simple to use (I use aliases so I don't have to remember the great long command lines).

Perhaps HandBrakeCLI brings faults that are only seen on huge TV screens? On that subject I can not comment. As it stands, I can't see me/us ever needing anymore than 24" monitors.
[B]
[I][Edit:][/B] The following is the kind of settings I use with HandBrakeCLI usually:

HandBrakeCLI -t --main-feature -i /media/dvd -o NAME.HERE.mp4 -e x264 -b 1000 -B 192 -s 1 --subtitle-burn
[/I]

---

