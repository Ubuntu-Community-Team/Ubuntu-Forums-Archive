---
title: "Colleged student debating on getting an Ubuntu laptop"
date: 2009-05-01
forum: System76 Support
---

### Post by brandonterrill on 2009-05-01
I am currently debating on getting a Pangolin Performance laptop from System 76 when I start college in the fall(though I would like to get the computer asap). I'm going to be working on earning a bachelors degree in computer science then an associates in computer programming. I have been stuck with the same outdated computer since 2003, so I don't really have anything to compare performance-wise with what I'm going to need.

The configuration I'm willing to buy looks as follows...
**Display: **15.4" WSXGA+ Super Clear Glossy LCD (1680 x 1050)
**Processor: **Core 2 Duo T6400 2.0 GHz 800 MHz FSB 2 MB L2 (35 Watt)
**Memory:** 4 GB - DDR2 800 MHz - 2 DIMMs
**Hard Drive:** 500 GB 5400 RPM SATA II
**Wireless:** Intel Wi-Fi Link 5300 - 802.11A/B/G/N Up to 450 Mbps
Everything else is standard, this comes out to be almost exactly at the most I'm willing to spend on a laptop, $1,049.00

I will more than likely have to run Windows in a virtual machine (VirtualBox seems most appealing to me) with VC++, VC#, Dreamweaver, and maybe Photoshop(I'm more of a GIMP fan myself). We will be working seldom with *nix, mainly for server management. I could just buy a Windows PC, but to be honest I like Ubuntu better. Will this system be up to running a virtual machine at a tolerable speed with these kinds of requirements? If not what kind of configuration would you reccomend? Thank you in advance!

---

### Post by Synthros on 2009-05-01
I think that configuration would serve you well.  4GB of RAM should be plenty, especially if you're only going to be running a single virtual machine.

---

### Post by Derath on 2009-05-01
I'm currently running a very similar system as a college student (MIS Major, CIT minor), and it's been working great for me. And VirtualBox is highly recommended as a VM application.

---

### Post by brandonterrill on 2009-05-01
Thank you for the feedback, it looks like I will definitely going the System76 route :) can't wait to get it now

---

### Post by TheBuzzSaw on 2009-05-01
You won't be disappointed. Heck, I'm typing this message on my daru2 (old Darter Ultra). System76 puts out quality systems!

---

### Post by 3Miro on 2009-05-01
I have 2.4Ghz CPU and smaller HDD. VB runs without any trouble (out of the box). On my desktop (different HW, but still the same VB), I am running Visual Studio, also without trouble. (win XP in both cases)

---

### Post by arepaking on 2009-05-01
Stop debating. With Ubuntu you will be able to do almost everything you normally do in Windows and worst case scenario you can use Virtualbox to create a Windows virtual machine and run those apps that you really need but couldn't find the way to make it work in Ubuntu (This is what I do with my Iphone, I am running iTunes in Windows XP through a virtual machine using Virtualbox in Ubuntu).

---

### Post by sloggerkhan on 2009-05-01
As a CS student in college I think you are better off getting a cheap netbook with linux and building a basic desktop for use at home (with linux). I used to have just a laptop, but it wasn't flexible enough.(Not enough battery life for class, too bulky, but at the same time not enough storage space, battery life quickly worsened to being terrible...)

I finally ended up building a desktop and getting a netbook, and combined they cost less than my good laptop did. Now I can actually have enough battery life to take notes in all my classes and can carry it arround really easy, with SSH access to home computer I can have access to all my stuff everywhere, plus I have a computer that I can try risky things on without compromising my ability to have  functioning computer for coursework. Also, netbooks aren't too expensive to replace, desktops you can just swap a part, if you have issues with an expensive laptop, it's as good as dead.

---

### Post by 3Miro on 2009-05-01
When I was undergrad and for most of my graduate studies I was using a desktop + SSH and such (financial reasons). It works well enough, however, some schools now require a laptop (I think).

---

### Post by jjacobs2 on 2009-05-02
I believe that Intel processor does not have virtualization support.  You may find it useful to upgrade to one that does.

---

### Post by Vadi on 2009-05-02
Virtualbox does not require a CPU extension to do virtualization so you'll be just fine. It's just that if you want to install VMware that it'll be needing it (and virtualbox only benefits from the cpu extension on 64bit hosts & guests, otherwise its not much use).

Serval 3 here with an 8600gt, works fine for a 3h lecture with wireless on or a bit less time for etqw ;)

---

### Post by betrunkenaffe on 2009-05-02
Went to 2 universities so far and both have had the majority of coursework on nix machines. There was in total 3 classes that actually required Windows, 2 Human Computer Interaction courses and a Distributed Computing (used asp and their nix machines didn't have it on them)

For the classes that required Windows, I had to use the machines at the university anyways. (and I was using Windows at home at the time)

---

### Post by glacialfury on 2009-05-02
The only thing you'll experience slowdowns on in a virtual machine, at least in day-to-day software use, would be applications that use video hardware; this is emulated in a virtual machine, so there's no true hardware acceleration.

Bear in mind for programming, depending on school flexibility, you could do C# with mono and GTK, since GTK is available for Windows as well - you just need to make sure wherever your app gets deployed has GTK.

And speaking of that, you can run GIMP on Windows anyway ;-)

---

### Post by Derath on 2009-05-03
> **jjacobs2 said:**
> I believe that Intel processor does not have virtualization support.  You may find it useful to upgrade to one that does.

I have the P8400 Intel, and it does have the virtualization support on the chip, not sure if that's relevant or note, but most of the Intel chips manufactured within the last year or two do have the virtualization. I can't remember the command nor the flags, but there was a cpu-info command that would say whether or not it had it...

---

