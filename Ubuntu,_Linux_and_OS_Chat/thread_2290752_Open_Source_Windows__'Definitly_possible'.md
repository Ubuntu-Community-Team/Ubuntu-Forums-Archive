---
title: "Open Source Windows : 'Definitly possible'"
date: 2015-08-14
forum: Ubuntu, Linux and OS Chat
---

### Post by night_sky2 on 2015-08-14
I just wanted to share this very interesting article.

[http://www.wired.com/2015/04/microsoft-open-source-windows-definitely-possible/](http://www.wired.com/2015/04/microsoft-open-source-windows-definitely-possible/)


Do you think Microsoft will open source Windows at some point, giving it away for free?

---

### Post by tgalati4 on 2015-08-15
Yes, when nobody wants it and there are no more devices being produced that it will run on.

---

### Post by night_sky2 on 2015-08-15
> **tgalati4 said:**
> Yes, when nobody wants it and there are no more devices being produced that it will run on.
MS is no longer at war with Linux. It embraces it. It's time to move on from that old feud.

[IMG]http://blogs.technet.com/resized-image.ashx/__size/550x0/__key/communityserver-blogs-components-weblogfiles/00-00-00-41-57/ms_5F00_loves_5F00_linux.png[/IMG]
Source: [http://blogs.technet.com/b/windowsserver/archive/2015/05/06/microsoft-loves-linux.aspx](http://blogs.technet.com/b/windowsserver/archive/2015/05/06/microsoft-loves-linux.aspx)

---

### Post by monkeybrain20122 on 2015-08-15
> **night_sky2 said:**
> MS is no longer at war with Linux. It embraces it. It's time to move on from that old feud.

[IMG]http://blogs.technet.com/resized-image.ashx/__size/550x0/__key/communityserver-blogs-components-weblogfiles/00-00-00-41-57/ms_5F00_loves_5F00_linux.png[/IMG]
Source: [http://blogs.technet.com/b/windowsserver/archive/2015/05/06/microsoft-loves-linux.aspx](http://blogs.technet.com/b/windowsserver/archive/2015/05/06/microsoft-loves-linux.aspx)

I hope this is tongue in cheek. Secure boot?

---

### Post by mystics on 2015-08-15
Microsoft will only do it if they can profit off of it. Android has worked for Google because they can use it to push things like Google Search and GMail. In that case, putting out a mostly open source OS has worked very well for them, but Android itself also isn't Google's primary revenue stream. Microsoft isn't in that position at the moment, so I'd imagine we'll see them finding other ways to profit off of other open source technology, such as allowing Linux on Azure, until then. That said, they definitely seem to be setting themselves up to try to pull that off, so I don't doubt that it is a possibility they want to leave open for the future. But at the same time, they are a company, so they are going to put profitability above all else. Whether or not that eventually leads to an open source (or mostly open source) Windows is something we'll have to wait and see.

---

### Post by night_sky2 on 2015-08-15
> **monkeybrain20122 said:**
> I hope this is tongue in cheek. Secure boot?

UEFI Secure boot is intended as a security feature to make sure the UEFI firmware only execute signed UEFI applications. So that malware and rootkits are refused. Technology evolve and so do PC manifacturers. Secure boot is quite useful and not intended to ''locked-out'' Linux in any way. As a matter of fact, Debian, Ubuntu, Mint, Fedora, OpenSUSE, Red Hat all support Secure Boot.

---

### Post by grahammechanical on 2015-08-15
I really do not see the point of doing that. Now, if Microsoft was to fully comply with certain Open Document formats that made it easier for other people's programs to export and import to & from Microsoft programs, then that would be something. It would also be something if Microsoft was fully open about all the Windows APIs so that other people's programs worked just as well on Windows as Microsoft's own programs.

I really do not know if it is true today, but years ago Microsoft was able to lock in users to its OS and programs by having its own document formats and being secretive about the APIs.

Regards.

---

### Post by monkeybrain20122 on 2015-08-15
> **night_sky2 said:**
> UEFI Secure boot is intended as a security feature to make sure the UEFI firmware only execute signed UEFI applications. So that malware and rootkits are refused. Technology evolve and so do PC manifacturers. Secure boot is quite useful and not intended to ''locked-out'' Linux in any way. As a matter of fact, Debian, Ubuntu, Mint, Fedora, OpenSUSE, Red Hat all support Secure Boot.

Yeah right with due respect are you drunk on MS's cool-aid? First of all it is not secure boot perse but who hold the key. I don't know about Debian but the others 'support' secure boot because they pay for a MS key. Well why should they (and even with that it is not problem free)? Secondly most Windows machines got infected AFTER booting into Windows, not at boot. It is a way to lock down hardware and restrict users' control. MS has  a long history of that, just google trusted computing.

---

### Post by night_sky2 on 2015-08-15
> **monkeybrain20122 said:**
> Yeah right with due respect are you drunk on MS's cool-aid?
No, I am just not on the bashing team. ;)
But yeah, I am a fan of their products and appreciate the new direction the Redmond Firm is going. I don't see why I should hide that fact because I am using Linux Ubuntu as my OS of choice.

As a matter of fact, Canonical and Microsoft are now official partners for Azure and the Internet of Things (IoT)
[https://insights.ubuntu.com/2015/03/10/microsoft-canonical-demonstrate-first-fully-automated-ocp-deployment/](https://insights.ubuntu.com/2015/03/10/microsoft-canonical-demonstrate-first-fully-automated-ocp-deployment/)
[URL="http://www.zdnet.com/article/canonical-and-microsoft-working-together-on-containers/"]http://www.zdnet.com/article/canonical-and-microsoft-working-together-on-containers/
http://www.zdnet.com/article/canonical-partners-with-amazon-microsoft-and-others-on-internet-of-things/[/URL]

 > **monkeybrain20122 said:**
> First of all it is not secure boot perse but who hold the key. I don't know about Debian but the others 'support' secure boot because they pay for a MS key. Well why should they (and even with that it is not problem free)? Secondly most Windows machines got infected AFTER booting into Windows, not at boot. It is a way to lock down hardware and restrict users' control. MS has  a long history of that, just google trusted computing.
Ok, they paid a one-off 99$ for a VeriSign key. Big deal.

Secure Boot is, as the names says, more secure. I don't see why PC manifacturers shouldn't make use of this technology. Rootkit attacks have elvolved in recent years and they can now target the firmware and mess up with the boot process. The only way to tackle this threat efficently is to implement a mechanism that will deny them access.
For more: [http://www.uefi.org/sites/default/files/resources/UEFI_Secure_Boot_in_Modern_Computer_Security_Solutions_2013.pdf](http://www.uefi.org/sites/default/files/resources/UEFI_Secure_Boot_in_Modern_Computer_Security_Solutions_2013.pdf)

I know some people want to see a MS conspiracy no matter what (actually they had to pay for their own VeriSign key.. :-\") but that's just not why UEFI Secure Boot has been embraced in the first place. Such a feature can also be turned off in most cases so far (plenty of tutorials online) with basic computer knowledge. For Windows 10, PC manifacturers will decide for themselves if they want it to be turned on/off and while that may indeed be concerning for the Linux community as a whole, it's the hardware manifacturers you should go after, not MS. The choice  has been given to them. Not all OEMS may have the 1.5% of Linux users in mind, that's true. But in any case, the big Linux distributions will continue to be supported as usual on Windows-certified computers.

---

### Post by bcschmerker on 2015-08-16
I found out through the [Ubuntu® Group at Google+®]("https://plus.google.com/communities/107299007624972266094") that the Battelle Memorial Institute has discovered a core problem with all Intel® Pentium Processors®, Xeon Processors®, Core Processors&#8482;, and Atom Processors&#8482;:  [Secure Management Mode]("http://ruggedgamers.com/new-rootkit-exploit-discovered-affects-all-intel-smm-enabled-x86-cpus/"), which dates back to 1994 and the N80386SL, has a vulnerability to rootkits that may not be fixable short of hardware redesign for the 6th-Generation Core Processors&#8482;, 3rd-Generation Atom Processors&#8482;, and 9th-Generation Xeon Processors® to address the bugs involved.  Same could very well hold true for the Advanced Micro Devices® Athlon®, Sempron®, Phenom® and FX-Series Processors and E- and A-Series APU's.  In this context, SecureBoot, introduced with Unified Extensible Firmware Interface 2.3.1, is a band-aid on the core problem with the master processing units listed above.

Were I porting software to the Microsoft® Surface&#8482; tablet computers, I'd most definitely want the C headers for driver and interrupt access, as Windows® RT&#8482; (designed for the nVIDIA® TEGRA&#8482; Accelerated Processing Units, which are not affected by the critical SMM hardware bug) was ill-supported for user applications at last check.

---

### Post by mörgæs on 2015-08-16
The fact that some distros have bought the key to Restricted Boot does not indicate that they have done so voluntarily nor that they 'embrace' the idea. They are simply forced to do so because one company dictates how hardware is going to be built. 

As long as GNU/Linux has a small market share nothing will happen but if it gains popularity the keys will be delayed, denied or sold for a huge fee.  

The hardware manufacturers have only a limited say in the game. Bullying GNU/Linux does not increase hardware sales so why should they do so on their own?

---

### Post by coldraven on 2015-08-16
> Secure Boot is, as the names says, more secure.
Not necessarily! Read this : [http://www.theregister.co.uk/2015/08/12/lenovo_firmware_nasty/](http://www.theregister.co.uk/2015/08/12/lenovo_firmware_nasty/)

---

### Post by night_sky2 on 2015-08-16
> **mörgæs said:**
> As long as GNU/Linux has a small market share nothing will happen but if it gains popularity the keys will be delayed, denied or sold for a huge fee.  
That's an assumption which I don't think has any basis in reality. The keys are provided by VeriSign (MS receives no money) and their price do not fluctuate because of an OS popularity. With a key you can also sign as many binaries as you want. I am not sure why some people makes such a big deal with that.

Chances are if GNU/Linux gain more popularity on the desktop, distros will be selling their own certified computers - in partnership with OEMs - on a much larger scale than it currently does. 

> **mörgæs said:**
> The hardware manufacturers have only a limited say in the game. Bullying GNU/Linux does not increase hardware sales so why should they do so on their own?
There are hardware manifacturers who simply don't care about Linux. In their views, they are selling Windows-licensed computers and Linux Oses are not even on the back of their mind.

That's a reality we have to deal with as Linux users. Microsoft doesn't tell them ''PLease, you must prevent Linux from booting!!''. If an OEM do such a thing then the Linux Community should boycut that particular hardware manifacturer. From Microsoft's perspective, if some customers decide to boot Linux, than fine, maybe they will use some of their products anyway, but they are not gonna actively push users away from the Windows OS. We all know that. Since Windows 10, the decision to add a Secure Boot switch on/off is now left entirely in the hands of the PC manifacturers.

---

### Post by night_sky2 on 2015-08-16
> **coldraven said:**
> Not necessarily! Read this : [http://www.theregister.co.uk/2015/08/12/lenovo_firmware_nasty/](http://www.theregister.co.uk/2015/08/12/lenovo_firmware_nasty/)

Thankfully there is now a fix for the LSE functionality and has been removed from new systems. UEFI Secure Boot is more secure but that doesn't mean ''total security''. There are no such things.

---

### Post by monkeybrain20122 on 2015-08-17
> **night_sky2 said:**
> That's an assumption which I don't think has any basis in reality. 

Oh yeah, then your reality must be different from mine. It must feel cozy to live in a  parallel universe where MS has a track record of honesty and benevolence and none of the nasty patent trolling, bullying,  blackmailing, embrace extinct, attempts to subvert open standards, monopolistic practices and other predatory tactics.


> The keys are provided by VeriSign (MS receives no money) and their price do not fluctuate because of an OS popularity. With a key you can also sign as many binaries as you want. I am not sure why some people makes such a big deal with that.

Whether MS receives money is besides the point. I am sure whether $0.99, $9.9, $99 or $999 it is less than loose change to MS. The point is that whether you can boot your OS on your machine depends on MS's discretion. It can revoke the key with some BS 'security' excuses any time. This is power and MS shouldn't have it. 

> Chances are if GNU/Linux gain more popularity on the desktop, distros  will be selling their own certified computers - in partnership with OEMs  - on a much larger scale than it currently does. 


The user should be able to decide what can boot. Not distro makers or MS, period. It has nothing to do with market share. I would be  equally unhappy if Ubuntu OEMs such as system76 don't allow users to boot other flavours of Linux (e.g Arch) without a key from Canonical.

Maybe you don't have an issue that the house builder puts locks on your house and keeps the keys from you because of 'security' (as in maximum security prison) as long as the house has enough shiny toys and cool furniture to distract you from the fact that you are in fact in jail. But many people would have a problem if they know what happen.

> There are hardware manifacturers who simply don't care about Linux. In their views, they are selling Windows-licensed computers and Linux Oses are not even on the back of their mind...That's a reality we have to deal with as Linux users. Microsoft doesn't tell them ''PLease, you must prevent Linux from booting!!''. If an OEM do such a thing then the Linux Community should boycut that particular hardware manifacturer. From Microsoft's perspective, if some customers decide to boot Linux, than fine, maybe they will use some of their products anyway, but they are not gonna actively push users away from the Windows OS. We all know that. Since Windows 10, the decision to add a Secure Boot switch on/off is now left entirely in the hands of the PC manifacturers.

MS is not stupid. If it tells OEM explicitly it will be sued. But by making secure boot mandatory and not requiring OEM to provide a way to turn off it will create a situation that some will not provide one (how many remains to be seen)and MS knows that too. It doesn't lock out only Linux but makes these laptops basically unrepairable so you will have to get a new one and pay more $$ to MS if it gets hit with a nasty virus and needs to boot a rescue cd or something to fix (not to mention the environmental cost) 

MS can get away by mandating secure boot impossible to disable in arm devices because mobiles are considered special purpose devices, but general purpose computers have a different history and people have different expectations. It is clear that MS's goal is to turn generic PC's into locked down special purpose devices just like mobile in a creeping fashion. If it gets no resistance it will push a bit further, then a bit further until one day the PC is completely locked down and you need to be a heavy duty hacker to install Linux (and probably illegal)  if it succeeds it would be in not a small part because of complacent people.

Google Trusted Computing. UEFI secure boot is basically a reincarnation of that, but more stealthy since the first attempt failed because it was too brazen and met with huge resistance.

---

### Post by ian-weisser on 2015-08-18
> **night_sky2 said:**
> Do you think Microsoft will open source Windows at some point, giving it away for free?

Microsoft is giving away Windows 10 so it's customers and partners will forgive them for the  lousy Windows 8, not because of price pressure from Linux. Many Windows  customers use software that *only* works on Windows. Most retail customers purchase Windows pre-installed - it's currently in MIcrosoft's best interest to keep it that way...so the retail price (including zero) is irrelevant.
It's about keeping that market share and market-shaping control. It's about keeping Software partners, OEMs, and large customers who are looking at non-Windows alternatives invested in the Windows ecosystem.

I don't see any benefit to Microsoft's profitability by open-sourcing Windows.

---

### Post by night_sky2 on 2015-08-18
> **ian-weisser said:**
> **Microsoft is giving away Windows 10 so it's customers and partners will forgive them for the  lousy Windows 8**, not because of price pressure from Linux. Many Windows  customers use software that *only* works on Windows.
I guess we will see if they do the same with Windows 11 or whatever else the next version will be called. Chances are it has become the norm rather than the exception as people are reluctant to pay for OSes, let alones Oses upgrades as they once did. OSX is free, iOs and Android are free I mean what the heck! It's just the trend we are seeing. MS makes the bid that by bringing the masses on it's newest platform, they will still use some of their products and can probably still monetize the Windows with OEMS, enterprises and by collecting aggregated data.

---

### Post by mystics on 2015-08-18
> **night_sky2 said:**
>  OSX is free, iOs and Android are free I mean what the heck!

At the same time, though, Apple and Google each have different focuses than Microsoft. Apple is mostly concerned with hardware, App Store, and iTunes sales. Google is mostly concerned with selling data and also likely gets a lot from things like the Google Play Store. Microsoft, on the other hand, has traditionally relied on sales of software like Windows and Microsoft Office.

That said, Microsoft does seem to be shifting their business model to rely more on things like selling data and subscriptions. Still, it is hard to tell at this point if they will be profitable enough in that area to warrant making Windows free. At the very least, they are currently nowhere near as established there as Google is, and only time will tell if they get established enough in that area that they are as comfortable making Windows free as Google is making Android free.

---

### Post by ian-weisser on 2015-08-18
> **night_sky2 said:**
> MS makes the bid that by bringing the masses on it's newest platform, they will still use some of their products and can probably still monetize the Windows with OEMS, enterprises and [....]

A highly successful and profitable strategy for them for 20 years so far. I'm not seeing a significant change

I don't see the giveaway to existing licensees as a significant change. Most Windows users purchase new pre-installed systems, which generates revenue for Microsoft.

---

### Post by night_sky2 on 2015-08-18
> **ian-weisser said:**
> A highly successful and profitable strategy for them for 20 years so far. I'm not seeing a significant change
When the top engineer of Windows mention publicly that an open source Windows is now *definitly possible, *that to me is a significant change in rethoric.
The old guard is gone from the Redmond Firm or not in a position of power any longer. Changes of manners and ways of doing things have already happened and no doubt more are coming.

What we are seeing is the top management at Microsoft now looking 'outside the Windows box'. Microsoft wants to be more like Google. Developpers are now allowed to reach users on other platforms such as Android, iOS, OSx and even Linux (Azure LXD, Skype, cloud-based services such as Outlook, Office Web Apps, OneDrive, Groove ect.).

It's realistic to consider that at some point, MS will no longer need a paid, closed source Windows, especially as the developpers are very much aware of the benefits of the open source and that OS license fees are becoming harder to sell. MS's ecosystem can also sustain itself, without a paid OS. Plus, the desktop is no longer the primary way many people are using a computer these days.

Microsoft would still make money from an open source Windows. Enterprises still need support regardless if the code is open or closed.

---

### Post by neu5eeCh on 2015-08-21
Just my 1 5/8 cents, but I'm having a hard time seeing what MS would gain by open sourcing their OS. I agree with other users who suggest that MS is creating a model in which all their software is lease/subscription based. And if they want even a minimally walled garden, I'm not sure how open sourcing would help them (without severe license restrictions). They wouldn't, for example, want forks of their OS.

---

### Post by rebusgadfly on 2015-08-22
I'm middle aged and I don't see Windows open source in my lifetime. They are a business and not a community. It would take a major paradigm shift  for microsoft to open up.

---

### Post by sol8712 on 2015-08-23
All I can imagine from open  source windows is how much people here are gonna tear it to shreds like a pack of hungry hobos,  discard and change the 90% of Windows thats garbage and port the 10% of awesomeness to their favorite Linux distro. Then Linux domination will be complete.

Now if M$ ported the good from Windows to their own version of Linux then they might be able to stay on top of the game.

---

### Post by night_sky2 on 2015-08-24
> **rebusgadfly said:**
> I'm middle aged and I don't see Windows open source in my lifetime. They are a business and not a community. It would take a major paradigm shift  for microsoft to open up.
Google is a tech giant too and they use the open source as way of developping some of their products. Chromium, Android, Chrome OS...
And one could argue that Windows already has a strong community of users. The open source has many advantages in terms of security, bug fixes ect since the code is available for review.

BTW, Microsoft already has open source projects on Github.

.Net: [https://github.com/Microsoft/dotnet](https://github.com/Microsoft/dotnet)

WinObjC (tool to port iOS apps to Windows): [URL="https://github.com/Microsoft/dotnet"]https://github.com/Microsoft/dotnet

full list: [https://github.com/Microsoft](https://github.com/Microsoft)

[/URL]The paradigm shift has already begun under Nadella.

---

### Post by monkeybrain20122 on 2015-08-24
> **night_sky2 said:**
> Google is a business too and use they the open source as way of developping some their products. Google Chrome, Android, Chrome OS...

BTW, Microsoft already has open source projects on Github.

.Net: [https://github.com/Microsoft/dotnet](https://github.com/Microsoft/dotnet)

WinObjC (tool to port iOS apps to Windows): [https://github.com/Microsoft/dotnet](https://github.com/Microsoft/dotnet)

Because .dotnet is kind of dead. MS is migrating away from it itself. Adobe may one day open source flash when the whole net has gone html5.

---

### Post by RichardET on 2015-08-28
> **rebusgadfly said:**
> I'm middle aged and I don't see Windows open source in my lifetime. They are a business and not a community. It would take a major paradigm shift  for microsoft to open up.

In 1995, you could have made the same claim about Solaris.

---

### Post by RichardET on 2015-08-28
> **sol8712 said:**
> All I can imagine from open  source windows is how much people here are gonna tear it to shreds like a pack of hungry hobos,  discard and change the 90% of Windows thats garbage and port the 10% of awesomeness to their favorite Linux distro. Then Linux domination will be complete.

Now if M$ ported the good from Windows to their own version of Linux then they might be able to stay on top of the game.

Linux already is the dominant player within the UNIX community.  No one cares about Solaris, AIX, HP-UX, SCO anymore.

Scott McNeely and Bill Joy must "hate" Torvalds.  Sun openly shat on Linux until they were forced to open up Solaris, and by then, it was too late.

---

### Post by mystics on 2015-08-28
> **night_sky2 said:**
> Google is a tech giant too and they use the open source as way of developping some of their products. Chromium, Android, Chrome OS...

BTW, Microsoft already has open source projects on Github.

.Net: [https://github.com/Microsoft/dotnet](https://github.com/Microsoft/dotnet)

WinObjC (tool to port iOS apps to Windows): [https://github.com/Microsoft/dotnet](https://github.com/Microsoft/dotnet)

A couple things to consider about Google compared to Microsoft:
1. Google has traditionally relied on selling data, not software. Microsoft's primary revenue stream is still Windows sales.

2. (This one is more important) Microsoft is *the* dominant player in the OS market already. Google wasn't the dominant player in the industry when they gave us things like Android and Chrome OS. Google's concern was with getting into a market, not trying to capture the 5% of people they didn't already own and who may not have switched anyways due to needing to learn something new. Windows, as of right now, has virtually no competition when it comes the desktop OS.

Simply put, Microsoft is in a position right now to earn a ton of money from selling Windows to the still 85%+ share Windows has in the market *and* earning money off of their new attempts to be like Google and sell data. There is little, if any, incentive right to make Windows open source. Even if Microsoft does make selling data their primary revenue stream, which they probably would like, there's still little reason to cut off the money they make from selling Windows in a market where it is still by far the most dominant OS. Making it open source, as of right now, is probably more a worst-case-scenario plan for them.

At this point, I'd imagine Microsoft is mostly talking about open sourcing things like Windows simply to avoid completely cutting off open source communities and to capitalize on a popular buzzword going around. And don't get me wrong, I would *love* it if Windows went open source. That would be better for everyone, and I'm saying that as someone who is unlikely to use it much given that I'm significantly more comfortable in UNIX-like environments. However, Microsoft is a company, and it is best to remember that companies are designed first around being as profitable as they can, and until things like OS X, Chrome OS, Steam OS, and Ubuntu and other Linux distros make a serious cut into Windows' market share, Microsoft will never be as profitable as it could be by open sourcing Windows. 

In short, we can be optimistic and hopeful for an open-source Windows, but I think it's best to avoid giving Microsoft too much credit before they actually back this up with actions.

---

### Post by Bucky Ball on 2015-08-28
Does Microsoft Word allow .odt files yet? That's all I care about. :D

I don't care what OS people use or whether MS goes open-source, but I do care about proprietary file types and partition filesystems. They should be outlawed. Making them cross-platform and universal would definitely be a step towards making life easier. 

If 85% of people are using MS, the least MS could do is allow their users the ability to access documents from the other 15% with ease. An .odt won't open on a Windows system and the Win user will claim its Linux's fault and therefore Linux must be rubbish. Sheesh, what a world.

---

### Post by buzzingrobot on 2015-08-28
I can't see how Microsoft could make money trying to sell an open sourced Windows, at least if it wears the usual FOSS licenses. As far as I know, no one else has ever sustained a business selling open source software:  Five minutes after you start selling, someone else has built that open source and is giving your product away.

Microsoft could release the source code under a "don't rebuild this and don't redistribute executables" license. That would not deter anyone running a Chinese factory cranking out PC's running those executables.

Chances of a release of source code from a DOS-based Windows are probably greater, once it has aged sufficiently to be technically inconsequential.

---

### Post by night_sky2 on 2015-09-10
> **buzzingrobot said:**
> I can't see how Microsoft could make money trying to sell an open sourced Windows, at least if it wears the usual FOSS licenses. As far as I know, no one else has ever sustained a business selling open source software:  Five minutes after you start selling, someone else has built that open source and is giving your product away.
Unless they no longer *need* to make money with it, that's the point. Google does not need to charge a license fee for Android or Chrome OS. Apple does not need to charge for OSX or iOS.

You become the product in one's compagny ecosystem. That's how they monetize the whole thing.

---

### Post by RichardET on 2015-09-11
> **night_sky2 said:**
> Unless they no longer *need* to make money with it, that's the point. Google does not need to charge a license fee for Android or Chrome OS. Apple does not need to charge for OSX or iOS.

You become the product in one's compagny ecosystem. That's how they monetize the whole thing.



No wonder Google does not have to charge for Android - its a Linux rip-off.

---

### Post by RichardET on 2015-09-11
> **night_sky2 said:**
> I just wanted to share this very interesting article.

[http://www.wired.com/2015/04/microsoft-open-source-windows-definitely-possible/](http://www.wired.com/2015/04/microsoft-open-source-windows-definitely-possible/)


Do you think Microsoft will open source Windows at some point, giving it away for free?

It is already "free" - on every *new* computer sold in the USA, essentially.

---

### Post by CantankRus on 2015-09-11
In my opinion Microsoft's implementation of secure boot was more about taking ownership of the PC 
and stifling interest in linux by making it much more complicated for the curious to dual boot.
Next step... let everyone upgrade to 10 for free whereby through forced updates your PC will gradually 
transform into a personal data miner and advertising platform. :-k 8-[

---

### Post by Bucky Ball on 2015-09-11
> **CantankRus said:**
> 
... forced updates your PC will gradually transform into a personal data miner and advertising platform. :-k 8-[

That has pretty much been the intention from the start, or should I say, at least from when internet arrived and grew and the potential for what you suggest dawned on the bright sparks at MS. Some of the independently written literature from the 90s-early 2000s quotes representatives of MS stating as much, rather proudly I might add.

---

### Post by night_sky2 on 2015-09-11
> **RichardET said:**
> No wonder Google does not have to charge for Android - its a Linux rip-off.
Yep but at the same time, Android is under Google's tight grip. OEMs aren't allowed to take the Google out of the Android. 
The compagny monetize it's share of the mobile world with it's apps and ads, which mine user data and that are sold to third-parties.

[I]''If a company does ever manage to fork AOSP, clone the Google apps, and create a viable competitor to Google's Android, it's going to have a hard time getting anyone to build a device for it. In an open market, it would be as easy as calling up an Android OEM and convincing them to switch, but Google is out to make life a little more difficult than that. Google's real power in mobile comes from control of the Google apps -- mainly Gmail, Maps, Google Now, Hangouts, YouTube, and the Play Store. These are Android's killer apps, and the big (and small) manufacturers want these apps on their phones. Since these apps are not open source, they need to be licensed from Google. It is at this point that you start picturing a scene out of The Godfather, because these apps aren't going to come without some requirements attached.

While it might not be an official requirement, being granted a Google apps license will go a whole lot easier if you join the Open Handset Alliance. The OHA is a group of companies committed to Android -- Google's Android -- and members are contractually prohibited from building non-Google approved devices. That's right, joining the OHA requires a company to sign its life away and promise to not build a device that runs a competing Android fork.''[/I]

See: [http://arstechnica.com/gadgets/2013/10/googles-iron-grip-on-android-controlling-open-source-by-any-means-necessary/](http://arstechnica.com/gadgets/2013/10/googles-iron-grip-on-android-controlling-open-source-by-any-means-necessary/)

I can see a similar future for Microsoft in which Windows is but a platform, open-sourced, where OEMs are required to ship MS apps and the MS store by default.

---

### Post by monkeybrain20122 on 2015-09-11
> **night_sky2 said:**
> Yep but at the same time, Android is under Google's tight grip. Manifacturers aren't allowed to take the Google out of the Android. 
The compagny monetize it's share of the mobile world with it's apps and ads, which mine user data and that are sold to third-parties.

Well the PC has a different history than the phone. This is the difference between general computing and locked down devices just for consuming contents they feed you. I love the word "consumer", which is a subtle but significant change from "user". Windows 10 is a war on general computing and it wants to convert users into passive consumers on traditional general computing platform.

Windows 10 has stooped to a new low with the tracking and spying even by current 'industry's standard'. Win 10 is an  overall push towards a lower bar, If we accept this as the new standard of normalcy it will get worse and eventually it will be the end for General computing (which MS has been trying to accomplish since "Trusted Computing") Yes, I know the clueless (the "consumers") are easily sold on the new shiny and "cool" features, at least that is what MS is counting on. But I expect people on UF to be more aware instead of blindly drinking MS's cool aid.

> I can see a similar future for Microsoft in which Windows is but a platform, open-sourced, where OEMs are required to ship MS apps and the MS store by default.
 
And it is a good thing? BTW, Google services are at least cross platform. MS locks you to Windows and frequently tries to subvert open standards.

Related story
[http://www.ctvnews.ca/sci-tech/digital-privacy-concerns-the-new-normal-as-users-pay-with-personal-information-1.2556421](http://www.ctvnews.ca/sci-tech/digital-privacy-concerns-the-new-normal-as-users-pay-with-personal-information-1.2556421)

The CTV is as mainstream and corporate friendly as you can get. And the Canadian privacy commissioner is looking into possible violation of Canadian law by Win 10.

---

### Post by RichardET on 2015-09-11
The thing is though - you only pay once  - when you buy it.  Keep it a long time.

---

