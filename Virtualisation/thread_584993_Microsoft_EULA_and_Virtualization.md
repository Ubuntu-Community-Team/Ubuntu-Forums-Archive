---
title: "Microsoft EULA and Virtualization"
date: 2007-10-21
forum: Virtualisation
---

### Post by bodhi.zazen on 2007-10-21
Microsoft sets out terms and conditions of use in the so called "EULA" :** EULA (End User License Agreement)**

If you do not understand the EULA, please contact Microsoft, but ...

PLEASE IT IS NOT APPROPRIATE TO POST CRACKING INFORMATION ON THE UBUNTU FORUMS :twisted:

---

### Post by RealG187 on 2007-11-15
Doesnt Windows run under VM without cracking?

---

### Post by harrisony on 2007-11-27
> **RealG187 said:**
> Doesnt Windows run under VM without cracking?
Home versions of Windows vista don't
[http://www.zdnetasia.com/news/software/0,39044164,61969665,00.htm](http://www.zdnetasia.com/news/software/0,39044164,61969665,00.htm)

---

### Post by peabody on 2007-11-27
> 
According to the Gartner analyst, Microsoft's decision is derived from a license restriction, not a technical one. So, a consumer who wants to run Windows Vista under VMware on a Mac, for instance, will violate Microsoft's EULA, he added.


Sounds to me like it can certainly be done according to the article.

I think the purpose of the sticky is to let people know that they may be violating the end user license agreement unintentionally if they try to run Vista under virtualization.

What I love about the article is how full of BS it shows Microsoft to be.  If virtualization was "not yet mature enough for broad consumer adoption", there would be no reason for the license restriction.  Their behavior is so contradictory it's laughable.  Virtualization is here and its going to become only more and more important for the consumer down the road.  They know this and that's exactly why they want you to have to pay more for it.

---

### Post by RealG187 on 2007-11-27
I dont think things are stable enough to be run under VM, but especially Ultimate, if any version would be stable enough it wold probably be the home versions, this is bad management this will just cause people to pirate Ultimate...

---

### Post by wheredidrealitygo on 2007-12-13
**UPDATE**

Microsoft [changed their mind]("http://arstechnica.com/news.ars/post/20080121-microsoft-relents-vista-virtualization-ban-lifted.html") about being able to legally virtualize Home Premium and Home Basic versions of Windows Vista. It is now completely legal to do so.

My former post that occupied this spot is below.

> I used to work for Microsoft in one of the lower subsections of the Licensing Department (ok ok.. a call centre hehe), I used to "interpret" (and sometimes literally translate) EULA's, if anyone would like to know more specifics of any particular EULA we can open up a thread specifically on that topic.

License restrictions for XP: If it's an OEM copy, it's not allowed to legally be used on any machine other than the first it was installed upon (including virtual machines), and XP can not legally be used to provide commercial hosting services.

If it's a retail copy of XP, one machine at a time, doesn't matter what kind of machine though (physical or virtual).

Vista License: Vista's License is more restrictive, in that OEM copies are limited to the first machine they are installed upon, retail copies are still transferable like XP retail copies, however Vista is legally limited to one **partition/drive** where XP is not, and only Vista Business/Ultimate are legally allowed to be virtualized at all.

---

### Post by RealG187 on 2007-12-13
> **wheredidrealitygo said:**
> retail copies are still transferrable like OEM copies

I though you said OEM are not transferable

> **wheredidrealitygo said:**
> however Vista is legally limited to one **partition/drive**
What do you mean by this? You can not install it twice on the same computer?

---

### Post by wheredidrealitygo on 2007-12-14
I corrected my previous post. Thanks for pointing that out.

And yes, according to the Vista EULA, it is only legal to install it once on one computer (one partition or drive, and not another partition or drive, on the same computer, or a different one). It is of course removable and transferable (if it is a retail copy) to another partition or hard drive, or computer, but again, only one at a time.

---

### Post by RealG187 on 2007-12-14
That sucks, you should bne able to, it's the same computer.

Does anyone ever read the things, I just click agree so it instals ;)

