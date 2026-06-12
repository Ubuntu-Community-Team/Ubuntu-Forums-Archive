---
title: "Rumours of Ubuntu shooting self in the foot???"
date: 2018-01-19
forum: Ubuntu, Linux and OS Chat
---

### Post by Richard_York on 2018-01-19
I've just been told that newer Ubuntu versions no longer work on many computers, and that people are abandoning the system in droves. What's the truth in this?

I write as one who enjoys Ubuntu because (i) it's enabled us to continue using old machines otherwise past their sling-by date, (ii) it's friendly to use, and (iii) it's not paying the Gates corporation. But I don't understand it, nor most of the acronyms, abbreviations, nor tech stuff, and am unlikely to do so, so I'm probably anathema here, sorry! But it has done a very good job running the applications we want to use, so that's good enough for us.

Both our desktop & laptop machines are fairly early-21st Century 32 bit and both slowing down. Since everything seems to be moving to 64 bit, I asked my local friendly computer shop about buying a refurbed newer computer, for me to install Ubuntu 16 LTS. ( I'd tried 16 on one of our laptops last year and it just refused to work, when I was told that the 64 bit version is really needed.) He enthusiastically encouraged me onto Ubuntu 3 or 4 years ago.

Now he reckons that from 16 on, there are frequent problems with displays not working, cooling fans failing, and more.  The machine he's selling has Windows 10 already on it, and it'll make no difference to him whether I keep with Windows or re-format & install Ubuntu - though he also reckons 16 onward are much harder to install. He's shown himself trustworthy & helpful in the past, so now I'm puzzled.

Obviously you're here as Ubuntu enthusiasts, so I expect you to shoot his views down, but I'll welcome any information on where this is coming from, and where it's going.
With thanks.

---

### Post by QIII on 2018-01-19
On what basis has he formulated these conclusions?

---

### Post by kansasnoob on 2018-01-19
The very early 16.04 (Xenial) kernels presented problems for me on a variety of older hardware but all is good now - at least I haven't encountered any big problems. Something I find very important is to avoid the later HWE kernels by sticking with the 16.04.1 images (always stick with the first point release images of each LTS):

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Also if you're shopping for "new" used stuff avoid AMD GPU's for now until they get things sorted out:

[https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

Regarding 32 bit, Xenial will be upgradeable to Bionic around August 2018 so those 32 bit machines could conceivably be used until 2023 with no problem.

There have been other changes, like Ubuntu switching from the Unity DE to GNOME Shell, and the occasional nasty bug like this:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1734147](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1734147)

There are always potential hardware compatibility issue to be considered when shopping for new stuff.

But the sky is not falling :)

---

### Post by kansasnoob on 2018-01-19
One thing i left out, why replace Windows with Ubuntu? I'm a big believer in dual-booting.

I've rebuilt a couple dozen computers recently using mostly 7 to 8 year old components at an average cost of $80 each and there is a lot of really great Intel stuff out there.

---

### Post by TheFu on 2018-01-19
There are no guarantees.

Ubuntu is the flagship distro from Canonical and needs to target the newest, hottest, computers to be competitive and continue growing in happy users.  That could leave older computers behind, since they don't have all the hardware necessary to keep up. That is just for the flagship "Ubuntu Desktop."

But there is good news.  Ubuntu has lots of other distros, like Xubuntu and Lubuntu and Mate which do support older computers, including 32-bit ones.

As for the computer guy - who can say why he said what he said?  Maybe keeping up with new Linux distros/releases has become too complex for someone who makes most of their money supporting Windows?  As I get older, I find that I just don't care anything about Microsoft or Apple stuff and don't want to know or touch it.  It isn't worth my time, since I barely use Windows and will never touch anything made by Apple (political reasons). I could understand someone else feeling the opposite.

The last month or so, lots of news has come out regarding CPU security problems for pretty much all CPUs made the last 20 yrs.  Support for CPUs, formal support that is, is 5 yrs.  So CPUs older than that will not be getting corrective updates unless the updates happen to work which are the same as needed for newer CPUs.  80% of my servers are older than 5 yrs, so they won't get CPU firmware updates specifically targeted.  I don't think the sky is falling.  Most of these servers have very low attack probabilities. They are for internal use only, not on the internet.

