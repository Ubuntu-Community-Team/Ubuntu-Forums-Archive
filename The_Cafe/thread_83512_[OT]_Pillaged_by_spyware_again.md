---
title: "[OT] Pillaged by spyware again"
date: 2005-10-28
forum: The Cafe
---

### Post by jdong on 2005-10-28
I knew it was too good to be true -- SAV 10 is not invincible... A bit more surfing on underground sites inside a VMWare session eventually picked up a few nasties that not even SAV+PestPatrol+Spybot+Ad-Aware +/- Safe Mode could completely cure.


Every time I run a scan, over 800 items are found in total, and removed. Upon reboot, there is heavy disk activity and all of the items come back from the dead (how appropriate for halloween!).


Note that this was picked up on a fully updated XP SP2 install using IE, under what I'd personally consider to be a very secure setup (minus running as an Administrator, but not doing so is TOO limiting).


Right now, I'm making a few extra clones of this specimen, and examining where over 100MB worth of spyware infections are popping back from. Spyware research is truly fascinating.

---

### Post by Wide on 2005-10-28
You need to stay away from those places


Or use better protection ;)

---

### Post by jdong on 2005-10-28
In real life, I would. It's just that I'm surrounded by MS-brainwashed computer users who keep on telling me how "advanced security technologies" from Windows keeps computers safer, all while lowering TCO....

My goal was to set out and prove two things:

(1) There are indeed still flaws in IE that allow software to forcibly enter the system without the user's permission.

(2) Not even with multilayered quality protection can one escape from these nasties.


and I believe I proved both well... #1 is self-explanatory. #2, I may be opinionated but I speak from experience managing Windows public workstations... Symantec AV 10 has done a far superior job of stopping spyware/adware than everything else I've heard of COMBINED. Even it was swamped as the original infestation unleashed over 150 processes that all protected themselves from termination.

---

### Post by xequence on 2005-10-28
I do find it quite cool to do a controled experement in vmware. If only I could get VMware working on linux...

---

### Post by Riverside on 2005-10-28
[QUOTE=jdong]There are indeed still flaws in IE that allow software to forcibly enter the system without the user's permission.[/QUOTE]Running XP as a user without administrative privileges is Microsoft's recommended way to avoid most of these issues, however as you have noted in your posting, doing so is impractical for real world usage.

---

### Post by Riverside on 2005-10-28
[QUOTE=xequence]I do find it quite cool to do a controled experement in vmware.[/QUOTE]What is the approximate cost of a single user VMware license these days?

---

### Post by xequence on 2005-10-28
[QUOTE=Riverside]What is the approximate cost of a single user VMware license these days?[/QUOTE]

I think it is 189$ for a download, 199$ for a CD.

---

### Post by jdong on 2005-10-28
[QUOTE=Riverside]Running XP as a user without administrative privileges is Microsoft's recommended way to avoid most of these issues, however as you have noted in your posting, doing so is impractical for real world usage.[/QUOTE]

Absolutely. XP offers no plausible "sudo/su" alternative -- there are some tasks, like certain test-cases of new hardware, that would fail completely under an ordinary user account. From what I've heard, Vista corrects this (and I sure hope it does... too many headaches to deal with)... Also, many Windows programs (not MS's fault though) still think they should save settings and files inside Program Files or the Windows folder, making limited user account setups virtually impossible.

---

### Post by jdong on 2005-10-28
[QUOTE=xequence]I think it is 189$ for a download, 199$ for a CD.[/QUOTE]
That is correct -- it's not cheap, but many fields of software (and even some hardware) work greatly benefit from VMWare.

---

### Post by erikpiper on 2005-10-29
There is always bittorent..