---

### Post by wheredidrealitygo on 2007-12-15
I refreshed my knowledge of the EULA (on the virtualization tech). It's a little complicated.

For Ubuntu users, these will be the parts that matter:
```

2. INSTALLATION AND USE RIGHTS. Before you use the software under a license, you must
   assign that license to one device (physical hardware system). That device is the “licensed device.”
   A hardware partition or blade is considered to be a separate device.
   a. Licensed Device. You may install one copy of the software on the licensed device. You may
       use the software on up to two processors on that device at one time. Except as provided in the
       Storage and Network Use (Ultimate edition) sections below, you may not use the software on any
       other device.

6. USE WITH VIRTUALIZATION TECHNOLOGIES. You may use the software installed on the
   licensed device within a virtual (or otherwise emulated) hardware system on the licensed device. If
   you do so, you may not play or access content or use applications protected by any Microsoft digital,
   information or enterprise rights management technology or other Microsoft rights management
   services or use BitLocker. We advise against playing or accessing content or using applications
   protected by other digital, information or enterprise rights management technology or other rights
   management services or using full volume disk drive encryption.
```

So according to section 2. part A, you have to assign the license to a device. They consider the license to be the product key, so this has no "real" meaning, basically only be using that product key on one device. 

That last one on virtualization only applies to business and ultimate. Home Premium or Basic are not allowed to be virtualized. Basically the way they explain it is, if you are using Business or Ultimate, you can virtualize Business on a machine running Business. If you are running Ultimate, you can run a virtual machine of Ultimate.

**Legally, going through it, the bottom line, according to the EULA is, you can only run a virtual machine of Vista from the same partition that Vista is actually installed upon. Since Vista/Ubuntu can not occupy the same partition** (Can someone clarify the position of how Wubi is installed for me?)** it is technically _not legal to install Vista in a virtual machine on Ubuntu_, because Ubuntu does not exist on the same partition or hardware device as the actual Vista installed on the system.**

---

### Post by RealG187 on 2007-12-17
That's crap.

Okay I can see it couild be against it to use one disk for all computers (at over $100 for a peice of plastic if one byus a disk then they will make use if it, buying the same disk for each computer is ridiculous). But if you wanna run it on the same computer that's bull**** if you need an other license, and yet even if you have a license (which is way to far as it is) and you wanna run in a VM you only can do so from the same OS, the whole point of VM is to run different OSes at the same time.

The thing is if it's the same OS you shouldnt need an other license, and if you have a licesne you should be able to go from any OS!

---

### Post by wheredidrealitygo on 2007-12-17
Definitely agreed on all points.

Unfortunately, unless someone is able to better interpret the EULA, that makes Virtualizing Vista not permissible to any of us currently running it from Ubuntu.

---

### Post by RealG187 on 2007-12-17
Well I do what I want.

I dont even read the EULA, I just click agree so it shuts up and installs.

---

### Post by FrankVdb on 2007-12-20
I have my doubts as to the legality of that EULA in certain countries. Depending on local legislation, things can be interpreted differently.

Regardless of the legal side, it is a disgrace that one cannot use an operating system the way one wants after HAVING PAID FOR IT.

---

### Post by wheredidrealitygo on 2007-12-20
I completely agree to the disgrace part, however Microsoft thinks they're being clever in wording the EULA so that in no way, shape or form does it ever say you're paying for the operating system. They sell you the license (the EULA in effect) and merely "include" the operating system free of charge to accompany the license you paid for.

That's how they get around being sued for selling a product, they're technically not selling the OS but the license.

---

### Post by RealG187 on 2007-12-20
Well I want both

---

### Post by tiachopvutru on 2007-12-21
What if I want to run XP instead of Vista?

---

### Post by wheredidrealitygo on 2007-12-21
XP's license is much less restrictive than Vista's. It doesn't mention anything about Virtualization specifically, where Vista does.

According to the EULA, XP is legally installable on one machine at a time. If it's an OEM copy, it can only be installed on one machine, and every subsequent re installation must occur on the same machine.

