---
title: "Video graphics issue on guest OS"
date: 2011-06-28
forum: Virtualisation
---

### Post by Ginzell on 2011-06-28
Well first, now that I've got my VB all installed and got the guest OS on it (Thanks to Varunendra!)
Now - I'm having trouble with the graphics. 
The Video is only showing 16 colors and 640x480 resolution and doesn't give the option to change either one. Course this makes the graphics icky. I've searched up and down for this answer and I'm finding a lot of outdated stuff.  
I tried the xorg.conf file but it opens blank, which I saw someone say because it's not needed anymore. 
I tried 2&3D acceleration. 

VB-4.0.8 - Guest additions installed 
Ubuntu 11.04 host.
Guest-WinME Base Memory-512MB Video Memory-64MB. 
*Intel Graphics Media Accelerator 4500M

And second, I also installed Ubuntu 11.04 as a Guest OS and it's using 1366x768 and is fine with that, except for it says my hardware doesn't support Unity and it changes me to classic. I wanted Unity so I could test desktop animations etc. without crashing my real desktop as I've done several times already.  

Anyone know how I can fix these things?
Thanks!

---

### Post by varunendra on 2011-06-28
> **Ginzell said:**
> Well first, now that I've got my VB all installed and got the guest OS on it (Thanks to Varunendra!)....
Umm.. actually I think I'm the one who got you into this worthless trouble (I swear I didn't know it at the time !!.. :))

Only after reading this post and some googling I realized that VBox has only limited support for anything older than Win2000, with no guest additions for those older versions (check out the help contents > supported guest OS). You might have tried installing guest additions, but it must have failed with some error message that perhaps you didn't notice.

Here is a possible workaround you may try if you wish: [http://forums.virtualbox.org/viewtopic.php?f=2&t=9918](http://forums.virtualbox.org/viewtopic.php?f=2&t=9918)

But I'd suggest to switch to [VMware player]("http://downloads.vmware.com/d/info/desktop_downloads/vmware_player/3_0") if you really need good support for WinME (I still couldn't figure out why do you need such an old OS??). In fact VMware products are supposed to be better in everything regarding support and performance, however, they're much heavier on resources as compared to VirtualBox. It's free ('player' and 'server', while 'workstation' is paid), but needs you to register (which is free too).

Just remember to download the binary file (.bundle), not the .rpm version which is meant for RedHat and its derivatives.

In order to avoid installing ME all over again in VM Player, just 'export' your current VM in virtualbox as an 'ova' appliance, then import the 'ova' file in VM Player. I've no idea how well this is supported in VM Player, but the option certainly is there and may save you a lot of time.

As for the unity issue, it's just a small trick as described here: [http://forums.virtualbox.org/viewtopic.php?f=3&t=40893](http://forums.virtualbox.org/viewtopic.php?f=3&t=40893)
and here: [http://www.revthatup.com/fix-ubuntu-11-04-unity-in-virtualbox](http://www.revthatup.com/fix-ubuntu-11-04-unity-in-virtualbox)

Hope it goes well this time..

---

### Post by Ginzell on 2011-06-28
I actually wasn't able to install the guest additions with the installer, it would show up in the CDRom but not open so I extracted the drivers and did it that way. Was a pain that got me nowhere.  Since I posted that, I found out just as you did that the OS is pretty much too old to waste time on.  Plus everything on it is so out of date.

The only reason I was using WinME is because I have spent so much money on software from Microsoft over the years that when I found Ubuntu, I vowed I wouldn't give another cent to Bill Gates. So I was just using what I had on hand.  

I really had to laugh when I read your response because I was on that exact page you gave me for the workaround already, I had just downloaded the bearwindows driver and unzipped it on Ubuntu host then realizing I needed it on the VM and I was so frustrated and about to giving up on it anyway! 

I think I may break my vow and buy Windows 7, I think it will be the best and easiest thing to do, although, I wouldn't, but my husband wants to be able to play Combat Arms on Ubuntu and Combat Arms don't make a linux version. I've been trying to get him to come on over to Ubuntu but that game holds him up. So I thought if I could get the VB working we could be done with Windows all together.  

Anyway, after all that, I still have learned SOOOOO much and I am glad I went through it all. :)

Now since I THINK I will buy Windows7, my mind is at ease and it's turning to thinking about the fact that I dual-booted both of my laptops for Ubuntu and the Windows sides' wouldn't give up too much space to Ubuntu so now I am thinking I wish I had just wiped the entire thing of Windows..Is there any way I can do this without losing my Ubuntu install I've already created? 
If that doesn't make sense just tell me and I'll explain better. My brain is being way overactive right now. :)

---

### Post by varunendra on 2011-06-28
> **Ginzell said:**
> The only reason I was using WinME is because I have spent so much money on software from Microsoft over the years that when I found Ubuntu, I vowed I wouldn't give another cent to Bill Gates. So I was just using what I had on hand.
There are things that can be done perfectly well over ubuntu/linux, even with greater performance, but there also are things for which you must keep returning to windows at least until linux desktop versions get mature enough, and commercial companies start paying attention to it. A general and optimal compromise goes like this -
[INDENT]try as many linux distros as you can (repeat this process as your understanding and skills grow), choose the one (or more) that suits you best. Make a dual boot with windows, then for everything you can do on linux, use linux, turn back to windows only for things you can't do on linux. As your experience grows, you'll find yourself more and more comfortable with linux compared to windows.
[/INDENT]But that's a general idea. Every OS has its pros and cons.

