---
title: "Had no choice but to go back to DELL OEM Windows 8!"
date: 2013-03-27
forum: Ubuntu Development Version
---

### Post by kevpan815 on 2013-03-27
Every Nightly Build of 13.04 has recently been Failing the DELL UEFI Security Check A.K.A. Secere Boot, and I refuse to Disable Dell UEFI Secure Boot just to run the Latest Nightly Build of Ubuntu, as I would be putting myself at a huge Security Risk if I were to get some kind of Virus/Malware that Targets Linux, Just FYI. I will return to Ubuntu Nightly Build Testing just as soon as Canonical fixes their Secure Boot Problem.

---

### Post by oldfred on 2013-03-28
One of Linus' rants on security.

 [http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/](http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/)
 the whole UEFI thing is more about control than security

---

### Post by cariboo on 2013-03-28
Why not run with the version you got installed, and help squash other bugs?

---

### Post by VinDSL on 2013-03-28
> **kevpan815 said:**
> [...] I refuse to Disable Dell UEFI Secure Boot just to run the Latest Nightly Build of Ubuntu, as I would be putting myself at a huge Security Risk if I were to get some kind of Virus/Malware that Targets Linux [...]
My understanding is, UEFI Secure Boot only improves boot-time security on Windows 8 machines.

How does it improve security on Linux machines :confused:

Er...

On second reading, are you saying that malware/viruses on dual-boot machines, infected with Windows 8, will target your Linux install?

---

### Post by kevpan815 on 2013-03-28
The Security Key was in here before! Why is it Gone Now? This Issue is Definitely NOT Fixed!

---

### Post by IanW on 2013-03-28
Not sure which repos I have enabled (posting from work), but Synaptic is reporting a UEFI signed kernel available.

