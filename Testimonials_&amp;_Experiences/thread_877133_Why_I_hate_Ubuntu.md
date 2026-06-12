---
title: "Why I hate Ubuntu"
date: 2008-08-01
forum: Testimonials &amp; Experiences
---

### Post by skaufman on 2008-08-01
Maybe this will be considered a flame, but sorry, I'm disgusted.   I dual-booted my first system maybe 15 years ago.  While I've never been great as a system administrator on Linux, I have installed it several times and used it.  I have NEVER encountered a Linux flavor that is so prone not to install as ubuntu, and I am getting awfully tired of this nonsense.  I could live with its refusal to resize an NTFS partition.  I did that manually with gparted.  I forgave it for spending hours checking and formatting partitions that I had just created with gparted.  OK.  I even was willing to use bootitng as a boot loader when it seemed that grub wasn't properly installing.

But when I finally decided to give a bunch of unallocated space to ubuntu's installer and let it handle everything automatically, it is unforgivable that it could not create a system correctly and update a boot loader.

Oh, and a fellow with enough importance to have a sticky, Sef, didn't even bother to reply to my query.

I'm appalled.

---

### Post by Pumalite on 2008-08-01
Probably human error.

---

### Post by meindian523 on 2008-08-01
and Private Support is NOT done.Mods,please move this to the experiences section.

---

### Post by skaufman on 2008-08-01
Yes, the error in the designers of the install program, who failed to create a robust installer.  Perhaps they thought that someone with a Dell Precision 690 (running x64) with five SATA hard drives (3 RAIDED) would never think of installing this flavor of Linux.

So I called Novell, and I was told that I can get a year of phone support for suse enterprise desktop for $120.  I won't need to deal with overwhelming indifference or snidely unhelpful comments in the future.

Oddly, I have participated in Perl and Emacs groups, contributing and being helped in both.  The attitude was much different.

Enough.

---

### Post by Pumalite on 2008-08-01
Bitterness harms the soul

---

### Post by skaufman on 2008-08-01
"And private support is not done."

OH, I get it.  So my original query under "Main Support Categories>Installation & Upgrades" is considered "private support" and is not done in a support forum.

I am convinced that the only reason ubuntu is so known is that it is so waaaay PC.

Blah!  Give me Slackware over this!

---

### Post by Pumalite on 2008-08-01
Troll on sight

---

### Post by skaufman on 2008-08-01
Pumalite, you're right.  I'll get out of my registration as fast as I can type.

---

### Post by skaufman on 2008-08-01
Correct that, Pumalite.  I thought you were a decent fellow.  Obviously, you're unable to distinguish between a very, very frustrated user and a troll.

---

### Post by meindian523 on 2008-08-01
> **skaufman said:**
> "And private support is not done."

OH, I get it.  So my original query under "Main Support Categories>Installation & Upgrades" is considered "private support" and is not done in a support forum.

I am convinced that the only reason ubuntu is so known is that it is so waaaay PC.

Blah!  Give me Slackware over this!
Go ahead with slackware.And I ony said Private Support because you mentioned Sef by name,hope you know that all members of this forum cannot keep track of what new thread were started where and by whom.

---

### Post by skaufman on 2008-08-01
Oh, well it seems you jumped to a conclusion.

It seems that the link in the email that told me my password also says I can get out of this forum via the link associate with:

To stop receiving this email, please visit this URL:

So, I'll make everyone happy by implementing this (mislabeled) advice.

The mods can feel free to move this thread to the "bad experiences" area of the forum.  This will have the added desirable effect of making sure that those who are pissed off are safely out of the sight of those who don't care.

---

### Post by skaufman on 2008-08-01
So, I can't even get out of this place with that link.

Frustration piled on top of frustration.

---

### Post by Arthur Archnix on 2008-08-01
[IMG]http://www.forumspile.com/Thread-I_like_where_this_thread_is_going.jpg[/IMG]
/hotlinked, for your pleasure

---

### Post by rbstern on 2008-08-01
I have to admit sympathy for the OP.

Having done a few painless Linux installs in years past, and having been away from hands on Linux installs more recently, I was very enthusiastic to find Ubuntu and all of the positive marketing on the Ubuntu site.

Now, having spent many hours trying to get around a simple install problem on brand new hardware, I'm reminded of the days of Windows 95/plug-and-play, when Microsoft told us it would be good and we'd love it.  And we didn't.

