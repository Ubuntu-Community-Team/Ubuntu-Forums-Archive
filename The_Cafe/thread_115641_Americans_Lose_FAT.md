---
title: "Americans Lose FAT"
date: 2006-01-11
forum: The Cafe
---

### Post by poofyhairguy on 2006-01-11
This is very depressing:

[http://news.com.com/Microsofts+file+system+patent+upheld/2100-1012_3-6025447.html?part=rss&tag=6025447&subj=news](http://news.com.com/Microsofts+file+system+patent+upheld/2100-1012_3-6025447.html?part=rss&tag=6025447&subj=news)
```

Two patents covering one of Microsoft's main Windows file-storage systems are valid after all, federal patent examiners have decided.

The decision, announced Tuesday by the software giant, effectively ends a two-year saga over the patents and reverses two non-final rulings--the latest issued in October--in which the U.S. Patent and Trademark Office rejected Microsoft's claims.

In their latest action, filed last week, the examiners concluded that the company's File Allocation Table (FAT) file system is, in fact, "novel and non-obvious," entitling it to patentability. Now the office is in the process of issuing a "patent re-examination certificate," which signals the finality of the decision, a Microsoft representative said.

The FAT file system, a common means of storing files, was originally developed for Windows but is also employed on removable flash memory cards used in digital cameras and other devices. Some Linux- and Unix-related products also use the system to exchange data with Windows. 
```

So....does this mean that FAT won't be the default on pen drives and iPods anymore (therefore making them read only in Linux with NTFS)?

Darn.

---

### Post by drizek on 2006-01-11
why does it seem that microsoft is so determined to make us hate them?

---

### Post by byen on 2006-01-11
[QUOTE=drizek]why does it seem that microsoft is so determined to make us hate them?[/QUOTE]
I do not think they want us to hate them..... they just dont give a damn!!! Looks like Microsoft is clearing up the battlefield for Vista to come in and just take over.

---

### Post by Kyral on 2006-01-11
They can have FAT! I'll be here cuddling with ext3 and ReiserFS :D

---

### Post by briancurtin on 2006-01-11
[QUOTE=Kyral]They can have FAT! I'll be here cuddling with ext3 and ReiserFS :D[/QUOTE]
bingo

screw FAT anyways

---

### Post by Iandefor on 2006-01-11
Poofy: Ipods come formatted with HFS, not FAT. Just a minor correction.

---

### Post by prizrak on 2006-01-11
[QUOTE=Kyral]They can have FAT! I'll be here cuddling with ext3 and ReiserFS :D[/QUOTE]
Ahh but see then we would have issues with Flash media for Linux. You know that the manufacturers won't switch to ext2 (not much point in journaling on those drives) since Windows doesn't support it (and never will). MS will just license it under favorable pricing that wouldn't raise the price of the end product high enough to affect the consumer. This happened with the MP3 format before. I really hope that it doesn't go that way and that the flash manufacturers come together in a consortium to either adopt one of the open FS's or develop their own. If all or at the very least the biggest manufacturers do that MS will be forced to include the driver by default.
They can have my fat tho, I don't need it :)

---

### Post by adriantry on 2006-01-11
[QUOTE=Iandefor]Poofy: Ipods come formatted with HFS, not FAT. Just a minor correction.[/QUOTE]

iPods that sync with Macs are formatted with HFS.

iPods that sync with Windows or Linux are formatted with FAT32.

---

### Post by BoyOfDestiny on 2006-01-11
A relevant link

**3 Initiatives to Improve the Patent Mess Announced - Updated**

[http://www.groklaw.net/article.php?story=2006011009141979](http://www.groklaw.net/article.php?story=2006011009141979)


A small excerpt:

"Microsoft has won a debate where they were the only party allowed to speak, in that the patent re-examination process bars the public from rebutting arguments made by Microsoft," he told CNET News.com. "We still believe these patents are invalid and that a process that gave the public equal time to present its positions would result in them being found as such."

---

### Post by Iandefor on 2006-01-11
[quote=adriantry]iPods that sync with Macs are formatted with HFS.

iPods that sync with Windows or Linux are formatted with FAT32.[/quote] The default formatting is HFS. Oh, and My Ipod, which I use with my Linux box, is formatted with HFS. There are packages which let you deal with with HFS in POSIX-Compliant systems. There are a few available in the repo's. Search for hfs.

---

### Post by Breepee on 2006-01-11
Saying that this doesn't matter is stupid; it obviously not only affects your possible FAT partition for compatibility with Windows, or unified storage; pretty much all digital audio players (e.g. MP3 players) and flashcards for your phone/camera/whatever use FAT.

This is not good.

---

### Post by nocturn on 2006-01-11
The fact that they have the patents does not mean anything yet.

If I'm correct, the patent is not valid because their is prior art?  So, it will never hold up in real life.

---

### Post by prizrak on 2006-01-11
[QUOTE=nocturn]The fact that they have the patents does not mean anything yet.

If I'm correct, the patent is not valid because their is prior art?  So, it will never hold up in real life.[/QUOTE]
No that's not it. The point is that the patent IS valid, they confirmed MS to have the right to the patent and that it was in fact a new technology with no prior art.

---

### Post by gord on 2006-01-11
does this cover all implimentations of fat though? theres FAT, VFAT and FAT32 as far as i know.

sometimes the advantage of living somewhere, where software patents don't exsist is ruined by america's dominence of the market...

---

### Post by nocturn on 2006-01-11
[QUOTE=prizrak]No that's not it. The point is that the patent IS valid, they confirmed MS to have the right to the patent and that it was in fact a new technology with no prior art.[/QUOTE]

Yes, but MS was the only one allowed to speak.  So nobody could offer facts that prove the opposite.

The question is if this patent will hold up in court when the other party has a right to present evidence too...

---

### Post by prizrak on 2006-01-11
[QUOTE=nocturn]Yes, but MS was the only one allowed to speak.  So nobody could offer facts that prove the opposite.

The question is if this patent will hold up in court when the other party has a right to present evidence too...[/QUOTE]
I sincerely hope that it does not. We all know MS however they got everyone bought.

---

### Post by rpgcyco on 2006-01-11
[QUOTE=Kyral]They can have FAT! I'll be here cuddling with ext3 and ReiserFS :D[/QUOTE]

Indeedly. :) I switched my small 5GB partition that I use to share files with Windows to ext3 just the other day. I use the ext2 file system driver for Windows from [here](http://www.fs-driver.org/) to access it. Nothing important is on there, so if the driver is unstable it won't cause any damage.

- Rpg Cyco

---

### Post by ssam on 2006-01-11
[QUOTE=rpgcyco]Indeedly. :) I switched my small 5GB partition that I use to share files with Windows to ext3 just the other day. I use the ext2 file system driver for Windows from [here](http://www.fs-driver.org/) to access it. Nothing important is on there, so if the driver is unstable it won't cause any damage.

- Rpg Cyco[/QUOTE]

it could run deeper than whether linux can mount FAT partitions. I dont think you could dual boot if GRUB could not read FAT partitions.

---

### Post by Miguel on 2006-01-11
I suppose this means we no longer get FAT support out of the box, right? We should need to either get a kernel from multiverse or compile it ourselves, shouldn't we?

I mean, MP3 support is on multiverse because MP3 is patented. Playing DVDs in linux with libdvdcss (installed manually or via Marillat) is also illegal in the US as far as I know (DMCA?). So for my untrained eye this fat issue seems similar. Great. What about pens? What about portable media players? What about digital cameras? What about sharing files between OSes? I would think this can have some very serius consecuences (sp?) in the FOSS world.

Just imagine a newbie asking how to share files between windows and linux. What will be the answer? 

*If you are not from the U.S. recompile the kernel with full FAT32 support. If you are in the U.S., this is illega*

I'm closer and closer to say goodbye to my gaming alter ego and dump windows forever. For the sake of convenience.

---

### Post by UbunT00L on 2006-01-11
Couldn't hardware manufacturers just start using UDF instead of FAT for cameras/mp3 players/usb storage devices/etc???  Don't some already do this?

---

### Post by Stormy Eyes on 2006-01-11
[QUOTE=adriantry]iPods that sync with Windows or Linux are formatted with FAT32.[/QUOTE]

The kernel can be built with HFS support, thus allowing Linux to use iPods formatted to sync with Macintosh.

---

### Post by nocturn on 2006-01-11
[QUOTE=UbunT00L]Couldn't hardware manufacturers just start using UDF instead of FAT for cameras/mp3 players/usb storage devices/etc???  Don't some already do this?[/QUOTE]

The could and why they ever choose FAT is beyond me...

---

### Post by Arktis on 2006-01-11
Because as far as I know, you can read and write to FAT on basicly everything.  I'm pretty sure that there's no other file system you can say this about.

---

### Post by UbunT00L on 2006-01-11
Don't Linux Macs and Windows all have read/write support built in for UDF?

---

### Post by Arktis on 2006-01-11
I think that's only for CD's.  Also I remember making some cd's for a friend of mine who only uses some form of bsd, and I made sure that they were in UDF.  He couldn't read them.  Doh!

---

### Post by towsonu2003 on 2006-01-11
from what I understand, Dapper just lost its newbie base... Hmm, more developers for portable ext2/3 drivers of Windows...

Anyway, it was about time to move free software OUT of the U.S...

Edit: Very adequate title selection ("Americans Lose FAT" instead of "FAT32 not available to Linux anymore") in order not to "scare" off newbies away to Windows VISTA... [After 40 minutes of silence] See, no body cared ;) change the name to what I suggested and you'll have a widespread panic in your hands :P

---

### Post by prizrak on 2006-01-11
[QUOTE=towsonu2003]from what I understand, Dapper just lost its newbie base... Hmm, more developers for portable ext2/3 drivers of Windows...

Anyway, it was about time to move free software OUT of the U.S...

Edit: Very adequate title selection ("Americans Lose FAT" instead of "FAT32 not available to Linux anymore") in order not to "scare" off newbies away to Windows VISTA... [After 40 minutes of silence] See, no body cared ;) change the name to what I suggested and you'll have a widespread panic in your hands :P[/QUOTE]
Ubuntu is not based in the US :)

