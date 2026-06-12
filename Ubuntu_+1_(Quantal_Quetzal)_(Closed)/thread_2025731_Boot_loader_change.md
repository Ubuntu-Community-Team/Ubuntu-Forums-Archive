---
title: "Boot loader change"
date: 2012-07-14
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by thnewguy on 2012-07-14
I've read that Ubuntu 12.10 will feature a new boot loader, efilinux, in order to better handle secure boot technology. The efilinux boot loader doesn't support pre-efi hardware. What I'm wondering is, will Ubuntu 12.10 still install on machines with older BIOSs, pre-efi hardware? Will older machines still have the option of installing GRUB2, or will users have to make sure they are using modern hardware with support for efi?

---

### Post by ronacc on 2012-07-14
given the fact that Ubuntu has not given a thought to chasing away longtime users lately and orphaning hardware rather cavalierly I think you have your answer .

---

### Post by thnewguy on 2012-07-14
That's not an answer at all, that's idle speculation. I want to know (not speculate) if Ubuntu 12.10 will come with a boot loader which supports older hardware and, assuming it does, which one? Will efilinux be patched to support older devices? Will GRUB2 be included, which makes the "Ubuntu drops GRUB2" headlines awfully misleading? Or will there be another solution in the works? I have yet to see any blog or mailing list post regarding their stragegy for older hardware.

---

### Post by dext on 2012-07-14
> **thnewguy said:**
> That's not an answer at all, that's idle speculation. I want to know (not speculate) if Ubuntu 12.10 will come with a boot loader which supports older hardware and, assuming it does, which one? Will efilinux be patched to support older devices? Will GRUB2 be included, which makes the "Ubuntu drops GRUB2" headlines awfully misleading? Or will there be another solution in the works? I have yet to see any blog or mailing list post regarding their stragegy for older hardware.