(Personally I would download it, see if it worked good enough, then pay. Nothing worse than paying $200 for something you can't use....)

---

### Post by TravisNewman on 2005-10-29
[QUOTE=jdong]Absolutely. XP offers no plausible "sudo/su" alternative -- there are some tasks, like certain test-cases of new hardware, that would fail completely under an ordinary user account. From what I've heard, Vista corrects this (and I sure hope it does... too many headaches to deal with)... Also, many Windows programs (not MS's fault though) still think they should save settings and files inside Program Files or the Windows folder, making limited user account setups virtually impossible.[/QUOTE]
vista corrects this, but any old programs that still save settings to the program installation directory will be crippled unless you're running as an admin, from what I undertand. The idea is that they're making changes that will fix this, but program developers have to follow suit as well.

---

### Post by WildTangent on 2005-10-29
[QUOTE=erikpiper]There is always bittorent..

(Personally I would download it, see if it worked good enough, then pay. Nothing worse than paying $200 for something you can't use....)[/QUOTE]
That's what I did. I pay up for programs I really like. Does anyone know if the licences work for both the linux and Windows versions?

-Wild

---

### Post by Remmelas on 2005-10-29
[QUOTE=panickedthumb]vista corrects this, but any old programs that still save settings to the program installation directory will be crippled unless you're running as an admin, from what I undertand. The idea is that they're making changes that will fix this, but program developers have to follow suit as well.[/QUOTE]
From what i've been made to understand, Vista will actually catch and redirect user priveledges reads and writes to those directories, into the users home directory.  Sounds like an opportunity for failure, and it's second hand knowledge, since it's only a dev friend of mine that was telling me about it.

---

### Post by jdong on 2005-10-29
[QUOTE=erikpiper]There is always bittorent..

(Personally I would download it, see if it worked good enough, then pay. Nothing worse than paying $200 for something you can't use....)[/QUOTE]

Windows and Linux are licensed separately -- a Windows VMWare license will not work on the Linux VMWare version.

They do offer 30-day trial keys for evaluation purposes.

---

### Post by darrenrxm on 2005-10-29
You scared me with the topic you put. I thought that ubuntu now had a problem with spyware.

---

### Post by xequence on 2005-10-29
[QUOTE=erikpiper]There is always bittorent..

(Personally I would download it, see if it worked good enough, then pay. Nothing worse than paying $200 for something you can't use....)[/QUOTE]

Well, for me, ill download any software. I really cant afford to pay 200$ for something really cool, but I wont get alot of use out of it.

But for things like vmware, you just download it off the website, and dont get a trial key. Get a real key from a crack site.

But then again, not everyone likes doing that stuff, which is understandable.

---

### Post by towsonu2003 on 2005-10-29
[QUOTE=jdong]A bit more surfing on underground sites inside a VMWare session eventually picked up a few nasties 
(...)
Every time I run a scan, over 800 items are found in total, and removed. Upon reboot, there is heavy disk activity and all of the items come back from the dead  over 100MB worth of spyware infections are popping back from. [/QUOTE]

argh I almost had a heart attack when I saw the title (what?! in linux?!! nooooooooooooo)

I guess some posts here are not good for the health of a linux newbie... :)

I have a couple of questions:
Which sites specifically? (please specify whether it's legal in the US to go to them)
What happens when you visit them in linux (no emulation), with firefox + epiphany + galeon?
How long did you visit each site (or) how many links did you click in each?
Did your anti-stuff give any alerts while visiting (did it succeed in picking up *any* malware)?
What happens when you visit them with firefox in XP?

Just to clarify, I am not arguing or anything, just (*very*) curious newbie. Also, I can't try this as it would trash my XP installation (no emulation) and dialup (100MB - wow) too afraid to do it in linux :)

---

### Post by xequence on 2005-10-29
> Which sites specifically? (please specify whether it's legal in the US to go to them)
What happens when you visit them in linux (no emulation), with firefox + epiphany + galeon?
How long did you visit each site (or) how many links did you click in each?
Did your anti-stuff give any alerts while visiting (did it succeed in picking up *any* malware)?
What happens when you visit them with firefox in XP?

I got loaded with spyware in ten minutes, in XP, from going on keygen.us for a couple minutes to get a crack for opera. I have no idea if its legal to go to that site...

---

### Post by towsonu2003 on 2005-10-29
[QUOTE=xequence]I got loaded with spyware in ten minutes, in XP, from going on keygen.us for a couple minutes to get a crack for opera. I have no idea if its legal to go to that site...[/QUOTE]

And what about this one:
What happens when you visit them in linux (no emulation), with firefox + epiphany + galeon?

Thanks for the quick reply :) and sorry if this particular question makes me look stupid :KS 

keygen.us seemed to be fine 2 or so years ago with ie in xp. I guess they don't stop developing themselves :)

---

### Post by jdong on 2005-10-29
Mostly andr.net, cracks.am, and keygen.us... Especially the download dialogs.

I mean these things are picked up just after around 15-20 minutes of surfing on the site, not even downloading any cracks. Firefox and other browsers on Windows or Linux are not affected.

All sites are legal to view, and technically illegal to download or execute any of the patches/cracks/keygens in the US, though largely (almost completely) unenforced.


**CAUTION CAUTION CAUTION CAUTION**
andr.net recently switched to an .exe unpacker for all its cracks -- Approximately 30% of these **CONTAIN ROOTKITS** or rootkit like technology that sabotages AV programs and shields files from Windows, even while in Safe Mode. As a result, executing such EXE's **WILL** break your Windows beyond repair by any security tools I know.

These are fun to play with (in a testbed), and are excellent spyware-in-a-box examples for exercising your spyware removal skills or seeing the newest ITW's. Also very nice for testing AV/Anti-Spyware software. Currently, my tests rank SAV 10 near the top of the list. Sadly, Spybot and Ad-Aware seem to have met their days.



P.S. Yes, all three underground sites have gone exceptionally nasty recently.

---

### Post by wmcbrine on 2005-10-29
VMware is now available for free as "VMware Player". The only significant limitation is that it won't let you create VM images (only "play" existing ones). However, it's easy to obtain images (legally!) from third parties, or create your own with third-party tools. You can probably even take an image that came with one OS and install a new one over it, but I haven't tried that.

Running as non-admin in Windows is IMHO not that hard. I do it. Anything that doesn't work that way, I delete. I haven't had to do that often, nor for anything important.

There *is* a near-equivalent to sudo in Windows -- not quite as convenient as in Ubuntu, but better than having to log out and back in again. It's "Run as". Right-click on an app, and the option will appear in the pop-up menu. (You might have to hold down "shift" as you click, in some cases.)

---

### Post by jdong on 2005-10-29
[QUOTE=wmcbrine]Running as non-admin in Windows is IMHO not that hard. I do it. Anything that doesn't work that way, I delete. I haven't had to do that often, nor for anything important.

There *is* a near-equivalent to sudo in Windows -- not quite as convenient as in Ubuntu, but better than having to log out and back in again. It's "Run as". Right-click on an app, and the option will appear in the pop-up menu. (You might have to hold down "shift" as you click, in some cases.)[/QUOTE]

Well,

(1) Run as usually isn't available for those things that really need it, like plugging in a legacy device for the first time (where the process for re-initiating the Device Wizard is a huge pain)

(2) When a critical, day-to-day program requires admin access, it's no longer appropriate to delegate it this way.

(3) If users have access to a C compiler (or can transport in binaries), I've seen very crafty ways of abusing DirectX and other very common direct-access drivers for elevated access... It won't be long before automated attacks use this vector.

---

### Post by GreyFox503 on 2005-10-30
Yeah, it is fun to trash a fake windows installation with spyware in vmware :)  (sometimes I have too much free time).

I've never tried this, but as some other people have mentioned, vmware does give a 30-day free trial. Also on their website is a VMware "player" which will run existing virtual machines, but not create them. You could try downloading the 30-day trial to create a few machines, them back them up and use the free player to run them. Even if it didn't work, it wouldn't cost you anything (except time).

As for the technical aspect of getting VMware working, I recently had to do this in Breezy. A couple of Hoary -> Breezy changes made this more interesting for a few programs.

1) Upon install, I was warned that my kernel was compiled with a different version of gcc (3.4) than the one installed on my system (breezy currently gives you 4.0 by default). So i had to use Synaptic to download gcc 3.4 and then make the VMware installer use that. I also had to download the header files for my running kernel, also doable through Synaptic.

2) I also had some funky network breakage after trying to run VMware (it wouldn't start up, and trying to do so would cause my Ubuntu networking to screw up.) This was solved by applying a patch to VMware after a short Google.

If you guys want more details, you can ask me or search the forums. There were several other threads I spotted dealing with this problem.

---

### Post by jdong on 2005-10-30
The latter network issues also plague SuSE 10.

---

### Post by wmcbrine on 2005-10-30
[QUOTE=jdong](1) Run as usually isn't available for those things that really need it, like plugging in a legacy device for the first time (where the process for re-initiating the Device Wizard is a huge pain)[/quote]OK, but how often does that come up? That's not a reason not to use a Limited account *most* of the time, as one's main account.

The main thing I use "Run as" for is to install new programs.

> *(2) When a critical, day-to-day program requires admin access, it's no longer appropriate to delegate it this way.*I might agree, but I've yet to encounter such a program, at least as regards my own needs. Granted, I'm not a heavy Windows user. Do you have an example?

> *(3) If users have access to a C compiler (or can transport in binaries), I've seen very crafty ways of abusing DirectX and other very common direct-access drivers for elevated access... It won't be long before automated attacks use this vector.*I'm not sure of the relevance. Are you saying that since a Limited account can potentially be breached, there's no point to even using it? I can't agree with that. Privilege escalation is an issue for any OS. But limited rights still work, most of the time. And exploits eventually get patched, even in Windows.

We can certainly agree that it all works better in Linux (and particularly Ubuntu). But it's still worth attempting, at least, in Windows. I assumed it wouldn't work myself, until I tried it.

P.S. There's one program that needs admin privileges in Windows that I didn't delete: DVDDecrypter. But it wants admin for a good reason -- to access the drive at a low level -- not because of bad design. However, I did cut DVDDecrypter out of my backup process once I realized that DVDShrink could do the job fine by itself, without needing admin privileges. I think I'd only need DVDDecrypter if I had to deal with a disc from another region.

---

### Post by jdong on 2005-10-30
[QUOTE=wmcbrine]OK, but how often does that come up? That's not a reason not to use a Limited account *most* of the time, as one's main account.

The main thing I use "Run as" for is to install new programs.

I might agree, but I've yet to encounter such a program, at least as regards my own needs. Granted, I'm not a heavy Windows user. Do you have an example?
[/quote]
It doesn't come up often, but when it does it's damned annoying... It's one of the reasons I don't recommend Joe Windows User to run as a limited account.

> 
I'm not sure of the relevance. Are you saying that since a Limited account can potentially be breached, there's no point to even using it? I can't agree with that. Privilege escalation is an issue for any OS. But limited rights still work, most of the time. And exploits eventually get patched, even in Windows.

I'm not saying that there's no point to using it, but I am saying that it could well be **luring you into a false sense of security**. Especially if you use a burning program as a regular user (IMAPI open to limited accounts) or are able to interface to buggy device drivers (I had a friend demonstrate to me spawning cmd.exe as SYSTEM from a Best Buy computer under the Guest account, using VB Editor and the Win32 API) from 3rd parties. I'm not denouncing those who use limited accounts -- great for you -- I highly encourage it to the power user who can work around these problems.

However, I don't want anyone to walk around thinking that just because they're running under a Limited Account they are significantly more likely to dodge attacks like the ones I've experienced. It's trivial for spyware to start exploiting these loopholes.


And as far as patching, true Microsoft has done better recently with patching, but who says that my wind502u wireless card, with drivers dated in 2003, is making sure NDisEnumerateNextPacket() is escaped properly, or that the **unsigned** driver firmware package inside one of Windows's built-in drivers isn't tampered with? I have also seen a USB Key based attack succeed at the logon screen, implanting a new msgina.dll that bypasses Windows logon at next boot. I'm sure that this mechanism can be exploited to install spyware under limited user accounts.

> 
We can certainly agree that it all works better in Linux (and particularly Ubuntu). But it's still worth attempting, at least, in Windows.

I agree with you that it's worth the try (doesn't hurt much), but definitely isn't as strong