So, I sit here, looking at my failed Ubuntu install, the screen cursor mindless winking at me, machine frozen, wondering whence I shall go.  Perhaps back to CentOS.

---

### Post by confused57 on 2008-08-01
> **skaufman said:**
> Maybe this will be considered a flame, but sorry, I'm disgusted.   I dual-booted my first system maybe 15 years ago.  While I've never been great as a system administrator on Linux, I have installed it several times and used it.  I have NEVER encountered a Linux flavor that is so prone not to install as ubuntu, and I am getting awfully tired of this nonsense.  I could live with its refusal to resize an NTFS partition.  I did that manually with gparted.  I forgave it for spending hours checking and formatting partitions that I had just created with gparted.  OK.  I even was willing to use bootitng as a boot loader when it seemed that grub wasn't properly installing.

But when I finally decided to give a bunch of unallocated space to ubuntu's installer and let it handle everything automatically, it is unforgivable that it could not create a system correctly and update a boot loader.

Oh, and a fellow with enough importance to have a sticky, Sef, didn't even bother to reply to my query.

I'm appalled.

The Ubuntu installer won't resize a NTFS partition, if it is highly fragmented, which "may" have been the case.  As far as grub's bootloader, it may have been installed to the mbr of a different drive.

I may be wasting my time, but try selecting the "Manual" partitioning option, click on the unallocated space or partition that you want to install Ubuntu on...you'll need to delete if it's already a formatted partition.  You'll need a root partition at least 10 Gb...format ext3, mountpoint / , logical(or primary...I would personally select logical or extended).  You probably don't need a swap partition with 16 Gb of ram.  Make a note of how the partitioner or installer recognizes the drive you're installing Ubuntu to(sda, sdb, sdc, etc).  Near the end of the install, click on the "Advanced" button in the lower right...change the default (hd0) to /dev/sdx(or however the drive is designated) as the location to install grub's IPL.  Set your bios to boot first to this drive, if you get a grub boot menu, highlight the first Ubuntu entry, press "e", highlight the line with root, press "e" again, change root from (hdx,y) to (hd0,y), press "enter", then "b" to boot.
This is temporary, but you can make it permanent.

You probably won't be able to install Ubuntu to a drive that's configured as part of a Raid array.

---

### Post by wootah on 2008-08-01
I'm going to agree with rbstern with sympathy for the OP after the server edition (7.10) wiped out my friend's 1.5TB RAID'd server machine *somehow*.

To the people: "oh it's not Ubuntu's fault it must be user error", simply: no. The installer needs more attention and still more work done on it. For me personally, I have never had a problem at all, but these very serious fringe cases need to be ironed out fast. The install I did on my dual boot machine, was a NTFS resize which work fine. No problems what-so-ever.

GRUB being broken? That is very odd though.

More work to do :) Time for some contributions.

---

### Post by Arthur Archnix on 2008-08-01
Wow... I'm surprised to find you commenting on this thread wootah, after having that particular thread linked to in your sig.

---

### Post by tamoneya on 2008-08-01
you didnt seem to give your thread much of a chance before discounting ubuntu.  You didnt really even try to work with the one person who tried to help you.

---

### Post by cyclouno on 2008-08-01
@Arthur Archnix
That was picture perfect !!

@rbstern / @skufman
ha ha.. it's wicked funny when people who claim to be frustrated find time to take time & bit#h back.. 

Just sharing a funny comment here.. [no offence]

you can ask for direction if a road splits into 2.. if some1 guided u in the wrong direction.. you can bit#h about the former.. but what when there ain't a road at all !! [ no one gives a hoot :) ]

---

### Post by Rocket2DMn on 2008-08-01
Moved to Ubuntu Testimonials & Experiences

---

### Post by Methuselah on 2008-08-01
> 
You probably won't be able to install Ubuntu to a drive that's configured as part of a Raid array.


funny, that's exactly what i did months ago.
i do have true hardware raid though and
a non-crappy gigabyte motherboard.

---

### Post by confused57 on 2008-08-01
> **Methuselah said:**
> funny, that's exactly what i did months ago.
i do have true hardware raid though and
a non-crappy gigabyte motherboard.
Hey Old Man,
   That's good to know that it can be done, it may be the software raid that is problematic...usually drives that are part of a Raid array are recognized as separate drives & grub has trouble booting Windows if grub's IPL is installed to the mbr of the 1st (or boot) drive of the array.  Maybe you can describe to the OP how your system is set up & how you installed Ubuntu on the Raid.

