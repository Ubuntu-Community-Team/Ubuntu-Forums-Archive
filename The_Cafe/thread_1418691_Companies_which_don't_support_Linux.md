---
title: "Companies which don't support Linux"
date: 2010-02-28
forum: The Cafe
---

### Post by Timtro on 2010-02-28
Hi All,

I'm writing an article, and I'm going to mention a couple of companies that don't support Linux well. Two companies that immediately came to mind are Canon and ATI. But it appears that ATI has gotten better in recent years.

Can anyone suggest another company which fails to support us?

Thanks!

---

### Post by 2hot6ft2 on 2010-02-28
Microsoft;)
Lexmark
Kodak

---

### Post by Linuxforall on 2010-02-28
CANON.......stay away from their products.

---

### Post by Primefalcon on 2010-02-28
Apple?

---

### Post by Timtro on 2010-02-28
Thanks for those.

Are there any companies that aren't mainly printer manufacturers?

Actually, I had tentatively written in Apple, after a recent experience I've had with an ipod. But I thought I would stay away from companies that produce OSs. The point I'm making is specifically about hardware.

I'll post a link to the article when I'm done. The article is about how Chrome OS could make it profitable for companies to support Linux and might lead to us taking a bigger piece of the desktop market.

Thanks a lot!

---

### Post by prshah on 2010-02-28
Linux device support usually depends on the chipset underpinning the device. For example, a few years back, most wireless chipsets were using a variant of the Realtek 818x family; this was recently unsupported (directly) until Ubuntu 8.04, which had a native RealTek 8187 kernel module. 

So basically, you are looking for unsupported chipsets. Sometimes, even supported chipsets fail due to non-standard implementations. The manufacturer sometimes switches chipsets without changing product name or model number.

Examples of unsupported (directly) or poorly supported chipsets:
 = Graphics cards: via chrome
 = Canon scanners LIDE 100 onwards (prior models used gl840 chipset, LIDE 100 uses gl841 chipset).
 = Audio : while intel_hda_audio is mostly supported, a few vendors have implementation bugs, which they work around in the driver software (Eg jack sensing, reassignment, etc). Note that the audio spec itself is solid; poor implementation by cheap-as-chalk vendors is the cause.
 = Most TV Tuner cards based on the SAA713x and 878bt chipsets. While there are a few good models available that work right out of the box, the cheapers ones don't and require a lot of experimenting with the "model=" module parameter to get workng.
 = via USB chipsets are known to be problematic at times, though this is more of a platform specific problem, I think.
 = USB webcams (again the cheaper ones) which have non-standard implementation for standardized chipsets. Typical chipsets: cannot recall right now, will post back later.

I think you will have to point out in the article that unsupported chipsets are usually the cause of the problem.

---

### Post by john newbuntu on 2010-02-28
From an application perspective, Citibank.  And then you add the "user agent switcher" add-on to firefox and they are happy.

---

### Post by robertcoulson on 2010-02-28
Especially Lexmark...Wrote them to complain about my printer not working on Ubuntu and their reply was "Call us and we will give you 25% off coupon on your next purchase of a Lexmark printer"...Yikes.
Robert

---

### Post by dcstar on 2010-02-28
> **john newbuntu said:**
> From an application perspective, Citibank.  And then you add the "user agent switcher" add-on to firefox and they are happy.

Yep, still too many websites are IE and/or Windows dependant - far too many to mention here.

If I ever come across one I usually complain bitterly and state that they have just lost my business - and possibly many other non-Microsoft users as well - because of this....... and also state that only crap websites are not browser agnostic.

A lot seem to get the message and (eventually) change - but only because people have bothered to complain directly to them.

---

### Post by Endomancer on 2010-02-28
Kaiser baas don't support Linux.
I got one of their digital photo keyrings for xmas and it wouldn't work with Ubuntu, I sent an email asking if they had a linux version of the installation softwear, to which they replied 
"
Unfortunately there is no Linux software available. The software is designed to be used with the Windows operating system.
 
Thanks
Hasan

I still don't see why it can't be a plug and play item with drag and drop file transfer, then installation wont be necessary

---

### Post by asmoore82 on 2010-02-28
Go for the big fish.

Apple.
Best Buy.

Acer!

DELL!
Dell's Linux offerings conspicuously went away just in time for Windows 7.
I tried to order my girlfriend a dell mini with Ubuntu just before
Christmas and they wouldn't do it. I started customizing it on their site
and moved to the phone to finish the order and they said it wasn't
offered. I said it was on their website. They said that if I had
completed the order there I would've been Emailed shortly to be
informed that it wasn't available anymore.

The same model is *still* shown on their website!
What's the deal??

---

### Post by Endomancer on 2010-03-08
One of the biggest fishes here in Australia.

**Telstra BigPond  **(my ISP) only offers tech support for 