---

### Post by poofyhairguy on 2006-01-11
[QUOTE=towsonu2003]
Edit: Very adequate title selection ("Americans Lose FAT" instead of "FAT32 not available to Linux anymore") in order not to "scare" off newbies away to Windows VISTA... [After 40 minutes of silence] See, no body cared ;) change the name to what I suggested and you'll have a widespread panic in your hands :P[/QUOTE]

Thanks.

---

### Post by Zensunni on 2006-01-12
Hold the phone...

This won't affect things like samba, or anything that communicates with FAT systems, will it?

---

### Post by BSDFreak on 2006-01-12
[quote=Zensunni]Hold the phone...

This won't affect things like samba, or anything that communicates with FAT systems, will it?[/quote]

Samba doesn't care about the file system the share lives on.

From what I can tell the patents only affect long filenames, if there were any patents on FAT itself they're way past expired.

---

### Post by nocturn on 2006-01-12
[QUOTE=BSDFreak]Samba doesn't care about the file system the share lives on.

From what I can tell the patents only affect long filenames, if there were any patents on FAT itself they're way past expired.[/QUOTE]

So the patent applies only to Vfat?  I really thought this one had prior art....

---

### Post by BSDFreak on 2006-01-12
[quote=nocturn]So the patent applies only to Vfat?  I really thought this one had prior art....[/quote] 
It does and if it's ever challenged MS would lose, this hearing only involved MS so there was no opposing side presenting a case which is why it went the way it went.

