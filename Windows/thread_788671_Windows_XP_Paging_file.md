---
title: "Windows XP Paging file"
date: 2008-05-09
forum: Windows
---

### Post by abhiroopb on 2008-05-09
Sorry to post this here, but I don't really know any other good forum.

Basically I just dual-booted XP SP3, and I have a paging file that is about 2gb. What is the ideal setting for the virtual memory?

Any thoughts?

---

### Post by Monicker on 2008-05-09
[http://www.theeldergeek.com/]("http://www.theeldergeek.com/")

---

### Post by abhiroopb on 2008-05-10
Thanks found the article. But I'm still not too sure. As you can see I have 2gb of ram, and I will mainly use this partition to play games. I've only set aside 20gb so that I can install 1-2 games at a time. The rest is for my ubuntu partition (about 70gb). So I was wondering what an ideal paging file would be. I read the article and I guess 1.5 times my ram is about right. But I don't really want to waste 3gb of space unless I can see a benefit from it.

---

### Post by Monicker on 2008-05-10
That site does have a forum.

[http://www.theeldergeek.com/forum/]("http://www.theeldergeek.com/forum/")

---

### Post by dbstraffin on 2008-05-10
1.5 times your ram used to be the general rule of thumb.  Once you get over 1GB this isn't necessary. I have my page file set to 1gb with 2gb of ram and I haven't had any problems even running Crysis.  I've seen some stuff online about Vista not needing any page file at all after about 4gb. I wouldn't recommend this with XP as it needs some swap no matter how much ram you throw at it.

---

### Post by niteshifter on 2008-05-10
Hi,
> 
Thanks found the article. But I'm still not too sure. As you can see I have 2gb of ram, and I will mainly use this partition to play games. I've only set aside 20gb so that I can install 1-2 games at a time. The rest is for my ubuntu partition (about 70gb). So I was wondering what an ideal paging file would be. I read the article and I guess 1.5 times my ram is about right. But I don't really want to waste 3gb of space unless I can see a benefit from it.

Ah me... Ye Olde Swap-Paging-Windows-Linux confusion ;) So let's start with this:

You are dual-booting XP and Ubuntu. XP has 20GB of space on the hard drive, Ubuntu has 70GB.

Ubuntu's swap (sometimes called paging) and XP's paging file (sometimes called swap) are two completely separate things - one has nothing to do with the other. Windows can't "see" the ubuntu stuff (files, but you can enable this), Ubuntu can see the Windows filesystem - but it won't use the Windows page file.

For Ubuntu: a **swap partition** of 1.5 X RAM is good. Practical minimum is 1X, pratical maximum is 2X. But these are general guides, folks who do large scale video work, animations, run mulitple virtual machines might need a larger swap (what they really need is more RAM).

Also Ubuntu: Linux can use a **swap file** but it's not a useful as a swap partition - the ability to hibernate is lost when using a swap file. It's also slightly slower in operation (but it's not all that noticeable.)


For Windows: the **paging file** should be at least 1.5 X RAM, but the best thing is to either use the option that sets a minimum and a maximum (1.5 X min, 3X max) use the option that lets Windows figure it out (the option "System managed size").

Note that the Window paging file lives where Windows is, that is, it's part of the Windows file system which is the partition on your drive that Windows is installed on. The Ubuntu swap partition will occupy a chunk of disk "real estate" but it's not that much percentage wise: 90GB total, a 3 GB swap partition is all of 3.3% of the total, 4.2% of the Ubuntu install. This shouldn't cramp you at all.

Clear? Or I have I heaped more confusion upon you?

---

### Post by thisiam on 2008-05-10
> **niteshifter said:**
> Hi,


Ah me... Ye Olde Swap-Paging-Windows-Linux confusion ;) So let's start with this:

You are dual-booting XP and Ubuntu. XP has 20GB of space on the hard drive, Ubuntu has 70GB.

Ubuntu's swap (sometimes called paging) and XP's paging file (sometimes called swap) are two completely separate things - one has nothing to do with the other. Windows can't "see" the ubuntu stuff (files, but you can enable this), Ubuntu can see the Windows filesystem - but it won't use the Windows page file.

For Ubuntu: a **swap partition** of 1.5 X RAM is good. Practical minimum is 1X, pratical maximum is 2X. But these are general guides, folks who do large scale video work, animations, run mulitple virtual machines might need a larger swap (what they really need is more RAM).

Also Ubuntu: Linux can use a **swap file** but it's not a useful as a swap partition - the ability to hibernate is lost when using a swap file. It's also slightly slower in operation (but it's not all that noticeable.)


For Windows: the **paging file** should be at least 1.5 X RAM, but the best thing is to either use the option that sets a minimum and a maximum (1.5 X min, 3X max) use the option that lets Windows figure it out (the option "System managed size").

Note that the Window paging file lives where Windows is, that is, it's part of the Windows file system which is the partition on your drive that Windows is installed on. The Ubuntu swap partition will occupy a chunk of disk "real estate" but it's not that much percentage wise: 90GB total, a 3 GB swap partition is all of 3.3% of the total, 4.2% of the Ubuntu install. This shouldn't cramp you at all.

Clear? Or I have I heaped more confusion upon you?

haha you kind of confused me there. for either swap or page file its good to have 2 times your physical memory. if you have a big hardrive this shouldn't bother you at all as i doubt you would be missing say 2gb of space.

---

### Post by abhiroopb on 2008-05-10
So I should be setting my paging file to about 3gb to 6gb??? That seems a bit excessive! I have set it to system managed for now...

---

### Post by mshiva on 2008-05-10
the maximum alowed size is 4GB, if you have that much of free space, just set pagefile to 4GB, and forget about it and have a peace of mind

---

### Post by smoker on 2008-05-10
> **abhiroopb said:**
> Thanks found the article. But I'm still not too sure. As you can see I have 2gb of ram, and I will mainly use this partition to play games. I've only set aside 20gb so that I can install 1-2 games at a time. The rest is for my ubuntu partition (about 70gb). So I was wondering what an ideal paging file would be. I read the article and I guess 1.5 times my ram is about right. But I don't really want to waste 3gb of space unless I can see a benefit from it.

as the page file size is simple to change, and you want the minimun you can get away with. set it for 1GB, or even half that. if you are only running one app at a time that may suffice.

you can monitor the page file usage through the windows task manager under the 'performance' tab. if you find you are approaching the maximum in the displayed graph, or that the game you're playing slows right down, you can increase your page file a bit more. once you think you have a suitable and reasonable amount, then increase it slightly and leave it at that.

best of luck

---

### Post by abhiroopb on 2008-05-10
Thanks, thats just what I was looking for! I've decided to first switch it off completely. Let it clear itself out, and then I'll let windows manage it. I've heard that windows does a pretty decent job in any case.

---

### Post by smoker on 2008-05-10
an easy way to save space is to cut down on the amount allocated to system restore. this is usually set at 12.5% which is unnecessary. you could probably cut this down to around 5% and still have a reasonable amount of restore points.

---

### Post by abhiroopb on 2008-05-10
I actually used nlite and streamlined my OS (leaving out a lot of stuff including system restore). It came to about 180mb

---

### Post by LaRoza on 2008-05-10
For the page file, there are several problems with it. The first is that it is on the same partition as your system.

To reduce fragmenting and other issues, create a small NTFS partition for it and put the page file on there (this is configurable, I am sure you saw the options)

This will prevent it from causing any problems with your OS, and it will be safer also. It will like be faster, but if you are using the page file a lot during normal use, you should get more RAM.

Ideally, swap (page files) should be on their own partition and on another disk, but not everyone has two hard disks like me.

---

### Post by abhiroopb on 2008-05-10
I have 2gb of ram, there is no way I'm paying for more any time soon! :P My computer hasn't been and hasn't caused any problems. I just never had a problem before with it being on the same partition. I actually never even thought of the page file before. The only reason I brought it up was because I used nlite, and along the way it created the 2gb pagefile. Something that I had never seen before, and I was wondering what it did exactly. I'm using pagedefrag to defrag it on boot. Other than that like I said I'll use a windows defined swap. If it does slow down at any time then I'll consider these solutions. 

Thanks a lot for the help guys!

---

### Post by abhiroopb on 2008-05-10
OK so now for whatever reason ff 3.0beta4 (from the repo) is officially worse than ff2. I opened up the subscriptions page on ubuntu forums and clicked on the page for this thread, and everything stopped for a few seconds and then the page loaded. Then I was scrolling down the thread and everything stopped again.

Similar thing happened in digg.com.

Also the hard disk light on my laptop starts flashing. Not sure whats going on.

Any thoughts?

---

### Post by LaRoza on 2008-05-10
> **abhiroopb said:**
> OK so now for whatever reason ff 3.0beta4 (from the repo) is officially worse than ff2. I opened up the subscriptions page on ubuntu forums and clicked on the page for this thread, and everything stopped for a few seconds and then the page loaded. Then I was scrolling down the thread and everything stopped again.

Similar thing happened in digg.com.

Also the hard disk light on my laptop starts flashing. Not sure whats going on.

Any thoughts?

That isn't enough to judge a browser. Fx 3 (note: I am an Opera fanperson) is functional and faster than Fx 2.

It may be many things.

---

### Post by timzak on 2008-05-12
Regarding the pagefile, I generally don't use more than 768 MB on a 1 GB ram system.  This may change depending on what you do.  Gaming or photo editing could need more.  Set it to a conservative number and run your system for awhile.  If you don't get any feedback from Windows about the pagefile being too small, you're okay.  

One tip though:  disable the pagefile, defragment your drive, then re-enable the pagefile and set the min and max size to the same number.  This keeps the page file from growing and shrinking (and hence, fragmenting over time).  As someone else mentioned, place the page file on a second physical drive if possible.  This will increase performance.  A hard drive cannot access two locations at the same time (hence the term "random access time"), but two hard drives can run simultaneously.  So if your main drive is running, and the swap is running on a 2nd physical drive, they can each do their thing simultaneously, without any slowdown from the read/write head having to jump back and forth between data and pagefile.

If you only have one physical drive, then just set the min and max size to the same and be done with it.

Good luck.

---

### Post by Living2007 on 2008-05-12
> **dbstraffin said:**
> 1.5 times your ram used to be the general rule of thumb.  Once you get over 1GB this isn't necessary. I have my page file set to 1gb with 2gb of ram and I haven't had any problems even running Crysis.  I've seen some stuff online about Vista not needing any page file at all after about 4gb. I wouldn't recommend this with XP as it needs some swap no matter how much ram you throw at it.

1.5x is acceptable, but "I" never knew that "that" figure wasn't required for over 1GB

---

### Post by Living2007 on 2008-05-12
So far, FF3 Beta6 seems toi be much be_tt_a

---

### Post by fuzzywigg on 2008-12-31
Hey all,
I have dual drives and am looking for a tutorial for how to set up XP or Windows7 on one and have Ubuntu on the other.

Does anyone have a good tutorial for how to place my page files on seperate partitions on drive X and Y, to respective OS's?

Thanks!

---

### Post by jrusso2 on 2009-01-02
There is not a lot of speed advantage in doing it this way.  For it to be a speed advantage use two drives and put the paging file on the front of the second drive.

With only one hard drive the only advantage is lack of fragmentation.

---