• Windows 2000 
• Windows XP 
• Windows Vista

 They say they do not offer support for Mac and they don't even mention Linux

[http://bigpond.custhelp.com/cgi-bin/bigpond.cfg/php/enduser/std_adp.php?p_faqid=5624&p_created=1086238694&p_sid=7ak4cjWj&p_accessibility=&p_redirect=&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9OTAsOTAmcF9wcm9kcz0mcF9jYXRzPSZwX3B2PSZwX2N2PSZwX3BhZ2U9MSZwX3BsYXRmb3JtPU4mcF9zZWFyY2hfdGV4dD1saW51eCBzdXBwb3J0&p_li=&p_topview=1](http://bigpond.custhelp.com/cgi-bin/bigpond.cfg/php/enduser/std_adp.php?p_faqid=5624&p_created=1086238694&p_sid=7ak4cjWj&p_accessibility=&p_redirect=&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9OTAsOTAmcF9wcm9kcz0mcF9jYXRzPSZwX3B2PSZwX2N2PSZwX3BhZ2U9MSZwX3BsYXRmb3JtPU4mcF9zZWFyY2hfdGV4dD1saW51eCBzdXBwb3J0&p_li=&p_topview=1)

---

### Post by puzzler995 on 2010-03-08
Dynex/Best Buy. I walked up to a sales guy in Best Buy and the second I said Ubuntu he said "good luck with that". 

And I have a Canon Pixma MP210 and have had no problems.

---

### Post by Psychodox on 2010-03-08
While all the buttons on my Logitech Mouse and Wacom3 tablet work like I want them too, it is a fairly involved process to get them recognized properly and functioning like I want. There is no support from either manufacturer that I could find. A ton of thanks though to these Ubuntu forums for getting me where I am :D, and others in the same situations! :D

---

### Post by PhilGil on 2010-03-08
How about RIM - a large and influential Canadian corporation?  They provide no Linux support for their Blackberry smartphones.

---

### Post by redbook4574 on 2010-03-08
> **Timtro said:**
> Hi All,

I'm writing an article, and I'm going to mention a couple of companies that don't support Linux well. Two companies that immediately came to mind are Canon and ATI. But it appears that ATI has gotten better in recent years.

Can anyone suggest another company which fails to support us?

Thanks!

I think you may find the shorter list will be companies which do support linux, but their loss we manage without them I think.

---

### Post by DeMus on 2010-03-08
What to think of Sweex?
They make a lot of products which need drivers, but drivers for Linux??? No way!!!
So, until they better their lives, don't buy Sweex.

---

### Post by fragos on 2010-03-08
Many products work with Linux by virtue of the chip sets used, non-proprietary protocols and the choice of hardware interface. However the vendors that manufacture those devices frequently don't advertise or claim support for Linux. Googling around you can find many compatibility lists. Personally I stick with Linux friendly vendors like Nvidia for graphics cards, HP for Printers and scanners and Hauppauge for TV cards. I for one continue to be amazed at how well Linux supports hardware automatically. I just changed out my motherboard and went to a new CPU. Dispite the fact that all the supporting chip sets on the mother board were different than my prior system my new system booted right up with the disk and Ubuntu OS build from the older system. Try that with Windows.

---

### Post by MichealH on 2010-03-08
You have all lost your mind what about...
[SIZE="6"]SIS?!?![/SIZE]

The company who put the Graphics in my Computer and now I have a 1/2 hour task of getting my screen resolution to 1280x800 (my native resolution.)

---

### Post by derande on 2010-03-08
> **PhilGil said:**
> How about RIM - a large and influential Canadian corporation?  They provide no Linux support for their Blackberry smartphones.

agreed. 
they finally release a desktop manager for mac late last year but zero linux love. 

i get frustrated when i have to call the dummies @ at@t to report a dsl outage. in their troubleshooting "checklist" i always get the "we're sorry but we don't support your operating system" as the operating system that i run on one computer connecting to my wireless router would determine THEIR outage.

---

### Post by DawieS on 2010-03-08
**Canyon** - More specifically their **Web-cam** division.

About a year ago, I e-mailed them, requesting support in terms of Linux drivers. Their reply was short: They do not support Linux.

I got the web-cam working in the meantime, although the image is not up to scratch - it also has to be unplugged frequently from the USB port to resume after freezing - definitely a driver problem.

---

### Post by RedRat on 2010-03-08
> **prshah said:**
> Linux device support usually depends on the chipset underpinning the device. For example, a few years back, most wireless chipsets were using a variant of the Realtek 818x family; this was recently unsupported (directly) until Ubuntu 8.04, which had a native RealTek 8187 kernel module. 

So basically, you are looking for unsupported chipsets. Sometimes, even supported chipsets fail due to non-standard implementations. The manufacturer sometimes switches chipsets without changing product name or model number.

Examples of unsupported (directly) or poorly supported chipsets:
 = Graphics cards: via chrome
 = Canon scanners LIDE 100 onwards (prior models used gl840 chipset, LIDE 100 uses gl841 chipset).
 = Audio : while intel_hda_audio is mostly supported, a few vendors have implementation bugs, which they work around in the driver software (Eg jack sensing, reassignment, etc). Note that the audio spec itself is solid; poor implementation by cheap-as-chalk vendors is the cause.
 = Most TV Tuner cards based on the SAA713x and 878bt chipsets. While there are a few good models available that work right out of the box, the cheapers ones don't and require a lot of experimenting with the "model=" module parameter to get workng.
 = via USB chipsets are known to be problematic at times, though this is more of a platform specific problem, I think.
 = USB webcams (again the cheaper ones) which have non-standard implementation for standardized chipsets. Typical chipsets: cannot recall right now, will post back later.

I think you will have to point out in the article that unsupported chipsets are usually the cause of the problem.

Well yes that is true, it is the chipsets, but unfortunately we lowly users do not buy chipsets, we buy the final device whatever that is. It is the company, e.g., Dell, HP, Canon, etc, that decide which chipset they will buy and use. I don't believe that going into chipsets was the point of the original request. I think the intent of the article is a good one. Perhaps if certain companies were mentioned in a slightly "bad light" they might think twice or perhaps consider that Linux is important.

---

### Post by fragos on 2010-03-08
> **DawieS said:**
> **Canyon** - More specifically their **Web-cam** division.

About a year ago, I e-mailed them, requesting support in terms of Linux drivers. Their reply was short: They do not support Linux.


Few companies claim Linux support but that has nothing to do with their hardware being well supported by Linux without their envolvement. The question should be does the Linux community support a particular piece of hardware.

---

### Post by ibuclaw on 2010-03-08
Moved to the Cafe, if no one has any objections.

Regards
Iain

---

### Post by katie-xx on 2010-03-08
Wow!! what a subject .... Companies which dont support Linux!!
I would assume you are talking about hardware ?
Well there may be any number of reasons but I would guess the bottom line decides if a hardware company is going to make a datasheet available or, alternatively, produce a driver for Linux.The world does not owe the Linux project a living.

I see quite a lot of instruments or pieces of hardware which actually run Linux but expose an interface which Linux cant consume :) Figure that one out ..and believe me it isnt unusual.
I know there are a few people on here who would argue about that so if you want confirmation check out Kepware, Iconics, Foxboro, Hexatec, Wonderware, Schneider, and many more. Believe me  ... real time data acquisition is a totally different paradigm to what you guys do so well ... and, in particular ..DCOM just cannot hack it!! Sorry business IT guys ..but I speak the truth :) You do your thing and Ill do mine !!

