---
title: "Disastrous experience with Ubuntu 7.10"
date: 2008-03-07
forum: Testimonials &amp; Experiences
---

### Post by IvanYosifov on 2008-03-07
Hello, everyone. 

This is the story of my ( disastrous ) experience with ( the current stable ) Ubuntu 7.10 . I'm writing this to point 
out the issues I ran into so that they can be fixed. This post was due a month ago but got delayed due to my busy 
schedule, so please excuse me if my memory has let go of some details.

The hardware:

Gigabyte GA-X38T-DQ6 motherboard
Intel Core2 Duo E8200 CPU
2G 1066MHz DDR3 RAM
one PATA hard disk
one SATA hard disk
2x XpertVision GeForce 7300 SE video cards
2x Creative Audigy2 Value sound cards
ZM500-HP Zalman PSU

The software:

The end goal was to build a two-seat multiseat system using the 32 bit Ubuntu 7.10 release. I also wanted an ext3 / 
partition on one drive with an external journal on the other ( consider it an experiment as this is not the way I 
ultimately ended up running ).

Condensed version of the story ( details in the bullet-point issue list ):

As the GUI installer doesn't support installing on premade partitions I downloaded the alternative install CD with the 
text based installer, which in my personal experience was very broken. It installs the system misconfigured in both 
critical and cosmetic ways. Next, even after mkfs'ing things properly from a Linux install on a different partition or 
from the live CD and testing that they mount correctly ( in the environment they were created in ) the text-based 
installer refused to mount the ext3 partition with the external journal ( giving me a very non-descriptive error like: 
"could not mount partition" ) in 4/5 cases and in the other 1/5 cases the installed system could not boot with the 
kernel panic'ing about not being able to connect the journal. I don't recall the external-journal-setup installing and
booting correctly even once. I'm sorry I can't be any more specific but all this was a month ago. At this point I 
abandoned the external-journal requirement ( or experiment if you prefer ) and installed the system using the GUI 
installer. I ran into several problems with this new ( now successful ) install. The showstopper was that performance 
under the slightest IO load was completely unacceptable. Copying a file from one hard disk to the other or downloading 
a torrent at higher speed made things slowly respond to clicks and simple YouTube clips in non-visible windows skip. 
Said YouTube clips stopped skipping as soon as IO activity ceased so it could not have been a network throughput issue. 
The things that turned up in my ( admittedly limited ) research were:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131094](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131094)
[https://bugs.launchpad.net/ubuntu/+bug/147464](https://bugs.launchpad.net/ubuntu/+bug/147464)

The discussions of the above bug tracker entries contained suggestions about manually compiling a newer kernel. At this 
point, since Ubuntu apparently didn't have the out-of-the-box polish and stability I expected it to, I gave up and 
decided to move forward with what I already fell comfortable and have several years of experience with - Gentoo. Gladly, the E8200 seems pretty well suited for compiling software. I had the entire base system + all of KDE + OpenOffice.org 
compiled and installed in under 12 hours. 

Bullet-point issues list:

1 ) Cosmetic issues with the text based installer: ugly text console font, double install CD reference in aptitude

Contrary to common sense the text based installer and the live CD GUI installer don't do the same thing. When comparing 
a system installed with the former to one installed with the latter I noticed the following cosmetic issues:
	- the text console font is much uglier
	- the installation disc is listed twice in aptitude's screen about package sources

2 ) Showstopper issues with the text based installer: bootloader installation.

Assume disk1 and disk2 are the first and second disks in the BIOS hard disk boot priority dialog. For some reason the 
text based installer was always installing GRUB to disk2's MBR while the system was booting from disk1, resulting in an 
unbootable system. The contents of grub.conf were all correct, just the boot loader itself was going to the wrong disk's
MBR. Switching disk boot priority did not help, the boot loader was still being installed to the wrong hard disk. This
does _NOT_ happen when installing with the GUI installer.

3 ) Live CD GUI installer system clock settings

It is my understanding that the live CD installer automatically sets the system clock to localtime if Windows is detected
and uses UTC otherwise. While nice, I'd still prefer being allowed to set this manually. I wouldn't mind if it was put 
away in an "advanced" installer section or something like that so that the casual user doesn't get confused, however it 
should be configurable. The PC in question here was new and I was going to install both Linux and Windows. I shouldn't 
run into trouble just because I installed Linux first.

4 ) Live CD GUI installer should support installing on premade partitions

It is my understanding that the alternate install CD is meant for more advanced setups that involve things like RAID, 
LVM or premade partitions while the GUI installer refuses to install on a premade /. Well, in my experience the alternate
install CD was almost useless. It's partitioning dialogs seemed quite clumsy and limited too. After all, advanced setups 
imply competent admins and no sensible partitioning dialog could possibly match the degree of control manual mkfs gives. 
Because of this Ubuntu should simply free the live CD installer from it's artificial limitation ( possibly with a huge 
red warning for the casual user ) rather than refer the user to the problematic alternate install CD.

