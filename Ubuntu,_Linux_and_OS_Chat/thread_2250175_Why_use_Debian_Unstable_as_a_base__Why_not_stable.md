---
title: "Why use Debian Unstable as a base ? Why not stable ?"
date: 2014-10-27
forum: Ubuntu, Linux and OS Chat
---

### Post by linuxyogi on 2014-10-27
Hi,

AFAIK Ubuntu is based on Debian's unstable branch. 

I have realized the fact that some users don't like the 

idea of Ubuntu becoming a rolling release. 

So if the reason behind that is to maintain stability 

then why not choose the stable branch instead ?

An alternative might be to use the Debian Stable

branch for every LTS release and the unstable 

branch for the short term releases.

I mean hopefully that will keep the number of crash 

reports that appear on start up to a minimum.


Also, personally I like rolling release distros but at 

the same time I hate the amount of updates that I

need to download every week under 

Manjaro (Dual boot) .

What I want is a stable base, just like Debian stable 

and latest packages for only some apps like Firefox,

VLC and qbittorrent. 

I am on the default update channel of Aurora. I downloaded 

the tarball so FF is updated quite frequently.

14.10 has VLC 2.2.0 atm so its even higher than their official

stable release but since the version freezes in Ubuntu I guess

I wont receive newer versions in future.

---

### Post by Bucky Ball on 2014-10-27
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Better here and I removed the font formatting. Please use text wrap and regular, single spaced paragraphs. Unsure why your text has come out like that.

---

### Post by grahammechanical on 2014-10-27
I am a little confused. You do not like the idea of Ubuntu being based upon Debian unstable but you seem to want the very latest versions of some packages and are not happy that the very latest of those packages does not always make it in the latest release of Ubuntu due to feature freeze.

As I understand things from just a little reading, Ubuntu syncs with Debian every six months and it syncs with Debian unstable because that is where the new stuff in Debian is being put. If Ubuntu was to sync with Debian stable then there would be little change over the year. This method of basing Ubuntu on Debian has been the way things are done long before some developers started pushing for a rolling release version of Ubuntu.

Every release of Ubuntu is meant to be stable, even the code base being developed into the next version of Ubuntu. I have been using the Ubuntu development release for more than two years. I used Utopic Unicorn (14.10) all through its 26 week development cycle. I found it so stable as to be boring. I am right now using Vivid Vervet (15.04 under development). Stability is the aim even for the Ubuntu version under development. This is for the purpose of allowing application developers to develop their applications on the latest Ubuntu instead waiting until the next version is released.

Mark Shuttleworth wanted to do away with Interim releases completely and just have an LTS release every 2 years and the development release. He did not want an actual rolling release. He saw no need for it because Ubuntu has the development release for those who want the very bleeding edge (his words). He wanted to reduce the work load of maintaining so many Ubuntu releases. There was a compromise. The Interim releases are still with us but they only get 9 months support. 

Ubuntu is more than Debian with the Unity user interface. There is a lot of Ubuntu code that is distinct from Debian. There is a lot of Ubuntu code that is distinct from Gnome.

Regards.

---

### Post by ian-weisser on 2014-10-27
> **linuxyogi said:**
> An alternative might be to use the Debian Stable
branch for every LTS release and the unstable 
branch for the short term releases.

Couple possible issues:
1) Debian Stable releases are not matched to the LTS release schedule. If Debian Stable releases four months before an LTS, this is a great idea. If Debian Stable releases 18 months before the LTS, then I imagine you'll see a lot of complaints like "Why did the new LTS revert me two versions of Firefox?" and "Why does my new hardware no longer work?"

2) You are asking Ubuntu to run two completely parallel toolchains, testing programs, and repository imports. One of which runs only every two years (reinventing that wheel each time). That seems like a tremendous amount of extra work. Is the benefit worthwhile? Would using Debian Stable for LTS actually prevent or cure a significant percentage of crash reports?