A retail copy of XP, because it is more expensive than an OEM copy, will allow the user to transfer it from one machine to another, but it is still only allowed to be on one at a time.

XP does ***NOT*** limit the amount of installations that can occur on that same machine as Vista does, you can have it installed on 20 different hard drives or partitions, so long as they are all attached to that one physical computer.

Also, for the record, changing out the motherboard *WILL* violate the EULA of an OEM copy, since it's technically no longer the same computer after that. Retail licenses do not have that same restriction. This is true of both XP and Vista. 
(OEM stands for Original Equipment Manufactured, the software must stay with the original equipment it came with, and if too many hardware changes do occur with an OEM copy, there can even come a point where MS employees can not re activate that copy, the system just won't let them.)

---

### Post by RealG187 on 2007-12-21
Thats dumb, I can (sort of) understand things like piracy, but using under a VM or different mother board is just dumb, MS loses no money, I have the right to change my motherboard if I want and run a VM....

---

### Post by SRP on 2008-01-01
What I can't understand is why would someone want to run Vista in a VM anyway?  It has enough issues running on the hardware that was designed for it?  My advice is stay away from Vista...

As a VMware Certified Professional and Microsoft Partner, I constantly hear the bickering between VMware and Microsoft.  IMHO, Microsoft is pissed-off that VMware has beaten them and MS is retaliating by changing their EULA and making it more difficult for 'Microsoft Shops' to use virtualization.   MS has publicly stated their #1 goal with their virtualization product is to put VMware OUT OF BUSINESS!  Hell hath no fury like Microsoft scorned...
But let's face it, Microsoft wouldn't have to change their EULA if VMware (and virtualization) wasn't so successful.

---

### Post by RealG187 on 2008-01-02
@SRP


Yeah I was gonna say that Vista in VM is unstable, my version of VMWare doesnt have vista in it's list, but it "knows about vista" since it uses UAC sometimes and it says the the program name that you need to tell UAC to run as admin for it to work proporly..


Funny thing is if there was any version of Vista I would run in a VM it would be Basic since it probably would run the best, but M$ says you can do it (like that would stop me anyways), I bet they planned that!


Why would M$ want VM ware out of business anyways?

---

### Post by wheredidrealitygo on 2008-01-22
Microsoft [changed their mind]("http://arstechnica.com/news.ars/post/20080121-microsoft-relents-vista-virtualization-ban-lifted.html") about being able to legally virtualize Home Premium and Home Basic versions of Windows Vista. It is now completely legal to do so.

---

### Post by RealG187 on 2008-01-22
> **wheredidrealitygo said:**
> Microsoft [changed their mind]("http://arstechnica.com/news.ars/post/20080121-microsoft-relents-vista-virtualization-ban-lifted.html") about being able to legally virtualize Home Premium and Home Basic versions of Windows Vista. It is now completely legal to do so.
Good, thank you MS (notice I didnt put M$!). They had no right to. I had renewed my faith in MS and hearing this  made me lose it again, but I have it back, except there being 7 Vistas, 2 XPs was bad and they went worse. And the prices.....


I am now after Apple ([Apple is the New M$]("http://www.p2pnet.net/story/13553"))

---

### Post by rubenvb on 2008-01-26
When I install my OEM Vista Home Premium, I get an EULA for Home Basic and Ultimate, thus clearing me of any license restrictions, because technically, nothing stated in the license I read applies to me... (hehe, love to hear what anybody else thinks of this).
It's true: I insert my OEM reinstall dvd and after a few nexts, I am reading (or most likely skipping) the EULA for Home basic and Ultimate...
By the way, Virtualbox does a nice job of running Vista, haven't had the slightest trouble with it...

---

### Post by Rinzwind on 2008-01-26
> **SRP said:**
> What I can't understand is why would someone want to run Vista in a VM anyway?  It has enough issues running on the hardware that was designed for it?  My advice is stay away from Vista...

As a VMware Certified Professional and Microsoft Partner, I constantly hear the bickering between VMware and Microsoft.  IMHO, Microsoft is pissed-off that VMware has beaten them and MS is retaliating by changing their EULA and making it more difficult for 'Microsoft Shops' to use virtualization.   MS has publicly stated their #1 goal with their virtualization product is to put VMware OUT OF BUSINESS!  Hell hath no fury like Microsoft scorned...
But let's face it, Microsoft wouldn't have to change their EULA if VMware (and virtualization) wasn't so successful.

Software testing. Have 1 system. Install many OS'es and you can easily test your software on many systems. 
Otherwise you need to reboot every time of have multiple machines. 

The EULA will probably be tossed if they try to inforce it overhere,,,

---

### Post by JoshuaRL on 2008-01-27
Where is over here?

---

### Post by RealG187 on 2008-01-28
> **rubenvb said:**
> When I install my OEM Vista Home Premium, I get an EULA for Home Basic and Ultimate, thus clearing me of any license restrictions, because technically, nothing stated in the license I read applies to me... (hehe, love to hear what anybody else thinks of this).
It's true: I insert my OEM reinstall dvd and after a few nexts, I am reading (or most likely skipping) the EULA for Home basic and Ultimate...
By the way, Virtualbox does a nice job of running Vista, haven't had the slightest trouble with it...


Is VirtualBox freeware? What OS is that for?

---

### Post by wheredidrealitygo on 2008-01-28
Virtualbox is a free virtual machine server, it has an open source and proprietary version, which runs on many OS's, including Linux, they have specialised .debs for it too. [Binary downloads]("http://www.virtualbox.org/wiki/Downloads"). Those are for the open source version. It also, unlike vmware server, does not require any "unlocking" or anything to get it to work, although you may have to manually add yourself to the fuse group and restart.

---

### Post by scientus on 2008-01-29
I guess Microsoft already had this in mind (stamping down virtualization) when addressing the basics of Vista.  Anyone tried doing the originally simple task of cloning a machine for backup purposes, and then trying to restore that image at a later date?  Vista will sit on its hands because the serial of the hd + install id combo it stores is not identical to the original install(guessing its md5 based) and you're stuck with a dead machine and have to navigate via running vista off a live dvd to "fix" the problem....

---

### Post by RealG187 on 2008-01-29
> **scientus said:**
> I guess Microsoft already had this in mind (stamping down virtualization) when addressing the basics of Vista.  Anyone tried doing the originally simple task of cloning a machine for backup purposes, and then trying to restore that image at a later date?  Vista will sit on its hands because the serial of the hd + install id combo it stores is not identical to the original install(guessing its md5 based) and you're stuck with a dead machine and have to navigate via running vista off a live dvd to "fix" the problem....

That's why DRM doesnt work...


Anyways, does the open source VirtualBox have limits oposed to the propritery (I dont know how to spell that word, I hate that word, it's not worth it to spell right or copy and it's more worth it to give this speech) one.

---

### Post by wheredidrealitygo on 2008-01-31
> Anyways, does the open source VirtualBox have limits oposed to the propritery (I dont know how to spell that word, I hate that word, it's not worth it to spell right or copy and it's more worth it to give this speech) one.

Not at all, that's the purpose of open source, to have no limits. You can write your own better version off of it's source code, that's why proprietary (closed source) versions are so disliked by Linux users, no one can see what's inside of it so they don't know exactly how well it works.

Proprietary versions also have restrictive usage licenses with them (as in, the Microsoft EULA for every version of everything they have ever made).

---

### Post by RealG187 on 2008-02-01
Well the propritery (hey did I actually spell it right that time, spell check never came up) version is stil free to use though?

It doesnt *directly* affect me ince I dont know that code, but then again if someone out there who does is able to make a change that would benifit me, then it would be good...

---

### Post by BlueKoala on 2008-02-12
Is it considered piracy to copy an OS that is no longer available for purchase such as Win95?

---

### Post by wheredidrealitygo on 2008-02-12
The short answer is yes, but there are a lot of factors. Technically it would be considered abandonware, classed as commercial software that is unavailable and unsupported by a viable (still active) company.

Technically Microsoft doesn't consider Win95 to be "[Obsolete]("http://support.microsoft.com/gp/lifeobsoleteproducts")", so it would still "technically" be illegal to use it if you didn't purchase a retail copy, or have a computer it originally came with.

However, for the purpose of being practical, they probably wouldn't care (I know for a fact they wouldn't, we were allowed to give out PK's for older versions of Office, and Win95 doesn't even require PK's, so they probably feel the same way) as much as if you were to do the same thing to XP or Vista for example. Again, short answer would be, yes, it would be against the EULA.

---

### Post by akiratheoni on 2008-02-12
> **RealG187 said:**
> That's why DRM doesnt work...


Anyways, does the open source VirtualBox have limits oposed to the propritery (I dont know how to spell that word, I hate that word, it's not worth it to spell right or copy and it's more worth it to give this speech) one.

Sorry to answer an old post, but IIRC, the open source version of VirtualBox lacks several features such as USB support, but I'm sure you'll be fine without it.

---

### Post by bluewhale on 2008-03-27
Just a thought: don't go ballistic. 

Microsoft wrote it's EULA. It is NOT law. It is MS's attempt to get what it wants. EULA's, once challenged in the courts, are interpreted by those courts. 

I doubt any of us would survive being challenged in court by MS, but the facts are that EULA's may not be enforceable, or parts of them may not. 

If every company could put whatever they want on the shrinkwrap or EULA then what would stop them from saying you must give them your home after installing the product? Ridiculous? sure.  The point is someone ( the courts ) decides if a 'contract' is enforceable or not. The legal articles I've read the past 18 years regarding software have overwhelmingly indicated they are not enforceable for various reasons. 

Why post here?  

If Microsoft has the country buffalo'd into believing this then they will start working on some other aspect of their sales to increase profits, not that profits are bad. That's why they are in business.  Microsoft would take something ( a right, license, whatever ) we currently have and remove it or start charging us separately for it.  They probably do not like seeing their thousands of attorneys sitting idle. :]

