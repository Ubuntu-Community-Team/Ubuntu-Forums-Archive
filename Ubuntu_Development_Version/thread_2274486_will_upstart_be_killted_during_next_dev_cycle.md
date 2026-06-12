---
title: "will upstart be killted during next dev cycle ?"
date: 2015-04-20
forum: Ubuntu Development Version
---

### Post by ventrical on 2015-04-20
As the title suggests .. I am curious as to what real plans the ubuntu dev team has for upstart.  Is Grub becoming a one sheriff town where hosting upstart and systemd is not big enough for the both of them?

Regards..

---

### Post by cariboo on 2015-04-20
Did you forget about LTS releases? Upstart will be supported at least until April 2019.

---

### Post by ventrical on 2015-04-20
Thnx :)

---

### Post by grahammechanical on 2015-04-20
As few minutes ago I was giving thought to a similar subject and I reminded myself that an important part of Ubuntu is the server edition and that with servers it is LTS releases that are important. The developers would not want to break anyone's server system. So, without even any gossip to base this on I would think that systemd will not fully replace upstart on the server edition until the release of 16.04 LTS server edition. Apparently there are a lot of server scripts that have to be re-written and tested.

I also remember that Ubuntu is following Debian but the developers do not sync Ubuntu with Debian every day or even every week. I think that it is once a cycle. I am not sure about that bit. 

> In the beginning of each Ubuntu development cycle the packages in Ubuntu are updated to those in Debian unstable.

[https://wiki.ubuntu.com/UbuntuDevelopment/Merging](https://wiki.ubuntu.com/UbuntuDevelopment/Merging)

Regards

---

### Post by ventrical on 2015-04-21
Thanks grahammechanical. I was concerned because of this past and recent behaviour  [http://ubuntuforums.org/showthread.php?t=2274484](http://ubuntuforums.org/showthread.php?t=2274484)   that /upstart/ in Grub is not getting very much attention .. especially so close to release day.  I have been  growing a ubuntu_gnome install from day one and it had a problem once with not shutting down with upstart and nVidia problem. That was fixed but with yesterdays updates, when I restart, while under the influence of upstart, it will completely *kill* my machine. That means will not hard/cold start and so I have to unplug power and re-insert power to be able to get the machine back. This behaves like a malware. I have tested other distros  on same machine with no similar effects. It did it once in unity I believe .. but as as said .. it was fixed.. but now it is back.

Being that systemD is default booter and behaviour of upstart is questionable I cannot help but assume that upstart is being treated with slack .. so they may fork over some repos and abolish upstart in 16.04. I just want to get a handle on this before I have to re-tutor myself all over again.

1.SystemD works awful while over-clocking. I produces MPU errors and other verbose but can still boot up at a midway overclock.
2.Upstart wasn't really broke to begin with and I am just thinking out loud as to what happened to the conventional wisdom of - 'if it ain't broke, don't fix it'.

regards..

---

### Post by grahammechanical on 2015-04-21
I agree with you about Upstart being fine. Certainly as far as I was concerned. And as you know I have been experimenting with Linux Containers (LXC) I have noticed two things regarding systemd

1) if the host is vivid and the container has vivid also, then Upstart is installed.

2) if the host is trusty and the container has trusty then I can upgrade to utopic and everything works as it should but my one attempt to upgrade (lubuntu) from utopic to vivid crashed and burned. The desktop in the container would not load.

I am trying to find a way of run W codename Ubuntu and the flavours in LXC and the latest idea was to install trusty in the container and upgrade all the way to W codename as all my other ideas failed. I am starting to think that systemd is to blame. Maybe things will improve once W codename is synced with Debian. Then we should get any of the Debian bug fixes that have not already come down. 

Regards.

---

### Post by ronparent on 2015-04-22
Not personally having followed recent development cycles - would this be informative.?

The five biggest changes in Ubuntu 15.04, Vivid Vervet

> Steven J. Vaughan-Nichols of ZDNet takes a look five important changes coming in Ubuntu 15.04 which he says are a switch of init manager from upstart to systemd, a kernel upgrade which features improved graphics and file system support, local menus being made the default, the last iteration of Unity 7 for the desktop, and updated applications such as Firefox and LibreOffice.

