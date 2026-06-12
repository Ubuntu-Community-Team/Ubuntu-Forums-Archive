---
title: "What virtualization software are you using? Poll"
date: 2007-10-24
forum: Virtualisation
---

### Post by djRob on 2007-10-24
I would like to ask you what virtualization software you are using and why you chose this virtualization software? I am interested in in full system virtualization (not Wine type emulators). 
How fast Windows programs run, what is sound support etc.? Please give your system specs.

I installed Vista in VMware server on Kubuntu Feisty i386 but programs ran slow on Intel Core 2 Duo 2Ghz.

---

### Post by prezbedard on 2007-10-24
None just yet. Thinking about m$ Virtual Server 2005 (I have a windows network).

---

### Post by godog on 2007-10-24
In feisty I had VMWare Server. Now I upgraded to Gutsy, VMWare won't load any VM and I can't reinstall it, Automatix doesn't have it anymore and I don't know what to do. Any Ideas?

---

### Post by Calash on 2007-10-24
With the most recent upgrade to VirtualBox all of my stability issues have dropped, so I am happily using that as my primary, with VMWare Server as a backup in-case I have issues.

The seamless windows feature, though still a bit buggy with compiz, is a nice touch and works quite well over all.

---

### Post by tribaal on 2007-10-24
VMware workstation (yes, I paid for it)

- trib'

---

### Post by jespdj on 2007-10-25
I tried VMWare Server on Feisty and now I am using VirtualBox on Gutsy.

I have just tested it with Windows XP as a guest OS and it looks like it works well, except for USB which is not working (VirtualBox gives me a warning that it doesn't have access to USB on the host, this is a known problem for which a solution is described in the help, I just haven't done it yet).

One thing I am wondering about: In VMWare I could choose how many processors I want in my virtual machine (I have a Core 2 Duo, so I could assign 1 or 2 processors). I don't see such an option in VirtualBox, and Windows XP thinks that there is only one processor. Is it possible to make both cores available to a virtual machine with VirtualBox?

Another problem is that my native screen resolution, 1280 x 800, is not listed in Windows XP and VirtualBox's solution for adding custom video modes does not work.

Seamless mode does not work well when you have Compiz enabled on your Ubuntu desktop; sometimes the entire desktop becomes black for a moment and things don't repaint properly. I haven't yet tried out if these problems disappear if I disable desktop effects.

---

### Post by gtdaqua on 2007-10-25
The free edition VMWare Server. Quite ok with it.

---

### Post by djRob on 2007-10-27
I played a little bit with VMWare server (free version) and VirtalBox lately. I like VMWare server more because:
- I could install Windows 98 in it,
- it didn't have any problems with networking like in VirtualBox.

---

### Post by stomponthis on 2007-10-28
Using Virtual Box on Gusty and am very happy with it :-)
Tried VM Ware as well and that worked fine for me with Fiesty.
I have had very minimal problems with both programs!

---

### Post by Shazaam on 2007-10-28
VMware Player.
I love it. I can thrash it to no end and it keeps on ticking. There IS one error message that I don't like. It's the one that says "Sorry you cannot install VMware on a virtual machine". :)

---

### Post by FredB on 2007-10-28
VMWare workstation - I'm thinking of buying a license of it. Why ? 64 bits guest os support which is not available in Virtualbox right now !

---

### Post by Tlon on 2007-10-28
A GREAT reason to run VMWare over any of the other options is simple standardization.  If you work in IT, then you'll get experience with what is, by far, the industry standard virtualization suite.  Moreover, VMWare has so many resources at hand, and so many industry partners and so much support, that I find it unlikely that any of these small-fish are going to keep pace very well.  I know that must seem like a funny argument coming from someone using mostly FOSS, but them's sort of the breaks.

---

### Post by jimmydean on 2008-01-25
I was using VMware server until I made some graphics changes to resolve video playback in Gutsy and now it won't load my native XP install (corporate XP image). I am looking at VirtualBox but it looks like I can't mount the XP install I have, so I might be stuck trying to resolve my VMware issues.

---

### Post by Anzan on 2008-01-26
I'm using VirtualBox now.

I had used VMware in Vista to run Ubuntu last year but as it's free but closed and I have no interest in closed software or OS after 20 years of it, VirtualBox ose seemed a good option.

There is nothing in Windows I'm interested in running as the only really necessary Windows programs are Spybot, AdAware, ClamAV, and CrapCleaner and I don't need them if I'm not running Windows.

So I'm just using VB to run different Linux and BSD distros.

And it's working out pretty well. VB's GUI is very clean and it's wizard is quite clear.

---

### Post by Tichondrius on 2008-01-27
VBox user here. Running guest Ubuntu 7/10 on windows-xp host, mostly used as a web and mail server 24/7. Using raw disk access for VM (400GB), which is INFINITELY better than using the silly virtual disk images ("differentiating" ?!) and their poor performance. My Ubuntu VM is running at close to native speed on my quad-core duo 4GB machine, and since Windows is the host, I can still play the latest games on the same machine (also using windows for web browsing and messaging, etc). As a server, it's a monster on my 20/1.5 mbps internet connection, capable of handling complex 3-tier web apps (currently running a few custom pylons apps, as well as wordpress, phpbb, gallery, trac, etc.).

---

### Post by dark_phantom on 2008-01-28
Running VirtualBox right now and so far I like it.  I also run VMware and I agree with Tlon, we run that at work.

---

### Post by fjgaude on 2008-01-28
VMware Server, the free one, works great and is fast if you only use one core or CPU. The next version should fix this bug.

I've used both VBox and VMware and I like the latter better for what I do.

---

### Post by dpj23 on 2008-01-29
VMware hands down is the best...  Hard core people will try and say they can match VMware right now...And while that statement is somewhat true...  None of the other providers are as polished as Vmware at the present moment...  

Maybe they will be someday...  That's what they are hoping for...  To have their product running in a enterprise environment.  Then a true comparison can be completed...   

I run:
ESX server
vmserver
vmworkstation
vmplayer

---

### Post by technotika on 2008-03-03
For me I had issues with printing  - so after "a lot of faffing" about I went for a virtualisation option to run my windows based printing application and newsleecher.

VMware had dreadful usb support - first of it wouldnt pick up usb. Then when I got it ready after faffing about it told me my usb ports were slow. Then it told me my printer malfunctioned and just wouldnt work.

Had a look for an alternative and found virtual box. I work in IT too and know that VMWARE is king but foor my little ubuntu experiment VB kicked the ar$e off VMWare; instant usb management, eveything working perfectly. No more headaches.

At the end of the day both good products and FREE so just trial and error and see what fits best for YOU!

---

### Post by ung/xunil on 2008-03-03
First I tried qemu, than I tested vmware and liked for its networking out-of-the-box (virtualbox was to be born yet). Than I tested virtualbox and like it too.

Than I notice that vmware had some security problems regularly, so I went deep to [qemu, dnsmasq and vde]("https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo") along with shorewall to make "real" safe and good networking for qemu - all free software, no "obscure" modules or networking.

I don't have a VT processor, so my options don't include Xen or KVM. I use qemu to have a "headless" virtual ubuntu server in my PC (I start qemu in a tty console with -nographics and access it with SSH) without any problems with my "normal" installation or long gnome sessions because I can logoff from Gnome without killing the server. Can even stop Gnome. Working great.

---

### Post by arkara on 2008-03-03
i voted for virtualbox because it is FREE LIKE BEER and because it is easy to use!

---

