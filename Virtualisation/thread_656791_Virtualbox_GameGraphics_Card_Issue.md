---
title: "Virtualbox Game/Graphics Card Issue"
date: 2008-01-02
forum: Virtualisation
---

### Post by icarus7000 on 2008-01-02
I've been working on getting a virtualbox machine working properly for the past day or so, and have finally come across a problem that I can't find a solution for on these forums. Here's hoping someone out there can help.

I've got Virtualbox running a Windows XP machine with guest additions, sound, networking, all installed and working correctly. The main reason I'm using a virtual machine to begin with is for gaming - I'm not a heavy gamer so most of the time I just use Ubuntu 7.04. One of my main downfalls so far has been the fact that I have an old ATI X1300 Graphics Card - fortunately the forums have been able to help me out with that so far. Anyway, let's get to the issue: I just installed Elder Scrolls IV: Oblivion in the XP VM, and when beginning the game up to play I get the following error window in Windows: 

Failed to initialize renderer.
NiXAdapaterDesc::GetDeviceCaps() failed.

I'm assuming that this has something to do with the way Guest Additions communicate graphics card/driver to the guest machine...Help!

---

### Post by PPAAUULL on 2008-01-02
I once looked at useing a VM to play windows game and found out that for it to render fast and sometimes at all it is not possible in a VM at this point in time with the technology. If it is games you are after check out WINE or other applications they should do the trick for some games. Other then that though you might have to dual boot, that is what I do so that I know that I can always use the windows side for anything that needs it (which is very unfortunate.)

---

### Post by wolfen69 on 2008-01-02
i second the dual(or triple)-boot option. i have a 20gb "Wintendo" partition. i tried to go 100% linux for a while, but found out i should just use the best tool for the job. and for gaming, xp is the best. i turn off all unneeded services and eye candy, and it runs great. i also keep it offline most of the time. i guess the second best thing would be wine. but dont expect to be able to run the latest and greatest.

---

### Post by autonomouse on 2008-02-27
I got the same problem - dual boot and wine aside, has anyone manage to work this out? 

pretty please?

---

### Post by supmax on 2008-06-19
Also when Playing games, they do not seem to be full screen. Does any one know if its possible to make games run full screen in virtualbox?

---

### Post by theUg on 2008-07-28
> **supmax said:**
> Also when Playing games, they do not seem to be full screen. Does any one know if its possible to make games run full screen in virtualbox?
In the Vbox window in menu there&#8217;s an option to go full screen mode. Shortcut would be Host (usually Ctrl) + F.

---

### Post by Fire_Chief on 2008-07-28
Virtualbox does not support 3d acceleration for VMs. If you don't want to run through Wine or dual boot, you may be stuck. I think VMware now supports 3d acceleration for VMs but it's still kinda experimental.

Cheers!

---

### Post by Im_Original on 2009-01-17
i was just trying to do this the other day as well, I wanted to play KOTOR I. I looked around, and virtual machines cannot play games as far as I can tell. There isn't a graphics interface that works yet. Wine didn't work either. Then I ran across a project called TinyXP: someone has hacked windows xp down to the bare essentials and wound up with a system that runs small, boots faster and is easy to install. I don't know if you've ever installed windows from scratch, but its a pain. This one is easier, all though you'll still have to track down some drivers. This makes it good for a gaming partition for dual boot because it only takes up about 400mb as opposed to around 1.1 gigs for a full XP install, and the OS takes less ram so there is more for games. It's also better for virtual machines because it only needs 50 - 100 mb of ram and it still runs all windows programs (except games, still no games in a vm). 

So I tried it, it works well and it's worth looking into. There is no website for TinyXP, because there is no budget, but if you search pirate bay for Tiny XP you'll find a bunch of editions. Most of the info I found was in the torrent description there. If you want more info, you'll have to google around. 

So, Tiny XP is not a perfect solution, still can't run games in Ubuntu, but it is better than doing a full sized install for dual boot, and it is still useful for virtual machines. 

Enjoy.

---

### Post by Im_Original on 2009-01-17
whoops, this thread is probably dead. I saw the first post in this thread was Jan 3, 2008 . . . and forgot it's 2009 now. Happy new year!

---

### Post by theUg on 2009-01-17
Thanks for the tip though, worth checking out.

---