5 ) IO performance

I pretty much described this in the condensed story. The system becomes totally unusable under IO load. Possibly related
to:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131094](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131094)
[https://bugs.launchpad.net/ubuntu/+bug/147464](https://bugs.launchpad.net/ubuntu/+bug/147464)

In my personal opinion, such an issue is hardly acceptable for a beta version, let alone a stable release.

6 ) Hard disk SMART inaccessible on the PATA disk

For some reason I was only able to get SMART readings on the SATA disk, while I know that both disks are SMART capable 
and that it's enabled in the BIOS. I didn't really dig into this one. Now ( current Gentoo 32 bit stable branch ) it's 
working so it could easily have been a package version issue.

7 ) Ubuntu should advertise the live DVD more prominently

The live DVD seems to be a much more handy install medium than the live CD. It contains both the text based and GUI 
installers for one. Not that this would matter if the text based installer is abandoned as I suggest above, but it would 
have saved me quite a bit of CD switching. Also, having a larger selection of software available off the install disk is 
always a plus. Yet, for some reason the live DVD isn't even mentioned on Ubuntu's main download page 
( [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) ).
It was by pure chance that I found out it existed at all. I personally would certainly have downloaded only it in the 
first place if I knew it was available.

8 ) Updates that don't work should be retracted.

While experimenting with the system, for about a week there was an automatic update available that was consistently
failing to configure with an error very similar to [https://bugs.launchpad.net/ubuntu/+source/fontconfig/+bug/104553](https://bugs.launchpad.net/ubuntu/+source/fontconfig/+bug/104553) .
Much to my surprise the failing update wasn't retracted even after there were was a forum thread and a 
bug tracker entry about it. Automatic non-exprimental updates should get at least some trivial testing and should
not require the user to search the forums or bug tracker just to get them to install. While I understand there are
manpower issues with thoroughly testing everything, to keep pushing an update after being notified of a problem makes 
no sense to me.

On the positive side:

If I ignore the issues outlined above, I must say that Ubuntu _does_ seem to be a very polished, functional and 
user-friendly binary distro. I think that it has an immensely more mature attitude towards closed-source software like 
Adobe's flash player, NVIDIA's drivers and SUN's java jdk than Debian. Also, the restricted codec installation procedure 
is just ingenious - the user gets to play his files and Ubuntu does _not_ get to hear from anyone's legal department. 
In short, I think Ubunut has a great deal of potential. However grave issues like the under-IO-load performance should 
never be allowed in a stable release. After all, when a system is useless stability is a non-issue.





I hope the development team is reading the forums, since I don't really have the time to file proper bug reports on
all of the above.

---

### Post by wolfen69 on 2008-03-07
i have done probably over 100 installs of ubuntu (on numerous computers) and never experienced the problems that you describe. it is ***your*** hardware that is the problem. if everyone had the problems you have, would millions of people be using it? i think not.

if you really want to use linux, buy it pre-installed. (Dell) windows machines work off the shelf because the hardware is preselected. you need to do the same with linux. good luck.

---

### Post by CaptainCabinet on 2008-03-07
> **wolfen69 said:**
> i have done probably over 100 installs of ubuntu (on numerous computers) and never experienced the problems that you describe. it is ***your*** hardware that is the problem. if everyone had the problems you have, would millions of people be using it? i think not.

if you really want to use linux, buy it pre-installed. (Dell) windows machines work off the shelf because the hardware is preselected. you need to do the same with linux. good luck.

OR he could just try a different distro.
Not everyone can afford a new computer with Ubuntu pre-installed.

---

### Post by Antman on 2008-03-07
> **CaptainCabinet said:**
> OR he could just try a different distro.
Not everyone can afford a new computer with Ubuntu pre-installed.

+1
There are many distros out there besides Ubuntu that could work well with your hardware. Just experiment.
Try Sidux, Debian Lenny, openSUSE, etc.
:popcorn:

---

### Post by SunnyRabbiera on 2008-03-07
Linux mint might work better too

---

### Post by CaptainCabinet on 2008-03-07
> **SunnyRabbiera said:**
> Linux mint might work better too

Forgot about that. 
Give it a try. :)

---

### Post by IvanYosifov on 2008-03-08
I'm sure my hardware is playing a big part. After all the post was about my _personal_ experience. Yet, I didn't file the 
bug reports I've referenced so apparently I'm not the only one having issues. I also think that more general problems like
the text installer being clumsy and the GUI one artificially limited apply to everyone. I might be wrong, but AFAIK the
text installer isn't even being developed by Debian anymore, so IMHO it should just be allowed to die.

Otherwise, I don't need to buy a computer with Linux preinstalled just go get it running. Nobody does, provided they are
ready to invest some time. As I mentioned in the post, I'm happily running Gentoo now, without issues. Still, I'm in no 
way suggesting for Ubuntu to adopt Gentoo's installation procedure even though doing so will invalidate _all_ "the 
installer doesn't do foo" complaints. ;)

