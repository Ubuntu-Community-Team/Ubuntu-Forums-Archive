---
title: "Wanna read/write to your Ext2/3 drive from windows?"
date: 2005-12-22
forum: The Cafe
---

### Post by MetalMusicAddict on 2005-12-22
Ive posted this link in some threads before and recieved many thanks about it so Im posting this to bring it to people who might not know.

I was hunting around awhile back and came across this; [Ext2 Installable File System For Windows]("http://www.fs-driver.org/index.html")
While it says Ext2 it works for 3 also.

[I]"Ext2 Installable File System For Windows"
"It provides Windows NT4.0/2000/XP with full access to Linux Ext2/3 volumes (read access and write access). This may be useful if you have installed both Windows and Linux as a dual boot environment on your computer."[/I]

Alot of people use FAT32 as a go between. I like this because it lets me use filesizes over 4 gigs. Which FAT32 doesnt.

Ive been using it since I found it and its been great. ;)

---

### Post by super on 2005-12-22
or if you're like me and use reiserfs on your linux box there is [this]("http://yareg.akucom.de/") program.

it doesn't look pretty, but it works!

---

### Post by BSDFreak on 2005-12-22
I wouldn't trust it further than i can throw a 1 ton brick.

Make a shared partition, never put anything on it without a backup (IE, never move it from your partition, copy it) and you'll do just fine, all of these things like Paragon to write to NTFS or these hacks to read and write to different file systems are just that, hacks, you can use them just fine until something happens that the driver doesn't know what to do with because only access was implemented, not the entirety of the file system.

---

### Post by MetalMusicAddict on 2005-12-22
Id like to find something like Ext2 IFS to do ReiserFS. Something that makes it seamless.

---

### Post by MetalMusicAddict on 2005-12-22
[QUOTE=BSDFreak]I wouldn't trust it further than i can throw a 1 ton brick.

Make a shared partition, never put anything on it without a backup (IE, never move it from your partition, copy it) and you'll do just fine, all of these things like Paragon to write to NTFS or these hacks to read and write to different file systems are just that, hacks, you can use them just fine until something happens that the driver doesn't know what to do with because only access was implemented, not the entirety of the file system.[/QUOTE]
Did you even click the link I posted? This has nothing to do with NTFS. What Ive posted *IS* about a shared partition. A Ext2/3 one.

---

### Post by BSDFreak on 2005-12-22
[QUOTE=MetalMusicAddict]Did you even click the link I posted? This has nothing to do with NTFS. What Ive posted *IS* about a shared partition. A Ext2/3 one.[/QUOTE]

Yes, and it's a hack, just like Paragon is for Linux this is a hack to make Windows read Ext2/3.

The point is that making a shared partition with a tried and true system supported by both OS's is a better choice, or even better, NAS.

---

### Post by MetalMusicAddict on 2005-12-22
Try it before you knock it. ;) Have an informed opinion. Though you are entitled to you uninformed one. 

Ive been using it 6 months on a 80gig drive and a 120gig with no problems. Just because this is "unsupported" by MS doesnt mean it will go haywire. Lot of things are written by 3rd parties that work just fine.

I will trust that this will work better than the NTFS hack because developers have access to the code. They do not for NTFS.

---

### Post by BSDFreak on 2005-12-22
[QUOTE=MetalMusicAddict]Try it before you knock it. ;) Have an informed opinion. Though you are entitled to you uninformed one. 

Ive been using it 6 months on a 80gig drive and a 120gig with no problems. Just because this is "unsupported" by MS doesnt mean it will go haywire. Lot of things are written by 3rd parties that work just fine.

I will trust that this will work better than the NTFS hack because developers have access to the code. They do not for NTFS.[/QUOTE]

It's not the first time i have looked at this solution, it's not the first time i have dismissed it, my data is more important than that, i'll spend the money on disk space rather than using a hack like this one.

That is, if i even had to, i'm sharing between Linux, FreeBSD, OpenBSD and OpenSolaris on one machine, i'm using a nas that is accesible from all of it, inexpensive, enough gigs, works as a backup and a share.

