---
title: "Please excuse my rant"
date: 2008-10-15
forum: Testimonials &amp; Experiences
---

### Post by RedRat on 2008-10-15
OK, I have used Ubuntu now for about a year. Perusing these forums and even the newsgroups, I see that if Ubuntu has a weakness it is in the handling of video drivers. This morning I did a synaptic update and completely botched my display. Thanks to all on this forum for helping out and eventually getting it straight. 

But here is my point, it took a bit of messing around to get my system back to "normal". I would hope that the Ubuntu/Linux developers would take some pity on us beginners and realize that installing and maintaining the video display can be complex. I pity the newbie here. I would hope that in the upcoming releases of Ubuntu that they could make these video driver installs far more easy. 

In reality I should be able to go some menu item and click on display and be able to manually set my monitor description, screen resolution & refresh, and then select my video card. Yes this can be done but in most cases the setting don't stick. Eventually I had to reinstall the Envy drivers using envyng from the command line. Most newbies would find that daunting. There really has to be an easier way.

OK, sorry about the long rant. But maybe someone can pass along the suggestion to the developers.

---

### Post by kellemes on 2008-10-15
Rant should be addressed to the driver-developers, they are responsible for creating working drivers and offering an easy install path.

---

### Post by jerome1232 on 2008-10-15
nvidia is pretty easy usually, you have nvidia-settings and nvidia-xconfig. nvidia-settings is a gui to configure xorg.conf, 

nvidia-xconfig get's you to default settings that work with nvidia cards.

---

### Post by porchrat on 2008-10-15
And ATI has the Catalyst Control Center (downloadable from their website or you can get it from the add/remove programs option which is really simple)

---

### Post by RedRat on 2008-10-15
> **kellemes said:**
> Rant should be addressed to the driver-developers, they are responsible for creating working drivers and offering an easy install path.

A quick look at the forum here does not indicate exactly what forum you have in mind. I would suggest that maybe if the developers would occasionally take a look here in Beginners forum that might see some problems. If you know exactly where to send the rant, please do so. I don't and don't know how to do that.

---

### Post by kellemes on 2008-10-15
> **RedRat said:**
> A quick look at the forum here does not indicate exactly what forum you have in mind. I would suggest that maybe if the developers would occasionally take a look here in Beginners forum that might see some problems. If you know exactly where to send the rant, please do so. I don't and don't know how to do that.

I meant the developers of the cards themselfs.. AMD, NVidia, Intel etc..
They create the card, they should create a working Linux driver for it.

---

### Post by kevdog on 2008-10-15
I actually thought your rant was well thought out and very logical.

---

### Post by RedRat on 2008-10-15
> **jerome1232 said:**
> nvidia is pretty easy usually, you have nvidia-settings and nvidia-xconfig. nvidia-settings is a gui to configure xorg.conf, 

nvidia-xconfig get's you to default settings that work with nvidia cards.

If you had seen my earlier plea for help you would see that trick did not work. All my attempts to get the nvidia driver to even work was to no avail. Basically, I had to go to the command line and use the envyng -q command,that finally resolved my issues. Here I got help from this forum and I thank all who contributed.  

But my real point is that it shouldn't be that complex. Take consideration of the newbie here. Luckily I have had some minor experience in envyng and command lines, not all newbies do.

---

### Post by LowSky on 2008-10-15
He wasn't pointing to the forum, as this is a forum run by users not developers. He meant send an email to Nvidia, AMD/ATI, VIA, SiS and Intel about making better drivers for linux users. Just understand that most users have few if any issues with video drivers when using a basic install. The probelms is that many issues arrive when you introduce things like Compiz or Games. Things that for years were something no one really did on linux

---

### Post by DrMega on 2008-10-15
> **kellemes said:**
> I meant the developers of the cards themselfs.. AMD, NVidia, Intel etc..
They create the card, they should create a working Linux driver for it.

ATI claim they check the "major" forums regularly.

---

### Post by SpenceMakesSense on 2008-10-15
albiet I agree with what he says one rant I would like to say is how people put rants and stories of leaving linux inside of absolute begginer talk instead of the community forums.

---

### Post by RedRat on 2008-10-15
> **LowSky said:**
> He wasn't pointing to the forum, as this is a forum run by users not developers. He meant send an email to Nvidia, AMD/ATI, VIA, SiS and Intel about making better drivers for linux users. Just understand that most users have few if any issues with video drivers when using a basic install. The probelms is that many issues arrive when you introduce things like Compiz or Games. Things that for years were something no one really did on linux

That may be true. But why then did my synaptic update screw up the video display, basically uninstalling the video driver. My final solution was to reinstall via the command line and envyng. I don't think that was Nvidia's fault. That is a ubuntu issue in making the update today.

---

### Post by jerome1232 on 2008-10-15
> **RedRat said:**
> That may be true. But why then did my synaptic update screw up the video display, basically uninstalling the video driver. My final solution was to reinstall via the command line and envyng. I don't think that was Nvidia's fault. That is a ubuntu issue in making the update today.

Well, I'm willing to bet you got a kernel upgrade. If you installed using envyng then it compiled a driver for your old kernel. 

Ubuntu can't recompile the driver envy has to. The only time the driver gets automatically updated is when using the restricted driver manager, I do realize newer cards can't use that though.

But yes I wish Nvidia/ATI would better support their linux drivers, namely with their configuration utilties and a way to automatically recompile the driver every kernel upgrade.

---

### Post by ByteJuggler on 2008-10-15
> **RedRat said:**
> A quick look at the forum here does not indicate exactly what forum you have in mind. I would suggest that maybe if the developers would occasionally take a look here in Beginners forum that might see some problems. If you know exactly where to send the rant, please do so. I don't and don't know how to do that.

Unfortunately the developers are unlikely to look here as a matter of course as this is community supported forums.  Some of them *might* come here but it's not a given.  For particular suggestions of comments that are more likely to find developer ears, you should visit [Launchpad]("https://launchpad.net/ubuntu") and submit bug reports, or perhaps new blueprints or suggestions for blueprints.  I notice there's a [blueprint]("https://blueprints.launchpad.net/ubuntu/+spec/driver-device-manager") thats somewhat related to your suggestion (inasmuch as it relates to a GUI for drivers in general) that's been deferred since Feisty (7.04).

That said, for what it's worth, the whole driver and video support aspect of the X server is being improved and worked on substantially at the minute, so this situation is due to improve as new releases come out.

---

### Post by porchrat on 2008-10-15
> **DrMega said:**
> ATI claim they check the "major" forums regularly.

LOL yea right.  With all the issues people have with ATI drivers you'd think ATI would create some sort of concrete guide for each distro with a step-by-step install guide that also lists the common problems encountered.  I know that it is generally regarded as the community's job by most companies, but I really hate that mentality.

---

