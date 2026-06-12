---
title: "Impending Doom"
date: 2022-05-05
forum: The Cafe
---

### Post by Shibblet on 2022-05-05
Are Linux users the only people who sees the impending doom coming on the horizon?

Microsoft has been slowly changing their OS over the past few years, and are finally making one of the most difficult steps.  i.e. ["How to Boil a Frog."]("https://en.wikipedia.org/wiki/Boiling_frog")

This particular step is going to be quite a hike in temperature.  

Anyone can sell the need for a faster processor, HD Resolution, and/or UEFI Bios. Those are simple.

The TPM 2.0 Chip is entirely for Microsoft to control and monitor your computer.
They can, at this point, require any software loaded, to be specifically from the Microsoft Store.
And because Mac OS, iOS, Linux, Android, and ChromeOS are available, they are not considered a monopoly.  However, they do truly control most of the computers out there.

I'd be willing to bet that within the next 5 years, all computers will be data mining as part of some required update for Windows...

---

### Post by grahammechanical on 2022-05-05
> The TPM 2.0 Chip is entirely for Microsoft to control and monitor your computer.
They can, at this point, require any software loaded, to be specifically from the Microsoft Store.

If that proves to be correct it will likely mean that it will be impossible to install a dual boot with Linux on machines pre-installed with Windows. People said similar things years ago when they first heard about Secure Boot. But Microsoft allowed Linux boot binaries to be verified and be given a Microsoft signed key that was registered in the machine's secure boot database. I believe that Canonical played a part in fixing up that arrangement. Perhaps Canonical will make a similar approach regarding TPMs.

Microsoft documentation says this:

> Before it can be used for advanced scenarios, however, a TPM must be  provisioned. Starting with Windows 10, the operating system  automatically initializes and takes ownership of the TPM. That means  that IT professionals should not have to configure or monitor the  system.

