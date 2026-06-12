---
title: "thinking about installing on main pc.."
date: 2013-10-13
forum: Ubuntu, Linux and OS Chat
---

### Post by HfCThkM on 2013-10-13
Hi all!

I havent posted much because I'm in the process of working on getting my name back, HOWEVER, Ive got a question/just looking for advice..

I've got Ubuntu 12.04 LTR installed (dual booting) on my old pc, which originally was supposed to just make my pc work as windows was slow, I mean. SLOW. Ever since I got it (about.. 3 years ago) I've gotten a new pc running windows 8. I am a gamer, but I hate the wine library. Even so, I've been greatly debating on installing Ubuntu 12.04 LTR on my main pc as a dual boot as well. Keeping windows 8 mainly for a backup in case ubuntu needs a re install or other reason. I WOULD be wiping the pc, so any games ect. would be gone. I dont game a whole lot so its not a huge deal for me..

what do you guys think?
boyo

---

### Post by boyo1991 on 2013-10-13
for the record, OP is me, so I can be reffered as such, and seeing as I dont any longer have that crazy name (the forum via SSO gave me a new account, thanks again iowan! :D) I cant modify the post.

What I'd like to add is that after a bit of looking, it does not work with my system (I already sort of assumed it wouldnt, but, I thought I may have found a workaround..) BUT! Ive done a little experimenting, I got DSL (damn small linux) and it was more of a proof of concept, Id really rather not use a virtual machine, so, I'm looking for a straight up emulator of ubuntu.

Personally I'd like to get 12.04 LTR kernel running within windows 8 WITHOUT VM. Even if its just emulated and the underlying processesses are really the windows kernel, I'd still much rather do it through an emulator.

Theyres even a basic linux kernel written in javascript, so Im certain this isnt too far away.. but i want it to have a gui and be native so I can at least have basic functions..

sorry if this was "TLDR" lol
Boyo

---

### Post by sollidsnake on 2013-10-13
They say 13.04 is much faster than 12.04. Also 13.10 is comming this week and may bring speed improvements with it. But, if you're looking for the best performance, you might want to try XFCE (Xubuntu), LXDE (Lubuntu) or even KDE (Kubuntu) with no effects. Those are more lightweight desktop environment and usually much faster than Unity (Ubuntu default desktop environment). Just google those names and see if you like them :). Also, once you've got one distribution installed, you can always install other desktop environment if you didn't like (or wasn't fast enough) the default one.

---

### Post by boyo1991 on 2013-10-14
i know of these variants, but they are not compatible with my hardware. (as far as ive found)

also, id rather not make a burn disk, i could do this with standard ubuntu (and im thinking about doing this.) but with wubi, ubuntu is not compatible.

Unlike so many others, Im a huge fan of unity. It may not be the greatest as far as performance, but im not worried about that too much because:

a)any linux distro is already faster than windont's, and that works fine already for me

b)ive got more power than i need. im a developer, but more just for fun. I.e. I am not able to make intensive apps (of course i set out to crash my pc XD)

kubuntu and xubuntu to me are like htc sence to android. I dont like it. I perfer the official with my own modifications. Not that theyre bad softwares, just that its not what I want.

thanks for the input!
Boyo

---

### Post by mastablasta on 2013-10-14
> **boyo1991 said:**
> Personally I'd like to get 12.04 LTR kernel running within windows 8 WITHOUT VM. Even if its just emulated and the underlying processesses are really the windows kernel, I'd still much rather do it through an emulator.


you will have to make that yourself if you want it. i mean to run an os within the OS without virtual mashcine (which is like an emulator anyway..)

> **boyo1991 said:**
> i know of these variants, but they are not compatible with my hardware. (as far as ive found)

that's new. but you are porbably wrong. since they all have same kernel and drivers are part of kernel in linux so hardware working in lubuntu will work in xubuntu, kubuntu etc.

> 
kubuntu and xubuntu to me are like htc sence to android. I dont like it. I perfer the official with my own modifications. Not that theyre bad softwares, just that its not what I want.


That's not true. Though they share the kernel and programmes they are in essence their own projects. it's kind like saying that you like Luna desktop more than Aero in windows. Luna and Aero are desktop environemnts. and KDE is a desktop environmet as is XFCE. they both can run Gnome programmes just fine. and Gnome can run KDE programmes. in fact you canrun Gnome and KDE programmes in windows as well. the difference is in philosophy and libraries that are used and the way desktop is drawn. for example Gnome (Unity) tends to hide settings in GUI so as not to overwhelm the user. While KDE will have all settigns shown. Gnome does changes instantly when you select them (e.g. them change), KDE requires you to click apply. KDE is a lot more windows like in some things. it even has control panel.

---

### Post by grahammechanical on 2013-10-14
I am a bit confused as to what you want to achieve. Windows 8 is incompatible with a Wubi.exe. So, no running of any version of Ubuntu inside Windows 8 as if running in a VM or emulator. The developers have taken the view that it is not worth the time and trouble to get Wubi.exe working. I do not blame them.

Since 12.10 Ubuntu has been compatible with secure boot. That feature has now been included in the 12.04.2 and 12.04.3 (the latest) releases of 12.04. Linux has been compatible with UEFI and GPT for a few years now.

There are _potential_ problems with installing Ubuntu on a machine running Windows 8. We get people posting about it on this forum. On the other hand, people usually come here with their problems. They rarely come here to post about how successful installing Ubuntu was. So, it is not possible to say how high the risk is but there is a risk of hitting a problem.