[http://www.zdnet.com/article/the-five-biggest-changes-in-ubuntu-15-04-vivid-vervet/](http://www.zdnet.com/article/the-five-biggest-changes-in-ubuntu-15-04-vivid-vervet/)

from:>  [https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue413](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue413)

---

### Post by ventrical on 2015-04-22
Hey .. thanks !

> 

People who really dislike systemd have asked for a choice of init  managers. They're not going to get one. As one Ubuntu developer put it, "[Ubuntu [has] never offered a choice of init system]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/1427654/comments/11"), and won't start doing that."








If all that article says is true then I guess the answer to my question is , 'yes' upstart will be killted.

Regards..

---

### Post by QDR06VV9 on 2015-04-22
Or as put on that link.
>   As stated on the mailing list few months ago ([https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2014-December/015154.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2014-December/015154.html)),  
Ubuntu never offered a choice of init system, and won't start doing  that. systemd is mandatory to be the supported ubuntu path. That's the  reason 
why ubuntu-standard won't depend on systemd|upstart.
 Note that for some kernel reasons, the Touch image is still using upstart, but that will change in the future.              

Hope they get it sorted out a bit more though(Fingers crossed);)

---

### Post by Cavsfan on 2015-04-24
I'm pretty sure they killed upstart in 15.04 except on vanilla Ubuntu and Xubuntu. Or has anyone experienced anything different from my experience with Vivid Mate?

I installed upstart but it's basically worthless on my system unless I don't want the option to logout, restart or shutdown.

---

### Post by Elfy on 2015-04-24
I don't think it's been killed - if that was the case Xubuntu wouldn't have it. 

More likely to be odd recommends or something in a flavour's seed.

---

### Post by Cavsfan on 2015-04-24
> **Elfy said:**
> I don't think it's been killed - if that was the case Xubuntu wouldn't have it. 

More likely to be odd recommends or something in a flavour's seed.

But, how come only 2 flavors got it out of the 6?
**Ubuntu**
Kubuntu
**Xubuntu**
Lubuntu
Ubuntu Gnome
Ubuntu Mate

I installed upstart and could not logout, restart or shutdown. I looked at the uninstalled suggested packages and none looked like they would fix the problem.
Besides, I'm trying to be a regular user who doesn't know anything about all of this and I don't care to investigate what it would take to get upstart working on Mate.

So for me and most others I believe it is in fact dead on all but those 2 flavors. I also don't understand why those 2 were the chosen ones to come with both. 
I guess that was the intention all along which did surprise me.
I expected both to come on the final release ISO. But that was not what happened.

I'm OK with it though systemd runs fine on my system.

---

### Post by zika on 2015-04-25
UpStart works nicely, fast and responsive (even more than with SystemD at the moment). ShutDown and all are working as they should. Just wanted to try. It even makes me think of staying with it for some time... ;)
This is a sort of offtopic in this part of Forum(s) (now that 15.04 is not in testing anymore) but... ;)

---

### Post by Elfy on 2015-04-25
> **Cavsfan said:**
> But, how come only 2 flavors got it out of the 6?
**Ubuntu**
Kubuntu
**Xubuntu**
Lubuntu
Ubuntu Gnome
Ubuntu Mate

...

No idea at all - just the guess.

Frankly I don't really care much either - I mentioned it to a couple of other flavour people - my job done ;)

---

### Post by ventrical on 2015-04-25
> **Elfy said:**
> I don't think it's been killed - if that was the case Xubuntu wouldn't have it. 

More likely to be odd recommends or something in a flavour's seed.

I hear you. It would be good  for ubuntu as a whole if it (upstart) remained a staple for xubuntu past 16.04 so as noobs could make  a more sensible and comprehensive migration until they can wrap there minds around systemD , especially those migrating  from other non-ubuntu distros to ubuntu.

Regards..

---

### Post by syntaxerror74 on 2015-04-25
> **cariboo said:**
> Did you forget about LTS releases? Upstart will be supported at least until April 2019.
Phewww. THANK GOODNESS. That feels very comfortable. I reckon that up to said date, I'm easily going to be able to do without systemd, which has been nothing but trouble so far.

