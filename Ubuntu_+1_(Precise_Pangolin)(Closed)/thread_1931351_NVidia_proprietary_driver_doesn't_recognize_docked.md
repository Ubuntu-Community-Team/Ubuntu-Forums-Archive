---
title: "NVidia proprietary driver doesn't recognize docked state"
date: 2012-02-25
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by skewty on 2012-02-25
Notebook: Dell Latitude E6510 (Intel i7, 8GB RAM, NVidia video)

I wanted to give Ubuntu another try.  I installed the newest daily build of 12.04.  I used Ubuntu back in 2010 with some success but needed the kernel updates of newer versions for trackpad, USB devices and such.  Unity didn't work well for multi-monitor or with VirtualBox in 11.10 so I got frustrated and left.

While Ubuntu multi-monitor support with Unity is clearly improving, I find Ubuntu is still nowhere close to where it needs to be.  "Paper cuts" everywhere.

The biggest issue for me now is the NVidia proprietary driver doesn't seem to recognize when my notebook is docked and the monitor is closed.  It still draws windows onto it.  How does one use a mouse to get a window off of a monitor that doesn't exist??  Why is such a popular driver so dumb and untested so many years later?

Also, the NVidia prop driver makes all sorts of screen corruption junk during its initialization.  This is totally unacceptable.

I use my computer as a VirtualBox host for many activities.  Our Corp network switches only allow one MAC per access port so when I start my Corp VM (bidged NIC) Ubuntu musn't have sent any TCP/IP packets or it would have registered the host MAC.  I renamed the auto-generated network entry and selected "Disabled" on the IPV4 tab.  Why is there no "Disabled" on the IPV6 tab?  I chose "Ignore" on the IPV6 tab.  I was hoping this would let me plug in the Ethernet cable and have it not attempt to communicate.  What I get is the endless cycling of the animation up there in network manager.  This is a huge distraction.

When I plug in my USB 1 Gig Ethernet adapter, it works.  My complaint is how the connections are labelled in network manager.  If I have a bunch, which I do, there is no nice way to sort them by which adapter they belong to.  Perhaps another column is required in the list.

Software Manager is another horrible app.  I downloaded VirtualBox from VirtualBox.org.  I double clicked the .deb, Software Manager loaded.  I clicked the Install button.  The "Install" button goes gray for a moment and then the "Authenticate" window opens.  The "Install" button is black again and it responds to mouse clicks.  Fail!  Since it responded to mouse clicks, it seems to queue the clicks.  So basically it tries to start the install process multiple times.  While it is installing, the button remains black and the screen gives no indication that something is happening.  I have to know to click the tab at the top?  Why aren't they using the standard progress windows for File Copy and such?

How does one graphically add a user to the "vboxusers" group using the default installed apps of 12.04?

Anyways..  I am not interested in filing bug reports / feature requests.  I did that for years and can't handle the additional communication that results.

Here is another rediculous long standing bug.  When I click All Formats button in Save As dialog in LibreOffice calc I get a big list that opens and half of it is unused space.  Really!?

The GNU / Open Source people really need to stop emphasizing on their differences and focus on what they have in common.  I really want the OpenSource stuff to  work but there are too many personal agendas and big egos in the way.  It is sad.  Why must many suffer because of the decisions of a few?  (See the parallels in government / elsewhere in life?)

Please somebody, file these bits where they need to be filed so somebody might address them.

Thanks,

Scott

---

### Post by effenberg0x0 on 2012-02-25
> **skewty said:**
> Notebook: Dell Latitude E6510 (Intel i7, 8GB RAM, NVidia video)

I wanted to give Ubuntu another try.  I installed the newest daily build of 12.04.  I used Ubuntu back in 2010 with some success but needed the kernel updates of newer versions for trackpad, USB devices and such.  Unity didn't work well for multi-monitor or with VirtualBox in 11.10 so I got frustrated and left.

It has improved a lot, both in hardware detection and multi-monitor support on Unity. It works OK for me in many different hardware tested.

> **skewty said:**
> 
While Ubuntu multi-monitor support with Unity is clearly improving, I find Ubuntu is still nowhere close to where it needs to be.  "Paper cuts" everywhere.

The biggest issue for me now is the NVidia proprietary driver doesn't seem to recognize when my notebook is docked and the monitor is closed.  It still draws windows onto it.  How does one use a mouse to get a window off of a monitor that doesn't exist??  Why is such a popular driver so dumb and untested so many years later?


