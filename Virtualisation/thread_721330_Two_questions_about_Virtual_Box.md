---
title: "Two questions about Virtual Box"
date: 2008-03-11
forum: Virtualisation
---

### Post by GSZX1337 on 2008-03-11
I have started using an XP Virtual Box.

The first question is: Why does #1 DVD Ripper not work? It crashes every time I use it. I do have Virtual Box mounting the Drive. [If ripping DVDs is impossible on Virtual Box, what is a good DVD ripper for Linux that can convert the DVD to DivX]

The second question is: How can I take files from my Virtual Box and put them in my Documents folder? I use Adobe Fireworks CS3 and need the files on my physical HD.

Thanks in advance.
~GSZX1337

---

### Post by luisromangz on 2008-03-11
About the first one I don't know, as I don't rip DVDs, but there are many solutions for the second. You can use samba shares, or use the Virtualbox's shared folder feature, for example.

---

### Post by Live-Dimension on 2008-03-11
Vbox's share works like this.
Make sure the VM is turned off. Go settings. Shared folders. Setup a new share, don't forget what you named the share.

Go into the GuestOS (XP)

My computer. Dropdown address bar, go down to "My Network Places".
Entire Network
VirtualBox Shared Folders
Right click the displayed folder (should be \\VBOXSRV\SharedFolderName)
Map Network Drive

if you want - change the drive. This will show up as a Network Drive in my computer, and functions as a normal one (minus xp's annoying "Are you sure you want to run" network thing).

---

### Post by Hero of Time on 2008-03-11
> **Live-Dimension said:**
> if you want - change the drive. This will show up as a Network Drive in my computer, and functions as a normal one (minus xp's annoying "Are you sure you want to run" network thing).
This is incorrect if you install IE7. With the installation of IE7, detection of zones doesn't work as it should. Therefor, network shares through UNC paths are detected as Intranet Zone, but when you map it to a drive, it will change to Internet Zone. See [this MS KB article](http://support.microsoft.com/kb/929798) for more info about this issue. You can request a hotfix, but as I experience it, it doesn't work for the Vboxsvr share. If you have set up Samba and use any form of networking (preferably NAT) then you can use that share too, which will work as it should. If you use NAT, then mount the drive to ip 10.0.2.2\sambashare.

For the first question, are you sure it works on normal XP? Did you install the correct updates for the program too? The program should just work, as it's the same as running it on a fysical machine.

---

### Post by Live-Dimension on 2008-03-12
Thanks for the heads up Hero!
I havent gottern around to installing IE7 yet, but was going to soon :P

---

### Post by Hero of Time on 2008-03-12
I tested this by uninstalling IE7 on server 2003 and it didn't work. Perhaps the installer of IE7 broke it already and was irreversable by uninstalling IE7, but it might be that the issue is already happening. As I have it on my systems, my VM has this problem, my PC doesn't (actually, the other way around, name is fine, IP is bogus).

---

### Post by GSZX1337 on 2008-03-12
> **Hero of Time said:**
> 
For the first question, are you sure it works on normal XP? Did you install the correct updates for the program too? The program should just work, as it's the same as running it on a fysical machine.

Yes it does work on my XP partition and it is exactly the same on my partition as it is on my VBox.

---

### Post by Hero of Time on 2008-03-13
> **GSZX1337 said:**
> Yes it does work on my XP partition and it is exactly the same on my partition as it is on my VBox.
Does it use specific CPU instructions like SSE2? Check with CPU-z if the virtual CPU supports it. As I have an Intel T2300 CPU that supports Vitualisation Technology, the CPU is passed to the VM directly with all options (single core though, and lower speed) for instructions supported by the CPU.

---

### Post by GSZX1337 on 2008-03-13
> **Hero of Time said:**
> Does it use specific CPU instructions like SSE2? Check with CPU-z if the virtual CPU supports it. As I have an Intel T2300 CPU that supports Vitualisation Technology, the CPU is passed to the VM directly with all options (single core though, and lower speed) for instructions supported by the CPU.
From what I see it does use SSE2. My CPU is an AMD Opteron 165 (I keep it at stock for Linux) which does support SSE2 and SSE3. It doesn't have Virtualization though. :(

---

### Post by Hero of Time on 2008-03-13
Then check if the SSE2 is also available in the virtual machine. If it isn't, then you might have found the cause of the error.

An alternative to ripping dvd's is AnyDVD. It can copy the dvd to your hard drive and remove the protection from the dvd. You mention that you convert the dvd to divx, you might want to check [www.doom9.org](www.doom9.org) for other tools that can do the job.

---

### Post by GSZX1337 on 2008-03-13
> **Hero of Time said:**
> 
An alternative to ripping dvd's is AnyDVD. It can copy the dvd to your hard drive and remove the protection from the dvd. 

Lol, I have that software (and most of the other software available from that company) and didn't think of that!

---

