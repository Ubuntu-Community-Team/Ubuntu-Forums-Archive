---
title: "Proposed end of Ubuntu 32 bit images"
date: 2016-02-04
forum: Ubuntu, Linux and OS Chat
---

### Post by kansasnoob on 2016-02-04
This is so far only proposed, and would only affect Ubuntu. Other flavors would still be able to host and maintain 32 bit (i386) images:

[https://lists.ubuntu.com/archives/ubuntu-devel/2016-February/039161.html](https://lists.ubuntu.com/archives/ubuntu-devel/2016-February/039161.html)

I think it makes sense since they dropped Unity 2-D after Precise. My only concern is how that might affect Edubuntu LTSP thin clients (which use flashback w/metacity), but I'll let the Edubuntu devs do the worrying about that.

---

### Post by sudodus on 2016-02-04
I agree that it makes sense to drop the 32-bit version of standard Ubuntu.

But it is very important to keep the the 32-bit versions of the flavours, at least the light-weight flavours Lubuntu, Xubuntu and Ubuntu Mate, because there are still many 32-bit computers that work well (and need 32-bit linux). We should also keep the 32-bit mini.iso and Ubuntu Server.

---

### Post by qyot27 on 2016-02-04
All I can say is that 32-bit UEFI support better get fleshed out better so we can install 64-bit on those mixed-mode tablets and mini-PCs with newer Atoms based on Silvermont, etc. (like the Z3735F in the Quantum Byte).  Even though trying to run 64-bit Debian on here is pretty unstable and I had to drop to 32-bit for everything so it wouldn't randomly decide to not boot correctly and force me to hard reset.  The only reason I didn't use Ubuntu is because, while the 64-bit image does support mixed-mode and boots just fine into the Live session after you manually add the right bootia32.efi file, it refuses to actually install correctly at this point, and there is no UEFI support on the 32-bit image.


Not that any of that is relevant to what that discussion is really about, but still.  I do have a Pentium III machine that I've generally installed stock Ubuntu on, then pulled in Mate and LXDE, rather than going with one of the alternative flavors where those are immediately available.  It's tradition, but at some point I do realize that switching over to Lubuntu or whatever becomes the relevant 32-bit LXDE flavor/distro is going to become a necessity.

---

### Post by PaulW2U on 2016-02-04
> **kansasnoob said:**
> This is so far only proposed, and would only affect Ubuntu. Other flavors would still be able to host and maintain 32 bit (i386) images:

[https://lists.ubuntu.com/archives/ubuntu-devel/2016-February/039161.html](https://lists.ubuntu.com/archives/ubuntu-devel/2016-February/039161.html)
Missed this. Perhaps this is yet another mailing list that I should join?
> **sudodus said:**
> But it is very important to keep the the 32-bit versions of the flavours, at least the light-weight flavours Lubuntu, Xubuntu and Ubuntu Mate, because there are still many 32-bit computers that work well (and need 32-bit linux). We should also keep the 32-bit mini.iso and Ubuntu Server.
Agreed sudodus.

I'm fully 64-bit here but I see endless posts on these forums of users trying to run various *buntu flavours on ageing PCs which I would long have discarded.

**Edit: **By the way, I've flagged the mailing list post for inclusion in the next issue of the [Ubuntu Weekly Newsletter]("https://wiki.ubuntu.com/UbuntuWeeklyNewsletter") to bring this matter to a larger audience.

---

### Post by The Cog on 2016-02-04
> **sudodus said:**
> But it is very important to keep the the 32-bit versions of the flavours, at least the light-weight flavours Lubuntu, Xubuntu and Ubuntu Mate, because there are still many 32-bit computers that work well (and need 32-bit linux). We should also keep the 32-bit mini.iso and Ubuntu Server.

Absolutely! I'be got a collection of netbooks that all run Xubuntu and can't run 64-bit.

---

### Post by grahammechanical on 2016-02-04
A lot of people think that they can bring new life to old hardware by installing Linux. Well, they can. But not with Ubuntu. In many cases the RAM is not enough & the video adapter is not capable.

Ubuntu of 10 years ago would have run fantastically on the hardware of 10 years ago. The Ubuntu of today runs fantastically on the hardware of today. But people are wrong to think that the Ubuntu of today will run fantastically on the hardware of 10 years ago.

It is good that there are developers who see the need and who are working to meet the need.

Regards.

---

### Post by Irihapeti on 2016-02-04
> **sudodus said:**
> I agree that it makes sense to drop the 32-bit version of standard Ubuntu.

But it is very important to keep the the 32-bit versions of the flavours, at least the light-weight flavours Lubuntu, Xubuntu and Ubuntu Mate, because there are still many 32-bit computers that work well (and need 32-bit linux). We should also keep the 32-bit mini.iso and Ubuntu Server.

Totally agree. I have an EeePC 900 that still works very nicely with a barebones system, and I don't want to have to discard it just yet.

But I also understand the point about standard Ubuntu. It won't run on the EeePC and there's no point in trying.

---

### Post by night_sky2 on 2016-02-04
There are still low-end, x86-based processors being manifactured by Intel. The HP Stream and Acer Cloudbook lines come into mind. These laptops have 2GB of RAM so there is really no point in having a x64 OS in this case, nor will it work. The hardware runs Windows 10 fine. Why not Ubuntu? Besides, the vast majority of software out there are still developped primarily in x86.

Seeing that these budget machines are becoming popular (as they are more efficient than the older 'netbooks'), I don't think it is wise to drop Ubuntu 86x at this point.

---

### Post by kevdog on 2016-02-06
I'm sorry I've read about the discussion on another site?  Why do they want to drop 32 bit support?  It seems like there are probably a lot of people still using this option.

---

### Post by justen_m on 2016-02-07
Yeah, why drop it? As a software engineer, I can understand the cost of building, testing, etc, and I admit I take it for granted with Ubuntu.

I run 32-bit on two ancient systems, my HP server, from 2006, and Acer netbook, from 2008. Both now on 14.04.3LTS, but started with 9.04, IIRC. Both came with XP, but I nuked that partition years ago. The former's Xeon can run 64-bit, but only has 4GB of RAM. The latter's Atom can't run a 64-bit OS. Both run Ubuntu fine. I've been debating whether or not I'll update these systems to 16.04LTS, but is this discussion saying that might not even be an option?  My newer systems are already running 16.04LTS Alpha, and it seems stable.

Not a huge deal. My server is running fine now, but I'd at least like the option, in my head anyway, of running all of my systems on the same OS. I thought that 16.04LTS might have been it. Maybe my old systems will have to be on 14.04 forever?

(Ok, I am going to try upgrading my netbook to 16.04... worst that can happen is I'll have to wipe the drive and restore from a backup drive via clonezilla. It is going to take freaking forever, seeing as it only has wireless G, a slow HD, and a 1.6GHz Atom. I'm curious to see where the bottleneck in the process is. I'm guessing it is the cpu installing all the packages...)

---

### Post by sudodus on 2016-02-07
> **justen_m said:**
> Yeah, why drop it? As a software engineer, I can understand the cost of building, testing, etc, and I admit I take it for granted with Ubuntu.

I run 32-bit on two ancient systems, my HP server, from 2006, and Acer netbook, from 2008. Both now on 14.04.3LTS, but started with 9.04, IIRC. Both came with XP, but I nuked that partition years ago. The former's Xeon can run 64-bit, but only has 4GB of RAM. The latter's Atom can't run a 64-bit OS. Both run Ubuntu fine. I've been debating whether or not I'll update these systems to 16.04LTS, but is this discussion saying that might not even be an option?  My newer systems are already running 16.04LTS Alpha, and it seems stable.

Not a huge deal. My server is running fine now, but I'd at least like the option, in my head anyway, of running all of my systems on the same OS. I thought that 16.04LTS might have been it. Maybe my old systems will have to be on 14.04 forever?

(Ok, I am going to try upgrading my netbook to 16.04... worst that can happen is I'll have to wipe the drive and restore from a backup drive via clonezilla. It is going to take freaking forever, seeing as it only has wireless G, a slow HD, and a 1.6GHz Atom. I'm curious to see where the bottleneck in the process is. I'm guessing it is the cpu installing all the packages...)

Would it be an option for you to run one of the Ubuntu family flavours, Kubuntu, Lubuntu, Ubuntu Gnome, Ubuntu MATE, Ubuntu Studio, Xubuntu? They will probably keep the 32-bit kernel (at least I think the flavours with light desktop environments will vote for keeping the 32-bit kernel for several more years).

---

### Post by deadflowr on 2016-02-07
> **justen_m said:**
> I've been debating whether or not I'll update these systems to 16.04LTS, but is this discussion saying that might not even be an option? 
Not even close.
The discussion is about dropping the image from Ubuntu-Desktop's beyond 16.04, starting with 16.10.
Won't affect 16.04 since that is already in full development.
It won't affect the various flavors like Kubuntu or Xubuntu or the like.
(Unless those flavors decide to also drop the arch, unlikely with Xubuntu, but a 50/50 toss up with Kubuntu, imo)
It won't affect servers, at least not for 16.04.

---

### Post by kansasnoob on 2016-02-07
> **deadflowr said:**
> Not even close.
The discussion is about dropping the image from Ubuntu-Desktop's beyond 16.04, starting with 16.10.
Won't affect 16.04 since that is already in full development.
It won't affect the various flavors like Kubuntu or Xubuntu or the like.
(Unless those flavors decide to also drop the arch, unlikely with Xubuntu, but a 50/50 toss up with Kubuntu, imo)
It won't affect servers, at least not for 16.04.

+1! And since Xenial is supported for 5 years that rolls us into 2021, who knows what computing will look like by then? What we're using today may compare to the Tandy by then :biggrin:

---

### Post by yoshii on 2016-02-08
For what it's worth, I use 32-bit Ubuntu Studio LTS even though my hardware has more than 4GB of RAM.  
I heavily use Wine, and the 64-bit version of Wine is reported by the Wine website to be a lot buggier than the 32-bit version.  
Also, almost every single one of my Windows freewares that I use is the 32-bit type.  Ubuntu Studio uses Xfce.  

I like the idea of being able to liberate my unneeded RAM, but in all honesty, I've never run out of RAM (in Windows or in Linux) with 4GB installed.  
If I did have full access to my RAM, I'd probably start messing around with a gigantic RAM disk to speed up certain multimedia tasks.  
But that's kind of a pie in the sky type of idea.  

I still use an old laptop, so it's nice to have 32-bit Xubuntu.  I know that 64-bit will come eventually.  But it's nice to be able to get use out of old used computers instead of just throwing them away.

---

### Post by poorguy on 2016-02-14
> **grahammechanical said:**
> A lot of people think that they can bring new life to old hardware by installing Linux. Well, they can. But not with Ubuntu. In many cases the RAM is not enough & the video adapter is not capable.

Ubuntu of 10 years ago would have run fantastically on the hardware of 10 years ago. The Ubuntu of today runs fantastically on the hardware of today. But people are wrong to think that the Ubuntu of today will run fantastically on the hardware of 10 years ago.

It is good that there are developers who see the need and who are working to meet the need.

Regards.

I have several 10 year old desktops that run Ubuntu of today very well due to the fact that they have graphics cards installed that are very capable of running Ubuntu of today.

Agreed  Ubuntu of today runs fantastically on the hardware of today. 

But there are still a lot of older computers that are capable of running Ubuntu of today.

---

### Post by kurt18947 on 2016-02-14
As long as the 'lightweight' flavors continue to support 32 bit, I don't know that there'll be an issue. How many people with machines sporting 32 bit processors run full-up Ubuntu, Kubuntu or other graphics intensive distros? How much of a burden will it become for Lubuntu, Xubuntu, MATE etc. to continue with 32 bit versions of Ubuntu-Unity drops 32 bit support? I have no idea what's involved.

---

### Post by ian-weisser on 2016-02-14
> **kurt18947 said:**
> As long as the 'lightweight' flavors continue to support 32 bit, I don't know that there'll be an issue. How many people with machines sporting 32 bit processors run full-up Ubuntu, Kubuntu or other graphics intensive distros? How much of a burden will it become for Lubuntu, Xubuntu, MATE etc. to continue with 32 bit versions of Ubuntu-Unity drops 32 bit support? I have no idea what's involved.

+1
The proposed change affects only 32-bit Unity packages...and by extension the 32-bit Unity .iso

The discussion in ubuntu-devel is not about dropping all 32-bit support.
Nobody is proposing to drop 32-bit kernels. 
Nobody is proposing to drop any other 32-bit packages.

---

### Post by justen_m on 2016-02-19
> **sudodus said:**
> Would it be an option for you to run one of the Ubuntu family flavours, Kubuntu, Lubuntu, Ubuntu Gnome, Ubuntu MATE, Ubuntu Studio, Xubuntu? They will probably keep the 32-bit kernel (at least I think the flavours with light desktop environments will vote for keeping the 32-bit kernel for several more years).
I haven't decided yet for my netbook. It is slow running straight Ubuntu. I bit the bullet and upgraded my antique server to 64-bit 16.04LTS Alpha, as it's got the horsepower and capability. I've been looking at [LXLE]("http://www.lxle.net") (Lubuntu-based) for my netbook, but that's a discussion for another thread.

Anyway, to all, thanks for the info about 32-bit not disappearing until _after_ 16.04. With the other flavors keeping 32-bit alive, it won't matter if the main Ubuntu branch doesn't. So I guess I wouldn't really miss it.

---

### Post by uRock on 2016-02-19
I run standard ubuntu on my Netbook motion server. As many times as I've tried the other flavors, I still end up putting ubuntu back on it.

---

### Post by len-ovenwerks on 2016-04-09
One question. I have a server running 32bit. There are rather a lot setting I would like to keep. So far I have been able to just upgrade from version to the next. Does Ubuntu have some way for people to migrate from 32bit to 64bit? Something reasonably automated? Even an install 64bit in one partition(s) point to 32bit partition(s) migrate settings.

---

### Post by deadflowr on 2016-04-09
> **len-ovenwerks said:**
> One question. I have a server running 32bit. There are rather a lot setting I would like to keep. So far I have been able to just upgrade from version to the next. Does Ubuntu have some way for people to migrate from 32bit to 64bit? Something reasonably automated? Even an install 64bit in one partition(s) point to 32bit partition(s) migrate settings.

No.
But then again, there would be no need, as 32-bit server edition should still be around.
The discussion here is/was about Ubuntu's desktop dropping the 32-bit version.
Should not affect servers in any way.

---

### Post by Mike_Walsh on 2016-04-10
I feel it's probably right to drop the 32-bit Ubuntu package, since the 3D acceleration required by Unity is very demanding for a lot of older netbooks/laptops. These tend to have onboard graphics chips; some have the GPU contained within the CPU (an Accelerated Processing Unit), but not many.

My own 14-yr old Dell Inspiron 1100 laptop has problems even with the 32-bit version of Ubuntu, due to the dreadful Intel 'Extreme' graphics chip it's fitted with. Xubuntu, however, runs sweetly (if a wee bit slowly), and I certainly hope support is maintained for the 32-bit version for the forseeable future.


Mike. ;)

---

### Post by UbuntuAddict99 on 2016-04-26
Hello All, 

Yes i agree Ubuntu should drop support for 32 Bit systems i mean the 32 Bit system is going to expire in what, was it? forgive me if a i am wrong in the 2020's!
due to the UNIX clock, i have forgotten the proper term for it. But no one seems to use 32 Bit system anymore anyway it is like using a 16 Bit system, but then again it is all up to the developers.

I mean 64 Bit is the standard now and soon hopefully 128 Bit systems will come out but that will probably be in another few decades anyway commercially anyway.
But whatever happens i am happy on my 64 Bit system.

Happy Linuxing.

"Linux Ubuntu the final frontier!"
                                              -UbuntuAddict99

---

### Post by ChuangTzu on 2016-04-26
Hey, at least options will remain.  RedHat and openSUSE both dropped 32bit.  Worse case scenario one could always run Debian for old or low powered boxes.  I have Ubuntu on a 7 year old desktop HP AMD Athlon II 800mgz, 8GB RAM, handles it pretty well.  Debian is on a very old (10+, cant remember exactly) Gateway laptop and it runs well with Xfce.  Might try Xubuntu on their one day, just havent seen the need since its had Debian on since Deb. 5 Lenny.

---

### Post by mörgæs on 2016-04-28
> **UbuntuAddict99 said:**
> 
the 32 Bit system is going to expire in what, was it? forgive me if a i am wrong in the 2020's!
due to the UNIX clock, i have forgotten the proper term for it.


2038. 

> **UbuntuAddict99 said:**
> 
But no one seems to use 32 Bit system anymore anyway it is like using a 16 Bit system, but then again it is all up to the developers.


And it's up to us who can try to convince them. 

Lots of people use 32 bit systems. There is so much old hardware out there that can and should be kept running for many years to come.

---

### Post by mastablasta on 2016-04-29
Various ATOM CPU's for example that are not that old to be thrown away yet are actually 32 bit only. we are talking about 4, 5 year old CPU's (released 4 or 5 years ago and then probably last sold 3 years ago or are even sitll out on the market) used in netbooks and ITX boards (e.g. for some home theater) e.g.: [http://www.mini-itx.com/store/?c=47](http://www.mini-itx.com/store/?c=47)

for example [https://en.wikipedia.org/wiki/Intel_Atom](https://en.wikipedia.org/wiki/Intel_Atom) :
> Intel states the Atom supports 64-bit operation only "with a processor, chipset, BIOS" that all support [Intel 64]("https://en.wikipedia.org/wiki/Intel_64"). Those Atom systems not supporting all of these cannot enable Intel 64.[SUP][[22]]("https://en.wikipedia.org/wiki/Intel_Atom#cite_note-22")[/SUP] As a result, **the ability of an Atom-based system to run 64-bit versions of operating systems such as [Ubuntu]("https://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29") or [Debian GNU/Linux]("https://en.wikipedia.org/wiki/Debian_GNU/Linux")  may vary from one motherboard to another**. Online retailer mini-itx.com  has tested Atom-based motherboards made by Intel and Jetway, and while  they were able to install 64-bit versions of Linux on Intel-branded  motherboards with D2700 (Cedarview) processors, Intel 64 support was not  enabled on a Jetway-branded motherboard with a D2550 (Cedarview)  processor.[SUP][[23]]("https://en.wikipedia.org/wiki/Intel_Atom#cite_note-23")[/SUP]

 **Even among Atom-based systems which have Intel 64 enabled, not all are able to run 64-bit versions** of [Microsoft]("https://en.wikipedia.org/wiki/Microsoft") [Windows]("https://en.wikipedia.org/wiki/Microsoft_Windows"). For those *Pineview*  processors which support 64-bit operation, Intel Download Center  currently provides 64-bit Windows 7 and Windows Vista drivers for [Intel GMA]("https://en.wikipedia.org/wiki/Intel_GMA") 3150 graphics, found in *Pineview* processors.[SUP][[24]]("https://en.wikipedia.org/wiki/Intel_Atom#cite_note-24")[/SUP] However, no 64-bit Windows drivers are available for Intel Atom *Cedarview* processors, released Q3 2011.[SUP][[25]]("https://en.wikipedia.org/wiki/Intel_Atom#cite_note-25")[/SUP] However, Intel's Bay Trail-M processors, built on the [Silvermont]("https://en.wikipedia.org/wiki/Silvermont")  microarchitecture and released in the second half of 2013, regain  64-bit support, although driver support for Linux and Windows 7 is  limited at launch.[[]("https://en.wikipedia.org/wiki/Intel_Atom#cite_note-26")

---

### Post by Cammy_White on 2016-05-01
Absolutely.
A special 'Atom' edition could be created with performance tweaks simply for that processor set, I know of a few programs such as Pale Moon which have done this for Windows XP.

I agree, 32-bit needs to go, although would this affect other distros? The purpose I think for Lubuntu is to run in older machines, correct?

---

### Post by kansasnoob on 2016-05-01
> 32-bit needs to go, although would this affect other distros?

AFAIK it would only effect Ubuntu desktop versions. 32 bit server builds will still be available and each flavor will have the option to maintain a 32 bit version if they wish.

---

### Post by Portaro on 2016-05-05
If I can participate my answer is no! I think that if many distros can support on different flavours the 32 Bit systems is better for all :
1- many machines only accept this architecture type Kernel + system configs.
2- Reuse machines and maintain these old hardaware active to more or less use , and in some cases this fact can be important many people dont have money to buy new pcs , many people maybe receive this machines by associations like Emmabuntus or others and this associations installs Linux to people with poor economic resources and offer the computers and many of this machines obviously is provided by people that substitute the pcs with others because they can pay and share the old pc for others, schoolls, people around world , associations.... many of them can need the GNU/Linux support for 32 and this can make difference between can access to TI, digital society and literacy on web or not!
Ubuntu I think have the resposability to support this ideal and this great opportunity tha GNU/Linux brings to us, the model in windos is pay a new machine and system 5 after 5 years - I hope this model of work dont arrive to Ubuntu.

I understand if the default Unity Ubuntu only can support x86_64 or 64 , but I dont feel this happy , or good because I think that then the other flavours make the same decision or the same proposal and release after release the old 32 bis pcs lost the place on the offer of GNU/Linux.


But if is guaranteed that for example Lubuntu is totally compromised with the objective to maintain 32 bits support then I think that the Fact of Ubuntu Uity is or not 32 bit compatible is a minor question!
I hope that all understand my words.
Thanks.

---

### Post by kansasnoob on 2016-05-05
> **Portaro said:**
> If I can participate my answer is no! I think that if many distros can support on different flavours the 32 Bit systems is better for all :
1- many machines only accept this architecture type Kernel + system configs.
2- Reuse machines and maintain these old hardaware active to more or less use , and in some cases this fact can be important many people dont have money to buy new pcs , many people maybe receive this machines by associations like Emmabuntus or others and this associations installs Linux to people with poor economic resources and offer the computers and many of this machines obviously is provided by people that substitute the pcs with others because they can pay and share the old pc for others, schoolls, people around world , associations.... many of them can need the GNU/Linux support for 32 and this can make difference between can access to TI, digital society and literacy on web or not!
Ubuntu I think have the resposability to support this ideal and this great opportunity tha GNU/Linux brings to us, the model in windos is pay a new machine and system 5 after 5 years - I hope this model of work dont arrive to Ubuntu.

I understand if the default Unity Ubuntu only can support x86_64 or 64 , but I dont feel this happy , or good because I think that then the other flavours make the same decision or the same proposal and release after release the old 32 bis pcs lost the place on the offer of GNU/Linux.


But if is guaranteed that for example Lubuntu is totally compromised with the objective to maintain 32 bits support then I think that the Fact of Ubuntu Uity is or not 32 bit compatible is a minor question!
I hope that all understand my words.
Thanks.

I think you're missing the point. Ubuntu w/Unity, Ubuntu GNOME, and Kubuntu are no longer suitable for "older" hardware anyway. There would still be a 32 bit version of Ubuntu server edition so the 32 bit kernel would still be alive and well. Those flavors that require less in regards to graphics acceleration and such would easily be able to opt into producing 32 images. It's also important to remember that Ubuntu 16.04 is supported until April 2021, that's a long ways off :)

---

### Post by mörgæs on 2016-05-06
There is a [thread]("http://ubuntuforums.org/showthread.php?t=2254322") spanning, at the time of writing, 944 posts dealing with getting Ubuntu to work on modern 32 bit hardware. I think this clearly demonstrates that Ubuntu has a strong following on all hardware platforms. 

The observation that weak hardware is 32 bit does not mean that 32 bit hardware is weak.

---

### Post by uRock on 2016-05-07
> **mörgæs said:**
> There is a [thread]("http://ubuntuforums.org/showthread.php?t=2254322") spanning, at the time of writing, 944 posts dealing with getting Ubuntu to work on modern 32 bit hardware. I think this clearly demonstrates that Ubuntu has a strong following on all hardware platforms. 

The observation that weak hardware is 32 bit does not mean that 32 bit hardware is weak.

+1

---

### Post by poorguy on 2016-05-07
A lot of people got started using Linux because they have a 32 bit  computer sitting around doing nothing so they installed Linux on it and  now use it.

Many good 32 bit computers still in use today.
Even Microsoft supports 32 bit OS and IMO that is the best reason to keep 32 bit alive in Linux.

---

### Post by ian-weisser on 2016-05-08
'OMG Ubuntu is dropping 32-bit' is pure FUD.

The discussion was ONLY about dropping 32-bit Unity7. Nothing else. The mailing list discussion includes the reasons why.

EVERY other package and flavor of Ubuntu that currently includes 32-bit support is unchanged. Unchanged!

---

### Post by uRock on 2016-05-08
> **ian-weisser said:**
> EVERY other package and flavor of Ubuntu that currently includes 32-bit support is unchanged. Unchanged!

I was happy to find that Ubuntu Mate supports RasberryPi. I had thought all of Ubuntu's releases had dropped support for ARM.

---

### Post by kansasnoob on 2016-05-08
> **ian-weisser said:**
> 'OMG Ubuntu is dropping 32-bit' is pure FUD.

The discussion was ONLY about dropping 32-bit Unity7. Nothing else. The mailing list discussion includes the reasons why.

EVERY other package and flavor of Ubuntu that currently includes 32-bit support is unchanged. Unchanged!

+1!

---

### Post by mörgæs on 2016-05-09
FUD means that a company is spreading misinformation about a competitor, a sport in which Microsoft excels. Hardly the situation here.

Though the mailing list only mentions Unity / Ubuntu the discussion is still relevant. It's likely that the thoughts are triggering other developers, open source or not, to consider abandoning 32 bit.

---

### Post by poorguy on 2016-05-09
> **mörgæs said:**
> FUD means that a company is spreading misinformation about a competitor, a sport in which Microsoft excels. Hardly the situation here.

Though the mailing list only mentions Unity / Ubuntu the discussion is still relevant. It's likely that the thoughts are triggering other developers, open source or not, to consider abandoning 32 bit.

Agreed.

Once changes as this begin to happen than it is only a matter of time before a complete end of other 32 bit Ubuntu based distros by developers.

---

### Post by kansasnoob on 2016-05-09
> **mörgæs said:**
> FUD means that a company is spreading misinformation about a competitor, a sport in which Microsoft excels. Hardly the situation here.

Though the mailing list only mentions Unity / Ubuntu the discussion is still relevant. It's likely that the thoughts are triggering other developers, open source or not, to consider abandoning 32 bit.

There is some merit to that argument. A good example would be the lack of support for non-PAE. Lubuntu tried to fill the gap somewhat but none of the individual flavors have the manpower to maintain a true non-pae kernel.

OTOH I can understand Canonical's challenge here. Just one example is Canonical's own browser that's being built to work specifically with Unity. It takes a lot of additional man-hours to maintain both 32 bit and 64 bit versions of each package.

It would be interesting to know what the download statistics are. That is, what percentage of bog standard Ubuntu desktop version downloads are amd64 vs i386?

---

### Post by mastablasta on 2016-05-10
yesterday i read sensationalist news that Debian will be dropping 32 bit support. Turns out they will only be dropping i586 support.

> The older processors will continue to be supported in jessie until at
least 2018, and until 2020 if i386 is included in jessie LTS.

[1] The following processors, supported in jessie, are now unspported:

* AMD K5, K6, K6-2 (aka K6 3D), K6-3
* DM&P/SiS Vortex86, Vortex86SX
* Cyrix III, MediaGX, MediaGXm
* IDT Winchip C6, Winchip 2
* Intel Pentium, Pentium with MMX
* Rise mP6
* VIA C3 'Samuel 2', C3 'Ezra'

Source: [https://lists.debian.org/debian-devel-announce/2016/05/msg00001.html](https://lists.debian.org/debian-devel-announce/2016/05/msg00001.html)

---

### Post by mörgæs on 2016-05-10
> **kansasnoob said:**
> ...lack of support for non-PAE. Lubuntu tried to fill the gap somewhat but none of the individual flavors have the manpower to maintain a true non-pae kernel.

Actually all 32 bit kernels in Buntu require PAE, and all Buntus share the same kernels. The last non-PAE-kernel was from 12.04.

The oldest part of the still-popular Pentium M processor family don't advertise that they have PAE, which they in fact have. In order to get a recent Buntu to boot on a first-generation Pentium M a certain boot option has to be applied, raising the missing PAE flag.

Not trying to be rude, just for clarity.

/deviation over.

---

### Post by kansasnoob on 2016-07-01
[http://www.pcworld.com/article/3089509/linux/end-of-an-era-linux-distributions-will-soon-stop-supporting-32-bit-pcs.html](http://www.pcworld.com/article/3089509/linux/end-of-an-era-linux-distributions-will-soon-stop-supporting-32-bit-pcs.html)

>  Ubuntu’s Dimitri John Ledkov put forth a proposal to wind down 32-bit support on the Ubuntu mailing list recently. Hardware that can’t run 64-bit software is becoming much less common, while creating 32-bit images, testing them, and supporting them takes time and effort. (On Linux, the “i386” architecture is the standard 32-bit for Intel-compatible CPUs, while “amd64” is the 64-bit architecture originally made by AMD that Intel CPUs are compatible with.)

Ledkov points out that Ubuntu wants to limit the number of new 32-bit installations, with Ubuntu 16.10. **[COLOR="#FF0000"]This next release will not offer a 32-bit Ubuntu Desktop or Ubuntu Server image[/COLOR]**. The software could still be installed for legacy compatibility purposes via more traditional installers. **[COLOR="#FF0000"]By Ubuntu 18.10 in October 2018, Ubuntu would completely end support for 32-bit software[/COLOR]** and encourage running it in a virtual machine or container instead. 

---

### Post by fdrake on 2016-07-01
can someone tell me what benefit would bring dropping down the 32bit support? to the community and to the developers?

---

### Post by mc4man on 2016-07-01
> **fdrake said:**
> can someone tell me what benefit would bring dropping down the 32bit support? to the community and to the developers?

It's generally poor practice to speak for others but I'd venture the benefit to Ubuntu(Canonical) is less resources, (ie. money) needed to produce & maintain a Desktop version. I doubt they'll ever monetize the Desktop to any significant or even noticeable  level so better to limit what it costs.

---

### Post by kansasnoob on 2016-07-01
> **fdrake said:**
> can someone tell me what benefit would bring dropping down the 32bit support? to the community and to the developers?

Just as it says in my previous post:

> creating 32-bit images, testing them, and supporting them takes time and effort

---

### Post by grahammechanical on 2016-07-01
32 bit 16.04 will still be supported until it reaches end of life. Anyone still using a 32 bit machine in 2021 will have got their money's worth out of it.

---

### Post by ventrical on 2016-07-01
If an end_user wants to keep a 32bit install running past the due date it is quite simple.  Just don't try to do any updates. Build what you need and let it roll from there. If you have access to extra hdds (which I have several of) then you can do 32bit builds, update them and then lock them. You can swap those hdds out to different PCs without any real damage.

 I have a working install of Maveric Meerkat which was an interim cycle before the release of Precise Pangolin . it works beautifully. Never seems to require any flashplugin update for firefox and it is overall very stable. Just because a distribution reaches an EOL does not mean that it has to stop being used. If fact some of the older builds are much more stable and don't forget you can still run a 32bit legacy install on a newer form factor. it is not all that painful not having new features because recently it has been newer features that have been breaking older installs through the upgrade process.

Windows based systems are almost impossible to swap in and swap out because of spyware and authentication schemes. i.e. like Windows XP for example.

Regards..

---

### Post by &amp;KyT$0P# on 2016-07-01
> By Ubuntu 18.10 in October 2018, Ubuntu would completely end support for 32-bit software and encourage running it in a virtual machine or container instead. 
Oh noes!  Part of the reason we were able to go fully 64-bit on Linux is because of the ability to install 32-bit libraries and run 32-bit applications.  And VM is not an option for every 32-bit software we run.
What is meant by "container"?

---

### Post by kansasnoob on 2016-07-02
> **grahammechanical said:**
> 32 bit 16.04 will still be supported until it reaches end of life. Anyone still using a 32 bit machine in 2021 will have got their money's worth out of it.

+1!

---

### Post by kansasnoob on 2016-07-02
> **ventrical said:**
> If an end_user wants to keep a 32bit install running past the due date it is quite simple.  Just don't try to do any updates. Build what you need and let it roll from there. If you have access to extra hdds (which I have several of) then you can do 32bit builds, update them and then lock them. You can swap those hdds out to different PCs without any real damage.

 I have a working install of Maveric Meerkat which was an interim cycle before the release of Precise Pangolin . it works beautifully. Never seems to require any flashplugin update for firefox and it is overall very stable. Just because a distribution reaches an EOL does not mean that it has to stop being used. If fact some of the older builds are much more stable and don't forget you can still run a 32bit legacy install on a newer form factor. it is not all that painful not having new features because recently it has been newer features that have been breaking older installs through the upgrade process.

Windows based systems are almost impossible to swap in and swap out because of spyware and authentication schemes. i.e. like Windows XP for example.

Regards..

I would never use an unsupported distro if the machine is connected to the internet. There are way too many supported options out there to take the risk :)

---

### Post by mörgæs on 2016-07-02
> **kansasnoob said:**
> I would never use an unsupported distro if the machine is connected to the internet. There are way too many supported options out there to take the risk :)

+1. 
Maverick Meerkat / 10.10 lost its support four years ago. The vast number of security bugs that has been discovered during that period of time should act as a warning against using it.

Here's the amount of security fixes for just one week: [https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue471#Updates_and_Security_for_12.04.2C_14.04.2C_15.10_and_16.04](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue471#Updates_and_Security_for_12.04.2C_14.04.2C_15.10_and_16.04)

and an example of how many bugs that can be covered by one fix: [https://lists.ubuntu.com/archives/ubuntu-security-announce/2016-June/003462.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2016-June/003462.html)

---

### Post by mörgæs on 2016-07-02
Please post here to show that 32 bit is still relevant now and in the future:

[http://goo.gl/forms/UfAHxIitdWEUPl5K2](http://goo.gl/forms/UfAHxIitdWEUPl5K2)

---

### Post by grahammechanical on 2016-07-02
> What is a container?

[http://www.ubuntu.com/cloud/lxd](http://www.ubuntu.com/cloud/lxd)

It is like a VM but without the need for a large chunk of system resources. My hardware is not powerful enough to run a VM but It can run operating systems in a Linux container (LXC).

An alternative would be for 32 bit applications to be snap packaged. They would have all their libraries in the package and snap apps are confined which would lessen any security risk from using old software.

Here is a challenge for someone. Run 32 bit Ubuntu in LXC/LXD and  document how to do it. It might prove useful to someone in the future.

Regards.

---

### Post by &amp;KyT$0P# on 2016-07-02
Thanks grahammechanical!  Sounds like snap packaging will probably be the best option here.

---

### Post by grahammechanical on 2016-07-02
This might help for those who want to run 32 bit Ubuntu and 32 bit applications in a Linux container. I am guessing that doing this in 16.04 now will keep those 32 bit applications useful for a long time.

[https://www.stgraber.org/2014/02/09/lxc-1-0-gui-in-containers/](https://www.stgraber.org/2014/02/09/lxc-1-0-gui-in-containers/)

This of course, not a solution for those who have 32 bit CPU's.

Regards.

---

### Post by ventrical on 2016-07-03
> **kansasnoob said:**
> I would never use an unsupported distro if the machine is connected to the internet. There are way too many supported options out there to take the risk :)

I'm just saying .. if there are some die hards out there who do not want to invest in 64bit hardware then they can still do 32bit of course without a lot of bells and whistles.. but it can still be done however jumpity the system may get after a while :)

regards..

---

### Post by ventrical on 2016-07-03
> **grahammechanical said:**
> [http://www.ubuntu.com/cloud/lxd](http://www.ubuntu.com/cloud/lxd)

It is like a VM but without the need for a large chunk of system resources. My hardware is not powerful enough to run a VM but It can run operating systems in a Linux container (LXC).

An alternative would be for 32 bit applications to be snap packaged. They would have all their libraries in the package and snap apps are confined which would lessen any security risk from using old software.

Here is a challenge for someone. Run 32 bit Ubuntu in LXC/LXD and  document how to do it. It might prove useful to someone in the future.

Regards.

Tried and tried and tried ...can only get htop and midnight commander to run from cli. I guess there must be a way  to put Xserver onto it but I haven't figured it out yet. If xapps (like firefox) can run in containers in the unity8 program on xmir I presume then they should be able to run standalone in lxc containers.

regards..

---

### Post by Portaro on 2016-10-14
> **mörgæs said:**
> Please post here to show that 32 bit is still relevant now and in the future:

[http://goo.gl/forms/UfAHxIitdWEUPl5K2](http://goo.gl/forms/UfAHxIitdWEUPl5K2)

What was the result?
The  form is closed there are other to I add my vote?

---

### Post by cariboo on 2016-10-14
32 bit support will still be around for a while, as many IOT devices are 32-bit, so although there won't be any Ubuntu ISO's, there will still be packages in the repositories.

---

### Post by Portaro on 2016-10-15
Good news so we still have some voice on the developent team.
Thanks I will need 32 Bit in future I think because my pcs are very very old and I dont have money for others.:popcorn:

---

### Post by oldrocker99 on 2016-10-19
I have a 32-bit Lenovo laptop, and it would be a huge drag not being able to install a new version on it.

---

### Post by Portaro on 2016-10-19
> **oldrocker99 said:**
> I have a 32-bit Lenovo laptop, and it would be a huge drag not being able to install a new version on it.

Maybe Ubuntu team can release one special version with Openbox or else identical.

My case is like your so I also need some 32 bit alternatives. :popcorn:

---

### Post by poorguy on 2016-10-20
There are a lot of 32 bit and 64 bit light weight Linux distros that are excellent alternatives and do everything that the big mainstream Linux distros do. :cool:

---

### Post by ArgentWarrior on 2016-11-06
What would be the point in dropping 32-bit support when the devs will still have to maintain 32-bit versions of everything? Don't think for a second that Valve will suddenly decide to make Steam for Linux 64-bit because of Shuttleworth's shenanigans, or that Wine will work without its 32-bit deps.

---

### Post by kostkon on 2016-11-06
> **ArgentWarrior said:**
> What would be the point in dropping 32-bit support when the devs will still have to maintain 32-bit versions of everything? Don't think for a second that Valve will suddenly decide to make Steam for Linux 64-bit because of Shuttleworth's shenanigans, or that Wine will work without its 32-bit deps.
Well, Valve has just made the beta release of [Steam 64bit-only on Linux]("https://support.steampowered.com/kb_article.php?ref=4090-RTKZ-4347"), well sort of, only the web component is 64bit now. That means you cannot browse the store on 32bit systems now or access the community section, you can only play your games; and in a way that's bad because your purchases will not register as Linux ones if you are forced to buy your games through the web browser.

---

### Post by hwertz10 on 2016-12-13
I think there may not be anything to worry about.  If you look at the current situation, Ubuntu has formal support for x86, x86-64, and ARM.  But, there are DVD images, network bootable images, and so on for 64-bit ARM, PowerPC (both old PowerMacs and other systems), 64-bit PowerPC (mostly IBM RS/6000s), and s390x (run on IBM Z series mainframes.) 

The reasons they'd like to make x86 unsupported... 1) build system resources.  Ports tend to have some volunteers running the buildd software (the software that checks for "proposed" updates, downloads the source, builds it, tests it, and turns it into a debian package).  2) Debian and Ubuntu usually block updating a piece of software until it builds (and passes whatever self-tests) on ALL supported platforms.  So, if x86 were no longer "supported" an x86-only build failure wouldn't block a package from being updated on other systems.

The reality:  I've run a few of these unsupported "ports" systems over the years (PowerPC, PA-RISC, Alpha, ARM several times, MIPS).  Honestly?  Smooth sailing, I wouldn't worry too much.  I found the consequences of the above to be pretty mild, you don't really feel like your running a system with a "second tier" of support.  Mainly, the buildd situation meant big updates (libreoffice, chromium, etc.) could "clog up" the buildd, so other updates could fall behind a few days then play catch-up compared to a supported system.  And the build failure thing, that just means other platforms get that 0.1 or 0.0.1 newer software update and you don't, until a patch is found.  

Generally the sign a port is REALLY in trouble with debian at least, you'll have the number of buildd systems drop until updates don't just fall behind when there's big updates, it's permanently behind; and when software begins to have build or test failures but nobody comes up with patches to fix them.  (PA-RISC, Alpha, Motorola 68k are a few formerly supported systems that suffered this fate).  I would guess x86 is far from this point yet.

*ARM being a bit odd since the included kernel only supports about a dozen systems, with many others using a custom kernel that can usually run any armhf software including an Ubuntu distro.

---

### Post by kansasnoob on 2017-09-27
Update to where we stand now:

[https://ubuntuforums.org/showthread.php?t=2372469&p=13691051#post13691051](https://ubuntuforums.org/showthread.php?t=2372469&p=13691051#post13691051)

This pretty much says it all:

> What this means is that Ubuntu desktop is not releasing i386 with
the *[COLOR="#800080"]Artful[/COLOR]* final beta, and we won't build i386 ISOs any more.

[B]Other flavours are unaffected and, as xnox said, existing installations
that are on i386 on a previous release will be able to upgrade to 17.10
and 18.04 when they are released and they'll continue to be supported as
normal.[/B] 

---

### Post by mastablasta on 2017-09-28
PC had 1.3 GB ram, so it got a 32 bit install. it now has 2 GB ram. for now i plan to upgrade it to 16.04 (maybe next year or in 2018), so only in 2021 i will dela with 64 bit if the PC is still working by then. i wasnt' able to uprgade the GPU and this one is starting to act strange. luckilly the CPU is 64bit. 

however, i would worry more about drivers and such. will they still be supported? will 32bit libraries then still be provided for 32 bit apps? windows 10 for exmaple (though not perfect) can run many 32 bit apps. some that were made in winxp or even in win98 era. in fact for some reason certain 64 bit version won't run on on it, while the 32 bit ones run perfectly.

---

### Post by mörgæs on 2017-09-28
Just hoping that it will not trigger posts like "throw away that 32 bit hardware, it's out of support", which is far from the truth. The light Buntus carry on.

---

### Post by sudodus on 2017-09-28
> **mörgæs said:**
> Just hoping that it will not trigger posts like "throw away that 32 bit hardware, it's out of support", which is far from the truth. The light Buntus carry on.

+1 :-)

---

### Post by kansasnoob on 2017-09-28
> **mörgæs said:**
> Just hoping that it will not trigger posts like "throw away that 32 bit hardware, it's out of support", which is far from the truth. The light Buntus carry on.

Sadly some people always look at every change as the end of the world ;)

I wanted to find out because I was just handed some old boxes with Intel Atom 230 CPU's and, while they are 64 bit capable, 32 bit performs much, much better on them. Now I can comfortably install Xenial i386 knowing that it will be upgrade-able to 18.04.1 when it drops about August of next year. Using Ubuntu w/flashback should carry them up to April 2023 unless the hardware dies. 

I'll use the 16.04.1 install media to avoid HWE changes. And I may just leave them on Xenial until it goes EOL, then I can buy another two years with an upgrade to 18.04 when that time arrives. Who knows what 2021 will bring? By then Google and Microsoft may be handing out free puters just to get you to use their OS :lolflag:

---

### Post by kansasnoob on 2017-12-21
They've decided to drop the server images also:

[https://lists.ubuntu.com/archives/ubuntu-release/2017-December/004257.html](https://lists.ubuntu.com/archives/ubuntu-release/2017-December/004257.html)

[https://lists.ubuntu.com/archives/ubuntu-release/2017-December/004258.html](https://lists.ubuntu.com/archives/ubuntu-release/2017-December/004258.html)

Please note that it says:

> As with the desktop i386 ISO change, there are no other changes requested to d-i, mini.iso, archive, or the upgrade paths.

---

### Post by mörgæs on 2017-12-22
:-( 
Old hardware with weak graphics is/was a good candidate for a headless server install. 

Anyway, people can still add server components beginning from a minimal ISO install. If only they know the option is there.

---

### Post by kansasnoob on 2017-12-22
> **mörgæs said:**
> :-( 
Old hardware with weak graphics is/was a good candidate for a headless server install. 

Anyway, people can still add server components beginning from a minimal ISO install. If only they know the option is there.

I'll have to check but I think you could still use an Lubuntu alternate image to perform a "minimal" install also. It works almost identical to the mini.iso but doesn't require downloading as many packages to complete the install. I'll check in the next few days to see if that still works. I'll have to dust off some old notes.

---

### Post by kostkon on 2017-12-22
On a related note, [NVIDIA will end driver support for 32-bit operating systems after the release of version 390]("https://nvidia.custhelp.com/app/answers/detail/a_id/4604/").

---

