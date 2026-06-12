---
title: "Virtual Machine recommendations"
date: 2012-06-04
forum: The Cafe
---

### Post by Dragonbite on 2012-06-04
I just got an old computer (Dual Core, up to 8 GB of RAM) and am thinking of using it as a replacement for the family computer. Then a co-worker got me thinking.  What about virtualizaing?

If I put a barebone host with virtualization software on top of it, could I have it so when the family boots up the computer it boots up the host and then immediately (hopefully without notice) boot into a specified virtual machine running the desktop system?

I was thinking of having it run a Linux distribution, but would love to be able to run Windows 7 if I so choose sometime later.

Some of the reasoning if for
[LIST]
[*]Being able to snapshot and store (backup) the image onto a networked hard drive
[*]Enable easily multi-booting without having to worry about GRUB
[*]Enable running a headless server-orientated VM such as a web server, automatically in the background
[*]Make upgrading safer by being able to work out the kinks in a second VM before moving everybody over (and finding out it doesn't work!)
[/LIST]

I don't know if the above is very feasible.

Would it be better to run it on a barebone systems such as VMWare ESXi or a Linux distro?
Would it be better to, if on a Linux distro, run VMWare, VirtualBox or KVM?
Would any enable hardware acceleration?  Games will be played on it, but not the resource-intensive ones (unless you count Super Tux Kart, Neverball and the like)

---

### Post by Bachstelze on 2012-06-04
I don't know much about virtualisation besides the occasional VirtualBox, but I think Xen sounds like what you want. Last I checked it was not very well supported in Ubuntu, so you might have to use another distro (when I researched this a couple months ago, OpenSuse looked like the best choice--but I lost interest in the whole thing before actually implementing it :p).

---

### Post by forrestcupp on 2012-06-04
Sounds like VMware ESXi might be a good choice for you. I don't know how hard it would be to set it up. One thing I wonder is whether VMware ESXi can pass through the real hardware. If not, going the Xen route in openSUSE might be a better option.

---

### Post by Bandit on 2012-06-04
If you wanted to play any games I would dual boot before fooling with a VM. VBox is free, but mehh when it comes to hardware accl. VM Ware can be expensive. Dual booting is free and no issues with hardware then.

---

### Post by stmiller on 2012-06-05
> I just got an old computer (Dual Core, up to 8 GB of RAM) and am thinking of using it as a replacement for the family computer. Then a co-worker got me thinking. What about virtualizaing?

What is the exact processor? Does it support VT-x?

---

### Post by sandyd on 2012-06-05
> **Bandit said:**
> If you wanted to play any games I would dual boot before fooling with a VM. VBox is free, but mehh when it comes to hardware accl. VM Ware can be expensive. Dual booting is free and no issues with hardware then.

Vmware ESXi is free.
I use it.
Its nice if you want a GUI to configure the VMs though.

---

### Post by Dragonbite on 2012-06-06
> **stmiller said:**
> What is the exact processor? Does it support VT-x?

How do I determine if it does or not.

---

### Post by CharlesA on 2012-06-06
> **Dragonbite said:**
> How do I determine if it does or not.
[http://www.howtogeek.com/howto/linux/linux-tip-how-to-tell-if-your-processor-supports-vt/](http://www.howtogeek.com/howto/linux/linux-tip-how-to-tell-if-your-processor-supports-vt/)

---

### Post by stmiller on 2012-06-06
Also intel's website will list processor features, including vt-x


Ex:

[http://ark.intel.com/products/42915/Intel-Core-i5-750-Processor-%288M-Cache-2_66-GHz%29](http://ark.intel.com/products/42915/Intel-Core-i5-750-Processor-%288M-Cache-2_66-GHz%29)

---

### Post by Bandit on 2012-06-06
> **sandyd said:**
> Vmware ESXi is free.
...

Hmm /scratch head..

I assumed it was a better version of regular VM Ware.. :)

I used regular VM ware in College, how does it fair against their standard offerings? I tried to convince my college professor to switch to VBox to save money on license fees. All they used it for was to give the students a hands on feel for installing WinServer.

---

### Post by forrestcupp on 2012-06-06
> **Bandit said:**
> Hmm /scratch head..

I assumed it was a better version of regular VM Ware.. :)

I used regular VM ware in College, how does it fair against their standard offerings? I tried to convince my college professor to switch to VBox to save money on license fees. All they used it for was to give the students a hands on feel for installing WinServer.
VMware ESXi is the one that allows you to run VMs without a host OS. Pretty cool concept.

---

### Post by CharlesA on 2012-06-06
> **forrestcupp said:**
> VMware ESXi is the one that allows you to run VMs without a host OS. Pretty cool concept.
ESXi is the OS. ;)

Xen does a similar thing.

---

### Post by sandyd on 2012-06-06
> **Bandit said:**
> Hmm /scratch head..

I assumed it was a better version of regular VM Ware.. :)

I used regular VM ware in College, how does it fair against their standard offerings? I tried to convince my college professor to switch to VBox to save money on license fees. All they used it for was to give the students a hands on feel for installing WinServer.

