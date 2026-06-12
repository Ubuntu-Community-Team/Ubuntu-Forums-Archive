---
title: "Age of Mythology in Virtual Box"
date: 2008-12-10
forum: Virtualisation
---

### Post by _Arelas_ on 2008-12-10
I'm currently trying to get Age of Mythology to work in Virtual Box. I circumvented the debugger problem by using a no-cd fix, but now when I try to run the game it displays the error message:

> This graphics card is not supported by Age of Mythology.
Please check [http://microsoft.com/games/ageofmythology](http://microsoft.com/games/ageofmythology) for a full list of supported graphics cards.
Age of Mythology will now exit.

```
Video Card 0: VBoxDisp.dll VirtualBox Graphics Adapter Vendor(0x80EE) Device(0xBEEF)
```

Is there some way I can convince Age of Mythology to run on this adapter, or change my adapter so it will register as supported?

---

### Post by b4r7 on 2008-12-11
same request.. i tried to install the game with wine, but it works badly..

run it on virtualbox could be THE solution.. but there's this problem with the graphic card..

---

### Post by binbash on 2008-12-11
it wont work on virtualbox, however it might work on vmware which has a little 3d support

#  16 MB 3D video card is required; 32 MB video card is recommended.

---

### Post by _Arelas_ on 2008-12-11
I have the required graphics card on my main machine, the problem is changing the Adapter so that Age of Mythology recognizes it as a supported graphics card. It seems like if I just installed a different driver, it should work fine.

---

### Post by vgrisham on 2009-03-04
> **binbash said:**
> it wont work on virtualbox, however it might work on vmware which has a little 3d support

#  16 MB 3D video card is required; 32 MB video card is recommended.

I tried it on vmware in early January 2009. No dice.

---

### Post by ocozette on 2010-02-22
> **_Arelas_ said:**
> I'm currently trying to get Age of Mythology to work in Virtual Box. I circumvented the debugger problem by using a no-cd fix, but now when I try to run the game it displays the error message:
 
 
 
Is there some way I can convince Age of Mythology to run on this adapter, or change my adapter so it will register as supported?
 
 
To play with Age of Mythology under vmware (tested successfully under my vmware workstation 7), you must create a file named
"C:\Program Files\Microsoft Games\Age of Mythology\gfxconfig\0x80EE_virtualbox.gfx" and it will work.
 
It's a adaptation of my solution successflly tested under vmware, so you must see the display driver and replace VirutalBox by the vendor (VirtualBox or Sun) and replace month/day/year (9/21/2009 here) by the date of your virtuabox driver.
 
 
In this this file you must put the following lines in "C:\Program Files\Microsoft Games\Age of Mythology\gfxconfig\0x80EE_virtualbox.gfx":
\[config\]
Vendor=VirtualBox
defaultdevice=CyberBladeXP.gfx
 
\[knownGoodDriver\]
Month=9
Day=21
Year=2009
Product=0
Version=0
SubVersion=0
Build=0
 
\[device\]
0xBEEF=CyberBladeXP,CyberBladeXP.gfx

---

### Post by DragonQ on 2010-04-08
ocozette, I tried your solution but it doesn't work for me. I'm using VirtualBox 3.1.6 and I've enabled both 2D and 3D acceleration of a Windows XP virtual machine. I created a "0x80EE_virtualbox.gfx" file in the gfxconfig and gfxconfig2 folders and paste this inside them:

[I]\[config\]
Vendor=VirtualBox
defaultdevice=CyberBladeXP.gfx

\[knownGoodDriver\]
Month=3
Day=25
Year=2010
Product=0
Version=0
SubVersion=0
Build=0

\[device\]
0xBEEF=CyberBladeXP,CyberBladeXP.gfx[/I]

However, I still get the "unsupported graphics card" window, with the graphics card being quoted as "  3/25/2010 3.1.6.0". If I replace the "vendor" property to "Sun" or "Sun Microsystems, Inc.", nothing changes. Any ideas?

---

### Post by XNess01 on 2010-04-13
> **DragonQ said:**
> ocozette, I tried your solution but it doesn't work for me. I'm using VirtualBox 3.1.6 and I've enabled both 2D and 3D acceleration of a Windows XP virtual machine. I created a "0x80EE_virtualbox.gfx" file in the gfxconfig and gfxconfig2 folders and paste this inside them:

[I]\[config\]
Vendor=VirtualBox
defaultdevice=CyberBladeXP.gfx

\[knownGoodDriver\]
Month=3
Day=25
Year=2010
Product=0
Version=0
SubVersion=0
Build=0

\[device\]
0xBEEF=CyberBladeXP,CyberBladeXP.gfx[/I]

However, I still get the "unsupported graphics card" window, with the graphics card being quoted as "  3/25/2010 3.1.6.0". If I replace the "vendor" property to "Sun" or "Sun Microsystems, Inc.", nothing changes. Any ideas?


In the created file, delete the "\" x that still does not recognize drivers
In my case I also need to Install the MSXML 4.0
Everything works ok
Regards

---

### Post by DragonQ on 2010-04-18
Thanks, that gets rid of the error message. However, after the game loads I just get a blank screen (same as with Microsoft Virtual PC). Did you do anything else to get it to work?

EDIT: Never mind, I fixed it using some D3D8 and D3D9 workaround instructions that I found for Windows 2000.

---

### Post by camdude on 2010-04-18
This advice may sounds really stupid, but I might try downloading Microsoft VPC 2007, and running that under WINE, and installing AOM on VPC... but idk if that will work

---

### Post by DragonQ on 2010-04-18
AoM doesn't work on VPC. It'll load but you'll just have a black screen.

---

### Post by spamhideout on 2010-05-17
> **DragonQ said:**
> EDIT: Never mind, I fixed it using some D3D8 and D3D9 workaround instructions that I found for Windows 2000.
 
 
DragonQ, what work around did you use? I'm having the same difficulty with a black screen at the main menu of AOM in a Win2000 OS in Virtual Box. I only get the music and a pointer.
 
UPDATE: I figured it out.  You can find the final piece to the puzzle here: [http://forums.virtualbox.org/viewtopic.php?f=2&t=25937](http://forums.virtualbox.org/viewtopic.php?f=2&t=25937)
You need to install 3D acceleration in Windows 2000.

---

### Post by YanH on 2010-07-31
> **XNess01 said:**
> In the created file, delete the "\" x that still does not recognize drivers
In my case I also need to Install the MSXML 4.0
Everything works ok
Regards
Hi, I don't suppose you could post an example of your config file. I've tried various combinations of text inside the file but cannot get past the unsupported graphics card message. Also I'm not quite sure what the 'Delete the "\" x ' means I should delete. Thanks.

---

### Post by vaisius on 2011-02-01
I can confirm that Age of Mythology works on VirtualBox 4.0.2 with Windows XP SP2. I tried installing SP3 and got the error that my video card is unsupported. 
Using 0x80EE_virtualbox.gfx on Win XP SP3 helped to start the game, but only black screen appears after loading.

Good luck.

---

### Post by caprilo on 2011-12-10
> **YanH said:**
> Hi, I don't suppose you could post an example of your config file. I've tried various combinations of text inside the file but cannot get past the unsupported graphics card message. Also I'm not quite sure what the 'Delete the "\" x ' means I should delete. Thanks.
I also wasn't sure of what deleting the "\" was. In fact, it is to change all "\[" and "\]" for "[" and "]". After that, it works without problem.

---

