---
title: "The best OS ever....made from linux"
date: 2008-09-09
forum: The Cafe
---

### Post by Howitzer777 on 2008-09-09
well a lot of people dual boot, usually with windows and linux, but its a hassle to reboot everytime when switching OS, so what if i made an OS that just a blank operating system and a user could use a xp disc, and install windows, and then take a linux live cd and then put that on there. and you could seamlessly switch between OSs and it would be wonderfuL!

---

### Post by RedPandaFox on 2008-09-09
> **Howitzer777 said:**
> well a lot of people dual boot, usually with windows and linux, but its a hassle to reboot everytime when switching OS, so what if i made an OS that just a blank operating system and a user could use a xp disc, and install windows, and then take a linux live cd and then put that on there. and you could seamlessly switch between OSs and it would be wonderfuL!

But how do you intend to do this?

I was going to put Ubuntu on a desktop, with duel monitors then put XP to boot in a VM on startup on the second monitor

---

### Post by Newuser1111 on 2008-09-09
> **Howitzer777 said:**
> well a lot of people dual boot, usually with windows and linux, but its a hassle to reboot everytime when switching OS, so what if i made an OS that just a blank operating system and a user could use a xp disc, and install windows, and then take a linux live cd and then put that on there. and you could seamlessly switch between OSs and it would be wonderfuL!I don't understand.
Is it like VirtualBox/VMware/Wine? Or is this something different?

---

### Post by zmjjmz on 2008-09-09
One possibility is to have two hard disks, and put one in hibernation (just store the current memory stack in swap) and then go back to something like a Splashtop BIOS and boot into another OS on the other hard disk.

---

### Post by cardinals_fan on 2008-09-09
...and if pigs had wings, they could fly.

---

### Post by RedPandaFox on 2008-09-09
> **cardinals_fan said:**
> ...and if pigs had wings, they could fly.

Not really, if they have wings they could be like penguins and not be able to fly

---

### Post by inportb on 2008-09-09
Like Wine on Linux? Or if you want to get more hardcore... CoLinux? o.o (or CoUbuntu, which is being planned, I think)

---

### Post by Howitzer777 on 2008-09-09
no no no. alright. I called it BlankOS, 

think about ubuntu's multipul desktop feature. you can switch from desktop to desktop. 

well this is the same concept but with OSs

---

### Post by DoctorMO on 2008-09-09
It would be technically possible with a couple of VTs which are very small and handle only hardware abstraction. normally bassed on Linux.

I think they already existing, although a pain in the neck to use and I don't even know if they work with mouse/monitor as their build for server use.

---

### Post by scouser73 on 2008-09-09
> **Howitzer777 said:**
> no no no. alright. I called it BlankOS, 

think about ubuntu's multipul desktop feature. you can switch from desktop to desktop. 

well this is the same concept but with OSs

Why?...I know what you mean, but all I can think of is, why?:confused:

---

### Post by RedPandaFox on 2008-09-09
> **Howitzer777 said:**
> no no no. alright. I called it BlankOS, 

think about ubuntu's multipul desktop feature. you can switch from desktop to desktop. 

well this is the same concept but with OSs

Why not just put a VM in a different desktop on Ubuntu?

---

### Post by smartboyathome on 2008-09-09
> **inportb said:**
> Like Wine on Linux? Or if you want to get more hardcore... CoLinux? o.o (or CoUbuntu, which is being planned, I think)

