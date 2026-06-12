---
title: "Harsh but fair criticisms for Linux on the Desktop, 2016 edition"
date: 2016-03-16
forum: The Cafe
---

### Post by user1397 on 2016-03-16
[http://itvision.altervista.org/why.linux.is.not.ready.for.the.desktop.current.html](http://itvision.altervista.org/why.linux.is.not.ready.for.the.desktop.current.html)

I just came upon this post, and although it may seem harsh at times, you've gotta admit the guy is being objective and fair, and corrects anything he said wrong (users can comment and have corrected him on a few things, which he has crossed out).  I just think it's a good thing to sometimes take a hard look at yourself (as in the Linux community) in the mirror and face the facts.

Here is his own TL;DR version summary, although I strongly advise reading the whole thing:

> 
[h=3]Summary[/h]
[LIST]
[*]**No [stability]("http://alien.slackbook.org/blog/kde-update-4-14-2-no-kde5-updates-yet-devs-need-to-get-their-act-together/"), [bugs]("http://www.dedoimedo.com/computers/fedora-18-kde.html"), [regressions]("https://www.google.com/search?hl=en&q=regression+site%3Alkml.org"), [regressions]("https://www.google.com/search?hl=en&q=regression+site%3Afreedesktop.org") [and]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/966744") [regressions]("https://bugs.kde.org/buglist.cgi?query_format=specific&order=relevance+desc&bug_status=__open__&product=&content=regression")**: There's an *incredible* amount of [regressions]("https://plus.google.com/u/0/111104121194250082892/posts/aCiB7kTLXTh")(both in the [kernel]("http://codemonkey.org.uk/2013/03/01/39-merge-window-fallout/") and in user space applications) when things which used to work break inexplicably, some of regressions can even lead to [data]("http://neil.brown.name/blog/20120615073245") [loss]("https://lkml.org/lkml/2012/10/23/690"). Basically there is no [quality control]("http://www.h-online.com/open/features/Kernel-Comment-Get-testing-1669920.html") ([QA/QC]("https://www.google.com/search?q=ext4+corruption+linux+4.0")) and regression testing in *most*Open Source projects (including the kernel) - Microsoft, for instance, [reports]("http://techcrunch.com/2012/10/25/microsoft-launches-windows-8-after-1-24b-hours-of-testing-available-on-over-1000-certified-devices/") that Windows 8 received *1,240,000,000 hours of testing* whereas new kernel releases get, I guess, under 10,000 hours of testing - and every Linux kernel release is comparable to a new Windows version. Serious bugs which impede normal workflow can take years to be resolved. A lot of crucial hardware (e.g. GPUs, Wi-Fi cards) isn't properly supported. Both Linux 4.1.9/4.1.10, which are considered "stable" (moreover this kernel series is also LTS(!)), crash under [any network load]("http://lwn.net/Articles/658749/"). WTF??
[*]**Hardware issues:** Under Linux many devices and devices features are still poorly supported or not supported at all. Some hardware (e.g. Broadcom Wi-Fi adapters) *cannot* be used unless you already have a working Internet connection. New hardware often becomes [supported]("http://apple.slashdot.org/story/12/08/16/1741235/linux-is-a-lemon-on-the-retina-macbook-pro") months after introduction. Specialized software to manage devices like printers, scanners, cameras, webcams, audio players, smartphones, etc. almost always just doesn't [exist]("https://www.phoronix.com/scan.php?page=news_item&px=MTEyNDA")- so you won't be able to fully control your new iPad and update firmware on your Galaxy SIII. Linux graphics support is a big bloody mess because kernel/X.org APIs/ABIs constantly change and NVIDIA/ATI/Broadcom/etc. companies don't want to allocate extra resources and waste their money just to keep up with an insane rate of changes in the Open Source software.
[*]**The lack of [standardization]("http://www.itwire.com/business-it-news/open-source/65402-torvalds-says-he-has-no-strong-opinions-on-systemd"), fragmentation, unwarranted & excessive variety, as well as no common direction or vision among different distros:** *Too many* Linux [distributions]("http://linux.slashdot.org/comments.pl?sid=2737589&cid=39424927") with incompatible and dissimilar configurations, packaging systems and incompatible libraries. Different distros employ *totally different* desktop environments, different graphical and console applications for configuring your computer settings. E.g. Debian based distros oblige you to use the strictly text based `dpkg-reconfigure` utility for certain system related maintenance tasks.
[*]**The lack of [cooperation]("https://lkml.org/lkml/2012/10/3/484") between open source developers and [internal]("http://permalink.gmane.org/gmane.linux.gentoo.devel/81901") [wars]("http://lists.gnu.org/archive/html/help-smalltalk/2012-12/msg00014.html"):** There's no central body to organize the development of different parts of the open source stack which often leads to a situation when one project introduces changes which [break]("https://bugzilla.redhat.com/show_bug.cgi?id=638477") other projects (this problem is also reflected in "Unstable APIs/ABIs" below). Even though the Open Source movement lacks manpower, different Linux distros find enough resources to fork projects (Gentoo developers are going to develop a udev alternative; a discord in ffmpeg which led to the emergence of libav; a situation around OpenOffice/LibreOffice; a new X.org/Wayland alternative - Mir) and to use own solutions.
[*]**A lot of rapid [changes]("http://theoden48.wordpress.com/2012/07/22/ive-gone-back-to-windows/")**: Most Linux distros have very [short]("https://news.ycombinator.com/item?id=3716884") upgrade/release cycles (as short as *six months* in some cases, or e.g. Arch which is a rolling distro, or Fedora which gets updated every six months), thus you are constantly bombarded with changes you don't expect or don't want. LTS (long term support) distros are in most cases *unsuitable*for the desktop users due to the policy of preserving applications versions (and usually there's no officially approved way to install bleeding edge applications - *please, don't remind me of PPAs and backports - these hacks are not officially supported, nor guaranteed to work*). Another show-stopping problem for LTS distros is that LTS kernels often do not support new hardware.
[*]**[Unstable]("http://upstream.rosalinux.ru/") [APIs]("http://itvision.altervista.org/files/history_api_break.png")/[ABIs]("http://itvision.altervista.org/files/abi_breaks.png") & the [lack]("https://wiki.archlinux.org/index.php/Steam#Steam_runtime_issues") of [real]("http://developerblog.redhat.com/2015/02/10/gcc-5-in-fedora/") [compatibility]("http://tech.slashdot.org/comments.pl?sid=3010389&cid=40798035"):** It's very [difficult]("https://web.archive.org/web/20140910085118/http://weblogs.mozillazine.org/asa/archives/008499.html") to use old *open* and closed source software in new distros (in many cases it becomes impossible due to changes in core Linux components like kernel, GCC or glibc). Almost [non-existent]("https://www.youtube.com/watch?v=5PmHRSeA2c8#t=357") backwards compatibility makes it incredibly difficult and costly to create closed source applications for Linux distros. Open Source software which doesn't have active developers or maintainers gets simply dropped if its dependencies cannot be satisfied because older libraries have become obsolete and they are no longer available. For this reason for instance a lot of KDE3/Qt3 applications are not available in modern Linux distros**even** though alternatives do **not** exist. Developing drivers out of the main Linux kernel tree is an excruciating and expensive chore. There's no [WinSxS]("https://en.wikipedia.org/wiki/Side-by-side_assembly") equivalent for Linux - thus there's no simple way to install conflicting libraries. **In 2015 Debian [dropped]("https://lwn.net/Articles/658809/") support for Linux Standard Base (LSB). Viva, incompatibility!**
[*]**Software issues:** Not that many games (mostly Indies) and few AAA games (Valve's efforts and collaboration with games developers have resulted in many recent games being released for Linux, however every year *thousands* of titles are still released for Windows exclusively[SUP]**[*]("http://itvision.altervista.org/why.linux.is.not.ready.for.the.desktop.current.html#SteamOS")**[/SUP]. More than 98% of existing and upcoming AAA titles are still unavailable in Linux). No familiar Windows software, no Microsoft Office (LibreOffice still has major troubles opening correctly [Microsoft Office]("http://www.zdnet.com/article/huge-savings-prompt-italian-city-to-dump-openoffice-for-microsoft-after-four-years/") produced documents), no native [CIFS]("https://en.wikipedia.org/wiki/Server_Message_Block") (*simple to configure and use, as well as password protected and encrypted* network file sharing) equivalent, no Active Directory or its featurewise equivalent.
[*]**Money, enthusiasm, motivation and responsibility**: I predicted years ago that FOSS developers would start drifting away from the platform as FOSS is no longer a playground, it requires substantial efforts and time, i.e. **the fun is over**, developers want real money to get the really hard work done. FOSS development, which lacks financial backing, shows its fatigue and disillusionment. The FOSS platform after all requires **financially** motivated developers as underfunded [projects]("http://ksensors.sourceforge.net/") [start]("https://www.phoronix.com/scan.php?page=news_item&px=MTEyNjI") [to wane]("http://ppenz.blogspot.nl/2012/06/dolphin-21.html") and [critical]("https://bugs.kde.org/duplicates.cgi?sortby=count&reverse=1&sortvisible=0&maxrows=50&changedsince=7&openonly=1") bugs stay open for years. One could say "Good riddance", but the problem is that oftentimes those dying projects have no alternatives or similarly featured successors.
[*]No [polish]("http://linux.slashdot.org/comments.pl?sid=2608362&threshold=5&commentsort=0&mode=thread&cid=38619928"), no [consistency]("http://linux.slashdot.org/comments.pl?sid=2608362&threshold=5&commentsort=0&mode=thread&cid=38623292") and no [HIG]("https://en.wikipedia.org/wiki/Human_interface_guidelines") adherence (even KDE developers [admit it]("http://lamarque-lvs.blogspot.com/2012/02/new-qml-shutdown-dialog-in-490.html?showComment=1330091928115#c3431625452916542616")).
[/LIST]


Also to be even more fair, he has an article about windows 10, iOS, and Android too.  Clearly he isn't a "fanboy" of any OS...seems like he hates them all equally :P

---

### Post by frank75 on 2016-03-16
I have to agree that sometimes an update or upgrade can/will break your desktop. I've had it happen recently in a fresh install of Manjaro Gnome where after the update my start button and settings button disappeared from the menu.  I've had other similar issues with MATE and Xfce where things will stop working or go missing(bluetooth icon in the panel for example) but for the most part I'd say that as far as the base operating system goes things work pretty well. There is better support for the Broadcom wifi cards now and an easy fix is to simply spend $5-$10 bucks and get an Intel card and the problem is solved once and for all. 
 Games are not as much of an issue anymore either because of Steam and Valve as a lot of games that run under Linux now.
 I've actually had more issues with Windows when I ran it because it takes up a tone of hard drive space, needs lots of ram for the desktop and is virus/malware prone more so then either OS-X or Linux so I'd say Windows is at the bottom of the list IMHO.

---

### Post by buzzingrobot on 2016-03-17
He's been updating this annually for a number of years, and it keeps being re-discovered.

I think his criticisms are usually valid, but the references he uses to substantiate his assertions are often old.

Personally, I don't think it's valid to talk about the "Linux desktop" because no such thing really exists, What does exist?  A variety of desktop environments built on a smaller variety of not-very-compatible tool sets, delivered to  users via hundreds of distributions, most of which are repackagings of a few major distribution.

In other words, while we have a Gnome desktop, or a Unity desktop, or a KDE desktop, etc., no "Linux" desktop exists.

Elsewhere, in OS X, Windows, iOS, and Android, we see *single *interfaces on each platform.  Ultimately, nothing gets out the door unless the CEO signs off.

Consistency, polish, etc. are easier to deliver when everyone is focused on a single approach. (In the case of OS X, that approach is well over 10 years old.)

No one's in charge like that in Linux. Because it's not a single product stovepiped by a single vendor, there's no CEO, no managers, who can say, "Do that, but not this." and enforce that decision across all of Linux.

---

### Post by HermanAB on 2016-03-17
Simple really:  If you want a polished Linux Desktop, use KDE and if you want an unpolished one, use anything else.  It doesn't matter which distribution you choose, underneath, they are all the same.

---

### Post by montag dp on 2016-03-17
A lot of those are valid.  I've been playing with FreeBSD in a VM lately because it purportedly is better with some of those issues (stability, backwards compatibility, standardization) while being worse with many others (mainly hardware support: even on the best-supported hardware there are still big issues with things like battery usage, suspend/hibernate, wireless networks; also software support like Flash, playing media, etc.).  So alas, I think on the VM it will stay.  But it is intriguing to me nonetheless.

---

### Post by HermanAB on 2016-03-18
Well, I've been using my Linux engineering laptop exclusive for the past 5 years at work, because IT was unable to fix an Active Directory problem in my Windows Profile.    So, people who complain about Linux desktops are simply looking for an excuse while merrily ignoring all the cruft on Windows systems.

---

### Post by RichardET on 2016-03-25
> **buzzingrobot said:**
> He's been updating this annually for a number of years, and it keeps being re-discovered.

I think his criticisms are usually valid, but the references he uses to substantiate his assertions are often old.

Personally, I don't think it's valid to talk about the "Linux desktop" because no such thing really exists, What does exist?  A variety of desktop environments built on a smaller variety of not-very-compatible tool sets, delivered to  users via hundreds of distributions, most of which are repackagings of a few major distribution.

In other words, while we have a Gnome desktop, or a Unity desktop, or a KDE desktop, etc., no "Linux" desktop exists.

Elsewhere, in OS X, Windows, iOS, and Android, we see *single *interfaces on each platform.  Ultimately, nothing gets out the door unless the CEO signs off.

Consistency, polish, etc. are easier to deliver when everyone is focused on a single approach. (In the case of OS X, that approach is well over 10 years old.)

No one's in charge like that in Linux. Because it's not a single product stovepiped by a single vendor, there's no CEO, no managers, who can say, "Do that, but not this." and enforce that decision across all of Linux.

You consistently have one of the more intelligent posts within any thread.  +10

---

### Post by Geoffrey_Arndt on 2016-03-25
Ditto for BuzzingRobot post . . .  a +++.

Regarding the constructive critique - - - one of the pluses to the Linux ecosphere is the freedom from the "Steve Ballmer" mentalities and methods of governance.  Standardization is good IF that standardization designed and managed by an Open Organization . . . (not private, closed companies).    That doesn't happen so much in the MS-Apple world.   And it shouldn't apply to all variations of a product or service, else you can kill innovation and creativity.

---

### Post by AllenGG on 2016-03-25
**Harsh but Fair !**  naw.    Most of those criticisms are out of date.   Personally I got tired of repairing friends Window's systems, A problem a day.
And of course, there is no "Linux Desktop"
The complainers and usual lazy suspects would be safer with Linux Mint.  A little more trouble free, perhaps not as innovative.
New recommendations, now I suggest that the average user would be better off with Apple.  Many critics are pointing out that Linux is NOT for the average user.
Apparently, we're a buch of geeks.

Allen
[IMG]http://ubuntuforums.org/images/icons/icon6.png[/IMG]

---

### Post by neu5eeCh on 2016-03-25
This website has been referenced elsewhere at Ubuntuforums. 

Being that almost all of the critiques are above my pay scale, all I can do is to say: *Okay, if you say you.*

That said: My entire family runs Linux (and one Chromebook). We wouldn't use it if it weren't reliable, stable and useful. Windows 10 only gets fired up for taxes. Linux has problems but Linux is **_fun_**. First of all, there are dozens of desktop environments to try -- something for everyone. It's a playground for the distro-hopper and the dream of any tweaker and tinkerer. Anyone can go as deep with a Linux Distro as they want. Windows and Apple can't touch it in that respect. They're not even on the same planet. They're a gateway to something else, and that's it. Their OS is theirs and not yours. Period.  So yeah, I'd say. Linux has some real limitations (hibernate will never work -- ever), but the trade-off is freedom for the just-plain curious. I'll take the latter.

---

### Post by mikodo on 2016-03-26
Oh the heck with that. I've seen it before. I didn't read a word of it this time.

You all know my story. Started with Vista, broke it within 6 months running admin rights with a worm and had no idea what to do. Started with Ubuntu and broke it waaay too many times to remember. At one point, I thought I would get everything running to my liking and then coast and do what I bought the computer for in the first place. Oops! That's right. The computer sat in its' boxes for 6 months because of unforeseen circumstances that precipitated the end of that "back to school plan", I bought it for. Along the way I, like VTPoet above me, started looking at this Linux thing more as a hobby. Not a tool to reach an end. I can't imagine trying to do that in Windows. What would I be doing with it? I dunno. I'm pretty sure I wouldn't have the options to tinker with that, I have now. I guess I'll keep chasing the next project to learn until senile dementia sets in.:)

---

### Post by Welly Wu on 2016-03-27
Linux is in varying stages of being broken and not very usable because it's more of an experiment than a finished product. It's for people like us that are willing to stick with it and overlook some of its flaws. My experience is quite similar using Windows and various Linux distributions over the past few decades. It would not make much of a difference to me at this point if I were to use either one or dual-boot on my desktop or laptop. While Macs have their appeal and fan base, I just don't consider them to be suitable for me especially when it comes to PC gaming which is limited by very high prices for mid range or old AMD or nVidia GPUs that do not get refreshed frequently over a few generations.

I only recommend Linux to others that can't afford to buy a new Windows PC or those that have had enough of Microsoft for some personal reason and they don't want to pay Apple for their very expensive Macs. Linux has been the least problematic for non-computer people that view it as a tool to get a limited set of things done for a short period of time. It's only the geeks and nerds that realize its shortcomings and are willing to work through them that care about these points of which some are somewhat valid. None of my friends that use Ubuntu pester me with telephone calls or e-mail messages about problems any longer. Right now, one of my friends recently complained that his Windows 7 desktop suddenly upgraded to Windows 10 without his permission. Now, he is upset and he wants to go back to Windows 7.

The biggest problem that Linux faces is that most computer users don't want to change their desktop operating system or upgrade it over time. Ubuntu like many other distributions regularly deprecates older software packages, libraries, and dependencies and it is like a moving target that is difficult to manage over a long period of time if the end user is not ready to accept important changes under the hood. It requires a level of curiosity and commitment that are becoming extinct because more people view computers as disposable devices that wind up getting handed down or recycled.

I can't hand off a Linux computer to more friends because they don't know much about it and they rather deal with the devil that they already know and they have come to love and hate at the same time. This is especially true of older computer users that don't want to abandon Mac or Windows because their jobs require it or they have become locked into specific software applications that they think that they can't replace or don't know where to go about looking for alternatives.

One of the biggest changes that comes with the territory when using GNU/Linux or BSD UNIX is that almost each distinct software package has a singular feature or capability. Before I purchased JRiver Media Center 21, I had to install and use Banshee, Rhythmbox, Tomahawk, VLC, Totem, and MPlayer along with Shotwell just to manage my enormous private media library. Apple and Microsoft customers expect a few software applications or products to handle a wider range of features set or capabilities some of which charge a lot of money for the privilege to be able to consolidate them together. It becomes an enormous burden for new Linux users that are already accustomed to the Apple or Microsoft way of using their computers to learn how to use Linux to perform similar tasks using a myriad of free, libre, open source software packages and tools built in for free of charge. The burden that shift in mindset entails is a major put off that seems to be a big waste of time for the advantage of saving money in the end. Not everybody is willing to dedicate the time it takes to learn Linux and its peculiar way of handling common tasks and some people do not care about FOSS philosophy if it means that they have to invest a significant portion of their work or family time.

---

### Post by nmw01223 on 2016-03-27
I think it depends what you are looking for. Pretty much everything he said is valid in concept, and it really summarises why Linux could never have knocked Windows out of the mainstream desktop market (quite apart from the fact it missed the boat timewise).

Linux is a loose confederacy without commercial focus. Say what you like about Microsoft, the one thing they do have is commercial focus. So has Google actually, which is why Android succeeds on phones and tablets.

It is good for people who - professionally or as a hobby - like to or are prepared to mess around with software. Most people don't, they just want a tool to do a job. As an example I have a MythBuntu based PVR, which works very well most of the time after a lot of effort to get it to go. Made the mistake a few weeks ago of doing a full distribution upgrade, and it was totally trashed. However I keep backups and one way or another I sorted it out. Most people won't do that - they'd throw their hands up, dump it and move to something else.

I'm a retired professional s/w developer (not Linux), and I must admit it drives me up the wall at times - but I put up with it because I knew what I was getting into, and given that, there are then strong positives.

So it's horses for courses. It is what it is and it is not for the masses, and it never will be, it is not in it's DNA.

---

### Post by mastablasta on 2016-03-29
It is important to note that the writer talks about desktop. it's an OS developed form server to be working on desktop.

1. **No stability, bugs, regressions, regressions and regressions** - there is if one uses a stable version. they are tested for longer period of time and there is actually QA on them. still less of it than on windows. less users, less testers, less money...

2. **Hardware issues** - manufacturer issues. then again many hardware actually does work. not always to it's full potential though. again a manufacturers issue. what is the Linux community to do about it? hold them hostage until they write good drivers?

3. **The lack of standardization, fragmentation, unwarranted & excessive variety, as well as no common direction or vision among different distro **- is this a weakness or strength? some distros are oriented towards servers, others toward routers (now these are not "Linux desktops"), some towards security, others towards privacy... in other words this can be a weakness but also strength. there is no windows designed with privacy in mind that I would know of. hardened widnows kernels? never heard of them on desktops. pentesting windows distro would be a laugh as it can probably be penetrated during testing. plus a user of specialized distro has different needs than "normal" desktop user. they might not need fancy desktop features or applications and are fine with i3 or openbox. furthermore see how this affected Android.

4. **The lack of cooperation between open source developers and internal wars **- not really wars. just difference of opinion. if you don't like it create your own. which could be said for drivers - if you don't like the situation create your own drivers.

5. **I don't understand** - does the writer want stability or bleeding edge where apps are full of bugs? how would users react to bleeding edge windows kernel? and what about bleeding edge windows drivers like the ones from nvidia that caused windows reboot loop.

6. U**nstable APIs/ABIs & the lack of real compatibility **- the only real issue here. but mitigated by containers, virtualisation...

7. **Software issues** - is MS Office compatible with Libre office? not really. why are they not fully compatible with open standards? Games - yes they are made for Windows. this is not a Linux issue as the OS supports them. this is a market issue. unless there is an easy to use, cross platform game making tool available it will be hard to break the monopoly. 

8. **Money, enthusiasm, motivation and responsibility** - RedHat became 2 bn $ company. I would say a good motivation for those that are in it for the funds.

---

### Post by kevdog on 2016-03-29
> **HermanAB said:**
> Simple really:  If you want a polished Linux Desktop, use KDE and if you want an unpolished one, use anything else.  
Hmmm just thinking out loud here -- since when once Plasma 5 a polished experience?  It's not a bad experience however it just seems plain buggy and bloated for the most part.

---

### Post by help_me2 on 2016-03-29
I disagree with the stability part. Linux has been near perfect for me since '07. I used to have a lot more issues with windows. On top of that, I really don't care what anyone else thinks. Linux works *for me*.

---

### Post by help_me2 on 2016-03-29
> **kevdog said:**
> Hmmm just thinking out loud here -- since when once Plasma 5 a polished experience?  It's not a bad experience however it just seems plain buggy and bloated for the most part.
I was just thinking the same thing. Not saying KDE is horrible, but every time I try it, I wind up uninstalling it. It has always been a buggy mess for me. Some people might not like Unity, but at least it's stable.

And believe me, every time I install KDE I cross my fingers hoping it works well, because I really want to use it and like it. But it *always* disappoints. I think Mandriva '08 was the last KDE distro I tried that was fairly solid.

---

### Post by montag dp on 2016-03-29
> **help_me2 said:**
> I was just thinking the same thing. Not saying KDE is horrible, but every time I try it, I wind up uninstalling it. It has always been a buggy mess for me. Some people might not like Unity, but at least it's stable.

And believe me, every time I install KDE I cross my fingers hoping it works well, because I really want to use it and like it. But it *always* disappoints. I think Mandriva '08 was the last KDE distro I tried that was fairly solid.KDE 4 is pretty solid for me.  I don't have any crashes or glitches or anything like that.  KDE 5 is still under heavy development, but will probably be a lot less buggy once it matures some more.  Anyway, by polished I'm guessing he meant visual polish, because it does have that.

---

### Post by mastablasta on 2016-03-30
KDE 4 is now at 14 or 15th iteration. it sure is not buggy. KDE 5 is basically still kind of in beta.

stable in these projects would often mean not changing or frozen state where only bugs are fixed and security patches made. the longer it is in such state the less bugs software has. which is why Debian or RedHat/CentOS is so "stable" when it reaches later iterations. software there is just frozen for so long that they had time to remove most of the big bugs. I am more bothered here by the "wontfix bugs" because supposedly next version has the fix. but you are not supposed to use the next version.

now in windows we actually do not receive cutting edge kernels or other things as the creator of article might think. not in OS. if we did everyone would get the experience that was similar to preview version. and even preview was tested before released. while in Linux users have to test it.

---

### Post by rudihawk on 2016-03-30
> **help_me2 said:**
> I disagree with the stability part. Linux has been near perfect for me since '07. I used to have a lot more issues with windows. On top of that, I really don't care what anyone else thinks. Linux works *for me*.

Same here, been using Ubuntu since 6.06 and haven't looked back.

---

### Post by paeschli on 2016-11-10
I agree that the fun is over.

No one cares about Ubuntu anymore [https://www.google.be/trends/explore?date=all&q=%2Fm%2F03x5qm](https://www.google.be/trends/explore?date=all&q=%2Fm%2F03x5qm)

---

### Post by QIII on 2016-11-10
Your data does not support your conclusion.

In the time frame covered, what is the level of interest in Linux in general and other distros specifically?  Linux was "new" to many people before Ubuntu.

Furthermore, your source does not reveal its source or methodology and the various flavors of Ubuntu are separated.

Your source represents "fun with stats".

---

### Post by 7dEfOk4AgU on 2016-11-10
The stats mean nothing to me. I install or deploy what the customer wants after all the preliminary investigations and POC's. It does not matter to me if it is Windows, MacOS, or a Linux Distribution. Stats only matter to statisticians. Of course for my own computing things are a little different.

---

### Post by bearlake on 2016-11-10
I've been a Linux user for 10 years now.

Having a open mind and choices are all we need.

Certainly don't need polls.

---

### Post by RichardET on 2016-11-10
Ubuntu Mate 16.04 is very good, on a 4 month old Dell Desktop, ~$300 in cost, very good.  Why this constant diss of Linux by some individuals??

---

### Post by LT1Caprice57L on 2016-11-11
I have issues in Linux, but I also have issues on Windows.

Dell Precision M6500, on Ubuntu MATE 16.04, it won't resume from suspend, and sometimes the sound is entirely too low despite being at max volume.  Seems to be when I restart into Ubuntu after running Windows, and persists until I shut down the computer and turn it back on.  Once I do that, sound in Ubuntu returns to normal.

But I also have issues in Windows 7.  Sometimes I boot up and the touchpad driver doesn't function properly, and I lose all my settings for it.  And even when it does 'function properly' things like two-finger scrolling are horribly erratic and sometimes don't work at all.  Dell has released no driver updates for it.  This actually makes Ubuntu less frustrating to use than Windows.

Ubuntu ran just about perfectly on my Latitude E6510, but that computer itself has had too many problems, unlrelated to the OS, and so I've retired it.  Like any computer I buy, it was used, and some idiot had worked on it at one point and left a screw floating around inside.  Before I bought my chill pad, I would turn the laptop upside down when closing the lid but not shutting down or suspending so it didn't overheat.  Enough times of doing that worked the screw over to something important, she went 'snap, crackle & pop' and that was it.  Ordered a new motherboard, put it in, solder joint issue, pressing even lightly on a certain part of the case causes a lock-up.  Threw my hands up in the air, gave up, and ordered the M6500.

---

### Post by silverslimer on 2017-08-26
My biggest criticism with Linux has to do with the remarkably bad performance for most games within Linux. Those made by Valve run better within Linux, but anything else which exists on both platforms is 2x to 4x smoother on Windows.

---

### Post by ChuangTzu on 2017-09-01
> **silverslimer said:**
> My biggest criticism with Linux has to do with the remarkably bad performance for most games within Linux. Those made by Valve run better within Linux, but anything else which exists on both platforms is 2x to 4x smoother on Windows.

Linux was created for far greater purposes then entertainment, while it can handle that task as well.

---

### Post by JonPaul on 2017-09-02
I have a Microsoft Wireless desktop 700 (Yes Microsoft) on a dual boot Windows 10 and Ubuntu 17.10. 

In windows 10 I have to reinstall the drivers every time I use it. On Ubuntu it just works - go figure!

Also, my Windows 10 suddenly wouldn't install any updates. I tried every solution on every forum I could find before having to completely reinstall which took hours. 

I use windows once a week for one package only because I have to. Ubuntu works just fine for me the rest of the time and it's a helluva lot more fun.

---

### Post by SunnyDaze on 2017-09-02
Hardware issues?  Why do people expect Linux to run on machines built for Windows.  It makes no sense.  If you want to run an OS, you buy hardware for that OS.  I never buy hardware unless it has good Linux support.  My laptop ran Ubuntu from the factory, and it is was one of the most powerful laptops you could buy at the time.  (Dell Precision M4600)  So the hardware issues aren't nearly as severe as he makes them out to be.

Linux desktop still spins circles around MS Windows when it comes to efficiency, especially if you are running Compiz, and taking advantage of many of it's plug-ins.

These are just a few of the many, many things the Linux desktop does better than MS:
1.  Mouse focus follows the mouse pointer.  No need to click to get window focus with the mouse pointer
2.  You can set any window to "Always on top"
3.  You can easily make a window go semi-transparent by holding down Alt and the scrolling the mouse button up or down. (Compiz plug-in)  This feature
4.  Multiple desktops have been a part of Linux since decades ago
5.  You can "aero-snap" windows 9 different ways on each monitor,as well as at the edges between multi-monitors.  4 quarter-screen options, 4 half-screen options, and full-screen, either by dragging the window to an edge or corner, or by holding down CTRL+ALT and hitting a number on the number pad.  (Compiz plug-in)
  
He points out that LibreOffice doesn't draw Microsoft Office documents "properly,"  but he fails to point out that Microsoft Office doesn't even open a LibreOffice document.  I don't accept the premise that the Linux vs. Windows is to be viewed only form a Windows perspective.  Besides, the rendering issue is solved by installing the latest MS fonts on your system.  The only way to get a document to render properly across all platforms is to export it to pdf, which OpenOffice/LibreOffice did long before Microsoft Office ever came around to reasonable.

---

### Post by poorguy on 2017-09-03
It is ***imperative*** for a ***new Linux user*** to learn some basic things about*** what Linux is*** and*** how Linux works*** and ***what hardware Linux supports*** to have a*** successful first experience***.
Most new Linux converts are*** unwilling*** to take these few minor steps in learning.

This of course is my own observation from trying to help some new Linux users.

I have tried several different Linux distros before finding the Linux distros that suit my computers and hardware for what I need to accomplish using my computers.
I have also experienced my share of problems with Linux although through help from the Linux forums were able to find solutions to most problems I have experienced.

The PoorGuy :D

---

### Post by lammert-nijhof on 2017-09-03
I have no complaints about the stability or Linux or Ubuntu, I use it as my main system since my retirement on Jan 2011. I also have no complaints from people, I helped to install Ubuntu, they keep on using it. It always works and it always recognizes the HW. To be honest I use ex-lease machines from Dell or HP, but also e.g. the PCIe cards I buy always work. Since April 2017 I moved my main distro to a Virtual Machine and basically I only use a stripped version of Ubuntu as my Host OS. 

In a Vbox environment almost none of the distros have driver issues. All my exception are related to the 3D support for Virtualbox. Ubuntu 16.04 writes the updates to my screen and  rewrites that same update half a second later.  Simple typing in Gedit becomes a disaster. Ubuntu Gnome 17.04 did not boot with 3D support enabled. Probably Oracle and Virtualbox are to blame for the rewrite and Ubuntu Gnome for the boot issue. Given the ongoing redesign of the graphical stack, I should not complain too much and switch off 3D support for the moment and look 3D videos using my host OS. 

For those 3D videos Mozilla Firefox beats Google Chrome nowadays hands down on my older hardware. So open source software can beat commercial software.

---

### Post by mastablasta on 2017-09-04
> **lammert-nijhof said:**
>  

For those 3D videos Mozilla Firefox beats Google Chrome nowadays hands down on my older hardware. So open source software can beat commercial software.

[CENTER][COLOR=#000000]:confused:

[/COLOR][/CENTER]google chrome is based on chromium which is opensource. Chrome is Chromium with some Google branding added and perhaps a few changes (e.g. pepper flash added).

---

