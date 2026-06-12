---
title: "New computer"
date: 2009-11-01
forum: System76 Support
---

### Post by AutoLink on 2009-11-01
My plan is to get an Ubuntu desktop (such as Wildebeest) and install Windows (initially XP, maybe later W7) for dual booting. Down the road I probably will try to use Windows through virtualization. In any case, I can’t do without Windows yet. I have several questions:
  **1.**What specs are needed for Windows dual booting? Virtualization?
  **2.**Would having Windows on the computer influence System76’s support policies?
  **3.**I am trying to decide between a Core i5-750 and a Core i7-860. Other than $125, the main difference between them seems to be that the i5 has hyperthreading disabled, whereas the i7 doesn’t. Is there any significant software available or on the way in the near future that can take advantage of the additional i7 features?
   
  Thank you in advance.

---

### Post by HotShotDJ on 2009-11-01
> **AutoLink said:**
> My plan is to get an Ubuntu desktop (such as Wildebeest) and install Windows (initially XP, maybe later W7) for dual booting. Down the road I probably will try to use Windows through virtualization. In any case, I can’t do without Windows yet. I have several questions:
  **1.**What specs are needed for Windows dual booting? Virtualization?
  **2.**Would having Windows on the computer influence System76’s support policies?
  **3.**I am trying to decide between a Core i5-750 and a Core i7-860. Other than $125, the main difference between them seems to be that the i5 has hyperthreading disabled, whereas the i7 doesn’t. Is there any significant software available or on the way in the near future that can take advantage of the additional i7 features?
   
  Thank you in advance.
Fist of all, I strongly recommend that you try out virtualization first rather then second (my current favorite is VirtualBox PUEL version) -- see my signature, with props to Thomasaaron.

[LIST=1]
[*]I've looked at most of the System76 offerings, and they all look like they will easily support Windows XP and probably Windows Vista and Windows 7.  For virtualization, you will need a minimum of 2 Gig RAM, although I recommend 4 Gig RAM for this.  The more RAM you have, the more RAM you can assign to the virtual machine.  Buy as much RAM as you can afford.  On my PanP5 (P8700 Core 2 Duo CPU and 4 Gig RAM), I have a Windows XP virtual machine running at what I can only describe as speeds indistinguishable from native.  Both the Core i5 and Core i7 will support hardware virtualization (VT-x) just fine.
[*]System76 does not officially support Windows.  But my experience is that they will do their best to help if you run into a problem
[*]I don't know.  I'm sure somebody else who does will chime in.
[/LIST]

---

### Post by AutoLink on 2009-11-01
> **HotShotDJ said:**
> Fist of all, I strongly recommend that you try out virtualization first rather then second (my current favorite is VirtualBox PUEL version) -- see my signature, with props to Thomasaaron.


   Certainly, virtualization is the way to go if it works. There are three major activities that I anticipate possibly needing Windows for:
   
  1. I use a Palm Centro, syncing with my desktop computer, and likely will switch to an iPhone next year. Would these phones be expected to work well with virtualization, or can I sync directly through Ubuntu?
   
  2. Also, I use Citrix a lot, both GoToMyPC and Corporate remote access. Do you know if Citrix works with virtualization? Citrix’s support for Linux is very limited.
   
  3. If I am unable to get all of the Ubuntu drivers that I need for my MFDs (an HP Officejet 6500 and a Canon MF4150) to fully function, are they likely to work under virtualization?
   
  Thanks again.

---

### Post by HotShotDJ on 2009-11-01
Regarding your first question... I really don't know.  I can tell you that I'm able to sync my cell phone (Nokia 6085) directly in Linux using MultiSync 0.90 with the opensync (version 0.22) evolution and gnokii plugins.
> **AutoLink said:**
> 2. Also, I use Citrix a lot, both GoToMyPC and Corporate remote access. Do you know if Citrix works with virtualization? Citrix&#8217;s support for Linux is very limited.:shock:
I've used Citrix, and it has always worked wonderfully under Linux.  The initial installation can sometimes be a pain, but once you get it installed, you shouldn't have any client side issues.  What problems have you experienced?  GoToMeetingPC should work with Virtualization as long as you aren't trying to use a webcam with it.  Webcams are notoriously buggy under VirtualBox.  I've never gotten one to work without significant problems.  I've never used GoToMeeting through Citrix.  However, if it works in Windows, I see no reason why it shouldn't work under Linux.
> **AutoLink said:**
> 3. If I am unable to get all of the Ubuntu drivers that I need for my MFDs (an HP Officejet 6500 and a Canon MF4150) to fully function, are they likely to work under virtualization?I only purchase hardware, such as printers, that are known to be fully supported under Linux, so I really have no experience with unsupported printers.  However, I do know that networked printers will not be a problem with virtualization.  Just install the Windows drivers and connect to the networked hardware in your Windows VM just like you would with a native installation.  This should also be the case with USB printers, as long as you use the PUEL version of VirtualBox.  Remember, though, with most USB devices (with the exception of keyboards and mice), once it is "captured" by the VM, the device won't be available to Linux until it is released by the VM.

---

### Post by AutoLink on 2009-11-02
> **HotShotDJ said:**
>  [SIZE=2]I've u[/SIZE][SIZE=2]sed Citrix, and it has always worked wonderfully under Linux.  The initial installation can sometimes be a pa[/SIZE]in, but once you get it installed, you shouldn't have any client side issues.  What problems have you experienced?...  
I only purchase hardware, such as printers, that are known to be fully supported under Linux, so I really have no experience with unsupported printers. [SIZE=1]

[/SIZE]   [SIZE=2][FONT=Arial]Actually, I had never tried Citrix outside of Windows before. It does appear that the corporate access will work if I ever get it set up. I was unsuccessful in doing so using my Wubi installation, but I found some instructional videos that I'll look at when I get a chance.[/FONT][/SIZE]
 [FONT=Arial]
Everything did work with my HP MFD except the two sided printing. Maybe an update will fix that.[/FONT]

Overall, I spent a lot of time spinning my wheels this weekend. There isn't a lot in Ubuntu that is intuitive to a Windows user. I have a lot to learn, but I'm looking forward to it.

---

