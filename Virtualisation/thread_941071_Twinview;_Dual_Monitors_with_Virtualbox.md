---
title: "Twinview; Dual Monitors with Virtualbox?"
date: 2008-10-07
forum: Virtualisation
---

### Post by olhat on 2008-10-07
I tried to install nVidia Windows xp driver in Virtualboxwindows xp
The following error happened:

NVIDIA Setup Error:
The NVIDIA setup program could not locate any drivers that are compatible with your current hardware. Setup will now exit.

Is it supposed to work on Twinview dual monitor setup both monitors or am I chasing a red herring again?

---

### Post by bradmkjr on 2008-10-07
You forgot the basis of virtualization.

Windows is running on Virtual hardware, not actual hardware. 

To give you a better idea, read my post here:
[http://x86virtualization.com/intel/vmhp-sun-virtualbox-162-part-3-of-many.html](http://x86virtualization.com/intel/vmhp-sun-virtualbox-162-part-3-of-many.html)

Virtualbox actually uses this video card: "VirtualBox Graphics Adapter [Display adapter]" not an Nvidia.

So if your system is working with dual monitors, in Virtualbox, I believe you can stretch the window to fill both screens. I don't know if virtual box has spanning, like VMware workstation has. For more information on multiple monitor support read my post:
[http://x86virtualization.com/virtualization/mulitple-monitors-with-ultramon-and-vmware-workstation.html](http://x86virtualization.com/virtualization/mulitple-monitors-with-ultramon-and-vmware-workstation.html)

Hope this helps,
Bradford Knowlton
[http://x866v.com](http://x866v.com)

---

### Post by specterunseen on 2009-03-04
I've been running into this issue. I'm ALL FOR SWITCHING TO LINUX if I can, however I have a triple screen setup. Hoping when the card comes in that everything runs smoothly, as I've seen some support, limited, for it as it is an ATI Sappaphire card. 

Even when I streched out the virtualbox, it wouldn't let me drag between the other monitors in twin view. I'm upgrading to 3-4 monitors this week, and if Ubuntu won't allow me to run visual studio and office in seamless and use all the windows, then its going to be relegated sadly to the stack of "use in the future." I really want to use Ubuntu, however school requirements require everything in Office 2007 and Visual Studio format. 

Anyone have a simple solution for us **NEWBS** on how to use seamless mode among multiple windows. I'd love to stick with Ubuntu, though the learning curve is tough, but multiple monitor support AND Multiple monitor support with Virtualbox is essential since I need this for programming projects. :(

:popcorn:

---

### Post by Vadi on 2009-03-04
Can't you just maximize the virtualbox window?

works okay here..

---

### Post by specterunseen on 2009-03-04
> **Vadi said:**
> Can't you just maximize the virtualbox window?

works okay here..

When maximized, it adopted the monitor resolution I was working on, but still wouldn't use the 2nd monitor. I'm about to go to 3-4 monitors, so that's not cool! I need multiple monitors with my programming tools or its wasting all that useful space!

---

### Post by Vadi on 2009-03-04
I see your issue.

At any rate, this would be a question to Virtualbox who makes the Virtualbox drivers which the guest uses, not your host.

---

### Post by Ng Oon-Ee on 2009-03-04
Actually, if you're already able to drag the window from monitor to monitor, you should be able to resize the window to fit all your monitors. Or set a rule in Compiz to do that, using ccsm.

Of course, more than 2 monitors on nVidia in linux is currently a bit of hit and miss due to the state of xinerama with XGL, works fine IF you don't want hardware acceleration. That's a more complicated problem, but if you can get that working, then VBox should be able to handle it. Note that you should NOT in any case use separate X servers without xinerama, since windows will not be able to be moved/resized between the screens.

---

### Post by Vadi on 2009-03-04
Setting up dual monitors was easy using the nvidia's twinview thing. However the virtualbox only resizes to so much - the rest it pads with blank spaces.

---

### Post by yther on 2009-03-04
Just out of curiosity, have you tried this idea?  VirtualBox has a "seamless" mode, similar to VMware's "Unity" mode.  I think you should be able to use that, to break the VS and Office apps out of the Windows desktop and put them on whichever monitors you like.

Would that help you, or am I missing the point?  :)

---

### Post by Vadi on 2009-03-04
No, didn't work unfortunately.

---

### Post by specterunseen on 2009-03-05
Ok. I'm at the brink of giving up. I've spent more time than ever as a newb fiddling trying to really give it my all and I successfully editing my x config file for the first time and got it to work with two 20in monitors in POTRAIT MODE in the right position (googled a lot!). 

Still facing major hurdles: 

1. MUST have Visual C# and Office 2007 working in VirtualBox to keep Linux, otherwise have to go straight windows for school. Visual C# won't succeed in installing period. .NET framework update won't work, etc. Here's the error if someone knows what is going on. 

2. Can't get the integrated card, ie the third monitor, to even show up??? The graphics card is running fine, but not the integrated card that I can use for #3. It's a integrated Nvidia, so I don't know why it won't show up in the GUI Nvidia editor. 

3. USING Virtual Box across multiple monitors. Logging in via RDP (my first time trying this stuff) was successful, but a empty black screen. 


Seems that Windows has the upperhand with the ease of use with multiple monitors due to all the proprietary issues with graphics cards. :(

---

### Post by specterunseen on 2009-03-05
> EventType : visualstudio8setup     P1 : 10861     
P2 : 9.0.30729.01_orcas_x86_net     P3 : msi     P4 : inst     P5 : f     P6 : -
P7 : -     P8 : 1601     P9 : -     P10 : 



C:\DOCUME~1\Sheldon\LOCALS~1\Temp\WLFC.tmp
C:\DOCUME~1\Sheldon\LOCALS~1\Temp\SDBD.tmp
C:\DOCUME~1\Sheldon\LOCALS~1\Temp\VSW0\VSSWMSISummary.txt
C:\DOCUME~1\Sheldon\LOCALS~1\Temp\VSW0\VSSWMSIFailInfo.txt
<NoFiles>


Here was my error during install, all the errors are similar with some slight differences in some of the file names.

---

### Post by Vadi on 2009-03-05
What Ubuntu version are you on, btw? I hope not 6.06.

---

### Post by specterunseen on 2009-03-05
> **Vadi said:**
> What Ubuntu version are you on, btw? I hope not 6.06.



8.10 - intrepid Ibex:)

---

### Post by Vadi on 2009-03-05
Ok. Well, see virtualbox forums or their bug tracker, I doubt their people are going to find this thread. This is purely an issue with their driver

---