> **linuxyogi said:**
> What I want is a stable base, just like Debian stable 
and latest packages for only some apps like Firefox,
VLC and qbittorrent. 

I think that a 'stable base' is more myth than reality. Hardware changes constantly, and the kernel and numerous systems (Udev. Mir/X) must evolve to keep up. Those lead to second-order changes: Init systems, interprocess communication, introspection/interrogation tools, etc. Plus more changes caused by newly-reported bugs, and even more changes to fix newly-discovered vulnerabilities.

---

### Post by craig10x on 2014-10-27
Actually, thanks to unity 8 and the new package management system that will be part of the desktop, ubuntu will become a rolling style release but one with stability and yet will bring in the newer apps and other stuff as they are stable and ready, because the desktop will be capable of updating in the same manner the phone/tablet versions of ubuntu will be able to do...it's called CONVERGENCE and is expected by no later the 16.04...

What will likely happen is that LTS will remain the same as it is now, but the 6 month version will morph into the new version that i just described...so, there would not be much point to switching to debian stable and besides that, as previously mentioned, the newer packages are first developed in debian unstable...it's a pretty long wait until debian stable gets them...
[http://news.softpedia.com/news/Canonical-Details-Plans-for-Unity-8-Integration-in-Ubuntu-Desktop-462117.shtml](http://news.softpedia.com/news/Canonical-Details-Plans-for-Unity-8-Integration-in-Ubuntu-Desktop-462117.shtml)

---

### Post by mastablasta on 2014-10-27
stable branch is old (old software).
stable branch doesn't mean bugfixes.
stable branch has old kernel (means worse HW support).

new proposal for Ubuntu was to keep basic OS on LTS and update software. rather than keeps it at single version. something many users are doing now via PPA. besides it is kind of ridiculous that you should either upgrade to get new software or be condemned to old version of software from official repos. sometimes new software brings in much needed features. but should you update the OS just to have that? well we will see how it develops.

I was recently faced with Debian conservative thinking that didn't help me at all as a user. software had an annoying bug that produced mass errors in logs (I am talking about log spam every second). devs knew it had it. patch was released. it was decided it wont' be ported back to old stable. then it was decided that it won't be ported to current stable. it might be in next stable. or maybe not. maybe they will just leave the bug as it is. who cares about the users? who cares they get log spam with monitoring software enabled? who cares the devices are displayed in a non human way.... obviously not debian decision makers. 

I stayed on it non the less but I am configuring it all in a way that would be possible to port it to Ubuntu if necessary. writing down things as I go and set it all up. so far I could juts install Ubuntu and move a few config files over. I am curious however to see what all the fuss about Stable is about. so I plan to run this server for a year on stable. let's see how it goes. 

as for the bug I patched it my self using the friendly Chrunchbang forums and their solution. I also had to remove monitoring software (that in connection to the bug caused excessive loging) . in the end I am left with normal system logs and security logs.

---

### Post by linuxyogi on 2014-10-27
> **grahammechanical said:**
> 
Every release of Ubuntu is meant to be stable, even the code base being developed into the next version of Ubuntu. I have been using the Ubuntu development release for more than two years. I used Utopic Unicorn (14.10) all through its 26 week development cycle. I found it so stable as to be boring. I am right now using Vivid Vervet (15.04 under development). Stability is the aim even for the Ubuntu version under development. This is for the purpose of allowing application developers to develop their applications on the latest Ubuntu instead waiting until the next version is released.


I don't face any major stability issues with Ubuntu. Its just those annoying crash reports. When I Google I find someone has already filed a bug report. This is usual for me for all releases I have used after 8.04. I have seen threads about this specific issue quite a lot and I have no explanation for it. I once tried using Antergos which uses the Arch repos directly. I used to read the Arch news everyday and upgrade. Everything was fine for three days but on the fourth day it went haywire. Although restoration was as simple as downgrading the problematic package but it kept happening and I move to Manjaro again. When I mentioned this on the Manjaro forums some said they experienced the same thing while others said they have been running upgrades for years without a single breakage. 


> **ian-weisser said:**
> Couple possible issues:
1) Debian Stable releases are not matched to the LTS release schedule. If Debian Stable releases four months before an LTS, this is a great idea. If Debian Stable releases 18 months before the LTS, then I imagine you'll see a lot of complaints like "Why did the new LTS revert me two versions of Firefox?" and "Why does my new hardware no longer work?"

