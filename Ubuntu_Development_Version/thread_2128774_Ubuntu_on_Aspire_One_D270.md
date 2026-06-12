---
title: "Ubuntu on Aspire One D270"
date: 2013-03-24
forum: Ubuntu Development Version
---

### Post by Dingo7 on 2013-03-24
Hey guys,

I recently got a D270 Netbook, and, like many others have had troubles installing Ubuntu on this machine..

I am now typing on the same netbook running Ubuntu 13.04 Daily Build, and GMA 3600 are working great in 3D mode.
The only problem is that top reports CPU as 100% all the time, The problem is compiz, reporting use of 217% CPU etc, (Screenshot attatched below.), The CPU is not over heating or anything, but still, that shouldnt be happening.

Baby steps guys, Baby steps...

[IMG]http://i.imgur.com/sU9gbcT.png?1[/IMG]

---

### Post by Dingo7 on 2013-03-24
Come on, anyone? The problem persists even when compiz isnt running....

---

### Post by Dingo7 on 2013-03-24
hey guys, I have 100% CPU all the time, even if Xorg and Compiz are not running... Can anyone help me please?

Screen shot [here]("http://ubuntuforums.org/showthread.php?t=2128774")

---

### Post by matt_symes on 2013-03-24
Threads merged.

Please don't create multiple threads on the same subject. It dilutes community effort.

---

### Post by mike555 on 2013-03-24
I also have a Acer netbook, I found out Lubuntu runs much better,because it is much lighter ..... no fancy effects though.

---

### Post by Dingo7 on 2013-03-24
> **mike555 said:**
> I also have a Acer netbook, I found out Lubuntu runs much better,because it is much lighter ..... no fancy effects though.

Cool, I was really hoping for Unity though, Ive been trying for ages and this is alot of progress for me, even if the way of installing through OEM mode was a pain. VGA is working too, havnt tried HDMI yet...

---

### Post by oldos2er on 2013-03-24
Moved to Ubuntu +1

---

### Post by Dingo7 on 2013-03-24
Thanks, thought I posted in the right place... Anymore thoughts on this?

---

### Post by mikewhatever on 2013-03-24
Intel's GMA3600 is the current reincarnation of the [infamouse GMA500]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo").  Much had been said about it over the uears, and you are welcome to read up on that saga of failure by searching this forum or the web.
To run Unity well, you'd would need a 3d capable GPU and driver, and we've been waiting fro the driver since 2008.
You can try 12.04.1 with Unity2d though. 12.04.1 even has a proprietary CedarView 2d driver.

---

### Post by Rob Sayer on 2013-03-28
I have a D270 running kubuntu 12.04.  I wouldn't even consider running unity and/or compiz on my i3 laptop (also kubuntu 12.04) let alone the 270.  Compiz performance stinks.  KDE is much faster.  Both take similar ram as far as I can see.

You can install cedarview drivers in a 270.  I wouldn't recommend the way I did it first, which involves installling and holding an older generic non pae kernel.  That caused me other odd problems.  For instance, the HDD controller in my 270 isn't totally compatible with the cedarview patches.  There were other weird things too.

I recently just installed kubuntu 12.04 32 bit and lightdm (lightdm may not have been actually necessary but it works, at least on kubuntu).  Then run sudo apt-get update.  Then run the update manager a few times until there aren't any more updates.

Then, and only then, go into additional drivers and install the cedarview one.  The screen went blank, and I had to to a hard shutdown with the power button.  A wee bit panicky, that.  But when I turned it back on it worked fine.  The brightness keys work and it plays youtube video and billardgl as well as with the previous method.  And without holding the system to an older generic kernel.

However, you still will only get xrender video, not opengl.  So I would not use Unity or any other gnome 3/compiz based shell on a cedarview machine.  But I hate gnome 3/compiz anyway.  No loss.

Most people would reccommend something like xubuntu or lubuntu in a situation like this, and they're largely right.  But I'm running kde (kubuntu) on my 270.  It definitely uses more ram than xubuntu (which I used for a while but I never tried lubuntu).  That's not a problem for me.  It's a netbook.