Its already in progress, its called andLinux. There's also Topologilinux, which is based off of Slackware. I haven't been able to get any to work for me though, it always crashes my video driver. :(

---

### Post by Newuser1111 on 2008-09-09
> **Howitzer777 said:**
> no no no. alright. I called it BlankOS, 

think about ubuntu's multipul desktop feature. you can switch from desktop to desktop. 

well this is the same concept but with OSsSuch as VirtualBox? (or VMware)

---

### Post by cardinals_fan on 2008-09-09
> **Howitzer777 said:**
> no no no. alright. I called it BlankOS, 

think about ubuntu's multipul desktop feature. you can switch from desktop to desktop. 

well this is the same concept but with OSs
How do you plan to implement this?  Virtualization is nothing new...

---

### Post by worx101 on 2008-09-10
To late, already done, VMware has a OS that does just this.

---

### Post by zachtib on 2008-09-10
so, essentially ESXi, but geared towards the desktop?

---

### Post by BLTicklemonster on 2008-09-10
> **RedPandaFox said:**
> Not really, if they have wings they could be like penguins and not be able to fly

lol "piguins"

sorry, that was my second play on the word penguin in a row.

---

### Post by y@w on 2008-09-10
Parallels and VMware have already done this on Mac with a Windows VM. You can mix windows from Windows (sorry, had to) with windows of applications with OS X. Works pretty slick if you ask me..

---

### Post by MaxIBoy on 2008-09-10
If I understand you correctly (you meaning the original poster,) you're talking about hosting multiple OSs under a hypervisor (which is a "host" OS specifically designed to host and even coordinate one or more "guest" OSs.)

Linux already has the built-in ability to run as a hypervisor. (I think.)

This is different than running something like VMware, which is an extra layer of abstraction *on top of* the OS. Parallels for Mac turns OS X into a hypervisor host OS. As I've already said, this feature is built into the Linux kernel itself. 

However, even VMware or VirtualBox can do Seamless Mode (windows from different OSs freely interact in the same desktop environment.) The advantage of using a hypervisor instead of running an emulator is a performance boost.

---

### Post by stat30fbliss on 2008-09-10
Although impossible, it would be cool to run A Desktop cube with each face correlating to an OS.  Windows, OSX, Ubuntu, & Fedora :)

That would be awesome.

---

### Post by RedPandaFox on 2008-09-10
> **stat30fbliss said:**
> Although impossible, it would be cool to run A Desktop cube with each face correlating to an OS.  Windows, OSX, Ubuntu, & Fedora :)

That would be awesome.

Not possible with multiple VMs?

---

### Post by dgrafix on 2008-09-10
Yes it is.

I have Ubuntu with an XP and Dos6.2+3.11 pair of VMs. 
I can switch between them easily when they are running.
They all connect with a mapped drive to my main disk shares where i keep my files so essentially they all have the same "harddisk" for data storage so to speak. (at least the XP one does, the DOS one is just for really old games :))

go here:
[www.easyvmx.com](www.easyvmx.com)

---

### Post by RedPandaFox on 2008-09-10
> **dgrafix said:**
> Yes it is.

I have Ubuntu with an XP and Dos6.2+3.11 VM. 
I can switch between them easily when they are running.
They all connect to my main disk shares where i keep my files so essentially they all have the same user data-space so to speak.

You got any info on how to set this up?

---

### Post by SunnyRabbiera on 2008-09-10
> **Howitzer777 said:**
> no no no. alright. I called it BlankOS, 

think about ubuntu's multipul desktop feature. you can switch from desktop to desktop. 

well this is the same concept but with OSs

well with the rate of technology its possible to do something like this, but please getting Microsoft to co operate is like trying to teach a Hippopotamus to fly.

---

### Post by tariquepark on 2008-09-10
i think what we are all talking about is vmware as an OS?? while a brilliant idea you would still have all the inherant problems of windows linux mac compatability and each os's hardware management.
I mean having two programs in one OS attempting to access the same hardware at the same time can still yield unfavourable results occasionally :):)

---

### Post by wishyjr on 2008-09-10
there are a lot of flying animals in this thread, like it. :)

---

### Post by MaxIBoy on 2008-09-10
> **stat30fbliss said:**
> Although impossible, it would be cool to run A Desktop cube with each face correlating to an OS.  Windows, OSX, Ubuntu, & Fedora :)

That would be awesome.

Absolutely possible. Four different fullscreen VirtualBoxes.