See [http://packages.ubuntu.com/source/raring/linux-signed]("http://packages.ubuntu.com/source/raring/linux-signed")

---

### Post by kevpan815 on 2013-03-28
> **VinDSL said:**
> My understanding is, UEFI Secure Boot only improves boot-time security on Windows 8 machines.

How does it improve security on Linux machines :confused:

Er...

On second reading, are you saying that malware/viruses on dual-boot machines, infected with Windows 8, will target your Linux install?

VINDSL: There are some Viruses/Malware that target Linux! The recent Oracle Java Problem is one of them that can affect Linux!

---

### Post by kevpan815 on 2013-03-28
> **IanW said:**
> Not sure which repos I have enabled (posting from work), but Synaptic is reporting a UEFI signed kernel available.

See [http://packages.ubuntu.com/source/raring/linux-signed](http://packages.ubuntu.com/source/raring/linux-signed)

The UEFI Security Check started Failing on me sometime right around the time that Ubuntu Kernel 3.8.0.14 came out (either sometime last week or the week before).

---

### Post by rrnbtter on 2013-03-28
Greetings,
It goes without saying that one should not be using a testing version of Linux unless they are willing to accept unexpected consequences.  If you are dual booting Win8, using Raring is not the best decision.  I'm betting that when you come back it will be to the next testing version. You seem like that kind of guy.  No real tester will ever be happy with the anything called "stable". Isn't that why you are posting in this part of the forum in the first place?

---

### Post by kevpan815 on 2013-03-28
Well the CDIMAGE Download Server is down right now so I can't come back at the moment.

---

### Post by buzzingrobot on 2013-03-28
> **kevpan815 said:**
> VINDSL: There are some Viruses/Malware that target Linux! The recent Oracle Java Problem is one of them that can affect Linux!

That's not a boot-time attack, which is the only thing Secure Boot is intended to protect you from. 

Secure Boot, on Windows or any OS, is not a magic panacea that protects you from any and all attacks.

---

### Post by ronacc on 2013-03-28
this image is available in synaptic . linux-signed-image-3.8.0-14-generic . but I don't see a daily that says it has that kernel . 

rant !  another MS attempt to kill off linux .

---

### Post by ronacc on 2013-03-28
I just had an idea , try making a usb stick with a persistence file and installing that kernel to it . I don't know if that would work , I don't have anything with a uefi bios to try it on .

---

### Post by mc4man on 2013-03-28
> **ronacc said:**
> this image is available in synaptic . linux-signed-image-3.8.0-14-generic . but I don't see a daily that says it has that kernel . 

In raring-desktop-amd64, ck. the manifest, not in raring-desktop-i386

---

### Post by kevpan815 on 2013-03-28
Right now I am having trouble getting the Download Links on the CDIMAGE Download Server to work from within OEM Windows 8! The only Security Software that I have installed is Avast 8.0.1483 Premier Edition and Malware Bytes Anti-Malware 1.75 Beta. The Download Links at Releases.Ubuntu.com work just fine however anything older than 13.04 does NOT work on my system as this is a 2013 Dell System Model and the Ubuntu Kernel's in 12.04.2 and 12.10 are too old to work on this system.

---

### Post by kevpan815 on 2013-03-28
P.S. I should also mention that this is the PRO Edition of Malware Bytes Anti-Malware 1.75 Beta so it may be Blocking Access to the CDIMAGE Download Server I will try Disabling it and Avast and see if the Download works or NOT.

---

### Post by mc4man on 2013-03-28
> **kevpan815 said:**
> Right now I am having trouble getting the Download Links on the CDIMAGE Download Server to work from within OEM Windows 8.
try again, if still issue then it's on your end, server is just fine atm & reasonably fast

---

### Post by ronacc on 2013-03-28
I'm sure this is what MS had in mind when they pushed the OEM's into using UEFI  . I fear we will have endless grief out of it . Fortunately there are  still non UEFI mobo's available and I build my own boxes so I can dodge the bullet .

---

### Post by oldfred on 2013-03-28
The issue is not UEFI, that is just a new (actually better in many ways) way to boot. It does away with MBR and allows many systems to all have a boot loader in the efi partition to make multi-boot easier. It also does away with interrupts and how hardware communicates with system. Everything is then driver based not interrupts and all the age old issues with interrupts.

The issue is secure boot and how Microsoft has implemented secure boot. 

The few Windows 7 systems that used UEFI made installs relatively easy. No issues of 4 primary partitions as UEFI uses gpt partitioning.

Users have installed to Dells with UEFI, but better support is coming with each new kernel update and improvements to grub2 efi:

       Installing Ubuntu 12.10 x64 on Dell XPS 13 Alongside Windows from USB New user with Details post 10
[http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450)

            HOWTO Ubuntu 12.10 x64 Dell XPS 14 (UEFI + Intel Rapid Start Technology + Flashcache), bumblebee - Details
[http://ubuntuforums.org/showthread.php?t=2117166](http://ubuntuforums.org/showthread.php?t=2117166)

    
In the future we will be able to add our own keys (still  $100?) but will need the very newest kernel to do that.
 UEFI generic shim - Secure Boot bootloader
[http://mjg59.dreamwidth.org/20303.html](http://mjg59.dreamwidth.org/20303.html)
Matthew Garrett's Blog
[http://mjg59.dreamwidth.org/](http://mjg59.dreamwidth.org/)
New Linux UEFI boot loader - hash based no key
[http://mjg59.dreamwidth.org/23113.html](http://mjg59.dreamwidth.org/23113.html)

---

### Post by ronacc on 2013-03-28
that may be fine for the major distros  lie Ubutntu , Suse and Redhat who can afford the ransom but what about the niche or small distros that are on a shoestring but still very worthwhile efforts ?

---

### Post by oldfred on 2013-03-28
It is a $100 once to get a new key, not $100 per system. 

But the new Linux LF loader uses hashes and Matthew Garrett says he plans to merge his shim with the Microsoft key, that Ubuntu & Redhat currently use with the LF loader version that uses hash. But that requires the next version of the kernel and release of all the changes to grub. Will not be in 13.04.

---

### Post by ronacc on 2013-03-28
I tried to install the signed kernel on a live usb stick , it wouldn't configure and resulted in an unbootable stick so I guess that option is out  .

---

### Post by buzzingrobot on 2013-03-28
Microsoft bashing works better when it's informed, not paranoid.

It's rational for Microsoft to want to verify that Windows hasn't been subject to a boot-time attack. Contrary to what Torvalds seems to have said, it's rational for Linux to do the same.

It's the fact that Windows controls the market that influences a handful of OEM's to ignore the requirements of the secure boot standard and push out hardware that can only boot the version of Windows that was pre-installed on it because they broke the user's ability to disable secure boot and to use his own keys.  They can get away with it because the market has no incentive to care about Linux users.

If the situation was reversed, if Linux controlled 90 percent of the market, the same scenario would be playing out, tilted in Linux' favor.

It's the incessant focus on the evils (real and imaginary) of Microsoft, and the mirror-image cheerleading assertions that Linux is always right and always best about everything,  that often gets in the way of doing something smart.  

(On the cost issue:  No one in the Linux community has stood up and said, "We will issues keys. We will verify the requesters." For free or for a fee, or otherwise.)

---

### Post by VinDSL on 2013-03-28
> **buzzingrobot said:**
> No one in the Linux community has stood up [...]
I think the lawyers/courts are going to [decide this one]("http://www.techweekeurope.co.uk/news/linux-users-in-spain-file-an-official-complaint-against-microsoft-111512").  ;)

---

### Post by ronacc on 2013-03-28
My MS bashing IS informed from watching their lies and dirty tricks since DOS was their only product .

---

### Post by ventrical on 2013-03-28
> **VinDSL said:**
> I think the lawyers/courts are going to [decide this one]("http://www.techweekeurope.co.uk/news/linux-users-in-spain-file-an-official-complaint-against-microsoft-111512").  ;)

Nice read Vin. Thanks..

---

### Post by kevpan815 on 2013-03-28
> **mc4man said:**
> try again, if still issue then it's on your end, server is just fine atm & reasonably fast
I am getting an HTTP 404 Page NOT Found from within MSIE 10.0 on DELL OEM Windows 8! Any Ideas?

---

### Post by kevpan815 on 2013-03-28
Same 404 Page NOT Found in Apple Safari 5.1.7 for Windows!

---

### Post by kevpan815 on 2013-03-28
By the way, I have tried 12.04.2 on this system and it does NOT work at all! Have NOT yet tried 12.10 but I am NOT sure it will work either Because 12.10 is actually Older then 12.04.2 and they both now come with the Same 3.5.X Kernel, just to let you guys know.

---

### Post by kevpan815 on 2013-03-28
Tried to Download with Both Mozilla Firefox Nightly Build (X64 22.0 Alpha 1 for Windows) and Mozilla SeaMonkey Nightly Build (X86 2.19 Alpha 1 for Windows ) same 404 Page NOT Found Error on CDIMAGE Download Server. Releases Download Server works just fine so the Problem is NOT on my END. All other Websites work just fine. Just FYI.

---

### Post by rrnbtter on 2013-03-28
Greetings,
I don't dual boot but everything that I know about this process is that with Win8, dual boot or even with just Ubuntu you will need a UEFI enabled kernel on a Secure Boot machine even if you are only booting Ubuntu, and probably even if you have Secure Boot turned off. That means Kernel 3.8 or newer. There does exist reported machine specific quirks that the Kernel Devs will have to address on an individual basis. There are many posts in this section that suggest not testing on a Primary Box. I personally choose to ignore that suggestion but I don't mind a reinstall, its cheaper than a movie, popcorn and drink.

---

### Post by kevpan815 on 2013-03-28
> **rrnbtter said:**
> Greetings,
I don't dual boot but everything that I know about this process is that with Win8, dual boot or even with just Ubuntu you will need a UEFI enabled kernel on a Secure Boot machine even if you are only booting Ubuntu, and probably even if you have Secure Boot turned off. That means Kernel 3.8 or newer. There does exist reported machine specific quirks that the Kernel Devs will have to address on an individual basis. There are many posts in this section that suggest not testing on a Primary Box. I personally choose to ignore that suggestion but I don't mind a reinstall, its cheaper than a movie, popcorn and drink.

That was exactly my point when I said that 12.04.2 LTS does NOT work on my 2013 Dell Inspiron 15 3521 PC, the Machine needs 13.04 to work, and right now I am having trouble downloading 13.04 Nightly from [http://cdimage.ubuntu.com/daily-live/current](http://cdimage.ubuntu.com/daily-live/current) AND [http://cdimage.ubuntu.com/daily-live/pending](http://cdimage.ubuntu.com/daily-live/pending) (404 Page NOT Found Error when I click on the AMD 64 Download Link)!

---

### Post by cariboo on 2013-03-28
Just out of curiosity, have you tried zsyncing the last iso that worked for you? BTW both of the links you posted work for me.

---

### Post by mc4man on 2013-03-28
> **kevpan815 said:**
> That was exactly my point when I said that 12.04.2 LTS does NOT work on my 2013 Dell Inspiron 15 3521 PC, the Machine needs 13.04 to work, and right now I am having trouble downloading 13.04 Nightly from [http://cdimage.ubuntu.com/daily-live/current](http://cdimage.ubuntu.com/daily-live/current) AND [http://cdimage.ubuntu.com/daily-live/pending](http://cdimage.ubuntu.com/daily-live/pending) (404 Page NOT Found Error when I click on the AMD 64 Download Link)!

Where are you clicking on, at top of page or on the actual file/iso name below. Use the one below, as in screen (raring-desktop-amd64.iso

---

### Post by ping-wu on 2013-03-28
[QUOTE=kevpan815;12578282]That was exactly my point when I said that 12.04.2 LTS does NOT work on my 2013 Dell Inspiron 15 3521 PC, <snip>

Ubuntu 12.04.2LTS works with a UEFI machine, but you need the 64-bit version as I have not found any machine with 32-bit UEFI firmware.  All the Windows 8 notebooks have 64-bit UEFI firmware.

One way to run a 32-bit Ubuntu (or any other distro that is not UEFI-enabled) is to install it in a non-UEFI machine, then copy the image to a target machine.  Some adjustments are required which involve editing (i.e., changing to appropriate UUIDs) the /boot/grub/grub.cfg and /etc/fstab files, but it is not too difficult.

Of course you can turn on the (BIOS) compatible mode, then you can install the 32-bit version of Ubuntu.  But you will lose the ability to dual-boot into Windows 8.

---

### Post by kevpan815 on 2013-03-28
> **mc4man said:**
> Where are you clicking on, at top of page or on the actual file/iso name below. Use the one below, as in screen (raring-desktop-amd64.iso

Thank You, mc4man, your solution worked, it looks like the Download Links at the Top of the Page are Broken Today, i will get this Downloaded A.S.A.P. and let you guys know if Today's Build Passes or Fails Secere Boot.

---

### Post by EgoGratis on 2013-03-28
> **kevpan815 said:**
> Every Nightly Build of 13.04 has recently been Failing the DELL UEFI Security Check A.K.A. Secere Boot, and I refuse to Disable Dell UEFI Secure Boot just to run the Latest Nightly Build of Ubuntu, as I would be putting myself at a huge Security Risk if I were to get some kind of Virus/Malware that Targets Linux, Just FYI. I will return to Ubuntu Nightly Build Testing just as soon as Canonical fixes their Secure Boot Problem.

Just to set things straight.

>  ... as I would be putting myself at a huge Security Risk if I were to get some kind of Virus/Malware that Targets Linux, Just FYI.

This does not hold water because you would be putting yourself "at a huge Security Risk" if you were to get some kind of Virus/Malware that Targets **Windows** (boot process), Just FYI. 

If you were to get some kind of Virus/Malware that Targets Linux (or Windows) on Ubuntu it would not help much because only boot process is signed ("therefore immune") and after that loading Ubuntu there isn't much that is signed ATM and i hope it won't be for a while because i don't like lock-in to just USC for example and not to be able to install .deb package from the internet. And if you are not doing this and only use USC i do imagine the risk is not high to get something you would not like from USC.

P.S. If you are afraid to use Ubuntu you probably should stop doing it and just use Windows and the apps available from Microsoft store and that is it and that will give you decent security but it's still possible you would get something you would not like because i can assure you UEFI+SB didn't make Windows "bullet proof" and immune to all security risk out there it might just slightly made it harder for some of it.

---

### Post by kevpan815 on 2013-03-28
Today's AMD64 Proposed Build Passed Secure Boot! Problem Solved! By the way I did NOT say that I was trying to download X86 Ubuntu. I said that I was trying to use X86 Mozilla SeaMonkey for Windows (Mozilla does NOT make an X64 Build of SeaMonkey for Windows, AND Mac, ONLY Linux is X64 for Mozilla SeaMonkey) to download AMD 64 Ubuntu 13.04 Proposed. Just FYI.

---