I'm not sure. But it doesn't work for me on Windows too. 

> **skewty said:**
> 
Also, the NVidia prop driver makes all sorts of screen corruption junk during its initialization.  This is totally unacceptable.

It's not NVidia, it's Plymouth. You have to disable it if you are using NVidia proprietary drivers and not nouveau. Plymouth does not work with it.

> **skewty said:**
> 
I use my computer as a VirtualBox host for many activities.  Our Corp network switches only allow one MAC per access port so when I start my Corp VM (bidged NIC) Ubuntu musn't have sent any TCP/IP packets or it would have registered the host MAC.  I renamed the auto-generated network entry and selected "Disabled" on the IPV4 tab.  Why is there no "Disabled" on the IPV6 tab?  I chose "Ignore" on the IPV6 tab.  I was hoping this would let me plug in the Ethernet cable and have it not attempt to communicate.  What I get is the endless cycling of the animation up there in network manager.  This is a huge distraction.

 I'm not sure I understand you. No matter what network setting you use in VirtualBox, it is virtual: It will rely on the host's real hardware and connection. Normally the host has a connection to your LAN and the Guest will be configured to share that connection via Bridge or NAT, or it will emulate it's own NIC and send DHCP requests using a customizable MAC. But, no matter what option is chosen, the real NIC will establish a real connection to the LAN.

> **skewty said:**
> 
When I plug in my USB 1 Gig Ethernet adapter, it works.  My complaint is how the connections are labelled in network manager.  If I have a bunch, which I do, there is no nice way to sort them by which adapter they belong to.  Perhaps another column is required in the list.

Yes, although the information is easily accessible elsewhere, it would be a nice feature.

> **skewty said:**
> 
Software Manager is another horrible app.  I downloaded VirtualBox from VirtualBox.org.  I double clicked the .deb, Software Manager loaded.  I clicked the Install button.  The "Install" button goes gray for a moment and then the "Authenticate" window opens.  The "Install" button is black again and it responds to mouse clicks.  Fail!  Since it responded to mouse clicks, it seems to queue the clicks.  So basically it tries to start the install process multiple times.  While it is installing, the button remains black and the screen gives no indication that something is happening.  I have to know to click the tab at the top?  Why aren't they using the standard progress windows for File Copy and such?

It is indeed an immature application, but under constant development. I'm not experiencing any of the problems you mentioned with a fully updated install, but I don't doubt they are there. Unfortunately it still has many problems.

> **skewty said:**
> 
How does one graphically add a user to the "vboxusers" group using the default installed apps of 12.04?

I can't find it either. Ideally, one would hit the Dash and go to "User Accounts". Then select "Unlock" and edit groups for the required user. But there's no groups options there anymore. I'm sure it will be available sometime.  

> **skewty said:**
> 
Anyways..  I am not interested in filing bug reports / feature requests.  I did that for years and can't handle the additional communication that results.

This is not productive. Developers can't reasonably test software in all of the worlds possible hardware without help from users, and that's the only way Linux distros and free software improves. Basically, if that's your policy, then it's useless to complain about things that don't work as you'd like them to. Open source is strongly participative. If you don't wanna participate, report bugs, request features, interact with development, you should really give up Linux and use Windows. 
  
> **skewty said:**
> 
 Here is another rediculous long standing bug.  When I click All Formats button in Save As dialog in LibreOffice calc I get a big list that opens and half of it is unused space.  Really!?

Libreoffice is not developed by Ubuntu and this bug will affect any distro that uses it (mostly all). But, again, they do have their development process and are open to bug reports, feature requests, etc.

> **skewty said:**
> 
The GNU / Open Source people really need to stop emphasizing on their differences and focus on what they have in common.  I really want the OpenSource stuff to  work but there are too many personal agendas and big egos in the way.  It is sad.  Why must many suffer because of the decisions of a few?  (See the parallels in government / elsewhere in life?)

I don't see how that fits reality. All open source software is available to adoption and developed by people using many different distros. It makes no sense. Users of one or another distro may have some sense of competition but, from a developer's point of view, software is software - it's made to run in any distro.
> **skewty said:**
> 
Please somebody, file these bits where they need to be filed so somebody might address them.


Effenberg

---

