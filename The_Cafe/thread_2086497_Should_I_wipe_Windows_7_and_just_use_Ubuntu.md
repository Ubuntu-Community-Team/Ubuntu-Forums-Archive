---
title: "Should I wipe Windows 7 and just use Ubuntu?"
date: 2012-11-21
forum: The Cafe
---

### Post by Dedwyn on 2012-11-21
Hey all,

I have been interested in Linux for a while now, almost a year or two, and I am curious to how viable is it to wipe my Windows installation with Ubuntu and just use Ubuntu.

The reason why is because whenever I dual boot to play games on windows I find that I never go back to Ubuntu I just stay on Windows while Ubuntu sits there gathering dust (so to speak).

The applications I NEED to run are:

Steam (not an issue anymore, will come out very soon, hopefully)
Curse Client, for World of Warcraft
Guild Wars 2
League Of Legends
Skyrim
Battlefield 3
World Of Warcraft
Call of Duty Black Ops 2
The Blackberry Desktop Software (to manage my playbook)
Foxit reader (or another PDF Reader that is fast, stable, secure and has tabbed browsing)
Hamachi (or an alternative that can run on Windows and Linux)
Origin (obviously
Oblivion
EVE Online
Razer Synapse 2.0 (this NEEDS to be NATIVE, otherwise my mouse is pretty much useless, Razer Naga)


Now obviously hardly any of them (if any) will run natively, so I am wondering what is it really possible to run Windows 7 in a Virtual Machine and have all my games installed in that? What I mean by this is, will my games (For example Battlefield 3) have playable frame rates and actually be playable or will I have to rely on Wine?

My computer Specs are:

AMD 955 Quad Core 3.2GHz CPU
AMD Radeon HD 6670 (Formerly ATI instead of AMD)
8GB DDR3 1333MHz RAM

No wireless or anything like that.

Or should I just stay on Windows 7?

---

### Post by Grenage on 2012-11-21
> **Dedwyn said:**
> The applications I NEED to run are:

Steam (not an issue anymore, will come out very soon, hopefully)
Curse Client, for World of Warcraft
Guild Wars 2
League Of Legends
Skyrim
Battlefield 3
World Of Warcraft
Call of Duty 4 and up
The Blackberry Desktop Software (to manage my playbook)
Foxit reader (or another PDF Reader that is fast, stable, secure and has tabbed browsing)
Hamachi (or an alternative that can run on Windows and Linux)
Origin (obviously
Oblivion
EVE Online
Razer Synapse 2.0 (this NEEDS to be NATIVE, otherwise my mouse is pretty much useless, Razer Naga)

Stay on Windows 7.

---

### Post by Dedwyn on 2012-11-21
So running my games in a virtual machine is not going to be viable, performance wise?

---

### Post by Statia on 2012-11-21
> **Dedwyn said:**
> So running my games in a virtual machine is not going to be viable, performance wise?

AFAIK, 3D graphics support in virtual machines is quite limited. Things may work, but you will take a significant performance hit compared to running the games natively on your GPU.

You are probably better off with Windows 7 for gaming, but it could be an interesting experiment to try out one of your games in a virtual machine and compare how it performs.

---

### Post by Lars Noodén on 2012-11-21
I'd say try out the virtual machine first.  It might solve your gaming problems.

---

### Post by Dedwyn on 2012-11-21
Would WINE take care of most of them?

---

### Post by Lars Noodén on 2012-11-21
WINE is likely to work for some of them at least.  You'll have to check the database for the status of individual games [http://appdb.winehq.org/](http://appdb.winehq.org/)

Either that or you can try them one by one to see how they go.  There were reports a few years ago that some games actually run better under WINE.

---

### Post by coldcritter64 on 2012-11-21
OP, if I were in your position, I'd be doing a lot of virtual machine testing before wiping anything. With your list of gaming, I'd tend to stick with dual booting or only use Windows. 

I have very minimal gaming requirements here and no specialized hardware. So I no longer use Windows.
However, unless you have a specific dislike of Windows, I see no reason for you to do a complete switch, dual booting although it can cause headaches for some, worked well for me for nearly two and a half years.

By all means check out virtualization, but for some of your listed games, I suspect you will end up back in Windows. Hopefully virtualbox 3d support has improved since my last tryout with it. Good luck, whichever route you choose :).

---

### Post by Dedwyn on 2012-11-21
Sweet, I'll download Ubuntu 64bit for desktop and dual boot and then try and install the games using wine and VM and see how I go, one last question while I am waiting for it to download, is NFTS a good file system? Because I have my 1TB HDD for my windows and another 2TB where I store everything and I was wondering if I do choose to stick with Linux should I format it to a different file system?

---

### Post by westie457 on 2012-11-21
Personally I would keep the extra hard drive with NTFS. Simply because it can be connected to another computer running a different OS and still allow you to access the files on it. Windows is very limited in the file-systems it can recognise.

---

### Post by whatthefunk on 2012-11-21
Stay with Windows.

---

### Post by Lars Noodén on 2012-11-21
> **Dedwyn said:**
> Sweet, I'll download Ubuntu 64bit for desktop and dual boot and then try and install the games using wine and VM and see how I go, one last question while I am waiting for it to download, is NFTS a good file system? Because I have my 1TB HDD for my windows and another 2TB where I store everything and I was wondering if I do choose to stick with Linux should I format it to a different file system?

I would avoid NTFS.  It is prone to fragmentation and cannot handle basic file permissions.  If you stick with Linux, you should consider using EXT3 or EXT4.  I can't help but wonder if there isn't a way to force Windows to read any of the EXT filesystems.

---

### Post by vasa1 on 2012-11-21
Use Ubuntu as much as you like but **don't** wipe Win 7.

---

### Post by Majorix on 2012-11-21
Keep Windows 7.

---

### Post by Gremlinzzz on 2012-11-21
:popcorn:for games keep Windows!

---

### Post by BrokenKingpin on 2012-11-21
I don't even see the point of trying to get all that working in wine... if you already have a Win7 install use it. You can still use Ubuntu for everything else, and Win7 for gaming. I just don't see the point of fighting with wine for all that when you can simply just boot into Windows.

---

### Post by Paqman on 2012-11-21
VMs are not a good solution for gaming. Wine has a limited amount of success, but can be a lot of hassle to get set up right.

TBH, if you're playing a lot of Windows games then by far the easiest and most hassle free route is to use Windows.

However, that doesn't mean you can't use Linux for some stuff. Some games do work fine in Wine, and some are available for Linux natively. I'd set up a dual-boot and try to do as much stuff in Linux as you can.

---

### Post by mastablasta on 2012-11-21
you preety much answered to yourself. stay on windows since you have the need for programmes that are made for windows only.
 
some games you mentioned (such as Oblivion) can run well in wine. but most can't run at all. you might be able to installthem but that's about it. For example there is no Origin for linux as i know. Virtual maschine is a waste of time.  you will get much better performance under windows.
 
if you want to test linux, use it for safe browsing or learn a few things it's better to install it in virtual box for example: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)
 
you have enough ram and CPU to run it nicely and fast in there.

---

### Post by mamamia88 on 2012-11-21
No reason not to have both installed unless you really need the harddrive space. With the ubuntu installer you get a slider for how much space you want to dedicated to each os.   It will install ubuntu for you as well as grub and you can pick whatever one you want at boot.   Only caveat is that if you delete ubuntu you will have to restore the mbr which can sometimes be complicated.

---

### Post by leclerc65 on 2012-11-21
Sacrifice 20G, and shove it there - forget about that thing ever existed. 
One day you may be thankful if the external NTFS hard drive all of a sudden refuses to be mounted, or you decide to buy an ...iPad :(, etc...

---

### Post by Jakin on 2012-11-21
Absolutely NOT. There is no reason in the world, why anyone couldn't just dual-boot. That is, until they are COMPLETELY sure they dont need or want win7 anymore.

---

### Post by mastablasta on 2012-11-22
if windows takes long time to boot then dual boot can get annoying :-)

---

### Post by Erik1984 on 2012-11-22
> **mastablasta said:**
> if windows takes long time to boot then dual boot can get annoying :-)