[http://lwn.net/Articles/453638/](http://lwn.net/Articles/453638/) . should answer a question

---

### Post by WelshDragon on 2012-07-15
"We hope that we'll also be able to make the first stage loader detect whether Secure Boot is enabled and otherwise chain to GRUB 2, to ensure that we don't regress behaviour for those with UEFI systems that do not implement Secure Boot or that have it disabled."

[https://lists.ubuntu.com/archives/ubuntu-devel/2012-June/035445.html](https://lists.ubuntu.com/archives/ubuntu-devel/2012-June/035445.html)

---

### Post by Georgia boy on 2012-07-17
Hmmmm. So another one bows down to the mighty Microsoft. All Hail!!!
 
"For machines that come preloaded with Ubuntu, Canonical will store the Ubuntu key in firmware. The company will require machines that have "Ubuntu certified" labels to have the Ubuntu key stored in the UEFI signature database."

"Canonical said it will require the Microsoft key to be present on machines that are Ubuntu certified so users can install Microsoft's Windows operating system if they wish."

Both taken from:[http://www.theinquirer.net/inquirer/news/2186842/canonical-intels-efilinux-ubuntu-uefi-secure-boot](http://www.theinquirer.net/inquirer/news/2186842/canonical-intels-efilinux-ubuntu-uefi-secure-boot)

You know, maybe I'm wrong in thinking this but seems to me that if someone buys anything with Linux pre-installed then they didn't want Windows on it to begin with so why force another manufacture that supports Ubuntu to bow down to Microsoft? If a person wanted a system with Windows on it then wouldn't they buy one with it already installed?

Guess Systems 76 is going to be installing that crap? Too bad if so. 

Oh well, that leaves ZaReason and the others that install other Linux Distros besides Ubuntu to buy from right? 

Sad to see that this is  happening like this.

---

### Post by ventrical on 2012-07-17
I'm sure there will be GRuB rollback for older machines.

---

### Post by ventrical on 2012-07-17
> **WelshDragon said:**
> "We hope that we'll also be able to make the first stage loader detect whether Secure Boot is enabled and otherwise chain to GRUB 2, to ensure that we don't regress behaviour for those with UEFI systems that do not implement Secure Boot or that have it disabled."

[https://lists.ubuntu.com/archives/ubuntu-devel/2012-June/035445.html](https://lists.ubuntu.com/archives/ubuntu-devel/2012-June/035445.html)


Thanks! :)

---

### Post by DogMatix on 2012-07-17
At what point is UEFI compatibility being added to 12.10? or, is it included already? 

I'm a bit out of the loop as I haven't been testing this release.

---

### Post by ventrical on 2012-07-17
"The biggest threat to user data and software choice (on their own computers) are implementations of the [UEFI]("http://en.wikipedia.org/wiki/Extensible_Firmware_Interface") boot protocol "SecureBoot". See the [FSF whitepaper]("http://www.fsf.org/campaigns/secure-boot-vs-restricted-boot/whitepaper-web")  regarding this issue. Certain hardware with this implementation rigidly  ties hardware to the OS, giving control to the OS manufacturer, not to  the user. Hardware failure in such a configuration causes unrecoverable  data loss (as frequently happened when a similar mechanism was initially  used for Windows XP a decade ago).  Be extremely careful when  purchasing hardware that includes the UEFI "SecureBoot"; many  implementations do not allow the user to install (or modify) their own  operating systems, making the computer or device essentially a  short-lifespan disposable one. Do not choose hardware that puts your  important data at risk. (If forced to use such hardware, user data  should never be stored on such a computer or device.) [H-node]("http://www.h-node.org/hardware/catalogue/en") maintains a list of hardware compatible with flexible, free, and open source software and operating systems. [Coreboot]("http://en.wikipedia.org/wiki/Coreboot") (with SeaBIOS) is an open source alternative to UEFI and is supported by AMD-based motherboards."

[http://ubuntuguide.org/wiki/Kubuntu_Quantal](http://ubuntuguide.org/wiki/Kubuntu_Quantal)

Manufacturers will still build systems without UEFI or (SecureBoot) because they all know what  Genuine Advantage and the MS Authentication tool did to a lot of valid  and licensed -legitimate systems.  I do not think anyone wants to take a back-step into that corrundrum.

---

### Post by ventrical on 2012-07-17
> **DogMatix said:**
> At what point is UEFI compatibility being added to 12.10? or, is it included already? 

I'm a bit out of the loop as I haven't been testing this release.


it's already in the quantal <universe> repos.

sbsigntool

[http://packages.ubuntu.com/search?suite=quantal&keywords=bsign](http://packages.ubuntu.com/search?suite=quantal&keywords=bsign)

---

### Post by Georgia boy on 2012-07-17
Too bad. Guess  if I get a preinstalled system it will be one that didn't bow down and knuckle under. Sad. Guess I'd go for ZaReason or another company and have Debian or whichever has the balls to stand on their own. When I left Windows it was for freedom to do whatever I wanted to do with my own machine. To totally get away from MS. Not to find myself having to fall into their do what we want not what you want. Sad state.

---

### Post by mcellius on 2012-07-18
Remember, though, that this forum is for testing.  The final result won't necessarily be different than what you find now, but if problems are found it could be subject to changes.  This is the time to find out and provide responses, and you might be able to influence how things turn out.

---

### Post by ventrical on 2012-07-18
> **Georgia boy said:**
> Too bad. Guess  if I get a preinstalled system it will be one that didn't bow down and knuckle under. Sad. Guess I'd go for ZaReason or another company and have Debian or whichever has the balls to stand on their own. When I left Windows it was for freedom to do whatever I wanted to do with my own machine. To totally get away from MS. Not to find myself having to fall into their do what we want not what you want. Sad state.

 I do not see how offering a level playing field can be a sad state. Nobody is forcing anyone to use SecureBoot. We both do not know because we both do not have a pre-installed system. So far, Quantal hasn't had any major problems handling my older machines.

  As for "balls" ...I think we have to have the balls to  modify and manage our own systems. The tools are there.  Why blame Canonical?

---

### Post by Harry33 on 2012-07-18
> **ventrical said:**
> it's already in the quantal <universe> repos.

sbsigntool

[http://packages.ubuntu.com/search?suite=quantal&keywords=bsign](http://packages.ubuntu.com/search?suite=quantal&keywords=bsign)

Right, it is in the universe repos, while grub2 is the main repos.

---

### Post by ronacc on 2012-07-18
> **ventrical said:**
> I do not see how offering a level playing field can be a sad state. Nobody is forcing anyone to use SecureBoot. We both do not know because we both do not have a pre-installed system. So far, Quantal hasn't had any major problems handling my older machines.

  As for "balls" ...I think we have to have the balls to  modify and manage our own systems. The tools are there.  Why blame Canonical?

and some of us see this as the first step in another M$ attempt attempt to prevent installation of ANY alternative . As someone who has been around since before the pc existed I can say without hesitation that M$ is pure evil and will never cease trying to murder any competition .

---

### Post by mcellius on 2012-07-18
> and some of us see this as the first step in another M$ attempt attempt  to prevent installation of ANY alternative . As someone who has been  around since before the pc existed I can say without hesitation that M$  is pure evil and will never cease trying to murder any competition .

Could be.  But if we do nothing, we give in to Microsoft.  Canonical and RedHat are at least trying ways to deal with it; they may not have found the ideal solution yet, but they're making an effort.  Nobody yet seems to be very sure how all of this will go, but we do know that something has to be done.

---

### Post by jerrylamos on 2012-07-18
> **ronacc said:**
> and some of us see this as the first step in another M$ attempt attempt to prevent installation of ANY alternative . As someone who has been around since before the pc existed I can say without hesitation that M$ is pure evil and will never cease trying to murder any competition .
I've been on computers since '59 and pc's since '82 all the way through Microsoft's "rise".  Bill Bate and Steve Jobs were highly competitive doing everything they could to kill the competition just for the sake of killing competition whether there was any impact on their business or not.

On topic I'm very interested in Linux keeping right on top of what is necessary for their products to run on pc's, tablets, whatever.  My widescreen notebook I swapped out the Windoze....7 hard drive because unstable development Ubuntu installs kept clobbering Grub boot taking all sorts of antics to recover/restore.

This netbook has Ubuntu and Windoze....7 on the hard drive which I keep in case I replace it and the next user might need Microsoft.  Example my wife who maintains a couple web sites with Dreamweaver $$ which is not available on Linux.

BTW, I've ordered a Raspberry Pi for $40.  At 700 gHz and 256 MB a bit questionable but I'd like to try Ubuntu on it when (if) it is supported, runs Debian at the moment.

Jerry

---

### Post by ventrical on 2012-07-18
> **ronacc said:**
> and some of us see this as the first step in another M$ attempt attempt to prevent installation of ANY alternative . As someone who has been around since before the pc existed I can say without hesitation that M$ is pure evil and will never cease trying to murder any competition .

 I'm with you here. Iv'e been working with electronics (started my TV service repair apprenticeship in 1962) for a long time, and PC programming also. But my point it that  Microsoft cannot kill old PCs, older hardware, etc.. and they cannot dictate to PC manufacturers as to how to build and structure their PCs. I mean , at first it sounds like Canonical is shooting itself in the foot with pre-installed systems that are up and comming but I think the reason  they want to include a MicroSoft key is so there will not be a conflict when running MS products under Virtual Machine. SecureBoot UEFI embedded into MS software installations may give VM a real hard time and I think it is wise that Canonical is trying to cover their bases. As it stands now I can install Windows XP in VM and it actually runs better in VM than under a hard install. Of course, if I were Microsoft, I would want to eliminate this capability in Ubuntu because it makes Microsoft look bad.

  It's not like that Canonical is a "walled garden" like Apple/Mac is-was. I think what Ubuntu is doing here is trying to reach out a hand and "unify" a lot of division between competitors so at least that they will be able to agree on standards in the future.

  But the real kicker about SecureBoot is that is assumes that most end_users are complete dummies and propounds the premise that you will eventually bork your own system through end_user inability.!! Then, it is rather quite simple , to just avoid  newer PCs with UEFI/SecureBoot unless for beta testing purposes.

---

### Post by ventrical on 2012-07-18
> **Harry33 said:**
> Right, it is in the universe repos, while grub2 is the main repos.


Well, thats exactly my point on the whole matter. Contrary to that dev e-mail  it appears that GRUB will be around for quite some time and it answers the question about Quantal.  Whether or not it (GRUB2/GRUB) is pulled by release time and replaced with a reasonable facsimile of SeureBoot ? - I am not privy to that knowledge -so - yes - I am assuming.

---

### Post by pressureman on 2012-07-18
> **jerrylamos said:**
> BTW, I've ordered a Raspberry Pi for $40.  At 700 gHz and 256 MB a bit questionable but I'd like to try Ubuntu on it when (if) it is supported, runs Debian at the moment.

700 GHz? Holy smokes, where do I get one of these lightning fast Raspberry Pis?

;-)

---

### Post by dino99 on 2012-07-18
> **jerrylamos said:**
> 

BTW, I've ordered a Raspberry Pi for $40.  At 700 gHz and 256 MB a bit questionable but I'd like to try Ubuntu on it when (if) it is supported, runs Debian at the moment.

Jerry

there is a distro made for it: try  Raspbian  :P

---

### Post by jerrylamos on 2012-07-18
> **pressureman said:**
> 700 GHz? Holy smokes, where do I get one of these lightning fast Raspberry Pis?;-)My typo error.  Actually it's supposed to be lightning cheap.  By changing a boot parameter it'll overclock to 900 mHz, overvoltage (voids warranty) to 1 gHz.

Since it's for Debian & variants hopefully it will help increase Linux footprint...

Jerry

p.s. Try [http://www.raspberrypi.org/](http://www.raspberrypi.org/) for what you can do and where to order.  It's a non-profit so it has slow build up, first 100,000 are presumably out and second 100,000 coming in next month.

---

### Post by ventrical on 2012-07-18
> **pressureman said:**
> 700 GHz? Holy smokes, where do I get one of these lightning fast Raspberry Pis?

;-)


I think we're talking time travel on this one :)

haha

---