16.04 changed many things from 14.04; some good and some unwanted.  I only use LTS releases, so don't have direct knowledge with the intermediate, developer, releases like 17.04 or 17.10.  I have read about some huge changes in 17.10 which do change things that have been core to Linux since 1992, X11 is replaced by Wayland.  My workflow is completely dependent on X11, so wayland is pretty useless to me at this point.  18.04 will almost certainly include those changes, but with a backwards compatible X11 mode. There are no guarantees, but I'm not concerned.  Linux is very flexible and it isn't like anyone will force a replacement OS onto us in May 1.  We have over a year for our 14.04 server systems before a newer release is necessary.  Some 14.04 desktop distros lose support this year and many 14.04 desktop applications have already lost whatever support they had.  Canonical doesn't support every application on our systems after all.

If you want a newer computer, fine.  Computers do wear out.  I have a solid Dell laptop from 2010 that has a repeating key issue, sometimes.  I'll see 'd' entered into whatever window was left up a few times a week.  It is always the 'd' key.  Something about the way the keyboard wiring is connected to the motherboard.  Folks say that replacing the keyboard doesn't help.  The battery for that laptop is well beyond help too.  The laptop hasn't moved from the shelf where it is running today in about 5 yrs.  Battery is used only for a few minutes a year these days.  I've switched to smaller, lighter, longer battery, laptops for travel.  After 2-3 yrs, my travel laptops start to have small issues too, usually keyboard related. 
My servers have issues from time to time, usually related to a failed HDD or something easily replaced like a PSU or video card.  Computers wear out, especially the moving parts things.  But the heating and cooling cycles also cause wear and tear on any electronic device. Just turning them on and off and temperature changes make connections just a little looser over time. That impacts USB ports, printer ports, and soldered connections.  Plus there is the vibration from the fans and HDDs.  All of that adds up, until one day, there is a power off event that lets the computer cool sufficiently .... and it won't boot ... ever ... again.

I'm looking at a newer "server" to replace some of my older 2010-ish servers.  I think $400 should replace 3 of those older computers with a hot new CPU+motherboard+RAM.   That will drop the power bill a bunch (3x125W vs 1x65W) and provide better performance.   I want to have 2 "servers" each capable of running all the stuff alone, so should 1 fail, the other will pick up and go.  Desktops are less important to me.  Heck, a Raspberry-Pi v3 ($48 all in) is probably sufficient for a desktop these days.  I run most things on the servers anyways, so a powerful desktop just isn't needed.  
I can't completely switch to a $50 tablet device, though I am close.  A keyboard and tablet do get really far today.  Main issue for me with any tablet is all the spying those devices perform, so I limit use to very specific things.

So, there you have a slightly different viewpoint.  I'd wait and see. No need to worry about something that might not happen until 2020, right?  Even then, there will be a fallback using LXDE or XFCE or Mate.  32-bit computers aren't completely dead and there are specific distros planned to keep working on those, even if Canonical forces the low-end Ubuntu guys to drop it. There is always debian.

---

### Post by oldfred on 2018-01-19
Some newer UEFI  computers are more difficult to install into as vendors have not fully compiled with UEFI standards. And vendors early on (5 yrs ago), did not even have good implementations of UEFI (did not fully work with Windows either).

And UEFI is a bit more complex as it is both the newer UEFI and has a compatibility mode for older BIOS. So more selections. And UEFI itself has some more settings than older BIOS which may be required.

Video has always been an issue. Newer proprietary video cards/chips often need proprietary drivers, so boot parameters required to initially boot.
But most systems that are a year or two old have all the work arounds available if you look for that vendor/model or similar models.
If you get a middle of the road system from 2 years ago and replace HDD with SSD, you will have a very good system. 
Some of the high end gamer laptops with dual video and more special hardware take more effort to install.

My two desktops just worked, but did require a few UEFI settings before install.
And my now 10 year old 64 bit laptop with 1.5GB RAM still runs 16.04, but a bit slow compared to newer systems.

---

### Post by Chanath on 2018-01-19
> **kansasnoob said:**
> One thing i left out, why replace Windows with Ubuntu? I'm a big believer in dual-booting.



If I could, I'd even add Mac OS too.

---