---

### Post by anotherdisciple on 2008-09-10
That would use A LOT of RAM! and I can't imagine the situation where I need to go back and forth between OS's over and over again.

Besides, running an OS inside an OS is basically a virtual box... and they always run slower than you'd like.

---

### Post by god0fgod on 2008-09-10
Why have Windows as well?

---

### Post by spupy on 2008-09-10
What I imagine is having something like Wine for operating systems. You got Linux installed with this Thing. The Thing emulates Windows and OS X kernels on a very low level, near the kernel. That is a layer on top of the Linux kernel that implements the interfaces of the Win and OS X kernels. So you can install Windows and OS X on the Thing, and run them and their stuff like you run programs in Wine right now. With almost no performance boost. There shouldn't be any hardware conflicts since there is only one kernel governing devices.

In memory of this thread, the Thing will be called...

PIGUIN

---

### Post by niccholaspage on 2008-09-10
^Possible.
It would take VirtualBox,Some stuff changed and some good RAM.
EDIT:What is wrong with my brain.I was trying to quote this poste:
> **stat30fbliss said:**
> Although impossible, it would be cool to run A Desktop cube with each face correlating to an OS. Windows, OSX, Ubuntu, & Fedora :)

That would be awesome.

---

### Post by Newuser1111 on 2008-09-10
> **stat30fbliss said:**
> Although impossible, it would be cool to run A Desktop cube with each face correlating to an OS.  Windows, OSX, Ubuntu, & Fedora :)

That would be awesome.I'm already trying to do that except it would be
Desk1: Ubuntu 8.04
Desk2: Windows XP Home Edition
Desk3: OS X Leopard
Desk4: FreeBSD or PC-BSD

Right now,
I am waiting for an update to VirtualBox so it can use VHDs correctly and have to try to get VMware working. And FreeBSD is currently downloading, It's at 85.57%

---

### Post by MaxIBoy on 2008-09-10
> **spupy said:**
> What I imagine is having something like Wine for operating systems. You got Linux installed with this Thing. The Thing emulates Windows and OS X kernels on a very low level, near the kernel. That is a layer on top of the Linux kernel that implements the interfaces of the Win and OS X kernels. So you can install Windows and OS X on the Thing, and run them and their stuff like you run programs in Wine right now. With almost no performance boost. There shouldn't be any hardware conflicts since there is only one kernel governing devices.

In memory of this thread, the Thing will be called...

PIGUIN

That would be too complicated and glitchy to create, I'd just stick with hyperviser hosting multiple guests, or better yet, just run multiple compatibility layers.

---

### Post by smartboyathome on 2008-09-10
Xen, anyone? Xen would do this very well, and runs on Linux. Xen is a type 1 hypervisor (which is the same type as Paralells Server), unlike VMWare Workstation and Virtualbox which are VMs, or type 2 hypervisors. The difference between type 1 and type 2? Type 1 hypervisors run on a given platform's hardware, which means its running more or less on the native hardware, whereas type 2 hypervisors run on an operating system as a "guest" OS.

---

### Post by cardinals_fan on 2008-09-10
> **smartboyathome said:**
> Xen, anyone? Xen would do this very well, and runs on Linux. Xen is a type 1 hypervisor (which is the same type as Paralells Server), unlike VMWare Workstation and Virtualbox which are VMs, or type 2 hypervisors. The difference between type 1 and type 2? Type 1 hypervisors run on a given platform's hardware, which means its running more or less on the native hardware, whereas type 2 hypervisors run on an operating system as a "guest" OS.
NetBSD runs Xen very well :)

---

### Post by RedPandaFox on 2008-09-10
> **Newuser1111 said:**
> I'm already trying to do that except it would be
Desk1: Ubuntu 8.04
Desk2: Windows XP Home Edition
Desk3: OS X Leopard
Desk4: FreeBSD or PC-BSD