So why cant Linux, I ask, take advantage of the position it has forged for itself running on embedded systems. The money is on the other side .....pulling it all together.

So essentially im putting your question back to you .... why doesnt Linux get used more for the things it would seem to be suited to ??? 
its now got a mountain to climb in terms of proving reliability ... Windows had the same problem circa 1995 or so ....but managed it :) If you want details on that please ask ..very interesting story. A company called Hexatec made the first Windows based Scada available for free download over the internet.
Amazingly ..you got a 3 hour licence to try it out. That hasnt changed much ..an evaluation now is typically 3 hours for most suites :)


Kate

---

### Post by JDShu on 2010-03-08
Hmm I think it would be useful to compile a list so that people know what to avoid. Kinda like a reverse HCL. 

I guess I'll add Broadcom, which does support Linux, but can cause a lot of grief.

---

### Post by Jarmen_Deffs on 2010-03-08
> **JDShu said:**
> Hmm I think it would be useful to compile a list so that people know what to avoid. Kinda like a reverse HCL. 

I guess I'll add Broadcom, which does support Linux, but can cause a lot of grief.

A little bit unfair I think. I've had some trouble with their drivers too, but they do actually go to the trouble of putting Linux drivers on their site...

---

### Post by takisan on 2010-03-08
Not directly related, but I am running Karmic on hardware from the late 90s. Works like a charm. Um: I'd say a lot of stuff is not supported by Linux Directly. There are alternative drivers but they are not the ones to run on it. They can still work, but not as brilliantly as if having the proprietary drivers on Win or Mac.

---

### Post by fragos on 2010-03-08
@takisan -- <marquee> is markup proprietary to IE and not supported by others.

---

### Post by BuffaloX on 2010-03-08
I would remove ATI from that list, maybe their support isn't stellar, but they make Linux drivers and they've opened specifications.

Saying they don't support Linux is a lie, if it's good enough, is a matter of opinion.

Are you only asking for hardware companies only?