---

### Post by MetalMusicAddict on 2005-12-22
See your PMs. No need for a back and forth in the thread.

---

### Post by ember on 2005-12-22
Ext2IFS is really great, it only has two drawbacks:

1) No UTF-8 support (which breaks special characters like german umlauts)
2) Some problems with assinging drive letters to external harddisks (if you unplug them before you removed the drive letter, things get unpleasant)

Yet I decided to switch to Ext2 instead of FAT32 to share my data and it runs a lot quicker.

---

### Post by MetalMusicAddict on 2005-12-22
[QUOTE=ember]
2) Some problems with assinging drive letters to external harddisks (if you unplug them before you removed the drive letter, things get unpleasant)[/QUOTE]
This is something I tell people who want to use it with USB drives. I havnt had a problem with mine so far. For people who want to ues it read the FAQ on the site. :)

---

### Post by BSDFreak on 2005-12-22
Since this is valid to this thread i'll post it here instead.

[QUOTE=BSDFreak]It's not the first time i have looked at this solution, it's not the first time i have dismissed it, my data is more important than that, **i'll spend the money on disk space rather than using a hack like this one.**[/QUOTE]

That actually implies that you buy the driver.

> That is, if i even had to, i'm sharing between Linux, FreeBSD, OpenBSD and OpenSolaris on one machine, i'm using a nas that is accesible from all of it, inexpensive, enough gigs, works as a backup and a share.

I find it odd how someone can dismiss something without ever having used it?

NAS is nice but ive found it slower then having it *in* my server on a gigabit network. I had a Linksys NSLU2.[/QUOTE]

---

### Post by BSDFreak on 2005-12-22
> That actually implies that you buy the driver.

No it doesn't, read it again.

> I find it odd how someone can dismiss something without ever having used it?

I find it odd how someone can recommend somthing they know nothing of to be used on such a crucial thing.

> NAS is nice but ive found it slower then having it *in* my server on a gigabit network. I had a Linksys NSLU2.

Yeah, most nas's are slower than having it in your server, not everyone has the money to go out and build a server to cater to their storage needs though and shared files are commonly not very large so it shouldn't be much of a problem.

---

### Post by MetalMusicAddict on 2005-12-22
[QUOTE=BSDFreak]
I find it odd how someone can recommend somthing they know nothing of to be used on such a crucial thing.[/QUOTE]
However crucial, I can recommend it because Ive actually tried it. Successfully. For months now. People who *want* to do this should try it for themselves. Then *they* will have a better informed opinion. ;)

Fin.

---

### Post by BSDFreak on 2005-12-22
[QUOTE=MetalMusicAddict]However crucial, I can reccomend it because Ive actually tried it. Successfully. For months now. People who *want* to do this should try it for themselves. Then *they* will have an informed opinion. ;)

Fin.[/QUOTE]

Yo udo realize that it is all about opinion, i am not claiming it isn't safe or that it is safe, i am just telling you that i wouldn't trust ANY such hack with my data.

Having tried someting for a few months doesn't really allow you to have an informed opinion on the matter, not in this world. 

To me, my data is important enough to keep separate and as i said, having an in computer partition or even an in computer disk that is shared (via something both systems will write to natively) is a good solution.

---

### Post by MetalMusicAddict on 2005-12-22
> **BSDFreak]You do realize that it is all about opinion, i am not claiming it isn't safe or that it is safe, i am just telling you that i wouldn't trust ANY such hack with my data.[/QUOTE]
I do. Thats why I said it a few posts up you had that right.

Its my opinion that people here will take "hack" as a negitive connotation.

[QUOTE]Having tried someting for a few months doesn't really allow you to have an informed opinion on the matter, not in this world.[QUOTE]
Better than someone who has'nt tried it.  said:**
> To me, my data is important enough to keep separate and as i said, having an in computer partition or even an in computer disk that is shared (via something both systems will write to natively) is a good solution.
NAS isnt exactly "native" isnt there something still as a go-between like samba built into the unit. I was sure my NSLU2 used samba.

