---
title: "AMD vs Intel"
date: 2009-10-18
forum: Virtualisation
---

### Post by corsakh on 2009-10-18
Sup guys,

I want to upgrade my computer to be able to run Windows XP under VB. My current Athlon X2 4800+ with 3Gb RAM is a little too slow on Windows part. Linux flies. Which processors would you recommend? Do those "vritualization" technologies from Intel and AMD do much of a difference? How much RAM would you recommend? Windows use is pretty intense, its gonna run some flash animation and a couple of programs most of the time.

---

### Post by jocampo on 2009-10-18
> **corsakh said:**
> Sup guys,

I want to upgrade my computer to be able to run Windows XP under VB. My current Athlon X2 4800+ with 3Gb RAM is a little too slow on Windows part. Linux flies. Which processors would you recommend? Do those "vritualization" technologies from Intel and AMD do much of a difference? How much RAM would you recommend? Windows use is pretty intense, its gonna run some flash animation and a couple of programs most of the time.

Hi

some people believe that upgrading the CPU to one with with virtualization built-in support they will fix their problems but don't go too fast. For CPU upgrades you must check this 1st.


-Did you check how much could cost you a brand new laptop or PC with a AMD or Intel processor with virtualization support?
-Does your current motherboard support virtualization?

I just recently bought a Compaq laptop with AMD processor and built-in virtualization and paid under $400 with taxes. I used to have a Dell Inspiron. So, check prices, upgrading your CPU could cost you more especially if you are gonna use your old and slow disk.

Regarding differences between AMD and Intel, I have not see anyone. What is more important is the kind of WIndows you are using. Do not expect take full advantage of Virtualization if you are not using a 64bit or your motherboad simply does not offer the feature.

Between 3 and 4GB of RAM should be more than enough to run a couple of VMs, say 2 or 3, with no issues. It also depends of what you are running inside the VM. I usually run Oracle and MS-SQL so need about 3GB min  for the host and about 1GB for the VM.

---

### Post by mgol on 2009-10-18
> **jocampo said:**
> Regarding differences between AMD and Intel, I have not see anyone.
Actually, there are some important differences:

1)Intel ships both CPUs with and withiut VT-x, they use having VT-x as an extra feature that costs additional money. AMD-V is present in all modern AMD CPUs.

2) Intel supports disabling VT-x via BIOS and - unfortunately - a lot of notebook sellers (Lenovo in IdeaPads, Sony in VAIO etc.) blocks those features. It looks much better on desktops, though. As far as I know, ADM doesn't allow to disable AMD-V.

