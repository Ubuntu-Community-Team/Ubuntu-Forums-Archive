---
title: "POLL: Is Grub2 worth the trouble vs old Grub?"
date: 2010-02-22
forum: The Cafe
---

### Post by gwilson on 2010-02-22
I hope the Cafe is an acceptable place to poll with a question like this. After a few minor excursions into editing menu.lst and its internal setting parameters, I found the old Grub to be very simple to work with and very easy to repair if I messed it up with bad settings. Personally, I like a simple bootloader and couldn't care less about splash screens or graphics during boot-up. I may be wrong, but I think Grub's sole function to simply point at the kernel and load the damn thing. With that in mind, here's the question:

In practical terms, is Grub2 an important step forward, or does it really only complicate what used to be done more simply by the old Grub?

---

### Post by undecim on 2010-02-22
Grub2 is a lot more flexible, but also a little more complicated.

Also, it's handled different in Ubuntu than grub. Now, you have config files that govern config files (metaconfigurations?) and scripts that set it all up for you. There is still a single file that grub actually looks at, but you're not actually supposed to edit it directly.

Though you can to lots more with it. I had it on a live thumb drive once with several distros with both 32 and 64 bit versions, and had each menu item select the approprate version for the computer.

But if you are still using grub just fine, I wouldn't upgrade to grub2 just yet. If it ain't broke, don't fix it.

---

### Post by bruno9779 on 2010-02-22
I like grub2.

It is just so much easier to set up multi-boot systems now.

"update-grub" works for real now, detecting and setting up boot menu entries, for pretty much any OS I have tried it on.

---

### Post by swoll1980 on 2010-02-22
I didn't know this and edited the menu.lst directly. What could go wrong?

---

### Post by dragos240 on 2010-02-22
Honestly, the only point I see in using grub2 is not having a 16 bit bootsplash, and plus, ubuntu doesn't even HAVE a bootsplash! Even gentoo has a bootsplash, it looks really good considering it's 16 bit. Grub legacy is a lot easier to navigate than grub2, more users know how to navigate it, it's just easy, grub 2 is hard, and plus, harder to recover if your MBR gets wiped. I love my grub 0.97, never leaving it.

---

### Post by jenaniston on 2010-02-22
As I understand it . . . grub2 is needed for ext4 filesystems . . . ?

There*** are*** "hackers" / developers that are using ext3 and legacy grub0.97 for their Karmic Koala 9.10 installs - 
I think that shouldn't be *too *hard - but it's just not mainstream newbie installs f'r sure.

I like your idea of a real choice and an option of choosing during installs - so yes . . . 
ext3/grub0.97 v. ext4/grub2 - I do prefer the former for now at least - so Jaunty.

---

### Post by Simian Man on 2010-02-22
> **jenaniston said:**
> As I understand it . . . grub2 is needed for ext4 filesystems . . . ?

Nope.  Legacy Grub has been patched to allow booting ext4 for a while now.

---

### Post by gnomeuser on 2010-02-22
Let's see a deprecated GNU project which is defacto unmaintained for years, then forked by every distribution to support required features.. or an overly complicated yet poorly designed GNU project which doesn't take into account requirements for modern features such as those needed supporting btrfs which has been years in the making without becoming stable.

It's like being asked which essential boy part I would prefer to have hit repeatedly with a hammer.

I believe it is time we consider if there might an option C.

---

### Post by gwilson on 2010-02-22
I'm surprised to read that Grub2 picked up all of you installations because that was the initial gripe I had. I have several different linux installations as well as XP and Win7 on a number of partitions. Sometime after the final release of 9.1, I did a clean install. I was surprised that it did not even Ubuntu-based systems like Mint 6. I finally ended up booting to an older partition that had the older Grub installed so that I could edit in all of the missing operating systems.

My ultimate resource in an emergency was putting my old Super Grub Disk into the drive and looking around. As far as I know, there's no such tool for Grub2. I don't mind learning a new Grub, but it isn't as easy going in and editing one menu.lst file (especially since Grub2 specifically tells you NOT to edit the file that really changes the boot options).

---

### Post by Eddie Wilson on 2010-02-22
> **swoll1980 said:**
> I didn't know this and edited the menu.lst directly. What could go wrong?

Nothing really but when Grub2 is updated it will overwrite your changes that you made. What Ubuntu or linux in general really needs is an easy way to modify the menu system. Grub2 is really more advanced then Grub and does pick up other operating systems better.

