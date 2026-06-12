---
title: "Playing 3D games on a virtual machine"
date: 2010-02-18
forum: Virtualisation
---

### Post by Objekt on 2010-02-18
Is there any way to run a virtual machine with more or less direct access to graphics hardware?  I have a triple-boot Ubuntu 9.10 64-bit/Windows XP/Windows 7 RC setup, but it's a huge inconvenience to reboot into Windows XP, just so I can play a few games.  I then have to reboot yet again back into Ubuntu, when I'm ready to do "important" stuff like email and posting on forums.  When I'm running Ubuntu 9.10, which is the rest of the time, I only need a Windows XP virtual machine to access my Windows-only printer.

I use Virtualbox 3.1.4 PUEL to run that Win XP VM.  I have tried to install one 3D-intensive game, Elder Scrolls IV: Oblivion.  The installer quits with some kind of Direct3D-related error.  FWIW, yes, I have the appropriate Guest Additions installed, but apparently "experimental" D3D support is not adequate, for Oblivion at least.

From what I have read about other virtualization solutions, such as Xen and Parallels, they are in more or less the same boat.  The virtual video card provided is OK for 2D desktop applications, but forget about heavy 3D.

Someone's probably going to suggest I run Oblivion with Wine, but that method has its own problems.  Let's assume I want full 3D performance, equal (or at least 90% equal let's say) to what I would get running Windows XP natively.  I want the convenience of running a virtual machine, but with the performance of running natively on hardware, and no constant rebooting.  Impossible?  Sorta-posssible?  Somewhere between?

---

### Post by linux4life88 on 2010-02-18
> **Objekt said:**
> Is there any way to run a virtual machine with more or less direct access to graphics hardware?  I have a triple-boot Ubuntu 9.10 64-bit/Windows XP/Windows 7 RC setup, but it's a huge inconvenience to reboot into Windows XP, just so I can play a few games.  I then have to reboot yet again back into Ubuntu, when I'm ready to do "important" stuff like email and posting on forums.  When I'm running Ubuntu 9.10, which is the rest of the time, I only need a Windows XP virtual machine to access my Windows-only printer.

I use Virtualbox 3.1.4 PUEL to run that Win XP VM.  I have tried to install one 3D-intensive game, Elder Scrolls IV: Oblivion.  The installer quits with some kind of Direct3D-related error.  FWIW, yes, I have the appropriate Guest Additions installed, but apparently "experimental" D3D support is not adequate, for Oblivion at least.

From what I have read about other virtualization solutions, such as Xen and Parallels, they are in more or less the same boat.  The virtual video card provided is OK for 2D desktop applications, but forget about heavy 3D.

Someone's probably going to suggest I run Oblivion with Wine, but that method has its own problems.  Let's assume I want full 3D performance, equal (or at least 90% equal let's say) to what I would get running Windows XP natively.  I want the convenience of running a virtual machine, but with the performance of running natively on hardware, and no constant rebooting.  Impossible?  Sorta-posssible?  Somewhere between?

I asked a similar question awhile ago:
[URL="http://ubuntuforums.org/showthread.php?p=8084062"]
http://ubuntuforums.org/showthread.php?p=8084062[/URL]

Getting a game in Virtualbox seems to be a hit or miss ordeal. I know this is not the answer you were wanting, but this is just what my experience has been.

---

### Post by GolemXIV on 2010-02-19
I've never had good luck running games from vbox or vmware. (vbox is limited to 128mb of video memory and I've gotten really messed up graphics from vmware)

Dual boot, and play-on-linux (wine front-end) are the only really good solutions I've found.

I know you have had problems using wine but you might want to give play-on-linux a try. It should have an install script for oblivion and is a lot easier to use then raw wine.
[http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)

If you need to install a game manually be sure to find out what version of wine works best with the game and set playonlinux to use that version. I've had games go from wont run to runs perfectly just by changing to a suggested version of wine.
[http://appdb.winehq.org/](http://appdb.winehq.org/)

Sorry I can't think of a non-wine non-rebooty solution.

---

### Post by Objekt on 2010-03-01
I tried some games on my virtual Windows XP machine (through Virtualbox).

So far the results aren't promising.

Urban Terror 4.1: Runs, but is unplayable.  The mouse is far too sensitive at first.  Even after turning the sensitivity way down, there's a weird rubber band effect, where a mouse input is only reflected onscreen after considerable delay.

Simpsons Hit & Run: Crashes.

Oblivion: The Elder Scrolls IV: Installer crashes.

Thief 2: Error on launch.  It says: "Your video card is not compatible with Thief 2."

Frogger 3D: (a really old one, you'd think it might work) Crashed my virtual machine.

I'm not sure exactly what you CAN do in Virtualbox that is 3D.  Clearly, I haven't found it yet.

---

### Post by MelDJ on 2010-03-01
check this out: [http://forums.virtualbox.org/viewtopic.php?t=16](http://forums.virtualbox.org/viewtopic.php?t=16)

---

### Post by lahmanwokard on 2010-03-01
I dont understand what is this live pc listen all i wan to do is this get the best virtualmachine besides parallels witch is the only one able to run windows xp with full capabilities i manage to activate direct 3d but i still&#65279; dont have agp aceleration how did you do this i see Wareham player there.

---

### Post by Objekt on 2010-03-02
> **lahmanwokard said:**
> I dont understand what is this live pc listen all i wan to do is this get the best virtualmachine besides parallels witch is the only one able to run windows xp with full capabilities i manage to activate direct 3d but i still&#65279; dont have agp aceleration how did you do this i see Wareham player there.

Do you have a question?  I have no idea what you're trying to ask.  It would help if you used punctuation.

---

### Post by Objekt on 2010-03-02
> **MelDJ said:**
> check this out: [http://forums.virtualbox.org/viewtopic.php?t=16](http://forums.virtualbox.org/viewtopic.php?t=16)

Interesting.  I didn't read the entire, long thread, but here's what I got out of it:

You have to either emulate the original GPU, or hack together a system which can respond properly to the various OpenGL or DirectX calls.

The former approach being impossible, we're left with the latter, unavoidably slow & buggy approach.  For now, running the OS natively is the only way to get full performance.

I wouldn't so much mind having to reboot into Windows, if it only took 10 seconds from "press reset switch" to "Windows XP desktop."  Instead it's closer to 2 minutes.

Hardware mfgs. are partly to blame.  The time from "power on" to "initialization complete, OS loading" has hardly changed over the last 10 years.  If anything, it is now longer.  Why is the time for my network adapter to "start up" even perceptible?

---

### Post by freakalad on 2010-03-02
For my experience, 3D in VM is a mess.

As was indicated, VMWare & Parallels are OK, & VBox is the only FLOSS hypervisor that does 3D (I think it actually uses bits of those other HV's)

There was a project a few years ago, VMGL, that would've provided OpenGL on VM, but that seems to have run dead :(
So no possibility of 3D for KVM or Xen any time soon (maybe Sun will release something eventually)

I've even tried remote desktop solutions like NX & RDP, but there are also some pretty serious latency issues; event over virtio NIC drivers

Server virtualization on GNU/Linux is pretty tried & tested, but desktop virtualization still seems a long way off

---

### Post by Objekt on 2010-03-03
On the last page of the thread I linked, there's a link to a quite interesting paper by one of the guys at VMware.

[http://vmware-svga.svn.sourceforge.net/viewvc/vmware-svga/trunk/doc/gpu-wiov.pdf?revision=1]("http://vmware-svga.svn.sourceforge.net/viewvc/vmware-svga/trunk/doc/gpu-wiov.pdf?revision=1")

Nutshell: they can run Half Life 2 at high res (1600x1200) at 22 frames/sec.

Interactive, certainly, but not really playable.

I suspect we're in one of those situations where, by the time the virtual machine can deliver "normal" FPS (40-60 minimum), we will be playing 10 or 20 year old games.

---

### Post by freakalad on 2010-03-03
At this stage I'm not too concerned with low-latency gaming, as such (would be nice, but not a priority). 

I think the way to deal with gaming-type applications, eventually, would be to do a bit of pre-rendering on the server/cloud, and then pump that data to the client to do the final rendering & provide the interactivity (a little bit like WoW)

What I'm more concerned with immediately is just a "simple" sort of desktop virt.
For example, I can run boxee, xbmc, moovida/fluendo or any number of media server front-ends in a VM, and then use some sort of remote control protocol/client like [NX]("https://help.ubuntu.com/community/FreeNX"), [SPICE]("http://www.redhat.com/virtualization/rhev/desktop/spice/") or even RDP to access that system over the wire or air. 
So then I can watch movies in the living room on my PS3/Wii, or in my office, or in the kitchen, or in bed. 
I can even have the same environment follow me as I move about.
I can also access the same environment from any thin-client/device, even if I get disconnected.

This may be especially useful in office environments where users can sit at any available terminal & still have access to their own system; even from home/conference/hotel.

Just because they work remotely, does not mean that they will not find value in a rich UI experience.

---