### Post by SteveNorman on 2008-10-15
The problem is with the manufacturers of the graphics cards. Many are under pressure from MS et al not to make drivers for linux, or they just dont see it as a profitable endeavor. As a result proprietary drivers have to be made by a gracious volunteer or a team of developers willing to spend their time on it. It is very recently that nvidia started making linux drivers at all. And if you think linux is tricky now,,you should have tried it a few years ago. Ubuntu is one of the first "easy" distros, they have done a great job making a difficult os easier for new users transitioning from windows. The learning curve is still higher than windows, but the rewards for learning are greater in the long run. I just got through re-loading my graphics drivers after the new update hosed mine. A few months ago I would not have been able to do this,,but know I can. You will know more about your computer and the way things work after a year of linux than after 10 years of windows.

I really think it would be helpful to voice your concerns to your preferred hardware manufacturers  so that they can see that the linux community is growing and there is a legitimate market amongst us that warrants their co-operation. Supply and demand dont you know

---

### Post by Lateforgym on 2008-10-15
Your concerns are valid and improvements are being made. I wrote a rant similar to your, then deleted it before posting relating to my wireless being cut out after and update.

Bare with me. Consider though how difficult hardware can be to work with. For example I have a Intel Pro wireless card which is a Broadcom chip as I understand it. It is the such a recent card that it is still widely  available. It is Intel branded and a commonly used part in Dells. Intel and Dell> You would think there products would work very well. Let me tell you the problems I have had with Windows XP and this card. First it brand new, not a refurb and not used.   While at a coffee house that uses encryption such as WEP and I think ACCP, over a 5 hour period I will have to connect and reconnect 2-3 times; yet MAC users and others dont have this problem. Yes I have the latest drivers, in fact this has had at least 4 driver updates and Intel still doesnt have it right. Further, after 5-6 hours of beating my system to death, I finally figured out that the reason why my laptop takes 2 minutes to shut down is because of this driver, made by Intel (I think its off their website) for Dell computers, for Windows XP AND its XP certified! The oly way around this is for me to disable the very handy Intel Wireless management software. Upon hours of searching, the evidence is clear this is massively bloated and there are plenty of threads where people just accepted their losses and bought a card from a different maker. I have went through all sort of sharades changing settings, at one point I would have to resart 5-6 times instead of 2-3.

You may find this interesting. Linux works perfectly with this wireless card. WHAT? Yes, I mean to tell you that Linux runs ungodly better then the latest, Windows certified driver by Intel for heavy use in Dell computers, which makes computer for Linux.

Here is another one, before ignorantly buying this card I had its previous generation. Intel sold it as working with WEP encryption. It didnt, after hours of toying on that card the unofficial Intel "fix" as told to others spent hours on this issue was to buy a new card or try to set your WAP to another encryption that works. Which the latter is stupid since its not like I can tell the manager of the coffee house to change his router setup, assuming he even knows what a router is. As far as Im concerned, like in the auto industry you buy a car on the idea that it starts and runs, not sporatically, and like automakers one should get it fixed or a replacement, not "Hey buddy, just buy a new one".

Lastly the funny thing about all this is it still to much of an annoyance for me that this has pushed me to use Ubunutu a lot more so I dont have to deal with having my connection dropped. 

My lengthy point is that if something as amazingly common as the intel pro wireless card that is "windows certified" doesnt even run right and their answer is get lost, rants are ok, but just remember what life is like for underpaid Linux developers who are shunned by companies trying to not be forth coming with helpful info when they make drivers that are better then the makers themselves.

My card works perfect in Linux, not Windows. THANKS DEVELOPERS!!

---