Right now,
I am waiting for an update to VirtualBox so it can use VHDs correctly and have to try to get VMware working. And FreeBSD is currently downloading, It's at 85.57%

Let us know how that goes and with what specs.

What hardware would you think you would need to run this well?

---

### Post by uberdonkey5 on 2008-09-10
another possibility is to have two processors, each operating with its own hard drive, and its own monitor, and you could even put them in seperate boxes, connected by a USP cable... a bit like having two computers :D

only kidding, good luck and would love to hear the result

---

### Post by Newuser1111 on 2008-09-10
> **RedPandaFox said:**
> Let us know how that goes and with what specs.

What hardware would you think you would need to run this well?It should work in Ubuntu, because I did the same thing in Windows Vista with Virtual PC/VMware/Bochs and it ran very good.

Compaq Presario F756NR- AMD Turion 64 x2, 2GB of RAM, 120(?)GB Hard drive/320GB Portable Hard Drive.


In Vista I had it this way:

Windows Vista(Not in a VM)
Windows XP Home Edition(Virtual PC)
Linux(Bochs)[SIZE="1"]I forgot what Linux it was but I think it was Redhat.[/SIZE]
Windows 98(Virtual PC)
OS X 10.4.8(VMware)

---

### Post by RedPandaFox on 2008-09-10
> **Newuser1111 said:**
> It should work in Ubuntu, because I did the same thing in Windows Vista with Virtual PC/VMware/Bochs).

Compaq Presario F756NR- AMD Turion 64 x2, 2GB of RAM, 120(?)GB Hard drive/320GB Portable Hard Drive.


In Vista I had it this way:

Windows Vista(Not in a VM)
Windows XP Home Edition(Virtual PC)
Linux(Bochs)[SIZE="1"]I forgot what Linux it was but I think it was Redhat.[/SIZE]
Windows 98(Virtual PC)
OS X 10.4.8(VMware)

So you VMed in Vista with XP, RedHat, 98, and OSX at once?

---

### Post by Newuser1111 on 2008-09-10
> **RedPandaFox said:**
> So you VMed in Vista with XP, RedHat, 98, and OSX at once?Yes, all at the same time.

---

