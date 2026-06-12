---
title: "Would like some advice on using VirtualBox with current hardware..."
date: 2015-04-12
forum: Virtualisation
---

### Post by Mike_Walsh on 2015-04-12
Evening, all.

Mods:- I hope this is in the right place....if not, please re-locate: thanks!

--------------------------------------------------------------------------------------------

I've recently made a bunch of changes to my desktop hardware. I started using Linux about a year ago, with the installation of 'Trusty'. At the time I was running a single-core Athlon 64, a 3200+. I have 3 GB of RAM, and a 160GB WD Caviar 'Black'. The desktop is a Compaq Presario, circa 2005....about 10 yrs old. 

In recent weeks, the CPU has been uprated to an Athlon 64 X2 3800+ dual-core; basically, a pair of 3200+'s on the same die. The previously reliable onboard ATI Radeon graphics have finally been replaced with an nVidia graphics card, a GT 610; simply a basic replacement....I don't want it for gaming, or video-editing, or anything like that. And the ancient 300W Bestec PSU has been replaced with a CoolerMaster B500 ver2, with the revised single-rail output.

The RAM & HDD remain unchanged.

My question is this:- Although the 'new' CPU has improved responsiveness no end, do CPU's NEED to have VT (Virtualisation Technology) in the instruction set in order to run a VirtualBox install? I've also switched OS's to Xubuntu, having experimented with it during the last year, and realised that I really like it. I used to have VB in the Ubuntu install, but with the single-core Athlon (no 'VT'), it was 'sluggish', to say the least.

I'm merely wondering if there would be any point in installing VB in the new Xubuntu set-up? Any advice would be appreciated.


Regards,

Mike. :)

---

### Post by TheFu on 2015-04-12
For questions like this, use the source: [https://www.virtualbox.org/manual/ch10.html#hwvirt](https://www.virtualbox.org/manual/ch10.html#hwvirt)

I looked up the performance for that CPU - it is about half that of a C2D E6600, which is what I consider the min for acceptable virtualization performance.  So, it doesn't look good, but perhaps for server-only VMs, it would be fine?

---

### Post by coldraven on 2015-04-13
This five year old HP laptop has 2x Turion AMD running at 2GHz and 4GB RAM. It will run Windows XP in Vbox quite well. Or rather it used to run it, for some reason my backup copies won't finish loading at the moment. I don't use XP anymore so I'm not too bothered.
I did run Ubuntu server quite successfully for a while. For testing, you can get ready-made VBox images here: [http://virtualboxes.org/images/](http://virtualboxes.org/images/)
If you want to keep using one then don't forget to change the default password!

---

### Post by Mike_Walsh on 2015-04-13
Thanks for the replies, guys.

I'm well aware it's 10-yr old + tech, and as such probably not really suited to to the rigours of virtualisation..! To be honest, my 'distro-hopping' days are pretty well behind me; I've 'settled down' with the 'buntus & the 'Puppies. I'm 100% Linux these days; haven't had Windows in the house for nearly a year....don't really miss it, either.

I don't NEED to use a copy of Windows for any particular app or program; just exploring options. I'm extremely lucky that the few Windows apps I DO use will all run with acceptable functionality under Wine; out of the 4 that I use, three have the 'Platinum' rating and run perfectly (one of these was reviewed and rated BY me for the Wine HQ database), and one has the 'Gold'.....and runs well enough for what I require it to do. They're all graphic design apps...nothing particularly demanding. Some of the more exotic functions don't work THAT well, but since they're rarely accessed or needed, it's not a problem.

This was more of a fact-finding question than anything else; it's confirmed what I suspected. VT is not really an option with my current setup; which is what I wanted to know. Wine works for me.....so I'll stick with it.

Cheers!


Regards,

Mike. :)

---

### Post by GrouchyGaijin on 2015-04-13
For what it's worth here is my two cents:
If you are thinking of running Windows in the Virtual Machine I seriously doubt that 3 gigabytes of RAM will be enough.  I setup Windows 7 in a VM in order to use EndNote for my thesis.  I have 8 gigabytes of RAM on the host machine and was able to allocate 4 gigabytes to Windows.  That is enough for me to run Office and EndNote, however, just for grins I tried to run the hearts game that is bundled with Windows - it was unplayable the game was just too slow.

---

### Post by TheFu on 2015-04-13
> **GrouchyGaijin said:**
> For what it's worth here is my two cents:
If you are thinking of running Windows in the Virtual Machine I seriously doubt that 3 gigabytes of RAM will be enough.  I setup Windows 7 in a VM in order to use EndNote for my thesis.  I have 8 gigabytes of RAM on the host machine and was able to allocate 4 gigabytes to Windows.  That is enough for me to run Office and EndNote, however, just for grins I tried to run the hearts game that is bundled with Windows - it was unplayable the game was just too slow.

Odd. My Windows VM gets 1.5G of RAM, 1 vCPU and it runs great. It does Quicken, Quickbooks and 7MC recording (4 concurrent TV streams). It can only be accessed over RDP.  Windows does need a minimal amount of RAM, but like any VM, giving it too much RAM can actually make it slower, but it really depends on the workload.  I'm not running autoCAD here.

---

### Post by kurt18947 on 2015-04-13
This machine is an Athlon II X2 240. I have virtual box installed and virtualization enabled in the BIOS. I don't have Win7 installed, I do have MX14, a midweight linux distro installed there. It works very well, I haven't messed with getting it to run full screen. I've run WinXP in the past allocating 512 MB. RAM and it seemed to do well for basic tasks like office stuff, web browsing w/ flash.

---

### Post by Mike_Walsh on 2015-04-13
Hallo, Kurt.

I'm assuming this is yours...released in 2009, and it's the K10 architecture:-

[http://www.cpu-world.com/CPUs/K10/AMD-Athlon%20II%20X2%20240%20-%20ADX240OCK23GQ%20(ADX240OCGQBOX).html](http://www.cpu-world.com/CPUs/K10/AMD-Athlon%20II%20X2%20240%20-%20ADX240OCK23GQ%20(ADX240OCGQBOX).html)

This is mine: some years earlier (in fact the previous generation, K8), and released, I believe, in 2005. The biggest differences are not only the speed and size of the L2 cache, but also the fact of having the SSE4a instruction set.....and the all-important AMD-V (virtualization technology). Yours is considerably more suited to the job than mine is; but it's a case of what will work with the motherboard that I have.....and since funds are tight, it's also a case of doing what I can with what I've got:-

[http://www.cpu-world.com/CPUs/K8/AMD-Athlon%2064%20X2%203800%2B%20-%20ADA3800DAA5CD%20(ADA3800CDBOX).html](http://www.cpu-world.com/CPUs/K8/AMD-Athlon%2064%20X2%203800%2B%20-%20ADA3800DAA5CD%20(ADA3800CDBOX).html)

The differences are rather obvious..! Still, for £7 off eBay, I'm not complaining; it's transformed this old girl (and she wasn't a slug in the first place). Running the current set-up with a lightweight distro like Puppy, it flies. Xubuntu's pretty snappy, too!


Regards,

Mike. :)

---

### Post by GrouchyGaijin on 2015-04-13
> **TheFu said:**
> ... but like any VM, giving it too much RAM can actually make it slower, but it really depends on the workload.  I'm not running autoCAD here.
Really? I did not know that. Hmmm makes me wonder if I *decrease* the amount of RAM allocated to the VM if Windows 7 will run better?  It's worth a shot.

---