### Post by Richard_York on 2018-01-20
Thank you for all these, in many ways that's reassuring. It also reinforces how much I don't know - as I said, we use Ubuntu not for the joy of computers but because it does the job, and its politics suit us. So I have to admit that even talk here of Shells, UEFI, and kernels goes over my head - sorry! But it may be that I can learn how to dual-boot, this sounds worth trying. There's always the fear of taking one step too many in the dark (they're mostly in the dark for me!) and crashing and losing everything, but I'll investigate.

The shop owner's source for saying this stuff, he said, is partly a colleague in the business who's had repeated problems as described with his customers, he's read of such problems with more, and a number of his own customers who previously liked Ubuntu & now gone back to Windows following repeated failure of equipment. I think his customers are mostly into gaming, so will need much higher spec than us. We mainly use Libre Office, Gimp, music notation, and the internet, but no gaming. 

If he hadn't been so straight and trustworthy in the past I'd suspect him of spinning me a line straight away with all this, but other than the sensible suggestion that with the sheer complexity of everything, Ubuntu is something he's got out touch with, I can't see why he'd gain from all this. It's a small business, dependent on good relations and feedback.

Meanwhile I admit to having weakened and bought the 5yr old machine - whatever I end up using it with. Our ancient desktop, (significant parts of it go back to 2001, and I think none of it's newer than 2011), is frequently having periods of greying out the screen while it thinks, so more processing power seems a good idea.
The newer one's spec is
 [FONT=Arial]Intel i5-2400
          Asus P8Z68-V LX Mainboard
          8GB Kingston HyperX DDR3
          ATI HD6790 1GB PCI-E Graphics Card
          CoolerMaster Centurion 530 Case
          DVD-RW
          320GB Hard Disk
          USB Wifi adapter 
          Windows 10 Pro x64[/FONT]

So I hope this'll do the job.

Again, thanks for your replies here, they're appreciated.

---

### Post by sudodus on 2018-01-20
> **kansasnoob said:**
> The very early 16.04 (Xenial) kernels presented problems for me on a variety of older hardware but all is good now - at least I haven't encountered any big problems. Something I find very important is to avoid the later HWE kernels by sticking with the 16.04.1 images (always stick with the first point release images of each LTS):

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Also if you're shopping for "new" used stuff avoid AMD GPU's for now until they get things sorted out:

[https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

Regarding 32 bit, Xenial will be upgradeable to Bionic around August 2018 so those 32 bit machines could conceivably be used until 2023 with no problem.

There have been other changes, like Ubuntu switching from the Unity DE to GNOME Shell, and the occasional nasty bug like this:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1734147](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1734147)

There are always potential hardware compatibility issue to be considered when shopping for new stuff.

But the sky is not falling :)

I agree very much with kansasnoob. In addition, I would suggest that you try several Ubuntu community flavours with a lighter desktop environment than standard Ubuntu: Lubuntu, Ubuntu Budgie, Ubuntu MATE and Xubuntu. Try them live without installing, and install the flavour that you like best. See this link and links from it,

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

> **Richard_York said:**
> Thank you for all these, in many ways that's reassuring. It also reinforces how much I don't know - as I said, we use Ubuntu not for the joy of computers but because it does the job, and its politics suit us. So I have to admit that even talk here of Shells, UEFI, and kernels goes over my head - sorry! But it may be that I can learn how to dual-boot, this sounds worth trying. There's always the fear of taking one step too many in the dark (they're mostly in the dark for me!) and crashing and losing everything, but I'll investigate.

The shop owner's source for saying this stuff, he said, is partly a colleague in the business who's had repeated problems as described with his customers, he's read of such problems with more, and a number of his own customers who previously liked Ubuntu & now gone back to Windows following repeated failure of equipment. I think his customers are mostly into gaming, so will need much higher spec than us. We mainly use Libre Office, Gimp, music notation, and the internet, but no gaming. 

If he hadn't been so straight and trustworthy in the past I'd suspect him of spinning me a line straight away with all this, but other than the sensible suggestion that with the sheer complexity of everything, Ubuntu is something he's got out touch with, I can't see why he'd gain from all this. It's a small business, dependent on good relations and feedback.