The point is that companies are not the law, and never shall be. Ask any lawyer. :shock:

---

### Post by kneewax on 2008-03-28
> **bluewhale said:**
> Just a thought: don't go ballistic. 

Microsoft wrote it's EULA. It is NOT law. It is MS's attempt to get what it wants. EULA's, once challenged in the courts, are interpreted by those courts. 
:

I agree, here in the UK some years ago Microsoft was asked to leave FAST (The Federation Against Software Theft) because they refused to alter what FAST considered to be unworkable and illegal claims in the EULA that infringed the rights of the consumer.  

I am out of touch these days with where things have got to, it maybe MS bullied their way back into FAST, but I suspect they just ignored the due procedures and did their own thing like they always have - anyone here old enough to remeber the Stacker debacle with DOS 6.2? :)

---

### Post by dandl on 2008-05-05
how can you tell if xp is retail or oem?

---

### Post by wheredidrealitygo on 2008-05-06
If it came in a box, off the shelf, at a store, the cd is coppery/reflective and it's Retail, depending on where you live these are quite expensive, seeing as MS sold them for around $299+

If it's OEM, it either comes installed already on your computer, or you can buy it from small computer stores/places like newegg/amazon, and it'll say right on the cd itself "For distribution with a new PC only". These can usually  be gotten quite cheaply online (if it didn't already come with your computer) at around $80 per license depending on who you buy from.

---

### Post by RealG187 on 2008-05-06
Also the key is different, ms refused to answer a simple question because I was on an OEM key (I got an old computer with XP already on it).

Probably was illegal, but hey I didnt put it on, it came like that.

---

### Post by xrchris on 2008-05-10
So now that MS *allow* home users the benefit of using visualization legally does this apply to the OEM copies as well? 

If so is there an issue with Vista being tied to the motherboard or not? 

I basically wish to remove Vista run it in Virtualbox on Ubuntu but I want to check if there will be any issues before I start.

---

### Post by kneewax on 2008-05-10
My limited understanding of the OEM EULA is that the OEM copy is tied to the processor and / or motherboard of the machine with which it was shipped.  If you run the OS in a Virtual Machine the question is what hardware is it using?  To my mind, my Virtualbox OEM copy of XP is running on the laptop it was shipped with, using the processor, motherboard and memory etc that it is licensed for.  

Surely if a user uses their OEM copy in this way they are at the least doing right by the spirit of the law, if not the actual nuances of the EULA.  

I would say that is fine but then I am no legal expert.  As a user I try my best to stay on the rightside of licensing and copyright.  It is such a minefield that sometimes one has to just satisfy yourself that you are keeping within the spirit of the law.

---

### Post by xrchris on 2008-05-10
I was really getting at whether Vista will actually be able to *see* the embedded hardware information it requires so as not to request reactivation etc. 

I was under the impression that when Vista runs within the virtual environment then this is not possible but I was wondering if anyone could clarify this.

---

### Post by wheredidrealitygo on 2008-05-10
The XP EULA does not say anything for or against Virtualization, they only started mentioning Virtualization specifically with the advent of Vista. 

Having worked at the product activation centre myself, we activated OEM copies virtualized within the same computer all the time. So long as it literally stays on the same computer (doesn't matter on how many partitions, or hard drives, or virtualized versions, note: this is for XP only)

The Vista eula specifically states (for Home Premium/Basic):

USE WITH VIRTUALIZATION TECHNOLOGIES. Instead of using the software directly on the licensed device, you may install and use the software within ***_only one virtual (or otherwise emulated) hardware system on the licensed device_***. When used in a virtualized environment, content protected by digital rights management technology, BitLocker or any full volume disk drive encryption technology may not be as secure as protected content not in a virtualized environment. You should comply with all domestic and international laws that apply to such protected content.

Which can be found here: [http://download.microsoft.com/documents/useterms/Windows%20Vista%20SP1_Home%20Premium_English_63a4cc63-b747-4b8a-8b37-8fa5040d2306.pdf](http://download.microsoft.com/documents/useterms/Windows%20Vista%20SP1_Home%20Premium_English_63a4cc63-b747-4b8a-8b37-8fa5040d2306.pdf)

The point of virtualization is so that the hardware stays separate from the software (so the virtual machine is isolated and invulnerable, and what stays on it does not get spread to the host machine, so it will definitely ask for activation.

---

### Post by Nampla on 2008-05-14
This is why I would like to hand a big thanks to all the people involved in Ubuntu and all the other open source OS.  I am sick to death of microsoft and their proprietery greed!!! isnt 73+ billion enough f****n money for bill!!!
Keep up the good work

---

### Post by mr_byte on 2008-09-29
Personally, I don't give a fsck if I'm legal or not, as I doubt very seriously that M$ Goons will be pounding on my door.  However, I do have licenses for my XP and my Vista copies here, and as I understand it, Vista also allows you to downgrade to XP.

I run 1 copy of the given OS at a time, on the machine it is licensed for.  I use WGA hacks and a VLK, not because I'm running pirated (well, I guess I am running pirated software, if you consider the source for the installs) but because I hate activation and WGA and all the phone home crap M$ pulls.

The EULA may restrict this, that, and the color of my toilet paper, but I keep to the idea of "One license per physical machine" and for me, that means I run it however I like, so long as I have a license.  I had 2 copies of XP on physical partitions and 1 virtualized on this laptop, at one time, now I am 1 and 1, with Sabayon Linux as my main OS.

Any contract (as EULAs are) that cannot be understood by a person of average intellect should be void. And anything that can have multiple interpretations should be void, as well.

My $.02 worth.

Jeff

---

### Post by RealG187 on 2008-09-29
> **mr_byte said:**
> Personally, I don't give a fsck if I'm legal or not

Neither do I.

SOme parts of the EULA are understand able, like not using on more than one computer*, but to tell you which type of computer is too far.

* At the cost of over $100 a disk, one should be able to use this disk with as many PCs as they like, not just one though...

---

