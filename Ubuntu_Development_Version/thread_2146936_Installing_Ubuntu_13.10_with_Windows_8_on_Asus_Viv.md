---
title: "Installing Ubuntu 13.10 with Windows 8 on Asus Vivobook (A400C)"
date: 2013-05-20
forum: Ubuntu Development Version
---

### Post by cdoebbler on 2013-05-20
Trying to install Ubuntu 13.10 on an i5/4GB computer that cam with Windows 8. I cannot get it to boot from USB stick. Tried turning off Secureboot and check that USB is recognized by system, but still system just boots into Windows. I have trolled the forum and several others and tried several attempted fixes without any luck during the last five days. Is their any way to get around this apparent SecureBoot lock, which appears to stay on even when turned off?

---

### Post by 2F4U on 2013-05-20
How did you create the Ubuntu USB boot media? This often fails resulting in a non-bootable stick. Did you verify the checksum of the downloaded iso file before creating the USB stick?

---

### Post by sudodus on 2013-05-20
See this thread, and the solution by [*ublondie*]("http://ubuntuforums.org/member.php?u=894157")

[http://ubuntuforums.org/showthread.php?t=2108487](http://ubuntuforums.org/showthread.php?t=2108487)

---

### Post by IsmAvatar on 2013-05-20
How did you get your hands on Ubuntu 13.10 anyways? X_X

---

### Post by cdoebbler on 2013-05-22
Created it using Ubuntu download and Windows 8 ISO burner and checksum matched fine.

---

### Post by cdoebbler on 2013-05-22
At Ubuntu site....it is hard to find but search "Ubuntu 13.10" and it comes up.

---

### Post by cdoebbler on 2013-05-22
Thanks but tread is irrelevant as it is about creating USB ISO which I have done fine. I can boot from it on my HP Mini100c running Ubuntu 12.10, but not on the i5 Windows machine.

---

### Post by sudodus on 2013-05-22
1. Can you boot any USB drive in this computer?

2. Is there a 64-bit or 32-bit Ubuntu system on your USB boot pendrive? You need Ubuntu 64-bit 12.04.2 or newer to boot in UEFI mode.

3. You turned off secure boot. But did you turn off fast boot?

4. What happens if you turn off UEFI mode (and boot in CSM or legacy mode)?

-o-

The Ubuntu version 13.10 is still in an early development phase. It cannot be expected to work with everything yet. Try 12.04.2, 12.10 or 13.04.

---

### Post by cdoebbler on 2013-05-23
1. No. Although only tried Ubuntu (versions, 12.04, 12.10, 13.04 & 13.10).

2. 13.10, 64-bit.

3. Turned off secure boot, not fast boot...left fast boot on. (Tried with fast boot off, but same problem.)

4. Cannot turn off UEFI in Bios...is there way to do it from command line in Windows 8 terminal?

---

### Post by sudodus on 2013-05-24
It can be tricky to boot the locked computers with Windows 8. But with help from several people it will probably be possible. [COLOR=#ff0000]So anyone with a good idea, please jump in and help :-)[/COLOR]

a.  My first advice would be to concentrate on a released version of Ubuntu  (not this early version of 13.10). So concentrate on a 64-bit version  of one of 12.04.2, 12.10, 13.04). If you want the LTS version, do not  start with 12.04, start with the newest point release 12.04.2.

b. It is important to turn off secure boot and fast boot, both should be turned off at the same time!

c.  I don't think you can turn off UEFI in Windows. Look once more in the  BIOS menu system! But the above mentioned Ubuntu 64-bit versions do boot  in my computer (a Toshiba) in UEFI mode, so they should boot, unless  there is another trap in your computer.

---

### Post by Bucky Ball on 2013-05-24
*Thread moved to **Ubuntu +1**.*

[QUOTE=IsmAvatar]How did you get your hands on Ubuntu 13.10 anyways? X_X [/QUOTE]

It's currently testing and will be released in October. You will find it easily with a search.

MESSAGE TO ALL: DO NOT post about 13.10 in any other sub-forum but this sub-forum, thanks. 13.10 will not be released until October and is very much wet behind the ears and testing. We are talking bleeding edge and not for general consumption.

---

### Post by cariboo on 2013-05-24
[oldfred]("http://ubuntuforums.org/member.php?u=852711"), is our resident expert on booting and installing on systems with UEFI, fortunately for him, he has gone on vacation for a few weeks. He does have [this link]("http://ubuntuforums.org/showthread.php?t=2147295") in his signature though, that may help.

@IsmAvatar, the Saucy daily live iso is available [here]("http://cdimage.ubuntu.com/daily-live/current/")

---

### Post by cdoebbler on 2013-05-24
Thanks.

a. Used 13.04 64-bit version.
b. Turned off both secure and fast boot. 
c. Yes, I cannot find how to turn off UEFI. It certainly is not possible in Bios and I do not know command line commands for this.

Using 13.04 iso, still have problem that computer does not boot from USB.  

Using Wubi I can get Ubuntu 13.04 installed and get to dual boot screen, but then get following error message when trying to boot ubuntu 13.04:

File: \ubuntu\winboot\wubildr.mbr

Status: 0xc000007b

Info: The application or operating system couldn't be loaded because a required file is missing or contains errors.

I checked the Check Sum for Wubi 13.04 and it is good. I have tried several times to recreate USB iso, but same message every time when trying to run Ubuntu.

---

### Post by cdoebbler on 2013-05-24
Thanks for advice. I had already tried everything in the Oldfred's posts and the several linked posts. What I posted here is as far as I got.

---

### Post by sudodus on 2013-05-24
I'm sorry, but I think it was not possible to make wubi work in UEFI mode in 13.04. The chance to boot from USB is higher than wubi.

New computers are often fast, so if you need to press a key to get a temporary boot menu and select USB, you need to press that key at once, when you reboot (or at the same time as you boot or reboot). Otherwise it might skip to the standard hard drive boot. Or maybe you can change the boot order between HDD, CD/DVD and USB (in a BIOS menu)?

But it might not work in your particular computer, if it is made to be locked to only boot from the internal drive.

---

### Post by Bucky Ball on 2013-05-24
Yep. I'd forget about the Wubi path to a dual-boot install. Just use the LiveCD/USB for a clean install and try to work that out. It is much ... cleaner, and can be less problematic.

---

### Post by grahammechanical on 2013-05-24
1) Saucy Salamander is less than one month into development and it is not unusual for a daily image to have problems. They are available for testing.

