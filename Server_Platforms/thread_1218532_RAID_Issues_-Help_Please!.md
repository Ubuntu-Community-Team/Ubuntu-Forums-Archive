---
title: "RAID Issues -Help Please!"
date: 2009-07-20
forum: Server Platforms
---

### Post by Daisuke_Aramaki on 2009-07-20
I don't know where to post this, but if this is not the right section, please feel free to move this to a place more appropriate. Also, the problem I am mentioning is not Ubuntu specific.

We have a small cluster at work that some use for their simulations. Most of us use our super computing facility though! A friend of mine who sort of manages the thing, asked for my help a couple of days ago, since the thing went kaput.

Since he wasn't that much familiar with linux, i told him i could see what the problem is. The issue was kernel panic, due to the fact the root file system which is on the RAID was unable to be mounted, due to corruption. it uses the reiser filesystem by the way.

I put a live cd in and checked the thing. The disk was indeed corrupted, and none of the file check protocols worked. got the standard bad super blocks errors. I tried rebuilding the superblocks, but another fail. So we decided to at least recover the data. so after rebuilding the tree, which took around 5-6 hours, a lost+found directory was created with all the data.

Fair enough, the lost+found directory had a lot of directories with number ids which had most of the files, and data. Going through them individually is out of question right now, but if need be we decided to make an image later.

So here's my question. Obviously the file corruption was so extreme, and since rebuilding tree was the only option to recover the data, we had to do that. But that effectively meant all the linux files also have gone to lost+found, which means the raid does not have the proper directory structure anymore to boot.

Do any of you have an idea as to what could be done next? Install anew on the raid or try to recover the necessary files from lost+found that are needed for the boot?

It's an old transtec system, and runs Suse9.0.

Hope i was able to state my problem clearly. I have done a lot of searching in google so far, but couldn't get a clear picture.

Stupid thunderstorm! Caused a massive power shutdown effectively killing a couple of fermentations, and now this may be?

thanks for your time folks

---