That's true, however for me that's not the case. Windows 7 boots up faster than (K)ubuntu. Dual boot can get annoying when you don't regularly switch between the two. When you start the lesser used system then, you will be bombarded with updates (especially in the way Windows handles them).

---

### Post by Aaron Christianson on 2012-11-22
> **Dedwyn said:**
> The applications I NEED to run are:


I'd be interested to get a working definition of "NEED" in this context, for purely academic purposes.

---

### Post by Mikeb85 on 2012-11-22
> **Dedwyn said:**
> So running my games in a virtual machine is not going to be viable, performance wise?

Not really.  VMs tend to do poorly in 3D performance.

---

### Post by Mikeb85 on 2012-11-22
Keep dual booting.  Non-native gaming in Ubuntu is kind of a pain, I even keep a Windows 7 partition even though I use it less than once a month...  Having it around is nice for those times you need to use some obscure Windows-only software, or want to play a Windows only game...

---

### Post by orb9220 on 2012-11-22
Yep triple boot here With two of the OS'es on differt HD's. So Win7,Winxp & Mint 14 cinnamon. 

You can edit grub to change default. Or EasyBCD on windows allows you to edit boot menu changing wait times and default boot OS.

Most I find with people are one HD,One OS and No backup stratedgy. Then Poo-Poo to everyone when they can't boot their system or HD crashes and burns.