Besides, why was there a decision at all to move from upstart to systemd in the ´Buntus? Does the latter come up with any technical advantages?

---

### Post by Cavsfan on 2015-04-25
> **Cavsfan said:**
> But, how come only 2 flavors got it out of the 6?
**Ubuntu**
Kubuntu
**Xubuntu**
Lubuntu
Ubuntu Gnome
Ubuntu Mate


> **Elfy said:**
> No idea at all - just the guess.

Frankly I don't really care much either - I mentioned it to a couple of other flavour people - my job done ;)

LoL! Well if you don't care then neither do I! :P

---

### Post by Cavsfan on 2015-04-25
> **Elfy said:**
> I don't think it's been killed - if that was the case Xubuntu wouldn't have it. 

More likely to be odd recommends or something in a flavour's seed.

> **ventrical said:**
> I hear you. It would be good  for ubuntu as a whole if it (upstart) remained a staple for xubuntu past 16.04 so as noobs could make  a more sensible and comprehensive migration until they can wrap there minds around systemD , especially those migrating  from other non-ubuntu distros to ubuntu.

Regards..

So, are you saying people who use Xubuntu are noobs? I can't help it lol that is what I got from your comment. :lol:

---

### Post by zika on 2015-04-25
> **syntaxerror74 said:**
> Does the latter come up with any technical advantages?It would be easier to answer if You've made Your question other way around. Of course it does...

---

### Post by ventrical on 2015-04-25
> **Cavsfan said:**
> So, are you saying people who use Xubuntu are noobs? I can't help it lol that is what I got from your comment. :lol:

No. That is not what I am saying. For example on one of my laptops I have a working utopic 14.10 (unity) install. It just barely made it with the ATi Radeon graphics it has on board.  Just yesterday it notified me that a new version , '15.04 vivid' was available.  Utopic currently uses  upstart as default. So if I was a real noob and went ahead and upgraded the version and then broke my system (as a noob would see it) that would be very discouraging, especially with the verbose 'version 219' popping up at boot and all the other errors that come with systemD on now , recently made legacy and obsoleted machines.

 However , if you have some expertise and want to configurate systemD into the new development version as they roll off the pipe then that is not really fair to the rest of the newly created novice ubuntu database. Is it?

  So actually xubuntu would be the smarter man's choice for machines that are regurgitating verbose code on systemD. If you have the *time* to sit and configurate files to make things smooth once again then more power to you's, but don't expect it from noobs who are just dipping their toes in the ubuntu waters.

 Me? I 'm just a tester like most of you here.  I just try to work it (systemD) as best as I can. It works very well on some machines and very poorly on others.  It is not 'globally' friendly across the wider spectrum of available form factors that are currently in the wild.

  In my first couple of posts I pointed out how I have been growing a daily install of ubuntu-gnome from day one. It had problems with systemD and upstart and nVidia drivers. nVidia drivers worked out as did systemD but it seems that upstart has been left flapping in the wind on that particular distribution (some of you have better success than others) but you are working the development boards every day. A noob or potential prospect/convert has no idea how the development process works and I am just opining that systemD could scare them off.

  Perhaps I'll try another update/upgrade and see if I had missed some finals on that install.

Regards..

Edit:

Ahem .. cough ...ahar... cuff...sniff... Eeeeeeeeehhh.. !  ahh... uh (just clearing the dust that some whino kicked in me face (said with deep Irish accent ) :)  I think I may have a motherboard issue on that one machine that is causing upstart to malfunction.

Regards..

---

### Post by Cavsfan on 2015-04-25
Yes, I didn't think you intended to put it that way. But I see your point about upgrading from Utopic with upstart to Vivid with systemd. I never do that though. I'm into LTS's and a single version of the developmental system.

I also like to do clean installs. I did an upgrade from Lucid to Precise but it left me confused with all the extra packages that weren't removed so I stick to clean installs now.

Sometimes I jump around but am likely to stick with Mate for a while since it is an accepted flavor now. Systemd runs great on it too. I've never experienced the slowness that others have mentioned. It's always been about the same for me.

I never know what I'm going to do until I do it. Maybe I'll jump back into the vanilla Ubuntu I'll wait and see...

