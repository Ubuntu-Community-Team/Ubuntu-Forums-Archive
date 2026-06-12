---
title: "Query, not Complaint: Ratel Value Slow"
date: 2011-05-01
forum: System76 Support
---

### Post by Teasdale on 2011-05-01
I think maybe I just need to install a more upgraded version of Ubuntu. 8.10 won't upgrade anymore, so even it's outdated.

This is a System76 computer with all the original configurations:

> 
/dev/sda1: UUID="6c814527-5db0-4129-b3bc-f41a16213147" TYPE="ext3" 
/dev/sda2: TYPE="swap" LABEL="                " UUID="3d13dcef-1b8c-41d9-bada-a585b4022a2d" 
/dev/sda3: UUID="5aea32d9-f557-461a-958a-011fe718ac27" TYPE="ext3" SEC_TYPE="ext2" 
/dev/loop0: TYPE="squashfs"


I should be able to install 10.04 on just one partition (sda1, I think) and not lose the Home folder, which is on sda3, is that correct? Does the fact that I'm skipping 9 and that my current distro is not up-to-date create problems with doing this?



---------------------

Ignore my older post; I think upgrades might be the problem.

[I][SIZE="1"]My original Ratel Value is 2 1/2 years old, and I'm noticing that it's slow. It takes a long, long time to load webpages that have a lot of images and things to load, unlike my newer Ratel Value, which has a few upgrades. It also gets bogged down on tasks like "find and replace" with very large documents.

Is this because of the processor, video card, or RAM? I could probably upgrade the video card or RAM, but if it's the processor (it *is* a Ratel *Value*, after all), would I be wasting my time?[/SIZE][/I]

---

### Post by isantop on 2011-05-02
You should be okay. Be sure to specify /dev/sda1 to mount on / and mount /dev/sda3 on /home. I would format sda1, but don't format sda3 or you will lose all of your data.

---

### Post by Teasdale on 2011-05-02
Thanks! That's exactly what I needed to know!

---------------------------------------------------------

Upgrading to 10.04 seems to have helped.

---