Vmware ESXi is like a downgraded version of VMWare ESX.
Basically, everything is managed through the VSphere Client.

Its hard to explain unless you try it yourself.

I like it, however, because it is really easy to create complex networking setups using vswitches.

---

### Post by Metallion on 2012-06-07
Why not give Wakame-VDC a try? It's basically kvm with a web ui around it that allows you to create instances from your VM images. It also has that snapshot functionality you want.

We've got a DVD that sets up Ubuntu lucid with Wakame on top. Just install that, open a browser and connect to your machine on port 9000. Then log in with username demo and password demo. Should work out of the box.

[http://dlc.wakame.axsh.jp.s3.amazonaws.com/beta/11.12/wakame-vdc-11.12-amd64.20120202.iso](http://dlc.wakame.axsh.jp.s3.amazonaws.com/beta/11.12/wakame-vdc-11.12-amd64.20120202.iso)

If you decide to try it, feel free to pm me with any questions.

[/shameless plug] :)

---

### Post by Bandit on 2012-06-07
> **forrestcupp said:**
> VMware ESXi is the one that allows you to run VMs without a host OS. Pretty cool concept.

> **CharlesA said:**
> ESXi is the OS. ;)

Xen does a similar thing.

> **sandyd said:**
> Vmware ESXi is like a downgraded version of VMWare ESX.
Basically, everything is managed through the VSphere Client.

Its hard to explain unless you try it yourself.

I like it, however, because it is really easy to create complex networking setups using vswitches.


Ahh. Very Nice.
I will have to try it out then. :)
Thanks everyone.

---

### Post by spynappels on 2012-06-07
> **sandyd said:**
> Vmware ESXi is like a downgraded version of VMWare ESX.

Not strictly true anymore, it's now pretty much the same, it's just the features enabled by the license which are different.

I use this and VirtualBox, however, ESXi can be a real pain to install on non-server hardware, and that's from experience. I tend to do everything except for creating new VMs on the ESXi host from a SSH/CLI connection now.

---

### Post by forrestcupp on 2012-06-07
> **CharlesA said:**
> ESXi is the OS. ;)

Xen does a similar thing.An extremely minimal OS. :)

Do you know if ESXi can pass through real hardware, like they're doing with Xen?

> **spynappels said:**
> 
I use this and VirtualBox, however, ESXi can be a real pain to install on non-server hardware, and that's from experience.

I wondered about that.

---

### Post by spynappels on 2012-06-07
> **forrestcupp said:**
> I wondered about that.

Here is the list of machines that it will work on, although for some, workarounds are required.

[http://www.vm-help.com//esx40i/esx40_whitebox_HCL.php](http://www.vm-help.com//esx40i/esx40_whitebox_HCL.php)

---

### Post by Dragonbite on 2012-06-07
> **Metallion said:**
> Why not give Wakame-VDC a try? It's basically kvm with a web ui around it that allows you to create instances from your VM images. It also has that snapshot functionality you want.

We've got a DVD that sets up Ubuntu lucid with Wakame on top. Just install that, open a browser and connect to your machine on port 9000. Then log in with username demo and password demo. Should work out of the box.

[http://dlc.wakame.axsh.jp.s3.amazonaws.com/beta/11.12/wakame-vdc-11.12-amd64.20120202.iso](http://dlc.wakame.axsh.jp.s3.amazonaws.com/beta/11.12/wakame-vdc-11.12-amd64.20120202.iso)

If you decide to try it, feel free to pm me with any questions.

[/shameless plug] :)

Do you fine KVM better than VMWare or VBox?

Is Xen, for Linux, still around? It was bought by Citrix, and I see it referenced in our company's Citrix server but is the FOSS version still being maintained?

---

### Post by CharlesA on 2012-06-07
> **forrestcupp said:**
> An extremely minimal OS. :)

Do you know if ESXi can pass through real hardware, like they're doing with Xen?

I am not sure, but it looks like you can:
[http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1010789](http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1010789)

Needs specific hardware tho, from the looks of it.

> **Dragonbite said:**
> Do you fine KVM better than VMWare or VBox?

Is Xen, for Linux, still around? It was bought by Citrix, and I see it referenced in our company's Citrix server but is the FOSS version still being maintained?

KVM would work too.

