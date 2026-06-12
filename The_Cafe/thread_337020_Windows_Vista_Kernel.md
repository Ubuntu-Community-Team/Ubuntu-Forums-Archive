---
title: "Windows Vista Kernel"
date: 2007-01-12
forum: The Cafe
---

### Post by altonbr on 2007-01-12
I thought I'd bring to light a very important document: [The kernel improvements in the new Windows Vista and Windows Longhorn Server]("http://www.microsoft.com/whdc/system/vista/kernel-en.mspx").

This is the "stuff" in behind Windows Vista and the entities that Computer Science majors and Application developers will really hone into.

It's interesting to read that Windows Vista will STILL have to reboot after major DLL updates.

Anyways, enjoy.

---

### Post by Johnsie on 2007-01-12
Ubuntu needs to be rebooted after kernel updates

---

### Post by shining on 2007-01-12
> **Johnsie said:**
> Ubuntu needs to be rebooted after kernel updates

DLL updates <-> kernel updates ?
I thought it was equivalent to shared library updates.

---

### Post by angkor on 2007-01-12
> **Johnsie said:**
> Ubuntu needs to be rebooted after kernel updates

Only if you want to use the new kernel immediately. ;)

---

### Post by ~LoKe on 2007-01-12
> **Johnsie said:**
> Ubuntu needs to be rebooted after kernel updates

No it doesn't.  Only if you want to use the new kernel.  There's also a huge difference between DLL's and a completely new kernel.

---

### Post by Johnsie on 2007-01-12
Yeah but you only need to reboot Windows if you want to use the updates too.... What i'm saying is, if you update Ubuntu you need to reboot if you want to make some major chnages to the system just like on Windows. DLL's and the kernel are a bit different from each other but major chnages require a reboot for them to be activated on both systems.

---

### Post by ~LoKe on 2007-01-12
> **Johnsie said:**
> Yeah but you only need to reboot Windows if you want to use the updates too.... What i'm saying is, if you update Ubuntu you need to reboot if you want to make some major chnages to the system just like on Windows. DLL's and the kernel are a bit different from each other but major chnages require a reboot for them to be activated on both systems.

Changing your kernel is a serious thing.  However, in Windows, it requires you to reboot to just run simple applications.

Completely different and shouldn't be compared.

---

### Post by Brunellus on 2007-01-12
"major" is in the eye of the beholder.  A running Linux system really need only be rebooted to load a new kernel. Almost everything else can be updated "hot".

Well, that's not really so.  Updates to the xserver, for instance, mean restarting the xserver, but that can be done without bringing an entire system down.  Of course, to a desktop user, that's not reallyi all that comforting, since the end of the X session means the end of all the programs that depend upon X.

But it has always astounded me that I should need to reboot my Windows XP system THREE TIMES to apply security patches to Adobe Acrobat.  Why should a document reader update require a FULL system halt?

---

### Post by PatrickMay16 on 2007-01-12
> **angkor said:**
> Only if you want to use the new kernel immediately. ;)
Of course. But with the X update crashes and other problems caused by updates recently, it's far more sensible to boot into the new kernel straight away; you don't know if it will work or not, and it's better to find out now than a week or something later.

---

### Post by maagimies on 2007-01-12
> **Brunellus said:**
> But it has always astounded me that I should need to reboot my Windows XP system THREE TIMES to apply security patches to Adobe Acrobat.  Why should a document reader update require a FULL system halt?You should ask Adobe about that instead of Microsoft, my pdf viewing Foxit Reader in Windows is a simple one exe, takes seconds or less to start, and is updated by downloading a newer exe, with no reboots :mrgreen:
I guess all that bloat in Adobe's software requires full attachment to Windows :mrgreen:

But I DO wonder why Windows needs to be rebooted when you change a Workgroup :confused:

---

### Post by G Morgan on 2007-01-12
DLL updates are the equivalent of installing new libraries in Linux (all those .so files). Indeed DLL stands for dynamic link library. The difference is Windows has to restart if you do a kernel update and if you update libraries. Ubuntu only requires reboots for the kernel any new libraries could be used straight away.

---

### Post by bastiegast on 2007-01-12
In addition, try updating the Windows kernel :cool:

---

### Post by zerhacke on 2007-01-12
> **Johnsie said:**
> Ubuntu needs to be rebooted after kernel updates

When did DLL files in Windows equate to a kernel in Linux? I can't wrap my mind around that one.  Are you new to Linux, Johnsie?

---

### Post by Hendrixski on 2007-01-12
reboots aren't a big problem for me as a laptop user.

What bothers me about what MS is doing with the Vista Kernel is hiding it from application developers who need it.  Like Symantec, or Norton.  This way their software won't work right on Vista, so everyone will stop using their products and switch to the on-board virus-protection software.  The same thing they did with Netscape.  Except... this is with anti-virus software.   
\
Digging their own graves

---

### Post by bonzodog on 2007-01-12
In linux, you CAN actually hot change the kernel in system memory. I don't remember off the top of my head how you do it, but you can swap to the new kernel without rebooting.

---

### Post by FuturePilot on 2007-01-12
> **Brunellus said:**
> But it has always astounded me that I should need to reboot my Windows XP system THREE TIMES to apply security patches to Adobe Acrobat.  Why should a document reader update require a FULL system halt?
Yeah, really. Once I installed updates and restarted only to find out there were more updates for the update I just installed. Oh my.:o

---

### Post by altonbr on 2007-01-13
This PDF doesn't say much, but the first couple cards are interesting tid-bits: [http://www.i.u-tokyo.ac.jp/edu/training/ss/lecture/new-documents/Lectures/00-WindowsKernelOverview/WindowsKernelOverview.pdf](http://www.i.u-tokyo.ac.jp/edu/training/ss/lecture/new-documents/Lectures/00-WindowsKernelOverview/WindowsKernelOverview.pdf)

It's from the University of Tokyo.

---

### Post by Nonno Bassotto on 2007-01-13
I can't remember exactly, but I'm quite sure I read an howto start the new kernel without rebooting. It was not something for the average Joe, involving chroot and the likes, but it should be doable.

---

### Post by Ubunted on 2007-01-13
> **Brunellus said:**
> But it has always astounded me that I should need to reboot my Windows XP system THREE TIMES to apply security patches to Adobe Acrobat.  Why should a document reader update require a FULL system halt?

My last upgrade didn't require any reboots, just uninstallation of Acrobat Reader and running the Foxit executeable once so it associated itself with .pdf files.

---

