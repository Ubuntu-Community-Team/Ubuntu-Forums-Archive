---
title: "Scary Messages"
date: 2009-11-26
forum: Testimonials &amp; Experiences
---

### Post by scottuss on 2009-11-26
Hi everyone! I wanted to start this thread purely out of curiosity. As an advocate of Free software (particularly Ubuntu to "regular Joe" computer users) I wanted to find out what error messages you all think might scare beginners away. I don't want to know about issues and differences between Ubuntu and Windows, there are millions of threads about that.

What I'm focussing on here is the various error / warning messages that Ubuntu can throw up in every day use that would make a Windows user (read: new Ubuntu user) to panic and think Ubuntu is too complicated or for geeks only.

I'll start:

I have a portable USB hard disk, formatted as an NTFS drive (I have a good reason for this) and after not correctly unmounting it on my partner's Mac, I find the following error when plugging it into my Ubuntu box:

Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdf1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

Firstly: It makes little sense to a non-geek.
Secondly: It mentions using Windows to fix the error. Um... I tried so hard to convince my new user they don't need Windows and now the very software I recommended is telling them a different story...


So, let's see 'em!

P.S - to clarify for those people who skim-read: **I don't need assistance or help, I'm a techie and can fix this issue :)**

---

### Post by cariboo on 2009-11-26
Most Windows error messages don't make sense to new users either. NTFS is a windows file system, it is not native to linux, how else would expect to fix it. What kind of error message do you get when you connect to the Mac?

---

### Post by jdrodrig on 2009-11-26
I think you touch a very important thing; consistency in the way packages or software pieces report messages....

I guess, at some point in the development process there are requirements to provide help files or at least some informative error messages in order to be included in the next distributions...

---

### Post by scottuss on 2009-11-26
> **cariboo907 said:**
> Most Windows error messages don't make sense to new users either. NTFS is a windows file system, it is not native to linux, how else would expect to fix it. What kind of error message do you get when you connect to the Mac?

I never said Windows errors make sense, I just feel Ubuntu ones could be less scary. I nevercompared Ubuntu to Windows! :-) and the Mac doesn't complain. It mounts the drive without issue.

I appreciate NTFS is a Windows filesystem but that's no excuse for scary error messages.

---

### Post by coffeecat on 2009-11-26
I'm curious....

> **scottuss said:**
> I have a portable USB hard disk, formatted as an NTFS drive (I have a good reason for this) and after not correctly unmounting it on my partner's Mac, I find the following error when plugging it into my Ubuntu box:

> **scottuss said:**
> and the Mac doesn't complain. It mounts the drive without issue.

Which Mac driver are you using, the inbuilt read-only Mac one, or the read-write ntfs-3g for MacOS one? Either way, do you believe the Mac which is not complaining or the more-developed Ubuntu ntfs-3g driver which is complaining? :wink:

But I'll keep a lookout for scary error messages for you. Interesting thread idea. Thanks.

---

### Post by Methuselah on 2009-11-26
There is nothing scarier than 'Your program has performed an illegal operation' to people unaccustomed to PCs.

---

### Post by lisati on 2009-11-26
> **Methuselah said:**
> There is nothing scarier than 'Your program has performed an illegal operation' to people unaccustomed to PCs.

Gets one thinking about the pending arrival of the computer police! 
<aside>Back in the days when I used IBM mainframes, an equivalent error message, usually accompanied by a core dump that meant nothing to the typical user, referred to a "mysterious" thing called an "Abend S0C1" (i.e. invalid/illegal operation). A common cause was a program's user forgetting to include the job control statement that let the OS associate a file stream used by a program with a real file. The silly thing is that for many ASM programs there was a simple way of avoiding this by using two lines of ASM code to jump to a "die gracefully" routine when a file didn't open correctly. (And no, I never worked out the equivalent in COBOL, which is the language some of my colleagues used)</aside>

---

### Post by cariboo on 2009-11-26
I guess I should have put a smiley :) in my other post in this thread.

What I was getting at is, error messages are scary no matter what operating system a new user is using. Running windows, unless the computer locks up most users just ignore any error messages. The error messages you get while running Ubuntu. will make most users sit up and start paying attention.

---

### Post by scottuss on 2009-11-27
> **coffeecat said:**
> I'm curious....


Which Mac driver are you using, the inbuilt read-only Mac one, or the read-write ntfs-3g for MacOS one? Either way, do you believe the Mac which is not complaining or the more-developed Ubuntu ntfs-3g driver which is complaining? :wink:

But I'll keep a lookout for scary error messages for you. Interesting thread idea. Thanks.

I'd have to check that, but all I can say at the moment is, the Mac can read and write to the drive without any issue, but Ubuntu complained about it. I'm not saying I wouldn't want to be warned of possible inconsistency, but there's something to be said for a less scary error message.

As I'm the one who made the "complaint" I'll suggest an alternative:

"The hard disk you have just plugged in was not correctly removed from the computer when it was last used. Because of this, unfortunately, Ubuntu could not make the disk available for use. To fix this error, please press the Fix button or press More Information.

The fix button could be a link to a how-to on the Wiki, a script or whatever.

The general population don't need to know that they're using a flaky driver built from guess work because of a closed source proprietary filesystem, they don't care! They want the drive to work, and if it can't (we know why) they need to be told how to fix it in Plain English (or Plain whatever language) rather than what looks to be verbatim output from the filesystem.

Just thinking of the newbies here  :P

---

### Post by SlugSlug on 2009-11-27
pretty sure you can get round this by forcing a fsck

---

### Post by Hamchan on 2009-11-27
I had the same problem last night. fsck wouldn't work, but ntfsfix would. It's part of ntfsprogs.

---

### Post by coffeecat on 2009-11-27
[COLOR=red]Off-topic alert!!![/COLOR] This thread is about scary error messages, not how to repair NTFS drives. :wink: (Slaps own wrist for bringing up topic of MacOS NTFS drivers.)

> **scottuss said:**
> "The hard disk you have just plugged in was not correctly removed from the computer when it was last used. Because of this, unfortunately, Ubuntu could not make the disk available for use. To fix this error, please press the Fix button or press More Information.

Nice - but it will be an uphill task to get some devs to be that polite! :p

---

### Post by Hamchan on 2009-11-27
Messages really stop being so scary when you figure out that it is easy to copy the error message into a google search and find someone that has already had and solved the problem. The error messages that linux spits out at least give some clue as to what is wrong, even if they may contain some language many would consider gibberish.

---

### Post by scottuss on 2009-11-27
> **Hamchan said:**
> Messages really stop being so scary when you figure out that it is easy to copy the error message into a google search and find someone that has already had and solved the problem. The error messages that linux spits out at least give some clue as to what is wrong, even if they may contain some language many would consider gibberish.

Absolutely, and I would imagine software error messages are one of the most common things "Googled" but making them easier to understand with direct links to help would make new users making the switch feel much more at ease.

The problem Ubuntu has (slightly off topic rant here) is that Canonical and the community seem to be pushing ideas (a lot of them pointless) such as the on screen notification eye candy added in 8.10. We could have done with a more seamless setup, better audio and a myriad of other improvements that new users would appreciate. Instead we got eye candy. I'm not having a go, I'm just saying Ubuntu is touted as "for human beings" but at the moment, it's got a long way to go and it's not getting there too quickly.

---