[https://docs.microsoft.com/en-us/windows-hardware/design/device-experiences/oem-tpm](https://docs.microsoft.com/en-us/windows-hardware/design/device-experiences/oem-tpm)

Who makes these chips? A supplier who purchases machines and then installs Ubuntu on them should not have a problem unless Windows has been previously installed on the hardware. If the chip manufacturer is willing to provide the data it might be possible for Ubuntu to be modified to do the provisioning. Then we could have a situation where a OEM supplied machine with Ubuntu pre-installed could block Windows from being installed on it. But I do not think that Canonical would do something like that.

Regards

---

### Post by DuckHook on 2022-05-05
In my opinion, the danger that you cite is very real.

20 years ago, few would have thought that Google and Facebook would grow into multi&#8209;trillion dollar monsters whose market value is almost entirely predicated on their ability to completely strip&#8209;mine our data. There were a few futurists prescient enough to warn us, but they suffered the fate of Cassandra.

Considering also MS's history of avarice and amorality and there is every reason to expect the worst.

I'm not willing to take your bet.

The big question remains: what to do about it?

---

### Post by Tadaen_Sylvermane on 2022-05-06
I think it's a danger. I also think that this danger is eye of the beholder. Not everyone is as paranoid about security nor do they need to be. I don't personally care much myself. Everyone has different things that matter to them. To the average user a computer is nothing more than a tool. If they can get their work / email / games done then so be it. They don't much care how it works as long as it does work. Ignorance is bliss.

Linux people naturally have a curiosity that leads us to care more about this stuff. My choice isn't ignorance as much as I just don't care. It's quite irrelevant to me because everything can be compromised and nothing is truly safe and I accept that. Just because it's Linux doesn't mean a damn thing. I think it's the nature of a global networked world. As long as people have an interest in screwing other people over then it won't change. I don't lose sleep over it. At the end of the day if you can't afford for it to be seen it shouldn't be on any network capable device.

> [COLOR=#000000]But Microsoft allowed Linux boot binaries to be verified and be given a Microsoft signed key that was registered in the machine's secure boot database[/COLOR][COLOR=#000000]

Thankfully they don't control hardware and there is plenty of companies and people out there doing open source hardware designs that aren't locked into this crap. Pay a bit more but that is the world we live in.[/COLOR]

---

### Post by DuckHook on 2022-05-06
> **Tadaen_Sylvermane said:**
> …I don't lose sleep over it. At the end of the day if you can't afford for it to be seen it shouldn't be on any network capable device.
You are right of course. If we start losing sleep over it, then for all intents and purposes, we will already have lost. No one should feel so despondent that we succumb to despair or inertia. We do have some power over what data we surrender and Linux has its part to play in that.
> Thankfully they don't control hardware and there is plenty of companies and people out there doing open source hardware designs that aren't locked into this crap. Pay a bit more but that is the world we live in.
Right again. It may even give OEMs like System76, Pine and Purism a good shot in the arm. You give me hope. Much appreciated.

---

### Post by grahammechanical on 2022-05-06
> [COLOR=#000000]there  is plenty of companies and people out there doing open source hardware  designs that aren't locked into this crap. Pay a bit more but that is  the world we live in.[/COLOR]

These independent companies are not necessarily more expensive. Go to a big name brand and they will charge you a fortune because their idea of a Linux user is a Linux programer. So, they offer High end developer machines with a corresponding high price. But there are other companies that provide Linux machines (including Ubuntu) for a reasonable price and they are not low specified either. If you are an ordinary user and not fooled by the Developer Edition expensive trap then search OMGUbuntu. That is what I did when I wanted a Linux/Ubuntu laptop. 

Consider this offering for innovation.

[https://frame.work/gb/en](https://frame.work/gb/en)

Getting back on topic, here is a link with information as to which motherboards already have a TPM

[https://www.digitaltrends.com/computing/motherboards-that-support-tpm-windows-11/](https://www.digitaltrends.com/computing/motherboards-that-support-tpm-windows-11/)

Note the links to AMD and Intel CPUs. Our defenses have already been infiltrated.

Regards

---

### Post by TheFu on 2022-05-06
TPM is recommended by the Linux Foundation along with secure boot to have the most secure Linux workstation. 
[https://www.linux.com/news/how-choose-best-linux-distro-sysadmin-workstation-security/](https://www.linux.com/news/how-choose-best-linux-distro-sysadmin-workstation-security/)

TPM is a standard, not a MS-specific thing.

Virtual machines have virtual TPM capabilities. They aren't perfectly implemented yet, but getting better. Win11 forcing TPM will solve that for the rest of us too.

MSFT started their surveillance years ago, when they initially released the Win10 beta and changed the EULA for Win8 and Win7.  That's when I stopped updating all Windows computers at home and dropped MS-Windows from consideration as an OS for the future.  Not everyone can or cares to make that decision.   

Remember the BSA?  They still exist and visit companies looking for license problems. BSA is mainly a MSFT group and companies that use volume licensing agree to this oversight in their contract. In 2004, one CEO/Owner was made enough after a visit disrupted his business to tell his IT people to replace all Windows software - and they did:  [https://blog.jdpfu.com/2011/01/20/how-to-limit-microsoft-licenses-in-small-biz](https://blog.jdpfu.com/2011/01/20/how-to-limit-microsoft-licenses-in-small-biz)

In 2015, I said that MSFT was firing all their customers. [https://blog.jdpfu.com/2015/09/08/microsoft-is-firing-their-customers](https://blog.jdpfu.com/2015/09/08/microsoft-is-firing-their-customers)

And don't forget that "cloud computing is careless computing." [https://www.networkworld.com/article/2228050/cloud-computing-is-careless-computing-and-chromeos-pushes-people-into-it-says-open.html](https://www.networkworld.com/article/2228050/cloud-computing-is-careless-computing-and-chromeos-pushes-people-into-it-says-open.html)

---

### Post by forrestcupp on 2022-05-06
I haven't been able to use Linux for a lot of years because of specialized software that I regularly use. But I was exclusively on Linux (mostly Ubuntu) for several years, starting with the second release of Ubuntu (Hoary Hedgehog). The only point I want to bring up is that people were making these same predictions 15 years ago. They were angry that Microsoft was working to stamp them out and predicting impending doom even back then.

But it never happened! From my perspective, the opposite has happened. Linux has done nothing but advance. Gaming in Linux is much better than it used to be. Hardware support is ever advancing. And other than the TPM 2.0 thing (which screwed a lot of Windows users over, too), Microsoft seems to have actually become more friendly to Linux over the years.

Microsoft is supporting Win10 for several more years for the people who don't have TPM 2.0 hardware. And it's definitely not in their best interest to force everyone to only buy software from their store. In fact, they've shown the opposite of that with their actions. That became obvious when they decided to also sell their games on Steam, as well as their own store.

Linux users have always been the "little guy" from a market share perspective. And with that comes a paranoia that everything is going to fall out from under them. But take it from a guy who hasn't been in the middle of the emotion of it, your fears of impending doom are unfounded. Microsoft isn't going to screw you over and make it impossible to run Linux. Linux will keep progressing, just like they always have.

---

### Post by TheFu on 2022-05-06
> Linux users have always been the "little guy" from a market share perspective.
Only on the desktop.
On servers and phones, Linux has won, even when MSFT tried to kill the phone maker that was selling Linux-based (Debian) phones in 2008 - before Android.

MSFT being slightly nice is relatively new. I assume it is a trap, based on 40 yrs experience with that company. When they buy a company I am using, I close my accounts and wish they didn't get the data held there.  OTOH, if my job depended on using MSFT stuff, my view would be completely different.  Paychecks are a good thing. No paycheck is a bad thing and most other considerations don't hold the same weight for regular people during their working years.

---

### Post by forrestcupp on 2022-05-07
> **TheFu said:**
> Only on the desktop.
On servers and phones, Linux has won, even when MSFT tried to kill the phone maker that was selling Linux-based (Debian) phones in 2008 - before Android.

MSFT being slightly nice is relatively new. I assume it is a trap, based on 40 yrs experience with that company. When they buy a company I am using, I close my accounts and wish they didn't get the data held there.  OTOH, if my job depended on using MSFT stuff, my view would be completely different.  Paychecks are a good thing. No paycheck is a bad thing and most other considerations don't hold the same weight for regular people during their working years.

Yeah, you're absolutely right about it being only on the desktop. But it's usually only the Linux desktop users that are predicting impending doom. My only point is that people have been saying that for a very long time, and it never happened. People were freaking out back when motherboards started gravitating more to UEFI instead of BIOS. They said Microsoft was trying to use that to force Linux out of existence. The reality was that UEFI was a legit evolution, and it brought progress to the limitations of a BIOS. The other reality is that the Linux world just progressed and adapted with it, and it wasn't really the end of Linux. Linux isn't going anywhere. TPM 2.0 isn't the doom of Linux any more than UEFI was.

---

### Post by TheFu on 2022-05-07
> **forrestcupp said:**
>   People were freaking out back when motherboards started gravitating more to UEFI instead of BIOS. They said Microsoft was trying to use that to force Linux out of existence. The reality was that UEFI was a legit evolution, and it brought progress to the limitations of a BIOS. The other reality is that the Linux world just progressed and adapted with it, and it wasn't really the end of Linux. Linux isn't going anywhere. TPM 2.0 isn't the doom of Linux any more than UEFI was.

But with UEFI, it is still optional.  Of all my systems, only 1 uses UEFI to boot.  None of my Ryzens do.  Definitely optional.
Initially, UEFI was from Apple, then MSFT decided it, with Secure Boot, was a good idea to solve some Windows-specific issues.  Again, solving issues that linux people didn't have.

But the Linux community is flexible and turned the UEFI lemon into Lemonade. Some day, I may switch to using it, once the technology matures a bit more.

---

### Post by Rocket2DMn on 2022-05-08
I'll bite.

> **Shibblet said:**
> 
The TPM 2.0 Chip is entirely for Microsoft to control and monitor your computer.
They can, at this point, require any software loaded, to be specifically from the Microsoft Store.


These two sentences seem to be your core concerns.

AFAICT, the first statement is just wrong - TPM doesn't appear to have anything do with controlling and monitoring anything, it's a specification for doing secure computing operations, and it's not MS-specific.  See also TheFu's earlier reply.

The second statement might become true (to varying extents and with the possibility of exceptions) only within a MS Windows environment.  Windows cannot restrict what another OS installed and booted on the system does, nor can it (on its own) block installation of other OSes - that's a concern more related to using secure boot implementations.

> **Shibblet said:**
> I'd be willing to bet that within the next 5 years, all computers will be data mining as part of some required update for Windows...

Again - strictly a problem within a Windows environment.

---

### Post by grahammechanical on 2022-05-08
I decided to check if my recently purchased laptop had a TPM. It does. The place to look is in the Security section of the UEFI. I get these options.

Security Device Support> Enable/Disable BIOS support for TPM 2.0
Clear TPM> Enable/Disable removes all context associated with a specific owner
TPM device found

My thoughts on all this is that we have had UEFI, TPM and Windows 10/11 for a few years. Some people have difficulty installing Ubuntu. Is it because Windows 10/11 has put some blocking code into the TPM? I do not think so. 

Regards

---

### Post by Shibblet on 2022-05-09
This reminds me of when I worked in a Pharmacy.  If the customers insurance chose not to pay for certain medications, the customer just couldn't get it.  They have crazy rules...  For example: Let's say a doctor wants to put their patient on Nexium.  The insurance company can require the patient has been on Omeprazole for 6 months before they will authorize Nexium.  Regardless of what the doctor says.

> **Shibblet said:**
> The TPM 2.0 Chip is entirely for Microsoft to control and monitor your computer.
They can, at this point, require any software loaded, to be specifically from the Microsoft Store.

> **Rocket2DMn said:**
> I'll bite.
These two sentences seem to be your core concerns.

Yes.  Not so much the software loaded, because it won't matter if you're not using Windows...

But more importantly, this:

> **grahammechanical said:**
> If that proves to be correct it will likely mean that it will be impossible to install a dual boot with Linux on machines pre-installed with Windows. People said similar things years ago when they first heard about Secure Boot. But Microsoft allowed Linux boot binaries to be verified and be given a Microsoft signed key that was registered in the machine's secure boot database. I believe that Canonical played a part in fixing up that arrangement. Perhaps Canonical will make a similar approach regarding TPMs.

The problem with the TPM 2.0 chip, is that it does have the ability to stop any other OS from running on the computer in question.  And as much as I appreciate Canonical stepping up to the plate to find a solution, I have to ask... is this the right solution?

> **Rocket2DMn said:**
> Again - strictly a problem within a Windows environment.

Good point.  Do you think companies like System76, Slimbook, and Tuxedo Computers will have the option to disable/remove the TPM 2.0 on their motherboards?  Will the MoBo manufacturers even offer it?

Looks like System76 will give users the option of turning it off.  But it is still there.  [https://tech-docs.system76.com/models/addw1/setup-specs.html]("https://tech-docs.system76.com/models/addw1/setup-specs.html")

System76 now has TPM 2.0 Chips on their motherboards... and essentially it is completely unnecessary for a Linux based PC.  Does this mean that Microsoft has essentially forced Hardware Manufacturers to require this TPM 2.0 Chip?  Essentially making them Hardware dictators?

---

### Post by VMC on 2022-05-09
> **Shibblet said:**
> The problem with the TPM 2.0 chip, is that it does have the ability to stop any other OS from running on the computer in question...?Where's your source? A link confirming this statement.

---

### Post by #&amp;thj^% on 2022-05-09
> **VMC said:**
> Where's your source? A link confirming this statement.
+1 a link is needed.
last I heard
> Correction, 8:06PM ET: This story originally stated Windows 11 would likely still install on PCs with access to TPM 1.2 and older CPUs, because that’s what we read in Microsoft’s documentation. Microsoft has now corrected those documents to specify TPM 2.0 is a minimum requirement for Windows 11
I read that as Windows 11 only, I have 3 Linux systems along side of Win 11 now.

---

### Post by Shibblet on 2022-05-09
> **VMC said:**
> Where's your source? A link confirming this statement.

From: [https://docs.microsoft.com/en-us/windows-hardware/design/device-experiences/oem-tpm]("https://docs.microsoft.com/en-us/windows-hardware/design/device-experiences/oem-tpm")

The article states: > Trusted Platform Module (TPM) technology is designed to provide hardware-based, security-related functions. A TPM chip is a secure crypto-processor that helps you with actions such as generating, storing, and limiting the use of cryptographic keys. Many TPMs include multiple physical security mechanisms to make it tamper resistant, and malicious software is unable to tamper with the security functions of the TPM.

Generating, storing, and limiting.  Limiting may be a problem when the chip has "multiple physical security mechanisms to make it tamper resistant." 

I mean... I may be wrong here, but it says to me, if they want to block Linux, they can.  And there will be no work-around.

---

### Post by #&amp;thj^% on 2022-05-09
al i can say now is:
```
cat /sys/class/tpm/tpm*/tpm_version_major
2

```
also:
```
[ -d $(ls -d /sys/kernel/security/tpm* 2>/dev/null | head -1) ] && \
    echo "TPM available" || echo "TPM missing"
TPM available

```

---

### Post by VMC on 2022-05-09
> **Shibblet said:**
> From: [https://docs.microsoft.com/en-us/windows-hardware/design/device-experiences/oem-tpm](https://docs.microsoft.com/en-us/windows-hardware/design/device-experiences/oem-tpm)

The article states: 

Generating, storing, and limiting.  Limiting may be a problem when the chip has "multiple physical security mechanisms to make it tamper resistant." 

I mean... I may be wrong here, but it says to me, if they want to block Linux, they can.  And there will be no work-around.

How does this relate to Linux being on another partition?! How is TPM going to stop dual booting. The quote is about malicious software being on Windows.

---

### Post by TheFu on 2022-05-09
> **Shibblet said:**
> From: [https://docs.microsoft.com/en-us/windows-hardware/design/device-experiences/oem-tpm]("https://docs.microsoft.com/en-us/windows-hardware/design/device-experiences/oem-tpm")

The article states: 

Generating, storing, and limiting.  Limiting may be a problem when the chip has "multiple physical security mechanisms to make it tamper resistant." 

I mean... I may be wrong here, but it says to me, if they want to block Linux, they can.  And there will be no work-around.

Do you mean like how Google Chromebooks are all locked to only run ChromeOS?  Chromebooks have TPM and encryption.  Yet, people figured out how to modify the hardware to put any non-ChromeOS OS onto most of those machines.  There are a few that are so locked down, they cannot run anything else.

TPM isn't an issue anymore than SecureBoot is for Linux and both add security value.
There are BSD and Linux platforms that cannot run Windows ... TiVo and Roku for example, but nobody is too mad about that.  People sued TiVo, but their proprietary stuff was in hardware, outside the F/LOSS software areas.  Plus, the MIPS CPUs they used weren't exactly great at anything besides handing over encrypted files to the HW video decoder for playback.

If a business uses GNU licensed software, then they need to comply with the license.  A few have been caught - Linksys, Ubiquiti, Mikrotik of the top of my head.  They were all forced to comply. [http://gpl-violations.org/](http://gpl-violations.org/) is a website and org just about that. It still happens today.  The simple fix is to force all GPL to the AGPLv3 for **any** GPL use in a business. Google, Facebook, Twitter would never have grown, since they would have been sharing all their stuff back to the community from the beginning, except for their custom code in new programs.

When I was a CIO, we specifically avoided all GPL software. We loved BSD, MIT, Apache licenses, but not GPL.  Apple is built on BSD software.  So is Roku.

TPM has a standard, just like UEFI has a standard.  Some laptop makers still don't follow the UEFI standard correctly, which is why some Ubuntu installs require manually changing some file under /boot/EFI/ post-install.  I had a Toshiba laptop that was like that.

---

### Post by Rocket2DMn on 2022-05-10
> **Shibblet said:**
> From: [https://docs.microsoft.com/en-us/windows-hardware/design/device-experiences/oem-tpm]("https://docs.microsoft.com/en-us/windows-hardware/design/device-experiences/oem-tpm")
 
Generating, storing, and limiting [the use of cryptographic keys].  Limiting may be a problem when the chip has "multiple physical security mechanisms to make it tamper resistant." 

I mean... I may be wrong here, but it says to me, if they want to block Linux, they can.  And there will be no work-around.

Effectively restricting OSes has to be done by the system integrator, e.g., by using Secure Boot to verify a boot stage's SW signature against a read-only set of known hashes.  An OS on its own cannot change this - it doesn't get loaded until AFTER secure boot verifies it.  If it could retroactively change Secure Boot's set of known hashes, then Secure Boot would be worthless.  TPM is not Secure Boot.

The article states, "Starting with Windows 10, the operating system automatically initializes and takes ownership of the TPM." Here, initialization happens at OS boot time, and ownership means that the OS manages access to the hardware component (as is the typical responsibility of an OS).  More generally, memory/registers that are not read-only (i.e., written only once by the HW designer or system integrator, e.g., a stage-0 bootloader) and is accessible by the CPU is configurable by whatever OS is running (having been initialized by the earlier bootloader).  This is a simplification, but sufficient for now :).

Furthermore, "TPMs are passive: they receive commands and return responses."  It's basically an area to do secure computation.  It should probably not be storing data between boots (that screams security violation to me, which is entirely antithetical do TPM's purpose).

---

### Post by #&amp;thj^% on 2022-05-10
> **Rocket2DMn said:**
> Effectively restricting OSes has to be done by the system integrator, e.g., by using Secure Boot to verify a boot stage's SW signature against a read-only set of known hashes.  An OS on its own cannot change this - it doesn't get loaded until AFTER secure boot verifies it.  If it could retroactively change Secure Boot's set of known hashes, then Secure Boot would be worthless.  TPM is not Secure Boot.

The article states, "Starting with Windows 10, the operating system automatically initializes and takes ownership of the TPM." Here, initialization happens at OS boot time, and ownership means that the OS manages access to the hardware component (as is the typical responsibility of an OS).  More generally, memory/registers that are not read-only (i.e., written only once by the HW designer or system integrator, e.g., a stage-0 bootloader) and is accessible by the CPU is configurable by whatever OS is running (having been initialized by the earlier bootloader).  This is a simplification, but sufficient for now :).

Furthermore, "TPMs are passive: they receive commands and return responses."  It's basically an area to do secure computation.  It should probably not be storing data between boots (that screams security violation to me, which is entirely antithetical do TPM's purpose).

In a nut shell, Well said, outside of spell errors. :P

---

### Post by Shibblet on 2022-05-10
> **TheFu said:**
> Do you mean like how Google Chromebooks are all locked to only run ChromeOS?  Chromebooks have TPM and encryption.  Yet, people figured out how to modify the hardware to put any non-ChromeOS OS onto most of those machines.  There are a few that are so locked down, they cannot run anything else.

Exactly.  I own one.  Asus C425.  There are ways to "trick" the computer into running Linux, but it seems more trouble than it's worth.  

Will this mean that computers that come with Windows 11 pre-installed, will not be allowed to run Linux, because the TPM 2.0 is "limiting" the crypto-keys?
I do understand the concept of usage as well.  Why buy a Microsoft Surface if you don't want to run Windows?  And, again, I am aware that there are ways to "trick" the Surface into running Linux.
But if you have to "trick" your computer into doing it, that will eliminate many possible users... myself included.  

I made a point of finding out if my computer will run Linux.  Thankfully, they advertise Ubuntu.  And, yes, it's got a TPM 2.0.
[([https://store.minisforum.com/products/hx90](https://store.minisforum.com/products/hx90))]("https://store.minisforum.com/products/hx90")

A majority of Linux (in general, not just Ubuntu/Flavors) users are not installing on new computers.  Which the TPM 2.0 module will not be a problem.
Everyone eventually wants to upgrade though...

---

### Post by Shibblet on 2022-05-10
> **Rocket2DMn said:**
> Effectively restricting OSes has to be done by the system integrator, e.g., by using Secure Boot to verify a boot stage's SW signature against a read-only set of known hashes.  An OS on its own cannot change this - it doesn't get loaded until AFTER secure boot verifies it.  If it could retroactively change Secure Boot's set of known hashes, then Secure Boot would be worthless.  TPM is not Secure Boot.
Gotcha.  This was my concern.  

> **Rocket2DMn said:**
> The article states, "Starting with Windows 10, the operating system automatically initializes and takes ownership of the TPM." Here, initialization happens at OS boot time, and ownership means that the OS manages access to the hardware component (as is the typical responsibility of an OS).  More generally, memory/registers that are not read-only (i.e., written only once by the HW designer or system integrator, e.g., a stage-0 bootloader) and is accessible by the CPU is configurable by whatever OS is running (having been initialized by the earlier bootloader).  This is a simplification, but sufficient for now :). 
Again, thank you for the clarification.

> **Rocket2DMn said:**
> Furthermore, "TPMs are passive: they receive commands and return responses."  It's basically an area to do secure computation.  It should probably not be storing data between boots (that screams security violation to me, which is entirely antithetical do TPM's purpose).
And I think that's the problem.  There are a lot of articles out there about what a TPM does, but not enough explaining what it's purpose is.

---

### Post by forrestcupp on 2022-05-10
> **Shibblet said:**
> 
Good point.  Do you think companies like System76, Slimbook, and Tuxedo Computers will have the option to disable/remove the TPM 2.0 on their motherboards?  Will the MoBo manufacturers even offer it?

Looks like System76 will give users the option of turning it off.  But it is still there.  [https://tech-docs.system76.com/models/addw1/setup-specs.html]("https://tech-docs.system76.com/models/addw1/setup-specs.html")

System76 now has TPM 2.0 Chips on their motherboards... and essentially it is completely unnecessary for a Linux based PC.  Does this mean that Microsoft has essentially forced Hardware Manufacturers to require this TPM 2.0 Chip?  Essentially making them Hardware dictators?

I know I'm going to have the unpopular opinion here. But if you can get Linux working with TPM 2.0, in my opinion it would be silly to intentionally buy a computer that doesn't have it, even if it's unnecessary for Linux.

My own testimony is a good example. I was sold on Linux. I exclusively used Linux, and I had no intention of ever going back to Windows. But I ended up finding myself in a situation where I needed to use a few specialized programs that would not work with Wine, or any other way in Linux. So I was forced to use Windows. So at first, I tried out dual-booting. But it was just too much of a hassle to boot back and forth when I was perfectly capable of doing everything I needed to do in Windows. So I ended up gravitating away from Linux. Even today, I still like Linux better as an OS. I love that you can customize it as much as your heart desires. But alas, here I am typing from Windows.

My point is, you never know when you'll have to go back to Windows, or at least dual-boot, even if you think you never will.

---

### Post by TheFu on 2022-05-10
That's why we use virtual machines and don't dual/triple/quad boot. There are 7 running on this system now. I hardly notice it. Most are very, very, low use VMs that take almost zero CPU.

TPM is a standard. Linux supports it. That's all we need to know.

I'm fairly certain that I won't be using Windows 8+ on my systems ever. If a company wants me to use Windows, then they can provide the hardware and licenses.  The same for a cell phone.

---

### Post by Shibblet on 2022-05-11
> **forrestcupp said:**
> My point is, you never know when you'll have to go back to Windows, or at least dual-boot, even if you think you never will.

I know the feeling.

Things would actually be "easier" for me if I decided to use Windows.  Currently, I use a VM for Windows 7 when I need to run my Adobe Software.  I bought a copy of Adobe CS6 many years ago.  (BTW, Adobe really hasn't added much to their software suite since then.)  I have been a graphic artist for over 25 years.  I like the software that's available for Linux OS's such as Gimp and InkScape...  However, all of my old files and graphics were made in Adobe, so transitioning everything would be too much of a chore.

I also have a couple of utility programs for some hardware, that only works in Windows... fortunately, VirtualBox and Windows 7 work great.

When I say things would be easier... What I mean is that I wouldn't have to open VirtualBox.  All of my apps would run right in the OS.  No re-booting, no extra loading times, etc.  Hardware acceleration works without fussing, wouldn't have to worry so much about hardware compatibility, games in my Steam library just work, etc. etc. etc.

The problem is, when choosing to use Windows, you have to choose to give up certain amounts of privacy.  The OS is tracking your data at all times, even if you go through the trouble of attempting to disable it.  You can disable a lot of telemetry, but ultimately, you can't disable it all.  Nvidia users... beware, your Windows drivers have telemetry built in by default.

Windows also has horrendous memory management, and eats up WAY more resources than a KDE Desktop does.  And this is because it's loading apps into memory like MS Teams, Cortana, and a bunch of background applications that you may not want, or even use.

Unfortunately, there is no "middle ground."  You can't have Windows without the junk and telemetry, and you can't have Linux with flawless Windows software compatibility.

This is where most of my troubles with this TMP 2.0 issue come from.  Windows just keeps pushing ahead with features that no one asked for, or even wants.  They are taking your personal and usage data, and unfortunately, you have to choose to accept this, or not.  And to make an operating system, that actually requires a hardware replacement, for a "security" module, just seems like more of the same from Microsoft.

---

### Post by Tadaen_Sylvermane on 2022-05-11
I never thought I'd live long enough to see the day a computer was viewed as totally disposable. When I grew up they were just becoming a thing. You didn't buy a new one, you fixed it. Now they get replaced without a thought.

A couple years ago I found a machine on the side of the road. They had tossed it because of a clicking sound. I replaced the fan in the power supply and put in an ssd. Mom's parents have been using it daily for the last 3-4 years now. Pops love his solitaire. Kpat makes him happy.

Everything is disposable and Microsoft is just helping that right along and screwing us over in the process. The american way?

---

### Post by grahammechanical on 2022-05-11
If you want to do something for the rest of your life and still be no wiser, then here is the location of the TPM 2.0 specification.

[https://trustedcomputinggroup.org/resource/tpm-library-specification/](https://trustedcomputinggroup.org/resource/tpm-library-specification/)

Regards and happy reading! Let us know if you find anything sneaky.

---

### Post by Shibblet on 2022-05-11
> **grahammechanical said:**
> Regards and happy reading! Let us know if you find anything sneaky.

You never find "sneaky" in the tech documents of how something works.  You find "sneaky" when people learn how to exploit said technology, especially within the confines of the specs.

"The unleashed power of the atom has changed everything save our modes of thinking and we thus drift toward unparalleled catastrophe." - Albert Einstein

---

### Post by grahammechanical on 2022-05-11
I am intrigued by the setting "Clear TPM" in my UEFI settings. It  removes all context associated with a specific owner. What does that  amount to? I found this Microsoft document.

[https://docs.microsoft.com/en-us/windows/security/information-protection/tpm/initialize-and-configure-ownership-of-the-tpm](https://docs.microsoft.com/en-us/windows/security/information-protection/tpm/initialize-and-configure-ownership-of-the-tpm)

Under the heading Clear all the keys from the TPM:

> You can use the Windows Defender Security Center app to clear the TPM as  a troubleshooting step, or as a final preparation before a clean  installation of a new operating system. Preparing for a clean  installation in this way helps ensure that the new operating system can  fully deploy any TPM-based functionality that it includes, such as  attestation. However, even if the TPM is not cleared before a new  operating system is installed, most TPM functionality will probably work  correctly.[QUOTE][/QUOTE]

And then I saw this under the heading Precautions to take before clearing the TPM.


> Clearing the TPM causes you to lose all created keys associated with the  TPM, and data protected by those keys, such as a virtual smart card or a  sign in PIN. Make sure that you have a backup and recovery method for  any data that is protected or encrypted by the TPM.

This will cause some concern to some of us.

> If you have Windows 10, version 1507 or 1511, or Windows 11, the  initialization of the TPM cannot complete when your computer has network  connection issues and both of the following conditions exist:

I  am guessing that the encryption keys are stored on a Microsoft server.  Which seems fair enough. I am wondering if this situation could lead to a  solution that was taken regarding secure boot. That is with Linux  developers providing encryption keys that Microsoft will validate. Then  when Windows is first installed encryption keys for Linux will also be  part of the TPM initialization process.

Have there been any reports of Windows 11 preventing the installation of Linux? Apart from the usual issues.

Regards

---