---

### Post by gwilson on 2010-02-22
> **gnomeuser said:**
> 

I believe it is time we consider if there might an option C.

Not sure I caught the few bits of jargon you threw out there. Are you saying you'd like to see an entirely different approach unlike either Grub version? 

I can't argue with that, but when you look at menu.lst, it appears to be little more that batch file like the ones I used years ago to dual-boot things Windows 3.1 and OS2.

The files Grub calls up are written by the operating system during the install or upgrade, right?

---

### Post by gn2 on 2010-02-22
Never had any need to tweak Grub 2 which "just works" thus far.

@ gwilson, there wasn't a 9.1, January isn't October.

---

### Post by gnomeuser on 2010-02-22
> **gwilson said:**
> Not sure I caught the few bits of jargon you threw out there. Are you saying you'd like to see an entirely different approach unlike either Grub version?

The options we have are unmaintained grub1 or unstable grub2 designed without use cases that are going to become common place in a year or so for Ubuntu users (btrfs). Finally there is the option of going for another bootloader.

Neither of those options seem very appealing to me. Grub1 isn't being maintained, Grub2 seemingly has the wrong designs, still isn't stable after years in development and hasn't gotten any uptake outside of Ubuntu. Finally there are non-grub bootloaders but none of these seem to provide appealing alternatives to our current options.

I would suggest rallying together distributions to collect grub1 patches and officially maintain the bootloader as a distribution/vendor independent project, in much the same way as rpm is now being maintained.

It seems like a good project, grub1 is fairly stable or at least it's badness is well understood. It would also be a good place for distributions to collaborate since everyone needs a bootloader and grub1 seems to be the primary choice. 

Someone would probably need to hire a fulltime maintainer to handle such a project. Here Canonical is looking like the obvious choice, it would buy a lot of important goodwill sponsoring such a project and let us continue to improve on a codebase most people use and invest a lot of time in keeping solid.

Over time such a project could like rpm currently does provide a venue for improvements of the codebase beyond consolidating vendor patches and give us a codebase we can deploy unchanged and will minimal effort. Over time it would be the perfect platform for determining the areas and order in which we need to improve the bootloader for use cases distributions need. 

I would look at the tremendous progress rpm has made after the rpm.org project got started following this model. I believe it could be made to work for grub1 and that it would be a superior option currently.

---

### Post by BrokenKingpin on 2010-02-22
I like Grub 1, because it isn't horribly slow on my system. The option on install would be nice.

---

### Post by Mr. Picklesworth on 2010-02-22
/etc/grub.d made me happy when I discovered it. It's way easier to arrange things with that kind of setup, especially for a configuration GUI. (Although I really don't see the logic in numbering those files over having an index).

The one rather troublesome thing is you can either have ALL alternative operating systems above Linux or all of them below Linux; no in between. 

Hopefully down the line those scripts can be beefed up so we can more nicely configure the types of entries they create. Maybe some way to shift around particular entries after the stuff in grub.d all runs, or at least a different script for each of the alternatives.

Of course, beyond that — (and I concede that my first discovery of grub.d was preceded by a half hour of cursing as I tried to figure out what the heck was going on) — I really don't know Grub, so take my opinion with a grain of salt.

---

### Post by bruno9779 on 2010-02-23
I have found [this thread]("http://ubuntuforums.org/showthread.php?t=1195275") right after installing grub2, and I haven't had any issue going by it.

---

### Post by handy on 2010-02-23
My distro doesn't use Grub2, & I don't boot multiple distro's on my machines these days. So I won't be using Grub2 until I have no other choice.

I liked the sound of what you had to say gnomeuser.

---

### Post by Mark Phelps on 2010-02-25
Maybe I'm an exception, but I've not encountered any "trouble" using GRUB 2 -- and I use a desktop PC with four OSs on it, two Linux, two MS Windows -- and every time that update-grub runs, it finds ALL the OSs and kernels without any problem.

Plus, it retains the customizations I've made -- unlike GRUB (1) which required hand-editing menu.lst every time.

---

### Post by Slug71 on 2010-02-25
When will people stop whining about this? Grub2 is in and its here to stay. Get over it. For Multi booters like my self Grub2 is far superior to Grub Legacy. Grub2 is also really beginning to shape up well now and Grub Legacy is no longer maintained.

Pretty soon every Distro will be using Grub2.

