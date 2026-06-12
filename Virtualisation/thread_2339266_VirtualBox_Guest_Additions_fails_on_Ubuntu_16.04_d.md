---
title: "VirtualBox Guest Additions fails on Ubuntu 16.04 desktop guest"
date: 2016-10-06
forum: Virtualisation
---

### Post by two4two on 2016-10-06
I know, this question's been asked before.  But I couldn't see one that has my exact problem.  Ubuntu 12.04 desktop host with Vbox 4.4xx and Ubuntu 16.04 desktop guest.  When I run the Vbox guest additions script in the guest (under "devices") it says the headers are not installed, but they ARE.  It goes on to say some of the modules succeeded and others did not -- including Shared Folders.  And for a fact, shared folders does not work.  It's hard to say whether the video part worked because in the host there seems to be a generic video driver working because the ATI CCC says there is no supported adapter installed.  And so in the guest I can only get 4:3 with small resolution and auto resize is grayed out.  (Interesting that in an Ubuntu 12.04 desktop guest I get full-screen 16:9 and auto resize is available.)  This computer is an exact duplicate of another of mine where the video driver for ATI is installed and it finds the supported adapter.  This computer has Ubuntu 11.04 as the host OS.  The Ubuntu 16.06 desktop guest there gets full-screen 16:9 display, but it also gets the "Linux headers not installed/shared folders failures.  Should I try to install the AMD/ATI driver for my adapter (integrated in mobo)?  What's wrong with 16.04 that is thinks headers are not installed when they actually are?  I'm not at those computers right now, but later I can post logs and error msgs and other stuff that you all ask for.  I was just getting a head start here thinking maybe someone already knows what's up.  Thanks.  :D

---

### Post by QIII on 2016-10-06
Hello!

Before you or a nice person trying to help go chasing a red herring, let me say something really quickly:

Do not bother with the video driver issue.  It's a non-issue.  The Guest OS does not have direct access to your GPU and so does not detect it.  The Guest OS runs on the virtual hardware provided by the hardware abstraction layer in the software.  That driver is already included in the kernel when you install the Guest OS.  Don't try to install the fglrx driver in the Guest OS.  At best, nothing will happen.  At worst, you'll wind up with an inoperable guest.

Cheers!

---

### Post by &amp;KyT$0P# on 2016-10-06
> **two4two said:**
>  Ubuntu 12.04 desktop host with Vbox 4.4xx and Ubuntu 16.04 desktop guest.  When I run the Vbox guest additions script in the guest (under "devices") it s
Your Guest Additions are too old for 16.04.  You need at least Guest Additions version 5.0.20, because [this]("https://ubuntuforums.org/showthread.php?t=2329454").

I would be uneasy to stick a newer major version Guest Additions in an older major version VirtualBox.  If you can, uninstall that old VirtualBox and install [latest VirtualBox 5.0]("https://www.virtualbox.org/wiki/Download_Old_Builds_5_0"), it has a 12.04 package available.

---

### Post by two4two on 2016-10-07
QIII, 

Thanks for answering.  First let me point out that I edited my original post a bit to clarify that the duplicate computer I refer to is identical hardware but has Ubuntu 11.04 host OS and VirtualBox 3.3??.  Yes, I do understand about virtualization and the difference between the host and the guest.  When I referred to the fglrx driver I was referring to the host OS.  And the driver of the host does have an impact on what hardware will be virtualized for the guest.  The host has a generic driver.  When I try to execute the ATI Control Center software it tells me to run aticonfig and aticonfig tells me there is no ATI hardware installed.  But of course there is.  It's on the mobo.  I's a little old, so maybe 12.04 host does not have the legacy driver available and so installs a generic VGA driver.  Thus the guest is given a limited range of configs.  I know this because when I try to select 3D acceleration I get an error that says since it is not available on the host it can not be available on the guest.  On the duplicate computer (with 11.04 OS), I have installed on the host the driver that I downloaded from AMD/ATI and am able to specify 3D acceleration in the guest settings and more resolutions are available in the guest.  So I think I should install the legacy AMD/ATI driver for my hardware on the host OS.  I have now done this and I still need to run "aticonfig -- initial". I believe I need to do all this BEFORE continuing with the guest-additions work.

Assuming I've fixed the driver:

On both computers whenever I try to install guest-additions it tells me the headers are not installed.  On both computers I have successfully installed guest-additions on a 12.04 guest and all features (shared folders, keyboard/mouse integration and video drivers) work properly, so I figure if I can get beyond the Linux-headers problem then guest-additions will install properly and all my problems will be solved.

Is there a known bug in 16.04 and the installation of VirtualBox guest-additions? 

I still did not have time to post the logs, but I'll work on that over the weekend.

---

### Post by two4two on 2016-10-07
Thank you Halogen.  I edited my original post to say my other computer is duplicate hardware but the host OS is 11.04 and VirtualBox is 3.3??  A 12.04 guest works fine on both computers.  I will read your link and learn something.  Thanks.

---

### Post by QIII on 2016-10-07
I do not want to belabor this point, but:

The host driver may improve the overall performance of the host (and that is a valid subject for you to ask about) but it does not affect the hardware presented to the guest by the hardware abstraction layer.  It is important to understand that.  Your guest does not see your physical GPU.  GPU passthrough is not possible with VirtualBox.

> By default VirtualBox provides graphics support through a custom virtual graphics-card that is VESA compatible. The Guest Additions for Windows, Linux, Solaris, OpenSolaris, or OS/2 guests include a special video-driver that increases video performance and includes additional features, such as automatically adjusting the guest resolution when resizing the VM window[33] or desktop composition via virtualized WDDM drivers.