Best buy:
[http://www.linuxinsider.com/rsstory/69073.html]("http://www.linuxinsider.com/rsstory/69073.html")

Some companies such as ISPs banks and others with hot-line support don't support Linux, but most accept it if you can figure it out yourself.

---

### Post by lindsay7 on 2010-03-08
No one has brought up Intuit, makers of Quicken and TurboTax.  They could care less.

---

### Post by Ric_NYC on 2010-03-08
Netflix.

---

### Post by Ric_NYC on 2010-03-08
Autodesk (AutoCAD).

---

### Post by PC_load_letter on 2010-03-08
Almost any company that manufactures pro or semi-pro audio software or hardware that connects to a computer, e.g. audio interfaces, midi controllers, musical instruments. most of these companies have very minimal or nonexistent Linux support. 

If I'm gonna choose one company in this category, it has to be the **Yamaha owned Steinberg**, which by the way, until this day, requires that you register on their web site in order to download the free (as in beer I guess) VST SDK which is needed to run ANY VST host w/ wineasio under wine. 

Or **Muse research**, with their product the "Receptor", which is actually a freakin' Linux box running Windows VST instruments. But get this, the company does not support Linux on the user's end. The "Receptor Remote Control" software that allows you to download/upload presets from and to your computer is only available for Windows & Macs. Doesn't get any more ironic than this!!!](*,)

---

### Post by Ric_NYC on 2010-03-08
Yahoo?

---

### Post by spillin_dylan on 2010-03-08
There are a lot of very specialized proprietary hardware vendors that lean towards the Windows proprietary platform, because in my opinion that is part of there security model.  Not security as in viruses & firewalls, but security as in coding and "intellectual property".  

Whether or not you believe in "intellectual property" is completely up to you; I'm all for open-source, but I can understand the business model of selling something that consumers want to those consumers.  

PC_load_letter's comments regarding music recording and production hardware are very valid -- there are a few vendors that actually support freely recording audio on any platform with their hardware, but there definitely are a few that are Windows Only.

katie-xx also makes a great point regarding SCADA hardware and software, and in general most PLC/DCS control systems are still based off of Windows, because those industries are still in the "stone-ages" when it comes to open-source.  Proprietarism (?) is everything there, and any given product will try and promise you everything in order to out-sell the competition.  I will give credit - I have seen (never used) Isagraf for Linux.  

I personally think that Apple is a big hinderance with their absolute refusal of allowing an iPod to work on Linux.  Of course, people have been working on this to find ways to sync properly and whatever, but Apple still continually finds ways to break any developments the open-source community makes.  I hate to say it, but iTunes in Virtualbox is still the best way to sync my 6th Gen iPod Classic.  See further down regarding my Palm Pre.

I think that as long as these types of companies are trying to make a profit attempting to sell the "next big thing" in their industry, then they will stick with Windows, as it isn't as open and free as Linux, thus preventing (or at least limiting) (or at least attempting to limit) the opportunities to reverse-engineer, or otherwise develop any interface means.  Webcams, USB hubs, digital cameras, no big deal; basic consumer items that 95% of the population uses, so we (well, the actual developers - props to them!) can develop work-arounds to interface with that.  But these specialty devices and applications will continue to be developed "Windows only" as long as that's one extra layer of protection for their so-called intellectual property.

After this long rant, I desparately give thanks to Palm for the Pre smartphone.  The new WebOS is based on Linux (even Debian, I think?) and works OK (sure, it's new with a few bugs....), but gives me the freedom to do whatever I want with it.  It is super easy to gain root access, and from there, you actually own the hardware you bought.  Just like real Linux :).  And it syncs with iTunes as an iPod!  Okay, enough bragging up my phone.

I guess that's it, then.  I vote for Apple as a company which doesn't support Linux.

---

### Post by RedRat on 2010-03-08
Well as a Linux user who must make a choice of what device to buy, you have two choices for requisite support: 1) You rely on the manufacturer of the hardware (who is probably best suited to actually give support), or 2) the open source community (who are probably the least suited to support hardware). 

Once can argue that community can do this, however, there are indeed legal issues here about back-engineering drivers or digging too deeply into device software. Luckily, most hardware companies that cannot bring themselves to give Linux support, more than likely are not greatly bothered by community back engineering. They may feel they made a sale and that any back-engineered driver or other software would have minuscule sales that it would not impact their corporate bottom line. I suppose there are some that would give a hearty thanks to the Linux community for doing their job for them. 

Again, since Linux is only a small percentage of all computer users, I don't see a lot of companies falling all over themselves to offer Linux support now or in the immediate future. Until Linux becomes a significant portion of the total field of computers out there, I don't see much help.

---

### Post by phrostbyte on 2010-03-08
Cheapo Lexmark printers don't support Linux because they are "winprinters", they actually offload a lot of what a typical printer does to the drivers running on the computer. This way they can use a weaker ASIC and save something like 50 cents when they make the printer. It's only their cheapo printers that are affected.