### Post by RedPandaFox on 2008-09-10
Interesting, I want to try it on my laptop but I wanted it in Ubuntu but I cant get networking to work in Ubuntu :( I might have to run them in Vista like you...
How do you switch between them, do you have them always running and how well do they run and interact?

---

### Post by Newuser1111 on 2008-09-10
> **RedPandaFox said:**
> Interesting, I want to try it on my laptop but I wanted it in Ubuntu but I cant get networking to work in Ubuntu :( I might have to run them in Vista like you...
How do you switch between them, do you have them always running and how well do they run and interact?
They can use shared folders and when you want to switch to another one just press a certain key(s) to get the cursor out of one then click on the other one.

They were able to use the internet and shared folders but I had internet and shared folders disabled in XP because I think it has/had a virus.

They ran good, they were not slow.

---

### Post by RedPandaFox on 2008-09-10
> **Newuser1111 said:**
> They can use shared folders and when you want to switch to another one just press a certain key(s) to get the cursor out of one then click on the other one.

They were able to use the internet and shared folders but I had internet and shared folders disabled in XP because I think it has/had a virus.

They ran good, they were not slow.

So are they in all on the same monitor or minimized when not in use?

---

### Post by Newuser1111 on 2008-09-10
> **RedPandaFox said:**
> So are they in all on the same monitor or minimized when not in use?On the same monitor, but that caused some of them to have scrollbars, which is why I want to do it on Ubuntu so I have the cube and then they could all be fullscreen.

---

### Post by RedPandaFox on 2008-09-10
> **Newuser1111 said:**
> On the same monitor, but that caused some of them to have scrollbars, which is why I want to do it on Ubuntu so I have the cube and then they could all be fullscreen.

Thats what I want to do, I just need to get my networking on my laptop, then Ill try it in Ubuntu, If I use my Vista key twice on the same machine while both are still being used?

---

### Post by Newuser1111 on 2008-09-10
> **RedPandaFox said:**
> If I use my Vista key twice on the same machine while both are still being used?You can't use a key twice unless it has a strange problem like my XP one or if your reinstalling.

---

### Post by RedPandaFox on 2008-09-10
> **Newuser1111 said:**
> You can't use a key twice unless it has a strange problem like my XP one or if your reinstalling.

I know that if there is a problem you can re-install it and call Microsoft at activation, but if its being used on the assigned machine do you think I can?

---

### Post by Newuser1111 on 2008-09-10
> **RedPandaFox said:**
> I know that if there is a problem you can re-install it and call Microsoft at activation, but if its being used on the assigned machine do you think I can?Probably, you can try.

The problem with my XP key was that it was letting me activate it on multiple computers. So it's installed on my Laptop, my Desktop, and in VirtualPC on my laptop.
I didn't tell Microsoft that it was happening but I guess they know.

---

### Post by RedPandaFox on 2008-09-10
> **Newuser1111 said:**
> Probably, you can try.

The problem with my XP key was that it was letting me activate it on multiple computers. So it's installed on my Laptop, my Desktop, and in VirtualPC on my laptop.
I didn't tell Microsoft that it was happening but I guess they know.

You need to call and explain if its legitimate and they supply a new key to activate

---

### Post by Newuser1111 on 2008-09-10
> **RedPandaFox said:**
> You need to call and explain if its legitimate and they supply a new key to activateSounds easy.
So did it work?

---

### Post by RedPandaFox on 2008-09-10
> **Newuser1111 said:**
> Sounds easy.
So did it work?

I did it once with XP, and it works with word (my unnamed computer seller does it all the time in a business with one key, calls back a month later and says he has to reformat the HDD and they cant trace it)

---

### Post by Newuser1111 on 2008-09-10
> **RedPandaFox said:**
> I did it once with XP, and it works with word (my unnamed computer seller does it all the time in a business with one key, calls back a month later and says he has to reformat the HDD and they cant trace it)OK.

And,
I'll probably be waiting for a new version of VirtualBox for a few days, I don't expect it to be out tomorrow or today. Or I could just find a way to convert VHD to VDI.

---

### Post by RedPandaFox on 2008-09-10
Ill give it a try on my lunch break on my Vista laptop, if I have any live disks on me, I think I left them in my bags with other 2 laptops :(

---

### Post by archer6 on 2008-09-11
I'm putting the final touches on a 
ThinkPad T60p 

2.4.GHz Core2 Duo 4GB ram
Main bay 250GB 7200rpm HD 
Ultra bay 250GB 7200rpm HD
256mb video card 
15" IPS Flexview SXGA+ 
Intel 802.11 a/b/c
 
Running VMware  
1) Ubuntu 8.04 
2) XP ProSp3 
3) OS X Leopard
4) FreeBSD

Thus far I'm very pleased with the outcome.

---

