---
title: "Dofus questions (some unrelated to ubuntu) \o/"
date: 2010-12-15
forum: Security
---

### Post by communityofexcellence on 2010-12-15
So I hadn't found any policies against posting security q's if they weren't related to linux and I feel that even though this community is oriented on linux that here would be the best place to go. If I am infringing upon the politics of this forum, please let me know.

So I've multiple questions, but if you just know about one problem feel free to reply, all help is appreciated!

1. For pre-burnt media, such as a peice of software on a dvd you purchased from a retail store, is it possible to write more data to the disk or overwrite it if the disc registers as being completely full?

2. Is it possible to exploit the embedded linux system in typical home routers into re-flashing a malicious form of linux without consciously accessing the upgrade or install page of the web ui?

3. How does firmware malware function? How do they get there and how can they be removed?

4. For usb connections in windows, if I were to want to prevent a drive from doing any automated functions, would I just have to change the auto run registry values to prevent the.inf file from infecting a system if the drive was malicious?

As I said before, any and all help is greatly appreciated!

---

### Post by CharlesA on 2010-12-15
> **communityofexcellence said:**
> So I hadn't found any policies against posting security q's if they weren't related to linux and I feel that even though this community is oriented on linux that here would be the best place to go. If I am infringing upon the politics of this forum, please let me know.

Looks fine to me. There isn't any policy about asking security questions that are not related to Ubuntu here.

> **communityofexcellence said:**
> 
1. For pre-burnt media, such as a peice of software on a dvd you purchased from a retail store, is it possible to write more data to the disk or overwrite it if the disc registers as being completely full?

Those types of discs aren't "burned" like you do with a cd-r/cd-rw and since that's the case, they are considered "finalized" and cannot be written to.

See [here]("http://en.wikipedia.org/wiki/Compact_Disc_manufacturing") for some info on how they're created.

> **communityofexcellence said:**
> 
2. Is it possible to exploit the embedded linux system in typical home routers into re-flashing a malicious form of linux without consciously accessing the upgrade or install page of the web ui?

I cannot imaging flashing a router from over the internet, one hiccup and you have a bricked router.

In any case, don't allow remote management and you'll be fine.

> **communityofexcellence said:**
> 
3. How does firmware malware function? How do they get there and how can they be removed?

This I don't know, but encountering malware that attacks firmware is a rare occurrence as far as I know.

> **communityofexcellence said:**
> 
4. For usb connections in windows, if I were to want to prevent a drive from doing any automated functions, would I just have to change the auto run registry values to prevent the.inf file from infecting a system if the drive was malicious?

Disable Autorun. The Newer versions of Windows (Vista and 7) always ask you if you want to run someprogram.exe if there is an autorun.inf file on the media.

---

### Post by communityofexcellence on 2010-12-15
Your feedback is deeply appreciated. As for the router question, if it was successfully flashed via a lan is there a foolproof method to restore the proper firmware without risking the security of a clean system accessing it?

Super OT:By the way, I can't help but thank you and the other staff members and this entire community. The forums here provide excellent and pinpoint information that has been  the one stop place for those strange tech questions I get. Not only am I in debt but the internet alike is forever in your debt for helping others and providing the proper attention to linux based systems, paving the way for technological advances of the future. (No homo ¥_¥)

---

### Post by CharlesA on 2010-12-15
> **communityofexcellence said:**
> Your feedback is deeply appreciated. As for the router question, if it was successfully flashed via a lan is there a foolproof method to restore the proper firmware without risking the security of a clean system accessing it?

As far as I know, flashing a router with third-party firmware is a one-way process.

I suppose it goes back to the whole "physical access = root access" deal. If someone has physical access to your network/computers, they can do pretty much whatever they want.

Are you referring to a specific incident, or just in general? I don't really know of any malicious router firmware. That doesn't mean it doesn't exist, but it would be a hell of a lot of work to develop.

---

### Post by cariboo on 2010-12-15
There apparently is a way to change router firmware remotely, but it counts on the default router admin password still being set. See more [here]("http://www.engadget.com/2008/04/08/researcher-creates-malicious-router-controlling-website/").

> Your feedback is deeply appreciated. As for the router question, if it was successfully flashed via a lan is there a foolproof method to restore the proper firmware without risking the security of a clean system accessing it?

It all depends on what the firmware does. 

DD-WRT recommends that you disconnect the router from the rest of the network including the internet, and only have the system that holds the software needed to flash the firmware connected to it.

All routers have a utility to create a backup of the installed firmware which I'd advise you do, and then put the backup in a safe place.

---

### Post by communityofexcellence on 2010-12-15
No, but I'm just assuming that since the devs at dd-wrt and tomato can create their own excellent router firmware, shouldn't a baddie be able to do the opposite and create a malicious version?

