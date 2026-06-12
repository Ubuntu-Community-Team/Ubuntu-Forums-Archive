---
title: "Preparing my final pitch to the devs regarding the non-pae kernel"
date: 2012-03-10
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kansasnoob on 2012-03-10
Those who've been around for a while know I can be incredibly tenacious when it comes to design changes and development decisions that I disagree with. I guess it's a character flaw. 

Certainly I win sometimes and lose other times. I won the debate on keeping the option to change host-name in the live installer, but I lost the debate regarding the hidden initial boot menu in the live CD/DVD's.

Most notoriously I lost the debate regarding user confusion created by the presence of "Use Entire Disc" or "Use Entire Partition" buttons in the Maverick live installer which resulted in many users losing data and/or another existing OS :(

Now, on to the PAE-enabled kernel by default debate. To understand the debate you must first know about the Ubuntu Technical Boards decision:

[https://wiki.ubuntu.com/TechnicalBoard/TeamReports/11/December](https://wiki.ubuntu.com/TechnicalBoard/TeamReports/11/December)

Please take note of the highlighted section:

> Non-PAE kernel disposition

    Kernel team would like to drop non-PAE kernel soon
    TB members generally feel that (1) dropping the current default kernel is too much of a step, and (2) there is still a significant number of users which have non-PAE systems, based on Launchpad bug report data and an ubuntu-devel@ strawpoll
    Maintaining the extra flavour is not much extra work, and not comparable to e. g. the -ti-omap4 kernel which is an entirely separate source tree
    We need a way to prevent upgrades for non-PAE systems. Some options were mentioned:
        Add update-manager check to not offer the upgrade if PAE is not available

        Add libc6/linux preinst to abort the upgrade early if PAE is not available; that's not the best failure mode, but will prevent a safety net for users of apt-get dist-upgrade 

    Agreements:
        **[COLOR="Red"]Switch precise over to PAE kernel by default on i386; we retain the option to revert if it causes too much fallout (Colin)[/COLOR]**
        Drop non-PAE flavour in 12.10; this will give non-PAE systems another 5 years of life time, which is considered enough
        Further discuss upgrade strategy/checks 

So, while I'm not personally effected, I do think the fallout is significant enough to request this decision be reverted, and talking about it here first helps me prepare for the final push in hopes that I'm successful :)

My reasoning is this:

#1: Both pae and non-pae kernel versions are going to be supported throughout the 5 year Precise life cycle anyway, and those who desire a PAE-enabled kernel can easily install it post-installation.

#2: The only official methods to install non-pae Precise are:

(a) Install Lucid (10.04.4), install all available updates, then upgrade to Precise. Do note however this is not likely to work for Lubuntu.

(b) Install Oneiric (11.10), install all available updates, then upgrade to Precise. This should work for all official derivatives.

(c) Use the non-pae mini.iso, aka; netboot image, and then install the desired DE.

#3: I have a 5000kbps+ wired connection and any of the three above options are time consuming. Depending on which DE I use a mini.iso install takes about 1 hour and 20 minutes to 1 hour and 45 minutes to complete.

Either of the install + update + dist-upgrade options are even more time consuming, Oneiric more so since Lucid just had a point-release (10.04.4).

#4: More important than just time required is the fact that most, if not all, of those reporting the inability to install Precise due to the lack of pae support are laptop users many of whom lack access to a wired connection which is almost a requirement for a netboot/mini.iso install, and certainly preferable for dist-upgrades.

#5: It's nearly impossible to determine how many users are effected at this point but based on PM's, bug reports, mailing lists, etc. I'd put it at no less than 2 dozen .......... and remember we're just in Beta 1.

#6: David Henningsson has already produced the first "hybrid" Ubuntu image, and Greg Faith has reported on the Lubuntu mailing list that he's managed to create an Lubuntu hybrid image. While I applaud their efforts, how much difficulty does this present for the devs when it comes to squashing unrelated bugs? I'd think we can be sure that others will create their own hybrid images for other DE's and such.

#7: I understand that the Precise default download will be 64 bit anyway, and most hardware capable of 4GB+ RAM will run a 64 bit system so why default to the PAE kernel on i386? Isn't this a bit like rubbing salt in a wound?

#8: We're running out of time to revert ........ maybe we've already done so. It would be incredibly awkward to introduce such a change at 12.04.1!

**[COLOR="Red"]Time for a break[/COLOR]** :)

