---
title: "Any UEFI Issues Dual-Booting Linux?"
date: 2014-06-07
forum: Ubuntu, Linux and OS Chat
---

### Post by Kurt_Alan on 2014-06-07
[SIZE=5][/SIZE]****


I'm prepping my next Linux Box purchase, probably from thinkpenguin.com  I have a choice between BIOS and UEFI on the mb.  Of course, BIOS would be the safest route.  But because I'm a glutton for punishment and want to keep up with the evolution of BIOS < UEFI, I'm choosing the latter.  I have done general background reading but I have no experience with UEFI.

You don't have to read too many posts to find lots of issues with dual-booting Windows and Ubuntu, but that's not my concern.

Are there ANY issues/concerns with dual-booting Ubuntu and Ubuntu?  I am choosing Ubuntu 14.04 LTS and Xubuntu 14.04 LTS, since I have sweet spots both for Unity and Xcfe.

Any issues with changing boot sequence to recognize external drives? And Secure Boot?  I know Ubuntu supports UEFI and therefore Secure Boot but does this depend on the mb manufacturer? Leave Secure Boot on or off? 

I've installed hundreds of OS's on BIOS based mb's. In the case of UEFI is this a no-brainer or is there some tutorial I need to read?

---

### Post by kurt18947 on 2014-06-07
Look for posts by Old Fred.  He's the BIOS/UEFI/GPT guru here.  I did discover that just because a machine has a UEFI BIOS, it may not require wholesale changes -- or at least mine didn't.  I just plugged a MSDOS formatted SATA disk with Ubuntu 14.04 installed and working. I turned the new machine on and it just worked. The M.B. BIOS recognized the install and automatically switched to compatibility mode (or whatever it's called). I did remember to deactivate PPAs and proprietary video drivers before removing from the old machine.   I also learned that I'd have had to install 64 bit Windows 7 to use UEFI/GPT which I prefer to not do for compatibility reasons.  It appears that UEFI setups are nowhere near as mature and standardized as BIOS so can vary a good bit from manufacturer to manufacturer.

---

### Post by Copper Bezel on 2014-06-08
On my particular machine (an Asus Vivobook,) UEFI and Secure Boot haven't caused me any problems, and dual-booting with Windows 8 wasn't any more difficult than it's ever been while I bothered with it. I did disable Secure Boot before installing and later adjust Grub to support it, then turn it back on, but I don't think I needed to do any of that. But my understanding is that, yes, while Ubuntu should work with Secure Boot on any system, UEFI itself varies between motherboards and can cause issues. I still think it'd be best to go the UEFI route, though.

---

### Post by oldfred on 2014-06-08
UEFI issues seem to vary immensely by vendor. Some modify UEFI to only boot Windows, but there are work arounds for most of those.
Currently UEFI for standard computers offers CSM.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

A few new systems are set for 32bit only and use a custom 32bit UEFI as another way to lock you into Windows. And no Linux offers a 32 bit UEFI, but there is a thread were someone recompiled  a lot and seemed to make it work.

And there are locked down systems, mostly tablets but maybe a few crossover type tablet/computers. The have no CSM and only boot installed system.

And some of the new locked down systems have no CSM mode or the UEFI type 3. I expect in a few years all systems will eliminate the extra CSM chip and just be UEFI, but will dual boot only in UEFI mode.

Links to lots of the UEFI info in my signature.

---

### Post by RichardET on 2014-06-09
> **Kurt_Alan said:**
> 


I'm prepping my next Linux Box purchase, probably from thinkpenguin.com  I have a choice between BIOS and UEFI on the mb.  Of course, BIOS would be the safest route.  But because I'm a glutton for punishment and want to keep up with the evolution of BIOS < UEFI, I'm choosing the latter.  I have done general background reading but I have no experience with UEFI.

You don't have to read too many posts to find lots of issues with dual-booting Windows and Ubuntu, but that's not my concern.

Are there ANY issues/concerns with dual-booting Ubuntu and Ubuntu?  I am choosing Ubuntu 14.04 LTS and Xubuntu 14.04 LTS, since I have sweet spots both for Unity and Xcfe.

Any issues with changing boot sequence to recognize external drives? And Secure Boot?  I know Ubuntu supports UEFI and therefore Secure Boot but does this depend on the mb manufacturer? Leave Secure Boot on or off? 

I've installed hundreds of OS's on BIOS based mb's. In the case of UEFI is this a no-brainer or is there some tutorial I need to read?

I have three Lenovo laptops, all bought since 2010, all with UEFI;  none have any problems with openSUSE or Ubuntu 64 bit booting with UEFI.
In Lenovo machines, you can turn off UEFI, if desired.

---

### Post by kurt18947 on 2014-06-09
> **oldfred said:**
> UEFI issues seem to vary immensely by vendor. Some modify UEFI to only boot Windows, but there are work arounds for most of those.
Currently UEFI for standard computers offers CSM.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

**A few new systems are set for 32bit only and use a custom 32bit UEFI as another way to lock you into Windows. And no Linux offers a 32 bit UEFI, but there is a thread were someone recompiled  a lot and seemed to make it work.**

And there are locked down systems, mostly tablets but maybe a few crossover type tablet/computers. The have no CSM and only boot installed system.

And some of the new locked down systems have no CSM mode or the UEFI type 3. I expect in a few years all systems will eliminate the extra CSM chip and just be UEFI, but will dual boot only in UEFI mode.

Links to lots of the UEFI info in my signature.

I wonder what they were promised to implement *that*?  I thought that only 64 bit Windows install using UEFI, guess not huh?  I expect you're right about CSM going away down the road particularly on systems that are intended to be sold with Windows pre-installed.

---

### Post by monkeybrain20122 on 2014-06-09
> **oldfred said:**
> 
A few new systems are set for 32bit only and use a custom 32bit UEFI as another way to lock you into Windows. And no Linux offers a 32 bit UEFI, but there is a thread were someone recompiled  a lot and seemed to make it work.


Linux kernel 3.15 (just released two days ago) supports running 64-bit kernel on 32-bit UEFI.
[http://www.phoronix.com/scan.php?page=news_item&px=MTcwOTY](http://www.phoronix.com/scan.php?page=news_item&px=MTcwOTY)

In the meantime I see no reason to use UEFI if legacy/CSM mode is available. None whatever.

---

### Post by LastDino on 2014-06-09
If you're going to buy UEFI, I would make background check of that particular Mobo and google lot for its ability to support Linux before even thinking of buying it. While UEFI itself is not a problem, some manufacturers have went out of their way to use this to make their Hardware only windows compatible.

I've never tried GPT with Legacy, but if GPT requires you to use UEFI, then that's probably the only reason I would actually pick UEFI over legacy. Otherwise, I concur with monekybrains comment.

---

### Post by sammiev on 2014-06-09
> **monkeybrain20122 said:**
> Linux kernel 3.15 (just released two days ago) supports running 64-bit kernel on 32-bit UEFI.
[http://www.phoronix.com/scan.php?page=news_item&px=MTcwOTY](http://www.phoronix.com/scan.php?page=news_item&px=MTcwOTY)

In the meantime I see no reason to use UEFI if legacy/CSM mode is available. None whatever.

+1

---

### Post by grahammechanical on 2014-06-10
> [COLOR=#000000]Are there ANY issues/concerns with dual-booting Ubuntu and Ubuntu? I am choosing Ubuntu 14.04 LTS and Xubuntu 14.04 LTS, since I have sweet spots both for Unity and Xcfe.[/COLOR]

On that particular subject the answer is, none as far as I am concerned. I have several installations of Ubuntu and it flavours. The thing to remember is that the last Linux to be installed will put its Grub into the MBR/UEFI boot system and it will be at the top of the list. Also when an installation receives a kernel upgrade the Grub configuration file is re-written and so the last install to receive the kernel upgrade will take over the Grub boot menu.

So, we get into a situation where we expect Grub to boot a certain Ubuntu and it boots the other one instead. The solution is to boot into the Ubuntu/Xubuntu that we want to be the automatic choice and run

```
sudo update-grub
```
sudo grub-install /dev/sda[/code]

Another thing we can do is to put a background image to Grub. A different background image for each installation. Then when the Grub background image changes we know that the other installation has taken control of the Grub menu.

Regards.

---

### Post by kurt18947 on 2014-06-10
> **monkeybrain20122 said:**
> Linux kernel 3.15 (just released two days ago) supports running 64-bit kernel on 32-bit UEFI.
[http://www.phoronix.com/scan.php?page=news_item&px=MTcwOTY](http://www.phoronix.com/scan.php?page=news_item&px=MTcwOTY)

In the meantime I see no reason to use UEFI if legacy/CSM mode is available. None whatever.

The only reason that comes to my mind would be if you wanted more than 4 primary partitions for whatever reason. I'm assuming the 4 primary partition limitation is present in the CSM module.  I normally use a 3rd party boot manager (BootItNG from terabyteunlimited).  It did not work with a new MoBo with UEFI/CSM.  GRUB is fine.  It seems we need to know which manufacturers are using crippled/perverted UEFI implementations.

---

### Post by oldfred on 2014-06-10
Ubuntu boots in BIOS/CSM mode with gpt partitioning. You just have to have a 1 or 2MB unformatted bios_grub partition. My BIOS system had booted from gpt drives since 10.10 Maverick.

And if system is UEFI capable and your drive is not going to have Windows in BIOS mode,  as MBR is required, I suggest gpt partitioning with both an efi partition at beginning of drive for UEFI or future UEFI boot and a bios_grub partition for BIOS boot. Then you have flexibility to boot or change later. The efi partition is not large compared to most new hard drives and can be 100 to 300MB FAT32 with boot flag. If you add boot flag it will try to boot in UEFI mode, so leave boot flag off if only want CSM/BIOS boot.

---

### Post by monkeybrain20122 on 2014-06-10
> **kurt18947 said:**
> The only reason that comes to my mind would be if you wanted more than 4 primary partitions for whatever reason. I'm assuming the 4 primary partition limitation is present in the CSM module.  I normally use a 3rd party boot manager (BootItNG from terabyteunlimited).  It did not work with a new MoBo with UEFI/CSM.  GRUB is fine.  It seems we need to know which manufacturers are using crippled/perverted UEFI implementations.

Why do you need more than 4 primary partitions? With an extended partition I can boot as many Linux OSes as I can handle.

---

### Post by RichardET on 2014-06-10
> **monkeybrain20122 said:**
> Why do you need more than 4 primary partitions? With an extended partition I can boot as many Linux OSes as I can handle.

How many can you boot simultaneously?  :)

---

### Post by monkeybrain20122 on 2014-06-10
> **RichardET said:**
> How many can you boot simultaneously?  :)

What do you mean 'booting sumulatenously'? I can easily multi-boot 4 or 5 Linux OSes with an extended partition. Managing is just so much more flexible than using gpt. I can change the partition layout, add/delete logical partitions easily and selectively clone the OS I need to move/backup etc and restore. You can't do that kind of things with gpt, it only allows cloning the whole drive with inflexible tools like clonezilla and strictly for backup only.

For all that I have only one primary partition which is about 20G as / for Ubuntu which also controls grub.

---