Xen is still around:
[http://xen.org/](http://xen.org/)

---

### Post by BrokenKingpin on 2012-06-07
I have always been a fan of Virtual Box. It is easy to use and configure, and will do what you want it to do.

---

### Post by Metallion on 2012-06-07
> **Dragonbite said:**
> Do you fine KVM better than VMWare or VBox?

Is Xen, for Linux, still around? It was bought by Citrix, and I see it referenced in our company's Citrix server but is the FOSS version still being maintained?

I don't have much experience with VBox but I hear from many sources that KVM is better for server environments. I actually coded VMWare ESXi support for Wakame (still an early prototype) and I like KVM a lot better. It's just so much more open and easy to work with. I've had more than a few headaches working with VMWare's proprietary images.

I especially like how easy it is to convert KVM images to other formats and loop mount them.

Xen is indeed still around.

---

### Post by Bandit on 2012-06-07
> **BrokenKingpin said:**
> I have always been a fan of Virtual Box. It is easy to use and configure, and will do what you want it to do.

Same reasons I stick with it also. I like easy..

---

### Post by CharlesA on 2012-06-07
> **Bandit said:**
> Same reasons I stick with it also. I like easy..

I've been thinking of switching over to KVM or Xen but I haven't felt like relearning something when what I am using now works.

VBox is more for consumers, and I wouldn't run it in an enterprise environment.

---

### Post by Metallion on 2012-06-08
> **CharlesA said:**
> VBox is more for consumers, and I wouldn't run it in an enterprise environment.

That's exactly how it is. Also if it works for you, then by all means stick to it. :)

---

### Post by sandyd on 2012-06-10
> **spynappels said:**
> Here is the list of machines that it will work on, although for some, workarounds are required.

[http://www.vm-help.com//esx40i/esx40_whitebox_HCL.php](http://www.vm-help.com//esx40i/esx40_whitebox_HCL.php)

That list is inaccurate. ESXi 5 is aredy out.

---

### Post by mips on 2012-06-11
[http://www.overclock.net/t/1205216/guide-create-a-gaming-virtual-machine](http://www.overclock.net/t/1205216/guide-create-a-gaming-virtual-machine)

Above is a nice guide for Xen using hardware passthrough so you can directly access USB, Audio, PCIe GPU etc

Ensure your hardware has proper support for hardware passthrough though.

---

### Post by samalex on 2012-06-12
> **Bachstelze said:**
> I don't know much about virtualisation besides the occasional VirtualBox, but I think Xen sounds like what you want. Last I checked it was not very well supported in Ubuntu, so you might have to use another distro (when I researched this a couple months ago, OpenSuse looked like the best choice--but I lost interest in the whole thing before actually implementing it :p).

Same here, VirtualBox is all I've used, but it sounds like Xen would be a good option if Windows is to run virtually since Xen can be configured to run with very few resources unlike VirtualBox.

I've never used Xen, but I need to start working with it just to get some exposure.

---

### Post by roelforg on 2012-06-13
@OP Dude, i don't know what you call an old computer. But i'd kill for those kind of specs... That exceeds my main system. Sometimes i wonder where you get the money.
 
Anyways, i recommend qemu.
You might need to read into it a bit, but it's very very powerfull.
If you work with raw disk images, there's not really any difference to working with them than there is with a physical hdd.

---

### Post by Dragonbite on 2012-06-13
> **roelforg said:**
> @OP Dude, i don't know what you call an old computer. But i'd kill for those kind of specs... That exceeds my main system. Sometimes i wonder where you get the money.
 
Anyways, i recommend qemu.
You might need to read into it a bit, but it's very very powerfull.
If you work with raw disk images, there's not really any difference to working with them than there is with a physical hdd.

Never really looked into qemu.

I have only ever bought 2 comptuers... my first in 2000 and the latest was this past December for my wife (which I am not allowed to touch much because that's why we got it :lolflag:).

All of my other systems have been second-hand.  Most of  them are from companies that are clearing out their closet of old systems they replaced with newer ones for their employees.

Our company refreshes every 2-3+ years (I should be due in a year or two).  When they want to clear their closet out they raffle off to interested employees and that is where I got this one (and the P4 this one is going to replace).

If I don't virtualize this desktop, then when I replace the current desktop with this one I will probably set that one up as a collection of virtual servers so I can try things without killing my electricity bill!

Once I found Linux, I found these colder computers have still some life in them!

---

### Post by roelforg on 2012-06-13
> **Dragonbite said:**
> Never really looked into qemu.

I have only ever bought 2 comptuers... my first in 2000 and the latest was this past December for my wife (which I am not allowed to touch much because that's why we got it :lolflag:).

All of my other systems have been second-hand.  Most of  them are from companies that are clearing out their closet of old systems they replaced with newer ones for their employees.


Guess how i got most of my systems...
Free from friends and family, swap out a part if it's broken, spend a few hours custom building an ubuntu setup (manually selecting what stuff i do and don't want) and those oldtimer fly once more.


LOL, i've only bought 3 computers, one of them being second hand and only costing 30 bucks.
I seem to have something with that price... HQ ctx beamer, 3COM Superstack 3 4226T, computer, HP lcd monitor, all 30 bucks second hand.

---

### Post by Dragonbite on 2012-06-13
> **roelforg said:**
> I seem to have something with that price... HQ ctx beamer, 3COM Superstack 3 4226T, computer, HP lcd monitor, all 30 bucks second hand.

$20 got me my current laptop: IBM Thinkpad T42 Pentium M, 1 GB ram (upgraded to 2 GB immediately), computer bag and an optical mouse tucked into one of the pockets.

Oh, and a series of Windows XP recovery disks made from that machine by the previous owner (which didn't really work anyway but I still managed to get Windows 7 installed and it works fine).

---

