---
title: "Ubuntu 10 with Virtualized Windows 7"
date: 2011-02-12
forum: Virtualisation
---

### Post by Gerbilkit on 2011-02-12
I am at the moment thinking about switching to Ubuntu 10. I did make the full switch to Ubuntu 9 before, and my desktop (not my primary work environment) is running Ubuntu 10.  I liked Ubuntu, I didn't use it long enough to become as comfortable as I am in windows, but I liked it.  The problem was that I could not get around my need for windows specific applications, and I never will.

*I will make a specific request here. I do not want to hear about open source alternatives to my windows programs. I regularly use Photoshop/Fireworks/Flash CS5.  I am not interested in Gimp/whatever else. Yes I have used them, yes they are good programs, I just don't want to use them. Same with media monkey vs amorak etc.  I am not dissing the open source alternatives, and I don't want to go into it. I think it should be enough to say that my preferences are different. I know this won't be enough on these forums and I will still be subjected to many posts explaining how evil MS programs are and how great open source is. But I will request anyway, my preferences require MS specific programs, that isn't changing, period.*

Anyway my OS at the moment is WinXP. I like XP, it's simple, and I am used to it. I never have to wonder where something is or how to make something work, I don't have to jump through any hoops to make programs work. That being said, XP will become obsolete.  I like Ubuntu and I would like to use it, and I have an install disk for Windows 7 32 bit Ultimate.  I have been reading about running CS5 in wine. The consensus I am hearing is that CS5 doesn't work too well in wine. I liked some things I was reading virtualization via virtual box or VMware.  Especially where people have gotten seamless integration between the two OSes.  Before this I was planning on dual booting, however as I would be working with so many windows programs, I was questioning why even bother using ubuntu. However if I could use ubuntu with windows virtual machine I could use ubuntu, while still being able to run my windows program.

My question is what kind of performance hit would I be looking at for this? Could I have a dual boot scenario where I could boot into either OS, or run ubuntu with virtual windows and have all of them access the same file space? Would CS5 be able to run at a decent speed in VB? I have Intel Core Duo Processor (2Ghz) and 2 GB ram.  I would like to have ubuntu as my main OS but still be able to run MS programs in my main workspace, and be able to boot in full windows if the situation was ever needed (gaming etc) but also access the same filespace in all cases? Is this realistically possible? Has anyone managed to do this?

---

### Post by gordintoronto on 2011-02-12
Virtualbox should let you do what you want, and you could also dual-boot. You might find RAM is a bit of an issue. For the applications you use, I would install 4 GB to use them under Windows 7, whether Ubuntu was involved or not. Disk space could also be an issue; if you have a dual-boot Windows 7 and also Windows 7 in a virtualbox, they each need how many GB?

One thing which could become tiresome is system updates, if you have Ubuntu plus two versions of Windows 7. A big Patch Tuesday can take half an hour to install, and you would need to do it twice.

---

### Post by ingramproductions on 2011-02-12
If you use Ubuntu as your main OS, and have Windows 7 running as a virtual machine under VMware Workstation, then you can use the Unity Mode. This allows you to have a windows start menu in Ubuntu and allows you to run your Windows programs like they are native applications (they are still running like a normal virtual machine, but they are displayed in their own window, just like a native application.)

---

### Post by Gerbilkit on 2011-02-12
> **ingramproductions said:**
> If you use Ubuntu as your main OS, and have Windows 7 running as a virtual machine under VMware Workstation, then you can use the Unity Mode. This allows you to have a windows start menu in Ubuntu and allows you to run your Windows programs like they are native applications (they are still running like a normal virtual machine, but they are displayed in their own window, just like a native application.)
Well if this happens with no restrictions or serious performance benefits then I guess dual boot has no point. But that's mainly my question, what kind of performance cost am I looking at? For what I do, I have no problem on my laptop currently running Photoshop/Flash/Fireworks etc, even at the same time.  Would this be possible with VMware? Are there any programs that do not work under virtualization?

Also I'm assuming with unity the windows virtual machine can access the same filespace as ubuntu?

---

### Post by YesWeCan on 2011-02-14
I a run VirtualBox with Ubuntu 10.04.1 64-bit desktop as host and Win7 Home Premium 64-bit as guest on a system with 8GB of RAM and an Intel quad-core uP, with 4GB allocated to the guest.

YouTube video runs fine in full screen mode on Win7. Almost imperceptible difference to running on the host.

I'd say VirtualBox is excellent and you can run all your programs. The snapshot facility is good and you can back the whole thing up using Ubuntu. It really depends on your mobo hardware as to how fast it will run. I second the advice to use 4GB min. Haven't tried video over Skype, for example, although you can run this in the host anyhow. Gamers will want native Windows.

VirtualBox also allows you to have a sort of merged desktop so that it seems like you are running Ubuntu and Windows on the same desktop.

---

### Post by YesWeCan on 2011-02-14
I should add that you are better off running a 32-bit guest as it will be less memory intensive and it won't matter much at all to performance.
I am also running an old Gigabyte mobo with Athlon 4200+ dual-core and Ubuntu 10.04.1 64-bit host and 2GB RAM and Win7 HP 32-bit guest. Win7 runs just fine on 1GB RAM for non video apps. In fact, Win7 seems to be more responsive than Ubuntu 10.04 32-bit as guest. XP as guest is the fastest and I quite like using it. But 2GB is barely adequate and Limits how many apps you can run while VB is running.

---

