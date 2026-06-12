---
title: "Alternatives to Dual-boot?"
date: 2007-11-12
forum: Virtualisation
---

### Post by trishacupra on 2007-11-12
Hi,

I'm a web designer and currently I dual boot Gutsy and XP.

I hate having to boot up WIndows - I only do it to check my designs in IE and when I need to do a lot in Photoshop CS2. (I'm actually running CS2 in Ubuntu under Wine - but it's a bit crippled and gets frustrating for anything more than a quick tweak.)

I've heard about VMware, Virtualbox and so on, but I don't really understand how it works.

Right now, I have to restart my computer to load up WIndows. How does this differ to having Windows installed 'virtually'? Is it easy to open up a Windows program while using Ubuntu?

How much space does a 'virtual' installation take up? My laptop drive is only 30GB.

Thanks.

---

### Post by kennedyjch on 2007-11-12
Well, over the weekend I installed both VirtualBox and XP Home on my Feisty setup and it works like a champ. All my "needed" windows applications (mindmanager, some accounting software, gps software, voice dictation and paper filing management) seem to work with 0 problems. IE works fine for those things that only work under IE.

And if you ann the Compiz-Fusion interface... well... it's just awesome.

Only thing that appears to still require dual boot is those apps which take advantage of 3D functionality (gaming, perhaps some CAD apps, etc.)

---

### Post by xpod on 2007-11-12
Well i`m certainly no web designer but VirtualBox sure made those Virtual machines nice & easy for the complete pc noob i was at the time i first tried it....*still* am in fact:)

It sure beats that dualbooting lark though....as long as it`s not for games & such as mentioned of course.
Great for trying out other OS`s without worrying about partitioning & rebooting and if you also run compiz ..then Windows is just around the corner:)

---

### Post by trishacupra on 2007-11-12
Cool. I don't need gaming, so it sounds good. I miss mindmanager...

How go you use XP in virtualbox? How do you open programs? I should check Youtube - maybe someone has a video of it.

Any good HOWTO's you followed?

---

### Post by trishacupra on 2007-11-12
> **xpod said:**
> Well i`m certainly no web designer but VirtualBox sure made those Virtual machines nice & easy for the complete pc noob i was at the time i first tried it....*still* am in fact:)

It sure beats that dualbooting lark though....as long as it`s not for games & such as mentioned of course.
Great for trying out other OS`s without worrying about partitioning & rebooting and if you also run compiz ..then Windows is just around the corner:)

Do you have a video of virtualbox? I noticed your sig. :)

---

### Post by trishacupra on 2007-11-12
Oh - so its like this - [http://youtube.com/watch?v=lA52Y7I2hCE]("http://youtube.com/watch?v=lA52Y7I2hCE")

---

### Post by ingo on 2007-11-12
mindmanager? You should have a look at freemind! [http://freemind.sourceforge.net/wiki/index.php/Main_Page](http://freemind.sourceforge.net/wiki/index.php/Main_Page)

---

### Post by P4man on 2007-11-12
Check my signature for a demo and complete how-to install and configure virtualbox. 

Here, Virtualbox runs photoshop CS3 perfectly  (as well as dreamweaver and Sony vegas I might add).  Speed is a bit slower than native, but perfectly acceptable, especially for web stuff.

BTW, I didnt even know photoshop ran under Wine, I thought it didnt?

Edit: as for diskspace, it will not take up more space than dual boot. in fact, it will take less. Virtualbox itselve is neglectable (20Mb or so), the virtual harddisk you create for windows can be as big or small as you like. The cool thing however, is that you can assign a (virtual) large drive to your virtual windows, and it won't take up any space as long as its not used. Empty space on the virtual harddisk takes up no space on your actual harddisk. So right now you have to weigh how much diskspace to assign to each partition  / OS, when you virtualize, you no longer have that problem.

Anyway, you probably want to test first before ditching your dual boot. For that you will need a gigabyte or so to setup the virtual windows. once you decide you like it, you can remove the actual windows partition and reclaim that space.

---

### Post by trishacupra on 2007-11-12
Wow, thanks.

RE: Freemind. I got started with mind maps with Freemind, but last time I looked, it wasn't really comparable with mindmanager. But I'll take another look, for sure.

RE: Photoshop and Wine - PS7 is supported, anything newer is crippled one way or another - I hacked, hacked, and hacked and used Crossover Linux to get CS2 kind of working. And it's just plain *ugly*.

RE: Diskspace - now, that is good news. I had no idea it worked like that. Very cool.

So, seriously, all I need is one gig to try it out? I thought XP normally needed  3 or 4 gig just for a basic install.

What about memory? I have 1 gig of ram - is that enough?

---

### Post by P4man on 2007-11-12
Don't quote me on the 1 Gigabyte diskspace, but  I think its somewhere around that. No more than 2 for sure. Of course, you can create a larger virtual disk so XP doesnt feel too cramped, but it won't take more than 1 or 2 GB actual diskspace.

As for RAM; well, 1GB will work, good enough for testing, but maybe not very comfortable.  You'll want to give the virtual XP machine around 500Mb to work somewhat decently with photoshop, leaving you not that much for ubuntu. It could work, especially if you only work with relatively small bitmaps,  but it would be tight IMO. 

Only one way to find out though: try it :)

---

### Post by trishacupra on 2007-11-12
Cool. Questions:

Can you install xp on an external usb drive?

Will I be able to access my files on the linux default filesystem (ext3 or whatever it is) in xp?

Thanks.

---

### Post by trishacupra on 2007-11-12
Wow, Freemind has come a long way!

---

### Post by P4man on 2007-11-13
> **trishacupra said:**
> Cool. Questions:

Can you install xp on an external usb drive?.

Yes. You have to install XP on a virtual drive, which is a file for Linux. You can put this file anywhere you want, even move it later easily.
> 
Will I be able to access my files on the linux default filesystem (ext3 or whatever it is) in xp?

Yes, through shared folders, which will appear as network drives to XP. See the howto in my sig

---

### Post by ingo on 2007-11-13
> **trishacupra said:**
> Will I be able to access my files on the linux default filesystem (ext3 or whatever it is) in xp?The last windows I used was 98 but I am pretty sure that Win will not be able to read the Ext3 file system. Have a look here 
[http://www.fs-driver.org/faq.html](http://www.fs-driver.org/faq.html)

---

### Post by P4man on 2007-11-13
> **ingo said:**
>  I am pretty sure that Win will not be able to read the Ext3 file system. Have a look here 
[http://www.fs-driver.org/faq.html](http://www.fs-driver.org/faq.html)

If you run windows natively, no. But he considers running it on a virtual machine under Linux, in that case it is not a problem. Linux will read the Ext3 and provide the virtual machine with a network folder so XP can read/write to it.

BTW, I just found TinyXP
[http://thepiratebay.org/tor/3492757/TinyXP_Beast_Edition_(eXPerience)_06.06.06](http://thepiratebay.org/tor/3492757/TinyXP_Beast_Edition_(eXPerience)_06.06.06)

I haven't tried it yet, the legality seems dubious (ie I dont know if you can use your windows licence with it), but using just 40Mb RAM and less than 400Mb diskspace, it looks like something that could be pretty cool to run on a VM on a laptop.

---