---

### Post by teaker1s on 2005-10-30
why not just use firefox and  disable allow internet sites to install software would solve 80% of spyware problems

---

### Post by Big Venus on 2005-10-30
Why not use microsoft's anti-spyware tool. I haven't had spyware on my system and I don't even use it. But every now and then install it to check and make sure that no spyware is located on my system. Oh, oops that is for windows. Sorry...

For linux, I haven't seen a problem yet. But then I don't install anything from any website that I don't trust. I usually delete all my temporary files and have the browser delete everything that it can. 

I don't know how much help that would be, but that is what I have done...

---

### Post by jdong on 2005-10-31
[QUOTE=Big Venus]Why not use microsoft's anti-spyware tool. I haven't had spyware on my system and I don't even use it. But every now and then install it to check and make sure that no spyware is located on my system. Oh, oops that is for windows. Sorry...[/QUOTE]

I am -- it failed to stop this one... Right now, it's a combination of Adware.Look2Me, Adware.ISearch, and Adware.Lop.

Currently, Ad-Aware, MS AntiSpy, Spybot, and PestPatrol are all saying the system's clean, while Symantec keeps on finding these DLL's infected, though after removal new ones magically pop up.

---

### Post by Efwis on 2005-11-16
[QUOTE=teaker1s]why not just use firefox and  disable allow internet sites to install software would solve 80% of spyware problems[/QUOTE]
I can vouch that this doesn't work.