2) There have been issues installing Ubuntu on Windows 8 machines ever since they were put on the market. The solution, if there is one, is the same whether the Ubuntu version is 12.04.2, 12.10, 13.04 or 13.10 (still under development). This issue is not a Saucy Salamander specific issue.

There are many threads elsewhere in this forum giving advice on installing Ubuntu on Windows 8 machines.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

> [h=4]Windows installer is not compatible with Windows 8 or UEFI firmware, and is not available for Ubuntu 13.04.[/h]

[http://www.ubuntu.com/download/desktop/install-ubuntu-with-windows](http://www.ubuntu.com/download/desktop/install-ubuntu-with-windows)

Windows installer = Wubi.

---

### Post by dino99 on 2013-05-24
Wubi has been removed from the archive (at least Saucy archive)

[http://www.omgubuntu.co.uk/2013/04/wubi-unlikely-to-be-in-ubuntu-13-04-windows-users-lose-out](http://www.omgubuntu.co.uk/2013/04/wubi-unlikely-to-be-in-ubuntu-13-04-windows-users-lose-out)

---

### Post by cdoebbler on 2013-05-24
I have tried a clean install with four different versions of Ubuntu but none work. The farthest I have gotten is with Wubi...at least it seems to get the operating system on the machine. I don't know what there is (a lock, UEFI, or a hidden secure boot) but every time I try to boot from a USB the computer just by-passes the USB and boots Windows. In Windows the USB is recognized and I even appear to be able to load Ubuntu on to my harddisk via Wubi, but if I try to boot from the USB it is not recognized. I even set the bios to boot to only from USB and then it does bypass windows, but only goes to the bios again...apparently still not recognizing the USB drive and telling me to re-install windows 8.

---

### Post by cdoebbler on 2013-05-24
I am not sure Wubi is not compatible. It seems to have an issue with the image of Ubuntu it puts on the harddrive, but it does seem to put and iso on the harddrive. I have gotten further with Wubi on this Asus then I have with any other iso, including, of course, trying clean boots with each of the versions (12.04.2, 12.10, 13.04 or 13.10). 

PS - By the way I run 13.10 on another machine and it works pretty good, although I recognize it is in development there do not seem to be any kinks in installing it.

PSS - I would change the tread title to "Re: Installing Ubuntu 12.04 or 12.10 or 13.04 or 13.10 with Windows 8 on Asus Vivobook (A400C)" if I could.

---

### Post by Bucky Ball on 2013-05-24
Your wish is my command. Thread title changed. It only appears on the first post, not the rest, but the new title is what will appear when people see it on the forum lists. 

If the USB is recognisable in Windows and boot Wubi fine but won't boot when you install 12.04 or the others, I'd imagine it is skipping over the USB because it can't find anything bootable on the USB. How are you creating the USB installer? The problem may lie there as the machine is not seeing the USB as bootable media. Wubi is a different kettle of fish so installing Wubi vs installing Ubuntu to it's own partition from bootable media are not comparable.

---

### Post by ventrical on 2013-05-24
> **cdoebbler said:**
> Thanks but tread is irrelevant as it is about creating USB ISO which I have done fine. I can boot from it on my HP Mini100c running Ubuntu 12.10, but not on the i5 Windows machine.


Try burning the .iso image to DVD and then boot from there. I know it is waste of a DVD .. but you can try it.

Edit:

Sorry .. does not have a DVD !  ;(

---

### Post by ventrical on 2013-05-24
> **Bucky Ball said:**
> Your wish is my command. Thread title changed. It only appears on the first post, not the rest, but the new title is what will appear when people see it on the forum lists. 

If the USB is recognisable in Windows and boot Wubi fine but won't boot when you install 12.04 or the others, I'd imagine it is skipping over the USB because it can't find anything bootable on the USB. How are you creating the USB installer? The problem may lie there as the machine is not seeing the USB as bootable media. Wubi is a different kettle of fish so installing Wubi vs installing Ubuntu to it's own partition from bootable media are not comparable.


The op said :

"
Created it using Ubuntu download and Windows 8 ISO burner and checksum matched fine. 				"

Which I think would be a problem right off .. but the OP also said that the USB boots fine on other PCs

---

### Post by cdoebbler on 2013-05-24
I have tried clean install with iso downloaded from Ubuntu.com and Wubi. On clean install Windows just bots by-passing USB, even when I go to bios and set boot from USB. On Wubi Ubuntu installs (versions 12.04 to 13.04...there is no Wubi support for 13.10 hat I can see) and even gives me Windows' dual boot screen, but then when I try to boot from dual boot screen I get error message as reported above. For some reason this machine just does not want to boot Ubuntu from a USB. 

I will try digging up an old external CD/DVD player/burner I think I still have and see if that works, but any help on USB would still be welcome.

---

### Post by cariboo on 2013-05-24
I'd suggest you stop trying to install using wubi, as it will never work, as wubi isn't compatible with Windows 8. You can check the [Ubuntu-dev mailing list ]("https://lists.ubuntu.com/archives/ubuntu-devel/2013-April/036993.html")for more details

---

### Post by Bucky Ball on 2013-05-24
> **cariboo907 said:**
> I'd suggest you stop trying to install using wubi, as it will never work, as wubi isn't compatible with Windows 8. 

+1. As mentioned, forget Wubi.

---

### Post by serdotlinecho on 2013-05-25
Google is your friend :)

[Ubuntu Asus Vivobook]("https://www.google.com.my/search?q=ubuntu+Asus+Vivobook&client=ubuntu&channel=cs&aq=f&oq=ubuntu+Asus+Vivobook&aqs=chrome.0.57j60j62.2025j0&sourceid=chrome&ie=UTF-8#client=ubuntu&channel=cs&sclient=psy-ab&q=ubuntu+asus+vivobook&oq=ubuntu+asus+vivobook&gs_l=serp.3..0l2j0i8l7.6901.9194.1.9451.4.4.0.0.0.0.181.636.0j4.4.0...0.0...1c..14.serp.wX9CByp4s28&psj=1&bav=on.2,or.r_qf.&bvm=bv.47008514,d.bmk&fp=99a4970a7ff8579a&biw=1024&bih=516")

---

### Post by cdoebbler on 2013-05-25
Thanks for the link, but all I found was a bunch of people admitting defeat. I cannot believe Ubuntu does not run dual-boot on the Asus A400C Vivobook with Windows 8 pre-installed. If I missed something please correct me.

---

### Post by sudodus on 2013-05-25
Ask the vendor or ask Asus (or if there is an asus web forum, ask about it there). Ask for example how to boot into another mode than UEFI or how to install dual boot Windows 8 and linux.

Or wait until *oldfred* is back from his vacation. I'm afraid we have no solution for you at this moment.

---

### Post by Bucky Ball on 2013-05-25
Or start doing some research in preparation:

[http://www.dogpile.com/info.dogpl.t8.1/search/web?fcoid=417&fcop=topnav&fpid=27&q=install+ubuntu+uefi&ql=](http://www.dogpile.com/info.dogpl.t8.1/search/web?fcoid=417&fcop=topnav&fpid=27&q=install+ubuntu+uefi&ql=)

---

### Post by cdoebbler on 2013-05-25
Okay thanks for the replies and the efforts to help.

---

### Post by cdoebbler on 2013-05-26
Tried installing using external DVD with Ubuntu 12.04.2, but this is not recognized either at attempted boot...although DVD drivers installed. Windows 8 just seem to ignore any other boot OS and boot to Windows 8 on this machine. Asus seems to have really built a brick.

---

### Post by GuenterErde on 2013-05-26
only thing i could think is - on a lot of newer motherboards, it identifies all USB drives as standard drives (at least as far as booting is concerned). With the USB stick plugged in, change your boot order, and if it allows you to define what you mean by HDD, change it to the USB drive. Did it for me.

---

### Post by cdoebbler on 2013-05-27
Asus support (although they say they can't help with Linux/Ubuntu issues) tells me that the blocking of another operating system is hardwired into the motherboard? When I suggested that this might be illegal (violating European competition law) their reply was, I thought you were in the US and we can't tell you more. Has any one ever heard of a publicly available machine being hardwired to reject other operating systems?

---

### Post by cdoebbler on 2013-05-27
After booting with F9 and waiting about an hour for all drives to be reset, I tried adding a boot path using the USB and then SD card path...again paths ignored at boot and boots to Windows 8 or, if I only leave USB or SD card path, boots to blue screen with 00xc0000098 error.

---

### Post by ventrical on 2013-05-27
> **cdoebbler said:**
> Asus support (although they say they can't help with Linux/Ubuntu issues) tells me that the blocking of another operating system is hardwired into the motherboard? When I suggested that this might be illegal (violating European competition law) their reply was, I thought you were in the US and we can't tell you more. Has any one ever heard of a publicly available machine being hardwired to reject other operating systems?



Just google :

   microsoft partnership with asus 

...and enjoy.

so you know that they burned proprietary safeguards into the firmware! .. and trade secrets are not illegal until proven  that they  break competition act rules..


  Uhhh.. I am wondering if you can boot from  PLOP Bootloader CD on your usb dvd drive.

---

### Post by ventrical on 2013-05-27
> **cdoebbler said:**
> Asus support (although they say they can't help with Linux/Ubuntu issues) tells me that the blocking of another operating system is hardwired into the motherboard?

 It does not have to be the motherboard per se. It can just be a component leased out by an OEM. So .. eg; microsoft can buy licensing rights to a component (on the motherboard) that makes that particular piece of hardware exclusive to the OEM.


[http://www.microsoftstore.com/store/msusa/en_US/pdp/productID.259232900](http://www.microsoftstore.com/store/msusa/en_US/pdp/productID.259232900)

---

### Post by ventrical on 2013-05-27
enable Launch CSM in BIOS ??

[http://askubuntu.com/questions/252744/asus-x202e-vivobook-dual-boot-how-to-get-around-uefi-and-have-win8-ubuntu](http://askubuntu.com/questions/252744/asus-x202e-vivobook-dual-boot-how-to-get-around-uefi-and-have-win8-ubuntu)

---

### Post by cdoebbler on 2013-06-02
No can't boot from PLOP Bootloader CD.

Yes, of course, you must prove violation of competition laws, but blocking other operating systems through block that cannot be removed through reasonable means and without very good reasons related to public good is a violation of competition law. Recently discus this with several WTO colleagues, including Americans (where both Asus and MS are based) and they agreed.

---

### Post by cdoebbler on 2013-06-02
Enabling CSM in Bios does not make any difference. X202e Vivobook seems to have different Bios/firmware architecture from S400CA Vivobooks.

May they realized they were acting illegal. Asus seems to have changed S400CA architecture pretty quickly.

---

### Post by cdoebbler on 2013-06-02
Burning propriety 'safeguards' (blocks against other operating systems into firmware most likely violates international competition laws agreed by US unless it is very clearly advertised to consumers. In this case neither Microsoft or Asus advertised such restrictions.

Note when I reported this an international organization I consult with Asus was put on watch list, which essentially mans they won't buy from them...because their lawyers thought their equipment may violate international free trade rules. A small victory for open-source software.

---

### Post by dino99 on 2013-06-02
Looks like it can be installed :p  [https://plus.google.com/113812399853448537673/posts/AZLkDhtWZEu](https://plus.google.com/113812399853448537673/posts/AZLkDhtWZEu)

---

### Post by Bucky Ball on 2013-06-02
> **dino99 said:**
> Looks like it can be installed :p  [https://plus.google.com/113812399853448537673/posts/AZLkDhtWZEu](https://plus.google.com/113812399853448537673/posts/AZLkDhtWZEu)

Yes, but how? Also, that is a picture of an *_S400C_*, not an A400C, laptop running Ubuntu and that's it. I can see no instructions on how to install it. Am I missing something?

But yes, it proves it can be done. Somehow ...

The issue here is about getting around the Windows 8 issues which oldfred would able to advise on definitively if he were about but he's not at the moment.

You may get some joy here (read through but post #7):

[http://ubuntuforums.org/showthread.php?t=2116971&p=12521651#post12521651](http://ubuntuforums.org/showthread.php?t=2116971&p=12521651#post12521651)

... or here:

[http://askubuntu.com/questions/252744/asus-x202e-vivobook-dual-boot-how-to-get-around-uefi-and-have-win8-ubuntu](http://askubuntu.com/questions/252744/asus-x202e-vivobook-dual-boot-how-to-get-around-uefi-and-have-win8-ubuntu)

... or dig through anything related to UEFI issues. Good luck.

---

### Post by oldos2er on 2013-06-02
> **cdoebbler said:**
> Note when I reported this an international organization I consult with Asus was put on watch list, which essentially mans they won't buy from them...because their lawyers thought their equipment may violate international free trade rules. A small victory for open-source software.

Thread has gone far off topic, so closed.

---