As big as hardrives are nowdays. There is no reason not to have your flavors and protection at the same time on the same system.
.

---

### Post by RoosterHam on 2012-11-23
1 more for the majority vote here. For now (at least) keep Windows as it is. You've got enough hardware to test a Linux or more in a VM from Windows. This would let you learn Linux without changing anything.

Dual boot would probably be most suitable for you. Keep Windows for your 'needed' software, run both OS natively so no performance hit, and install wine in Linux, and see how much of your Win software you can get working from Linux. Plus you can discover all of the native linux games that are available to you.

Gaming inside a VM, anything highly graphical really, is a nightmare. I would advise against it for any recent releases.

Another thing to consider, if you got all of your games working in Linux, what about the games that will come out in the future? Are you going to be able to accept that most future releases will in no way work under wine? For me, I was okay with that when I deleted my very last Windows partition. There are always well supported consoles. But others won't adjust as I did. Its all about what works for you.

---

### Post by mastablasta on 2012-11-23
> **RoosterHam said:**
> There are always well supported consoles. But others won't adjust as I did.
 
consoles are more dated even than my old hardware. so some people really can't adjust....

---

### Post by Dedwyn on 2012-11-23
I have decided to follow your suggestion guys, I will keep Windows, however I will be trying to get more and more games to work with Linux and in a year or two when I am content with the current range of games on Linux I will probably say goodbye to Windows, and to be honest if I could get League Of Legends, Skyrim and Oblivion to work and Steam got all the games the mac has on Linux as well I would be perfectly content with Linux, but until then well I guess I will just have to dual boot.

P.S I am buying 8 games on Steam for Linux beta (no I am not on it *sadface*), seeming how it is currently the autumn sale I strongly recommend installing the Steam for Linux beta and buying a few games to send a strong message to other developers. For only 8 games it's roughly $40AUD.

---

### Post by stalkingwolf on 2012-11-23
In the end you are the only one that can answer your question.

On this machine i am multi booted. I have two fat32 partitions where i store movie files. I have Zorin, Ultimate edition and Peppermint.

My eee has win xp and zorin.  My wifes has zorin and ubuntu 12.04.

---

### Post by mr john on 2012-11-24
Why limit yourself to just one operating system when you can have the benefits of two? By deleting windows you save some extra space, but you also cut yourself out of being able to use thousands if not millions of good software packages. My opinion? Don't limit yourself. Keep your options open.

---

### Post by Bandit on 2012-11-24
> **Dedwyn said:**
> Hey all,

I have been interested in Linux for a while now, almost a year or two, and I am curious to how viable is it to wipe my Windows installation with Ubuntu and just use Ubuntu...........

Or should I just stay on Windows 7?

For gods sake yes you need to stay with Win7 on at least your gaming rig.. I got a gaming rig also that is best for Win7. Its the best solution for that rig. Ubuntu is nice, feature rich and nice replacement for most desktops. But for what you want/need to run, it just will not cut it.

I recommend dual booting if you can. Using Linux for everyday use and Windows for your gaming needs.

---

### Post by fontis on 2012-11-25
I'm kind of in a similar situation.
Even though I find myself rarely booting into Linux, I still like having a partition with it on my laptop. I dualboot but primarily use Win7 since most of the games I play (like League of Legends etc) don't run native or well enough in Linux.

But it's all fine and dandy. I keep the Linux partition because there are times when all else fails, I can always rely on my Linux partition to save the day - be it some dodgy Windows fail or some device not working properly in Windows (the irony right? :D)

Plus there are some benefits, I sometimes use Linux for Wifi security testing. The software and procedure I find is easier in Linux than it is in Windows :)

Ideally, I would want to stay in Linux and wipe Win7, but there's just too much stuff I use which doesn't exist/work in Linux so.. the compromise now does well enough :)

One day when I'm not stuck abroad with 1 device, I'll probably run Linux machines too (like I do back home) but for now this will do :)

---

### Post by Sunships on 2012-11-25
I keep Windows for when I need to write my CV, or any other document that needs to not look like ***.

---

