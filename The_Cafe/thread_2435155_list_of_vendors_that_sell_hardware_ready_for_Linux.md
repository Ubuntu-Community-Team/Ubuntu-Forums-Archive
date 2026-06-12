---
title: "list of vendors that sell hardware ready for Linux"
date: 2020-01-16
forum: The Cafe
---

### Post by Skaperen on 2020-01-16
of course i know of System 76.  i have 2 of their products which i remain happy with.  but their current offerings don't encompass my anticipated scope of coming needs.  so, i am looking around for more hardware vendors that have offerings they ensure will work with at least Ubuntu.  please limit URLs to those that provide a list, instead of linking to the vendors directly.

---

### Post by oldfred on 2020-01-16
If they are now supporting UEFI update from Linux, then that is a major step to full support.
[https://fwupd.org/vendorlist](https://fwupd.org/vendorlist)
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)
[https://github.com/rhboot/fwupdate/blob/master/README.md](https://github.com/rhboot/fwupdate/blob/master/README.md)

---

### Post by CatKiller on 2020-01-17
[Project Sputnik](https://www.dell.com/support/article/uk/en/ukbsdt1/sln310507/ubuntu-based-developer-and-engineering-systems-project-sputnik?lang=en)

---

### Post by tea for one on 2020-01-17
Is this list any help for you?

[https://linuxpreloaded.com/](https://linuxpreloaded.com/)

---

### Post by mastablasta on 2020-01-20
i agree that uefi update from linux is one of the main issues here. if not from linux then at least something like freedos or similar free OS should be offered.

otherwise we have a bunch of HP Linux certified PC and laptops here with no OS preloaded or with freedos. they used to sell some with SUSE, but not anymore.

some Acers come with linpus linux preloaded, but i am sure that distro is quite limited in scope. and often full fledged distro has issues to install.

Some Asus laptops here come preloaded with endlessOS. would these work well if we replaced endless with Ubuntu?

Dell offers Ubuntu support.
Some gaming Lenovo's come with Ubuntu preloaded or with no OS loaded. i checked and looks like they work well with linux.

as for desktop PC - the motherboard is the main issue. MSI looks well, Asus looks descent. i am sure there are others (Gigabyte and Asrock for example) but not all motherboards are equally well supported.

---

### Post by Skaperen on 2020-01-20
they need to work even if i re-install the latest (as of 2020-05 or later) LTS version of Xubuntu over what is pre-loaded (adding drivers is OK as long as they are not needed for disk, basic VGA, and ethernet).  UEFI needs to be not deployed, able to be disabled, worked around, or resolved enough so the live/install image and a re-installed system can boot up.  their highest end models must work this way.

---

### Post by CatKiller on 2020-01-21
> **Skaperen said:**
> UEFI needs to be not deployed, able to be disabled, worked around, or resolved enough so the live/install image and a re-installed system can boot up.  

If you aren't using UEFI then you're doing it wrong.

BIOS was an ancient pile of kludges, weirdness, and undocumented behaviour. No machine uses it now. They're all UEFI, which can be made to *emulate* those kludges, that weirdness, and that undocumented behaviour.

---

### Post by mastablasta on 2020-01-21
probably it is not mean UEFI but windows "secure boot". UEFI is a standard dating back to 2003 or sometime around then. it was first supported by Linux. windows added support for it later one. the issue is secure boot and sometimes fastboot. both should have disable option in UEFI.

issue 2 is updating UEFI. for some reason manufacturers decided you need windows to do that. this is ridiculous. why can't freeDOS do it for example? or at least windows restore /repair disk.

---

### Post by CatKiller on 2020-01-21
> **mastablasta said:**
> issue 2 is updating UEFI. for some reason manufacturers decided you need windows to do that. this is ridiculous.

Generally, you don't, even if the manufacturer gives instructions for Windows users. UEFI can update itself; it doesn't need an external application. Just feed it the file on a thumb drive.

---

### Post by mastablasta on 2020-01-21
oh so UEFI has it's own OS so to say. i only ever updated in BIOS and for that i used a DOS/windows floppy disk. i remember i had to update it to do an upgrade with a special adapter form Pentium 2 400 Mhz to Celeron with 1,6 Ghz. massive upgrade, interesting adapter solution, but needed BIOS update. i also flashed BIOS and then updated as i was having issues with RAM. but then i solved it by "upgrade" to windows XP. that was way back in 2003 or 2004.  and in all cases DOS formatted floppy was needed. first to boot into OS and then to run the .exe file that then performed the BIOS upgrade.

---

### Post by CatKiller on 2020-01-21
It doesn't have its own OS, but it can run applications and have a shell. The bootloader and firmware setup are both UEFI applications, for example.

BIOS was reverse-engineered and then extended in all sorts of opaque and proprietary ways, and making any implementation work *well* didn't sell new systems; being able to more-or-less launch DOS and, later, Windows was the only thing that was tested for.

By contrast, UEFI is actually a defined standard, and has explicit support for multiple operating systems and different architectures; it's no longer based on the limitations of the 8080.

It's not perfect - Microsoft's wishes play too strong a role in the defaults that are commercially viable, for example - but it's a whole lot better than what came before.

Being able to update the firmware from within the firmware - or from a button press to launch the firmware updater - has been standard for a long time. That behaviour only tends to not be there if the manufacturer has gone to the effort to take it out - tightly integrated platforms like laptops where the manufacturer prefers obsolescence to easy serviceability, for example.

There's also [Coreboot](https://en.wikipedia.org/wiki/Core boot) as an alternative to either.

We're getting off topic from OP's wish for computers with explicit Linux support from the manufacturer, so I'll point out that the Intel NUCs have that. There was also a Kubuntu laptop released recently.

---

### Post by Skaperen on 2020-01-22
> **CatKiller said:**
> If you aren't using UEFI then you're doing it wrong.

i really don't care.  my current laptop is 6 years old and it works.  it's from System76 and i'd buy from them, again, if they had an offering that meets my needs.

> **CatKiller said:**
> BIOS was an ancient pile of kludges, weirdness, and undocumented behaviour. No machine uses it now. They're all UEFI, which can be made to *emulate* those kludges, that weirdness, and that undocumented behaviour.

if they *all* use it then _why bring up the issue_, unless there is (still) a problem booting up a Linux kernel, including one you compile from your own (possibly modified) copy of the kernel source code?  you tell me.  can you build a Linux system from pure source code and boot it up on a UEFI system?  if i take the latest Ubuntu or Xubuntu ISO hybrid image, dd it (i have my own tool that does this without flooding page cache so it doesn't cause the system to waste time swapping other stuff out and back in) to a USB memory stick device, which boots just fine on this laptop, and boot it on one of today's *all-are-UEFI* computers?

---

### Post by Skaperen on 2020-01-22
and what about an old copy of Ubuntu 9.10 i found laying around the other day?  it was the copy i install Ubuntu for my father when he got too upset with all the pop-ups he kept getting in Microsoft Windows.  he used that laptop until we had to put him in a nursing home a few years ago, just before he passed away.  someone else in the family got that laptop and i have no idea what it runs now.

---

### Post by CatKiller on 2020-01-22
> **Skaperen said:**
> if they *all* use it then _why bring up the issue_, unless there is (still) a problem booting up a Linux kernel, including one you compile from your own (possibly modified) copy of the kernel source code?

You brought it up. 

Of course you can compile a kernel and boot it from UEFI. How exactly do you think everyone's computers work?

---

### Post by mastablasta on 2020-01-22
the confusion is caused because people think uefi and windows "secure boot" are one and they same. they are not. UEFI enabled the windows to have the "secure boot" function implemented. however, per UEFI standard, this function should be optional. some did not follow the standards.

UEFI on the other hand is upgraded BIOS.

more on UEFI: [https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

> [FONT=sans-serif]The [/FONT][Linux kernel]("https://en.wikipedia.org/wiki/Linux_kernel")[FONT=sans-serif] has been able to use EFI at boot time since early 2000,[/FONT][SUP][[88]]("https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#cite_note-89")[/SUP][FONT=sans-serif] using the [/FONT][elilo]("https://en.wikipedia.org/wiki/Elilo")[FONT=sans-serif] EFI boot loader or, more recently, EFI versions of [/FONT][GRUB]("https://en.wikipedia.org/wiki/GNU_GRUB")[FONT=sans-serif].[/FONT][SUP][[89]]("https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#cite_note-debiangrubexample-90")[/SUP][FONT=sans-serif] Grub+Linux also supports booting from a GUID partition table without UEFI.[/FONT][SUP][[17]]("https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#cite_note-grub-bios-installation-17")[/SUP][FONT=sans-serif] The distribution [/FONT][Ubuntu]("https://en.wikipedia.org/wiki/Ubuntu_(operating_system)")[FONT=sans-serif] added support for UEFI secure boot as of version 12.10.[/FONT][SUP][[90]]("https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#cite_note-h-ubuntusecureboot-91")[/SUP][FONT=sans-serif] Further, the Linux kernel can be compiled with the option to run as an EFI bootloader on its own through the EFI bootstub feature.[/FONT]

windows on the other hand was able to boot from EFI about 2 years later :
> 
[LIST]
[*]The [Itanium]("https://en.wikipedia.org/wiki/Itanium") versions of [Windows 2000]("https://en.wikipedia.org/wiki/Windows_2000") (Advanced Server Limited Edition and Datacenter Server Limited Edition) implemented EFI 1.10 in 2002. MS [Windows Server 2003]("https://en.wikipedia.org/wiki/Windows_Server_2003") for [IA-64]("https://en.wikipedia.org/wiki/IA-64"), MS [Windows XP 64-bit Edition]("https://en.wikipedia.org/wiki/Windows_XP_64-bit_Edition") and [Windows 2000]("https://en.wikipedia.org/wiki/Windows_2000") Advanced Server Limited Edition, all of which are for the Intel [Itanium]("https://en.wikipedia.org/wiki/Itanium") family of processors, implement EFI, a requirement of the platform through the [DIG64]("https://en.wikipedia.org/wiki/DIG64") specification.[SUP][[93]]("https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#cite_note-94")[/SUP]
[*]Microsoft introduced UEFI for x86-64 Windows operating systems with [Windows Server 2008 R2]("https://en.wikipedia.org/wiki/Windows_Server_2008_R2") and [Windows 7]("https://en.wikipedia.org/wiki/Windows_7"). The 64-bit versions of [Windows 7]("https://en.wikipedia.org/wiki/Windows_7") are compatible with EFI.[SUP][*[citation needed]("https://en.wikipedia.org/wiki/Wikipedia:Citation_needed")*][/SUP] 32-bit UEFI was originally not supported since vendors did not have any interest in producing native 32-bit UEFI firmware because of the mainstream status of [64-bit computing]("https://en.wikipedia.org/wiki/64-bit_computing").[SUP][[94]]("https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#cite_note-WindowsVistaUEFI-95")[/SUP] [Windows 8]("https://en.wikipedia.org/wiki/Windows_8") includes further optimizations for UEFI systems, including a faster startup, 32-bit UEFI support, and secure boot support
[/LIST]


---

### Post by Skaperen on 2020-01-22
> **CatKiller said:**
> Just feed it the file on a thumb drive.in ext4 file system format?

---

### Post by CatKiller on 2020-01-22
> **Skaperen said:**
> in ext4 file system format?

FAT is part of the specification.

---

### Post by Skaperen on 2020-01-22
> **CatKiller said:**
> Of course you can compile a kernel and boot it from UEFI. How exactly do you think everyone's computers work?

maybe they were using some special bootloader.  based on what i read about UEFI it was going to check if what it loaded was signed with a certificate that was signed by whoever it trusted and that this would be doable for major distros.  then i quit reading about UEFI.

---

### Post by Skaperen on 2020-01-22
> **CatKiller said:**
> You brought it up.

not me.  looking back, i see that _oldfred_ did.

is UEFI no longer a barrier to booting unsigned systems?

---

### Post by Skaperen on 2020-01-22
will any PC with compatible USB and/or storage devices boot up any Linux bootloader and kernel at least as far as getting the kernel to start?

i have found a laptop that meets my needs (128GB RAM) but it is made by a company with a record of Linux incompatibility.

---

### Post by CatKiller on 2020-01-22
> **Skaperen said:**
> ls UEFI no longer a barrier to booting unsigned systems?

It never was. 

Secure Boot, which is a feature that UEFI has that BIOS didn't, allows the motherboard to prevent the loading of software that isn't signed with keys that the motherboard knows about. Because of market realities, all motherboards ship knowing about Microsoft's keys. You can turn Secure Boot off.

Additionally, Canonical and Red Hat had *their* keys signed using Microsoft's key, so every motherboard that knows about Microsoft's key (ie, all of them) can use Secure Boot out of the box with that software without any trouble at all. You can also tell the motherboard about any other key you're interested in - known as "enrolling a Machine Owner's Key" - and sign whatever software you want to.

This is orthogonal to UEFI itself: UEFI is simply better than BIOS in every way, even though it's not perfect. If you don't want to use Secure Boot, you can just turn it off, and if you do want to use Secure Boot it's only marginally fiddly to use with any software you want to.

---

### Post by Skaperen on 2020-01-22
> **CatKiller said:**
> It never was. 

apparently, a lot of people didn't know that.  the word that spread was different.  too bad i quit listening to the topic before that got cleared up.  i do remember saying in a couple places that it needs to be able to be turned off.  no one ever answered that.

> **CatKiller said:**
> You can turn Secure Boot off.

too bad people didn't say that when the issue blew up.  maybe there was just too much noise.

> **CatKiller said:**
> Additionally, Canonical and Red Hat had *their* keys signed using Microsoft's key, so every motherboard that knows about Microsoft's key (ie, all of them) can use Secure Boot out of the box with that software without any trouble at all. You can also tell the motherboard about any other key you're interested in - known as "enrolling a Machine Owner's Key" - and sign whatever software you want to.

is Microsoft a Secure Boot CA or does the spec force chained signing?  if the latter, how deep?

> **CatKiller said:**
> UEFI is simply better than BIOS in every way, even though it's not perfect.

since you are saying that, maybe you can give a sweet summary of how UEFI is simply better.  we'll have number 1 as:  Secure Boot which can be turned off or have owner keys added.

---

### Post by oldfred on 2020-01-22
UEFI also uses gpt partitioning as its standard. Windows only installs in UEFI mode to gpt drives.
Ubuntu will install in UEFI mode to MBR partitioned drives, but probably should not.
I have used gpt with BIOS boot on my old system also.

From the Link in my signature below:
UEFI [https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)
ESP/efi -  Efi System Partition  [http://en.wikipedia.org/wiki/EFI_System_partition](http://en.wikipedia.org/wiki/EFI_System_partition)
[https://en.wikipedia.org/wiki/BIOS_boot_partition](https://en.wikipedia.org/wiki/BIOS_boot_partition)
BIOS - Basic Input/Output System [http://en.wikipedia.org/wiki/BIOS](http://en.wikipedia.org/wiki/BIOS)
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.
grub2 [https://wiki.archlinux.org/index.php/GRUB2](https://wiki.archlinux.org/index.php/GRUB2)
gpt(GUID) [http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
MBR(msdos) [http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

Now older, I have posted multiple times.
Torvalds clarifies Linux's Windows 8 Secure Boot position
[http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/](http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/)
 the whole UEFI thing is more about control than security

Info on signing keys
[https://wiki.ubuntu.com/SecurityTeam/SecureBoot](https://wiki.ubuntu.com/SecurityTeam/SecureBoot)
[https://bbs.archlinux.org/viewtopic.php?id=191056](https://bbs.archlinux.org/viewtopic.php?id=191056)

UEFI is a standard, but not all vendors fully comply with it.
After you have read this, you can explain UEFI to us. :)
New UEFI Specification, Version 2.8
[https://www.businesswire.com/news/home/20190604005069/en/Industry-Standard-Firmware-Takes-Step-New-UEFI-Forum](https://www.businesswire.com/news/home/20190604005069/en/Industry-Standard-Firmware-Takes-Step-New-UEFI-Forum)
2500 page spec
[https://uefi.org/sites/default/files/resources/UEFI_Spec_2_8_final.pdf](https://uefi.org/sites/default/files/resources/UEFI_Spec_2_8_final.pdf)

---

### Post by CatKiller on 2020-01-22
> **Skaperen said:**
> since you are saying that, maybe you can give a sweet summary of how UEFI is simply better.  we'll have number 1 as:  Secure Boot which can be turned off or have owner keys added.
I already did, earlier in the thread. 

Your number 1 is broadly neutral; if you *want* Secure Boot to restrict the ability of unauthorised software to run then having it is a definite plus. If you don't want it then being able to turn it off is no improvement over BIOS, which can't do it anyway.

Being an actual standard rather than a bunch of secret add-ons to a reverse-engineered proprietary implementation is the big draw. You can actually have expected behaviour and compliance tests for how you interact with it.

Being platform independent is another big plus. Writing good firmware is *hard*, and anything that makes that easier, with code reuse and the like, makes implementations better for everyone.

Having multiple bootloaders intended from the beginning is much better than the fairly hacky bootloader chaining, which is pretty fragile. 

Not strictly part of the UEFI spec, but going along with it, is GPT partitioning that doesn't have the annoying four primary partition limit that MBR has. Extended partitions are another weird hack that got bolted on to the old way of doing things. You can also have much larger partitions, as well as more of them, with GPT. 

BIOS can only be run in 16-bit mode and is limited to 1 MB of addressable memory. There's not a lot you can do within that. UEFI can run in 32-bit or 64-bit modes.

Drivers are easier to write, since you've got a standardised interface to work from. 

Because FAT is part of the specification, non-Microsoft OSes get to use that without being locked out of things like SD cards, which also use FAT. If something's going to be made essential, having a standard behind it is very useful. 

UEFI is able to run its own network stack, so you can do things like OS-independent remote monitoring and management. BIOS only understands networking at all if the network card has an "option ROM" to tell it what to do, and it has to unload that when it hands control to an OS otherwise networking stops working.

Being able to have the firmware setup at a high resolution with lots of colours rather than being restricted to low-resolution text mode is a nice-to-have: the manufacturer can have their own branding if they want, and the end user can get a whole lot more information about what each setting is for.

Being able to boot straight into the firmware setup from an OS is awesome. Being able to change firmware settings from within an OS I'd actually class as a negative; the idea of Windows being able to change things there gives me chills. 

We've already covered how doing firmware updates without an external application to write to specific flash ROM addresses makes that part easier. You can also load firmware for attached hardware on the fly because you've got a standardised interface. That makes things like fwupd possible.

For more than this you'd probably be best off reading the [specifications](https://uefi.org/specifications) yourself.

---

### Post by CatKiller on 2020-01-23
Back on topic:

> **Skaperen said:**
> i have found a laptop that meets my needs (128GB RAM) but it is made by a company with a record of Linux incompatibility.

Buying from a company with poor linux support sends a market signal that you don't care about good linux support. Whether you're more interested in the hardware than the support, and will fix any issues that arise yourself, is a question that only you can decide.

---

### Post by oldfred on 2020-01-23
I am anti-laptop. 
I guess I like sweeping the sea back with broom as everyone is now using laptops.
And you you really need portability, then a laptop is a choice. But a tiny pad type device (that may not even run Linux) may be more portable.

I find laptops to not be ergonomic.
The screen is too small, and two low when on table or desk. 
Keyboard then is too high.
At minimum with laptop you have to also buy keyboard, mouse & larger screen and use those when not traveling.

While they always say performance is now the same as a desktop, that is not true. 
Heat is a major issue and they cannot be as cool. They typically use lower power processors to limit heat output.

I prefer to build my own desktop. 
Then I can select the components I want. And can often upgrade any component that I want.

---

### Post by Skaperen on 2020-01-23
i also find laptops to not be ergonomic.  until a few years ago i, also built my own desktops.  i generally built about as much power as i could reliably air cool.  i always used the highest quality ball-bearing fans and added flaps to avoid them becoming a big hole if they did fail.  the light-weight flaps made it easy to see that the fans were operating.

now days, building a computer is out of the range of my ability.  a laptop fits well where i can put it.  i have been trying to think how i might use one of those big extra-wide monitors with a smaller computer in the space in am limited to using it.  it should be easy to go up to a 60+ cm monitor since the base size is the issue.  there are a huge range of keyboard choices that can waste less space.

i don't use the laptop's mouse pad.  i use a cheap ($10 from Amazon) wireless mouse (VicTsing) with USB receiver.  1x AA.  it goes to sleep after 10 minutes of non-use (click any button to wake it up).  the only issue i have with it is the middle button is integrated with the roller.  if it wears out i just buy another one.  if it lasts a year, that's an OK price.

i need some huge RAM for one of my applications.  with 16GB RAM i have now, i can't give it a full data set.  i am thinking of either buying a server for it (it only needs one core) or running it in the cloud somewhere.  then i won't need so much RAM here.  it only needs to be run occasionally (twice a week for about an hour) so the cloud option seems very reasonable.

---

### Post by mastablasta on 2020-01-24
> **Skaperen said:**
> 
now days, building a computer is out of the range of my ability.  a laptop fits well where i can put it.  i have been trying to think how i might use one of those big extra-wide monitors with a smaller computer in the space in am limited to using it.  it should be easy to go up to a 60+ cm monitor since the base size is the issue.  there are a huge range of keyboard choices that can waste less space.


what is different now? it took me 6 hours to get it to boot, but this was because the instructions were written wrongly. after i removed all and then started from scratch it went really fast.

rather than laptop i was checking the ITX machines. if you need something with more power, intel nuc has a nice gaming version. it's small, no fans, yet very powerful with AMD radeon GPU. in the end i still decided for a standard desktop due to price and also upgrade options (can fit a lot more drives in this box).

---

### Post by mastablasta on 2020-01-24
> **oldfred said:**
> I am anti-laptop. 
I guess I like sweeping the sea back with broom as everyone is now using laptops.
And you you really need portability, then a laptop is a choice. But a tiny pad type device (that may not even run Linux) may be more portable.

I find laptops to not be ergonomic.
The screen is too small, and two low when on table or desk. 
Keyboard then is too high.
At minimum with laptop you have to also buy keyboard, mouse & larger screen and use those when not traveling.

While they always say performance is now the same as a desktop, that is not true. 
Heat is a major issue and they cannot be as cool. They typically use lower power processors to limit heat output.

I prefer to build my own desktop. 
Then I can select the components I want. And can often upgrade any component that I want.

that's how we use it at work (with the dock). i couldn't use it every day as laptop. i type a lot and keyboard ergonomics are really quite bad on laptops.
the business ones are relatively upgradeable. but upgrades are expensive. for example just the price of sata connection cable is 10x as much as from the one for desktop.

---

### Post by Skaperen on 2020-01-27
i don't really need more CPU power.  i need more RAM and faster RAM.  i may need more than 64GB.  SSD will help a lot, but that is readily available.  i only need 1TB of storage but can make use of more.  a platform other than a laptop will be very difficult for me right now due to various limitations.  the ergonomics of a laptop are not an issue for me (i am using a 16GB one right now).  my need for the RAM is not immediate, but is anticipated over the expected time of using my next machine.  i'm hoping to get that next machine sometime before the end of 2020.

---

### Post by Skaperen on 2020-01-28
i'm trying to get a sense of possible PC brands to get.  or i may just go with having some small vendor build it under my guidance for parts (did that with my last server and it worked out great).  i'd like to get feedback of computer buying experience where some models just can't run Linux, out of the box.  that means the instali/live image won't boot/run or what it installs won't boot/run without some changes like adding a driver.  brands that make these i want to strike off my list, even if everything else works with Linux (unless they specifically label which work with Linux in their marketing).

---

### Post by mastablasta on 2020-01-28
system76 will put together something per your specs. you need power in a small box (work station laptop). the only issue is motherbaord and GPU. if you use intel or AMD GPU they shouldn't be a problem.

but even Dells most expensive workstation uses 2666 Mhz RAM. and max is usually 64GB. there is lenovo thinkpad p52: [http://blog.lenovo.com/en/blog/the-new-thinkpad-p52/](http://blog.lenovo.com/en/blog/the-new-thinkpad-p52/)

the problem with laptops is heating up or rather small confined space. if i had some calculation to do that didn't need GPU i would just setup a headless server and jam it with multiple processors, added ECC RAM modules and SSD drivers. many companies offer server machines that include better components than consumer modes (at a higher cost). they all support linux out of the box.

also bear in mind that the stronger the CPU and GPU the shorter the battery life :)

---

### Post by Skaperen on 2020-01-28
and the more RAM the shorter the battery life.  i'm sure that faster RAM does so, too, as well as more ram channels.  these things can also result in a lighter weight wallet.

---

### Post by CatKiller on 2020-01-28
> **Skaperen said:**
> and the more RAM the shorter the battery life.  i'm sure that faster RAM does so, too, as well as more ram channels.  these things can also result in a lighter weight wallet.

Kind of. More pressingly, the low-power memory specification LPDDR doesn't always have the larger modules and higher speeds available that the DDR specification can use. The two specifications are limited by the same technological levels, but are developed in parallel.

Using a laptop for its form factor to access another machine elsewhere that contains lots of RAM for those tasks that require it will be a lot easier to source, and probably considerably cheaper, than trying to stuff it all into that laptop form factor.

---

### Post by Skaperen on 2020-01-29
> **CatKiller said:**
> Using a laptop for its form factor to access another machine elsewhere that contains lots of RAM for those tasks that require it will be a lot easier to source, and probably considerably cheaper, than trying to stuff it all into that laptop form factor.

right.  that's what i'm looking at cloud costs for.  paying for a big 16 core machine for the time i need to run this using only 1 core might well be worth it, depending on how often i need it ... compared to owning that much hardware.  getting it out of here is a plus since i really don't have a good place for a server.  the house design i made never got built and now never will.  it had a utility room that had its own cooling and space for servers.

---

### Post by EuclideanCoffee on 2020-02-14
I know a lot of users throw around System76. I was a desktop system administrator for ~20 System76 PCs. The machines rarely broke down, but the driver support was infuriating with the older models. Their fans are loud. I had bought a System76 model myself, and eventually it stopped working. I've replaced every single component on the board. And their lack of support for older models with firmware annoys me. We've moved to Dell Latitude laptops and find them to work much better; however, if you want better support for Nvidia on your laptop, go with System76. Buying a "engineering" laptop is a waste of time from Dell, especially for Ubuntu.

I would like to try Purism and Think Penguin.

Actually, Think Penguin appears to sell what galp3 is on their store. [https://www.thinkpenguin.com/gnu-linux/penguin-j3-gnulinux-laptop](https://www.thinkpenguin.com/gnu-linux/penguin-j3-gnulinux-laptop)

But I've found that HP AMD computers and Dell Latitudes work the best for Ubuntu.

---

### Post by Skaperen on 2020-02-14
still, i need lots of RAM.  i periodically login as many as 20 virtual users at the same time.  i usually have 10 of them logged in.  currently i have 17 (a few are idle).  this is on 16GB and 4GB of swap is used and it gets sluggish sometimes (even affecting the mouse pointer).  i want to get 32 GB absolute minimum and considering 64GB.  if i were to get a desktop, i might even go for 128GB.

---

### Post by CatKiller on 2020-02-15
> **Skaperen said:**
> if i were to get a desktop, i might even go for 128GB.

With Epyc you could have 2 TB of RAM. Bit pricey, though.

---

### Post by him610 on 2020-02-15
> **oldfred said:**
> 
I find laptops to not be ergonomic.
The screen is too small, and two low when on table or desk. 
....
I prefer to build my own desktop. 
Then I can select the components I want. And can often upgrade any component that I want.
Agree mostly with OldFred's sentiments. I have had a few personal laptops in the past, had a few issued by employers. My spouse uses a System76 purchased a few years ago. Laptops are kind of handy to use as a travel machine; I switched over to using a Chromebook when traveling a few years ago; however, I don't travel much anymore. I use it when we go to Wegman's while I wait for my spouse to shop. Going to the casino down in West Virginia tomorrow, will take my Chromebook with me.

---

### Post by mastablasta on 2020-02-17
> **Skaperen said:**
> still, i need lots of RAM.  i periodically login as many as 20 virtual users at the same time.  i usually have 10 of them logged in.  currently i have 17 (a few are idle).  this is on 16GB and 4GB of swap is used and it gets sluggish sometimes (even affecting the mouse pointer).  i want to get 32 GB absolute minimum and considering 64GB.  if i were to get a desktop, i might even go for 128GB.


then you would probably benefit from RAM being as fast as possible. If you go with desktop it shouldn't be an issue.  

we had a guy giving presentation on an ERP enhancement and they used a small ITX machine. not sure was it one of those small imacs or something else (intel NUC?!). anyway they had Ubuntu on it with various virtual machines running concurrently and then the used that to give the presentation, tutoring and demos. along that they had a small laptop to connect to it and where the power point presentation was. the whole setup was very small. and  i guess i would just add a keyboard to it. or one of those small ones you can hold in one hand. the NUCs support 64 GB ram: [https://www.intel.com/content/www/us/en/support/articles/000055527/intel-nuc.html](https://www.intel.com/content/www/us/en/support/articles/000055527/intel-nuc.html)

the do run Ubuntu out out of the box. So if portability is an issuse this could also be a solution. hard to suggest sinc ewe don't know exactly what is being needed here. otherwise desktops have no issue supporting 64GB or 128 GB.

---

### Post by Skaperen on 2020-02-17
a desktop would make having plenty of RAM easy.  but i have a personal situation that makes having a desktop very hard to do.

---

### Post by lammert-nijhof on 2020-04-19
I use a desktop every day, it is always powered on and it suspends automatically. I have a laptop for two reasons:
- To have a computer when I go to Europe visiting family;
- As weekly backup for my desktop. 

For daily use, I agree completely with OldFred.
I find laptops to not be ergonomic.
The screen is too small, and two low when on table or desk. 
Keyboard then is too high.
At minimum with laptop you have to also buy mouse.
The CPU is always inferior, lower wattage and thus lower frequency
Laptops are more expensive.

As a consequence I have a $350 new desktop from May 2019 with:
- Ryzen 3 2200G and 16GB, runs Ubuntu 20.04 minimal install
- 512 GB nvme-SSD (3400/3000 MB/s);
- two old HDDs 500 GB and 1 TB;
to be upgraded in 2021/22 with e.g. a 4200G or 5200G or a faster APU.
 
and a HP Elitebook 8460p laptop from Dec 2011, bought 2nd-hand in May 2017 for $270 with 
- an i5-2520M and 8 GB ($200) runs Ubuntu Mate 20.04, somewhat more efficient with memory.
- 1 TB SSHD (new $70);
- to be upgraded in 2020 to 16 GB and maybe a 4-core Sandy Bridge i7.

My desktop is new and only 30% more expensive, while running at least 2 or 3 times as fast, 2268 vs 6762 passmarks and 12 vs 25 seconds boot time.
I even used a desktop, when living in a 1 bedroom hostel for 8 month.

---