---

### Post by tomthumb99 on 2010-02-25
I have been living with grup2 pain for 2 months now, gald to find this post. While the old grup was dos like, at least you could hardcode menu entries and find your win-XP boot partitions. I would just edit menu.lst each time a new kernel was install, very predictable process. This post talks about folder /etc/grub.d, I will look into.

So, you folks created grub2 with lots of scripting (point?), where are all the admin GUI menus to make my life easy.  Having me look thru script, does not make my life easy (lots of files, junk all over).  I have to dig thru all the stuff you wrote. This 2nd generation boot loader is half baked, you need a whole GUI set of tools for the Xwin side (my opinion).  This is so 'joe six pack' can work the thing without needing a Phd.  But, I do like the ext4 support though.

For those who have complex boot setup with multiple disks (ie: 5 boot OS - 3 - Unbuntu, - 2 winXP) this does not help that much.  For example, I now have 3 seperate boot option for 9.10, how to get rid of the 30-17 bad one?

Why make things so complex, the future of ubuntu is dependant upon 'joe six pack' using the os (ie: tech geeky only goes so far).  If its too complex,the are going to buy a Mac.  Do you folks not learn anything from the current MS problems, SW needs to be simple to use, simple to fx....

{NOTE: I often suspected that MS spies are in the Ubuntu principle ranks, over complicating things.}

Ubuntu cannot be like an old Fiat car ( drive 50%, fix 50% of the time)

---

### Post by gnomeuser on 2010-02-25
> **Slug71 said:**
> Pretty soon every Distro will be using Grub2.

Except that none of the major distros have commited to this due to missing functionality and regressions.