### Post by ByteJuggler on 2008-10-15
> **Lateforgym said:**
> Your concerns are valid and improvements are being made. I wrote a rant similar to your, then deleted it before posting relating to my wireless being cut out after and update.
[...]
My card works perfect in Linux, not Windows. THANKS DEVELOPERS!!
Glad you got yours working Lateforgym.  Unfortunately many wireless adapters (edit: or at least, to be more exact, their drivers...) seem to be notoriously flaky.  Your experience more or less mirrors my recent experience in trying to get a stable/working 300Mbps (N standard) wifi setup working reliably.  I originally bought a Belkin N USB adapter, with an RT2870 chip inside.  From the get go I had problems of dropped connections on Windows.  Irritatingly they only seemed to happen in relatively predictable situations (e.g. certain types of traffic/when the connection was being stressed a bit) which made me suspcious about the adapter and the drivers etc.  Anyway, I googled, I updated firmwares up and down, I did Indian rain dances etc. but all to no avail.  Eventually I got so frustrated up I went out and blindly bought a DLink N series (DWA-140) USB adapter, on the basis that it was listed as meant to work with my Dlink N (DIR-655) router.  (As an aside it eventually turned out this adapter uses the same chipset as the Belkin... so now I had  basically 2 identical adapters except for external window dressing.)  Now, you'd think products mentioned on the box as suitable for pairing would work flawlessly right?  Well, initially things looked a bit more promising, but ultimately I still experienced similar crashes and droupouts.  Eventually i just kind of put up with it, and I've been intending wiring up the computers at some point with wire when I have some free time.  However I also still had on my "todo" to try to get the adapter working on Linux, so yesterday I did some more research on that and found on the chipset maker's site (who produce the RT2870 chipsets used in the USB adapters) that they released a new version (1.40) of drivers for RT2870 based adapters for both Windows and Linux.  It turned out that all the dropouts and problems suddenly magically disappeared like mist before the sun on Windows, and I also managed to get the Linux driver going reasonably easily as well where it didn't want to work before.  (The driver still doesn't work on the latest version of kernel however, on which it crashes/doesn't work... but I can cope with that as I'll just keep booting with the .19 kernel a bit longer.)  So anyway, lengthy bottom line:  Crappy wireless drivers is sadly very common it seems... :(

---

### Post by ukripper on 2008-10-16
> **kevdog said:**
> I actually thought your rant was well thought out and very logical.

+1 fully agree

---

### Post by 3rdalbum on 2008-10-16
It wasn't a rant, it was a valid point.

There are three problems at work here:

1. Nvidia and ATI have little interest in making their drivers easier to install. They assume that "The people who use Linux are real gurus, therefore they'll have no trouble installing our drivers". The other day I had to turn off X in order to install a new Nvidia driver! Crikey, this is 2008, and I've never had to do that with an ATI driver!

2. It sounds like you recieved a kernel update. Graphics drivers link into the kernel, and when the kernel was updated your drivers weren't. Ubuntu developers are hard at work implementing two things that should help stop your situation from occurring:

# DKMS; it automatically rebuilds kernel modules, including the graphics driver wrappers, when the kernel gets updated
# A better recovery mode when Xorg fails, that should allow you to get back up and running easily

3. I don't trust Envy; it caused problems with my dist-upgrade. It's kinda not really supported, so i don't think you should use it if you can possibly avoid it.

---

### Post by ukripper on 2008-10-16
Ubuntu Recovery process needs improvement for xorg when new updates are installed. I had to compile and install manually ATI drivers for X1950 pro and next update borked the xorg putting back drivers to useless blurry resolution. Recovery mode didn't do any good either so had to reinstall the drivers again. I fully understand the pain OP has gone through.

---

### Post by SteveNorman on 2008-10-16
One thing that I think would be helpful, is when updates come out, maybe there could be a notice telling us what to expect. For instance letting us know that a kernel update will require re-loading the graphics driver would prevent the shock of OMG ALL I GOT IS A CURSOR when you reboot. I think a lot of the experienced linux community forgets how hard the transition from windows/mac is for many people, and in my experience the information available is still a little advanced for new users. Telling someone they need to mod their /etc/X11/xorg.conf file can scare the hell out of a new user if its not laid out in detail.

Good thread BTW

---

### Post by jerome1232 on 2008-10-16
hehe, I just had a fight with graphics while testing Intrepid, apparently nvidia-settings/nvidia-xconfig doesn't work correctly with the new version of xorg. I set up my tv-out with it and on x restart 'failed to parse xorg.conf' had to run 'dpkg --reconfigure -phigh xserver-xorg' and reinstall the graphics driver because 'nvidia-xconfig' wasn't working either.

I really hope those utilities get updated. My zsnes/playstation emulation depends on it (what good are console games if they aren't on the tv!?)

---

### Post by RedRat on 2008-10-16
> **SteveNorman said:**
> One thing that I think would be helpful, is when updates come out, maybe there could be a notice telling us what to expect. For instance letting us know that a kernel update will require re-loading the graphics driver would prevent the shock of OMG ALL I GOT IS A CURSOR when you reboot. I think a lot of the experienced linux community forgets how hard the transition from windows/mac is for many people, and in my experience the information available is still a little advanced for new users. Telling someone they need to mod their /etc/X11/xorg.conf file can scare the hell out of a new user if its not laid out in detail.

Good thread BTW
My rant came about because I really have fallen in love with Ubuntu and dearly wish it to succeed. Here's the thing, Linux needs to be a bit more aware of what it takes to be a success. 

The Linux community needs to be somewhat marketing oriented in that it ought to understand that most new users are coming from the Windows and Mac worlds. If you told a new user that they would have to recompile their video driver, they would faint on the spot. They wouldn't touch Linux or Ubuntu with a 10 ft pole and run screaming away. 

Now some of the old geeks in the community would take the attitude of "good riddance" (I have seen that attitude in the newsgroups particularly). But it is the newbies and the experimenters that will carry on and increase the Linux base. Luckily here in the Ubuntu forums I don't see that attitude expressed overtly and the people here are extremely helpful. Frankly, I steer people away from the newsgroups because of the flaming.

In the end I wish that the developers would look in here and see what problems users are encountering. I would hope that maybe just a few of those developers peeking in would pass their observations on to the rest of the development team and put more thought into the newbie experience. Linux has now reached a plateau of matureness that only indicated a great future.

---

### Post by DrMega on 2008-10-16
> **porchrat said:**
> LOL yea right.  With all the issues people have with ATI drivers you'd think ATI would create some sort of concrete guide for each distro with a step-by-step install guide that also lists the common problems encountered.  I know that it is generally regarded as the community's job by most companies, but I really hate that mentality.

There are hundreds of distros, no company is going pay someone to test drive each one and write up a custom installation guide for them.

---

### Post by RedRat on 2008-10-16
> **DrMega said:**
> There are hundreds of distros, no company is going pay someone to test drive each one and write up a custom installation guide for them.

Well there is no question that the many distros of Linux definitely stand in the way of it becoming a major OS, at lest on a par with Windows or Mac. You are right in that no company could possibly afford to test drive drivers or much of anything else. 

But the issue in my initial rant was that this was an update to Ubuntu that seemed to cause the problem, so the problem lies more at the feet of the Ubuntu development team, I think, than necessarily with the video card people. I agree with one of the others here who said that when a kernel update comes along, a warning ought to go out that you might need to recompile the video driver. Many newbies who are using Ubuntu for the first time would not know that they are installing an updated new kernel from synaptic update. 

All I am asking is that the development team take into consideration the new people who are coming into Ubuntu for the first time.

---

### Post by Keyper7 on 2008-10-16
RedRat, there's a major logic flaw in your posts: what you and other people who experienced problems when configuring video had are **bugs**. What you had to do to solve them are **workarounds**.

Bugs are, by definition, unexpected behavior. It's logically impossible to be prepared to something you don't expect. Last time I experienced a nasty bug with supposedbly user-friendly Vista, I had to open the command prompt and issue some lines to tweak the register. This is as far from newbie-friendly as it gets. And I don't blame Microsoft, what could they do? Prepare in advance for something that's not supposed to happen?

There's absolutely no garantee that the same bug will happen with everyone who uses the same video board (for example, your bug might be caused by a combination of video board and motherboard chipset). Likewise, there's no garantee that the same workaround will work for everyone who had the same bug.

In this situation, what useful info can Ubuntu give? Probably not much more than "Hey, this update might or might not work. It does not for some people. If it does not work for you, try this workaround that might or might not work. It works for some people at least..."

When bugs do not happen, Ubuntu is user friendly as it gets. I installed Hardy. In the first boot, a popup appeared and said that proprietary drivers were available. I clicked on the popup icon and a window appeared, with the nvidia driver listed with a checkbox. I checked the checkbox and the driver was installed. Asked me to reboot, I did and the next startup I had everything working, now with 3D acceleration. And until today, I had three or four kernel updates. All of them happened flawlessly and didn't bork anything.

You're just asking for too much. Your post essentially boils down to "Ubuntu should be **completely prepared** for **any bugs** that might happen during its usage, including those involving proprietary binary drivers over with Canonical has absolutely no control!" That's simply impossible.

---

### Post by Tamlynmac on 2008-10-17
I agree whole heartily with Keyper7.  
 

 > You're just asking for too much. Your post essentially boils down to "Ubuntu should be **completely prepared** for **any bugs** that might happen during its usage, including those involving proprietary binary drivers over with Canonical has absolutely no control!" That's simply impossible.
 

 The concept that Canonical is some how responsible for proprietary hardware drivers or could in any way resolve that issue is ludicrous.
 

 IMHO the real solution is three fold:
 
[LIST=1]
[*]Notify the hardware manufacturer 	and complain (not likely to solve the problem)
[*]Only purchase hardware that 	supports your OS of choice – I always spend time prior to 	purchase, investigating compatibility. One real good source is this 	forum.
[*]Write a driver and share it with 	the community. (I for one am not that person)
[/LIST]
 

 Somewhere on the forum I read a posting (getting old and can't remember where) that stated it might be a good idea to include a disclaimer as part of the installation - to advise installers of this issue and suggest they investigate hardware compatibility prior to continuing. Seems that may not be a bad idea.:-k

---

### Post by RedRat on 2008-10-17
Keyper7:
First off, you are using semantics (much like Microsoft does when a bug is turned into a feature), a rose by any other name is still a rose. For me it was unexpected behavior and thus it was a BUG. End of story!

Now I am fully aware about the developers dilemma about the myriad of boards and video cards out there. However, I would point out that my NVidia card seems to be fairly common among Linux users and works well. Be that as it may, I do not expect detailed warnings from the developers. But it sure would be nice if they said something like this: "A new kernel is being installed. Be aware that some video drivers might have to be re-installed or recompiled". At least I would not be taken by surprise and wondering what the hell happened and spend a couple of hours trying to recover. Again, I have a little bit of experience but consider some of the true newbies who are trying Ubuntu for the first time.

As to MS Vista or any other Windows version, I really am not even trying to make a comparison here, nor do I care to. Let's focus only on Ubuntu and Let MS take care of itself. 

As to your comment:"Hey, this update might or might not work. It does not for some people. If it does not work for you, try this workaround that might or might not work. It works for some people at least...". This type of extreme comment would certainly leave the newbie with very cold feet, heck even a somewhat experienced user might decide to let that download go. This is not a helpful comment to users.

I think your attitude that somehow no one is responsible for anything seems to permeate the developer community. If Linux and its distros are to survive, someone somewhere must take responsibility for what they put out there. What Canonical ought to do is to package some kind of warning when new kernels are installed and the impact that might have on drivers so that users can be somewhat prepared.

Tamlynmac and Keyper7:
Both of you  take the usergroup approach that I see in that you take my position and then turn it into an extreme statement. Your comment: 
"You're just asking for too much. Your post essentially boils down to "Ubuntu should be completely prepared for any bugs that might happen during its usage, including those involving proprietary binary drivers over with Canonical has absolutely no control!" That's simply impossible." 

This is an example of what I mean by removing ANY responsibility from anyone. Look, even if I took your advice to develop a driver of my own (which is beyond my inclination and ability) I should be the person to take some responsibility for that program. I am sorry, but shrugging my shoulders and telling a user that just had their system wiped out or crashed that "Gee, you can't expect me to be aware of everything that can go wrong" just doesn't cut it. If you decide to put something out there, whether it is free or costs money, does put responsibility on your shoulders that the program ought to work and not mess up a system. If I take your arguments to their logical extreme, what if Ford or GM merely shrugged their shoulders when your gas tank blew up and said "Gee, were sorry the guy died, but you can't expect us to plan for everything". I don't think that would fly very far. 

Now I am not just pointing a finger at Linux here, Microsoft and other Windows and Mac software developers certainly deserve some blame too, they don't write perfect programs either.

---

### Post by Modplanman on 2008-10-17
RedRat:

He did not use semantics at all. He stated quite clearly the flaw in your argument, being that they are bugs, ergo are unexpected behaviour, meaning Ubuntu developers cannot account for it. This does not mean responsibility is being absolved, just the acknowledgement that they have finite developers with finite time and are dwarfed by the possible number of configurations, and subsequently cannot entirely account for a Hell of a lot of possible conflicts, crashes and general craziness.

What Nvidia driver do you use? If it's the proprietary one, then there's even less chance, and does have warnings stating that the use of a proprietary driver means they cannot properly test or discover bugs as well as they would normally, let alone address them. In this case, it IS Nvidias responsibility, as they provide a closed driver that Canonical and none of the others can properly view or change as and when problems arise. When Nvidia provides the driver (a closed one at that), they inevitably shoulder the responsibility. Canonical and no one else can be entirely expected to take that responsibility, when they don't have say or even ability to change the initial driver creation.

I perfectly agree that responsibility shouldn't be dropped, but you have to properly figure out who is responsible in the first place. In the case you are using the proprietary driver, then it falls on the card vendor. If it is community developed, then the responsibility is share amongst several people.

---

### Post by jerome1232 on 2008-10-17
put simply, you are complaining about a 'flaw' in Nvidia's/ATI's driver and blaming it on Ubuntu, There is a warning where it belongs, when you install the driver that might cause these problems. (whether it be via restricted driver manager or envyng or off of Nvidia's/ATI's website)

That's what I get out of it.

---

### Post by RedRat on 2008-10-17
> **Modplanman said:**
> RedRat:

He did not use semantics at all. He stated quite clearly the flaw in your argument, being that they are bugs, ergo are unexpected behaviour, meaning Ubuntu developers cannot account for it. This does not mean responsibility is being absolved, just the acknowledgement that they have finite developers with finite time and are dwarfed by the possible number of configurations, and subsequently cannot entirely account for a Hell of a lot of possible conflicts, crashes and general craziness.

What Nvidia driver do you use? If it's the proprietary one, then there's even less chance, and does have warnings stating that the use of a proprietary driver means they cannot properly test or discover bugs as well as they would normally, let alone address them. In this case, it IS Nvidias responsibility, as they provide a closed driver that Canonical and none of the others can properly view or change as and when problems arise. When Nvidia provides the driver (a closed one at that), they inevitably shoulder the responsibility. Canonical and no one else can be entirely expected to take that responsibility, when they don't have say or even ability to change the initial driver creation.

I perfectly agree that responsibility shouldn't be dropped, but you have to properly figure out who is responsible in the first place. In the case you are using the proprietary driver, then it falls on the card vendor. If it is community developed, then the responsibility is share amongst several people.

I stand by original comment, call it a "workaround" or "bug", a rose by any other name....

If you look carefully at what I wrote, I did not imply or mean that Canonical ought to fall on its sword! What I would like to see is a polite warning that warns the user downloading THEIR update to expect that you might have to recompile/re-install some drivers. Look, if you are pushing something out there, take some responsibility for crying out loud. 

What I see here among the Ubuntu/Linux community nothing more than finger pointing at everyone for fault--basically it is nothing more than a circle jerk. What is the poor hapless user to do?? Consider I am directing my rant at developers for the newbies. The new user who is coming to Linux for the first time doesn't have a clue to whom to complain to or even how to complain. I am merely asking those here, who might be developers or know the developers, to take some time and try to smooth out these upgrades for the newbies. Linux is an awesome system and deserves to succeed, but in order to do that you need to bring far more onboard.

---

### Post by jerome1232 on 2008-10-17
Like that?

---

### Post by Modplanman on 2008-10-17
"I stand by original comment, call it a "workaround" or "bug", a rose by any other name...."?

I don't even understand what you're getting at with this. He is not renaming it, when a problem arises it is known as a bug (in every bit of software, not just in Ubuntu), and a workaround is exactly what you do when you try to address that problem (or one way of addressing it), by working around it, hence workaround. It is not a rose by another name, because he's not renaming it.

It is Nividias responsibility, as it is THEIR driver that is the problem. In case you don't get it, Ubuntu is open source. This means all (or as much as they can) of the code they include is open to everyone to see and change. Nvidias driver is proprietary - no one else can see it or change it. There is no reponsibility with the Ubuntu development community or Canonical because there is nothing they can do about it in the first place. The majority of the development is done openly, where it is generally much easier to see and address and bugs and spot potential conflicts.

Anything that is prorpietary is a thorn in their side, and is something they are nowhere near adequately able to address properly because of the nature of the development model. In the proprietary model, responsibiliy falls on the original vendor, NOT on the passers by. Nvidia is the original vendor, they have sole ability to see and edit the code, ergo the responsibility falls on them for development, testing and subsequently any problems that arise. Ubuntu cannot do anything about what it does not have control over.

"What is the poor hapless user to do?? "

File a bug report, blame the one reponsible (Nvidia) and send an email (to Nvidia), not make ill informed and rash rants with little background detail. 

"to take some time and try to smooth out these upgrades for the newbies. Linux is an awesome system and deserves to succeed, but in order to do that you need to bring far more onboard"

Did you miss the memo? That's the entire point of Ubuntu. And so far, it's been doing a pretty good job. Your issue so far is down to Nvidia, not them, ergo this is not an issue with Linux or Ubuntu.

---

### Post by RedRat on 2008-10-17
> **jerome1232 said:**
> Like that?

Hate to rain on your parade but that never came up after the update. It was pretty obvious to me that my video driver was trashed so I eventually struggled to get to my Hardware drivers, try that in 800x600 resolution that was supposed to 1280x1024 and could not click on the System in my menu because of the other programs I had in the bar. Eventually by removing them, I got to the system menu. When I tried to install the nvidia driver, it would not install as your thumbnail shows. Clicking on activating the nvidia driver (the one that comes with Ubuntu) did no good. All attempts to get to a decent screen resolution failed. Eventually, through help provided here by kind souls, I was able to get the envyng drivers installed and the system was ok.

But again, you seem to be missing my point. I have a bit of experience but still consider myself a newbie at Ubuntu. My point is what would have happened to a complete newbie, some don't even know of this forum!

Yeah, sure I can point my finger at Nvidia or Envy and blame them, but I could probably have back a few hours of my life had I at least would have been warned that this MIGHT HAPPEN.

---

### Post by Tamlynmac on 2008-10-17
RedRat
> Now I am not just pointing a finger at Linux here, Microsoft and other Windows and Mac software developers certainly deserve some blame too, they don't write perfect programs either.

**Theirs aren't free. **
I agree that if I paid hundreds of $ for an OS and/or software packages they should function OOTB. Ubuntu is free and I personally don't expect perfection from something that I didn't pay for. However, Ubuntu has actually modified that opinion, as it performs perfectly on all 5 of our systems and all other installs I've done. Complaining because it may not function on certain hardware or for just about any other reason indicates a sense of entitlement - as if I paid for it and should get what I paid for.

We must remember that OSS is free and complaining solves nothing. Better to submit bug reports or ideas for enhancement that might help in improving the software.

You indicate "someone must take responsibility". The OSS community didn't sell you anything or ask you to join anything. I don't believe they recruited you or even called and asked you to install their OS. The responsibility for assuring hardware compatibility lies with the installer - period. When I placed the Ubuntu disk into my machine and said install, I immediately became the responsible party. I would not expect a Linux software package to work on a system designed for a different OS. Many of the Ubuntu installs I've done required modifying certain hardware to assure success. No different than when the system states it's "Vista Ready". When I used to purchase Windows software for my systems - I always "read the box" to assure my system met the minimum requirements. What's different? It's my obligation as the installer of the software to assure system compatibility - not the programmer or the company that sells it or in this case gives it away.

As I indicated in my previous post, I'm certainly not the person to write drivers either. So I must depend on someone else. Should I hold that individual responsible if they were to write a driver for everyone (for free) and it didn't work on all my systems. Not in my world.

If you want a company to take full responsibility for installation of an OS, then I suggest you purchase a system that comes with that OS pre-installed.

---

### Post by RedRat on 2008-10-17
Modplanman wrote:
"I don't even understand what you're getting at with this. He is not renaming it, when a problem arises it is known as a bug (in every bit of software, not just in Ubuntu), and a workaround is exactly what you do when you try to address that problem (or one way of addressing it), by working around it, hence workaround. It is not a rose by another name, because he's not renaming it."
---------------
In common English parlance a workaround is a set of instruction of what to do when a problem arises. Where exactly was there a "workaround" when my system was borked? All I knew was that when I rebooted my video resolution was trash. To me the update was a Bug. Further, the video driver that comes with Ubuntu was clearly not working, I could not get out of 800x600. Please try to understand, I am coming at this rant from the standpoint of a newbie, not an experienced user or even a moderately experienced user. 
-----------------------
You say:"File a bug report, blame the one reponsible (Nvidia) and send an email (to Nvidia), not make ill informed and rash rants with little background detail." 

And how exactly is a newbie supposed to do this? Yeah, you know how. You and I both are aware of this forum for help. Again, I am coming at this from the standpoint of the newbie, not from your experienced user position. Many newbies don't even know about this forum yet. 
----------------------------------
Your write: "Did you miss the memo? That's the entire point of Ubuntu. And so far, it's been doing a pretty good job. Your issue so far is down to Nvidia, not them, ergo this is not an issue with Linux or Ubuntu."

This is exactly the attitude I am ranting against. It's nobody's fault. It is always the other guy. It is not an issue with Linux or Ubuntu. What are expecting that Ubuntu and Linux are being developed in some sort of vacuum? That every once and awhile the developers condescend to come down from Olympus on High and drop a bon-mot on us lowly peons with computers??? I am afraid that your argument sounds like my analogy to Ford and GM, cars and operating systems are designed to operate in the real world.

---

### Post by jerome1232 on 2008-10-17
But if you choose to add a turbo charger to your ford, then ford 'upgrades' everyones engine and the new engine isn't compatible with the turbo charger, is ford to blame?  Especially since the company that makes the turbo charger won't work with ford to make them compatible.

edit: A better example may be that it turns out you just have to drill a few new mount holes into the turbo charger and reapply the gasket when you purchase a new engine. But ford didn't warn you that buying a new engine might require some modifications on the engine accessories. The turbo charger had a warning on it, but your mad because the engine didn't.

---

### Post by RedRat on 2008-10-17
Tamlynmac wrote:
"You indicate "someone must take responsibility". The OSS community didn't sell you anything or ask you to join anything. I don't believe they recruited you or even called and asked you to install their OS. The responsibility for assuring hardware compatibility lies with the installer - period. .... It's my obligation as the installer of the software to assure system compatibility - not the programmer or the company that sells it or in this case gives it away.

As I indicated in my previous post, I'm certainly not the person to write drivers either. So I must depend on someone else. Should I hold that individual responsible if they were to write a driver for everyone (for free) and it didn't work on all my systems. Not in my world."
-------------------------
So because I give something away free I am now absolved from all that happens after ward. An interesting concept. Try that in business and see how far you get. If I give away free a defective item to a customer and he/she uses it and gets injured or killed, just go ahead and try that defense in court and see how are you would get. Give free food or candy away and if someone becomes ill, you would be on the spot for violating a health code. Just because something is given away for free, does not absolve the giver from SOME RESPONSIBILITY. 

Look, I am not asking for NVidia, Canonical, some obscure developer working away in his/her basement to fall on their swords here. What would it take for whoever is pushing out these updates to say that "you are getting a new kernel here, you might have to re-install new drivers". I don't think I am asking too much here.

---

### Post by RedRat on 2008-10-17
> **jerome1232 said:**
> But if you choose to add a turbo charger to your ford, then ford 'upgrades' everyones engine and the new engine isn't compatible with the turbo charger, is ford to blame?  Especially since the company that makes the turbo charger won't work with ford to make them compatible.

So basically you are saying here that Ubuntu and NVidia are not speaking to each other?? That Ubuntu is not even aware of NVidia's existence? Come on now. At least the company that is attempting to make a turbo-charger for a Ford or GM engine can open the engine and presumably do the due-diligence to calculate stresses and other engineering necessities to make a reasonable attempt at a turbo charger. NVidia has been around long enough and so has Ubuntu and Linux to have moved beyond the experimental stage.

---

### Post by jerome1232 on 2008-10-17
The Linux Kernel is open source, Nvidia can open the hood.

I mean I agree with you that it needs work, but 3d graphics IS actually a fairly new arena for Linux. Usually failures are on the monitor detection side I have noticed. I'm not sure if this is Xorg, or Nvidia that is responsible.

---

### Post by RedRat on 2008-10-17
> **jerome1232 said:**
> The Linux Kernel is open source, Nvidia can open the hood.

I mean I agree with you that it needs work, but 3d graphics IS actually a fairly new arena for Linux. Usually failures are on the monitor detection side I have noticed. I'm not sure if this is Xorg, or Nvidia that is responsible.

I can tell you this when I ran under the 800x600 video resolution, which I presume to be a basic mode for Ubuntu, I could not even get Ubuntu to load a generic nVidia driver that comes with Ubuntu. As to detection, I have a Samsung Syncmaster 191T that is now about 4 years or more old. Ubuntu does not seem to be able to detect it. It was only after reinstalling the nVidia driver via envyng that I was able to get stuff written to my Xorg.conf file. It seems that there have been changed in writing the xorg.conf file and its interpretation. I have seen other references to that here in the forums and in the newsgroups. Now the writing of stuff to xorg.conf is an ubuntu operation and not an NVidia one.

---

### Post by SteveNorman on 2008-10-18
I think if your going to do linux a certain degree of work is always going to be required. Remember that the focus of developers is more in line with new hardware versus old hardware. Every year there is a ton of new hardware and software being developed. Codec and driver writers are trying to keep up with these trends first and foremost.They are also in many cases risking being jailed or fined by skirting legal grey areas to get a piece circuit board to come to life. And if a peice of old hardware gets lost in the mix then your SOL.

   Load up gentoo and get it running to see just how much work the Ubuntu Team has done. gentoo is like operating system boot camp. You pretty much have to write all your own config files,,you have to know all your hardware, yada yada. With Ubuntu a whole lot of the struggle just to get the kernal so that it will boot has been knocked out in a very successful way. If you really think about it this way: Linux in its pure form has been developed by a community versus a corporation. It has been almost all volunteer for years. The trade off is that you have to learn a lot about operating systems to run linux effectively. If you get your graphics configured you will know a lot about the xorg.conf file that you didnt know before. Then you will see someone with the same problem you had and may provide the answer to their problem. Now you are a contributing member of that corporation free community. After many years you may know so much about operating systems that you start writing drivers yourself. If you contribute them to the community you have just become one of the linux developers. 

With freedom( beer and speech) comes responsibility, confusion, and hard work. There are already 2 operating systems that hold their users hands. They have held their users hands so tight they cant do anything but click on pretty pictures to get the computer to do what they want.If that breaks there screwed.

 Ubuntu is already headed in that direction, which is good and bad depending on how you want to look at it. But its better to do the leg work yourself, learn your OS and free yourself from the need to have your hand held by a corporation that does not have your best interests in mind.

---

### Post by Keyper7 on 2008-10-18
> First off, you are using semantics (much like Microsoft does when a bug is turned into a feature), a rose by any other name is still a rose. For me it was unexpected behavior and thus it was a BUG. End of story!

**That's exactly my point.** It's a bug. It's unexpected. How can you give warning about something you don't expect to happen?

> Now I am fully aware about the developers dilemma about the myriad of boards and video cards out there. However, I would point out that my NVidia card seems to be fairly common among Linux users and works well. Be that as it may, I do not expect detailed warnings from the developers. But it sure would be nice if they said something like this: "A new kernel is being installed. Be aware that some video drivers might have to be re-installed or recompiled".

**They are not supposed to be reinstalled or recompiled.** That's where the flaw in your logic is. Take a peek at Launchpad. For *each and every* Ubuntu package, there is at least one bug reported. And thousands of them are not considered solved yet. So, by your logic, for 90% of the software used in Ubuntu, the system should deliver a message to the user saying "Hey, the bugs X and Y about this software have been reported, so they might happen to you. Just to warn ya."

> As to your comment:"Hey, this update might or might not work. It does not for some people. If it does not work for you, try this workaround that might or might not work. It works for some people at least...". This type of extreme comment would certainly leave the newbie with very cold feet, heck even a somewhat experienced user might decide to let that download go. This is not a helpful comment to users.

Sigh... **That's exactly my point.** I wrote this ridiculously exaggerated warning example precisely to show how flawed your reasoning is. If you didn't get it, take your own example: "A new kernel is being installed. Be aware that some video drivers might have to be re-installed or recompiled.". What the heck is a kernel? What the heck is compiling? Is *this* your concept of newbie-friendly?

> I think your attitude that somehow no one is responsible for anything seems to permeate the developer community. If Linux and its distros are to survive, someone somewhere must take responsibility for what they put out there. What Canonical ought to do is to package some kind of warning when new kernels are installed and the impact that might have on drivers so that users can be somewhat prepared.

**This has nothing to do with who is responsible for what.** You and a lot of other people in this thread seem to be making this mistake. The main flaw in your logic is: if you are going to issue a warning about kernel updates and video drivers, you might as well issue warning about *each and every bug* that has been reported against Ubuntu software and is not considered solved yet.

> Tamlynmac and Keyper7:
Both of you  take the usergroup approach that I see in that you take my position and then turn it into an extreme statement. Your comment: 
"You're just asking for too much. Your post essentially boils down to "Ubuntu should be completely prepared for any bugs that might happen during its usage, including those involving proprietary binary drivers over with Canonical has absolutely no control!" That's simply impossible." 

This is an example of what I mean by removing ANY responsibility from anyone.

Why? I'm not removing responsibility from anyone, just using common sense: if the developers had enough insight about a bug to give an useful warning to the user, it is smarter to *solve* the bug instead of warning about it. If they don't have enough insight about a bug, a warning would be useless: they would not be sure if they bug will happen and they will not be sure if the workaround will work.

> Look, even if I took your advice to develop a driver of my own (which is beyond my inclination and ability)

What? When did I or Tamlynmac suggested that?

> I should be the person to take some responsibility for that program. I am sorry, but shrugging my shoulders and telling a user that just had their system wiped out or crashed that "Gee, you can't expect me to be aware of everything that can go wrong" just doesn't cut it. If you decide to put something out there, whether it is free or costs money, does put responsibility on your shoulders that the program ought to work and not mess up a system.

Fine. Then give me an example. **One single example** of a software that is completely bug-free or always issued warnings about each and every bug that could happen.

> If I take your arguments to their logical extreme, what if Ford or GM merely shrugged their shoulders when your gas tank blew up and said "Gee, were sorry the guy died, but you can't expect us to plan for everything". I don't think that would fly very far.

Nice example, it shows precisely where the flaw in your logic is. Suppose this actually happens. A guy buys a card from Ford and eventually the gas tank blows up and he dies. An inciddent of such proportions is obviously not expected by Ford, they're not psychopats. The family would have the right to complain and sue (demand the bug to be fixed), but would it be reasonable if they went to Ford and said that there should be a warning written in the car, saying that the gas tank might or might not explode and suggesting to run away from the car if the driver hears something strange?

> Now I am not just pointing a finger at Linux here, Microsoft and other Windows and Mac software developers certainly deserve some blame too, they don't write perfect programs either.

Like I said before, who is to blame has nothing to do with this discussion.

The responsibility of the developers is to fix bugs, not to give half-assed and possibly misleading workarounds to them. Who said that for everyone who has the same board recompiling the driver will be enough? Perhaps a less simple solution might suffice or a more simple solution might be necessary.

---

### Post by ByteJuggler on 2008-10-18
Guys I'm worried that some bad feelings/ill will is being unnecesarily generated here by the continuous arguing.  

So, can I suggest that we all agree to each do our best to make Ubuntu as good as it can possibly be, in whatever way that is, whether it is by reporting bugs (where devs will see them, e.g. on project mailing lists, bug trackers etc), doing some testing ourselves and QA'ing new releases, or by helping solve problems when unintended bugs do slip through the net (which will unfortunately happen on occasion.)  After all, no one working on Ubuntu (or any of the projects it relies on) *wants* to write buggy code or break anyone else's system!  

Intrepid Ibex is not far from release, and I'm downloading the beta to do some testing on the 3 machines in our house to help ensure it will work on (at least) machines similar to these 3.

---

### Post by RedRat on 2008-10-18
> Keyper7 wrote:
"They are not supposed to be reinstalled or recompiled. That's where the flaw in your logic is. Take a peek at Launchpad. For each and every Ubuntu package, there is at least one bug reported. And thousands of them are not considered solved yet. So, by your logic, for 90% of the software used in Ubuntu, the system should deliver a message to the user saying "Hey, the bugs X and Y about this software have been reported, so they might happen to you. Just to warn ya.""
---------------------
Got a newsflash for you kiddo, I could not get any recognition that either the nVidia driver was even present. I could not write to the xorg.conf file by calling nvidia-settings, it refused to run. I was using the nvidia-envy driver before. I could not get anything enabled! My only recourse was to go to the terminal and run envyng which removed all the old stuff and downloaded and re-installed the driver. Remember I am coming at this as a newbie, luckily not just a beginner. By your definition then, it was a bug. Got that.


> Keyper7 wrote:
"Why? I'm not removing responsibility from anyone, just using common sense: if the developers had enough insight about a bug to give an useful warning to the user, it is smarter to solve the bug instead of warning about it. If they don't have enough insight about a bug, a warning would be useless: they would not be sure if they bug will happen and they will not be sure if the workaround will work."
-----------------------------
What!!! It is smarter to not warn about a bug??? It's smarter to solve it?? Hey I think you have the cart before the horse here. Let's use your example about Ford and exploding gas tanks (BTW, that is real and Ford did end up paying millions of dollars to about 6 victims' families/survivors, they stopped making the Ford pinto for that reason). Ford had two choices after they discovered this flaw, 1) warn the buyer that their car might explode if rear-ended, 2) stop making the car and/or fix the gas tank. They chose the latter, stop making the car. Now they chose to stop making the car because the Pinto had received such bad publicity that they couldn't give them away so option #1 was untenable. Did Ford stop making cars? No, but they learned from their mistakes. Since that time many years ago, all manufacturers have car recalls when car safety is involved, but warnings go out. 

As to software, repairing bugs can be time consuming particularly in a volunteer community. The Linux community has developers working on their own basically donating to the cause of open source programs. I don't expect them to be able to devote full time effort to solving each and every bug. Microsoft, Apple, and Red Hat do have paid staff to do this and even they are slow as molasses sometimes. If you are aware of a bug, because of this lead time, a warning ought to go out. 


Look keep in mind where I am coming from in this rant. I am coming at it from the standpoint of the absolute new user, the NEWBIE! Many of you here who have defended Linux, as I said basically shrugging your shoulders and saying it your fault the user, are like proselytizers for a religion. No matter what happens the religious belief is true and its all your fault. What I am asking, do you want to bring more people into the Linux community or do you want to retire to your mountain top and feel smug about your accomplishment?

Ubuntu is now a mature OS, it can compete easily against Windows and the Mac, it has basically what it takes to succeed. It has reached a plateau where others with only a little computer knowledge can use it. It is time that it starts to bring more into the fold. I am merely pointing out that it needs to be a bit more user friendly for the "unenlightened" ones.

---

### Post by SteveNorman on 2008-10-18
> **RedRat said:**
> . What I am asking, do you want to bring more people into the Linux community or do you want to retire to your mountain top and feel smug about your accomplishment?

Ubuntu is now a mature OS, it can compete easily against Windows and the Mac, it has basically what it takes to succeed. It has reached a plateau where others with only a little computer knowledge can use it. It is time that it starts to bring more into the fold. I am merely pointing out that it needs to be a bit more user friendly for the "unenlightened" ones.

my point was that it IS more user friendly,,and is getting that way every release. Ubuntu is already an amazing thing if you have used other distros , or have tried linux in the past. Also commercial support is available through canonical if someone needs more than what is available via google and this forum

---

### Post by Modplanman on 2008-10-18
> "Got a newsflash for you kiddo, I could not get any recognition that either the nVidia driver was even present. I could not write to the xorg.conf file by calling nvidia-settings, it refused to run. I was using the nvidia-envy driver before. I could not get anything enabled! My only recourse was to go to the terminal and run envyng which removed all the old stuff and downloaded and re-installed the driver. Remember I am coming at this as a newbie, luckily not just a beginner. By your definition then, it was a bug. Got that."

What's your ******* point? A bug is a bug. Because you had a bad bug we have to agree with you automatically?

Newsflash kiddo. I had a bug. It meant my wireless internet adapter couldn't work, and currently the driver available for my onboard grapihcs lacks 3d support. I was once a newbie.

You know what I did?

Realised that **** happens and got on with my life. I realised that not everything can be accounted for, realised I would need to pull my socks up and get working, and did so. By your flawed logic, everything should have a warning message, because potentially ANYTHING can cause a bug, crash or something else. By your logic, the user should be scared shitless to do updates because they're scared that something will break. Every time they go to update "WARNING, DANGER WILL ROBINSON, YOUR SYSTEM MIGHT CRAP UP".

Every action has a reaction. Every time you put that warning up, you're making users wary and scared of updating, which has several knock on effects. They miss out on what might actually be fixes, not bug causes, they miss out on new functionality, they miss out on updates that might stop their system being compromised by some virus or 13 year old sat along in their room. 

This completely forgets the fact that 95% of the time it would be completely unnecessary. This completely forgets that 95% of the time, it would be more a hindrance than a help. When something breaks, rarely is the cause genuinely knowable from the user end, so making said warnings either useless or pointing the user in the wrong direction, meaning it would have to be such a general warning that if you have a bunch of updates in one go, it effectively makes it no less easier to diagnose any problem. Not to mention I seriously doubt that people are that idiotic or have such a short term memory as to forget when and what they're last update was, or to realise that after said update, something in the system had seriously ****** up when their display doesn't work. Ergo, making the warning pointless. There is little to nothing you can do in anticipation from a normal user end.

Also, see this:

[http://arstechnica.com/news.ars/post/20080923-study-confirms-users-are-idiots.html](http://arstechnica.com/news.ars/post/20080923-study-confirms-users-are-idiots.html)

> follow-up questions revealed that the students seemed to find any dialog box a distraction from their assigned task; nearly half said that all they cared about was getting rid of these dialogs. The results suggest that a familiarity with Windows dialogs have bred a degree of contempt and that users simply don't care what the boxes say anymore.



---

### Post by cariboo on 2008-10-19
I see a lot of post here blaming Nvidia, ATI, Broadcom et al for poor drivers. Has anybody actualy been able to purchase an Nvidia branded video card or a Broadcom branded wireless card? I'm not even sure ATI builds thier own video cards any more. If all the video cards were exactly the same, what would make us buy one brand over the other. The video adapter manufacurers have to be doing something to differentiate themselves from each other. We should not only be asking Nvidia and ATI to improve their drivers, but he card manufacturers have to shoulder some of the blame for video problems too.

Jim

---

### Post by 3rdalbum on 2008-10-19
No, no, no!

This is not the time or the place for a flamewar.

[COLOR="Red"]A few things to point out to the participants of the discussion:[/COLOR]

It's not Nvidia's fault for the kernel updates stopping the driver from working. The kernel is not ABI-fixed, for various reasons, so the old driver will not work with a new kernel. It's not an Nvidia bug, it's expected behaviour for people who know approximately how Linux works.

It's also not Ubuntu's fault. If you use the Nvidia driver that's in the repositories, that is linked against the kernel that Ubuntu provides. If Ubuntu updates its kernel, it also updates the Nvidia driver package. Installing the Nvidia driver using Envy will *remove* Ubuntu's Nvidia driver package, causing it NOT to be updated when the kernel updates! So it's not Ubuntu's responsibility, because if you do things the Ubuntu way, you do not run into trouble.

Dell has written a small utility called DKMS. When it is run after a kernel update, it will relink your existing drivers to the new kernel (or in the case of open-source drivers, it will recompile them). From what I've heard, Ubuntu Intrepid should ship with a fully-integrated DKMS, so new kernel installations will automatically trigger DKMS for any kernel modules that Ubuntu has not automatically upgraded.

I agree that the kernel-updates-breaking-locally-installed-kernel-modules problem is something that should be fixed, but it doesn't need to be fixed by the use of warnings of "This kernel update could break your drivers". The Ubuntu devs are already on the case. In the meanwhile, either use Ubuntu's own Nvidia packages, or manually reinstall your drivers after a kernel update.

---

### Post by fluxlizard on 2008-10-19
Personally, I think that ubuntu shouldn't touch the kernel or hardware drivers between releases- hardy should use the same kernel and drivers from day one until the day it dies. Releases are only 6 months apart and come on- who ever had a security problem in the real world because their kernel or hardware drivers weren't the latest?

It would solve all these problems...

On a similar note- have you guys with hardware problems ever simply tried another distro of linux? Hardware difficult in one often is simple in another...

---

### Post by SteveNorman on 2008-10-19
> **fluxlizard said:**
> 

On a similar note- have you guys with hardware problems ever simply tried another distro of linux? Hardware difficult in one often is simple in another...

I always keep another distro installed so that if I break one I have another that works so I can use to google the fix. Also its better for learning to have more than one distro running.

---

### Post by Keyper7 on 2008-10-19
> **fluxlizard said:**
> Personally, I think that ubuntu shouldn't touch the kernel or hardware drivers between releases- hardy should use the same kernel and drivers from day one until the day it dies. Releases are only 6 months apart and come on- who ever had a security problem in the real world because their kernel or hardware drivers weren't the latest?

You do have a point: usually such higher security concerns are more for servers than for Desktops. On the other hand, it were kernel updates that fixed really nasty bugs (lockups and freezes) during the first days of Hardy.

---

### Post by cariboo on 2008-10-19
What about a kernel that bricks a piece of hardware like kernel 2.6.27-5 did with the e1000e intel nic hardware. Are you saying that people should have to put up with something like that for 6 months?

Jim

---

### Post by fluxlizard on 2008-10-19
> What about a kernel that bricks a piece of hardware like kernel 2.6.27-5 did with the e1000e intel nic hardware. Are you saying that people should have to put up with something like that for 6 months?

Nah, but don't use kernels just released a few weeks ago. Give them a few months to make sure they are safe before making them part of the next ubuntu. Problem solved.

---

