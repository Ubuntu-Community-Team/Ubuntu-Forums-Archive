---
title: "Is LTS Really LTS?"
date: 2016-04-25
forum: Ubuntu, Linux and OS Chat
---

### Post by TheFu on 2016-04-25
Only the core repos get LTS.  Very few people will only use the core repos and it appears **any** desktop doesn't get LTS for everything. 

How bad is it on your system(s)?  Run ```

$ ubuntu-support-status --show-unsupported|more
```
to see.

On my primary 14.04 desktop, these were the results:
```
You have 1679 packages (68.8%) supported until May 2019 (5y)
You have 12 packages (0.5%) supported until January 2017 (9m)
You have 148 packages (6.1%) supported until May 2017 (3y)
**You have 196 packages (8.0%) supported until February 2015 (9m)**

You have 101 packages (4.1%) that can not/no-longer be downloaded
You have 304 packages (12.5%) that are unsupported

```
So almost 200 packages haven't been supported since Feb last year!  Some are scary. Some are not-so-scary.
Checked 15 of my Ubuntu LTS Servers too - similar issues.  I need to rethink my LTS beliefs.  One of the most concerning issues is that the backup solution I use has lost support on Ubuntu 14.04 (Feb '15). Funny thing is that the exact same version of that package is part of debian Wheezy and still listed as "supported."
[B]
Is this just a reporting issue?[/B]

I only use LTS releases. Seems that LTS isn't always LTS, at least for me.

---

### Post by vasa1 on 2016-04-25
Someone else has been going on about something similar here: [http://www.wilderssecurity.com/threads/ubuntu-lts-many-vulnerabilities-despite-long-term-support.385386/](http://www.wilderssecurity.com/threads/ubuntu-lts-many-vulnerabilities-despite-long-term-support.385386/)

---

### Post by Bucky Ball on 2016-04-25
*Thread move to **Ubuntu, Linux and OS Chat**.*

Interesting, and even more so on an install of 16.04 LTS:

```
$ ubuntu-support-status --show-unsupported|more
Support status summary of 'Studio':

You have 132 packages (7.8%) supported until April 2019 (3y)
You have 1364 packages (80.1%) supported until April 2021 (5y)
You have 76 packages (4.5%) supported until January 2017 (9m)

You have 30 packages (1.8%) that can not/no-longer be downloaded
You have 100 packages (5.9%) that are unsupported

No longer downloadable:
fonts-droid libbind9-90 libdns-export100 libdns100 libgee2 
libgnutls-deb0-28 libirs-export91 libisc-export95 libisc95 libisccc90 
libisccfg-export90 libisccfg90 liblouis2 liblwres90 libpoppler57 
libusbmuxd2 libvpx2 libxtables10 linux-headers-4.4.0-11 
linux-headers-4.4.0-11-generic linux-headers-4.4.0-17 
linux-headers-4.4.0-17-generic linux-image-4.4.0-11-generic 
linux-image-4.4.0-17-generic linux-image-extra-4.4.0-11-generic 
linux-image-extra-4.4.0-17-generic 
linux-signed-image-4.4.0-11-generic 
linux-signed-image-4.4.0-17-generic python-gtkspell 
ttf-indic-fonts-core 

Unsupported: 
antiword arandr exfat-fuse exfat-utils filezilla filezilla-common 
genometools genometools-common libalgorithm-c3-perl 
libarchive-extract-perl libb-hooks-endofscope-perl 
libb-hooks-op-check-perl libbareword-filehandles-perl 
libclass-c3-perl libclass-c3-xs-perl libclass-method-modifiers-perl 
libclass-xsaccessor-perl libcpan-changes-perl libcpan-meta-perl 
libcublas7.5 libcudart7.5 libcufft7.5 libcufftw7.5 libcuinj64-7.5 
libcurand7.5 libcusolver7.5 libcusparse7.5 libdata-optlist-perl 
libdata-perl-perl libdata-section-perl libdevel-caller-perl 
libdevel-globaldestruction-perl libdevel-lexalias-perl libfilezilla0 
libgetopt-long-descriptive-perl libimport-into-perl libindirect-perl 
liblexical-sealrequirehints-perl liblog-message-perl 
liblog-message-simple-perl liblouis-bin libmodule-build-perl 
libmodule-pluggable-perl libmodule-signature-perl libmoo-perl 
libmoox-handlesvia-perl libmro-compat-perl libmultidimensional-perl 
libnamespace-autoclean-perl libnamespace-clean-perl libnppc7.5 
libnppi7.5 libnpps7.5 libnvblas7.5 libnvrtc7.5 libnvtoolsext1 
libnvvm3 libpackage-constants-perl libpadwalker-perl 
libpath-tiny-perl libpod-latex-perl libpod-markdown-perl 
libpod-readme-perl libpth20 librole-tiny-perl 
libsoftware-license-perl libstrictures-perl libsub-exporter-perl 
libsub-exporter-progressive-perl libsub-identify-perl libterm-ui-perl 
libtext-soundex-perl libtext-template-perl libthrust-dev libtre5 
libtype-tiny-perl libtype-tiny-xs-perl libunicode-utf8-perl 
libvariable-magic-perl libvdpau-va-gl1 libxine2 libxine2-bin 
libxine2-doc libxine2-ffmpeg libxine2-misc-plugins libxine2-plugins 
libxine2-x lua-md5 me-tv nvidia-cuda-dev nvidia-cuda-doc 
nvidia-cuda-gdb nvidia-cuda-toolkit nvidia-modprobe nvidia-opencl-dev 
nvidia-profiler nvidia-visual-profiler ooo2dbk xarchiver zim
```

Bit of a worry, and also a bit confusing as I have Filezilla and arandr installed and they are on the unsupported list (yet still in Synaptic). :-k

I'm sure there's an explanation ... well, I imagine there's one!

(PS: Ninja-ed by vasa1! I'll check that link.)

---

### Post by QIII on 2016-04-25
Surely there is an explanation.

But I fear I will have to be wearing hip waders if anyone from Canonical happens to provide it ...

:)

Honestly, it could be very simple and straight forward:  maybe replacements are just not available yet and we'll get them as updates?

---

### Post by nothingspecial on 2016-04-25
It's quite clear, if you use the packages packaged with the LTS and from the main repos it is LTS, go elsewhere and it's not.

From [https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

> 
We start stabilizing the release early by significantly limiting the number of new features. We will choose which features we package into the LTS release, versus which ones we leave out and allow for users to optionally download and use from a separate archive.

Avoid structural changes as far as possible, such as changing the default set of applications, lots of library transitions, or system layer changes (example: introducing KMS or hal &#8594; DeviceKit would not have been appropriate changes in a LTS). 

> We start stabilizing the release early by significantly limiting the number of new features. We will choose which features we package into the LTS release, versus which ones we leave out and allow for users to optionally download and use from a separate archive. 

> We will focus on hardening functionality of existing features, versus introducing new ones1, except for in the areas of Online Services and Desktop Experience

I suppose the confusion is enabling the uni/mutiverse repos by default.

---

### Post by mikodo on 2016-04-25
Yes. I have wondered about that too.

I wonder what if any, will be the future 'buntu solution. Snap updates, for updates updating them on the OS's, and users using Debian and debs when needed.

---

### Post by grahammechanical on 2016-04-25
Define "support." This is what Canonical means most of the time. See the charts at the bottom of the page.

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Compare what you are thinking now with Canonical's publicity about snap packaging and its advantages to developers and to users. The definition of a support term will come to mean "as long as a developer pushes out an upgraded version into the app store." A Ubuntu distribution built on snappy Ubuntu core will no longer have new releases. Just upgrades to the kernel snap & the OS snap. Like OTA upgrades on the phone.

Regards.

---

### Post by QIII on 2016-04-25
I hadn't thought about it from nothingspecial's point of view, but I think that is probably spot on.  Anything outside of Main is maintained outside of Canonical's canon ( :) ) and packaged/presented by a MOTU.

Neither Canonical nor their MOTUs can support what others develop/maintain.  They only make the stuff available.

---

### Post by TheFu on 2016-04-25
"universe" repo = "unsupported"?  That's my only guess.
After all, canonical can't possibly patch everything ... but a refresh every month or quarter from Debian-stable for newer packages would be nice.  Suspect that most of the updates could be automated, with just a few packages need minor manual handling and a few more needing to be dropped.

OTOH, I know ZERO about packaging.

---

### Post by montag dp on 2016-04-25
> **TheFu said:**
> "universe" repo = "unsupported"?  That's my only guess.
After all, canonical can't possibly patch everything ... but a refresh every month or quarter from Debian-stable for newer packages would be nice.  Suspect that most of the updates could be automated, with just a few packages need minor manual handling and a few more needing to be dropped.

OTOH, I know ZERO about packaging.The packages couldn't just be taken directly from Debian-stable, if that's what you mean.  They would have to be recompiled against the Ubuntu LTS libraries, and the metadata updated.  However, it could be a time saver in the sense of knowing which packages need to be updated.

---

### Post by mc4man on 2016-04-25
> **QIII said:**
> I hadn't thought about it from nothingspecial's point of view, but I think that is probably spot on.  Anything outside of Main is maintained outside of Canonical's canon ( :) ) and packaged/presented by a MOTU.

Neither Canonical nor their MOTUs can support what others develop/maintain.  They only make the stuff available.
That's pretty much it, if you use synaptic then packages with the ubuntu icon are supported, the rest aren't. Some called unsupported may occasionally get a security update though certainly not guaranteed.

As far as snap - my impression is any snap not part of the core is unsupported from day 1. That could be  the whole point, Canonical bears no real responsibility other than some simple look see's when adding/building. No different than apple, google, windows, samsung, sony's  stores. They just put them out, collect their share & on occasion pull if there are reports.

---

### Post by sudodus on 2016-04-25
'Not supported' means 'not supported by Canonical' in this case. Many program packages are well supported by other people or organisations. Canonical cannot promise anything about them. You can use them anyway, but when you use such packages, it means that you trust 'other people or organisations'.

If you need very high security you should have a separate computer with no (or very few carefully selected) extra packages (except those packed with Ubuntu).

---

### Post by howefield on 2016-04-25
An interesting thread in the developer mailing list just started..

[URL="https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2016-April/016476.html"]
Support status of nginx in Ubuntu 14.04LTS expired in Feburary 2015?[/URL]

---

### Post by QIII on 2016-04-25
So....  Does that mean that those of us running LEMP servers exposed to the web are in a vulnerable state if we are using nginx from the repo?

Not a good thing if so...

---

### Post by buzzingrobot on 2016-04-25
Well, the wiki says "Universe" is "Community maintained software, i.e. not officially supported software". 

My assumption has always been that "support" in any given distribution means passing along upstream patches. Exceptions would include obvious things like Unity and Compiz in Ubuntu, patched kernels from Canonical, Fedora, Red Hat, etc., Cinnamon on Mint, etc.

---

### Post by QDR06VV9 on 2016-04-25
> **QIII said:**
> So....  Does that mean that those of us running LEMP servers exposed to the web are in a vulnerable state if we are using nginx from the repo?

Not a good thing if so...
I have been doing a lot of asking some old friends and came up this.
[https://news.ycombinator.com/item?id=11541017](https://news.ycombinator.com/item?id=11541017)

> If you're running a HTTP/2 server like NGINX on the 14.04 LTS you'll want to upgrade to this release.

Google Chrome will no longer support HTTP/2 on vanilla 14.04 after May 15th [0], even if you're using the latest official upstream NGINX packages. This is because 14.04 ships with a version of OpenSSL that does not support the ALPN extension (prior to OpenSSL 1.0.2 you're limited to NPN, now deprecated). There was a bit of back-and-forth about the exact date, as the change was originally scheduled for earlier. However, Chrome decided to specifically push back the date so that there would be an Ubuntu LTS release available with the required support [1]. If you're still stuck on SPDY, that's going to be dropped too, so there's really no good reason not to simply use HTTP/2 at this point.

Hope this is useful.
And I hope everyone has seen this by now.
> Short answer: don't use ubuntu-support-status, it doesn't work.

Long answer: ubuntu-support-status is a deprecated tool that used to be used
when we had a 3y/5y split on desktop and server packages. It returns the
contents of the "Supported:" tag which hasn't been updated since Ubuntu 10.04
LTS. I've filed a bug to get it removed:
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1574670](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1574670)

Marc.

---

### Post by poorguy on 2016-04-25
Perhaps I'm wrong here but none of this seemed to be a concern until the release of 16.04 and now it seems to be a big concern. 
I wasn't aware that any of the packages installed in my 14.04 were unsupported and hadn't been supported for awhile until I had checked prior to the release of 16.04. 
Isn't this what the maintenance updates and release points are for to update unsupported packages within the supported cycle of a distro.
Until I found out that I had unsupported packages in use I had no concern and now that I know it hasn't stopped me from using them.
So how big of a threat can the unsupported packages be as long as we are still receiving supported security updates.

---

### Post by buzzingrobot on 2016-04-26
> **poorguy said:**
> Perhaps I'm wrong here but none of this seemed to be a concern until the release of 16.04 and now it seems to be a big concern. 
I wasn't aware that any of the packages installed in my 14.04 were unsupported and hadn't been supported for awhile until I had checked prior to the release of 16.04. 
Isn't this what the maintenance updates and release points are for to update unsupported packages within the supported cycle of a distro.
Until I found out that I had unsupported packages in use I had no concern and now that I know it hasn't stopped me from using them.
So how big of a threat can the unsupported packages be as long as we are still receiving supported security updates.

Packages in Main and Restricted are "Canonical supported".  As I understand it, that means Canonical is paying people to monitor upstream activity in the packages in those repos and ensure fixes get into updated packages. For its own unique packages -- Unity, etc. -- Canonical itself is the upstream.

Packages in Universe are "community supported" and that means volunteer efforts. I.e., best effort (we hope) but no guarantee.  First, someone has to be responsible for creating fixes for a package:  The upstream.  Then, someone else has to be responsible for monitoring that, applying a fix to the package in Universe, testing it, and packaging it for release as an update.  

Rolling releases approach this issue by simply passing along changes from upstream as they happen.  That mean users get security fixes plus new code that adds new features and also the potential for new bugs. And, of course, they are just as dependent on someone else -- upstream -- to produce the fixes in the first place.

Distributions like Red Hat provide 10-plus years of support and accomplish that by freezing package versions at release (no new features), with few exceptions, and then fixing security issues.  They do not have anything comparable to Universe, though.  When their users go to third-party sources for packages, then, they are typically relying on the same "community support".

That's the nature of "community support" across Linux.

---

### Post by poorguy on 2016-04-26
I'm have faith that as time progresses that any and all new changes will come eventually.

Thanks

---

### Post by TheFu on 2016-04-26
> **QIII said:**
> So....  Does that mean that those of us running LEMP servers exposed to the web are in a vulnerable state if we are using nginx from the repo?

Not a good thing if so...

One of the few PPAs that I use is the one for nginx. Some things are too important NOT to go directly to the source project to use. Plus being 6+ months behind on something like a web server or reverse proxy (nginx) makes it worth that extra effort to me.

Can't recall if I posted about rdiff-backup here or not, but I checked the "supported" version in Debian Wheezy - it is exactly the same as in Ubuntu 14.04, so ... is there risk  or not?  For that package, I'd say no, zero, nada.  Do I want to do the same research for the 300+ other packages listed in the "unsupported" output?  Maybe not.  

Perhaps a difference report is needed?  "Canonical supported" vs "Upstream Supported" (PPA/alternate repo) vs "non-supported" (.deb file install)?  I dunno - just riffing here.  For example, if I manually install using autolib/configure; make; make install, I **know** that is not supported.  In the 1990s, we had to do that A-LOT because packaged versions for most software didn't exist at all.  It has gotten better and better and better and better year after year after year ... and will continue to get better, I'm certain.

At a minimum, perhaps this thread will get more volunteers to help with updating packages?  I'm tempted to help, but don't know enough about packaging to feel ready.

---

### Post by ChuangTzu on 2016-04-26
I always understood this as Canonical letting you know what they are responsible for, perhaps even liable for.  The rest fall under the usual Linux "upstream", which generally means, through the grapevine.  So, when a dev. updates a package, then Debian maintainer will patch the package in the repo and then it eventually is updated via Ubuntu as a security patch from upstream.  This is nothing new, RedHat does a similar thing, they quickly update "their programs" and the rest are patched upstream packages, openSUSE is similar as well.

---

### Post by mastablasta on 2016-04-27
in other words - just like windows. they update the OS, but any programs you installed... well they are not responsible for that or if OS get's breached thorugh them.

---

### Post by Konjad on 2016-04-28
Sounds reasonable. I think the way it is done now is satisfactory and doesn't really need an improvement.

---

### Post by poorguy on 2016-04-28
Would there be any advantage to go to the software manufactures site and check for the latest version of whatever software you were wanting to download.

---

### Post by pauljw on 2016-04-28
> **poorguy said:**
> Would there be any advantage to go to the software manufactures site and check for the latest version of whatever software you were wanting to download.

This line of thinking, though possibly valid in some rare instance, will lead to broken installs.  The latest greatest software releases are not necessarily going to play nice with your installed OS.  By going outside the repo, you risk your systems stability.  Trust the packagers.  JMHO

Paul

---

### Post by poorguy on 2016-04-28
> **pauljw said:**
> This line of thinking, though possibly valid in some rare instance, will lead to broken installs.  The latest greatest software releases are not necessarily going to play nice with your installed OS.  By going outside the repo, you risk your systems stability.  Trust the packagers.  JMHO

Paul

That makes sense.

---

### Post by ChuangTzu on 2016-04-29
> **poorguy said:**
> Would there be any advantage to go to the software manufactures site and check for the latest version of whatever software you were wanting to download.  Depends on system and OS.  If you want latest and greatest then best to use a Distro that is designed for rolling release (Arch, openSUSE tumbleweed, Gentoo etc...), otherwise best to stick with repos provided.  You could try Debian Sid but that is not really rolling release more like rolling unstable.

---

### Post by poorguy on 2016-04-29
I actually have openSUSE tumbleweed installed on another computer. I like it and out of the box it runs well but trying to install anything can sometimes be a real PIB as it isn't very user friendly.
I liked debian wheezy until they went to jessie and the gnome 3 gui and I hate it.

Oh well I'll just stay with the Ubuntu based distros and hope everything that need to be fixed will be. Hopefully the unsupported packages get supported again and if not mark them as not supported.

---

### Post by ChuangTzu on 2016-04-29
You could:  upgrade to newest version of Ubuntu ever 6mo. rather than staying on LTS.    test making your own packages from source then install into a virtualbox Ubuntu for testing purposes and if all is good then install it on your main box.

---

### Post by vasa1 on 2016-04-29
> **runrickus said:**
> ...
And I hope everyone has seen this by now.> Short answer: don't use ubuntu-support-status, it doesn't work.

Long answer: ubuntu-support-status is a deprecated tool that used to be used
when we had a 3y/5y split on desktop and server packages. It returns the
contents of the "Supported:" tag which hasn't been updated since Ubuntu 10.04
LTS. I've filed a bug to get it removed:
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1574670](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1574670)
Marc. 

I think ^^^ deserves a thread of its own. I'll add something to my sig for now [s]but the bug @ launchpad has > his page does not exist, or you may not have permission to see it. I suspect it's the latter[/s].

---

### Post by poorguy on 2016-04-30
[IMG]http://ubuntuforums.org/images/ubuntu-VB4/misc/quote_icon.png[/IMG] Originally Posted by **runrickus**                     [[IMG]http://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG]]("http://ubuntuforums.org/showthread.php?p=13477345#post13477345")                 
                 ...
And I hope everyone has seen this by now.                                                         Short answer: don't use ubuntu-support-status, it doesn't work.

Long answer: ubuntu-support-status is a deprecated tool that used to be used
when we had a 3y/5y split on desktop and server packages. It returns the
contents of the "Supported:" tag which hasn't been updated since Ubuntu 10.04
LTS. I've filed a bug to get it removed:
[https://bugs.launchpad.net/ubuntu/+s...r/+bug/1574670](https://bugs.launchpad.net/ubuntu/+s...r/+bug/1574670)

Marc. 
-------------------------------------------------------------------------------------------------------------------                     


So if this is the case then can one say that the software packages in the "Software Boutique" are up to date and supported. How can one check to make sure.

---

### Post by montag dp on 2016-04-30
> **poorguy said:**
> [IMG]http://ubuntuforums.org/images/ubuntu-VB4/misc/quote_icon.png[/IMG] Originally Posted by **runrickus**                     [[IMG]http://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG]]("http://ubuntuforums.org/showthread.php?p=13477345#post13477345")                 
                 ...
And I hope everyone has seen this by now.                                                         Short answer: don't use ubuntu-support-status, it doesn't work.

Long answer: ubuntu-support-status is a deprecated tool that used to be used
when we had a 3y/5y split on desktop and server packages. It returns the
contents of the "Supported:" tag which hasn't been updated since Ubuntu 10.04
LTS. I've filed a bug to get it removed:
[https://bugs.launchpad.net/ubuntu/+s...r/+bug/1574670](https://bugs.launchpad.net/ubuntu/+s...r/+bug/1574670)

Marc. 
-------------------------------------------------------------------------------------------------------------------                     


So if this is the case then can one say that the software packages in the "Software Boutique" are up to date and supported. How can one check to make sure.

If you keep reading in the chain, the next guy disagrees with him about that point. So I don't know what the final determination is.

---

### Post by vasa1 on 2016-04-30
> **montag dp said:**
> If you keep reading in the chain, the next guy disagrees with him about that point. So I don't know what the final determination is.Could you please provide the link to the relevant comment?

---

### Post by howefield on 2016-04-30
> **vasa1 said:**
> Could you please provide the link to the relevant comment?

Already posted in this thread...

[http://ubuntuforums.org/showthread.php?t=2321959&page=2&p=13477238&viewfull=1#post13477238](http://ubuntuforums.org/showthread.php?t=2321959&page=2&p=13477238&viewfull=1#post13477238)

---

### Post by vasa1 on 2016-04-30
> **howefield said:**
> Already posted in this thread...

[http://ubuntuforums.org/showthread.php?t=2321959&page=2&p=13477238&viewfull=1#post13477238](http://ubuntuforums.org/showthread.php?t=2321959&page=2&p=13477238&viewfull=1#post13477238)

I'm not sure what montag dp meant by "If you keep reading in the chain, the next guy disagrees with him about that point. So I don't know what the final determination is."

It would be better to know what exactly "the chain" refers to. For example, I can counter with "Understood that it's not a regression.  I think the current implementation follows logically from the time when we had multiple products in main, via the same seed pod (ubuntu), with different support lengths.  **But it's surely an oversight that packages seeded in a seed called "supported-foo" are shown as not supported** by ubuntu-support-status!" And I'd follow that up with a link to the particular post; in this case that'd be [https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2016-April/016483.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2016-April/016483.html)

Also, the issue is about more than one package.

---

### Post by mikodo on 2016-04-30
Well, I hope the results of this will be a step towards addressing these issues(s):

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1574670](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1574670)

Interesting, when I ran
```
ubuntu-support-status --show-unsupported
```

The first two reported unsupported were the 2 PPA's I have. An example of how the tool should report *Community Supported* I guess.

But again, they are working on it and it is all in the open for all to read so, another example of how Open-Source addresses important issues, and works well!

---