---

### Post by BSDFreak on 2005-12-22
[QUOTE=MetalMusicAddict]I do. Thats why I said it a few posts up you had that right.

Its my opinion that people here will take "hack" as a negitive connotation.


NAS isnt exactly "native" isnt there something still as a go-between like samba built into the unit. I was sure my NSLU2 used samba.[/QUOTE]

SMB short for Server Message Block, in FOSS, samba, implemented in Linux NATIVELY.

You are entering a discussion without knowledge and you will continuously learn from it if you don't assume that you know everythng because then i'll grow tired of exlaining it to you before you get it.

If that is your opinion and you do understand the implementation of SMB in Linux then anything supported by the linux kernle would be a hack in itself.

I'm sorry but before you can debate these issues you need to know what you are debating.

---

### Post by MetalMusicAddict on 2005-12-22
[QUOTE=BSDFreak]SMB short for Server Message Block, in FOSS, samba, implemented in Linux NATIVELY.

You are entering a discussion without knowledge and you will continuously learn from it if you don't assume that you know everythng because then i'll grow tired of exlaining it to you before you get it.

If that is your opinion and you do understand the implementation of SMB in Linux then anything supported by the linux kernle would be a hack in itself.

I'm sorry but before you can debate these issues you need to know what you are debating.[/QUOTE]

Ha, ha, ha. Dont you love how the internet is wonderfully non-emoting? :)

> Isnt there something still as a go-between like samba built into the unit?

A question because I was unsure/didnt know/didnt quite understand. I just missed some punctuation.

If you do want to explain it *now* take it to a PM because I feel it doesnt nessessarily pertain to the thread and it will really just be a conversation between us anyway. ;)

---

### Post by BSDFreak on 2005-12-22
[QUOTE=MetalMusicAddict]Ha, ha, ha. Dont you love how the internet is wonderfully non-emoting? :)



A question because I was unsure/didnt know/didnt quite understand. I just missed some punctuation.

If you do want to explain it *now* take it to a PM because I feel it doesnt nessessarily pertain to the thread and it will really just be a conversation between us anyway. ;)[/QUOTE]

It was raised in this thread and i think that it belongs in this thread.

You didn't miss some puctuation you CLAIMED something without knowledge, i really hate it when people do that, anyway i have already made it clear enough for everyone so no need to continue THIS discussion.

I suggest that you actually take the time to know what you are talking about before spreading more FUD, that is the last thing the FOSS community needs, we have enough MS trolls doing that as it is.

---

### Post by MetalMusicAddict on 2005-12-22
Thanx for telling **me** what I ment. ;) Its great to see us older folks developing into mindreaders and being there to not let someone do something. Like "going off the deep end" ;)
Thanx for catching me.

Ive said many times we should take this to PM. If you keep going Ill have it modded. ;)

---

### Post by detyabozhye on 2005-12-23
You guys are kinda, um, oh never mind.

I just access my data in a read-only way on both Linux and Windoze so as to be sure I don't mess anything up and I just use ext3 and NTFS.

---

### Post by MetalMusicAddict on 2005-12-23
[QUOTE=detyabozhye]You guys are kinda, um, oh never mind.[/QUOTE]
In love. :)

Use it. Dont. Whatever. Make up your mind for yourself. So far with 6 months of heavy read/write access on my 120gig Maxtor Ive had no problems. Yay me.

---

### Post by detyabozhye on 2005-12-23
[QUOTE=MetalMusicAddict]In love. :)[/QUOTE]
Ooooookaaaaay! *backs away slowly* LOL

---

### Post by exclipy on 2005-12-24
Thanks for posting this thread!  I used to have two drives for my data: a FAT32 one (D:) and an ext3 one (/home).  I was running out of space on my D: and had too much space on my /home.