2) You are asking Ubuntu to run two completely parallel toolchains, testing programs, and repository imports. One of which runs only every two years (reinventing that wheel each time). That seems like a tremendous amount of extra work. Is the benefit worthwhile? Would using Debian Stable for LTS actually prevent or cure a significant percentage of crash reports?

I think that a 'stable base' is more myth than reality. Hardware changes constantly, and the kernel and numerous systems (Udev. Mir/X) must evolve to keep up. Those lead to second-order changes: Init systems, interprocess communication, introspection/interrogation tools, etc. Plus more changes caused by newly-reported bugs, and even more changes to fix newly-discovered vulnerabilities.

> **craig10x said:**
> Actually, thanks to unity 8 and the new package management system that will be part of the desktop, ubuntu will become a rolling style release but one with stability and yet will bring in the newer apps and other stuff as they are stable and ready, because the desktop will be capable of updating in the same manner the phone/tablet versions of ubuntu will be able to do...it's called CONVERGENCE and is expected by no later the 16.04...

What will likely happen is that LTS will remain the same as it is now, but the 6 month version will morph into the new version that i just described...so, there would not be much point to switching to debian stable and besides that, as previously mentioned, the newer packages are first developed in debian unstable...it's a pretty long wait until debian stable gets them...
[http://news.softpedia.com/news/Canonical-Details-Plans-for-Unity-8-Integration-in-Ubuntu-Desktop-462117.shtml](http://news.softpedia.com/news/Canonical-Details-Plans-for-Unity-8-Integration-in-Ubuntu-Desktop-462117.shtml)

> **grahammechanical said:**
> I am a little confused. You do not like  the idea of Ubuntu being based upon Debian unstable but you seem to  want the very latest versions of some packages and are not happy that  the very latest of those packages does not always make it in the latest  release of Ubuntu due to feature freeze. 

I want exactly what they are planning to do 

[http://news.softpedia.com/news/Canonical-Details-Plans-for-Unity-8-Integration-in-Ubuntu-Desktop-462117.shtml](http://news.softpedia.com/news/Canonical-Details-Plans-for-Unity-8-Integration-in-Ubuntu-Desktop-462117.shtml)

I was thinking about the mismatch between Ubuntu and Debian's release cycle too
but this solves it all but I am not sure about one thing and that it the article talks about Unity only. So is this a Unity 8 only thing ? I mean can I expect the same idea that is CONVERGENCE applied to all the other variants like Xubuntu, Kubuntu, Lubuntu, etc ?

Thanks a lot for that link.

> **mastablasta said:**
> stable branch is old (old software).
stable branch doesn't mean bugfixes.
stable branch has old kernel (means worse HW support).

new proposal for Ubuntu was to keep basic OS on LTS and update software. rather than keeps it at single version. something many users are doing now via PPA. besides it is kind of ridiculous that you should either upgrade to get new software or be condemned to old version of software from official repos. sometimes new software brings in much needed features. but should you update the OS just to have that? well we will see how it develops.

I was recently faced with Debian conservative thinking that didn't help me at all as a user. software had an annoying bug that produced mass errors in logs (I am talking about log spam every second). devs knew it had it. patch was released. it was decided it wont' be ported back to old stable. then it was decided that it won't be ported to current stable. it might be in next stable. or maybe not. maybe they will just leave the bug as it is. who cares about the users? who cares they get log spam with monitoring software enabled? who cares the devices are displayed in a non human way.... obviously not debian decision makers. 

I stayed on it non the less but I am configuring it all in a way that would be possible to port it to Ubuntu if necessary. writing down things as I go and set it all up. so far I could juts install Ubuntu and move a few config files over. I am curious however to see what all the fuss about Stable is about. so I plan to run this server for a year on stable. let's see how it goes. 

as for the bug I patched it my self using the friendly Chrunchbang forums and their solution. I also had to remove monitoring software (that in connection to the bug caused excessive loging) . in the end I am left with normal system logs and security logs.

I don't maintain any servers. I tried Debian stable Whezzy for only a short period of time. I noticed 2 things, a) no crash reports and b) very few updates. After reading what you have written it seems like those crash reports didn't appear because they don't have that system in the first place and stability may not be the only reason behind fewer updates may its laziness to some extent.

---

### Post by craig10x on 2014-10-27
@linuxyogi: yeah, that is the only thing that isn't really explained about how convergence works...for me it would be no problem because i use unity, anyway...but it's not clear how it affects other versions of ubuntu (like kubuntu/lubuntu/xubuntu/mate/etc)...If anyone knows anything about that aspect, perhaps they will jump in here...

---

### Post by ian-weisser on 2014-10-27
If the Desktop Environment (DE) is not designed for a phone, then you might be able to install it.
Without Mir, that install might brick your system. If X worked well on that hardware, we wouldn't need Mir.
Without Unity, that install might be unusable. Icons and menus off the edge of the screen, no way to reach them, and no keyboard/mouse.

As convergence gets closer, each Ubuntu flavor will decide (or change it's mind) about the direction it wants to go.
No flavor is required to use Mir, nor to support tiny phone hardware.
Some flavors may decide to try. Some new flavors may emerge.
Good recurring discussion topic for Ubuntu Online Summits.

---

### Post by mips on 2014-10-27
OP sounds confused.

Debian Stable is nice and stable, captain obvious speaking. Manjaro updates are not really that heavy and if you prefer smaller more frequent updates switch to Manjaro Unstable, Arch or Gentoo which has it's downsides wrt stability.

A part of the linux community is full of crap & don't know what they want even though the choices available to them are endless, sigh...

---

### Post by mikodo on 2014-10-27
> **ian-weisser said:**
> 

<snippets>

As convergence gets closer, each Ubuntu flavor will decide (or change it's mind) about the direction it wants to go.
No flavor is required to use Mir, nor to support tiny phone hardware.
Ahh! That, really made my day!

I can worry less now, about derivatives. I understand now for example, how Kubuntu devs have remained steadfast, that it won't use Mir.

I appreciate, SABDFL/Canonical/Ubuntu more, each day.

---

### Post by /ADM on 2014-10-28
I hope it will never become a rolling release.  I only connect my main machine when needed, at times it is weeks apart, rolling releases tend to self-destruct with this and demand users are online constantly.  It is about loosing control, I demand to check each update manually instead of blindly updating everything.

---

### Post by craig10x on 2014-10-28
The kind of rolling release it would become is not in the traditional sense...it would be a stable core with stable updates of stuff when READY not when being tested...it would be more like an android phone app concept of getting new versions of things...the core and the apps get changes when ready and stable...you not going to be getting tons of updates each day...and it wouldn't be anything like development branch on ubuntu, either...read that article link i provided carefully...note below (when they are READY)...

[COLOR=#000000][FONT=museo_sans]The new desktop packaging system means that application developers can push updates out when they are ready and the user can benefit right away," says Will Cooke.[/FONT][/COLOR]

---

### Post by mastablasta on 2014-10-28
> **linuxyogi said:**
> I don't maintain any servers. I tried Debian stable Whezzy for only a short period of time. I noticed 2 things, a) no crash reports and b) very few updates. After reading what you have written it seems like those crash reports didn't appear because they don't have that system in the first place and stability may not be the only reason behind fewer updates may its laziness to some extent.

my issue with that is that the package in the in repos is causing the mass errors. while at the same time bug is present only shown in different way upon install. try df -h in debian stable and compare it to Ubuntu output.

> **ian-weisser said:**
> If the Desktop Environment (DE) is not designed for a phone, then you might be able to install it.
Without Mir, that install might brick your system. If X worked well on that hardware, we wouldn't need Mir.
Without Unity, that install might be unusable. Icons and menus off the edge of the screen, no way to reach them, and no keyboard/mouse.

As convergence gets closer, each Ubuntu flavor will decide (or change it's mind) about the direction it wants to go.
No flavor is required to use Mir, nor to support tiny phone hardware.
Some flavors may decide to try. Some new flavors may emerge.
Good recurring discussion topic for Ubuntu Online Summits.

but isn't wayland replacing X? and isn't wayland also made for phones and such?

---

### Post by linuxyogi on 2014-10-28
> **mips said:**
> OP sounds confused.

Debian Stable is nice and stable, captain obvious speaking. Manjaro updates are not really that heavy and if you prefer smaller more frequent updates switch to Manjaro Unstable, Arch or Gentoo which has it's downsides wrt stability.

A part of the linux community is full of crap & don't know what they want even though the choices available to them are endless, sigh...

Full of crap OP wants something like [this]("http://chakraos.org/wiki/index.php?title=Half-Rolling_Release_Model") 

> Core  The *core layer* consists of software that is critical for an operational system, such as the graphics or sound subsystems.  This layer is not updated as soon as possible, but following a more *tradicional time-based approach*. Its software packages are updated following *predefined schedules*.  Unlike the traditional release model, though, there isn&#8217;t a single  schedule for all the packages: it is a loosely<ref>In the sense  that schedules are not strictly defined. For example, a group of  packages can be updated *twice a year*, as opposed to *every six months* or *every 180 days*.</ref> ** time-based** release model on a **group basis**, where for different groups of packages there are different schedules.  This ensures the system is always **stable**. 


> Applications  The *applications layer* contains the rest of the software, including the applications users interact with.  These packages are updated following an **application-based rolling** release model, where end-user applications are updated following the *rolling release model*, whereas their dependencies also roll *but*  only as long as updating them does not prevent the end-user  applications from running smoothly, or makes them loose functionality.  That way you can always enjoy **bleeding-edge** application. 


Using Manjaro's unstable branch is almost the same as vanilla Arch. I have already tired that.
Didn't work for me. 

My hardware can't handle Unity so I hope Lubuntu or Xubuntu gets added to CONVERGENCE. I mean a ready to install iso (in future).

---

### Post by Lars Noodén on 2014-10-28
> **linuxyogi said:**
> This ensures the system is always stable. 

That's using the word stable in a different context than is meant by Debian-stable or Debian-unstable.  It is not unstable like MS, where it crashes and such.  It means stable in that the software selection, including versions, stay the same.  In other words, it is not changing.  New versions can have different functionality which introduce new behaviors, at best.  For example, going from Apache 1.3 to Apache 2.0 or from PHP 5.3 to 5.4 would cause lots of trouble if not planned in advance meticulously.  

That kind of surprise change is not desirable for most production environments.  [https://wiki.debian.org/DebianStability](https://wiki.debian.org/DebianStability)  Part of the problem is that over the years, MS has brought the focus away from the original use of stable in software engineering where it meant changing/unchanging to where it means reliable/unreliable.  Part of that has been about making bad engineering not only acceptable but expected.  But I digress.  

To address on of the questions in the original post, Debian unstable is more reliable and unchanging than some other systems, yet still has fairly new versions of the popular packages.

Edit: here's a little more on the relation between stable, testing, and exermental/unstable: [http://www.zdnet.com/debian-stable-or-debian-testing-which-linux-is-right-for-you-7000027776/](http://www.zdnet.com/debian-stable-or-debian-testing-which-linux-is-right-for-you-7000027776/)

---

### Post by mastablasta on 2014-10-28
or in other words - if a program crashes constantly on a certain occasion (let's say always when you press alt+z+F2) it means it's behaviour is predictable. Such a program can be consider stable if you don't do any changes to it, it would always crash at that point. :)

---