Another issue is with machines having some form of hybrid graphics. It is due to the lack of proprietary video drivers and the difficulty of writing open source drivers with next to no cooperation from the the graphic card manufacturers.

The main thing to consider when comparing Ubuntu versions is the length of support - 12.04.3 has support until April 2017 but 13.04 only has about 3 months support left and 13.10 will have only 9 months support when it is released.

On the other hand, a lot of work has been done to reduce memory usage. I am seeing a drop of about 15 - 20% in memory usage in 13.04/13.10 compared to what was happening in 12.04. I cannot say if these improvements have been worked into 12.04.3. Also, Unity 7 is much snappier than the version of Unity in 12.04. 

Regards.

---

### Post by leclerc65 on 2013-10-14
> They rarely come here to post about how successful installing Ubuntu was. 
There is reasons for that.
UEFI is a sorry state of affair, every manufacturer has its own way of implementing it.

Here is how I did:
 Machine: ASUS M51AC desktop - I add a 128GB SSD - Modify boot CSM Support to FULL
 Insert Ubuntu 12.04.3 DVD, during boot, hit F8, choose Asus DVD UEFI
 Install Ubuntu on the SSD - Won't boot - Use Boot-Repair
* from here on it's business as usual (the old way) *
 Install Mint Maya on the SSD - boot into Ubuntu - Use update-grub

I haven't yet installed another distro, but I believe I don't have to go thru that UEFI crap anymore - as long as I keep the 1st (Ubuntu) intact.
I reserve 15G for each distro, so my SSD has plenty of place to go. Next one will be Ubuntu 14.04 LTS.
Essentially I paid MS for Nothing, and the only thing I recovered is 1.5T of storage from the Data partition of the 2T drive A.
If anybody use this instruction on a Samsung or something, I cannot guaranty that will work, hence the silence.

---

### Post by boyo1991 on 2013-10-15
> **mastablasta said:**
> you will have to make that yourself if you want it. i mean to run an os within the OS without virtual mashcine (which is like an emulator anyway..)



that's new. but you are porbably wrong. since they all have same kernel and drivers are part of kernel in linux so hardware working in lubuntu will work in xubuntu, kubuntu etc.



That's not true. Though they share the kernel and programmes they are in essence their own projects. it's kind like saying that you like Luna desktop more than Aero in windows. Luna and Aero are desktop environemnts. and KDE is a desktop environmet as is XFCE. they both can run Gnome programmes just fine. and Gnome can run KDE programmes. in fact you canrun Gnome and KDE programmes in windows as well. the difference is in philosophy and libraries that are used and the way desktop is drawn. for example Gnome (Unity) tends to hide settings in GUI so as not to overwhelm the user. While KDE will have all settigns shown. Gnome does changes instantly when you select them (e.g. them change), KDE requires you to click apply. KDE is a lot more windows like in some things. it even has control panel.

okay its been covered now. yes its "compatible" but i should have specified wubi. not just the .iso.

yea most of what i said was totally incorrect and i have no idea why i even allowed myself to blurt it out. allow me to clarify:

Wubi is not compatible with windows 8. i decided to do a workaround. still didnt work. i dont like kubuntu or xubuntu not because they are not ubuntu, because they are, but because they are not the vanilla ubuntu that i like. just like how i hate htc sence because i love the vanilla android. as htc sence is a *similar* idea to what i mean. no additions, or stripdowns, just what the standard is.

*sigh* I guess I've just got to bite the bullet and get myself a blank disk and do this thing :P

next time you see me, I'll be hopefully running ubuntu 12.04 LTR on my main pc..

btw I'm going with 12.04 because I feel in the long run it will be the most stable, and all of the speed enhancements ect. will be brought in with updates in the future.

---

### Post by mastablasta on 2013-10-16
ah ok you like "vanilla" versions. well that is your choice then. Kubuntu used to be Canonical project and 12.04 is the last one. they developed two Kubuntu and Ubuntu actually. But Kubuntu is dropped after 12.04 and everything transfered to community. i use what works best for me andalso what i like. If Ubuntu works best for you and you like it then you are more than welcome to use it. eventhough quite a few other Ubuntu versions have official cannonical backing.

i think it's more the issue of Windows 8 not being compatible with Wubi. they (microsoft) really took the effort to make sure something like wubi can't run. it ran quite well in xp and 7. and it's not a bad idea to introduce linux to users liek that (again i think something similar and more easilly setup should be done with virtual box. For example see linuxliveusb creator (lili) and it's virtualise this key function via portable virtualbox.

anyway i think wubi source code is available, just maintainer gave up due to massive changes in windows 8.

---

### Post by boyo1991 on 2013-10-16
i caved in as i didnt have a cd available big enough and got lubuntu 13.04 running successfully on my main machine.

i like unity a bit more, but this is still nice :P

---

### Post by mastablasta on 2013-10-17
you can install default unity by installing ubuntu destkop in software center ;-)
and then removing lubuntu (e.g for 12.04): [B][http://www.psychocats.net/ubuntu/pureubuntuprecise](http://www.psychocats.net/ubuntu/pureubuntuprecise)

another option is to use minimal iso found here: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
and then install ubutnu desktop. here is a tutorial with icewm (just replace icewm with ubuntu desktop package :-) ): [/B] [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