> **Ginzell said:**
> Now since I THINK I will buy Windows7, my mind is at ease and it's turning to thinking about the fact that I dual-booted both of my laptops for Ubuntu and the Windows sides' wouldn't give up too much space to Ubuntu so now I am thinking I wish I had just wiped the entire thing of Windows..Is there any way I can do this without losing my Ubuntu install I've already created? Sure you can do this with gparted.
```
sudo apt-get install gparted
```
But I don't understand why you can't get desired space with windows. Have you installed via WUBI (16GB limit)? If yes, then removing windows partition will also remove ubuntu (it resides 'on' windows partition). If it is a normal dual boot, (win and ubu residing on their own separate partitions) then you can always resize partitions the way you want (partition being at least as large as the size of data on it of course). Be informed that resizing Vista/Win7 partitions using gparted sometimes corrupts their booting (which can be fixed, but takes extra exercise). Do your homework before trying this.

One last question - You've only recently switched to ubuntu from windows and you have got nothing above Win ME??????

And before dumping virtualization idea, I'd suggest to give VM Player a try. It's not open source, but is free and you may like it.

---

### Post by Ginzell on 2011-06-28
Yes, I just recently switched. I have an upstairs desktop that came with Windows Vista, 2 laptops - one has Windows 7 on it and the other is Vista, and my husband has Vista on his.  But all these came installed on the computers. So I don't have a disc I can use to install one of those OS's on the VM. My husbands' Toshiba didn't even come with any disc - not even a recovery. So after a couple months when it died(no boot) we took it back to the store and they had to fix it, but it would have had to been taken to them anyway because it was memory that was bad, so a recovery disc wouldn't have helped at that point. He did say something about them putting recoveries on the computers themselves, I don't remember. 

The desktop upstairs came with recovery disc and I believe both of my laptops did.  Anyway, those are up to date so to speak.  AND I know I had a Windows 2000 but when I was trying to use it for the VM I finally looked at it clearly and it was the Windows 2000 diagnostic tools disc. Blah..so I was trying to boot to Tools..I'ma smart one huh..haha! I couldn't find the actual disc. 

Ok about the dual boot deal, I didn't use WUBI, I shrunk my Windows HD's as much as it would let me and left the excess as unpartitioned space, then booted to Ubuntu ISO and installed side by side.  I wanted more space for Ubuntu but Windows wouldn't shrink any further.  
So I can use gparted to get space from the Windows side?  I'm not worried about the one laptop with Vista on it, that's the one I want to convert completely to Ubuntu anyway, but I will have to keep the Windows 7 one though because I do have things like Adobe Photoshop and some other software that I know will not be happy on Ubuntu. Also I haven't taken the time yet to learn the e-mail system on Ubuntu so I have to still boot to to Windows7 for that. I did look at it but it looked like it was going to be another thing for me to learn.  It's on my list. :)
But you're right, every OS has their pros and cons but I just am so negative towards Microsoft because having been on this side, looking at linux, learning all this stuff, I just see such teamwork and I really really like it.  You can't imagine how I felt when I saw LibreOffice and it was free.  I was so shocked.  So many good softwares that are FREE! How can that be?! I was used to paying extreme amounts of money for that.  I guess I was just so wrapped up in Microsoft I didn't think there was another way.  Linux/Unix I always thought they were geared to servers so I didn't mess with it.  When I did use servers, I just used Microsoft Backoffice.
Alright, I'm going to stop rambling.  I have pulled up the VM player site, I'll have a look.  

Oh and I fixed the Unity with your link. Thank you again.  I turned on 3D acceleration and installed the guest additions on that VM and they installed easily.  Yay. 
So I'm going to mark this as solved.  
:popcorn:
Was going to watch a movie but then I started thinking about the harddrive...so much for the movie. Heeheehee

---

### Post by Ginzell on 2011-06-28
I just had a thought, if I can get the windows vista install off the recovery disc some how, wouldn't it be alright to install it on the Ubuntu side  in the VB since it's on the same computer and all?  I wonder if there is a way to get that off the disc.

---

### Post by varunendra on 2011-06-28
> **Ginzell said:**
> Was going to watch a movie but then I started thinking about the harddrive...so much for the movie. HeeheeheeHmm.. you were 'shocked' by open source software.... and are in mood of a movie, have a look at [The Revolution OS]("http://video.google.com/videoplay?docid=7707585592627775409#") if you already haven't seen it. (I've downloaded the whole movie via keepvid.com)

> **Ginzell said:**
> I just had a thought, if I can get the windows vista install off the recovery disc some how, wouldn't it be alright to install it on the Ubuntu side  in the VB since it's on the same computer and all?  I wonder if there is a way to get that off the disc.Again, that depends upon the recovery disc's adaptability to Virtual vs Original hardware. Plus - 3D acceleration may not work inside VBox.

As for fiddling with OS partitions, I'd strongly recommend to create a recovery disc first (there must be an option inside Win7 to create one) before making any changes to partition size. Although it 'may' only be required if something goes wrong with Win7's boot sectors - to restore them.

---

### Post by Ginzell on 2011-06-28
Darn, I always forget that virtual vs original part.  
You would really laugh at me for being shocked about the free software if you knew my background.  But I'd rather not look like a complete idiot, so I'll just leave it at that. 

That movie sounds interesting.  Thanks! :)

Looks like my day will be full - course, it's 645am I probably should go to sleep but I'm kind of wired so I am certain my eyes won't shut.  

Enjoy the day!

---

