---
title: "Is there a way to get Wine in Windows?"
date: 2009-07-03
forum: Wine
---

### Post by Canthaxthis on 2009-07-03
I played around on my friend's Ubuntu for about three hours while he was away. His computer is about half the speed as mine and he has the same steam games as me.

When I played them, they ran better, looked better and had less bugs then Windows.

I don't want to half my drive and install OS for a speed boost as it breaks the workflow in Windows. I would switch if I didn't have programs that are strictly for Windows Vista.

 Is there way to get Wine working in Windows Vista?

---

### Post by madverb on 2009-07-03
You don't need Wine in Windows. I would also be surprised if those games were running better in Wine. I don't think I have come across a steam game that runs better in Wine than in Windows.

---

### Post by congminh1709 on 2009-07-03
Hi everyone, Linux has Wine to support Windows Softwares, does Windows have a tool like this to run Linux Softwares, too?

---

### Post by steveneddy on 2009-07-03
> **Canthaxthis said:**
> 
 Is there way to get Wine working in Windows Vista?

Wine is a software application to run Windows applications in Linux.

Wine won't run on Windows and shouldn't.

---

### Post by Th3_uN1Qu3 on 2009-07-04
> **steveneddy said:**
> Wine is a software application to run Windows applications in Linux.

Wine won't run on Windows and shouldn't.

And the OP's friend just happens to be extremely lucky with Wine. :guitar:

---

### Post by evermooingcow on 2009-07-04
> **congminh1709 said:**
> Hi everyone, Linux has Wine to support Windows Softwares, does Windows have a tool like this to run Linux Softwares, too?

Cygwin
[http://www.cygwin.com/](http://www.cygwin.com/)

---

### Post by Meow27 on 2009-07-04
> **steveneddy said:**
> Wine is a software application to run Windows applications in Linux.

Wine won't run on Windows and shouldn't.

it has worked before, its just like a windows emulator on top of windows, except that wine isnt an emulator :/

---

### Post by Tibuda on 2009-07-04
> **congminh1709 said:**
> Hi everyone, Linux has Wine to support Windows Softwares, does Windows have a tool like this to run Linux Softwares, too?

I don't think there's really a need for a Linux emulator in Windows, beacuase most Linux applications are open source, and use a cross-platform API (Gtk+, Qt, wxWidgets). Cygwin is good because allows you have some great command-line tools like grep, that are not available in Windows.

---

### Post by David Gerard on 2009-07-06
There's a [Wine On Windows]("http://wiki.winehq.org/WineOnWindows") page on the Wine wiki.

Summary: it doesn't even compile yet :-)

That said, I understand there are efforts to use Wine's Direct3D layer on Windows. When more of DX10 is implemented, that would bring DX10 to XP!

---

### Post by Th3_uN1Qu3 on 2009-07-07
> **David Gerard said:**
> That said, I understand there are efforts to use Wine's Direct3D layer on Windows. When more of DX10 is implemented, that would bring DX10 to XP!

DX10 already works on XP. Only a handful of games are supported, but i believe we'll reach DX12 before that handful of games gets supported in Wine...

[www.kms-system.com](www.kms-system.com)

---

### Post by David Gerard on 2009-07-07
> **Th3_uN1Qu3 said:**
> DX10 already works on XP. Only a handful of games are supported, but i believe we'll reach DX12 before that handful of games gets supported in Wine...

Yeah, DX10 support in Wine is presently minimal ... stub functions that say "hi, I exist" but don't actually do anything. OTOH, you'd be surprised how many Windows apps work perfectly well with stubs that don't actually do anything but claim to exist ... Win32 is more deeply messed-up than anyone dared contemplate, it really is.

---

### Post by Th3_uN1Qu3 on 2009-07-07
> **David Gerard said:**
> Win32 is more deeply messed-up than anyone dared contemplate, it really is.

More likely, there are things that *have* to be there even if they are not used, or they are automatically inserted by the compiler, coz no one still codes in ASM nowadays, isn't it so? Maybe only Steve Gibson.

I'm only 18 but i liked DOS games as a kid so i've started learning some DOS ASM lately... It probably won't be of too much use, but hey, quick 'n dirty switching of graphics modes is cool. :D

---

