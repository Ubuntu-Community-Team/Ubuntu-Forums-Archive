---
title: "How Can I Get My VMWare XP Guest Install To Have 1440x900?"
date: 2008-02-06
forum: Virtualisation
---

### Post by Minker17 on 2008-02-06
I just installed an XP virtual machine in Ubuntu via VMWare Server. Everything is going great, network, and all. My only issue is my resolution. I can't do widescreen resolutions. I installed VMWare Tools and it helped with speed, but it didn't allow me to change my res to 1440x900. I can't download a driver since it is a virtual card. 

Any help would be greatly appreciated!!

---

### Post by Minker17 on 2008-02-06
Anyone? I'm at a loss.

---

### Post by NeoGreen on 2008-02-06
There should be an option in the vwmare program itself to change size/resolution in the screen.  Check this link out  [http://www.devside.net/blog/vmware-player-resolution]("http://www.devside.net/blog/vmware-player-resolution")

---

### Post by fjgaude on 2008-02-06
Screens can be automatically adjusted as you wish. In vmware go to Edit/Preferences/Display. There you see all the choices.

---

### Post by VMan on 2008-02-07
I found that I booted WinXP in the virtual machine; Waited until VMware tools had started (sometimes this takes a little while); than grabbed the edges of the window XP is running in and stretched/moved it to the dimensions I wanted.  

My actual screen is 1280x800.  With the panels on the top and bottom of the screen and the window borders for the VMware window, I ended up with a resolution of approximately (not using laptop right now so don't have exact numbers) 1260 something by 692 or so.  Looks great.  

I found this out by accident when I was moving the window around.

---

### Post by Skeet on 2008-05-21
I have the same problem, old post i know, but i'd still like to know if anyone can help. Currently using Ubuntu 8.04, with latest VMWare Server, (VMWare Tools installed)

---

### Post by Skeet on 2008-05-21
Read a great guide online about getting widescreen resolutions in VMWare Server.

You must edit your "Virtual Machine Name*.vmx" file where Virtual Machine Name is obviously the name of your machine. And add the lines 

```

svga.maxWidth = "1400"
svga.maxHeight = "900"

```

Or whatever you want your res to be.

This fixed the problem for me.

---

### Post by OrwellBridge on 2008-05-21
I'm a noob and I've just 'battled' with this same problem, having just installed Hardy. This is how I solved it.
My setup is a laptop 1280x800 connected to a external screen 1680x1050.
I need to have laptop resolution available when mobile and large resolution when connected to external.

1280x800 (this was found in the ubuntu forums - can't remember the post.
--------
In Vmware server console, diasble the tick options in View menu:
-disable View->AutofitWindow
-disable View->AutofitGuest

Start the XP guest.
In VMWare server console choose View->FitGuestNow

This creates a registry entry on the guest.

In the XP guest, start regedit.
Navigate to:
HKEY_LOCAL_MACHINE->SYSTEM->CurrentControlSet->Control->Video->a number of GUID 

Note a GUID is a global unique identifier term used by microsoft and is a set of long digits.
In one of the GUID id's is a key folder '0000'
In this folder, choose key type REG_SZ named Resolution.kvm and enter (modify) to 1280x800
N.B.> there may be more than one guid available with the key folder '0000' containing the key value name Resolution.kvm, so I chose to change all instances of that key value.

Close regedit. The resolution is now available following xp reboot

1680x1050 (from vmware knowledge base)
---------
In the .vmx file of the vmware image (you need to switch off the vm image) append to the bottom the following:
svga.maxWidth = 1680
svga.maxHeight = 1050
svga.vramSize = 7056000

By the way, the vramSize value is obtained by multiplying by 4 the resolution value i.e. 1680x1050x4
So that maximum reslution is now available.

This is a rubbish solution to what should NOT be a problem, but it got me there in the end.

---

### Post by fjgaude on 2008-05-21
Gosh, all I've ever done with screen size is in the vm console menu, View, checked the autofit boxes, and then I resize console and guest and the windows jump into place. Has nothing to do with .vmx or WinXP files or menus.

---

### Post by OrwellBridge on 2008-05-21
> **fjgaude said:**
> Gosh, all I've ever done with screen size is in the vmconsole menu, View, checked the autofit boxes, and then I resize console and guest and the windows jump into place. Has nothing to do with .vmx or WinXP files or menus.

I remember reading thru fjgaude's posts (who has posted a few times on the subject in these forums) when i was trying to get it to work.
I never got the autofit working properly (guest in full screen mode) - the ubuntu guest always flashed and went black as if it was trying to find the correct resolution. At first i thought it was my video driver not (intel 945GM) working correctly but i believe that it is part of the distribution so is not an issue (i hope).

If there is an easy solution then great, but the 'using a hammer to crack a nut' approach worked for me. Good luck.

---

### Post by Swalchy on 2008-05-23
> **OrwellBridge said:**
> I'm a noob and I've just 'battled' with this same problem, having just installed Hardy. This is how I solved it.
My setup is a laptop 1280x800 connected to a external screen 1680x1050.
I need to have laptop resolution available when mobile and large resolution when connected to external.

1280x800 (this was found in the ubuntu forums - can't remember the post.
--------
In Vmware server console, diasble the tick options in View menu:
-disable View->AutofitWindow
-disable View->AutofitGuest

Start the XP guest.
In VMWare server console choose View->FitGuestNow

This creates a registry entry on the guest.

In the XP guest, start regedit.
Navigate to:
HKEY_LOCAL_MACHINE->SYSTEM->CurrentControlSet->Control->Video->a number of GUID 

Note a GUID is a global unique identifier term used by microsoft and is a set of long digits.
In one of the GUID id's is a key folder '0000'
In this folder, choose key type REG_SZ named Resolution.kvm and enter (modify) to 1280x800
N.B.> there may be more than one guid available with the key folder '0000' containing the key value name Resolution.kvm, so I chose to change all instances of that key value.

Close regedit. The resolution is now available following xp reboot

1680x1050 (from vmware knowledge base)
---------
In the .vmx file of the vmware image (you need to switch off the vm image) append to the bottom the following:
svga.maxWidth = 1680
svga.maxHeight = 1050
svga.vramSize = 7056000

By the way, the vramSize value is obtained by multiplying by 4 the resolution value i.e. 1680x1050x4
So that maximum reslution is now available.

This is a rubbish solution to what should NOT be a problem, but it got me there in the end.

Thanks for that - been trying for ages to find something that could give me my 1280x768 resolution. Your method worked flawlessly.

Although, I do have to wonder why 1280x768 wouldn't be one of installed options, as it's quite a common widescreen resolution...

---

