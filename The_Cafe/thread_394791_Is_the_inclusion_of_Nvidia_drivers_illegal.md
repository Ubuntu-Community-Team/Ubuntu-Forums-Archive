---
title: "Is the inclusion of Nvidia drivers illegal?"
date: 2007-03-27
forum: The Cafe
---

### Post by ndube on 2007-03-27
> **linuxmonkey said:**
> I plan on doing a reinstall tomorrow.  I'll give Automatix a try.  Why isn't this included in the standard installations?

It is not included because it has the capability of installing non-free programs and codec's which violate US law...

---

### Post by linuxmonkey on 2007-03-27
> **ndube said:**
> It is not included because it has the capability of installing non-free programs and codec's which violate US law...

Is it safe?  Should I run a antivirus before installing from that place?

---

### Post by hyper_ch on 2007-03-27
> **Toadmund said:**
> Now I got a question, why the hell is it illegal to download codecs and drivers for hardware that we already purchased?
Do they not want us to be able to use their stuff?:confused: 

I think it's a Micro$haft conspiracy, I mean; it all works on Micro$hafts OS without it being illegal, is it part of the purchase price of M's OS?


It is a question of intellectual property. Ubuntu is Debian based and Debian is free/open source software. Basically this means that you can get debian and download it as you want, modify it to your liking... you can do everything with it except for a few things:
(1) You cannot alter its licence
(2) If you distribute it you must also make the source code available

Now since Ubuntu is based on debian those principles apply also to Ubuntu.

However hardware manufacturers like nVidia and ATI have invested time and money in their drivers but they will not provide the source code of it. Hence Ubuntu cannot ship with those drivers as they are proprietary. Ubuntu would need to have the right to distribute the source of those drivers also.

One of the best cases to demonstrate that actually making the drivers opensource can boost sales on hardware is the LinkSys WRT54 router. LinkSys did use some GPL protected software in the firmware. After this became public LinkSys was required to publish their source code.
This then enabled people to modify/improve the firmware and a few interesting project appeared like [www.openwrt.org](www.openwrt.org) and [www.dd-wrt.com](www.dd-wrt.com) which have quite a bit modified the source code. Since everyone was now able to implement functions and stuff in that specific router this all boosted sales on that router and also the ones following it...

Although it's a pain for the enduser to not have the drivers directly integrated into the cd-image it is actually to blame nVidia and ATI that they don't release their drivers as open source. As long this doesn't happen ubuntu can't legally integrate them.

---

### Post by jrusso2 on 2007-03-27
If its "illegal" for Ubuntu to ship with Nvidia and ATI propiretary drivers why is it Sabayon, Freespire, Linsipre, and Xandros all ship with them?

This seems to be more a philosophical issue then a legal one.

If Ubuntu is going to stay with their "philosophical" legal issue they should make an easy one click way right on the desktop to install video drivers and codecs.

Jeanette

---

### Post by aysiu on 2007-03-27
> **jrusso2 said:**
> If its "illegal" for Ubuntu to ship with Nvidia and ATI propiretary drivers why is it Sabayon, Freespire, Linsipre, and Xandros all ship with them? It's not illegal, as far as I know. I thought they're not shipping them because the Ubuntu community raised a stink about including "blobs" by default.

---

### Post by Luggy on 2007-03-27
> **aysiu said:**
> It's not illegal, as far as I know. I thought they're not shipping them because the Ubuntu community raised a stink about including "blobs" by default.

However the Ubuntu devs are cheating in feisty a bit by allowing  "one click" installation of propiretary video drivers and audio codecs.

While not technically installing these things by default, you wont need things like automatix to actually "use" Ubuntu.

---

### Post by ndube on 2007-03-27
> **ndube said:**
> It is not included because it has the capability of installing non-free programs and codec's which violate US law...

Sorry for my lack of being specific. The ATI and NVIDIA drivers are not included because they are not open source. I did not mean to imply that installing them was illegal.

However, the non free audio codec's such as windows media codec's are illegal to install if you live in the US.

---

### Post by aysiu on 2007-03-27
> **Luggy said:**
> However the Ubuntu devs are cheating in feisty a bit by allowing  "one click" installation of propiretary video drivers and audio codecs.

While not technically installing these things by default, you wont need things like automatix to actually "use" Ubuntu. How is that cheating?

---

### Post by kinematic on 2007-03-27
including closed source drivers(or installing them yourself)with the linux kernel IS illegal.
each and every driver included must honor the license under wich the kernel is released,in this case the gpl.
this means that the source must be freely obtainable and redistributable but if nvidia/ati where to do that they would violate patents owned by other companies because they both license technologie from third parties.

---

### Post by aysiu on 2007-03-27
> **kinematic said:**
> including closed source drivers(or installing them yourself)with the linux kernel IS illegal.
each and every driver included must honor the license under wich the kernel is released,in this case the gpl.
this means that the source must be freely obtainable and redistributable but if nvidia/ati where to do that they would violate patents owned by other companies because they both license technologie from third parties.
No one's talking about including the closed source drivers with the *kernel*.

I believe people are talking about including the closed source drivers with the *distribution* built around the kernel--many distros do this, and it's not illegal.

---

### Post by saulgoode on 2007-03-27
> **kinematic said:**
> including closed source drivers(or installing them yourself)with the linux kernel IS illegal.

While I agree with your assessment that distributing closed drivers pre-installed is a violation of the copyrights of the kernel developers, "installing them yourself" is by no means a violation of their license. The GPL specifies that end users are free to do whatever they wish with the software (short of distribution, in which case they cease to be the "end user").

---