Regards

---

### Post by craig10x on 2015-04-27
I use ubuntu w/unity and just recently upgraded to 15.04 and find systemd to work fine...boot up time seems essentially identical to upstart, and shut down is actually faster...

---

### Post by fjgaude on 2015-04-27
> **craig10x said:**
> I use ubuntu w/unity and just recently upgraded to 15.04 and find systemd to work fine...boot up time seems essentially identical to upstart, and shut down is actually faster...

I'll have to do a clean install to see if what you say on your system is true on mine. Systemd slows my boot by up to 16 seconds over upstart.

---

### Post by ventrical on 2015-04-27
> **fjgaude said:**
> I'll have to do a clean install to see if what you say on your system is true on mine. Systemd slows my boot by up to 16 seconds over upstart.

I'll be watching this one :)

---

### Post by fjgaude on 2015-04-27
Well, ventrical... I did two clean installs of 15.04 release and got nothing but delays with **systemd** at boot, 42 seconds from grub menu, only 6 seconds using **upstart**. It must be my system, drive combination, Unity, Intel, etc., can't say. I'm now just waiting for 15.10. I have no issues with 14.04 LTS, my main OS.

---

### Post by craig10x on 2015-04-27
From the bios screen to the log in screen takes about 38 seconds, and after i log in my password, 10 seconds to desk top...shut down takes like less then 5 seconds...that is what i am getting on my systemd....
i never really counted it when we had upstart, so i have no basis for comparison, but it "feels" about the same as before...i don't think it is faster booting up, i would say, around the same...
I have a 4 year old toshiba 17" laptop (which is my desktop) sandy bridge i3 intel, and using ubuntu w/unity...

---

### Post by ventrical on 2015-04-27
> **fjgaude said:**
> Well, ventrical... I did two clean installs of 15.04 release and got nothing but delays with **systemd** at boot, 42 seconds from grub menu, only 6 seconds using **upstart**. It must be my system, drive combination, Unity, Intel, etc., can't say. I'm now just waiting for 15.10. I have no issues with 14.04 LTS, my main OS.

I am  interested in what type of hardware you are using.

Thanks..

Regards..

---

### Post by ventrical on 2015-04-27
As I probably posted before.. I am getting a wide range of differences with SATA I, II and III generation hdds with SSD ver 3.0, of course, being the fastest on SATA III MoBo. There is really no discernible  difference on that machine but older machines, circa 2010 with SATA II and prior have varying reports.

---

### Post by fjgaude on 2015-04-27
All my SATA drives are III, 600 MBs. Here's the full story:

Ubuntu Unity Linux on Z87 Haswell motherboard, ASRock Model Z87E-ITXac with Intel i5-4670K CPU 3.4GHz (800MHz-4.0GHz overclock), HD4600 video, Titan CU30 cooler, 16G DDR3 G.Skill 2400MHz (20.2 GB/s), Plextor M5S 256G and M5P 128G SSDs, WD VelociRaptor WD5000BHTZ 500G HDD, 300W SFX psu, latest UEFI BIOS 2.50. Suspend and Resume without issue. Booting fast, 5 to 20 seconds, from either Plextor SSD or VelociRaptor HDD in Lian Li PC-Q30X case. ASUS Monitor, 27" WQHD, 2560 x 1440 pixels.

It doesn't make any difference what apps I have installed. I tried none and full up with VBox and all the ones that we use for graphic design.

---

### Post by harry332 on 2015-04-28
> **fjgaude said:**
> All my SATA drives are III, 600 MBs. Here's the full story:

Ubuntu Unity Linux
Z87 Haswell motherboard, ASRock Model Z87E-ITXac
Intel i5-4670K CPU 3.4GHz (800MHz-4.0GHz overclock), HD4600 video, Titan CU30 cooler
16G DDR3 G.Skill 2400MHz (20.2 GB/s)
Plextor M5S 256G and M5P 128G SSDs, WD VelociRaptor WD5000BHTZ 500G HDD
300W SFX psu, latest UEFI BIOS 2.50.
ASUS Monitor, 27" WQHD, 2560 x 1440 pixels.