I've just merged them and it's great now!  Not only do I get a lot more space to play with in Windows, I can do things like install Quake 4 in Windows and reuse most of the files for the Linux install with a few symlinks.

Of course, it also means I won't be missing my music collection when I go to Windows and I won't have to mess around with [explore2fs]("http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm") any more.

---

### Post by BSDFreak on 2005-12-25
[QUOTE=MetalMusicAddict]In love. :)

Use it. Dont. Whatever. Make up your mind for yourself. So far with 6 months of heavy read/write access on my 120gig Maxtor Ive had no problems. Yay me.[/QUOTE]

*gives MetalMusicAddict a big sloppy kiss*

I hope you won't have any problems with that in the future either, i'm just really suspicious of filesystem hacks. :)

---

### Post by MetalMusicAddict on 2005-12-25
Happy Holidays. ;)

---

### Post by BSDFreak on 2005-12-25
[QUOTE=MetalMusicAddict]Happy Holidays. ;)[/QUOTE]

Right back at ya... :D

---

### Post by exclipy on 2005-12-25
BSDFreak: I wouldn't exactly say it's a filesystem hack.  It's just an implementation of ext2 for Windows, which is just about as safe as an implementation of ext2 in Linux.

---

### Post by BSDFreak on 2005-12-27
[QUOTE=exclipy]BSDFreak: I wouldn't exactly say it's a filesystem hack.  It's just an implementation of ext2 for Windows, which is just about as safe as an implementation of ext2 in Linux.[/QUOTE]

It's an implementation of a filesystem to an OS that does not support it, it's the definition of a hack.

It's like hacking an implementation of IE6 into Linux, it's also a hack.

I forgot which user requested the updated WinHTTP though but i found a way to "implement" it into wine, you'll need to create a link so it won't check for size. Sometimes it's as easy as that.

---

### Post by &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046; on 2005-12-27
MS includes (or used to anyway) drivers to allow windows access to novell and apple partitions. Is that a hack, too?

that said, see elsewhere in this forum someone now asking for help because his machine crashed while writing to his external 120gb ext2 drive (using this tool) and has become corrupt. Was the drive bad, leading to an  indeterminate state that caused this third party kernel driver to crash windows? Or did windows crash, corrupting his ext2 filesystem in the process? It's impossible to say, but it should serve as fair warning.

Use whatever tools that provide the best value to the application - but never, ever trust your data to one hard drive. So long as you have backups any failure is recoverable.

---

### Post by Jussi Kukkonen on 2005-12-28
[QUOTE=BSDFreak]It's an implementation of a filesystem to an OS that does not support it, it's the definition of a hack.

It's like hacking an implementation of IE6 into Linux, it's also a hack.[/QUOTE]

That is an analogy so bad that I have to comment:
ext2 is essentially a specification. IE6 is not a specification, it is an implementation. Generalizing a little, ext2 is to the linux-implentation-of-ext2 what HTTP client specs are to IE6.
I realize that calling it a real specification is overstatement, but the point is that ext2 is very standardized in the sense that the linux ext2 implementation will not, and cannot be changed... 

If you are going to keep undermining ext2IFS, please do it with actual technical facts. I'd love to hear if there really is technical reason that prevents a driver-based file system from working on windows, or if you think that ext2IFS has not been tested enough, or if there is a flaw in the design of ext2IFS. 

Really, I would. I am, however, not interested in hearing "it's a hack" without any basis...

---

### Post by Blurb06 on 2011-03-13
this worked for me [http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)

---

### Post by Dustin2128 on 2011-03-13
> **Blurb06 said:**
> this worked for me [http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)
I've seen necromancy before but... 6 years... new record.

---

### Post by Quadunit404 on 2011-03-13
I agree, this has to be one of the oldest necromances I've seen.

---

### Post by CarpKing on 2011-03-13
Dead threads are like fine wine.

---

### Post by jerenept on 2011-03-13
does that work with EXT4? Last time I checked, it didn't.

---

### Post by KiwiNZ on 2011-03-14
I will drive this thread away

---