ON my windows drive I use FF religiously. FF has fixed it for the most part as of 1.05 or 1.06 and it works to a degree.

I was visiting a website in FF and it did a work around which bypassed Ff settings and infected IE. for what its worth IE is the primary backbone for Windows. so for all instances where is the security in doing this???

---

### Post by bulldogzerofive on 2005-11-16
[QUOTE=GreyFox503]

I've never tried this, but as some other people have mentioned, vmware does give a 30-day free trial. Also on their website is a VMware "player" which will run existing virtual machines, but not create them. You could try downloading the 30-day trial to create a few machines, them back them up and use the free player to run them. Even if it didn't work, it wouldn't cost you anything (except time).

[/QUOTE]

Why not just use Qemu instead of VMWare?  It is (from what i understand, never having used VMWare) not as fast as VMWare, but most of the poeple here seem more interested in playing around with windows in a sand box than serious work.  Besides, it is in the repositories ready to use with little or no effort once you read the man page.

---

### Post by jdong on 2005-11-16
[QUOTE=Efwis]I can vouch that this doesn't work.

ON my windows drive I use FF religiously. FF has fixed it for the most part as of 1.05 or 1.06 and it works to a degree.

I was visiting a website in FF and it did a work around which bypassed Ff settings and infected IE. for what its worth IE is the primary backbone for Windows. so for all instances where is the security in doing this???[/QUOTE]

Ack, lots of these places are starting to use Java to do this....

---

### Post by Efwis on 2005-11-16
[QUOTE=jdong]Ack, lots of these places are starting to use Java to do this....[/QUOTE]
I was the original source, The one that got nailed, and an acqaintence in the spyware forums forwarded the info to Opera and FF. I am a member of a lot of spyware removal forums. Tomscoyote.org, Spywareinfo.com, Geekstogo.com, and quite a few more. 

so I spend most of my day running around cleaning peoples computers of this crap. I'm also a member ASAP (Association of Spyware Analisys Professionals)

I use Linux to tear apart malware files so we can find fixes for them. :)

---