We have a lot common regarding our hardware, this is mine:

Asus Sabertooth Z97 Mark II, Haswell socket 1150
Intel Core i7 4790 3,6 GHz (turbo 4,0 GHZ)
16 Gb G.Skill Sniper DD3 1866 MHz, 9-10-9-28-2N latency
3 x Samsung SSD 850 Pro 128 Gb, 550 Mb/s
Corsair RM 650 80 Plus 650 W PSU
HP Z27i IPS 27" monitor (2560x1440)

However, I do not have any issues with booting.
I use Gnome-shell DE with systemd booting.
With this setup it is about 5 sec from Grub to DE.

---

### Post by mc4man on 2015-04-28
I'd have no idea if sysd claims to be faster, certainly isn't here, probably around 100% slower.
Only use ubuntu on ext. sdd's (usb3), current one is mid range performance wise (ADATA USA SE720).
With upstart bootchart is 11 sec which includes a very quick greeter log in. I'd guesstimate 15.04 sysd at a bit over 20 secs or so on same drive/hardware.

---

### Post by fjgaude on 2015-04-28
I simply don't know why systemd is so slow in booting, could be Unity, not the hardware. I guess in the long run it will not matter to me, as I boot so seldom. Whether it's 6 seconds or 30, no big deal.

---

### Post by Cavsfan on 2015-04-28
I guess when you have only systemd they make it fast. :p

I'm running Vivid Mate and it, as I've mentioned at least once or twice, came with only systemd and my system on this old computer boots up relatively fast.

You can see what I have from my signature - a 6 year old machine. If it weren't for the delay while it finds the connected 1TB USB drive at boot, it would be much faster.

It boots about the same as my other two Linux systems but suspend is a second or two faster.

---

### Post by fjgaude on 2015-04-28
Okay, Cavsfan, you are likely right... under Unity 15.04 comes with the option to boot from the grub menu either systemd or upstart... that could be the issue. So I simply wait for the nest release with upstart already installed.

---

### Post by craig10x on 2015-04-28
That actually makes a lot of sense, and indeed that could be what slows down the boot up a bit with ubuntu w/unity in that since there is still the two options, and once that option is eliminated (next version of ubuntu w/unity) then boot up would likely be faster...Also, let us keep in mind that during the 15.04 updating cycle, there might be changes/improvements/fixes to systemd that will also aid in speeding things up as well ;)

---

### Post by fjgaude on 2015-04-28
Makes sense, craig! Thanks!

---

### Post by ventrical on 2015-04-29
> **craig10x said:**
> That actually makes a lot of sense, and indeed that could be what slows down the boot up a bit with ubuntu w/unity in that since there is still the two options, and once that option is eliminated (next version of ubuntu w/unity) then boot up would likely be faster...Also, let us keep in mind that during the 15.04 updating cycle, there might be changes/improvements/fixes to systemd that will also aid in speeding things up as well ;)

Yes.. in all fairness, systemD is still a work in progress. It most likely will get better. If it does not and starts corrupting files (as predicted by some pundits) then Canonical always has the luxury to roll back to upstart or even a newer convention before 16.04.

 It's good to see both the positive reviews and the negative reviews. So far it looks sort of 50/50 and those kind of ratios don't add up to a process that is efficient or stable. Whats that ol'e saying ... (stuff) rolls down hill? In a province in Canada called New Brunswick we have a tourist site called Magnetic Hill where it appears that (stuff) actually rolls uphill ! :)

Looks as if in these new cases that (stuff) <insert 'Smart Things' for stuff> may be rolling both  up and down hill... hmmmm :) ehehehe.. So if Smart Things can roll both up and down hill then they must be really smart :)

Regards..

---

### Post by syntaxerror74 on 2015-05-03
> **fjgaude said:**
> Okay, Cavsfan, you are likely right... under Unity 15.04 comes with the option to boot from the grub menu either systemd or upstart... that could be the issue. So I simply wait for the nest release with upstart already installed.