### Post by G Morgan on 2007-03-27
> **hyper_ch said:**
> It is a question of intellectual property. Ubuntu is Debian based and Debian is free/open source software. Basically this means that you can get debian and download it as you want, modify it to your liking... you can do everything with it except for a few things:
(1) You cannot alter its licence
(2) If you distribute it you must also make the source code available

Now since Ubuntu is based on debian those principles apply also to Ubuntu.

However hardware manufacturers like nVidia and ATI have invested time and money in their drivers but they will not provide the source code of it. Hence Ubuntu cannot ship with those drivers as they are proprietary. Ubuntu would need to have the right to distribute the source of those drivers also.

Debian do not hold even a fraction of the copyrights in their distribution and not everything is GPL'd. For example the X-Server is under the MIT license.

The MIT license allows linking to binary blobs. The real question is one of the shim, if the kernel shim is non GPL'd it is possibly illegal. Linus has repeatedly stated that he doesn't consider the shim to constitute a derived work. Until that position changes the driver will be legal given his position as benevolent dictator for life.

---

### Post by saulgoode on 2007-03-27
> **G Morgan said:**
> Linus has repeatedly stated that he doesn't consider the shim to constitute a derived work.

Source? Because I would say your interpretation may be taking liberty when compared with the view expressed in the following quote (source: [Linux Kernel Mailing List](http://lkml.org/lkml/2006/12/14/218)):

[QUOTE="Linus Torvalds"]I don't like binary modules. I refuse to support them, and if it turns out 
that the module was written using Linux code, and just for Linux, I htink 
that's a _clear_ copyright violation, and that binary module is obviously 
a license violation.

But if the module was written for other systems, and just ported to Linux, 
and not using our code, then it's very much debatable whether it's 
actually a "derived work". Interfaces don't make "derived works" per se.[/QUOTE]

---

### Post by G Morgan on 2007-03-27
Yeah and the Nvidia shim is an interface exactly as he says. The real business is in the X11 module that was built for X11 specifically not Linux, the Nvidia driver works on practically all Unix systems. Also most of the code there is shared across all platforms and was originally built for Windows.

He states that he feels binary blobs are idiotic (and they are) but that isn't a position of legality but a technical issue.

I'm against blobs as much as anyone because they're a technical nightmare but that doesn't make them illegal in this case.

A lot of FUD is spread over this though. The Nvidia code that touches the kernel is just an interface as Linus alludes to.

This under the FSFs interpretation is a GPL violation but Linus is the arbiter of right and wrong for the Linux kernel (which is under a modified GPL in any case) and the FSFs interpretation doesn't actually matter since they have no authority over the kernel as such.

//edit - very selective quoting from that page as well. Impressive even given the gist of it.//

---

### Post by G Morgan on 2007-03-27
"If you think this is a black-and-white "copyright owners have all the 
rights", then you're standing with the RIAA's and the MPAA's of the world.

Me, personally, I think the RIAA and the MPAA is a shithouse. They are 
immoral. But guess what? They are immoral exactly _because_ they think 
that they automatically own ALL the rights, just because they own the 
copyright.

That is what it boils down to: copyright doesn't really give you "absolute 
power". This is why I have been _consistently_ arguing that we're not 
about "black and white" or "good against evil". It simply isn't that 
simple."


This is also from that page.

---

### Post by saulgoode on 2007-03-27
> **G Morgan said:**
> //edit - very selective quoting from that page as well. Impressive even given the gist of it.//

Which is why I provided the citation. :) 

I disagree with your characterization of Linus feeling that binary drivers are legally acceptable. In my opinion, his view is that the issue is debatable. While I agree that it *is* debatable, I disagree with Linus' logic employing "fair use" doctrine; which is not about availing oneself of another's work for the benefit that work affords, but for reference within or the framing of one's own work. I would certainly be nice to have a "fair use" doctrine for software, but (to my knowledge) one has not yet been established and to address the issues Linus expressed, it would need to be rather different from the literary "fair use" criteria.

---

### Post by darksong on 2007-03-27
> **aysiu said:**
> How is that cheating?

Its not - its quite a leap forwards for ubuntu.

---

### Post by G Morgan on 2007-03-28
> **saulgoode said:**
> Which is why I provided the citation. :) 

I disagree with your characterization of Linus feeling that binary drivers are legally acceptable. In my opinion, his view is that the issue is debatable. While I agree that it *is* debatable, I disagree with Linus' logic employing "fair use" doctrine; which is not about availing oneself of another's work for the benefit that work affords, but for reference within or the framing of one's own work. I would certainly be nice to have a "fair use" doctrine for software, but (to my knowledge) one has not yet been established and to address the issues Linus expressed, it would need to be rather different from the literary "fair use" criteria.

I didn't say binary drivers in general. He explicitly states that most binary drivers aren't legal in the post. However this thread refers to the Nvidia driver which is a case of an interface. They don't use any kernel code in their own code (trust me if they did the opposition would be much louder) and the driver was written for other systems.

Personally I think Nvidia should GPL the shim to solve all these problems. If they did that then it is most certainly legal even if the X11 module is still unsupportable.

---

### Post by hyper_ch on 2007-03-28
I don't know how many licences there are involved with the Debian distribution but one of them is GPL and one of the provisions by the GPL is that - if the program is being distributed - also the source code must be made available and that is where the proprietary drivers fail as ubuntu can't distribute also the source of those proprietary drivers.

For this reason Ubuntu can't ship with proprietary drivers integrated.

---