[http://fedoraproject.org/wiki/Features/Grub2](http://fedoraproject.org/wiki/Features/Grub2)
[http://en.opensuse.org/GRUB](http://en.opensuse.org/GRUB)

Mandriva is waiting for openSUSE. Either distribution appears to deem a switch significant enough to warrant investing resources in filling in the gaps. 

If by pretty soon you mean no time in the immediate future and not much work being done to get there.. then yes you are right.

---

### Post by Twitch6000 on 2010-02-25
> **gnomeuser said:**
> Let's see a deprecated GNU project which is defacto unmaintained for years, then forked by every distribution to support required features.. or an overly complicated yet poorly designed GNU project which doesn't take into account requirements for modern features such as those needed supporting btrfs which has been years in the making without becoming stable.

It's like being asked which essential boy part I would prefer to have hit repeatedly with a hammer.

I believe it is time we consider if there might an option C.

A bit offtopic but dude that post was full of win.

Anyways that is why I use lilo now. =].

---

### Post by n0dix on 2010-02-25
legacy Grub never dies.

---

### Post by hiflyer780 on 2010-02-25
I run Ubuntu through Wubi and everytime I run an update I have to make sure to uncheck the grub-pc update otherwise it sends me to a grub prompt. Once I'm there I can't boot again and I have to reinstall Ubuntu. I hate the grub update. Worst move ever.

---

### Post by meierfra. on 2010-02-25
hiflyer780:

This will fix your Wubi problem:

[https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by Mr. Picklesworth on 2010-02-25
> **Twitch6000 said:**
> A bit offtopic but dude that post was full of win.

Anyways that is why I use lilo now. =].

Indeed. One should never get on gnomeuser's bad side; he emits more win than a supernova. Conquest and victory is the hallmark behind his every post.

---

### Post by andrew.46 on 2010-03-12
Hi gnomeuser,

> **gnomeuser said:**
> Except that none of the major distros have commited to this due to missing functionality and regressions.

Slackware still uses lilo as the default boot manager...

Andrew

---

### Post by gnomeuser on 2010-03-12
> **andrew.46 said:**
> Hi gnomeuser,



Slackware still uses lilo as the default boot manager...

Andrew

Remind me again this is that ultra elitist platform which at least for great parts of it's life considered a dependency resolving package manager and downloader an unneeded feature and thus had none or kept it highly optional for years? Don't fancy apt-get, yum, zypper or a tool such as Portage, I certainly can't imagine life without it and it is one of the highlights of any distro that it has one direct path to upgrade the entire suite of applications and the core system as well. It is a feature that functionally sets us part from the major competition such as Windows and OS X neither of which possess this. It gives us a clear edge. I am sorry for all the great things Slackware likely has done I hardly think they are the most relevant case to be studying in this instance.

Yes I certainly am impressed by their trackrecord of delivering a usuable project. It is however not the target audience that Ubuntu or any desktop system is trying to reach. Making it fairly irrelevant in the context.. OS X uses Boot Camp, Windows uses.. whatever. Foresight uses extlinux, most everyone else, the vast majority of users I would wager are on some unsupported or in perpetual pre-alpha version of Grub. Neither has feature completeness nor the desired level of support and active development.

Distributions really need to solve this problem, being different here gains you very little, it is basic code that just needs to work. It is best developed openly in the commons, not patched to smitherines by every distro on Earth to ail that trusty old horse around the race track. It is suboptimal and I am surprised we have let it happen for so long. 

It is time to do the Open Source thing and improve this sucker.

---

### Post by Paqman on 2010-03-12
> **bruno9779 said:**
> I like grub2.

It is just so much easier to set up multi-boot systems now.

"update-grub" works for real now, detecting and setting up boot menu entries, for pretty much any OS I have tried it on.

+1

Now that they've ironed out some of the bugs in Grub2 that shipped with Karmic, it's excellent.

---

### Post by Skaperen on 2010-03-18
Actually, Grub2 is a fundamental architectural shift compared to Grub1.  The arguments for Grub2 include it having new features that won't be in Grub1 (because the developers lost interest in ever reaching a true version 1.0).  But Grub1 has simplicity and nearly complete documentation.  Technically, neither is "ready for prime time".

In my experience, Grub1 is more mature, in part because of the documentation.  Grub2 has a lot more to be done.  However, switching to Grub2 in Ubuntu makes sense because Grub2 will be supported (as in adding new features when needed) by its developers.

Grub1 support has not disappeared.  Other distros that continue to use it are patching it as needed, such as support for drives larger than 2TB, and compiling on AMD64 platform.

Some of the "grub community" has gotten terribly religious about 1 vs 2 to the point of being arrogant.  They have failed to realize that something as simple as Grub1 still has uses that Grub2 cannot provide (though it isn't an issue for Ubuntu).  For example, I've built a system to construct flash drive bootable images directly into files, which is based on Grub1 because Grub1 builds genuine binary images in its compile process.  Grub2 does not (or if it does, the secrets to how to do this are not documented).  Grub2 requires running a program that is in the package to do the installing of the boot loader, and that doesn't seem to support image file building (again, maybe there is a secret undocumented way).

It would be nice if there was a "one universal boot loader" at least for the x86/amd64 platforms.  But with the approaches the Grub developers are taking, clearly there won't be.  They have abandoned some needs that Grub1 satisfied (including decent documentation).

The only thing Ubuntu might need to fear from Grub2 is that Grub3 might actually be a complete OS trying to replace Linux ... believable with the direction Grub2 is going.

---

### Post by gnupipe on 2010-03-18
GRUB1 is better for me.

---

### Post by Name change on 2010-03-18
GRUB1, and I'm a Arch user...
Funny thing, there was one user in Arch forums who wanted to go from Ubuntu to Arch and he was so pissed that GRUB2 wasn't in Arch repos, that he the decided not to change from ubuntu to Arch...
AFAIK.

---

### Post by Skaperen on 2010-03-18
> **gnupipe said:**
> GRUB1 is better for me.If you want to do things at a lower level, such as editing the config file to make it do what YOU want it to do, or work with systems constructed in different ways, then I think you will find GRUB1 (or LILO or others, depending on the circumstances) to be better.  Each bootloader has its target audience.

The confusion with GRUB is that the change from version 1 to version 2 changed the target, too.  That is a bit unusual for a project to do.  I didn't notice any change in target from Linux version 1 (I used Linux from even before that) to Linux version 2.  Apache didn't really change its target much (mostly expanded it) from version 1 to version 2.  I think the GRUB developers did recognize that by relabeling GRUB version 1 as "grub legacy" and then merely abandoned the relabeled project.

I'm considering starting my own boot loader project.  It's unlikely to be of much interest for the Ubuntu distribution as a default, but the way I have it planned, it should work OK as a boot loader Ubuntu users could switch to.  It will focus more on being a reliable (as in, try as hard as possible to get the system up) boot loader for embedded and dedicated systems.  One aspect of the design is that it will customize the boot loader binary image via compiling/assembling steps, to keep it small, as opposed to a boot loader that can do anything you want in one big fat binary image.

---