I believe that "card" is still the one produced by Innotek GmbH years ago.

 I'm on my mobile right now, but I'll see if I can get back to this later. We can deal with the fglrx driver on the host.

The issue of the version of the Guest Additions that will work with a 16.04 guest is still outstanding.  The Guest Additions do improve the graphics performance of VBox somewhat, but not to GPU-native performance.

Your thread has bifurcated into two subjects:  Guest Additions in the guest and the ATI driver on the host.  That will most certainly lead to confusion.

I suggest starting a new thread about the graphics driver and leaving this thread to deal with the Guest Additions.

---

### Post by two4two on 2016-10-07
QIII,

Thanks for the clarification.  That and with what Halogen says I think I've got some things to work on tonight.  Thanks for reading and helping on these boards. :)

---

### Post by &amp;KyT$0P# on 2016-10-07
**11**.04 is EOL (read: expired) for some years now.  Can you upgrade?

---

### Post by two4two on 2016-10-07
> **halogen2 said:**
> **11**.04 is EOL (read: expired) for some years now.  Can you upgrade?

I know it's out of support.  I have built a version of Lives on there with every codec enabled -- compiled and installed with all the requirements. It is my video editing OS.  To upgrade could ruin the build.  I also have other software in there that I compiled.  I've had things break whenever I go through an upgrade -- even something as simple as Gedit.  So this one will remain 11.04 until I do a clean install of 16.04 in another partition and rebuild Lives and the other software at their latest levels.  That's one of the good things about Ubuntu (and Linux in general) is that as long as you don't need newer software you can keep your current stuff.  I have multi-boot environment with 11.04, Win-XP, Win7, Win8.1, Win10, and VirtualBox in that 11.04 where I run 12.04 and 14.04 plus virtual versions of those Windows OSs.  But since I do a lot of video I mostly use the 11.04.  It works great.

---

### Post by two4two on 2016-10-07
BTW, is it possible to get the current VirtualBox source and configure/make/install it in my 11.04?  Or does it have a bunch of requirements that I can't get?

---

### Post by &amp;KyT$0P# on 2016-10-07
The source download is available from the page I linked.  As for requirements - [Linux build instructions]("https://www.virtualbox.org/wiki/Linux%20build%20instructions")

With a self-built VirtualBox, you may need to download the Guest Additions iso in addition to the Extension Pack.

I've never self-built VirtualBox, so can't help more on that.

---

### Post by two4two on 2016-10-08
I can't see where to mark this thread solved, but it IS solved.

Let me give a rundown.  It was simple.  If you read the different posts you'll see there are TWO host computers involved:  an Ubuntu 12.04 (Linux Mint 13) and an Ubuntu 11.04 (Ubuntu Studio).  On the 12.04 host I completely uninstalled all parts of virtual box and replaced with the latest and greatest from Oracle:  virtualbox-5.1_5.1.6-110634~Ubuntu~precise_amd64.deb and the corresponding extension pack.  On the 11.04 host, which runs virtualbox-4.3_4.3.30-101610~Ubuntu~lucid_amd64.deb and the corresponding extension pack, I could not upgrade to the latest and greatest without trying to build from source.  I didn't want to do that so I left it at the level it's at.  On BOTH computers, in the settings tab for the Ubuntu 16.04 guest I attached the latest and greatest guest-additions iso (the one corresponding the the deb file - good luck trying to find it on the virtualbox web site).  The I started the guest and used synaptic to completely remove all references to virtualbox.  Then I used terminal to navigate to /media/"user"/VBOXADDITIONS_5.1.6_110634 ran the command "sudo ./VBoxLinuxAdditions.run".  It removed whatever remnants of older guest additions it could find and rebuilt all the newer stuff.  No error telling me the headers weren't found.  Then I rebooted the guest and voila!  It works.  On both computers.  I have a problem with the display when I activate 3D acceleration in the settings and so I unchecked that.  Otherwise, mouse/keyboard integration, shared folders, shared clipboards, etc all work fine.  BTW, shared folders in the latest virtualbox release work a little different because they auto-mount in /media/sf_"share name" and are only accessible to root.  You need to put your username in the vboxsf group and then you'll have access.  The other thing I did for shared folders was to create a startup on the host using udisks command to mount them.  I thank QIII and halogen2 for pointing me in the right direction.  If anyone wants me to give more detail, such as the actual commands I used, or the startup I put on the host to automount the shared folders just let me know and I do it, but there is an thread here on the forum that explains it.  Thanks everyone, and now --- how do I mark this thread solved?

---

### Post by &amp;KyT$0P# on 2016-10-08
> **two4two said:**
> I can't see where to mark this thread solved, but it IS solved.

... Thanks everyone, and now --- how do I mark this thread solved?
Looks like someone already marked this thread solved.  For future reference, the statement in my signature about marking threads as solved is actually a clickable [link]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") that explains all that.

Glad to hear it's now working for you. :)

---

### Post by two4two on 2016-10-10
> **halogen2 said:**
> Looks like someone already marked this thread solved.  For future reference, the statement in my signature about marking threads as solved is actually a clickable [link]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") that explains all that.

Glad to hear it's now working for you. :)

Yes, I marked it as solved.  I noticed your link. :)  

Also, it was your other thread that led me to the resolution to the problem.  Also, QIII helped by keeping me away from unnecessary tedium of working on that driver.  I mentioned graphics problems (related to 3D accel) in this thread, but I'll do a different thread to work on that one.

Thanks guys. :)

---

