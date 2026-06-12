---
title: "Bit rot really a big problem?"
date: 2022-01-20
forum: Server Platforms
---

### Post by Tadaen_Sylvermane on 2022-01-20
This has been driving me up a wall. Trying to protect the stuff on my server. I've done a bunch of research and I found this article that quite succinctly tells us (home users mainly) that it isn't a huge problem complete with explanations. Fairly direct and to the point. It's an older article from 2017. Your thoughts?

[https://www.jodybruchon.com/2017/03/07/zfs-wont-save-you-fancy-filesystem-fanatics-need-to-get-a-clue-about-bit-rot-and-raid-5/](https://www.jodybruchon.com/2017/03/07/zfs-wont-save-you-fancy-filesystem-fanatics-need-to-get-a-clue-about-bit-rot-and-raid-5/)

---

### Post by MAFoElffen on 2022-01-21
My "Thoughts?" That may take pages... LOL

No matter who you are or the scale: "Always have a good Back-Up..."


Everyone is gong to have their own likes, dislikes and opinions... Me? Being an IT professional for over 33 years now, I have things I just base on my own experiences.

On all machines, I am fanatical about having a good backup and recovery plan, and sticking with it. You don't know how many times I was called into somewhere after a disaster, and I asked where their backup was... I have designed backup and recovery plans for companies... Written scripts to automated everything for them... If they don't keep to it. it is useless. No filesystem, filesystem manager, nor form/type of RAID will help you past 'some things'. And rebuilding a hardware RAID or Software RAID will take you a long time, and is no guaranty for anything.
that point
Once upon a time, I had a software project for a GUI Wrapper of mdadm. Until... who really used it and for what? I was told that it would be something that would have been used by very few. And that the people who might use it, probably didn't understand mdadm enough to be using it safely.

I used to recommend and do 3 node fail-over clusters and hardware RAID on all production or commercial systems, depending on the business, and their acceptance of risk. . If your business is "uptime", that is it, right? Well things evolved. You have a member fail in a RAID... How long to rebuild the array to recover, --OR-- restore new? Some times fixing something that you know is broke, that much longer, than restoring from just before, and rolling in the transactions up to current. A lot less downtime to a successful result. That is a different perspective than what it used to be, but is so much easier and faster... As long as you are backing things up and capturing those things... ut those are things That were driven into me 33 years ago... That still work. Dang that logic.

ZFS? Well, it is not a magical. solve-all I have used ZFS since 2006 when it was released with Solaris 10 and OpenSolaris. It has it's uses and places. It doesn't take the place of a good recovery and disaster plan. It is as good as LVM2. Both have their pro's and cons. But you need to have people in your infrastructure that understand what you have and how to use it in your environment. ZFS has been around for almost 16 years now... Why do people treat it as if it is something new??? How many people using it as just another buzzword, really understand how to use it? Why not LVM2?

LVM has been around since 1998... There is nothing that one or the other can do, (LVM2 or ZFS) that the other can't. Most people use about 15%-20% of the capabilities of either. (Just enough to scratch the surface.) Why? Because how many people do you know, that know "all" that either does?

Me? I have both here... Why? Because I have to support both. I have Hardware RAID cards, that I pass through now, to ZFS or LVM... With automated backups to RT1000 cartridge drives. That is different than what I had in my home lab years past, where it was hardware RAID, with a separate fiber-backbone to backup servers. That did everything in the background. What over-kill.

There is a time a place for everything... Hardware RAID on 3 node clusters. On risk acceptance RAID5 - RAID6 or RAID50-RAID60 based on that risk. If DB and transaction based, then transaction logs... That was what the industry said it "should" be... But ended up slowing things down, in some circumstances. 

If home server... What is important, what is the risk, and what is the budget? There are just ways to do things smartly, that do not cost a lot. It's all a matter of perspective and what you want to do. Look beyond the hype and buzzwords, to see what you feel is important, and how to protect that. Then look at how much time you can afford to be down (uptime), What is acceptable to you for that? Come up with a plan that works for you and that you can afford.

What is boils down to for a home user and home networks? What do you want to keep safe?What can you do to protect it that makes common sense? What is the real risk factor of that? How long can I afford to be without it, for it to be back up?

---

### Post by mIk3_08 on 2022-01-21
> **Tadaen_Sylvermane said:**
> This has been driving me up a wall. Trying to protect the stuff on my server. I've done a bunch of research and I found this article that quite succinctly tells us (home users mainly) that it isn't a huge problem complete with explanations. Fairly direct and to the point. It's an older article from 2017. Your thoughts?

[https://www.jodybruchon.com/2017/03/07/zfs-wont-save-you-fancy-filesystem-fanatics-need-to-get-a-clue-about-bit-rot-and-raid-5/](https://www.jodybruchon.com/2017/03/07/zfs-wont-save-you-fancy-filesystem-fanatics-need-to-get-a-clue-about-bit-rot-and-raid-5/)

Yeah this is proven and tested. Let your backups keep safely out of reach to your children for more safe keeping. :-D

---

### Post by ameinild on 2022-02-01
Bit rot (and other filesystem errors) are a problem. There is a reason ZFS was made the way it is. But as MaFoElffen correctly states, ZFS (and other fancy filesystemes) isn't a magical solution to everything.

ZFS has a number of data-protection features, such as:

[LIST]
[*]Parity and integrity-checking 
[*]Copy-on-write and snapshots 
[*]Hot-spares for failing disks 
[/LIST]
*None *of the above (extremely cool and handy) features can substitute a proper backup solution. Some of these features can *in some cases *prevent you from doing a full restore from a backup, which saves some time and makes administration easier.

But you still need _proper backups_, no matter what.

---