---

### Post by CharlesA on 2010-12-15
> **communityofexcellence said:**
> No, but I'm just assuming that since the devs at dd-wrt and tomato can create their own excellent router firmware, shouldn't a baddie be able to do the opposite and create a malicious version?
While possible in theory, it's a ton of work to create router firmware.

I suppose the point I'm trying to make is that there comes a point where it's just too much work to even bother with.

---

### Post by communityofexcellence on 2010-12-15
so its just too rare to consider. Okey. If anyone can answer my third question then that would do it for this thread. Thanks for the feed back thus far!

---

### Post by CharlesA on 2010-12-15
The only thing I can think of for number three is that someone would need physical access to your router to flash it with something like that.

The only way to get it back to the default is to try to flash the default firmware back on the router, but I don't know how feasible that is.

---

### Post by communityofexcellence on 2010-12-16
what about like... Keyboards and mice that function on firmware, those can be attacked as well right?

---

### Post by communityofexcellence on 2010-12-16
as it turns out I had another thread but we couldn't reach a conclusion on it so I suppose il ask it here too along with the ongoing firmware question.

Copied from: [http://ubuntuforums.org/showthread.php?t=1645821](http://ubuntuforums.org/showthread.php?t=1645821)

"So, I have a strange question which I haven't managed to find the answer to but I'm sure this wonderful and knowledgeable community could aid me. I was curious on whether or not there was non volatile memory in either of the two. Or any way to keep an amount of code residing in them after deprivation of current. Would this be possible?"

I ask out of wonder if malware could reside in them if transplanted and re infect a clean system. 

Another off topic note: I've made multiple accounts here for temporary aid but in the upcoming months I hope to begin to give back to this community. It simply astonishes me how readily you folks are to help any and all. I don't know why I keep doing this but its the last googoo eyes reply. Ill take it to the feed back forum next. :)

---

### Post by CharlesA on 2010-12-16
I have the same thoughts as cascade9 in that thread. In theory it might be possible, but I don't know if it'll actually work in "the real world"

---

### Post by communityofexcellence on 2010-12-16
> **CharlesA said:**
> I have the same thoughts as cascade9 in that thread. In theory it might be possible, but I don't know if it'll actually work in "the real world"

What do you mean?

---

### Post by CharlesA on 2010-12-16
> **communityofexcellence said:**
> What do you mean?
Data stored in RAM is lost when power is removed.

If a CPU has some type of non-volatile memory, it's probably too small to cause any problem if it was able to be written to and that's a big if.

In any case, there shouldn't be anything to worry about. :)

---

### Post by communityofexcellence on 2010-12-16
> **CharlesA said:**
> Data stored in RAM is lost when power is removed.

If a CPU has some type of non-volatile memory, it's probably too small to cause any problem if it was able to be written to and that's a big if.

In any case, there shouldn't be anything to worry about. :)

If there was, would any os or bios even be able to be affected? How would it even start itself?

---

### Post by CharlesA on 2010-12-16
> **communityofexcellence said:**
> If there was, would any os or bios even be able to be affected? How would it even start itself?
I don't know. It's hard to figure out "what ifs" with something that could work in theory, but isn't really seen in practice.

---

### Post by communityofexcellence on 2010-12-16
So this has never occurred or even been proposed before to your knowledge? 

thank you!

---

### Post by CharlesA on 2010-12-16
If it was something that was a wide spread, there would be loads more info about it.

It's probably been proposed, probably as proof of concept, but it isn't something you need to worry about at this point in time.

---

### Post by communityofexcellence on 2010-12-16
I really wish there was more information on this. Intel's site isn't of much use either.

---

### Post by cariboo on 2010-12-16
You can always contact Intel directly, and ask your question, all the Intel devs I've ever talked to have been very helpful.

Like CharlesA said, if what you are saying is possible, we'd have already heard about it.

---

### Post by cascade9 on 2010-12-17
> **CharlesA said:**
> Data stored in RAM is lost when power is removed.

If a CPU has some type of non-volatile memory, it's probably too small to cause any problem if it was able to be written to and that's a big if.

In any case, there shouldn't be anything to worry about. :smile:

Agreed 100%. 

> **cariboo907 said:**
> You can always contact Intel directly, and ask your question, all the Intel devs I've ever talked to have been very helpful.

Like CharlesA said, if what you are saying is possible, we'd have already heard about it.

Just because it hasnt been done before doesnt make it impossible. Though I really doubt that the memory is anywhere near big enough to do much, if anything at all. 

If anybody does ask intel, I'd love to see what they say. ;)

---

### Post by cariboo on 2010-12-17
Even zero-day exploits see the light of day fairly quickly. If an exploit is doable, someone is going to publicize the fact.

---