---

### Post by 3rdalbum on 2008-03-08
Ubuntu *was* the different distro he tried, after several years with Gentoo.

---

### Post by Antman on 2008-03-08
> **SunnyRabbiera said:**
> Linux mint might work better too

LinuxMint, at its core is still Gutsy, so hardware limitations would still apply.

Best to try pure Debian (lenny or sid), openSUSE, Arch, etc.

---

### Post by julian67 on 2008-03-08
I've used the gui and text installers many many times and never had trouble installing onto drives that were already partitioned, even when installing onto systems with multiple HDDs. 

Are there any 1 CD distro installers that will cope with the ext3 journal in a different physical location than the filesystem? I'd thought that the normal way to achieve this is to install a default ext3 filesystem and journal and after completing install use mke2fs and tune2fs to create and configure the external journal. I can't quite believe anybody expected this to be done using the default installer on a live CD or even the alternate, or even for this config to be pre-made and then recognised by the cd installers.....or did I miss something amazing on other distros' installers????

---

### Post by jdrodrig on 2008-03-08
> **wolfen69 said:**
>  it is ***your*** hardware that is the problem. if everyone had the problems you have, would millions of people be using it? i think not.
if you really want to use linux, buy it pre-installed..

To be honest, this is the most offensive, windows-forum-like response I have read in the forums. 

I could not be more dissapointed. What can we learn from "it is your hardware" ,nothing, and these forums are about sharing problems and solutions, not making the obvious, non-constructive statements.

"If you really want to use linux, buy it pre-installed.." what?!!

---

### Post by julian67 on 2008-03-08
> **jdrodrig said:**
> ............ not making the obvious, non-constructive statements.

"If you really want to use linux, buy it pre-installed.." what?!!

not obvious, but obviously wrong :)

---

### Post by Antman on 2008-03-08
The beauty of Linux is that you CAN use your current hardware - just find the distro that matches. :guitar:

Windows = Buy new stuff
Linux = use what you got :KS

---

### Post by CaptainCabinet on 2008-03-08
> **jdrodrig said:**
> To be honest, this is the most offensive, windows-forum-like response I have read in the forums. 

I could not be more disappointed. What can we learn from "it is your hardware" ,nothing, and these forums are about sharing problems and solutions, not making the obvious, non-constructive statements.

"If you really want to use linux, buy it pre-installed.." what?!!

I thought it was a bit of a silly response as well. :)
The whole point of Linux is to be used by everyone on every computer. Buying it pre-installed should be a last resort in my opinion because then it's like saying "I can't be bothered to try". Of course companies like Dell giving customers the option of having Ubuntu pre-installed on new computers is fantastic but it's a huge waste of money if you can just use a different distro on your computer.

---

### Post by Jay Jay on 2008-03-08
> **CaptainCabinet said:**
> I thought it was a bit of a silly response as well. :)

Me too and also very arrogant.

---

### Post by IvanYosifov on 2008-03-08
> **julian67 said:**
>  I can't quite believe anybody expected this to be done using the default installer on a live CD or even the alternate, or even for this config to be pre-made and then recognised by the cd installers.....or did I miss something amazing on other distros' installers????

I never expected to be able to create the external journal setup with the installer. However, recognizing it is a different matter entirely - it's the kernel's job, not the installer's. Normally the kernel should be able to mount such a file system without issues.

---

### Post by julian67 on 2008-03-08
> **IvanYosifov said:**
> I never expected to be able to create the external journal setup with the installer. However, recognizing it is a different matter entirely - it's the kernel's job, not the installer's. Normally the kernel should be able to mount such a file system without issues.

The installed to HDD kernel yes, but  the installer's kernel? Are there distros with installers which support this? I'm curious.

---

### Post by IvanYosifov on 2008-03-09
> **julian67 said:**
> The installed to HDD kernel yes, but  the installer's kernel?
I fail to see how the install CD's kernel is special and somehow inferior. There isn't even a kernel config option to disable ext3 external journal, so why should it not work ? Perhaps someone has specially patched it to remove support for external journal ? I don't think so. Besides, I had no problems mounting the fs with the external journal from the live CD, however the GUI installer was refusing to install on a pre-made root, otherwise I could create files, etc. This ( IMO artificial ) limitation was the only reason for me to consider the text based installer. And since both installers 
are launched from the same disk ( at least on the live DVD ) they should be using the same kernel, so it can't be a kernel problem.

> **julian67 said:**
> Are there distros with installers which support this? I'm curious.
My only recent experience with installers is with Ubuntu 7.10 and Gentoo 2007.0 . I had no problems mkfs'ing and mounting
an ext3 partition with external journal from the Gentoo install disk and installing to it ( 'installing' = extracting the base system tarball to it ).

Preventing user mistakes during installation is important but the installer should be able to just do what I tell it to.

---