---

### Post by Arthur Archnix on 2008-08-01
> **confused57 said:**
> Maybe you can describe to the OP how your system is set up & how you installed Ubuntu on the Raid.

Why? Did the OP ask a question?

---

### Post by confused57 on 2008-08-01
> **Arthur Archnix said:**
> Why? Did the OP ask a question?
I stand corrected, not in this thread, but here:
[http://ubuntuforums.org/showthread.php?t=873791](http://ubuntuforums.org/showthread.php?t=873791)

---

### Post by kspncr on 2008-08-01
Why I hate these posts

They do nothing. They stir up negative feelings to no positive effect. If you don't like Ubuntu, fine, why not just be on your way? Why sit here and say Ubuntu sucks? We on the forums like Ubuntu, you're not going to change our minds because you couldn't get it to work.

> **skaufman said:**
> Oh, and a fellow with enough importance to have a sticky, Sef, didn't even bother to reply to my query.

I'm appalled.
Where did it say he had to? Maybe your problem isn't the focus of his life. We don't get paid to help people, we do it in our *spare* time because we like to see people happy that their system's working. It's not working with you, so...maybe you should demand a refund.

See what I mean? Stirred up more negative feelings, sorry everyone, for getting caught up in it. I, too, am appalled.

---

### Post by aysiu on 2008-08-01
So anyone who has a sticky must be omnipresent on the forums and answer every single support thread; otherwise, you're appalled? I don't know where you get this unrealistic sense of entitlement from.

---

### Post by bmac on 2008-08-01
[[COLOR=#D40000]**aysiu**[/COLOR]]("http://ubuntuforums.org/member.php?u=21941")

> So anyone who has a sticky must be omnipresent on the forums and answer every single support thread; otherwise, you're appalled? I don't know where you get this unrealistic sense of entitlement from.

Excellent response. Unfortunately, I think the OP scampered off about three hours ago....
[[COLOR=#D40000]**](*,)**[/COLOR]]("http://ubuntuforums.org/member.php?u=21941")

---

### Post by Methuselah on 2008-08-01
> **confused57 said:**
> **Hey Old Man**,
   That's good to know that it can be done, it may be the software raid that is problematic...usually drives that are part of a Raid array are recognized as separate drives & grub has trouble booting Windows if grub's IPL is installed to the mbr of the 1st (or boot) drive of the array.  Maybe you can describe to the OP how your system is set up & how you installed Ubuntu on the Raid.

lol...funny thing is that i was born in the 1980s yet i chose the name of the oldest man when i was signing up.
i have an old computer named that and i was using it at the time. :)

---

### Post by confused57 on 2008-08-01
> **Methuselah said:**
> lol...funny thing is that i was born in the 1980s yet i chose the name of the oldest man when i was signing up.
i have an old computer named that and i was using it at the time. :)
Hi Methuselah,
   Good to know my reference to "Old Man" wasn't wasted.  The OP has probably already installed Slackware, Gentoo, & LSF and wouldn't be back to read any helpful advice anyone had for him.
I was mainly interested in your setup, because I've read of so many people having problems installing to a Raid configuration without having a drive separate from the Raid drives.  I know the forum is for people posting for assistance with their problems with Ubuntu and the majority may actually not have any trouble with Raid & Ubuntu.

Thanks

---

### Post by meindian523 on 2008-08-02
> **aysiu said:**
> So anyone who has a sticky must be omnipresent on the forums and answer every single support thread; otherwise, you're appalled? I don't know where you get this unrealistic sense of entitlement from.
Beautiful response.:cool::lolflag:

And @OP
7 posts don't make a solved issue.Patience is a virtue you obviously haven't learnt.

---

### Post by Canis familiaris on 2008-08-02
> **aysiu said:**
> So anyone who has a sticky must be omnipresent on the forums and answer every single support thread; otherwise, you're appalled? I don't know where you get this unrealistic sense of entitlement from.

Well said

---

### Post by collinp on 2008-08-02
[img]http://media.g4tv.com/images/blog/2008/01/10/633355760324563016.jpg[/img]

Lol i just had to do that...

---

### Post by hyper_ch on 2008-08-04
> **wootah said:**
>  The installer needs more attention and still more work done on it.

What do you mean by that?

---

### Post by MongooseCage on 2008-08-04
> **skaufman said:**
> "And private support is not done."

OH, I get it.  So my original query under "Main Support Categories>Installation & Upgrades" is considered "private support" and is not done in a support forum.

I am convinced that the only reason ubuntu is so known is that it is so waaaay PC.

Blah!  Give me Slackware over this!

I tried Slackware. I gave it quite a bit of my time... realized that I wasn't manly enough to do the entire networking configuration myself nor compile everything by source from slackbuilds(great thanks to them) because installing RPMs were full of dependency issues.

In the end it turned out like a learning experience. I ended up not fearing the command line as much. Though yes, I love that they let you choose where things go. Feels more simple but I couldn't deny I wasn't being as productive.

---

### Post by KoreanMadness on 2008-08-04
> **skaufman said:**
> Maybe this will be considered a flame, but sorry, I'm disgusted.   I dual-booted my first system maybe 15 years ago.  While I've never been great as a system administrator on Linux, I have installed it several times and used it.  I have NEVER encountered a Linux flavor that is so prone not to install as ubuntu, and I am getting awfully tired of this nonsense.  I could live with its refusal to resize an NTFS partition.  I did that manually with gparted.  I forgave it for spending hours checking and formatting partitions that I had just created with gparted.  OK.  I even was willing to use bootitng as a boot loader when it seemed that grub wasn't properly installing.

But when I finally decided to give a bunch of unallocated space to ubuntu's installer and let it handle everything automatically, it is unforgivable that it could not create a system correctly and update a boot loader.

Oh, and a fellow with enough importance to have a sticky, Sef, didn't even bother to reply to my query.

I'm appalled.

I am a new Ubuntu user. I thought the Ubuntu install was the easiest OS install I have ever done.

---

### Post by wolfen69 on 2008-08-04
> **skaufman said:**
> 
Blah!  Give me Slackware over this!

then use slackware. or better yet, vista. bye.

---

### Post by caravel on 2008-08-04
> **skaufman said:**
> Maybe this will be considered a flame, but sorry, I'm disgusted.   I dual-booted my first system maybe 15 years ago.  While I've never been great as a system administrator on Linux, I have installed it several times and used it.  I have NEVER encountered a Linux flavor that is so prone not to install as ubuntu, and I am getting awfully tired of this nonsense.  I could live with its refusal to resize an NTFS partition.  I did that manually with gparted.  I forgave it for spending hours checking and formatting partitions that I had just created with gparted.  OK.  I even was willing to use bootitng as a boot loader when it seemed that grub wasn't properly installing.

But when I finally decided to give a bunch of unallocated space to ubuntu's installer and let it handle everything automatically, it is unforgivable that it could not create a system correctly and update a boot loader.

Oh, and a fellow with enough importance to have a sticky, Sef, didn't even bother to reply to my query.

I'm appalled.
So you're disappointed by how the OS accommodates and tries to coexist with Windows?  It may come as a surprise to you, but Windows doesn't have any support for Linux or it's filesystems.  I haven't had the problems you're having, so I can't really comment.  Sorry you had such a bad experience, though perhaps you should have another go and ask for help?

---

### Post by cardinals_fan on 2008-08-04
> **skaufman said:**
> 
Blah!  Give me Slackware over this!
Use Slackware then.  I personally prefer Slack over Ubuntu.  There's no need to rant and rave, just use what works.

---

### Post by wolfen69 on 2008-08-04
> **kspncr said:**
> Why I hate these posts

They do nothing. They stir up negative feelings to no positive effect. If you don't like Ubuntu, fine, why not just be on your way? Why sit here and say Ubuntu sucks? We on the forums like Ubuntu, you're not going to change our minds because you couldn't get it to work.




well said.

i love it when it doesnt work for someone and they say it sucks. when will people realise that it will not work on every single computer in the world. it's too bad they have one of the few that dont, but that's the reality of it. windows doesnt even run on some computers. 

i recently tried opensuse. it didnt work out too well. does that mean i'm going to go storming their message boards saying it sucks? no. i'm sure many people run it and absolutely love it.

some people really need to stop acting like spoiled little kids, get a life, stop complaining and use what works.

---

### Post by AlphaMack on 2008-08-05
Appalled?

1.  It's free.  No one forced you to pay in order to install it.
2.  You're not entitled to anything in these forums.
3.  Whatever support herein is the result of people volunteering their time and resources.  See point #2.

---