However, few will want to base anything upon a technology that may be attacked should MS decide they want royalties for it.

Remember that this isn't a new patent, MS probably has a plan to introduce something new, that's why this is happening now.

---

### Post by UbunT00L on 2006-01-12
I have a bad feeling that microsoft will play this to their advantage, like telling all DMP manufacturers that if they include WMA/WMV support, and disclude support for open source codecs like ogg/flac/xvid then they will drop their FAT charge.

---

### Post by newuser111 on 2006-01-12
[QUOTE=prizrak]Ahh but see then we would have issues with Flash media for Linux. You know that the manufacturers won't switch to ext2 (not much point in journaling on those drives) since Windows doesn't support it (and never will). MS will just license it under favorable pricing that wouldn't raise the price of the end product high enough to affect the consumer. This happened with the MP3 format before. I really hope that it doesn't go that way and that the flash manufacturers come together in a consortium to either adopt one of the open FS's or develop their own. If all or at the very least the biggest manufacturers do that MS will be forced to include the driver by default.
They can have my fat tho, I don't need it :)[/QUOTE]

ext2 doesnt have journaling, ext3 does

ext2/ext3 read/write support can be added to windows with free drivers, but yes not supported out of the box

---

### Post by nocturn on 2006-01-12
[QUOTE=UbunT00L]I have a bad feeling that microsoft will play this to their advantage, like telling all DMP manufacturers that if they include WMA/WMV support, and disclude support for open source codecs like ogg/flac/xvid then they will drop their FAT charge.[/QUOTE]