Umm...you mean that it would run upstart *by default*?
I think you should scratch that thought...they've gotten a crush with systemd and they'll most likely keep it as a default for the next few releases since they *think* it runs perfectly fine (because it doesn't cause trouble on* their *machine(s) and they usually don't care about the others' ones).

---

### Post by Cavsfan on 2015-05-04
> **fjgaude said:**
> Okay, Cavsfan, you are likely right... under Unity 15.04 comes with the option to boot from the grub menu either systemd or upstart... that could be the issue. So I simply wait for the nest release with upstart already installed.

> **syntaxerror74 said:**
> Umm...you mean that it would run upstart *by default*?
I think you should scratch that thought...they've gotten a crush with systemd and they'll most likely keep it as a default for the next few releases since they *think* it runs perfectly fine (because it doesn't cause trouble on* their *machine(s) and they usually don't care about the others' ones).

I'm pretty sure he was referring to the fact that upstart comes already installed on vanilla Ubuntu and Xubuntu not that it comes default. On all the other flavors it does not come installed and installing it manually it pretty much worthless. Been there and done that twice. There may be some magical way of installing other things besides Upstart to get it to work but I'm not going to waste my time worrying about it.

This install of Vivid will turn into the next version after it comes out.

Although it may now be installable as it used to just install one package - upstart and nothing else. This is what it is proposing to install now:
```
cavsfan@cavsfan-MS-7529:~$ sudo apt-get install upstart
[sudo] password for cavsfan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libcgmanager0 libjson0
Suggested packages:
  graphviz upstart-monitor
The following NEW packages will be installed:
  libcgmanager0 libjson0 upstart
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/436 kB of archives.
After this operation, 1,957 kB of additional disk space will be used.
Do you want to continue? [Y/n]
```

Still not worth the effort to me.

---

### Post by fjgaude on 2015-05-04
> **syntaxerror74 said:**
> Umm...you mean that it would run upstart *by default*?
I think you should scratch that thought...they've gotten a crush with systemd and they'll most likely keep it as a default for the next few releases since they *think* it runs perfectly fine (because it doesn't cause trouble on* their *machine(s) and they usually don't care about the others' ones).

The way it is now is both are provided by default but systemd is first in the grub menu list. I think you are right and not sure if upstart will be automatically provided as time goes by. It is what it is. <smile>

---

### Post by syntaxerror74 on 2015-05-05
> **fjgaude said:**
> The way it is now is both are provided by default but systemd is first in the grub menu list. I think you are right and not sure if upstart will be automatically provided as time goes by. It is what it is. <smile>
I can see you got me perfectly right. :) 
BTW, I too have to select upstart every time by the 'Advanced' sub menu in grub as I am not too experienced with messing in there, rather being afraid of breaking something vital...Plus, the way of editing things is totally strange, as you're not supposed to directly edit grub.cfg, but instead edit a sort of template which then on its part *creates* a grub.cfg. Dunno where the deeper sense of this methodics is (I wished I *could* simply edit it the normal way), but they must have had their reasons to do things that way mustn't they...;)

> **Cavsfan said:**
> upstart comes already installed on vanilla  Ubuntu and Xubuntu not that it comes default. On all the other flavors  it does not come installed
No, it's not missing by default on *all* the others. As you can see, I'm running Lubuntu, and even Saucy had it installed - by default. And it even booted using upstart by default; not until they decided to made systemd default, problems started ;) (making me wonder if the **d** in system**d **actually stands for **[B]d**[/B]isintegration or even **d**isaster :P)

---

### Post by grahammechanical on 2015-05-05
Reasons? Want some guesses from me?

Canonical has already ruffled plenty of feathers introducing Unity and changing their mind about supporting Wayland development in favour of Mir. So, why cause even more hate comments by sticking to Upstart?

The quick decision to go over to SystemD following the wise decision not to get involved in the arguments the Debian developers were having seems to me to be a smart move for improving FOSS community relations.

Besides, the Debian developers have to do all the ground work. 

Regards.

---

### Post by ventrical on 2015-05-06
From what I gathered after watching the live keynote speech by M. Shuttelworth I take it that Canonical is sincere about collaboration with these newer projects and is definitely interested in mending fences and building bridges. With systemD there is always leeway, the possibility that bugs will be ironed out and breathing room to introduce even newer and more legacy friendly concepts that could perhaps replace it in the future if the need arises.

Regards..

---

