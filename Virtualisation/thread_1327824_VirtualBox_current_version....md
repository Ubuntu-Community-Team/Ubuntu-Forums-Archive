---
title: "VirtualBox current version?..."
date: 2009-11-15
forum: Virtualisation
---

### Post by VcDeveloper on 2009-11-15
In installing VBox I notice the version being 3.0.8.  When will the 3.0.10 version be available, because I notice a lack of performance.  

For instance: 1) when I restore VM after it was minimize the client screen doesn't refresh and I just have a frame with the host background.  I run the mouse curser and I get partial blocks of the client screen.  2) is does this with Ubuntu 9.10 as the guest, 3) I have Windows XP Pro as a guest and it works fine, 4) both have a slow delayed reaction and refresh rate.

I also have openSuSe 11.1 setup the same way on another machine, but with VB 3.0.10  and it performs very well.

I'm guesting the poor performance is because of the 3.0.8 version, but can anyone make any suggesting of correcting this?

Also, is there a module I can use to manually add url's to specific packages from the repository to keep my packages up to date?  About the same Repository Module as openSuSe's.

---

### Post by shababhsiddique on 2009-11-15
> **VcDeveloper said:**
> In installing VBox I notice the version being 3.0.8.  When will the 3.0.10 version be available, because I notice a lack of performance.  

For instance: 1) when I restore VM after it was minimize the client screen doesn't refresh and I just have a frame with the host background.  I run the mouse curser and I get partial blocks of the client screen.  2) is does this with Ubuntu 9.10 as the guest, 3) I have Windows XP Pro as a guest and it works fine, 4) both have a slow delayed reaction and refresh rate.

I also have openSuSe 11.1 setup the same way on another machine, but with VB 3.0.10  and it performs very well.

I'm guesting the poor performance is because of the 3.0.8 version, but can anyone make any suggesting of correcting this?

Also, is there a module I can use to manually add url's to specific packages from the repository to keep my packages up to date?  About the same Repository Module as openSuSe's.

I am using VBox ose 3.0.8 too. Inside karmic. I cant install any of the uubuntu distros inside. Have no idea whats wrong. It was fine when I used in 9.04....I tried to install Intrepid, Jaunty, Karmic ...whatever it is VBox just freezes at the first stage. Is anyone having problems whith VBox???like me. I am working on custom OSs so I need to set up my VBox very soon. Just dont want to see XP again just to use VMware

---

### Post by RedSingularity on 2009-11-15
Well you can get the most current one from the repositories located [here]("http://www.virtualbox.org/wiki/Linux_Downloads")

Look at the repos listed under "debian based distros".

---

### Post by VcDeveloper on 2009-11-16
Well, I installed the current VB and my Ubuntu Guest VM still acts the same, but I did a test and installed openSuse as a Guest and run well as the XP.  So there's two problems. 1) Ubuntu 9.10 doesn't run well in as a VM or Ubuntu doesn't like my LE 7300 video card in the VM.

Other than that, Ubuntu runs well as a host

---

### Post by VcDeveloper on 2009-11-16
Well I found the solution as to why Ubuntu wasn't performing well in a VM!  The poor performance is the x32, but x64 performs as expected.  Now I'm a Happy Camper!

Hope this helps others!  But, keep in mind I have a Hyper-V system, Quad Core 2, 6GB Ram, My Video sucks - nVidia LE 7300, but both the Ubuntu Host and Guest is performing well!  Yeah!

---

### Post by VcDeveloper on 2009-11-16
Argh! Well, it performs well a VM, but is still for some reason doesn't refresh the client screen after it has been restored from being minimized.  Just going to have to deal with it, but don't minimize it.  Down loading 9.04 x64 to see if this one does the same thing......

---

### Post by VcDeveloper on 2009-11-16
Well I ran another test by installing another x64 Ubuntu VM, and found the restore works fine until after I update the initial installation.  So something in the update has changed graphic interface properties from detecting rather the client needs redrawn.

---

### Post by VcDeveloper on 2009-11-16
Well, I think I found the actual problem! It's not Ubuntu at all I think, but I have two Ubuntu VM 1) updated without the Guest Additions installed and 2) with the Guest Additions intalled. The one "with" is the one having the problem not redrawing the screen after restoring from a minimized state.

So this means communication is broken between to two....., So I will post this also at the VB forum for a solution!

But to Note: I don't have this problem with openSuSe and XP Pro as Guests!  Is this a Ubuntu or VB Addition problem for this OS and is there something I can do to some settings to correct this?

---

### Post by VcDeveloper on 2009-11-17
I just created a Ubuntu 9.04 VM and so far it's working normally just like my XP and openSuSe 11.1, so it must be the 9.10...

---

### Post by VcDeveloper on 2009-11-17
Solution Solved!  Thanks to Perryg posting this in the [VBox forum]("http://forums.virtualbox.org/viewtopic.php?f=7&t=24708&p=110146#p110146").  Didn't realize I was using to much Vram and I turn off the 3Dx. So for know everything is normal.

---