I more or less think they will attempt to get vfat kicked out of the Linux kernel at some point...  which would break much of our support for multimedia players/digital cameras etc.

---

### Post by Miguel on 2006-01-12
Where is the kernel based?

AFAIK Linus is currently living in the US. So it would be illegal for him to support fat in the kernel out of the box... but it shouldn't be illegal for any non-american (from the US) distro to include FAT support in the kernel.

ANd yes, the main trouble for us lies in the ability to interoperate with external media. I was reading some web yesterday about M$ practices that irked me a lot. You know, after some time, people relax. 

It will be funny when I attend a conference at the GRC on Reserch at High Pressure in Maine this summer. I will be a fugitive. A laptop full of forbidden content.

FAT
SSH
libdvdcss
LAME
...

I am a bad boy

---

### Post by nocturn on 2006-01-12
[QUOTE=Miguel]Where is the kernel based?

AFAIK Linus is currently living in the US. So it would be illegal for him to support fat in the kernel out of the box... but it shouldn't be illegal for any non-american (from the US) distro to include FAT support in the kernel.
[/QUOTE]

Yes, it would when you also distribute it in America.  This was one of the scary parts of the Sklyarov case.

If Ubuntu would not be shipped to the US and there was a filter preventing downloads, then it would be OK, but not very practical.

---

### Post by Miguel on 2006-01-12
So Canonical is guilty for, let's say, George W. Bush choosing freely to download Ubuntu?

Following that logic, if I see a jewelry showcasing an enormous diamond and I steal it... the jewelry is guilty because it was showcasing the diamond!!! I know why I chose physics over law. I have a simple mind.

---

### Post by prizrak on 2006-01-12
[QUOTE=newuser111]ext2 doesnt have journaling, ext3 does

ext2/ext3 read/write support can be added to windows with free drivers, but yes not supported out of the box[/QUOTE]
I never said that ext2 was a journaling FS. You misunderstood what I was saying I was saying that if they would switch to a free FS the one that makes sense would be ext2fs since journaling is useless on flash media. 
I know that you can add support for free file systems, because you know they are free and stuff. MS will NEVER do that (unless the main manufacturers get together and tell them that they are gonna all switch to ext2). Those who know how to get ext2 on Windows most likely don't run Windows for more than gaming anyways :)

---

### Post by BSDFreak on 2006-01-12
[quote=Miguel]So Canonical is guilty for, let's say, George W. Bush choosing freely to download Ubuntu?

Following that logic, if I see a jewelry showcasing an enormous diamond and I steal it... the jewelry is guilty because it was showcasing the diamond!!! I know why I chose physics over law. I have a simple mind.[/quote]

No, a much better example would be drugs that are permitted in one country but not in another, it would be illegal to get the drugs there and it would be illegal to provide the drugs there.

Your example would work better for hacking crimes. (stealing private information)

---

### Post by nocturn on 2006-01-13
[QUOTE=Miguel]So Canonical is guilty for, let's say, George W. Bush choosing freely to download Ubuntu?

Following that logic, if I see a jewelry showcasing an enormous diamond and I steal it... the jewelry is guilty because it was showcasing the diamond!!! I know why I chose physics over law. I have a simple mind.[/QUOTE]

I know, it sounds silly.  But this is what happened to Dimitri Sklyarov a couple of years back.
[http://en.wikipedia.org/wiki/Dmitri_Sklyarov](http://en.wikipedia.org/wiki/Dmitri_Sklyarov)

He created a program to decode Adobe Ebooks (he wrote this for his employer, Elcomsoft).  The main goal was to open the format for multiple uses, including screenreading them to blind people.

None of this was illegal in Russia (where he and the company resided), nor would it be illegal in most surrounding countries.

When Sklyarov travelled to the US to speak at a conference, he was taken down by *armed* officers in an uneeded show of force and arrested under the terms of the DMCA.  

It took a lot of effort on the end of the international community and several organisations like the EFF to get him released (protest based on the fact that he had not commit any crime on US ground and his acts were completely legal in his own country).  

He was held in the US for several months before being released.

So, to answer your question: Yes

---