---

### Post by puzzler995 on 2010-03-09
> **lindsay7 said:**
> No one has brought up Intuit, makers of Quicken and TurboTax.  They could care less.
Well we were talking about hardware but if you want  to bring up software I think we know who the biggest offender is...

_***[SIZE=7][COLOR=Red]ADOBE[/COLOR][/SIZE]***_
How many of us have had to go through back doors to install their excuse of a flash player and PDF reader (the only Linux software they offer). They are in it for money and dont give a darn what the people think.

---

### Post by celem on 2010-03-09
Charles Schwab is very anti-Linux. Their StreetSmartPro trading platform uses Internet Explorer's libraries an is Microsoft only. The real crime is their specialty trading website, StreetSmart.com. It requires the Sun Java engine, states that it does not support the Microsoft jre, cites support of Firefox and IE on Windows and the Firefox and Safari on MacOS yet Firefox on Linux fails.

---

### Post by samalex on 2010-03-09
> **Timtro said:**
> Hi All,

I'm writing an article, and I'm going to mention a couple of companies that don't support Linux well. Two companies that immediately came to mind are Canon and ATI. But it appears that ATI has gotten better in recent years.

Can anyone suggest another company which fails to support us?

Thanks!

Crystal Decisions (or whatever they're called now).  The folks who make Crystal Reports.  On Windows it's about the best reporting tool I've used, but they have no support outside of Windows.

Sam

---

### Post by gsmanners on 2010-03-09
The worst offenders are the game companies. Among the top of those, many have made secret deals with Microsoft or have been bought out entirely. The only company among them that offered Linux versions of their games was id, and even they are moving away from Linux thanks to the epidemic stupidity of investors nowadays (for example, the Ubisoft fiasco).

---

### Post by swoll1980 on 2010-03-09
> **fragos said:**
> Many products work with Linux by virtue of the chip sets used, non-proprietary protocols and the choice of hardware interface. However the vendors that manufacture those devices frequently don't advertise or claim support for Linux. Googling around you can find many compatibility lists. Personally I stick with Linux friendly vendors like Nvidia for graphics cards, HP for Printers and scanners and Hauppauge for TV cards. I for one continue to be amazed at how well Linux supports hardware automatically. I just changed out my motherboard and went to a new CPU. Dispite the fact that all the supporting chip sets on the mother board were different than my prior system my new system booted right up with the disk and Ubuntu OS build from the older system. Try that with Windows.

I had just built a machine less than a month ago. The motherboard took a crap, and I went to microcenter to return it. The model I had was sold out, so they offered me a superior board at the same cost. This board had a completely different chip set. It also had a different nic, sound, and graphics card. To my amazement Window 7 fired right up. I had to re-verify it's authenticity, other than that it went off without a hitch.

---

### Post by murderslastcrow on 2010-03-09
On that note, Steam is being ported to Mac OS X in April! This good because, it may mean most of the games available for Steam will be redeveloped for compatibility. And if that means developers start depending on more platform independent tools, at the very least it would make more Steam games work in Wine over time, or at least have OpenGL modes and less Win32-specific code.

I don't think it would be too hard to port it to Ubuntu with the Software Store evolving like it is, so maybe we'll get those games, too! Then again, most people seem to have Steam installed under Wine and play most of its games anyway.

But yeah, I think it's less of "who doesn't support Linux" and more of, "who lets the incentive of majority market share allow them to neglect the rest of the software consumers in the world?" I mean, it may be more appropriate to ask who makes OS X software but not Linux software. Those are the people who have much less excuse for their exclusivity.

Either way, those days are coming to a close. As Microsoft eventually becomes less and less compatible with XP and they force people to "move on," developers and consumers will have more of a chance to make a transition to multiple systems, and people are more conscious of the value of their systems these days.

To be honest, the niche gaming market (MMOs and next-gen games you can't play with a gamepad, or would like to mod) are the largest crowd with money to move the market to another platform. Even if Adobe made everything for Linux, all the advanced CAD and office software got ported over, and every company gave it official support, There would still be a ton of people refusing to use Linux just because they want a brand name game or two.

I'm happy either way. If our designer tools become fully compatible with the latest Adobe formats, soon Windows will be nothing but an extremely poorly designed game console. In that case, I could care less if people use it XD.

---

### Post by puzzler995 on 2010-03-09
> **murderslastcrow said:**
> I'm happy either way. If our designer tools become fully compatible with the latest Adobe formats, soon Windows will be nothing but an extremely poorly designed game console. In that case, I could care less if people use it XD.

Yep thats called the Xbox 360 ;)

---

### Post by nuffink666 on 2010-03-09
There will never be a massive support for linux for a number of very simple reasons - its free - it works equally as good thanks to the dedication of those who contribute and because its free it doesnt make money and thats what companies bottom line is. Some will always see the bigger picture, IBM for instance support Suse and Fedora for a number of their enterprise and commercial products but those that "utilise" operating systems with the idea of giving the purchaser something for nothing will side with windows cos it dominates and its easy. The biggest offender IMHO to the detriment of linux is Adobe - this is a company that offers free readers and and free flash players etc etc but why not go that bit further and not for free but at least port things like Lightroom, Photoshop and the like to linux and instead of being a puppet of Bill be a truly cross platform product, cant believe its that hard TBH  

Rant over but Adobe to a point :)

