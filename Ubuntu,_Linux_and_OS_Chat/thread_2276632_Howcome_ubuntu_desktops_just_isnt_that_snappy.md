---
title: "Howcome ubuntu desktops just isnt that snappy?"
date: 2015-05-04
forum: Ubuntu, Linux and OS Chat
---

### Post by Higgins909 on 2015-05-04
I love my server, as it's running ubuntu server 14.04 (close to that) but desktop has allways been a bit iffy for me :/

For my laptop it was that you needed to download wifi drivers manually (didn't come with install) and then it was kinda slow... better then window 10 that I decided to try, but slow...
(windows 10 can barely play hulu/youtube/really any video)
Around 12.0-13.0 I couldn't even boot the cd because it would just give my a raindbow screen or something on my desktop... works now tho...

On my desktop:
amd athon II x4 640 propus (3ghz quadcore)
4gb ram
radeon hd 6790 gpu
plenty of storage and psu...

Things still arn't as fast as I would like... I've tried arch linux failed hard "several times" and openbox also failed hard several times...
like the... we'll call if start menu, is slow and shows random music and other stuff that I don't want to see... just like windows 10, but atleast UD will show you programs that are actually on your computer...
Right now I can't come up with enough reasons, but why is it just so slow? ... I'd love for me to open a program and it just open before I can even move my mouse open.
(that doesn't even happen on win7 but I hear/used windows 8/8.1 is snappy, esp with the start menu)

offtopic, but is this just how linux is? kinda unrefined?
I've been watching ubuntu for 3-5 years and it just still feels so unrefined... desktop atleast. (drivers and compatibility issues etc)
even my server has this memory leak right out of 14.04 or something... running it as is...

---

### Post by dino99 on 2015-05-04
here is a Mint experience [http://community.linuxmint.com/hardware/view/16529](http://community.linuxmint.com/hardware/view/16529)
if something is not working as it might on your installation, then glancing at logs should help narrowing down the issue(s)
or maybe compile the kernel to get a better experience
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

---

### Post by kerry_s on 2015-05-04
you can alway go to a lighter ubuntu version, i suggest trying the 1's without heavy 3d ui's.
that would be, ubuntu mate, xubuntu, lubuntu, .... you could even try others that are based on ubuntu such as elementary os. have a look at [http://distrowatch.com/](http://distrowatch.com/)

---

### Post by buzzingrobot on 2015-05-04
> **Higgins909 said:**
> 



radeon hd 6790 gpu


Seems to be supported by the open source driver used by default. More here: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver).  Note the ways to check the driver is working properly.

> ...menu, is slow and shows random music and other stuff that I don't want to see...

Unity searches and displays online results by default.  Check Systems Settings for adjustments. Also, install 'Unity Tweak Tool' for additional options.

Fours gigs of RAM should be adequate but certainly not excessive.  Check the system is seeing all of it. 

Otherwise, there's no info to go on.

The core components of any distro are much the same, varying by version number. Choice of desktop environment/window manager can make a difference to some degree, especially when combined with use of apps demanding less RAM.

---

### Post by ian-weisser on 2015-05-04
> **Higgins909 said:**
> it was that you needed to download wifi drivers manually (didn't come with install)
OEM's fault. Many wifi components works perfectly out-of-the-box. OEM chose something different.

> **Higgins909 said:**
> and then it was kinda slow.
Open a terminal and run the 'top' command for clues when it's slow.
Post the output here if you need help interpreting it.

---

### Post by Bucky Ball on 2015-05-04
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by craig10x on 2015-05-04
You can turn off the online searches in the dash (those are coming from amazon) by going to system settings, then security & privacy,  then search... and turn off the on button and you won't get those anymore...

---

### Post by mattharris4 on 2015-05-04
Higgins, I did a Google search on your CPU and found that it is from around 2010.  CPU speeds are not cross-comparable, for example some new 2 GHz CPUs could very well be much faster than your 3 GHz CPU.  It did test quite well back when it was new but likely most newer non power-saving chips have far surpassed the speed and power of this CPU (I say non power-saving because there have been several CPU lines built that emphasize low power usage over processing ability such as the Intel Atom and AMD E1, both of which your current CPU would likely run circles around).  Since current OSes are more demanding on CPUs (as well as current websites, browsers, etc.) than older OSes this could be part of the problem.  This is one reason a computer can seem to slow down as it ages even if the hard drive is wiped and the OS and related drivers and programs are reinstalled regularly, the OS, its updates and/or the replacement OS (say Ubuntu 14.04 as a replacement for 12.04) require more of the CPU causing the computer to run more slowly.  Lack of RAM is a big factor as well but you have 4GB of RAM which for a Canonical OS should be more than enough.  Normally I would say unless it is taking a ridiculous amount of time to open Firefox or other programs (say more than 30-45 seconds) that you probably should just live with it but since you mention running a server that may not be an option if that is what you are doing with this computer.  If this is for a server I cannot give you much advice here but if this is a day to day desktop for web browsing, word processing, database, Power Point type presentation preparation, etc. and it isn't running ridiculously slow I would just use it as-is.  I use an eight year old Pentium 4 CPU 3 GHz in an HP desktop, it still works passably using Edubuntu for these purposes.  It actually works faster than my year old laptop with the "power-saver" E1-2100 1GHz chip in it.

---

### Post by d-cosner on 2015-05-04
@ mattharris4

Ubuntu 15.04 x64 is running fine here on an HP 655 laptop with an AMD E1 processor @ 1.2 GHz. It was slow as molasses in winter until I installed the proprietary drivers. Now it runs pretty nice!

---

### Post by monkeybrain20122 on 2015-05-04
> **d-cosner said:**
> @ mattharris4

Ubuntu 15.04 x64 is running fine here on an HP 655 laptop with an AMD E1 processor @ 1.2 GHz. It was slow as molasses in winter until I installed the proprietary drivers. Now it runs pretty nice!

Probably you just need to upgrade your open driver. [https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers) A lot of work has gone into adm cards but it is not filtered down to Ubuntu releases (especially if you are using LTS) Probably need to update kernel to 3.19 or 4.0 as well to take full advantage of it.

---

### Post by d-cosner on 2015-05-04
@ monkeybrain20122

Yeah, I am running 15.04. After installing the proprietary ATI drivers and the AMD micro code driver the laptop was quick again. In the past the open source drivers worked better and the proprietary drivers gave me a washed out display. It all turned out good in the end!

---

### Post by mattharris4 on 2015-05-04
Thank you d-cosner and monkeybrain.  Your advice is much appreciated and this thread is bookmarked.  When I have the laptop on AC power and wired to the router I will look at this further.  However, it isn't ludicrously slow -- just slower than the non-low-power processors, it may be comparable to or slightly faster than a Celeron 900 processor running at (IIRC) 2.16GHz from 2010 which is a very cheap processor included in budget computers of that era -- my mother has a laptop with that processor and I update her Win 7 install monthly (I would love to install Lubuntu on that computer but she doesn't want it, I think it would take care of Firefox taking 30 seconds to start and five minutes to boot -- Lubuntu boots up in about 45 seconds on my laptop).  It is also somewhat slower using the factory-installed Win 8.1 than the processors produced in 2014 that aren't made to sip power rather than gulp it and many others have complained about it so I just took it for what it was.  The power adapter is only 45 watt (at 120VAC) rather than the 65-90 watt adapters  usually packaged with laptop computers (some gaming laptops come with a 120 watt adapter but that is just a very few computers from my research), that shows how low power the processor is that it will both run the computer and charge the battery with only 45 watts maximum current.  I hope this provides more information to my comments in the prior post.
 
My laptop is a Toshiba and it has the E1-2100 processor running at 1.0GHz (I know processor speeds aren't directly comparable but most processors a year ago ran between 2.0 and 3.2 GHz including the well regarded Intel i3/i5/i7 series). Yes, I do use the LTS version, I really don't wish to deal with every six months updating to a new version.  From posts here and comments/questions/bug reports in general it also seems to me that the non-LTS versions should generally be saved for those that test and troubleshoot the OSes and a person using these versions can expect more bugs and problems with their OS installs.  Upgrading the kernel is something I hadn't even thought of, I need to look into that more but I will probably try the linked driver as it appears to be simple to install and includes instructions to remove them if they cause an issue (admittedly as long as the computer still boots into Lubuntu after install).  It does say 14.04 LTS is supported although the compiler recommends 15.04 I am guessing because he uses that version regularly.  I will report any changes here after using it for a while or if I end up removing it due to some issue.


EDIT:  I installed the drivers referenced in the linked page along with some drivers that were supposed to be installed before it according to the instructions.  For the most part the computer does load web pages, scroll through bookmarks in Firefox and respond to clicking links faster.  It also uses somewhat less RAM and CPU percentage (about 10% or so less RAM).  It still isn't perfect as some surfing on RAM and CPU hog SFGate.com showed but surfing is improved.  However, it takes up to 45 seconds from clicking the off switch in the lower right corner of Lubuntu 14.04 to being able to select from (or even see) the shutoff menu where you select to shut off, reboot, etc.  I will see if that continues through routine updates, it is interesting that if everything else about the updated driver package works well that it would detrimentally affect turning off or rebooting the computer.  This is without knowingly updating the kernel.

---

### Post by craig10x on 2015-05-05
You might want to give 15.04 a try for your desktop...i find it runs faster and snappier then either 14.04 or 14.10 did...you could try it on a live session...of course, a live session would be a bit slower then an installed one but you would still get a "feel" for whether it would seem snappier to you or not...worth a dvd burn to check it out, anyway...

---

### Post by mattharris4 on 2015-05-05
^  Maybe I should find the USB stick I used to check out several OSes, then format and put Ubuntu 15.04 on it.  Whether it would work on the desktop would largely depend on whether support for the aging hardware was removed from it or not.  The desktop is eight years old so that is a concern.  The laptop would likely be supported at least as well as on 14.04 as it is only a year old but I have a dual-boot with Win 8.1 on that of which I would have to consider whether I wish to risk bricking or not for to install 15.04.  Of course I can try it out on that as well although it is 64 bit whereas the desktop is 32 so I would have to load two USBs separately in order to try it on both (32 bit Linux OSes whether Canonical's or another provider's are not compatible with computers running a UEFI which the laptop certainly has).  I doubt I would brick that install trying the new version out via USB, however.  My biggest concern other than the dual-boot install on the laptop (the desktop is dual-boot with Win XP which is woefully out of date now, it doesn't really matter if I mess that up) is whether I wish to update the OS version every six months, with the LTS versions even with Lubuntu I have a year or so after their release for Canonical to work the bugs out of the new version.

---

### Post by Bucky Ball on 2015-05-05
I advise LTS, but as you say, if you don't mind upgrading every nine months, go for an interim release. But ... I would advise sticking with 14.04 LTS. If your hardware was new, perhaps 15.04 would be an option, but I honestly have no idea what benefit going for 15.04 is going to give you. If it is not working in 14.04, there is no good reason the same will not be the case with 15.04 (in fact, support may have been dropped for some older hardware in 15.04).

The decision is yours, of course. Try them both from the USB and see what happens would be one way of finding out if there's any diff. Can't see it ...

---

### Post by d-cosner on 2015-05-05
@  				 				 					 						 	[**[COLOR=#000000]mattharris4[/COLOR]**]("http://ubuntuforums.org/member.php?u=1964569")

To make the web browser seem quicker I install ublock in Firefox, it's light on resources. Using heavier ad blockers like ad block plus slow down the menus in Firefox, at least with my 1.2 GHz E1 processor.

---

### Post by mattharris4 on 2015-05-07
> **Bucky Ball said:**
> I advise LTS, but as you say, if you don't mind upgrading every nine months, go for an interim release. But ... I would advise sticking with 14.04 LTS. If your hardware was new, perhaps 15.04 would be an option, but I honestly have no idea what benefit going for 15.04 is going to give you. If it is not working in 14.04, there is no good reason the same will not be the case with 15.04 (in fact, support may have been dropped for some older hardware in 15.04).

The decision is yours, of course. Try them both from the USB and see what happens would be one way of finding out if there's any diff. Can't see it ...

I haven't had a chance to try a USB of 15.04 yet.  I am leery of whether it would provide an improvement but as I said I don't think I would be able to brick my current install trying it out as long as I don't click the "install Lubuntu" icon.  I suspect if there were to be any improvement it would be to the laptop as the processor in it is still being used in new computers so there is impetus to improve support for it.  The desktop has a processor that hasn't been used in new computers for years and is working well as-is.  The new drivers have improved how the laptop works except for shutting it down where it takes about 45 seconds for the box to select shutdown, reboot, etc. to appear after clicking the power icon in the lower right corner of the screen.  In general as long as the computer continues to do that and the power off function does not fail completely I guess that isn't the biggest of concerns.  I probably should let the programmer that wrote those drivers of the issue, however.  I also need to test battery life with the new drivers, before installing them I got about four hours of battery life before having to recharge the battery (about an hour less than with Win 8.1 but that OS is not as smooth and responsive as Lubuntu for most functions either before or after the new driver install).

Since the link is on page one and this is page two I will repost the link to the drivers being discussed so people don't have to go back a page to take a look:  [https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers)

---

### Post by mattharris4 on 2015-05-07
I do have a couple of questions here about reporting bugs.  Granted this is not a Canonical report which is probably what most here are used to but I don't have any idea how to get the information needed to do a complete report.  I have attempted to copy and paste (to this forum but I think I would have the same issue here) before and the usual right click, copy and paste functions do not exist in the terminal so I don't even know how to do that for the programmer.  Here is a bug report for this driver as an example of what I think the programmer is looking for even though it does not specifically pertain to my shutdown issue:  [https://bugs.freedesktop.org/show_bug.cgi?id=79997](https://bugs.freedesktop.org/show_bug.cgi?id=79997) .  

I don't even know if I am using a 2D or 3D driver and the documentation says that the programmer needs bug reports to go to a different link based on whether the driver being used is 2D or 3D.  I would like to help this guy improve his product (other than the delayed shutdown issue it is excellent) but have no idea how to do so effectively, just a report with the problem and no other information isn't likely to help him much IMO.  As I have said on here before, I am not a programmer -- I can get by installing and using Lubuntu/Ubuntu/etc., solve common problems (which this definitely is not) and follow instructions if I have a problem I cannot solve on my own but I am not a programmer myself and as such do not have the knowledge of that end of Linux to even do a search on how to get the information needed here and copy it to his bug report form.

A large update just came through to my computer that requires a restart.  I will refer back to this thread in a little bit, maybe by chance the programmer sent through an update for this issue although since my desktop not using his drivers had one last night as well and he does not seem to have another report with this issue that may be wishful thinking.  

Thank you for any assistance you can provide me.  It is much appreciated.

Moderators:  If this thread has veered too far away from the intent of this sub-forum, please feel free to move the pertinent posts or the thread to the appropriate support sub-forum.  I don't know how to ask there without copying and pasting an unacceptable amount of others' posts to back up my questions.

---

### Post by monkeybrain20122 on 2015-05-07
The improvements I find in 15.04 are kind of idiosyncratic. It is easier to compile some software I use because of the more up to date libs (so that I don't have to get them from ppas or compile them) There are some performance tweaks and it feels faster on my hardware, though it is marginal because 14.04 is already fast on this machine. 15.04 itself is great, probably one of the best releases along with 13.04 and 13.10 (all non LTS's) and so far seems remarkably bug free for a new release (need more tests to be sure). But because of the short support cycle installing 15.04 would be gambling on 15.10 will also be a great release, well 14.10 wasn't so great here. 

In general I would think that unless you have new hardware 14.04 is probably preferred. There is a  less disruptive way to upgrade your user end software (ppas)

Things like shut down and start up cannot be benchmarked very accurately with a live usb. Also live .isos haven't been updated so you will see bugs that have already been squashed.

---

### Post by mattharris4 on 2015-05-07
That update I referenced in my last post must have been from the programmer.  The page where the instructions are located show that the programmer(s) have made five updates in the past 18 hours (likely more than one programmer on this project with five updates in such a short time).  The shutdown screen is appearing within a couple of seconds of clicking the appropriate icon.  Thank you to everyone for their assistance.  As issues may come up later where I need to access and copy/paste the info referenced in my post asking for assistance please post with the instructions if you can.  Evidently I do not need to post a bug report for this now but you know that bugs come up from time to time that don't get solved unless the programmer(s) know about them and I would like to be able to actually help the programmer(s) in taking care of the problem instead of just saying "my computer is doing this using version __________ of ___________" which isn't likely to be of much assistance to someone.  

I might still try a USB of 15.04 but likely will not install it unless it is earth-shatteringly better in something with my laptop.  With the shutdown issue evidently corrected with the new drivers many of my concerns are taken care of and with the crappy processor in my laptop I can only expect so much.

I will keep this thread bookmarked and refer to it over the next few days.  If I run into any more issues with the new drivers I will certainly post here.

---