**[COLOR="Red"]Please do add any comments and/or concerns[/COLOR]**! Be brutal, I need to prepare for the big argument ;)

---

### Post by dino99 on 2012-03-10
you are doing an amazing work ;) tenacious for sure ;)
i'm sad you lost some debates on some points to make the wordings less confusing :( (maybe you dont have talked/debated with the right people, pm the boss)

about the pae choice , it should be usefull to:
- ask the user for checking its cpu before doing installation:  cat /proc/cpuinfo | grep -i PAE  , and giving a few lines explaining whats about.
- in case of non supported pae cpu, explain what to do as an alternative.

This should be a pre-message outside of ubiquity (as that one is a nightmare itself; hopes it will be fixed that time, but i still doubt as you have lost some debates (seems that some dev brains are closed))

---

### Post by sudodus on 2012-03-10
> [quote]switch precise over to pae kernel by default on i386; we retain the option to revert if it causes too much fallout (colin)
 drop non-pae flavour in 12.10; this will give non-pae systems another 5 years of life time, which is considered enough
 further discuss upgrade strategy/checks 
so, while i'm not personally effected, i do think the fallout is significant enough to request this decision be reverted, and talking about it here first helps me prepare for the final push in hopes that i'm successful [/quote]
+(more than one); I have an IBM thinkpad T41, and I am affected. I know many other people who are happy this kind of laptops, and it should definitely be straight-forward to install 12.10 into these thinkpads.

I am preparing for the new situation by testing Linux Mint Debian, which is a rolling edition with a non-pae kernel version to download, but I hope that Ubuntu won't force me to move.

---

### Post by kansasnoob on 2012-03-10
> **sudodus said:**
> +(more than one); I have an IBM thinkpad T41, and I am affected. I know many other people who are happy this kind of laptops, and it should definitely be straight-forward to install 12.10 into these thinkpads.

I am preparing for the new situation by testing Linux Mint Debian, which is a rolling edition with a non-pae kernel version to download, but I hope that Ubuntu won't force me to move.

I hear you, I just need to do my best to be sure the devs hear you too :)

---

### Post by kansasnoob on 2012-03-10
> **dino99 said:**
> you are doing an amazing work ;) tenacious for sure ;)
i'm sad you lost some debates on some points to make the wordings less confusing :( (maybe you dont have talked/debated with the right people, pm the boss)

about the pae choice , it should be usefull to:
- ask the user for checking its cpu before doing installation: cat /proc/cpuinfo , and giving a few lines explaining whats about.
- in case of non supported pae cpu, explain what to do as an alternative.

This should be a pre-message outside of ubiquity (as that one is a nightmare itself; hopes it will be fixed that time, but i still doubt as you have lost some debates (seems that some dev brains are closed))

When I look at my worst failures I try to think what I could have done different. Regarding the Maverick live installation I did try hard, obviously just not hard enough :(

But I did get it somewhat fixed in Natty, I'm still a bit disappointed that "use largest continuous free space" is not displayed but it's "good enough" I guess ;)

---

### Post by kansasnoob on 2012-03-10
Just BTW I already mentioned this to SABDFL in an unrelated conversation:

[https://lists.launchpad.net/unity-design/msg08539.html](https://lists.launchpad.net/unity-design/msg08539.html)

No reply that time, but I have been a bit of a nuisance :redface:

---

### Post by keithpeter on 2012-03-10
Hello kansasnoob and all

Good luck with this. 

If Ubuntu sticks with non-pae for i386 it will be 'selling point' over fedora/centos/Scientific Linux/RHEL who stopped supporting non-pae in their version 6

I gather the default desktop download from Canonical will be the 64 bit image. Makes sense (to me, but what do I know) that the i386 desktop image supports the largest range of hardware possible, but with information on how to enable the PAE kernel for those who can use it.

5 years should see those Centrino laptops into recycling...

---

### Post by kansasnoob on 2012-03-10
> **keithpeter said:**
> Hello kansasnoob and all

Good luck with this. 

If Ubuntu sticks with non-pae for i386 it will be 'selling point' over fedora/centos/Scientific Linux/RHEL who stopped supporting non-pae in their version 6

I gather the default desktop download from Canonical will be the 64 bit image. Makes sense (to me, but what do I know) that the i386 desktop image supports the largest range of hardware possible, but with information on how to enable the PAE kernel for those who can use it.

5 years should see those Centrino laptops into recycling...

Glad you mentioned 64 bit being the default DL :D

I have two 64 bit capable desktops but each has only 2 GB of RAM .............. plenty for everything I do, and I've tried 64 bit but it eats memory and runs slower :(

Someone, can't remember who, said something during that Maverick installer debacle to the effect of, "we want to convince users to toss Windows off of their computers, not toss their computers out of a window"!

But it's easy to enable PAE:

[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

I've tried it just out of curiosity and it still works. And my hardware runs pae just fine, but the kernel team is basically playing the part of playground bully here :(

---

### Post by kansasnoob on 2012-03-10
> **keithpeter said:**
> Hello kansasnoob and all

Good luck with this. 

If Ubuntu sticks with non-pae for i386 it will be 'selling point' over fedora/centos/Scientific Linux/RHEL who stopped supporting non-pae in their version 6

I gather the default desktop download from Canonical will be the 64 bit image. Makes sense (to me, but what do I know) that the i386 desktop image supports the largest range of hardware possible, but with information on how to enable the PAE kernel for those who can use it.

5 years should see those Centrino laptops into recycling...

BTW that became point #7, many thanks for reminding me of that :D

I'm going to push this sometime tomorrow, I have doubts it'll help, but I felt the need to try.

---

### Post by ronacc on 2012-03-10
I support you fully in this , even though I swore off 32 bit when the very first Athalon 64 was launched and have compromised only once since , I just couldn't resist an eeepc 4g when they came out . I think cutting themselves off from the huge number of old but still functional machines that won't digest PAE is a stupid move for Ubuntu .

---

### Post by keithpeter on 2012-03-10
Hello kansasnoob

The summary for Shuttleworth might be something like

"Propose shipping 12.04 i386 desktop with non-default PAE to maximise supported hardware.

Rationale

We are shipping 64 bit desktop CD as default. The i386 desktop CD will be used mainly by people with legacy hardware. 

Releasing a PAE Kernel on the i386 desktop CD will exclude owners of non-PAE hardware. They will face a distribution upgrade or use of minimal iso, both routes hard to explain, possibly having already used precious bandwidth to download a useless image.

Releasing i386 with non-PAE kernel would mean that owners of PAE capable hardware install an extra package after installation. This route is easier to explain, and involves little extra bandwidth use.

Path of least pain and most inclusion for new users suggests shipping i386 with non-PAE kernel. This will differentiate the Ubuntu offer from RHEL/Centos/Fedora"

---

### Post by kansasnoob on 2012-03-10
> **keithpeter said:**
> Hello kansasnoob

The summary for Shuttleworth might be something like

"Propose shipping 12.04 i386 desktop with non-default PAE to maximise supported hardware.

Rationale

We are shipping 64 bit desktop CD as default. The i386 desktop CD will be used mainly by people with legacy hardware. 

Releasing a PAE Kernel on the i386 desktop CD will exclude owners of non-PAE hardware. They will face a distribution upgrade or use of minimal iso, both routes hard to explain, possibly having already used precious bandwidth to download a useless image.

Releasing i386 with non-PAE kernel would mean that owners of PAE capable hardware install an extra package after installation. This route is easier to explain, and involves little extra bandwidth use.

Path of least pain and most inclusion for new users suggests shipping i386 with non-PAE kernel. This will differentiate the Ubuntu offer from RHEL/Centos/Fedora"

I'm not going to hit SABDFL with this one, instead I'm going full-court press at the Ubuntu Technical Board since this was their debacle.

The worst that can happen is they'll tell to shut up :)

I've been married three times so I'm used to hearing that.

---

### Post by keithpeter on 2012-03-10
> **kansasnoob said:**
> The worst that can happen is they'll tell to shut up :)

I've been married three times so I'm used to hearing that.

I'm a teacher so I do the telling :twisted:

(We listen first though)

Good luck

---

### Post by kansasnoob on 2012-03-10
> **ronacc said:**
> I support you fully in this , even though I swore off 32 bit when the very first Athalon 64 was launched and have compromised only once since , I just couldn't resist an eeepc 4g when they came out . I think cutting themselves off from the huge number of old but still functional machines that won't digest PAE is a stupid move for Ubuntu .

In deed! This doesn't directly effect me either, I even have an old PII that supports PAE (which is weird because it has 256 MB of RAM and I doubt it would support more than 512 MB). But there seem to be a lot of Pentium M laptops, both Thinkpad and Dell Latitude, laptops that work well with Ubuntu who'll be shut out by this change.

BTW, thanks, I'll now include the "Thinkpad and Dell Latitude" names in my push :)

That's the advantage to talking here first :guitar:

Alone we're just individuals but when we put our thoughts together we're a nation!

---

### Post by grahammechanical on 2012-03-10
Hi kansasnoob

How are you feeling?

I remember a bit of a debate about this  a few months ago and I did not understand what the fuss was about. And so it is with this thread. I did not find out what the discussion is about until I got to keith Peter's post about 30 mins ago, when he said this:

```
"Propose shipping 12.04 i386 desktop with non-default PAE to maximise supported hardware.
```

This should be a heading at the beginning of the presentation. Set out the proposition and then relate the arguments to support the proposition.

I am not saying this about you but  people in authority often do not see a need to explain things in ways that ordinary people can understand.  In this case you know what the subject is and those who you are trying to convince know what you are on about. But there is a wider audience who do not know the purpose of the discussion.

Consider this:

>  ubuntu-devel@ strawpoll

Are these people living in the world of the support forums? We are the ones that will have to give help to those coming on these forums wanting to know why Ubuntu 12.04 will not install on their old laptop.

We are already seeing posts from some wanting to install on old XP machines. Linux has a bit of a reputation for keeping old hardware working.

Give these people a good experience with Ubuntu and their next machine might be a Ubuntu laptop or tablet and not a Windows PC.

I am sorry but I just can't do quick replies.

Regards.

---

### Post by kansasnoob on 2012-03-10
> **keithpeter said:**
> I'm a teacher so I do the telling :twisted:

(We listen first though)

Good luck

It shows :)

One of my foster mothers was a high school English teacher, does it show?

She'd likely be revolted by how I write now. She was a nice lady.

---

### Post by kansasnoob on 2012-03-10
> **grahammechanical said:**
> Hi kansasnoob

How are you feeling?

I remember a bit of a debate about this  a few months ago and I did not understand what the fuss was about. And so it is with this thread. I did not find out what the discussion is about until I got to keith Peter's post about 30 mins ago, when he said this:

```
"Propose shipping 12.04 i386 desktop with non-default PAE to maximise supported hardware.
```

This should be a heading at the beginning of the presentation. Set out the proposition and then relate the arguments to support the proposition.

I am not saying this about you but  people in authority often do not see a need to explain things in ways that ordinary people can understand.  In this case you know what the subject is and those who you are trying to convince know what you are on about. But there is a wider audience who do not know the purpose of the discussion.

Consider this:



Are these people living in the world of the support forums? We are the ones that will have to give help to those coming on these forums wanting to know why Ubuntu 12.04 will not install on their old laptop.

We are already seeing posts from some wanting to install on old XP machines. Linux has a bit of a reputation for keeping old hardware working.

Give these people a good experience with Ubuntu and their next machine might be a Ubuntu laptop or tablet and not a Windows PC.

I am sorry but I just can't do quick replies.

Regards.

No one was more clueless than me:

[http://ubuntuforums.org/showthread.php?t=1919647](http://ubuntuforums.org/showthread.php?t=1919647)

I wouldn't even have noticed except for grub including the "pae" suffix.

But, largely because of that thread, people started PM'ing me so I got into the whole thing.

Now I'm in and as an old poker player I'm not going to fold this early in the game.

Better to play and lose than not to play at all ;)

---

### Post by grahammechanical on 2012-03-10
I found this link to a post on this forum. I do not know if my guess is correct but I think that this problem could be related.

[http://ubuntuforums.org/showthread.php?t=1937351](http://ubuntuforums.org/showthread.php?t=1937351)

Could we not get together a collection of forum posts (if they exist) showing that this is a genuine issue that is affecting would be users right now and will continue to do so in the future?

There is no restriction on who downloads Ubuntu and what they try to do with it. This brings with it the potential of  a bad experience with Ubuntu and that brings a bad reputation.

Regards.

Update: I am adding another post that I have found. They might not be related to the non-pae/pae iso issue but t**hey do show that there are people trying to put Ubuntu on old machines.**

[http://ubuntuforums.org/showthread.php?t=1938012](http://ubuntuforums.org/showthread.php?t=1938012)

Another old un - machine not user:

[http://ubuntuforums.org/showthread.php?t=1938438](http://ubuntuforums.org/showthread.php?t=1938438)

How many devs are trying to put Ubuntu on old machines? The resources of this forum might provide a better straw poll then the dev straw poll.

---

### Post by ronacc on 2012-03-10
Being an old geezer I hang out with mostly old geezers , many of them have older but perfectly adequate desktops and laptops that they are unwilling to toss as long as they are working . They do not put huge demands on their machines , email , net surfing and maybe facetime with the grandkids . They are mostly NOT geeks and handling anything beyound  put the cd in and click install is going to chase them away from Ubuntu . The hardware probing in ubiquity can surely be adjusted to recognise a non pae cpu and install the correct kernel . The major problem seems to be that the kernel devs seem to be unwilling to continue supporting the non pae kernel so it seems that what will decide the matter is a command decision and we all know where that comes from.I certainly hope Mark can be convinced that abandoning the non pae kernel will hurt Ubuntu's chances with a large and relatively untapped "market" .

---

### Post by kansasnoob on 2012-03-10
> **grahammechanical said:**
> I found this link to a post on this forum. I do not know if my guess is correct but I think that this problem could be related.

[http://ubuntuforums.org/showthread.php?t=1937351](http://ubuntuforums.org/showthread.php?t=1937351)

Could we not get together a collection of forum posts (if they exist) showing that this is a genuine issue that is affecting would be users right now and will continue to do so in the future?

There is no restriction on who downloads Ubuntu and what they try to do with it. This brings with it the potential of  a bad experience with Ubuntu and that brings a bad reputation.

Regards.

Oneiric would not have been effected.

---

### Post by kansasnoob on 2012-03-10
> **ronacc said:**
> Being an old geezer I hang out with mostly old geezers , many of them have older but perfectly adequate desktops and laptops that they are unwilling to toss as long as they are working . They do not put huge demands on their machines , email , net surfing and maybe facetime with the grandkids . They are mostly NOT geeks and handling anything beyound  put the cd in and click install is going to chase them away from Ubuntu . The hardware probing in ubiquity can surely be adjusted to recognise a non pae cpu and install the correct kernel . The major problem seems to be that the kernel devs seem to be unwilling to continue supporting the non pae kernel so it seems that what will decide the matter is a command decision and we all know where that comes from.I certainly hope Mark can be convinced that abandoning the non pae kernel will hurt Ubuntu's chances with a large and relatively untapped "market" .

Same boat ............ both geezers :D

In my case most of my fellow oldsters just ask to borrow my loaner and drop their old boxes in my lap. I don't mind though. But it has been a bad winter, age being what it is I'm down from 41 to 32 folks that pester me like that, and only one went to the nursing home.

I hate very few things but I truly do hate funerals.

---

### Post by Dangertux on 2012-03-10
I would say that non pae should definitely be an option for systems that do not support physical address extension. However I also believe that PAE should be the default on any system that supports it. There are a number of reasons for this all of which essentially come back to the security features provided by some of the memory protection features provided in PAE kernels.

All that being said I would support any solution that still allowed the installation of a non pae kernel. Either via autodetection or manually.

---

### Post by kansasnoob on 2012-03-11
Done:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930447/comments/50](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930447/comments/50)

Not what I'd originally planned but I slept on it, thought about it a lot, and decided on this plan of action.

I just hope I don't make Colin mad at me. He's always been one of the most pleasurable devs to work with squashing bugs so I'd hate to damage that relationship.

---

### Post by effenberg0x0 on 2012-03-11
This is probably a stupid suggestion: Has anyone tried to diff a pae-enabled kernel from it's non-pae counterpart? Like, compile same kernel with and without PAE config and diff them. 

Maybe you don't really need to pack both kernels, wasting some media space and/or bandwidth, but a diffed binary patch, tgz'ed, *could* (again, no idea) be very small? 

I haven't really thought about it, but maybe we should consider the possibility of booting to busybox, check CPU and only then select the kernel (pae is available as default/non-pae will decompress and apply binary patch no pae-enabled one, to create non-pae kernel on the fly). Then kexec to new kernel and proceed? 

Feels doable, with small risk and almost no extra work (automate diff/tgz on release server means a few script lines, automate boot to busybox + check arch + decompress & apply patch + kexec is also easy).

Regards,
Effenberg

---

### Post by agurk on 2012-03-11
> **kansasnoob said:**
> Done

Excellent, well put, thank you. As you say, the move to pae as default would seem to bring more harm than good. As anecdotal evidence, I have a Tosh and an IBM here affected by this change, and since I don't consider either of them ready for the e-waste landfill just yet, I'd rather be looking at other distros than jumping through hoops to get Ubuntu 12.04 on there.

---

### Post by jbicha on 2012-03-11
kansasnoob, I don't believe Ubuntu's website will promote the 64-bit image as default for 12.04.

---

### Post by kansasnoob on 2012-03-12
> **jbicha said:**
> kansasnoob, I don't believe Ubuntu's website will promote the 64-bit image as default for 12.04.

You could be right, I just recall that being mentioned very early in the dev cycle ;)

---

### Post by sudodus on 2012-03-12
> **kansasnoob said:**
> Done:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930447/comments/50](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930447/comments/50)

Not what I'd originally planned but I slept on it, thought about it a lot, and decided on this plan of action.

I just hope I don't make Colin mad at me. He's always been one of the most pleasurable devs to work with squashing bugs so I'd hate to damage that relationship.

Good luck :KS

---

### Post by keithpeter on 2012-03-12
> **jbicha said:**
> kansasnoob, I don't believe Ubuntu's website will promote the 64-bit image as default for 12.04.

I think i386 as default is sensible, and it will minimise wasted downloads by netbook owners. This represent a change from what was announced originally. I've been testing 64 bit on the grounds it would be the default! Might do a reinstall...

Should we add ourselves to the bug (no comments, just 'this affects me')?

I have one non-pae laptop left now...

---

### Post by kansasnoob on 2012-03-12
> Should we add ourselves to the bug (no comments, just 'this affects me')?

By all means, it can't do any harm :)

---

### Post by nm_geo on 2012-03-13
> **kansasnoob said:**
> By all means, it can't do any harm :)

I have me too'd the bug and subscribed.. Now in waiting mode..
My last attempt at recreating the LiveCD manually with the non-pae kernel did not go so well.

---

### Post by grahammechanical on 2012-03-13
> kansasnoob, I don't believe Ubuntu's website will promote the 64-bit image as default for 12.04.

A pity. There are a lot of misconceptions as to why 32bit is the recommended install.

In a recent thread on this forum someone actually advised against using 64bit Ubuntu on a 64bit CPU because you are not supposed to use 64bit if you have less than 4GB RAM. Where people get these ideas from I do not know.

That recommendation actually caused me to choose 32bit the first time I downloaded an ISO image, even though I knew the difference between 32bit and 64bit and had in fact installed a 64bit Ubuntu from a CD given away by a Linux magazine.

I do not think that it is enough to simply say "32bit recommended." There should also be on that page a full explanation as to why or no recommendation at all. Just explain the differences.

Regards.

---

### Post by quequotion on 2012-03-13
> **grahammechanical said:**
> I do not think that it is enough to simply say "32bit recommended." There should also be on that page a full explanation as to why or no recommendation at all. Just explain the differences.

When can we start to officially call 32bit "legacy"?

---

### Post by jerrylamos on 2012-03-15
> **quequotion said:**
> When can we start to officially call 32bit "legacy"?

Where did I read 64 bit takes more disk space, more memory, and runs slower?

Thanks, Jerry

---

### Post by kansasnoob on 2012-03-15
> **jerrylamos said:**
> Where did I read 64 bit takes more disk space, more memory, and runs slower?

Thanks, Jerry

Well this is really off-topic but ................ you may have heard that from me, or possibly elsewhere.

I'd long thought that I had only one set of 64bit hardware but it turns out that I have two. Each has only 2GB RAM, one with an actual matched set, the other not. One has a 1.6Ghz Intel Atom CPU, the other has a Sempron 2.2Ghz CPU.

Both run very, very well with i386 .............. but both lag down after a few hours with 64bit! I can actually watch the "lag" take place by installing this:

[https://launchpad.net/indicator-sysmonitor](https://launchpad.net/indicator-sysmonitor)

So i386 simply works better for me, because 64 bit eats RAM like my dogs eat treats! Both of my machines are still DDR2 and with the reduction in price for DDR3 RAM I'll likely go to no less than 8GB RAM next YEAR!

And I really mean 2013! Until then I'll use what I have with i386 :D

---

### Post by cariboo on 2012-03-15
> **jerrylamos said:**
> Where did I read 64 bit takes more disk space, more memory, and runs slower?

Thanks, Jerry

Depending on what atom processor your netbook has, it will probably run 64-bit, give it a try.

---

### Post by keithpeter on 2012-03-16
> **kansasnoob said:**
> Both run very, very well with i386 .............. but both lag down after a few hours with 64bit! 

Hello kansasnoob and all

My Atom N270 Samsung NC10 netbook won't boot off Precise 64bit on a USB stick, I get the 'the kernel requires an x86-64 CPU' error.

My desktop, a recycled HP xw6200 workstation (quad core xeon with 4Gb ram and an nvidia graphics card in the PCI-e slot), runs i386 at about 150-200Mb of ram lower than 64 bit. E.g. 300Mb start up as opposed to 480Mb ish and similar with apps loaded. Of course, that could just be some memory leak thing on the testing 64bit.

I didn't see any lag over time with the 64bit on the desktop, but I'll boot off the stick and try measuring. I do use hibernate and so get uptimes in the days to a week with tens of hours of real time between reboots.

---

### Post by Yellow Pasque on 2012-03-16
> **grahammechanical said:**
> In a recent thread on this forum someone actually advised against using 64bit Ubuntu on a 64bit CPU because you are not supposed to use 64bit if you have less than 4GB RAM. Where people get these ideas from I do not know.

This idea probably comes from the same place where people get the brilliant idea to install proprietary Nvidia drivers on systems without Nvidia GPU's.

Anyway.. the thread seems to be getting off track. 32-bit vs. 64-bit is a different issue than not supporting non-PAE systems with the default install image. I would really like to see non-PAE systems supported "out of the box" for one last release (especially since 12.04 is an LTS). Note: I'd like to think I'm not biased since I've been using 64-bit for all my Linux installs for 5 years.

---

### Post by jerrylamos on 2012-03-16
> **Temüjin said:**
> I would really like to see non-PAE systems supported "out of the box" for one last release (especially since 12.04 is an LTS). Note: I'd like to think I'm not biased since I've been using 64-bit for all my Linux installs for 5 years.

I haven't seen any post results of anyone else actually trying to run a Pentium M non-pae example IBM Thinkpad T40.  Mine is 768 MB (256+512) and has 12.04 ubuntu and lubuntu installed on it, generic-pae, running O.K. for a Beta.  Maybe the memory less than 1 GB has something to do with this success.

Early in precise pangolin Alpha there were some daily builds that checked for the pae flag and wouldn't boot.  Lately the builds have booted and installed.

I also tried a mini.iso which did install the generic without the -pae.  I'm a softy and prefer all the standard ubuntu and lubuntu goodies so I went back to a normal install which put on the generic-pae which run.

Jerry

---

### Post by jerrylamos on 2012-03-16
> **Temüjin said:**
> I would really like to see non-PAE systems supported "out of the box" for one last release (especially since 12.04 is an LTS). Note: I'd like to think I'm not biased since I've been using 64-bit for all my Linux installs for 5 years.

I haven't seen any post results of anyone else actually trying to run a Pentium M non-pae example IBM Thinkpad T40.  Mine is 768 MB (256+512) and has 12.04 ubuntu-2D and lubuntu installed on it, generic-pae, running O.K. for a Beta.  Maybe the memory less than 1 GB has something to do with this success.

Early in precise pangolin Alpha there were some daily builds that checked for the pae flag and wouldn't boot.  Lately the builds have booted and installed.

I also tried a mini.iso which did install the generic without the -pae.  I'm a softy and prefer all the standard ubuntu-2D and lubuntu goodies so I went back to a normal install which put on the generic-pae which run.

Jerry

---

### Post by sudodus on 2012-03-17
> **jerrylamos said:**
> I haven't seen any post results of anyone else actually trying to run a Pentium M non-pae example IBM Thinkpad T40.  Mine is 768 MB (256+512) and has 12.04 ubuntu and lubuntu installed on it, generic-pae, running O.K. for a Beta.  Maybe the memory less than 1 GB has something to do with this success.

Early in precise pangolin Alpha there were some daily builds that checked for the pae flag and wouldn't boot.  Lately the builds have booted and installed.

I also tried a mini.iso which did install the generic without the -pae.  I'm a softy and prefer all the standard ubuntu and lubuntu goodies so I went back to a normal install which put on the generic-pae which run.

Jerry

I tried the lubuntu daily build one or two days before precise alpha turned into beta. My IBM Thinkpad T41 with 1GB RAM wouldn't boot, complained about the non-pae processor. I could try the present daily build and report back.

[I]Edit: I tried today's daily build (2012-03-17), and it stops installing from a unetbootin USB drive after the following message: This kernel requires the following features not present on the CPU:
pae
Unable to boot - please use a kernel appropriate for your CPU.
--
It boots nicely with [/I]*pre-Precise versions of Ubuntu and *[I]Linux Mint Debian XFCE, and Debian Stable can be installed.
[/I]

---

### Post by ikt on 2012-03-28
Any updates on this or is all hope lost?

---

### Post by jerrylamos on 2012-03-28
Pretty apparent, ubuntu development is not interested.

Kudo's to the lubuntu people.

Now with internet available, install offers to install updates while installing,

What's the big deal about install not wanting to download the non-pae kernel if needed??  The kernel is a lot smaller than some of the massive update packages....

Install itself certainly does NOT need pae function.

I have no idea if my ASUS tablet does pae.  That's significant since Shuttleworth is driving ubuntu toward tablets.

Jerry

---