---

### Post by cb951303 on 2010-03-09
3ds Dassault Systems

Owner/developer of the largest MCAD suites in the industry (SolidWorks and Catia).

They don't support Linux. Or any other OS -other than Windows- for that matter.

---

### Post by Mike'sHardLinux on 2010-03-09
Doesn't Toyota use Microsoft gas pedals? :-&

---

### Post by MasterNetra on 2010-03-09
Well the european website for cannon provides some linux drivers for their products. Which searching for drivers they have linux in the OS thing. certainly they could with having more linux installable drivers, but its a start.
I don't think Gateway supports linux.

---

### Post by squilookle on 2010-03-09
> **Endomancer said:**
> One of the biggest fishes here in Australia.

**Telstra BigPond  **(my ISP) only offers tech support for 

• Windows 2000 
• Windows XP 
• Windows Vista

 They say they do not offer support for Mac and they don't even mention Linux

[http://bigpond.custhelp.com/cgi-bin/bigpond.cfg/php/enduser/std_adp.php?p_faqid=5624&p_created=1086238694&p_sid=7ak4cjWj&p_accessibility=&p_redirect=&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9OTAsOTAmcF9wcm9kcz0mcF9jYXRzPSZwX3B2PSZwX2N2PSZwX3BhZ2U9MSZwX3BsYXRmb3JtPU4mcF9zZWFyY2hfdGV4dD1saW51eCBzdXBwb3J0&p_li=&p_topview=1](http://bigpond.custhelp.com/cgi-bin/bigpond.cfg/php/enduser/std_adp.php?p_faqid=5624&p_created=1086238694&p_sid=7ak4cjWj&p_accessibility=&p_redirect=&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9OTAsOTAmcF9wcm9kcz0mcF9jYXRzPSZwX3B2PSZwX2N2PSZwX3BhZ2U9MSZwX3BsYXRmb3JtPU4mcF9zZWFyY2hfdGV4dD1saW51eCBzdXBwb3J0&p_li=&p_topview=1)

I contacted my isp a few years ago (then NTL, now Virgin Media) to ask about Linux support the response I got back was fair enough - "We do not support Linux, but it will work". 

My bank is NatWest, they're picky about your browser/os combination. They support ie and firefox on Windows and Safari and Firefox on the Mac, but when I tried to log in using Firefox on Linux it would not let me. However, I did manage to log in using Konqueror, identifying itself as IE 6 on XP. It worked absolutely fine. My other bank, Nationwide handle it much better. You get a notice saying your browser/os is not supported but will PROBABLY work with no problems, and that you can try it at your own peril and it works fine.

---

### Post by spcwingo on 2010-03-09
How about Yardi Systems, Inc.?  Specifically a web-based program called Voyager.  It only supports the MS Win/IE combo (Using user agent switcher makes no difference).  Here's a link to their site:

[http://www.yardi.com/US/YardiVoyagerFamily.asp]("http://www.yardi.com/US/YardiVoyagerFamily.asp")

---

### Post by Timtro on 2010-05-06
> **squilookle said:**
> 

My bank is NatWest, they're picky about your browser/os combination. They support ie and firefox on Windows and Safari and Firefox on the Mac, but when I tried to log in using Firefox on Linux it would not let me...

Funny, a lot of Banks recommend Linux. Institutions including the ABA have come out and said that Windows and IE should not be used for online banking.

---

### Post by blueturtl on 2010-05-06
> **Linuxforall said:**
> CANON.......stay away from their products.

You've got to be careful giving out general statements like that. Brands like Canon produce a lot of different kinds of things.

In the case of Canon their printers are mostly unsupported, but for example their digital cameras work great. It doesn't make sense to tell people to stay away from both especially as the PowerShot series are practically always winners in their class.

---

### Post by MacUntu on 2010-05-06
IMO it's more useful to promote vendors that **do** support Linux.

---

### Post by Ylon on 2010-05-06
in 2003 Nvidia lost the contract with Microsoft to build the first Xbox's GPU chipset ([article](http://articles.sfgate.com/2003-08-15/business/17502789_1_nvidia-corp-microsoft-and-nvidia-nvidia-shares)). From 2003 nvidia now provide the best proprietary driver for Linux...
On contrary ATI (who "won" the contract with Microsoft afterwards) did make the worst ones.


The Xbox CPU is IBM... but IBM still support Linux 100%: xbox or not.


I think that ATI will still the most "linux unfriendly" company so long it's such Microsoft's partner.

At this moment nvidia it's the best one... but their driver are proprietary: this mean any time their support to linux would end. Peroid. (ie: Microsoft call nvidia back to build gpu for xbox 720)


All this for say: it's not easy to say which is friend or not. Things can change with just a contract.

---

### Post by xir_ on 2010-05-06
> **Timtro said:**
> Hi All,

I'm writing an article, and I'm going to mention a couple of companies that don't support Linux well. Two companies that immediately came to mind are Canon and ATI. But it appears that ATI has gotten better in recent years.

Can anyone suggest another company which fails to support us?

Thanks!

ATI is amazing at supporting linux. Their open documentation policy is slow but brilliant. Their new open source driver code (which they pay people to actively work on) is advancing quickly.

In fact you can even speak to the devs at phoronix.

---

### Post by ibuclaw on 2010-05-06
> **MacUntu said:**
> IMO it's more useful to promote vendors that **do** support Linux.

I agree, has anyone seen this? [http://www.wolfire.com/humble](http://www.wolfire.com/humble)

I think I might put £20 or £30 aside to help out with my support (besides, I enjoyed the demos of at least 3 of those games ;)).

---

### Post by Techsnap on 2010-05-06
> Two companies that immediately came to mind are Canon and ATI.If you don't know anything about the companies which you are quoting then don't even mention them, I've never had experience with Canon on Linux but ATi not supporting Linux? Get out of here! They have released their specification for goodness sake.

---

### Post by kellemes on 2010-05-06
> **MacUntu said:**
> IMO it's more useful to promote vendors that **do** support Linux.

Indeed..

By the way, I don't see why companies should be criticized for not supporting Linux.. It's there company, they make there own choices. If you happen to use Linux and want a functioning Printer, go find one that's compatible or use another os.

---

### Post by Techsnap on 2010-05-06
> By the way, I don't see why companies should be criticized for not  supporting Linux.. It's there company, they make there own choices.

I agree, it's their choice and it all leads to if it's going to commercially viable or not.

---

### Post by cap10Ibraim on 2010-05-06
***Microsoft supports Linux***
example just today 
Version 2.1 of the Integration Services Microsoft is offering for the open source Linux operating system is extremely close to finalization. On May 5th, 2010, the Redmond company started offering Linux Integration Services v2.1 Release Candidate to early adopters running mixed source environments. The RC development milestone of Linux Integration Services 2.1 is available for download via Microsoft Connect. At the time of this article, Connect was down, but the site will undoubtedly be up and running in no time for those that are looking to start test-driving Linux Integration Services 2.1 RC as soon as possible. 

“In March, we had announced the beta release of the Linux Integration Services for Microsoft Hyper-V, which added support for SMP-based virtual machines, timesync, and integrated shutdown. Today we're announcing the release candidate (RC) version of the integration services,” a member of the Microsoft Virtualization team revealed. 

As it was the case with the previous releases of the Linux Integration Services, version 2.1 comes with support for Windows Server 2008 Standard, Enterprise, and Datacenter (x64 only), Microsoft Hyper-V Server 2008, Windows Server 2008 R2 Hyper-V Standard, Enterprise, and Datacenter (x64 only), and Microsoft Hyper-V Server 2008 R2. In terms of Linux distributions, Linux Integration Services 2.1 RC is designed to play nice with Novell SUSE Linux Enterprise Server 10 SP3, SUSE Linux Enterprise Server 11, and Red Hat Enterprise Linux versions 5.2, 5.3, 5.4 and 5.5.

“In addition to the features that were present in the beta release, the following features have been added for this release candidate: Heartbeat: This provides a way for the host to detect if the guest is still running and responsive. Pluggable Time Source: A pluggable clock source module is included for a more accurate time source to the guest,” the Microsoft Virtualization team representative 
[http://news.softpedia.com/news/Microsoft-Linux-Integration-Services-2-1-Hit-RC-141446.shtml]("http://news.softpedia.com/news/Microsoft-Linux-Integration-Services-2-1-Hit-RC-141446.shtml")

---

### Post by RedRat on 2010-05-06
As to Canon printers I have been using my Canon i860 for over 3 years using the CUPS-Gutenberg system. The only thing that I miss is the "ink running out" notices. But other than that, printing on this now old machine is quite good. Of course, I cannot speak to the newer printers of Canon, but mine is working fine.

---

### Post by Ylon on 2010-05-06
> **cap10Ibraim said:**
> ***Microsoft supports Linux***
example just today 

The biggest dream of Microsoft is the *possibility*, for them, to talk directly with companies which want to give a try with linux. 
"*Ask us how you can solve your problem with linux... we'll show you what's a linux problem*" :popcorn:

---

### Post by rbrauns on 2010-07-10
Hauppage can be added to the list if not mentioned already

---

### Post by Ric95 on 2010-07-10
Disney.
If you want one of their 'printable coupons' or some other interactive perk, you need to install a small .exe that verifies you are only printing the allowed number of coupons. 
 They'd have saved a lot of effort by just pricing their movies more competitively.

---

### Post by fragos on 2010-07-10
> **rbrauns said:**
> Hauppage can be added to the list if not mentioned already

They don't mention Linux support but I know for a fact that their cards have been well supported by the BTTV and IVTV open source drivers for a long time. Wacom is another that doesn't mention Linux support but their tablets are also have been well supported by Linux. I find it difficult to fault a company whose products work well with Linux even though not officially supported on their web site or marketing literature.

---

### Post by JC Cheloven on 2010-07-11
Regarding lack of linux support: TASCAM is outstanding (it makes audio devices)

---

### Post by renkinjutsu on 2010-07-11
> **2hot6ft2 said:**
> Microsoft;)
Lexmark
Kodak

I don't know if anyone's posted this yet but.. Lexmark *does* support linux.

more details here:
> [http://www.phoronix.com/vr.php?view=14735](http://www.phoronix.com/vr.php?view=14735)

---

### Post by celldweller1591 on 2010-07-11
IMO ..indian companies like BSNL, Airtel, Infosys, TCS, HCL do not support linux at all  as my surces told me...but i may be wrong about TCS and Infosys.

---

### Post by RedRat on 2010-07-11
> **JC Cheloven said:**
> Regarding lack of linux support: TASCAM is outstanding (it makes audio devices)
Perhaps I am misunderstanding your coment about TASCAM, do you mean that they are "outstandingly" bad at supporting Linux or that they are "outstandingly" good at supporting Linux. Outstanding usually means a good thing, but it can also mean a bad thing too.

---

### Post by metalf8801 on 2010-07-11
Netflix watch instantly works on Windows, Mac OS X, PS3, Xbox 360, the Wii, the iPad, and even the Linux based Roku set top box along with several other devices but it doesn't work on any Linux desktops OS

PS
Hasn't Ati support gotten a lot better while Nvidia's support going down hill?

---

### Post by JC Cheloven on 2010-07-11
> **RedRat said:**
> Perhaps I am misunderstanding your coment about TASCAM, do you mean that they are "outstandingly" bad at supporting Linux or that they are "outstandingly" good at supporting Linux. Outstanding usually means a good thing, but it can also mean a bad thing too.

Sorry, I intended to use a bit of irony with the word "outstanding", which is (afaik) generaly used for good things. Perhaps I shoudn't use any irony as I'm not native and I may lead to confussion. So to be clear:

TASCAM has absolutely no support for linux. They simply don't care. If a tascam device works is by hazard, due to achitecture coincidences. And if a customer (like me) asks about that, the answer is simply "we don't support linux, sorry". I sold out my old good FW1804 because of that, after switching to linux. EDIT: and I've also read comments about tascam being plain hostile to linux devels requests of information about their products.

I hope to have made it clearer ;)
JC

---

### Post by Naitsirhc Hsem on 2010-07-11
Netflix +1

---

### Post by jerenept on 2010-07-11
Internet companies (ISP). If you tell them you are running Linux, hard luck for you, even if the problem is on your side. Once, the cable company in my country blamed their constant irregular service on my wireless router (DD_WRT-WRT54G) when it was their fault.

---

### Post by fragos on 2010-07-11
The last place to find out if a device is supported by Linux is from the manufacturer. The right place is here. It wasn't that long ago that Comcast support told customers they had to have Windows to use the Internet. The reason was that the software that registered your cable modem was Windows specific. Now they will initiate modem registration for Linux users with a phone call. When a vendor depends on Linux to support their products they limit their legal liabilities by saying they don't support Linux. They won't for example tell you if they provide information to the Linux community so that the community can create the necessary drivers and protocols.

---

### Post by Bachstelze on 2010-07-11
I don't know how it is in the US, but over her most ISPs nowadays just give their customers a modem/router combo which is pretty much autonomous: you just have one wire hooked to the phone line and at the other hand you have an Ethernet jack where you plug your computer. Since the thing  manages the connection all by itself, it is OS-agnostic (the ISP doesn't always mention that, but you don't need a PhD to figure it out).

---

### Post by parker.casey@gmail.com on 2010-07-11
It's not the kind of company you're probably all talking about, but Jackson Hewitt Tax Services. They franchise, and the franchisees HAVE to use Windows. Either Windows 2000 or Windows XP, with the root of the main drive shared. That is the ONLY way to use their franchise. So awful.

---