Meanwhile I admit to having weakened and bought the 5yr old machine - whatever I end up using it with. Our ancient desktop, (significant parts of it go back to 2001, and I think none of it's newer than 2011), is frequently having periods of greying out the screen while it thinks, so more processing power seems a good idea.
The newer one's spec is
 [FONT=Arial]Intel i5-2400
          Asus P8Z68-V LX Mainboard
          8GB Kingston HyperX DDR3
          ATI HD6790 1GB PCI-E Graphics Card
          CoolerMaster Centurion 530 Case
          DVD-RW
          320GB Hard Disk
          USB Wifi adapter 
          Windows 10 Pro x64[/FONT]

So I hope this'll do the job.

Again, thanks for your replies here, they're appreciated.

I suggest that you start by creating a complete backup of the hard disk drive with the original Windows 10 system. It will give you peace of mind, when you create the dual boot system.

An Intel i5 (even 5 years old) is powerful enough for the fancy standard Ubuntu and Kubuntu, but you might still like the flavours with lighter desktop environments (they play multimedia better).

Ask here if you need help during or after the installation. Good luck :-)

---

### Post by Richard_York on 2018-01-20
Thank you again. 
Just for your entertainment, when you mention the Intel i5 as useful "even 5 years old" ... the machine I'm using two write this has AMD Athlon(tm) 64 X2 Dual Core Processor 5200+ × 2   -   which I think may be an upgrade on the original, and though this will mean far more to you than me,  I know it's yet older, and is regularly struggling a little.

Having read all these useful comments, I'm doing nothing for a few days until a fairly heavy patch of work is over so I can concentrate, but yes, I am then very liable to ask for help.  I've not yet read up about it, and will, but installing dual boot currently sounds daunting!

Best wishes and thanks again.

---

### Post by DuckHook on 2018-01-20
A different perspective:

We get lots of enthusiasts on these forums who, for very good reasons, evangelize Ubuntu and Linux. Sometimes, it's a passion for what they believe to be a technically superior OS. There's a lot to be said for that, especially when it comes to power, flexibility, control and absence of malware (which is ***not*** the same as security). However, some do so for reasons that seem to me less good: they made a choice and want to validate that choice by dissing other OSes and bragging about their own. It's a form of "my daddy is bigger than your daddy" schoolyard taunting.

This mentality is not just restricted to some Linux enthusiasts; I find it very prevalent in adherents of proprietary OSes, expecially—sad to say—Apple fanatics (but I digress). The point is, a distinct group of such people whom I've often run into are computer shop owners and, more generally, computer store geeks. They fancy themselves experts. After all, they deal with a certain subset of computer problems all day. Their mistake is that they then take this very limited subset of experiences and generalize it to all of computing. And in their everyday world, where Windows is the undisputed 800 lb gorilla of the desktop, what is your computer shop geek really likely to say about an OS that is lousy for gaming, is largely unsupported by makers of peripherals & add-ons, requires a certain expertise to run, is complicated to install (especially with MS's insistence on secureboot and fastboot), all of which has likely challenged this geek's egocentric vision of their own personal expertise? Wouldn't it be just human nature to diss that OS?

I tinker with lots of old HW. It's a hobby. This puts me in frequent contact with a variety of computer shop owners and erstwhile geeks. At the risk of arrogance, I have to say: most of those who fancy themselves geeks actually know very little about the larger computing world. They look at things through a straw—some of them even have pretty big straws—but it's a straw nonetheless.

I don't know your buddy. S/he may not conform to the limitations I've just described. But whenever I hear all-encompassing statements like: "such-and-such is the best thing since sliced bread," or its converse: "such-and-such is dying and people are abandoning it in droves", my immediate reflex is to put my BS detector on full alert.

---

### Post by mörgæs on 2018-01-21
> **Richard_York said:**
> AMD Athlon(tm) 64 X2 Dual Core Processor 5200+

It's a fine processor. Just give it a light Buntu as mentioned above.

+1 to what Duckhook wrote.

Shooting oneself in the foot is a calculated and clever (though cowardly) act done by a soldier at the front line. He sacrifices a foot but gets sent away from battle, saving his life.

---

