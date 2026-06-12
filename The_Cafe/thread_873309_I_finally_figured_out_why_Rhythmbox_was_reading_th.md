---
title: "I finally figured out why Rhythmbox was reading the wrong tags.."
date: 2008-07-28
forum: The Cafe
---

### Post by Exershio on 2008-07-28
Wow, this problem has had me baffled for such a long time. Despite having the right ID3v2 tags, Rhythmbox was displaying tags that didn't even exist! (so I thought.) I had removed all ID3v1 tags AND all APE tags. Still didn't solve it.

So I decided to do a bit of experimenting, and finally found the problem. Some of my songs (the ones that were displayed wrongly) had more than one ID3v2 tag! I had no idea that was even possible. I found this out by using mp3tag to remove ALL tags from my songs. After doing that, some of my songs still had tags, and they were the wrong ones! So I removed them again, and a couple songs had tags still. So, I repeated the process again, and all my songs were tag-free.

Don't worry, I had a backup of all of my music before I stripped the tags. But incase any of you have the same problem, well, it just might be that your songs have multiple ID3v2 tags.

Now to figure out how to remove the wrong duplicates without removing the correct ones.

---

### Post by Exershio on 2008-07-29
YES! I finally got my entire music library tagged perfectly. I just cleared all the tags completely (from the songs that were tagged wrong) over and over until they were completely gone, then I used EasyTag to just fill in the correct tags for me.

Only took an hour or so too. Definitely worth it.

If anyone else had this problem, I hope my thread helped you at least a little. If not, give me a PM and I'll explain things better :D

---

### Post by kpkeerthi on 2008-07-29
What do you mean multiple tags? For e.g. artist tagged more than once, like so:
artist = ABC
artist = XYZ
???

---

### Post by nycste on 2008-07-29
mp3tag is a windows program no?

u used this in wine or actual windows?

and the used easytag a linux program to retag everything right?

did easytag messup tags on anything im just curious im tempted to retag all my music too, but 100gb or more is a scary thought

---

### Post by Exershio on 2008-07-29
> **kpkeerthi said:**
> What do you mean multiple tags? For e.g. artist tagged more than once, like so:
artist = ABC
artist = XYZ
???

Yes, just like that. When I deleted the tags, it only deleted "ABC" and then it left XYZ still tagged. So I deleted the tags again, and then it was cleared completely.

> **nycste said:**
> mp3tag is a windows program no?

u used this in wine or actual windows?

and the used easytag a linux program to retag everything right?

did easytag messup tags on anything im just curious im tempted to retag all my music too, but 100gb or more is a scary thought
mp3tag is indeed for windows only, but it runs perfectly through Wine (check the appdb). I used mp3tag to remove the tags since it supports more tag formats and I wanted to make sure they were really, really gone.

Then I used EasyTag to retag them all using ID3v2.3 (NOT ID3v2.4). ID3v2.4 doesn't seem to play nice with Rhythmbox

Also, just do what I did and **backup all your music before you start retagging them.** I would never risk losing so much music.

---

### Post by chensamurai on 2008-11-02
Hey, I've had the same issue for the past year and so I decided to use Banshee for a while rather than Rhythmbox.
However, since Rhythmbox is actually a great application, I googled for a solution to this tag issue once more and I found this.

Thanks a lot! I think this'll really help me. ~Now downloading mp3tag to re-tag my whole library. =D>

btw, is there a fast, automatic way to re-tag a whole music library after wiping it???

---