### Post by saulgoode on 2007-03-28
> **G Morgan said:**
> I didn't say binary drivers in general. He explicitly states that most binary drivers aren't legal in the post. However this thread refers to the Nvidia driver which is a case of an interface. They don't use any kernel code in their own code (trust me if they did the opposition would be much louder) and the driver was written for other systems.

The *compiled version* of [NVidia's driver for Linux]("http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html") is very much written for Linux. One is not able to use the compiled version on a Solaris, BSD, or other architectures; and the fact that NVidia has had to produce updates of their driver with the recent releases of the kernel (2.6.17->2.6.18->2.6.19) indicates that their binary module is clearly tied to the Linux kernel at a more intimate level than a standard system call interface.

---

### Post by DoctorMO on 2007-03-28
Aysiu - I'm getting tired of repeating my points, if you have time could you make one of your lovely wiki thingies of this?

> Sorry for my lack of being specific. The ATI and NVIDIA drivers are not included because they are not open source. I did not mean to imply that installing them was illegal.

NVidia binary drivers aren't included in some distributions because of the personal or technical preference of the users and integrators of those distributors. The proprietory licence that nvidia linux drivers are released under contains the following:

> 2.1.1 Rights. Customer may install and use one copy of the SOFTWARE on a single computer, and except for making one back-up copy of the Software, may not otherwise copy the SOFTWARE. This LICENSE of SOFTWARE may not be shared or used concurrently on different computers.

2.1.2 Linux/FreeBSD Exception. Notwithstanding the foregoing terms of Section 2.1.1, SOFTWARE designed exclusively for use on the Linux or FreeBSD operating systems, or other operating systems derived from the source code to these operating systems, may be copied and redistributed, provided that the binary files thereof are not modified in any way (except for unzipping of compressed files).

ATI binary drivers don't appear to have accessible terms, but it's likly they include a similar exception.

The issue of weather including user space propritory drivers with a thin layer of gpl kernel pace activation code is debatable. it clearly allows an escalation of privileges which is not good for security but nvidia and ati are unable to integrate their drivers directly into the kernel or xorg without violating the gpl.

> However, the non free audio codec's such as windows media codec's are illegal to install if you live in the US.

Codecs are a complex business, not only are each and every codec different in legal status but also in country used.

A quick table:

MP3 - Open Source codecs via LAME project or Helix project, restricted because of USA, Canada and Australian software patents previsions though two companies. one French and one German; legal to install in EU.
Real - Real media playback provided via proprietory real player, while helix player attempts to bridge some kind of a gap. the legals are being wrangled within real networks.
Mpeg (including DVD playback) - Normal mpeg encoded files from mpeg2 to mpeg4 are included by default as there are no restrictions currently.
Acc - Open format, available to decode and encode from most distributions
Windows Media Formats - In order to use these formats we must butcher existing dlls from Microsoft. this is illegal in ANY country as it breaks to copyright agreement with Microsoft that covers reuse under unintended target operating systems.
Flash Player - Flash is a binary proprietory solution which contains no linux friendly redistribution terms in the copyright licence, hench can not be included by default.
DeCSS - Open source solution available, decoding CSS encrypted dvds (comerical dvd releases) is iligal in the EU, USA and most parts of the world under the EUCD and DMCA respectively. because this law protects both propritory and open formats alike the owner of the format controls the keys; using a none aproved key is counter-mount to breaking the encryption.
Ogg - open source, public format should be available in most distributions

Some distributions figure that, hey if we're going to include FAT32 code (probably patented by Microsoft) we might as well include MP3 code too; it is open source.

As for not being able to include proprietory stuff in open source software releases. this is allowed as the recipient only has to follow all the terms consecutively for each piece of software. so if having the nvidia drivers included by default means you have to follow those terms as well as the gpl and other foss licences. Even if those terms include eating cherry pie on Thursdays while hopping to the beat of slim shady.

---

### Post by G Morgan on 2007-03-28
> **saulgoode said:**
> The *compiled version* of [NVidia's driver for Linux]("http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html") is very much written for Linux. One is not able to use the compiled version on a Solaris, BSD, or other architectures; and the fact that NVidia has had to produce updates of their driver with the recent releases of the kernel (2.6.17->2.6.18->2.6.19) indicates that their binary module is clearly tied to the Linux kernel at a more intimate level than a standard system call interface.

There's no such thing as a 'standard' driver interface. It simply doesn't exist and there is a large document in the kernel source explaining why. When Linus refers to interface he means the parts put into the kernel constitute merely an interface. They haven't imported large sections of Linux code into the driver.

The work is all done outside the kernel.

---

### Post by G Morgan on 2007-03-28
> **hyper_ch said:**
> I don't know how many licences there are involved with the Debian distribution but one of them is GPL and one of the provisions by the GPL is that - if the program is being distributed - also the source code must be made available and that is where the proprietary drivers fail as ubuntu can't distribute also the source of those proprietary drivers.

For this reason Ubuntu can't ship with proprietary drivers integrated.

Simply not true. For that to be the case all the code would have to be GPL'd. X.org is under the MIT license and you can put as many binary blob X.org drivers as you so choose.

It's not the case of a series of licenses with one taking precedent. Each individual program will be under it's own license. Linux is under a modified GPL, X.org MIT, there'll be a lot of BSD code.

---

### Post by saulgoode on 2007-03-28
> **G Morgan said:**
> There's no such thing as a 'standard' driver interface. It simply doesn't exist and there is a large document in the kernel source explaining why. When Linus refers to interface he means the parts put into the kernel constitute merely an interface. They haven't imported large sections of Linux code into the driver.

The work is all done outside the kernel.

There *is* such a thing as a "standard" system call interface to which I referred and it is mentioned in the first sentence of the kernel's "COPYING" file included in every source code distribution package. 

As to what Linus is referring, you will have to provide the origin you are citing (i.e., which "large document in the kernel source"; and since it is a large document, perhaps you could narrow things down by providing the precise section). I will share a quote from the LKML (along with [the link to the original](http://www.ussg.iu.edu/hypermail/linux/kernel/0210.2/0603.html)) which I feel contradicts your assertion (or maybe I am just misunderstanding you):

[QUOTE="Linus Torvalds"]There is **nothing** in the kernel license that allows modules to be non-GPLd.

The only thing that allows for non-GPL modules is copyright law, and in particular the "derived work" issue. A vendor who distributes non-GPL modules is *not* protected by the module interface per se, and should feel very confident that they can show in a court of law that the code is not derived.

The module interface has **never** been documented or meant to be a GPL barrier. The COPYING clearly states that the system call layer is such a barrier, so if you do your work in user land you're not in any way beholden to the GPL. The module interfaces are not system calls: there are system calls used to *install* them, but the actual interfaces are not.[/QUOTE]
(emphasized per original)

---

### Post by G Morgan on 2007-03-28
The system calls have nothing to do with drivers though. The sort of interface in this case would be referred to by /usr/src/linux/Documentation/stable_api_nonsense.txt.

It explains why there is no stable interface to build a driver against and hence why Nvidia have to rewrite their interface with each kernel release.

---

### Post by hyper_ch on 2007-03-29
> **G Morgan said:**
> Simply not true. For that to be the case all the code would have to be GPL'd. X.org is under the MIT license and you can put as many binary blob X.org drivers as you so choose.

It's not the case of a series of licenses with one taking precedent. Each individual program will be under it's own license. Linux is under a modified GPL, X.org MIT, there'll be a lot of BSD code.

You don't understand. GPL requires that also source code is being made available for any software that is somewhat bundled with the GPLed code AND distributed. You may distribute it als as blobs however you also have to make the source code available when requested. You have to differentiate in this case between binary and proprietary.

As long as the nvidia drivers remain proprietary they cannot legally be distributed together with GPLed code.

---

### Post by cowlip on 2007-03-29
> **kinematic said:**
> 
this means that the source must be freely obtainable and redistributable but if nvidia/ati where to do that they would violate patents owned by other companies because they both license technologie from third parties.

or they could *just* open the specifications up like Intel did :) (and I think 3dfx too)

> **DoctorMO said:**
> 
Acc - Open format, available to decode and encode from most distributions
Windows Media Formats - In order to use these formats we must butcher existing dlls from Microsoft. this is illegal in ANY country as it breaks to copyright agreement with Microsoft that covers reuse under unintended target operating systems.

ffmpeg includes support for windows media by reverse engineering, so then it's just software patents in some countries, like the mp3 issue.. [http://en.wikipedia.org/wiki/FFmpeg](http://en.wikipedia.org/wiki/FFmpeg)
 
> The FFmpeg developers have reverse-engineered and/or reimplemented, among others:

    * The Sorenson 3 Codec used by many QuickTime movies
    * Advanced Systems Format
    * Windows Media Audio
    * Windows Media Video (and thereby also the associated DivX hack)
    * QDesign Music Codec 2, used by many QuickTime movies prior to QuickTime 7.

The default MPEG-4 codec used by FFmpeg for encoding has the FourCC of FMP4.

FFmpeg's legal status varies by country. Some included codecs, (such as Sorenson 3), are claimed by patent owners. Such claims may be enforceable in countries like the United States which recognize software patents. Furthermore, many of these codecs are only released under terms that forbid reverse engineering, even for purposes of interoperability. However, these terms of use are forbidden in certain countries. For example, European Union nations do not recognize software patents and/or have laws expressly allowing reverse engineering for purposes of interoperability. In any case, many Linux distributions do not include FFmpeg to avoid legal complications.

---

### Post by cowlip on 2007-03-29
--delete--

---

### Post by G Morgan on 2007-03-29
> **hyper_ch said:**
> You don't understand. GPL requires that also source code is being made available for any software that is somewhat bundled with the GPLed code AND distributed. You may distribute it als as blobs however you also have to make the source code available when requested. You have to differentiate in this case between binary and proprietary.

As long as the nvidia drivers remain proprietary they cannot legally be distributed together with GPLed code.

Yes but not all the distribution is GPL and it still depends largely on what the copyright holder interpretes as a derived work. Just putting it on the same disc does not make is a derived work, hell some claim (as Linus does in some cases) that linking against GPL'd code doesn't always constitute a derived work. Things like the kernel and glibc have special exceptions placed into them to allow other code to use them without being GPL'd, similar to the class path license used for GPL'd Java class libraries.

For the last time Xorg **is not** GPL'd in any case, it is under MIT license, a binary blob there is entirely legal no matter what anyone else says. If Debian forked it under the GPL anyone else could easily take the MIT licensed version.

The absolute only legal issue is if the kernel shim, which provides a lightweight interface for the userland driver, constitutes a derived work and Linus has said previously he is cautious about claiming it does. Since he basically heads the kernel project that makes it legal.

Note I am entirely against binary blobs as a sub optimal solution but that is different to legal issues. There is no such thing as a universal license, all projects will come under a hundred different licenses and most distros will state that the core is GPL'd with each project under it's own license.

---

### Post by saulgoode on 2007-03-29
> **G Morgan said:**
> Things like the kernel and glibc have special exceptions placed into them to allow other code to use them without being GPL'd, similar to the class path license used for GPL'd Java class libraries.

Could you cite a source for where these kernel "special exceptions" are specified? I am unable to find any such stipulations in my kernel source tree.

> **G Morgan said:**
> For the last time Xorg **is not** GPL'd in any case, it is under MIT license, a binary blob there is entirely legal no matter what anyone else says. If Debian forked it under the GPL anyone else could easily take the MIT licensed version.

X.org is not the issue. The fact that the NVidia driver includes a *kernel module* is. 

> **G Morgan said:**
> The absolute only legal issue is if the kernel shim, which provides a lightweight interface for the userland driver, constitutes a derived work and Linus has said previously he is cautious about claiming it does. Since he basically heads the kernel project that makes it legal.

The kernel developers "tolerate" non-GPLed kernel modules (shims or otherwise) but that does not make them "legal". Torvalds cited a few instances of pre-existing Unix modules which were never written for Linux when he expressed his concern about claiming **all** modules to be derivative. 

I really think that you are misinterpreting Linus' views on this issue. The LKML is full of commentary like the following which would indicate quite strongly that he views kernel modules to be a derived work. 

[quote="Linus Torvalds"]The "derived work" issue is obviously a gray area, and I know lawyers don't like them. Crazy people (even judges) have, as we know, claimed that even obvious spoofs of a work that contain nothing of the original work itself, can be ruled to be "derived".

I don't hold views that extreme, but at the same time I do consider a module written for Linux and using kernel infrastructures to get its work done, even if not actually copying any existing Linux code, to be a derived work by default. You'd have to have a strong case to not consider your code a derived work.[/quote]

[quote="Linus Torvalds"]Well, there really is no exception. However, copyright law obviously hinges on the definition of "derived work", and as such anything can always be argued on that point.

I personally consider anything a "derived work" that needs special hooks in the kernel to function with Linux (i.e., it is not acceptable to make a small piece of GPL-code as a hook for the larger piece), as that obviously implies that the bigger module needs "help" from the main kernel.

Similarly, I consider anything that has intimate knowledge about kernel internals to be a derived work.

What is left in the gray area tends to be clearly separate modules: code that had a life outside Linux from the beginning, and that do something self-contained that doesn't really have any impact on the rest of the kernel. A device driver that was originally written for something else, and that doesn't need any but the standard UNIX read/write kind of interfaces, for example.[/quote]

---

### Post by G Morgan on 2007-03-29
FUSE modules are heavily dependant on the FUSE code in the kernel to work. Are all FUSE modules then forced to be GPL'd. Linus makes an exception for three circumstances generally.
1.Where the module links against a public interface (i.e. FUSE Modules).
2.Where the driver was clearly written for another system (i.e. Nvidia drivers, also FUSE comes under this as well as 1).
3. Some binary firmwares.

Linus has claimed that he would not consider a driver originally made for another system to be a derived work. Do you deny that the Nvidia driver was developed with a different system in mind.

In any case Dell has stipulated that they will shift proprietary GFX drivers until the OSS ones start working to a reasonable standard. I'm certain that their lawyers have given serious thought to the issue.

---

### Post by saulgoode on 2007-03-29
> **G Morgan said:**
> FUSE modules are heavily dependant on the FUSE code in the kernel to work. Are all FUSE modules then forced to be GPL'd.

If they are to be distributed together with the Linux kernel and the GPLed FUSE kernel module, they might very well need to be. You have yet to provide anything solid that would suggest otherwise. 

> **G Morgan said:**
> Linus makes an exception for three circumstances generally.
[snipped]

You stated that before yet failed to cite a source for this exception. It is NOT part of the Linux kernel's GPL licensing.

> **G Morgan said:**
> Linus has claimed that he would not consider a driver originally made for another system to be a derived work.

Linus made that particular statement in 1995 in reference to Unix character I/O drivers. The NVidia driver is not a simple character I/O driver, it is a kernel module which, when installed, intimately interacts with and relies upon Linux kernel resources. I have already refuted your assertion in my previous posts by quoting more recent expressions of Linus' opinion that kernel modules are indeed derived works.

> **G Morgan said:**
> Do you deny that the Nvidia driver was developed with a different system in mind.

Do *you* deny that the NVidia kernel module part of its driver will **not** work with those different systems?

The question of this thread is whether inclusion of NVidia's drivers with a Linux distribution is legal. I can find nothing in the kernel's licensing which suggest that it would be. You claim that special exceptions exist which supercede the terms of the GPL and I would be more than willing to accept such a situation if you'd just point out where those exceptions are specified. They are not specified at the end of the COPYING document in the kernel source tree (which is where the FSF recommends that any such exceptions be placed).

Whether or not the kernel developer's wish to pursue enforcement of their licensing does not change the legality of the matter. George Lucas tolerates Stars Wars fan films but that in and of itself does not mean that those films are not violations of his copyrights.

---

### Post by aysiu on 2007-03-29
This discussion has gone way over my head. I'm unsubscribing.

---

### Post by G Morgan on 2007-03-29
The part where the licensing comes into question is derived work. It isn't explicitly specified in the license what is and isn't a derived work (there is a vague description which is more subjective than your sexual preferences). Under some people's interpretations anything that runs on the same computer would be a derived work. As far as the FSF is concerned the binary firmware needed to run my wireless card violates the GPL.

Nobody has established that the shim constitutes a derived work. That would have to be done in court. All we can say is companies with huge legal budgets are shipping binary drivers and the people in charge of the kernel have not come out and explicitly stated that this is illegal and Linus as at best said the issue is grey and even established some conditions which he would consider it not to be a derived work.

---

### Post by samjh on 2007-03-29
With all due respect to Linus Torvalds, his opinion is opinion only, not necessarily absolute truth.  Given the fact that Torvalds is a software developer, and not a lawyer (has he ever had legal training?), his legal opinion carries no greater weight than any punter.

Torvalds may consider the likes of nVidia's binary drivers as illegal.  He has not clearly stated his position in the quotes provided throughout this thread.

Regardless of what Mr. Torvalds thinks, there is only one place where the legality of nVidia drivers can be decided: in a court of law.

If binary drivers such as those of ATI, nVidia, and probably many others, are truly illegal, and the Linux community or its "governing" body believes that they are illegal, then they should contest this in court and determine what is legally acceptable for Linux.

Until that test is applied, any claims of illegality, and any quoting, finger-pointing, or arguments, are merely academic.  The very paper (or disk space) that the GPL is written on is of little worth until that test.  A toothless tiger, if you wish to view it that way.

Now, what will Linux as a whole, gain from legally challenging nVidia or ATI about their binary drivers?  This is where principle needs to be balanced against practicality.  Does the Linux community uphold its "free and open source" principle to the very letter?  Or shall it compromise and allow "non free and closed source" software for the sake of practicality?

I think it is safe to say that both nVidia and ATI would have done their homework regarding their legal position, should their binary drivers be challenged in a court of law.  I think it is safe to say that both companies either feel safe about their legal position, or feel that such a challenge will not occur in the foreseeable future due to reasons of practicality.

---

### Post by G Morgan on 2007-03-29
Actually Linus is very important here. He speaks for the Linux kernel community. Essentially the most strict case of GPL enforcement will not be the general case, it will be the maximum. If a person states 'my project is GPL but hell, close it up and have fun' the courts will interpret that as a modifier to the contract. If tomorrow Linus declared the Nvidia driver to be legal then as dictator for life on the kernel team that would stand up in court until he officially retracted that statement or was removed from the position to make it with his replacement retracting it.

What people say is important. If not in general to their own project. This entire debate focuses on the kernel.

---

### Post by SunnyRabbiera on 2007-03-29
well with all idealism aside if a distro wasnted to include the nvidia drivers it is thier priority, after all nvidia's outlook to linux is mostly positive as they have done some good work.
if people want to include nonfree drivers in thier system, I say let them go ahead, that way people cant say "linux cannot load my (insert device here)!"

---

### Post by cowlip on 2007-03-29
except when Nvidia drops support for "old" cards...never mind ATI's horrible awful drivers that don't support xvmc or aiglx.  Sorry

I just tried to open Beryl on my Ti 4200 card and it doesn't work.  Nvidia is not supporting this card with drivers anymore.  I will never buy another ATI or Nvidia card again is all I have to say, until they open their drivers.

---

### Post by G Morgan on 2007-03-30
> **SunnyRabbiera said:**
> well with all idealism aside if a distro wasnted to include the nvidia drivers it is thier priority, after all nvidia's outlook to linux is mostly positive as they have done some good work.
if people want to include nonfree drivers in thier system, I say let them go ahead, that way people cant say "linux cannot load my (insert device here)!"

We are trying to set idealism aside here. Far too many people want to interpret the GPL in it's strongest wording because that's what fits their (and my own) ideals*. Whatever it is meant to be it has a form in reality that doesn't precisely match that otherwise the Novell deal would already be against the rules and TiVoisation would be impossible. 

While it has stood up in court given that the court considered the work in question to be a derivative work it does not mean the precedent has been set in general** nor does the GPL exclude people from establishing a verbal contract. Essentially if the head of a GPL project says 'this is not a derived work under the GPL' that will stand up in court for the period from when it was said to the point a retraction was given.

*this is dangerous because there are gaps in it and legal loopholes. The GPL is not bug free. Like software, no license ever will be.

**it doesn't mean that the court will always consider the same technical measures to constitute a derived work (there could be mitigating circumstances) and not all of those technical measures have been tested.

---

### Post by hyper_ch on 2007-03-30
> **G Morgan said:**
> Actually Linus is very important here. He speaks for the Linux kernel community. Essentially the most strict case of GPL enforcement will not be the general case, it will be the maximum. If a person states 'my project is GPL but hell, close it up and have fun' the courts will interpret that as a modifier to the contract. If tomorrow Linus declared the Nvidia driver to be legal then as dictator for life on the kernel team that would stand up in court until he officially retracted that statement or was removed from the position to make it with his replacement retracting it.

What people say is important. If not in general to their own project. This entire debate focuses on the kernel.

I don't agree with that. If you release software under a licence then that licence is applicable... however you as creator of that software can release the same software under multiple licences... in the beginning or later... that is up to you... that is within your powers.

A contract cannot be simply altered by one party.. it always needs to consent of both or a provision within the contract (licence) that one party can alter it (and to which extend and under what circumstances). That's what makes it a contract - a mutual agreement...

e.g. I have this piece of software and it is GPLed... then it is GPLed regardless of that the original creator says now. The time I got that piece of software it was GPLed... however if the author decides now to also publish it as modified BSD licence then, in theory, I would be required - if I wished to have it as BSD - to get hold of the BSD-version of that software because then one I got is GPLed and I am not allowed to alter the licence under GPL...

---

### Post by G Morgan on 2007-03-30
That's what the FSF would like to believe but just as the BPI stating that 'We don't mind Brits ripping CDs to their MP3 players' makes it legal irrespective of the fact British law normally does not guarantee a fair usage right nor did the license the public buy the music under, the same would hold true for the GPL.

You must stop thinking of the law as a logical process. It is not, has never been and never will be. It is standard to think of Linus as the dictator for life in terms of the kernel, this is a generally accepted point that no one has openly challenged as of yet. So if Linus says the GPL doesn't matter that would become legally binding until retracted. Note that a copyright holder could at this point come in and say he no longer accepts that Linus speaks for the kernel project. This would probably remove the established power he has over that persons work but even then it would still allow GPL abuse on the rest of the kernel.

This is the problem I find in the understanding of the law in the community, programmers are too used to programming languages and think everything else is just a set of instructions. IANAL but know enough to know that there is no such thing as deterministic law. It isn't A => B but whether the judge and/or jury considers X to be reasonable. All subjective, all open to interpretation and all about as certain as the assumption I will find Jessica Alba waiting in my bed when I head home tonight. Judges will bend the law to make things more sensible, when you have a widely distributed copyright holder base he will establish a person or group that speaks for all the holders as established by the community either explicitly or implicitly until otherwise objected to.

Look I don't want to sully the GPL but we must establish common sense. As of yet it hasn't been an issue because we haven't seen people in the community breaking rank and claiming a free for all. I don't think it will happen either. However it is important to note that every license/contract has circumstances under which it collapses. Even the GPL. Lawyers are keen on saying 'You can be sued for anything, at any time and there is always a chance you can lose', same applies here.

---

### Post by saulgoode on 2007-03-30
> **G Morgan said:**
> You must stop thinking of the law as a logical process. It is not, has never been and never will be. It is standard to think of Linus as the dictator for life in terms of the kernel, this is a generally accepted point that no one has openly challenged as of yet. So if Linus says the GPL doesn't matter that would become legally binding until retracted.

Sorry, but that is just plain nonsense. When I release software under the GPL, it is a license to use my code *only if you abide that license*. There are "contributions" to the kernel (just like any other Free Software project) which were never written with the kernel in mind; therefore what you are suggesting is that kernel developers have the right to take whatever GPLed software is out there, incorporate it into the kernel, and then Linus can negotiate "verbal agreements" which ignore the licensing of the original copyright holder. That is not how it works and it is ridiculous to suggest that is how it works. GPLed software is a public pool of software and Linus Torvalds holds no special status in determining how that pool is distributed.

> **G Morgan said:**
> Judges will bend the law to make things more sensible, when you have a widely distributed copyright holder base he will establish a person or group that speaks for all the holders as established by the community either explicitly or implicitly until otherwise objected to.

Judges may not understand the intracacies of software technology, but they understand multiple copyright holders (and patent holders, as the recent MS MP3 patent finding revealed). Let me provide one more posting by Linus on the LKML (something which you have yet to do, though you would speak on his behalf):

> **"Linus Torvalds"]But if you want to explain something to a judge, you get a real lawyer, and you make sure that the lawyer tries to explain the issue in non-technical terms. Because, quite frankly, the judge is not going to buy a technical discussion he or she doesn't understand.

Just as an example, how do you explain to a judge how much code the Linux kernel contains? Do you say "it's 6 million lines of C code and header files and documentation, for a total of about 175MB of data"?

Yeah, maybe you'd mention that, but to actually illustrate the point you'd say that if you printed it out, it would be a solid stack of papers 100 feet high. And you'd compare it to the height of the court building you're in, or something. Maybe you'd print out one file, bind it as a book, and wave it around as one out of 15,000 files.

But when you ask me about how big the kernel is, I'd say "5 million lines". See the difference? It would be silly for me to tell you how many feet of paper the kernel would print out to, because we don't have those kinds of associations.

Similarly, if you want to explain the notion of a kernel module, you'd compare it to maybe an extra chapter in a book. You'd make an analogy to something that never ever mentions "linking".

Just imagine: distributing a compiled binary-only kernel module that can be loaded into the kernel is not like distributing a new book: it's more like distributing a extra chapter to a book that somebody else wrote, that uses all the same characters and the plot, but more importantly it literally can only be read together with the original work. It doesn't stand alone.

In short, Your Honour, this extra chapter without any meaning on its own is a derived work of the book.

In contrast, maybe you can re-write your code and distribute it as a short-story, which can be run on its own, and maybe the author has been influenced by another book, but the short-story could be bound as is, and a recipient would find it useful even without that other book. In that case, the short story is not a derived work — it's only inspired.[/quote]


[QUOTE=G Morgan said:**
> Look I don't want to sully the GPL but we must establish common sense. As of yet it hasn't been an issue because we haven't seen people in the community breaking rank and claiming a free for all. I don't think it will happen either. However it is important to note that every license/contract has circumstances under which it collapses. Even the GPL. Lawyers are keen on saying 'You can be sued for anything, at any time and there is always a chance you can lose', same applies here.

I am by no means arguing the way I would prefer things to be (or even what may or may not be "common sense"). I am pointing out the legalities of the NVidia drivers as I interpret copyright law and Fair Use. A judicial court won't care a rodent's fundament whether I (or Linus Torvalds, for that matter) think the world would be a better place if copyright laws were ignored, they will care whether code has been used in violation of the licensing of its copyright holder.

---

### Post by prizrak on 2007-03-30
G Morgan,
Couple of things,
1) Once something has been released under a certain license it stays under that license for as long as the legal system that honors that license exists. Linus can take HIS (and anyone else's who agrees to it) parts of the kernel and release them under a new license. However what was released before will stay under the original license. This happened with XFree86 and Xorg, XFree decided to go closed and Xorg took the last open version of XFree and forked it. Linus is not a sole copyright holder of the kernel, there are thousands of people who have contributed and they all hold copyright (by default) to their parts unless they EXPLICITLY (nothing works implicitly in the court of law) signed their rights over to Linus. Basically anything he says about legality has no bearing on the kernel if it were reviewed in the court of law. 

2) The question is not only of the derived work but one of distribution. It is generally accepted that once you get your GPL'ed system you can do whatever you want with it. The GPL allows for full control by the end user and does not limit the end user's rights in any way. However, when you distribute something the GPL has provisions that in effect do limit what you can do. The question is, how do you judge something to be distributed. 

Here is the challenge. If you put the nVidia driver on the CD that Ubuntu also comes with but it doesn't get installed and activated unless it detects an nVidia card would you call that distribution? Or would distribution mean that the driver is already part of Ubuntu itself? By the same token when Dell preinstalls Linux on their computer and installs the binary drivers would that be a distribution or not? You will hear people argue for both. From one point of view of course it is being distributed to the end user, from another point of view it isn't part of the OS until it actually needs to be. From Dell's point of view the hardware is distributed and paid for, software is simply bundled.

---

### Post by G Morgan on 2007-03-30
We're clearly going round in circles here. I don't think anyone is going to change their mind on this. The phrase 'The law is an ***' exists for a very good reason. Law is not to be trusted at any moment in time by a sane person because it fails as often as it works and is adjudicated on by people who will not understand however you explain it to them since they lack the necessary years of experience.

Anyway I'll leave it at that otherwise we will get stuck in an infinite loop and then only Linux will get us out of it.

---

### Post by G Morgan on 2007-03-30
> **prizrak said:**
> G Morgan,
...

Here is the challenge. If you put the nVidia driver on the CD that Ubuntu also comes with but it doesn't get installed and activated unless it detects an nVidia card would you call that distribution? Or would distribution mean that the driver is already part of Ubuntu itself? By the same token when Dell preinstalls Linux on their computer and installs the binary drivers would that be a distribution or not? You will hear people argue for both. From one point of view of course it is being distributed to the end user, from another point of view it isn't part of the OS until it actually needs to be. From Dell's point of view the hardware is distributed and paid for, software is simply bundled.

That's an important distinction of where the judge might say it doesn't constitute a derived work until the person installs it on their computer, hence no distribution. This can easily be argued in court.

Also what if I took the Nvidia driver and just linked every call to Hello World and claimed that is how it is meant to work. I can then even install in on the machine (no need to compile) and claim it's only a derived work of Hello World. If the person runs a script to instead point it towards the kernel after the fact then it is also not distribution of a derived work.

I was going to leave this argument but you had to raise a relevant point didn't you ;) .

---

### Post by prizrak on 2007-03-30
> **G Morgan said:**
> That's an important distinction of where the judge might say it doesn't constitute a derived work until the person installs it on their computer, hence no distribution. This can easily be argued in court.

Also what if I took the Nvidia driver and just linked every call to Hello World and claimed that is how it is meant to work. I can then even install in on the machine (no need to compile) and claim it's only a derived work of Hello World. If the person runs a script to instead point it towards the kernel after the fact then it is also not distribution of a derived work.

I was going to leave this argument but you had to raise a relevant point didn't you ;) .

LOL sorry

---

### Post by el mariachi on 2007-03-30
> **kinematic said:**
> including closed source drivers(or installing them yourself)with the linux kernel IS illegal.
each and every driver included must honor the license under wich the kernel is released,in this case the gpl.
this means that the source must be freely obtainable and redistributable but if nvidia/ati where to do that they would violate patents owned by other companies because they both license technologie from third parties.

if installing these drivers is ilegal, how come nvidia releases Linux specific drivers? seems a contradiction...:confused:

---

### Post by hyper_ch on 2007-03-30
Have a read at the GPL... GPL says it is illegal to distribute GPLed code with proprietary code...
However you can for your own install proprietary code into GPLed software... you just may not distribute that bundle... that's not a contradiction :)

---

### Post by G Morgan on 2007-03-30
> **hyper_ch said:**
> Have a read at the GPL... GPL says it is illegal to distribute GPLed code with proprietary code...
However you can for your own install proprietary code into GPLed software... you just may not distribute that bundle... that's not a contradiction :)

It doesn't say that at all. Back to the infinite loop but it says anything that can reasonably be considered a derived work must be GPL. It doesn't actually give more than a vague description of what a derived work is. Also you make it sound as if aggregation is in violation as well.

"In addition, mere aggregation of another work not based on the Program with the Program (or with a work based on the Program) on a volume of a storage or distribution medium does not bring the other work under the scope of this License." - Clause 2, GPLv2, final paragraph.

So you can distribute proprietary code with GPL'd code given that they do not constitute a derived work. It would be perfectly legal to distribute the Sun JDK with a distribution if you can meet the Sun license for distribution.

You probably didn't mean that but the English language is clumsy and it's important to highlight the difference between derived and aggregated works.

---

### Post by prizrak on 2007-03-30
> **G Morgan said:**
> It doesn't say that at all. Back to the infinite loop but it says anything that can reasonably be considered a derived work must be GPL. It doesn't actually give more than a vague description of what a derived work is. Also you make it sound as if aggregation is in violation as well.

"In addition, mere aggregation of another work not based on the Program with the Program (or with a work based on the Program) on a volume of a storage or distribution medium does not bring the other work under the scope of this License." - Clause 2, GPLv2, final paragraph.

So you can distribute proprietary code with GPL'd code given that they do not constitute a derived work. It would be perfectly legal to distribute the Sun JDK with a distribution if you can meet the Sun license for distribution.

You probably didn't mean that but the English language is clumsy and it's important to highlight the difference between derived and aggregated works.
The main point here is of course that you are not bound by the GPL in any way shape or form if you don't distribute w/e it is that you do.

---