### Post by Richard_York on 2018-01-21
Again many thanks, DuckHook and all, for some very thoughtful replies. Maybe our local computer shop man falls into the "tribe" class. Every other human activity seems to generate tribes and sub-tribes after all, (I've met plenty of these in my life as a musician among other things), and self-reinforcement by running down other tribes is an essential activity here ... though given it was he who suggested Ubuntu in the first place and showed me how to use it rather than selling us a newer machine a few years ago, earning himself no money in the process, seems counter to that. Still puzzled!

Since I did end up buying the 5 yr old box to make things go faster here, (for a princely £250), I'm inclined to go for the dual Windows/Ubuntu boot when I get to dealing with this. Uninformed instinct suggests that trying to make a computer be two things at once must dilute its efficiency at either, so I hope it's not going too much OT to ask if it should cope with this without making a pig's ear of both.
The newer one's spec is
 [FONT=Arial]Intel i5-2400
          Asus P8Z68-V LX Mainboard
          8GB Kingston HyperX DDR3
          ATI HD6790 1GB PCI-E Graphics Card
          CoolerMaster Centurion 530 Case
          DVD-RW
          320GB Hard Disk
          USB Wifi adapter 
          Windows 10 Pro x64

Thanks again for your patience :-) 
[/FONT]

---

### Post by sudodus on 2018-01-21
Dual boot means that you have two operating systems installed in the computer, and at boot you can select which of them to boot. So only one of them will run at the same time. You have to reboot in order to run the other operating system.

Of course you have to split the drive space of the hard disk in order to store the operating systems, so there will be less drive space for each of them, but that is the only way that the dual booting will reduce the 'habitat' for each of the operating systems. You have 320 GB drive space, and it is more than enough for a dual boot system, so I would say that both operating systems will be able to run at full power and speed.

[hr][/hr]
I would allocate 100 GB for Windows and 60 GB for Ubuntu (or a community flavour of Ubuntu) and the remaining drive space for a common **data** partition with the NTFS file system. You can store your documents, pictures, music, multimedia files in the data partition, and these data will be available from both operating systems.

**In Windows**

After backup of the original Windows system, you boot into Windows and shrink the Windows partition C: to 100 GB and leave the rest of the drive as **unallocated** drive space. (Do not create partitions from Windows.)

Turn off fast startup in Windows. It is a kind of semi-hibernation, and creates problems in dual boot systems.

**In Ubuntu or an Ubuntu community flavour**

Then you can boot into a USB pendrive with Ubuntu or an Ubuntu community flavour.