Actually kde runs faster than xfce.  One of the most common myths in computers is that a program or system that uses less ram will run faster.  It's usually the opposite.

---

### Post by Dingo7 on 2013-04-02
Yes Rob. I have been looking into the Arch drivers for the Pouslbo chipset and other drivers and limited-documentation. The problem is that there is no Graphics Acceleration on the what seems to be updated GMA500_gfx kernel module. Therefore all the rendering takes place on the CPU. Maxing it out to 100%.

I'll keep researching though, I feel like im making small progress :)

---

### Post by jerrylamos on 2013-04-02
Not sure what a D270 is?

This is an Aspire One D255E $250 netbook, screen size 1024x600 happily running external monitor 1600x900  processor utilization normal with laptop screen off.  It's a dual processor so I don't know if it would go to 100% or 200%?

Intel Corporation N10 Family Integrated Graphics Controller

How do I tell what display driver is being used?

BTW, just got an Acer Chromebook C7 $199 which is dual processor 1 gHz 1366x768 screen, intel processor & display which for browsing only zooms compared to 1.6 gHz 64 bit dual processors netbook and notebook running unity ubuntu.  I got it thinking I would put unity on it, there are some complex instructions on how to do it.  Some blog comments ubuntu may not support the graphics accelerator on the C7. Anyway having fun fast browsing and video as is even though I'm no chrome fan. 

Now doing anything other than browsing on the chromebook is a challenge, limited offline spreadsheet and write capability.  I'm not about to knowingly put personal data up there in the cloud for the marketeers and hackers and spammers.  That goes for ubuntu cloud also.

Oh, BTW, this is 12.04 64 bit new install I'm going to install a 13.04 64 bit in place of the 32 bit 13.04 for comparison.

---

### Post by cortman on 2013-04-02
I would strongly recommend using Lubuntu for your netbook. Lubuntu 12.10 will run many times faster than Unity and stock Ubuntu. Haven't used 13.04 yet, but I'm looking forward to grabbing a beta image soon.
If you do use Unity, make sure you're aware of the fact that by default it will send your search phrases to Canonical servers and provide you with [s]ads[/s] shopping suggestions. If you're not interested, you can turn the feature off.
Good luck!

---

### Post by jerrylamos on 2013-04-02
On my Aspire One D255 10.1" netbook driving 20" external monitor at 1600x900, 1.6 gHz 1 GB, raring 13.04 64 bit 

On a BBC video about 60% utilization on both processors with 5 tabs up on Firefox, including this one.  According to the system monitor.

Video is running fine. I'm not using full screen because I couldn't see the monitor then.

Memory 56.2%, swap 32.7%.

Not sure about 12.04 64 bit vs 13.04 64 bit I've got both installed.

BTW, sitting on an endtable next to the lunch table, using wireless keyboard and mouse.

More memory on this model involves removing the mother board.  Said to be much easier on the Acer C7 chromebook I just bought, The D255 does everything linux, the Chromebook does browsing and cloud.  Period.  I've read about Chrubuntu don't know whether it would support the nice C7 graphics accelerator. 

Maybe my D255 is about like the D270??  I also have a 1.6 gHz Acer Amd64 notebook and a 3.3 gHz tower i386 32 bit Celeron.  Given unstable development 13.04 with bugs all three run fine.

Do note on the Aspire One D255

grep "SNA init" /var/log/Xorg.0.log

reports 

[    14.298] (II) intel(0): SNA initialized with gen3 backend

which I think means there's Intel graphics acclelerator SNA initialized and running,

---

### Post by jerrylamos on 2013-04-02
> **cortman said:**
> I would strongly recommend using Lubuntu for your netbook. Lubuntu 12.10 will run many times faster than Unity and stock Ubuntu. Haven't used 13.04 yet, but I'm looking forward to grabbing a beta image soon.

This netbook is running ubuntu unity nicely.  I'm very definitely not a unity fan  but it is working.