3) All modern AMD CPUs support Nested Paging which increases virtualization performance (You can google it, AMD describes it plainly in a nice document); as for Intel, only Core i7 CPUs support Nested Paging (and these CPUs cost *a lot*). In fact, Intel calls it Extended Page Tables and it seems they have done it worse than AMD (at least that's what VMware authorities say).

---

### Post by corsakh on 2009-10-18
> **jocampo said:**
>  Regarding differences between AMD and Intel, I have not see anyone. What is more important is the kind of WIndows you are using. Do not expect take full advantage of Virtualization if you are not using a 64bit or your motherboad simply does not offer the feature.

Between 3 and 4GB of RAM should be more than enough to run a couple of VMs, say 2 or 3, with no issues. It also depends of what you are running inside the VM. I usually run Oracle and MS-SQL so need about 3GB min  for the host and about 1GB for the VM.

Oof.. lets take it slow :D

Are you saying that I need a 64bit host or that I need a 64bit host and a 64bit client? If I need a 64bit client, its a problem because 64bit XP is not particular stable as it is. I am not sure I want to know about its stability under VB :D

Second. Many people say that a modest machine with like 4GB RAM is enough to run XP fast in VB. Although Linux is flying, I can not say the same about the Windows XP part. Its pathetically slow.  When I simply drag "My computer" window around, CPU stays around 40% range. When I load a flash application it I can "see" the animation spike. And CPU load goes to 100%. When I play a youtube video, CPU stays around 40%.

Things I have noticed:

Normal XP with SP3 seems to work faster than TinyXP with SP2 for some reason - anyone has experience with TinyXP editions to confirm this?

Rdesktop + headless VB seem to work faster than standard VB interface.

Removing wallpaper in Windows for some strange reason made a big difference to performance.

It seems that installing guest addons actually decreases virtual system performance. Any one else experience this?

If someone has a fast XP running on Linux under VirtualBox on a modest machine like mine (Athlon x2 4800+, 3-4GB RAG), please share:

- what versions of OS you are running - 32 or 64 bits, and what SP packs
- what interface you are using - standard VirtualBox or running it in headless + rdesktop
- have you installed guest addons?
- does changing desktop preferences in Windows (wallpaper, screen size, color depth) have an impact on your systems performance?

Thank you.

---

### Post by mgol on 2009-10-18
> **corsakh said:**
> If someone has a fast XP running on Linux under VirtualBox on a modest machine like mine (Athlon x2 4800+, 3-4GB RAG), please share:

- what versions of OS you are running - 32 or 64 bits, and what SP packs
- what interface you are using - standard VirtualBox or running it in headless + rdesktop
- have you installed guest addons?
- does changing desktop preferences in Windows (wallpaper, screen size, color depth) have an impact on your systems performance?

Thank you.
My VBox runs quite OK (strange though, with Intel VT-x it runs much slower... maybe a VBox bug). I have Core2 Duo P8600 (see my signature).

I use 64-bit Karmic, standard VirtualBox interface. I installed Guest Addons - it's a must have! It not only installs a better integration system between host & guest but it also installs a guest graphics driver, so yes - this ***IS*** important.

It's strange it decreases Your performance. I'm pretty sure it can't be decent without GA, though. It's like installing Your old WinXP on a new machine without drivers. Sure, it'll run, all cards have VESA support, but it'll run at 1024x768 or even 800x600 and it will be **damn slow**.

---

### Post by corsakh on 2009-10-18
Sigh, found some information on line that TinyXP apparently has problems with running flash animation. Not sure if its true or not yet, gonna do some tests later.

And yep, I am positive that desktop settings play a big role in performance. At least when I run VB in headless + rdekstop. When I simply move an explorer window around my screen with no wallpaper set, CPU use around 30. When I do that with a large colorful wallpaper, CPU goes all the way to 100%.

---

### Post by maxxjr on 2009-10-19
> **corsakh said:**
> Sup guys,

I want to upgrade my computer to be able to run Windows XP under VB. My current Athlon X2 4800+ with 3Gb RAM is a little too slow on Windows part. Linux flies. Which processors would you recommend? Do those "vritualization" technologies from Intel and AMD do much of a difference? How much RAM would you recommend? Windows use is pretty intense, its gonna run some flash animation and a couple of programs most of the time.

A few notes...

1. Your AMD processor does include virtualization support.

2. I've always found that the best two speedups of windows, virtual or not, are a clean install and NO anti-virus.  I would recommend creating a VM with just the apps that you need, then immediately take a snapshot.  If you get a virus, or if windows "degrades" over time, as it can do, you can revert to the snapshot.  It feels like a whole new PC if you do a fresh install, and DON'T install AV.

3. Virtualbox has a performance bug with its IO APIC implemenation on AMD processors.  IO APIC is not required (but is optional) for one virtual CPU.  IO APCI is required for dual virtual CPU's.  My experience is that XP with 1 virtual CPU was substantially faster than dual virtual CPU's.  Virtualbox has since released updates that "improve" the issue, and I have not tested this.

4. If your RAM requirements are low enough for your Windows app, you can also disable the Page file.  

5. Is the Flash streamed over a network?  If so, I would guess network performance might have more of an impact on app performance than the CPU (but I'm not familiar with this kind of app).  Any active scanning that your antivirus or other utilities do on incoming network data would also impact performance.  Are you able to disable any scanning to see if the PC is better able to perform with the application?  The reason I ask these last questions, is that if your PC with native windows is having difficulties with the app at 2.5GHz, I don't know that you would see a substantial improvement with a virtual PC at 3+ GHz.  Being virtual will eat into some of that added performance from a newer CPU.

---

### Post by corsakh on 2009-10-19
Thanks for the tips, I removed IO Apic and enabled AMD virtualization, it works better now.

Regarding flash, I am not sure what is wrong. But its not network related.

---

### Post by pookiebear on 2009-10-20
> **maxxjr said:**
> A few notes...



2. I've always found that the best two speedups of windows, virtual or not, are a clean install and NO anti-virus.  I would recommend creating a VM with just the apps that you need, then immediately take a snapshot.  If you get a virus, or if windows "degrades" over time, as it can do, you can revert to the snapshot.  It feels like a whole new PC if you do a fresh install, and DON'T install AV.



IF you are going this route.  DONT load any service packs or updates either. IT WILL BE about 3 times faster without SP3 on it. Use a winxp with sp2 already embedded. It till be a lot faster. 
Just don't use it for surfing the net. Just use it for copying files and running your program that you needed the VM for.

---

### Post by jocampo on 2009-10-20
To corsakh

Yes, if you are gonna create a VM, it should be a 64bit virtual machine, otherwise, you will NOT take advantage of your processor capabilities.

To mgol

When I said differences I was talking about performance. I've tested and used both...my own laptop and at work, I have not seen drastic differences in term of performance. In terms of design and architecture, they are different, yes.

---

### Post by jocampo on 2009-10-20
> **mgol said:**
> 
2) Intel supports disabling VT-x via BIOS and - unfortunately - a lot of notebook sellers (Lenovo in IdeaPads, Sony in VAIO etc.) blocks those features. It looks much better on desktops, though. As far as I know, ADM doesn't allow to disable AMD-V.


It depends of the BIOS. Mine, a Compaq Presario CQ60 with AMD Athlon X2, you can disable/enable the VT-x/AMD-v in bios... in fact, comes disable from factory ...

---

### Post by corsakh on 2009-10-20
> **pookiebear said:**
> IF you are going this route.  DONT load any service packs or updates either. IT WILL BE about 3 times faster without SP3 on it. Use a winxp with sp2 already embedded. It till be a lot faster. 
Just don't use it for surfing the net. Just use it for copying files and running your program that you needed the VM for.
Is it ok if the program that I am using connects to the internet? Does not involve any WWW surfing though.

---