[help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Check with

```
test -d /sys/firmware/efi && echo efi || echo bios
```

if the computer boots in UEFI mode or BIOS mode (alias CSM alias legacy mode). The vendor installed Windows in either mode, and things work in both boot modes, but I think it will be easier for you if he installed Windows in BIOS mode. For example, in UEFI mode some major updates of Windows is likely to mess with the bootloader, so that you have to reinstall/repair it in order to boot into Ubuntu again. You should install Ubuntu in the same boot mode as Windows (otherwise it will be possible but more more cumbersome to switch between Windows and Ubuntu).

Use **gparted** to create the partitions you want (use the unallocated drive space),

- A swap partition (I suggest 2 GB, but if you intend to hibernate, you need slightly more than RAM, so in that case 10 GB).

- 50 GB root partition with the ext4 file system

- the remaining drive space with the NTFS file system and the label 'data'.

After that you can start the Ubuntu **installer** from the icon on the desktop, and at the partitioning window select **'Something else'** and select the partitions you created with gparted for root partition and swap partition.

After the installation has finished and you boot into your Ubuntu system, you might want to add a line into your file /etc/fstab in order to mount your data partition exactly as you wish. More about that and other tweaks later.

[hr][/hr]
When your dual boot system is working, you should make a second backup of the whole drive.

---

### Post by TheFu on 2018-01-21
Dual boot used to be fairly easy and not really risky.  Eventually, it will be again, but for the last few weeks, because of lots of security considerations, people with dual boot systems have another worry, MSFT patches.  A number of people have posted in these forums that recent MSFT patches have removed their Linux boots.  

There is another option. The CPU you have now is more than powerful enough to run a virtual machine with Linux (or Windows).  This is an extremely common way for power-users to have multiple OSes on a single computer.  Best part is that what happens inside a virtual machine stays inside the virtual machine.  It is popular enough that there is an entire sub-forum here just about virtualization.  Depending on what you need from Windows (or Linux), a virtual machine might be a good option.

I use virtualization for almost everything.  It is easy enough that my 85 yr old Mom has Windows running inside a virtual machine under Linux for those 2 programs that she needs which only work in true Windows. It also means being able to use both OSes on a single machine, concurrently.  Any computer with a Core2Duo and 4G of RAM can happily run virtual machines. 

Anyway, it is another option and I think it is less risky than dual booting.  It might not fit your needs, but it is an option to consider.

---

### Post by SeijiSensei on 2018-01-21
Another vote for virtualization.  The easiest solution is to install a copy of VirtualBox.  I prefer the method described at [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions), though that may be a bit complex for someone not familiar with Linux.  So just install a copy from the ordinary Ubuntu repositories like this:
```

sudo apt update
sudo apt install virtualbox virtualbox-guest-additions-iso

```
Now you can create a virtual machine and install Windows into it.

The other option to consider, since you already have a machine running Windows 10, is to install VirtualBox on that platform instead and create a virtual machine into which to install Ubuntu.  This is often much easier than the reverse since you need a fully-licensed DVD or ISO image of Win10 to install it in a VB virtual machine.  You may not have one of those, so installing Ubuntu into a VM running in VirtualBox on Windows may be the better choice.  Here's the VB installer for Windows: [https://download.virtualbox.org/virtualbox/5.2.6/VirtualBox-5.2.6-120293-Win.exe](https://download.virtualbox.org/virtualbox/5.2.6/VirtualBox-5.2.6-120293-Win.exe)

---

### Post by monkeybrain20122 on 2018-01-21
> **kansasnoob said:**
> One thing i left out, why replace Windows with Ubuntu? I'm a big believer in dual-booting.
.

You may as well run Windows in VM if you really need it. Since UEFI and secure boot dualboot is hard to set up and a Windows update may destroy it. I personally have had no use for Windows since way back except for one program so I use it in a VM (not work in wine)

---

### Post by lammert-nijhof on 2018-01-21
First I have an HP dc5850 from Oct 2008 almost 10 years old. That is a 64 bit machine running Ubuntu 17.10 now. I am very happy with that new release and for me it is an improvement compared to 16.04. I use a Nvidea propriety driver, so 17.10 automatically sticks to X11, when logging in. Anyway everybody has the option to choose X11 in the login screen. I like some of the gimmicks, like "Night Light", the dynamic # of desktops and the Virtualbox VM appearing in the launcher, if assigned to a separate desktop. It makes switching between VMs very easy.

I have a 32-bit Pentium 4HT  at 3.0 GHz running Peppermint 8. That machine is probably 15 years old. Peppermint 8 is the sexy sister of Lubuntu and based on Lubuntu. I could easily keep running one of those two OSes till 2023 (new LTS release in 2018 + 5 years). I do not expect, that radiant heater P IV will reach its 20th anniversary. With 1GB it can't run Ubuntu itself, so I will not really miss Ubuntu on my old P IV. 

From time-to-time I use Windows, e.g. I still prefer Windows Media Player with WOW and True Bass effect for my music. I run all OSes in a Virtual Machine of Virtualbox. It allows me to look at other Linux distros and new Alpha or Beta versions of the Ubuntu family. I stopped using dual booting in 2011, too much of a hassle when Windows e.g overwrites again the boot-loader. 

A virtual machine has many advantages:
[LIST=1]
[*]You install and you move it from one desktop to your next just by copying the files. [COLOR=#800000]Install it once and use it forever![/COLOR] My XP-VM has been started in 2009 on that 32-bit Pentium 4, when Virtualbox was still owned by Sun. I moved XP to 64-bit 3-core and 4-core Phenoms. I also used that same installation om my laptops with an 2-core AMD Athlon and now on my second generation i5 laptop.
[*][COLOR=#800000]It gives more security.[/COLOR] I run all my banking, paypal and ebay application in a Ubuntu 17.10 VM. I do not use it for Email or general browsing. The firewall is closed for inbound traffic and most of the time the machine is "powered down". I have 3 Windows VMs (XP, Vista, 7) with different virus scanners. I have the Shared Folder/Partition of all VMs scanned weekly by all Win virus scanners.
[*]You can run two or three Oses at the same time using a seperate desktop for each and [COLOR=#800000]switch from Windows to Ubuntu in 0.5 seconds.[/COLOR]
[*]I keep backups of the crucial VMs by running the same installation on both desktop and laptop and I zip them once per month too. [COLOR=#800000]If you **** up an installation, just restore the backup.[/COLOR]
[*]It has become really more efficient on 64-bit machines, it takes avg. 10% to max. 20% more CPU load and they use the graphics cards more directly nowadays when enabling 3D acceleration.  Virtual Machines will run on 32-bit machines like my P IV, but it runs 32-bit OSes only, but the overhead will be larger due to missing HW support.
[/LIST]

---

### Post by mastablasta on 2018-01-22
> **Richard_York said:**
> 
Since I did end up buying the 5 yr old box to make things go faster here, (for a princely £250),[FONT=Arial] 
[/FONT]


if this was just a box it seems quite expensive to me. i better came with some warranty.

win10 pro is a solid OS with many security features built in. it also provides a bit better control over the OS, than the "home" version.

easy tutorial for virtualbox install: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

good luck with whatever you choose to use as the OS.

---

### Post by pteryges on 2018-01-22
Your specs are not too different from mine. CPUs are of a similar vintage, GPU is about the same. My machine runs 17.10 with the Gnome desktop with no problems and likely will for a while yet.

One of the dirty secrets of the computer world is there hasn't been a lot of advancement in CPU technology in the last ten years or so. While the ten years before that saw enormous change, the recent decade has really been about refinement: higher efficiency, less heat, smaller packaging, and on and on. What this means is that, with the exception of machines which were low-end specs when released, just about any decent computer made in the past seven or eight years will be just fine for daily use. You would only need more modern tech if you're need to do something like 3D, CAD, or video editing.

---

### Post by Richard_York on 2018-01-23
This thread gets more & more helpful! Thank you again, all - when I get over this patch of work & get to look into dealing with this I now have great sources of information. Thanks too for patiently writing them in (mostly!!) language even I can understand.

Seems as if setting up a virtual machine might be the answer then, from a quick reading just now. (Once I've read again lots of times how to do it.) And even a simple operator like me can install it?  - not being falsely modest here. I can follow computer instructions but only as long as they're clear & I don't need to understand why I'm doing it, whatever it is!

What excellent company this is.

---

### Post by Richard_York on 2018-01-23
PS to that - my wife asks: if we set it up with virtual Windows plus Ubuntu, do we need separate virus protection for the Windows part of it?
(If this is so off topic as to not belong in this thread, please tell me.)

---

### Post by QIII on 2018-01-23
Whether as a host or a guest, you need to attend to Windows security, including AV.

This is a chat thread, and you started it.  The thread has just naturally ended up here without deliberate off-topic posts, so don't worry.

However, if you do call for specific technical assistance,  please do so in a support area.

---

### Post by mivo on 2018-01-23
> **kansasnoob said:**
> One thing i left out, why replace Windows with Ubuntu? I'm a big believer in dual-booting.

I have never dual-booted any of my machines. For me, dual-booting would double the time I spend on maintenance and updating. My rural Internet connection is pretty slow, and Windows 10 updates are large, frequent and impossible to schedule unless you drop &#8364;200 on the Pro version, and even then control is pretty limited. Plus, there are two 3-4+ GB "feature updates" per year that are not optional (if you set the ethernet connection to "metered", it won't download the monthly security updates anymore, either). I still use it on my desktop, chiefly out of convenience (and I may change that soon because the lack of control and "Windows as a service" are things I philosophically clash with), but if I dual-booted that box, I'd have those updates plus Ubuntu updates, plus maintenance for both. Not an attractive option, for me. I'm also less keen on tinkering with OSes anymore and prefer them to largely just work once set up.

That aside, I generally don't see the benefit (for me), except for hardcore gaming with a focus on "AAA" titles, but in that case I'd probably just use only Windows (or get a console), likewise if I depended on software like Photoshop. Most of my work and hobby activities take place in the browser these days, so either OS is fine for me.

It's just an alternate view, though. And you asked. :)

---

### Post by SeijiSensei on 2018-01-23
Give VirtualBox a run on top of Windows since that will require the least effort on your part.  You just need to install the Windows VB software from the link I gave above.  Then open the VirtualBox Manager, click on New, and walk through the steps required to create a VM running Ubuntu.  You can just point the program at the downloaded ISO image for the Ubuntu version you've chosen; no need to create a DVD or USB to run the installation.  I'd give 2-3 GB of memory to the virtual machine and leave the rest for Windows.  On the big drives we have nowadays, I'd give the machine a virtual disk about 40-50 GB in size.

---

### Post by kansasnoob on 2018-01-24
Most of the hardware I work with is simply not capable of running both a host for a VM and the VM guest itself. I wonder though if a person can create a Windows VM of the existing Windows OS on a PC that originally came with Windows? When I very first started out with Ubuntu (circa 2007) I seem to recall reading a How To Forge how-to that showed how a VM could be created of the existing XP OS and then it could later be installed in Ubuntu. 

I always just opted for dual-booting because it was easy. In some ways it's even easier with Windows 10 than it was with XP. I've seldom encountered the loss of an operating system during re-installation of an operating system or during Windows 10 updates. And I always create full backups before undertaking such a task. There are certain common sense steps to follow when creating a dual boot with Windows - beginning with using Windows own partitioning tool to resize the existing OS.

Since I almost always build my own computers I generally install Windows after installing Ubuntu, but I do create one NTFS partition at the beginning of the drive before installing Ubuntu. It used to be that Windows would get confused and not think it existed on Drive C but that's no longer the case with Windows 10. And I make sure Ubuntu's / partition is a primary partition rather than a logical partition. I don't use a separate /home but if I did I think it would also need to be on a primary partition to keep Windows from thinking it should be wiped during install.

Regardless, my point was, why wipe one before installing another? I feel the same way about testing other operating systems. I don't do nearly as much distro hopping as I used to but I still like to check out what other distros are doing from time to time. I know I've had more than a dozen operating systems all multi-booting on the same machine in the past, but that's been quite a while back.

When I test release upgrades it's not uncommon for me to have 8 to 10 operating systems all installed on the same machine, particularly when testing LTS -> LTS upgrades before they recently modified the HWE cycle. I have to keep a log of what's installed where when I'm doing that so i don't get confused. For 16.04 -> 18.04.1 I should only have to run two tests, one with 16.04 running the OEM kernel and the other with 16.04 running the 18.04 HWE stack.

As with anything the longer you do something the easier (and more commonplace) it becomes. Since I've seldom messed with VM's I'd be lost, but dual/multi-booting is common place to me. Some day I'm sure I'll get bored and decide to play with VM's if I get one of my machines running enough RAM - even used 4GB sticks of DDR2 are kind of pricey.

At the end of the day it all comes down to choice, and that's the true beauty of Linux. I could live to be 110 and still never explore each and every choice available :D

---

### Post by kurt18947 on 2018-01-24
There is one other choice for running multiple OSs. I have a few USB flash drives with full install Linux distros. A 16 GB. flash drive is adequate though I prefer 32 GB. generic (no 'value added' features)drives. The installer on Ubuntu & offshoots make this pretty easy. You just have to careful to install onto the proper drive. I had an issue with this early on and have taken to disconnecting the hard drive(s) before booting live install media. The second flash drive will appear as the target, just install as normal. All my machines have a key that when pressed will give me a choice of boot media. I can also change BIOS boot order to boot first from a USB "hard drive' if one is present. There's always the chance that a USB drive will fail without warning so I'm careful about storing anything of significance on the flash drive install but aside from being slower to boot, it works pretty well and will not touch the existing hard drive.

---

### Post by SeijiSensei on 2018-01-24
> **kansasnoob said:**
> Most of the hardware I work with is simply not capable of running both a host for a VM and the VM guest itself.

The OP has an i5 with 8 GB of memory. I have a similar machine and run virtual machines on it with no problem. I've also run VirtualBox on a ten-year-old AMD-based HP notebook.

---

### Post by kansasnoob on 2018-01-24
> **SeijiSensei said:**
> The OP has an i5 with 8 GB of memory. I have a similar machine and run virtual machines on it with no problem. I've also run VirtualBox on a ten-year-old AMD-based HP notebook.

I'm limited to 4GB of RAM on my most powerful machines and I've found that anything less than 3GB is really just frustrating for decent browsing. I plan on shopping for RAM so I can upgrade at least one box to 6GB or 8GB RAM. Then I should be able to play with some VM's (just for fun). In fact I was looking on Ebay this morning and 4GB sticks are still running $30+. Some day I'll stumble on some for $20 or less :D

---

### Post by poorguy on 2018-01-24
> **kansasnoob said:**
> I was looking on Ebay this morning and 4GB sticks are still running $30+. Some day I'll stumble on some for $20 or less :D
Keep looking as I find DDR2 and DDR3 4.0 gig sticks all of the time for $20.00 for desktops although if needing laptop memory I have no clue what it is going for.
You got to buy when you find the deals or it can be gone when you go back and look from my own experience.

---