I like lubuntu fine but it is not nearly so good at causing bugs to report to launchpad as unity is.

Give 13.04 a whirl.  I just installed a fresh amd64 raring .iso on this 64 bit Intel and running very usably.  I have a 12.04.2 partition just in case, example the other day the screenshot wasn't working on the amd64 13.04.  Just put the screenshot icon on the unity launcher so hopefully the problem is fixed.

---

### Post by jerrylamos on 2013-04-02
Oh, Systems Settings Details says the video driver is "Intel IGD" whatever that might mean.  Runs O.K.  I don't know if there are other choices.

---

### Post by mikewhatever on 2013-04-02
> **jerrylamos said:**
> Not sure what a D270 is?

...

If not sure, why not find out first?
[http://panam.acer.com/acerpanam/netbook/2012/Acer/Aspire/AspireOneAOD270/AspireOneAOD270sp2.shtml](http://panam.acer.com/acerpanam/netbook/2012/Acer/Aspire/AspireOneAOD270/AspireOneAOD270sp2.shtml)

---

### Post by Dingo7 on 2013-04-02
> **mikewhatever said:**
> If not sure, why not find out first?
[http://panam.acer.com/acerpanam/netbook/2012/Acer/Aspire/AspireOneAOD270/AspireOneAOD270sp2.shtml](http://panam.acer.com/acerpanam/netbook/2012/Acer/Aspire/AspireOneAOD270/AspireOneAOD270sp2.shtml)
+1

To find what driver, open a terminal and do 'lsmod | grep gma' and you should see your gma500_gfx

---

### Post by Dingo7 on 2013-04-02
> **jerrylamos said:**
> This netbook is running ubuntu unity nicely.  I'm very definitely not a unity fan  but it is working.

I like lubuntu fine but it is not nearly so good at causing bugs to report to launchpad as unity is.

Give 13.04 a whirl.  I just installed a fresh amd64 raring .iso on this 64 bit Intel and running very usably.  I have a 12.04.2 partition just in case, example the other day the screenshot wasn't working on the amd64 13.04.  Just put the screenshot icon on the unity launcher so hopefully the problem is fixed.

Does your netbook have the gma500 or gma3600 chip on it?

---

### Post by jerrylamos on 2013-04-02
On this D255E netbook, I think similar to D270 but bought fall 2011,  I think Acer has several models of 10.1" netbook over the years.

lsmod grep | video
gets 
acer_wmi,i915

lspci | grep 'vGA 
gets
VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller

I don't know the chipset.  

Intel® Atom™ CPU N455 @ 1.66GHz × 2
 
Anyway, running raring fine, either 32 or 64, BBC video and all.

---

### Post by onurrsln on 2013-05-18
> **Dingo7 said:**
> Hey guys,

I recently got a D270 Netbook, and, like many others have had troubles installing Ubuntu on this machine..

I am now typing on the same netbook running Ubuntu 13.04 Daily Build, and GMA 3600 are working great in 3D mode.
The only problem is that top reports CPU as 100% all the time, The problem is compiz, reporting use of 217% CPU etc, (Screenshot attatched below.), The CPU is not over heating or anything, but still, that shouldnt be happening.

Baby steps guys, Baby steps...

[IMG]http://i.imgur.com/sU9gbcT.png?1[/IMG]

1. Download the synaptic package manager from the software center. 
2. Open the synaptic package manager
3. search apt-xapian-index
4. uninstall it.

after these steps can you tell us cpu usage ?

---

### Post by jerrylamos on 2013-05-18
This is a D255E, Acer Aspire One netbook, a bit older I think than the D270.  Dual Atom processors 1.66 gHz saucey amd64 updated most days.  1 GB memory.  

Top shows about 20% to 45% as I type this in,  Scrolling gets it up to 60% or more, then quiets down.

% memory about 30% not doing much, a terminal session running top and firefox with 5 tabs.  Adding more memory on this model involves removing the keyboard, removing the motherboard, etc.  I haven't been pressed to do all that.  Yet.

---