### Post by Canis familiaris on 2008-09-11
Already Done:
[http://amitech.50webs.com/ultimate.html](http://amitech.50webs.com/ultimate.html)

Courtesy: Virtualbox.

The only downside is No Games.

---

### Post by RedPandaFox on 2008-09-11
> **Anurag_panda said:**
> Already Done:
[http://amitech.50webs.com/ultimate.html](http://amitech.50webs.com/ultimate.html)

Courtesy: Virtualbox.

The only downside is No Games.

No games? Bah, whats the point? :lolflag:

---

### Post by Canis familiaris on 2008-09-12
> **RedPandaFox said:**
> No games? Bah, whats the point? :lolflag:

:)

---

### Post by god0fgod on 2008-09-12
What is this then?

[https://shop.canonical.com/product_info.php?products_id=118&osCsid=729e6fb4f826cf4a649b7fccb5908a3f](https://shop.canonical.com/product_info.php?products_id=118&osCsid=729e6fb4f826cf4a649b7fccb5908a3f)

---

### Post by Jonathan45 on 2008-09-12
Man if i only could have multiple desktops wit different OS like having OS X on 1 Windows on one GNOME on one and KDE on one hmmmmmmm.....
that would be cool!
:guitar:

---

### Post by god0fgod on 2008-09-12
And pointless?

---

### Post by RedPandaFox on 2008-09-14
When I get my laptop on the net with Ubuntu (I cant get it to work atm, Vista will work fine) I will try Vista, OS X, Ubuntu, XP and Debian

---

### Post by cardinals_fan on 2008-09-15
> **RedPandaFox said:**
> When I get my laptop on the net with Ubuntu (I cant get it to work atm, Vista will work fine) I will try Vista, OS X, Ubuntu, XP and Debian
I assume you have a Mac...

---

### Post by RedPandaFox on 2008-09-15
> **cardinals_fan said:**
> I assume you have a Mac...

Would I be posting this on a legal site if I didnt?

---

### Post by archer6 on 2008-09-15
> **RedPandaFox said:**
> Would I be posting this on a legal site if I didnt?
Ten points for the great humor, even if it wasn't supposed to be funny, I did get a chuckle out of it. But that's just me...:)

---

### Post by RedPandaFox on 2008-09-15
Dammit! Apparently my PC somehow has less than 1 CPU so I cant use that VM

---

### Post by billgoldberg on 2008-09-15
> **RedPandaFox said:**
> Dammit! Apparently my PC somehow has less than 1 CPU so I cant use that VM

lol

A PC with less than 1 cpu. 

lol

--

I guess you meant less than two.

I only have one cpu on my laptop (and not the fastest one) and I can run any OS in a VM.

---

### Post by phrostbyte on 2008-09-15
I do this already. Virtualbox set on one workspace.

---

### Post by phrostbyte on 2008-09-15
> **stat30fbliss said:**
> Although impossible, it would be cool to run A Desktop cube with each face correlating to an OS.  Windows, OSX, Ubuntu, & Fedora :)

That would be awesome.

Not impossible at all! In fact it's very trivial! You can set up a virtual machine fullscreen and switch between operating systems with Ctrl+Alt-Ctrl-Arrow - with cube effect and all between the OSes! Then you can use Super-E and view all four OSes at the same time. It's really not that hard, but you need a ton of RAM!

---

### Post by RedPandaFox on 2008-09-15
> **billgoldberg said:**
> lol

A PC with less than 1 cpu. 

lol

--

I guess you meant less than two.

I only have one cpu on my laptop (and not the fastest one) and I can run any OS in a VM.

No, it told me I have less than 1. I told it to use 1CPU and it told me something like "You have entered more CPUs than you have"

---

### Post by LaRoza on 2008-09-15
> **RedPandaFox said:**
> No, it told me I have less than 1. I told it to use 1CPU and it told me something like "You have entered more CPUs than you have"

Enter zero. It may be indexing from 0, like most logical people.

---

### Post by RedPandaFox on 2008-09-15
> **LaRoza said:**
> Enter zero. It may be indexing from 0, like most logical people.

Didnt have a 0 option

---

### Post by dgrafix on 2008-09-24
> You got any info on how to set this up?

Sure.

Go to [www.easyvmx.com](www.easyvmx.com) and create your VM. This will create you a file. Then go to vmware's site and download the free "vmware player" for linux (or windows) and then simply open the file you generated with the vmware player. I think there is a link to this under useful links on the easyvmx site.

This will give you a virtual machine complete with virtual bios. Put in your windows/dos cd and reboot the VM from the menu. Basically treat everything happening in that window as a separate PC. You can have as many of these as you like.

Whe whole thing (windows, apps and files on the C drive etc) will be stored in a special single virtual machine file (bit like an image) in your home folder (or wherever) which can be easily backed up.

And yes you can use the compiz cube with it.

---

