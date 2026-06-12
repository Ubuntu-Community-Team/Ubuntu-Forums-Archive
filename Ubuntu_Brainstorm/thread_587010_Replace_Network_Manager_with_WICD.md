---
title: "Replace Network Manager with WICD"
date: 2007-10-22
forum: Ubuntu Brainstorm
---

### Post by rahulthewall3000 on 2007-10-22
I have some similar threads, but I would herein like to make a request to the Ubuntu Developers. Network Manager doesn't have a nice UI and doesn't work very well either. Compared to that, WICD has a very nice UI and works perfectly. (at least for me)
I personally think that it would be a nice idea to replace network-manager (I love to call it network-mangler) with WICD.
I would love to hear everyone else's views on this topic.


Thanks
Rahul

---

### Post by ssam on 2007-10-22
NM only works with wireless drivers that use the Linux Wireless Extensions (WEXT) system.

in one way this is a bad thing. it means it does not work with all wireless drivers. but on the good side, it is encouraging the wireless drivers to be more sane. things get fixed in the right place (the driver), rather than worked arround in NM. the past few kernel versions have seen lots of unification and merging of wireless drivers. rt2x00 has been merged into 2.6.24.

also NM0.7 is pretty much a rewrite, and has lots of fancy new things [http://live.gnome.org/NetworkManagerToDo](http://live.gnome.org/NetworkManagerToDo)

fedora 8 will have NM 0.7 (or some sort of prerelease). so by hardy time NM 0.7 will definately be out.

so, if WICD works better for you, then use it. but i think NM is best for default

---

### Post by thtde on 2007-10-22
Please keep Network Manager as default.

It works perfectly for me and the next version should improve a lot of things (e. g. static IP).

---

### Post by rahulthewall3000 on 2007-10-22
My point was that we should try something that works better. 
However, it was only a suggestion and if the majority feels that network-manager is doing a good job then that is good.
And, I think that I would try network-manager 0.7 for the features that it promises, but if the UI does not improve, and there is no major upgrade in functionality I see myself remaining with WICD.

---

### Post by smartboyathome on 2007-10-22
I used WICD back in Gutsy while testing (when network manager broke my card), and I didn't like it as much as NetworkManager, though NetworkManager has been giving me some fuss lately.

---

### Post by Vadi on 2007-10-22
I find that I have to recommend WICD to a lot of people.

Why? Better wireless support.

Getting the right drivers for your card is only half of the battle, apparently. If iwconfig can see your card just fine, that doesn't mean that NM can see it. But can WICD? Yes, it does for all cases that I tried so far - so I recommend to replace NM with WICD for every single laptop user I get to try ubuntu, to save them headaches.

Their gamble on one protocol only, if that is true, is surely not the best way to go about things.

The only upside that NM has is that it automatically connects on my ethernet connection, whereas with wicd you need click "connect". Not a big deal, considering that nm never got my wireless up anyway.

---

### Post by tighem on 2007-10-22
WICD is definitely the superior offering right now. However, the one in the repos has a bug that causes it to take forever to load. Version 1.3.4 works much faster.

The biggest thing that I can see is wireless support is much, much improved. In order to connect my corporate wireless network required much command line work. WICD has all the options built into it and allows you to save profiles.

---

### Post by smartboyathome on 2007-10-22
> **tighem said:**
> WICD is definitely the superior offering right now. However, the one in the repos has a bug that causes it to take forever to load. Version 1.3.4 works much faster.

The biggest thing that I can see is wireless support is much, much improved. In order to connect my corporate wireless network required much command line work. WICD has all the options built into it and allows you to save profiles.

I like it and all (I tried it out again), but I don't like how it doesn't have a tray icon which allows you to click to open up the preferences (the current network monitor applet is far insuperior to NetworkManager). If that were implemented, then I am sure it would be THE best network manager out there.

---

### Post by rahulthewall3000 on 2007-10-22
> **smartboyathome said:**
> I like it and all (I tried it out again), but I don't like how it doesn't have a tray icon which allows you to click to open up the preferences (the current network monitor applet is far insuperior to NetworkManager). If that were implemented, then I am sure it would be THE best network manager out there.

What are you talking about, of course WICD has a tray icon. Try this:
/opt/wicd/tray.py

---

### Post by unisol on 2007-10-22
does wicd 1.3.4 have support for rt61 drivers?

---

### Post by qamelian on 2007-10-23
> **rahulthewall3000 said:**
> My point was that we should try something that works better. 
However, it was only a suggestion and if the majority feels that network-manager is doing a good job then that is good.
And, I think that I would try network-manager 0.7 for the features that it promises, but if the UI does not improve, and there is no major upgrade in functionality I see myself remaining with WICD.

"Something that works better" is a matter of opinion. As I stated in another similar thread, network-manager has always worked perfectly for me, but thus far wicd has never worked on my laptop.  If Ubuntu were to go the Wicd route, the first thing I would do is remove it and replace it with network-manager.

---

### Post by yostral on 2007-10-23
qamelian +1 :)

---

### Post by aamukahvi on 2007-10-23
I've had NM+WPA2 working flawlessly since feisty (no CLI voodoo) and NM 0.7 should improve on that so... NM!

---

### Post by ctsdownloads on 2007-11-05
Unisol: Yes, but use this guide for maximum results. Despite the Feisty issues of using rt61pci, in Gutsy it worked with the Edimax EW-7608PG which uses rt61pci with a PCMCIA card without issue. 

[http://www.lockergnome.com/nexus/linux/2007/10/18/ubuntu-gutsy-wireless-help](http://www.lockergnome.com/nexus/linux/2007/10/18/ubuntu-gutsy-wireless-help)

---

### Post by smartboyathome on 2007-11-05
> **rahulthewall3000 said:**
> What are you talking about, of course WICD has a tray icon. Try this:
/opt/wicd/tray.py

I stand corrected. Here is one but I _KNOW_ exists:
When I connect to a network, it should change the connect button in Preferences to Reconnect (I have gotten confused quite a few times).

---

### Post by rahulthewall3000 on 2007-11-06
> **smartboyathome said:**
> I stand corrected. Here is one but I _KNOW_ exists:
When I connect to a network, it should change the connect button in Preferences to Reconnect (I have gotten confused quite a few times).

Agree with you there, they should change that!

---

### Post by aldeby on 2007-11-08
WICD is indeed a good project, however, be fair, it hasn't at all a better user interface. It's interface is simply too big and clumpsy, whereas network-manager is much more handy. 

Talking on the features side both worked well for me, and I must say WICD has an useful feature nm does not have: the REFRESH button!!

Also if you do not want to rely on the gnome-keyring package WICD can handle autonomously your passwords, while nm cannot.

The bottom line is that although WICD seems a good project it needs to focus more on the UI. 
I myself would keep network-manager and test 0.7 version since this also has some important fetaures to be added.

---

### Post by dayzed2 on 2007-11-25
For those of you who are not familiar Wicd it is a wired and wireless manager. Wicd is Comparable to both knetworkmanager (Kubuntu) and network-manager-gnome (Ubuntu), but it is far superior in my opinion. To me it just makes sense to use Wicd for both Ubuntu and Kubuntu, it blows both knetworkmanager and network-manager-gnome away. For me compared to its competitors its so much faster and responsive not to mention easier to use, more control and less flakiness. I would personally like to see this as the default network manager in the next Ubuntu/Kubuntu release, I think it would be a smart move. Anyone care to vote for there favorite network manager.

---

### Post by dayzed2 on 2007-11-27
Guess I am all alone on this one.

---

### Post by Whiffle on 2007-11-28
Erm. I dunno.  I've used networkmanager, wicd and wifi-radar.  Networkmanager can work great, and when its working right, its awesome.  But for me it never really worked right, which is one of the big reasons I have slackware on my laptop now.  Networkmanager seems to be hard to get rid of on ubuntu.  Wicd works okay until you get a bunch of networks, then it takes forever to update.  I'm using wifi-radar on there right now though and its keeping me quite happy (connects to the LEAP network at school no problem, although I did have to setup wpa-supplicant)

---

### Post by octathlon on 2007-11-29
Yes, get rid of network manager! In fact, I'm on a Windows computer right now searching for the instructions to get it completely off my system and replace it with wicd or some other alternative, because whenever n-m has a problem it pretty much makes my ubuntu system useless.   I hate it

---

### Post by dayzed2 on 2007-12-01
To install Wicd in Kubuntu or Ubuntu read this [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)
The nice part is the wicd from this repository uninstalls its competitors for you. Just add the appropriate line to your /etc/apt/sources.list and your set to go. Took me less than 2 min and I was up and running with Wicd. I haven't had a problem with my wireless since. Just like the instructions say there is a tray icon that by default doesn't run. So don't miss that part.

---

### Post by 23meg on 2007-12-01
I've merged the two threads on the same subject. Please read [post #2]("http://ubuntuforums.org/showpost.php?p=3602609&postcount=2") before posting.

---

### Post by octathlon on 2007-12-02
Since replacing nm with wicd on Thursday, my wireless connection has not been dropped even once.  With nm it would happen from every few hours to every few minutes, and it would not always successfully reconnect.  So far I'm loving wicd. :D

---

### Post by ubutufan on 2007-12-02
Hi people. I am also amongst those that sponsor wicd as default. It is not perfect, does not work flawlessly but on most occasions it get's you connected. Here is my experience with it.
I run gutsy on a dell m1210. It comes with a very common card intel 3945abg. Using NM to connect to a secured WPA2 TPSK router is simply not happening. On the other hand wicd using wext, connects nicely with no interruptions. But....
I came across two networks that transmit the same essid (different dates, different places and obviously different mac addresses). Result: wicd simply won't reconnect to any of them again. I tried deleting the profiles. Nothing. can't connect. Any of you having any ideas, I would appreciate it.
I will be testing wicd 1.3.4 and NM 7 and hopefully will be back with another report.

---

### Post by Vadi on 2007-12-02
You should ask on their forums about this.

And the latest version of wicd is 1.3.7, I think..

---

### Post by smartboyathome on 2007-12-02
Well, I still think that WICD is a little out there for a user friendly distro (especially since the tray icon won't start up during a login!). Oh well, I just use E17's net module and open WICD when I need it by double clicking the module . ;)

---

### Post by ubutufan on 2007-12-02
Vadi the latest release is 1.3.8 issued december 1, 2007
As you suggested I did some searching in their forums and I found the following
[http://wicd.sourceforge.net/phpbb/viewtopic.php?f=3&t=218&sid=8493788018b706990bdd44b9fa22fe09](http://wicd.sourceforge.net/phpbb/viewtopic.php?f=3&t=218&sid=8493788018b706990bdd44b9fa22fe09)

This little hack has made wicd fully functional again.
By the way I did install version 1.3.4 It's got some great enhancements. Worth looking at it. Works flawlessly.
Thanks again

---

### Post by rahulthewall3000 on 2007-12-04
> **smartboyathome said:**
> Well, I still think that WICD is a little out there for a user friendly distro (especially since the tray icon won't start up during a login!). Oh well, I just use E17's net module oand open WICD when I need it by double clicking the module . ;)

You can make the tray icon start there by default.
Just add /opt/wicd/tray.py  sessions in gnome.
There must be something similar in KDE as well. Never used it, so do not know.

---

### Post by smartboyathome on 2007-12-04
I did add that to my startup, but it doesn't start when my computer does. I have to manually start it.

---

### Post by lswest on 2007-12-04
i personally like kwifimanager (meaning you also need to install kdebase, in my experience) but it has a nice configuration, and, in my experience, has less issues with lost configs and such as network manager or wicd (though of the 2 wicd is the better one).  Maybe someone should adapt it for gnome?:P  nah, i'm fine with the terminal too, so just ignore my random little post lol

---

### Post by Feenix3k on 2007-12-04
I will give WICD a try, I am sick of the headaches with network manage. I get network manager to work on my home secure network then I can't connect to free wireless. If the free wireless works then I can't log in at home.

---

### Post by wormser on 2007-12-04
Personally I am not a fan of network-manager.  I have always felt it was a weak point in Ubuntu.  I am going to take a look at WICD.

---

### Post by qamelian on 2007-12-04
In the interests of being fair, I replaced NM with wicd a few days ago to give it another try. As I've mentioned elsewhere, I've tried wicd several times before and it has never worked at all, while NM and wifi-radar both worked flawlessly on my laptop. Well, it has been three days and I am removing wicd and going back to NM. At least this time wicd actually seemed to do something whereas before it just didn't seem to want to deal with my wireless card. Unfortunately, while using wicd, my connection has been dropping about every 3 to 5 minutes requiring me to click the connect link each time. This doesn't happen when I'm using NM, so NM wins my vote again.

---

### Post by doorknob60 on 2008-02-09
I think Network-Manager should be default, because I find it easier to use, which is kinda the point in Ubuntu. Although, I use Wicd myself :)

---

### Post by Vadi on 2008-02-09
NetworkManager crashes everytime I shut down (it says some assertion fails). Pretty funny, considering this install is 2 days old.

---

### Post by 23meg on 2008-02-09
WICD has never even worked on my current laptop. However, it works flawlessly on another laptop. What does that say about WICD as a default?

---

### Post by AdemoS on 2008-02-11
On two notebooks and a desktop, network-manager-gnome would lose my wifi network, predicatibly, every couple hours.

Downloading on any protocol proved impossible.

Reading many NM tutorials, almost all of them required terminal commands. As open as I am to command-line, GUI just takes me less time.

Quite often, using left-click -> Manual Configuration....NM would freeze and become unresponsible without a reboot.



So I tried WICD after reading about it somewhere.

Following the simple instructions, I had it running in 2 minutes. 

Set up a a couple wifi profiles, and amazingly, it has been working ever since then---a year and a half---without one drop in signal.



My favorite feature in WICD? How EASILY you can choose your prefered wifi network and ***not allow*** any other wifi network to auto-connect.

With NM, when it died (and it did damn often) it would always connect to the wrong network....



Sorry guys, but even with NM 7's new features, I am done with NM. WICD all the way for me.

---

### Post by lichtgestalt on 2008-02-11
NetworkManager is just great and I can't see any real advantages of WICD.

There are only two things I'm still missing in NM:
1. Multinetwork support - with features like routing table adjusments and bridging
2. A more featurerich and especially better documented DBus interface

---

### Post by smartboyathome on 2008-02-11
The reason I use WICD most of the time is probably going to be solved with NM 0.7: WPA2 won't connect with it, while it does with WICD. WICD does work better for me, but I find NM easier to use overall than WICD.

---

### Post by gnomeuser on 2008-02-11
NM 0.7 works rather well for me on all my machines (3 of them currently). I have driver issues and there are bugs in the wifi stack causing headaches but NM itself works really well and it's stable.

---

### Post by 23meg on 2008-02-11
[QUOTE=gnomeuser]I have driver issues and there are bugs in the wifi stack causing headaches but NM itself works really well and it's stable.[/QUOTE]

I feel the majority of complaints with NM are actually complaints with drivers and the wireless implementation.

NM is picky and will only work properly with fully WEXT compatible drivers. This is actually a good thing in the long run, since it forces things to be fixed in the right place.

---

### Post by Jay Jay on 2008-02-11
From my experience NM is dreadful. Till I removed it, NM was the biggest hindrance to me enjoying reliable and stable wireless connectivity. I endured constant NM crashes during endless failed connection attempts and dropped connections. I would choose a router, which I knew to be correct only to have NM select a different one for me instead lol

I'm all for WICD :)

---

### Post by Vadi on 2008-02-11
> **23meg said:**
> I feel the majority of complaints with NM are actually complaints with drivers and the wireless implementation.

NM is picky and will only work properly with fully WEXT compatible drivers. This is actually a good thing in the long run, since it forces things to be fixed in the right place.

Yes, that is the majority of complaints.

And it's a real great strategy to limit yourself the amount drivers you,  can use. No, really, with absolutely tons of working drivers about, we really do have the luxury of picking out specific ones we like.

We should adapt this for graphics card too. OSS drivers only! Rah!

---

### Post by 23meg on 2008-02-11
[QUOTE=Vadi]And it's a real great strategy to limit yourself the amount drivers you, can use. No, really, with absolutely tons of working drivers about, we really do have the luxury of picking out specific ones we like.[/QUOTE]

"We" are not picking the ones "we" like; we're dependent on upstream, and there are certain development practices we can't compromise. You won't have much luck persuading the kernel people to merge non-WEXT-compatible drivers, and NM developers to stretch NM to work with them, and distribution developers to maintain them. "We" do not have much to do about any of this.

---

### Post by Vadi on 2008-02-11
Sure. We can, however, look into a more promising (one that makes less promises, claims, and accomplishes more) project, and evaluate their possibility.

---

### Post by pro-rsoft on 2008-02-14
Hmmm. why not have both? :)

---

### Post by smartboyathome on 2008-02-14
> **pro-rsoft said:**
> Hmmm. why not have both? :)

I don't think it is possible to have both installed on the same system. When I install WICD, it uninstalls network manager.

---

### Post by rahulthewall3000 on 2008-02-14
Yup, on Ubuntu for some reason it is not possible to install both. However, on my Gentoo installation it is possible to install both. And similarly in Ubuntu I think that if you install WICD from source install of using the .deb it should be possible to install both. Though, then again it does not make sense to have them both installed.

---

### Post by imdano on 2008-02-14
We package wicd to conflict with NetworkManager because of the likelyhood that someone installing wicd won't know or won't know how to properly disable NM, which will either cause networking problems or compound whatever problems the person was already having.

---

### Post by IanW on 2008-02-15
+1 Wicd. 

On my (now deceased) laptop, and its replacement (EeePC), I had to manipulate iwconfig by hand to connect to anything. Wicd just works.

---

### Post by enigma_0Z on 2008-02-26
I really don't mean to sound like I'm flamebaiting or trolling...

But why isn't WICD the default instead of networkmanager yet? 

NM is a really terrible app--never worked for me, but WICD (which is a frontend for wpa_supplicant that works) worked out of the box. Still does. From what I've read on the intertubes, most people prefer WICD over NM anyways.

At the very least, could someone put it into the hardy and gutsy repos, so users have a choice? IMO WICD is much more user friendly than NM though.

---

### Post by Jussi Kukkonen on 2008-02-26
> NM is a really terrible app--never worked for me
so you decided it's terrible with a sample size of one? Personally, I tried wicd once and ended up without any connection and no clue how to fix it, but I'm not claiming wicd is terrible... It just didn't work in that case.

> From what I've read on the intertubes, most people prefer WICD over NM anyways.
*reference needed...*

---

### Post by chewearn on 2008-02-26
Here is the poll, NM winning (approx 60%) as of this post:
[http://ubuntuforums.org/showthread.php?t=587010](http://ubuntuforums.org/showthread.php?t=587010)

---

### Post by chalewa on 2008-02-26
i think it is in the repos?

---

### Post by enigma_0Z on 2008-02-26
Last time I checked, it wasn't in the repos

Is there any way to add custom wpa_supplicant config templates to NM? (this is one of the features that I really apreciate w/ wicd.

---

### Post by aysiu on 2008-02-26
> **AstalaVista said:**
> Here is the poll, NM winning (approx 60%) as of this post:
[http://ubuntuforums.org/showthread.php?t=587010](http://ubuntuforums.org/showthread.php?t=587010)
Thanks for the link. I've merged the two threads.

---

### Post by hegenious on 2008-02-26
wicd definately over nm

I am using wicd 1.4.2 and it works flawlessly

auto connects to my preferred ap - nm never could
never asks for the passphrase again - nm ... ](*,)
survives a loss - nm would start asking all over again
survives a reboot and just connects - need I say more

somehow the integration with the keyring manager never worked out right.
I should say to the defense of nm that it might have been that keyring was the culprit in my hassles.

Anyways and besides that, I think the applet is really nice and has about the same functionality as the Windows wireless applet which I happen to like. \\:D/

As another user pointed out, one very minor little thing that should be fixed  if possible) is the connect button should display "disconnect" when connected, and not "connect" as you already are ;)

---

### Post by tobydeemer on 2008-02-27
I tried WICD, and it seemed to be going well, but then broke my wireless, and degraded to not even recognizing the card. Then my ethernet as well started getting finnicky. So, back to NM for me.

---

### Post by Average Joe on 2008-02-28
With Network Manager I never managed to get my wireless connection to work when using:
a) a fixed IP address, AND
b) WPA2 security

It works fine when using either one of those (a or b) but the combination is a show stopper for me.

I (very) recently discovered WICD and I got a and b up and running in no-time. Great application. Got my vote.

---

### Post by enigma_0Z on 2008-02-28
funny really, but everywhere what I've been reading seems to say that those for which NM works fine haven't tried WICD... It's anecdotal, but this poll is probably tainted by the fact that new users have more exposure to NM since it's installed by default.

Anyways, I also forgot to add my vote...

WICD++

---

### Post by smartboyathome on 2008-02-29
> **enigma_0Z said:**
> funny really, but everywhere what I've been reading seems to say that those for which NM works fine haven't tried WICD... It's anecdotal, but this poll is probably tainted by the fact that new users have more exposure to NM since it's installed by default.

Anyways, I also forgot to add my vote...

WICD++

I used WICD for a while, but I think that Network Manager's interface is more intuitive. If they can just fix password saving and WPA2 better, then it will be a definite keeper (not like it already isn't).

---

### Post by enigma_0Z on 2008-02-29
> **smartboyathome said:**
> I used WICD for a while, but I think that Network Manager's interface is more intuitive. If they can just fix password saving and WPA2 better, then it will be a definite keeper (not like it already isn't).

Interface-wise, it really depends. As far as I can remember, the config for adding a new network was pretty simple in NM, but in order to connect, all the networks are in a right-click menu. If the interface is the only complaint, AFAIK the tray app for wicd uses dbus to talk to the daemon, so it would be as simple as redesigning the tray app. To WICD's criticism, the password and manual configuration boxes should be isolated so that you don't see all of the manual IP & DNS stuff if you just have to enter a password for the network (most public networks use DHCP anyway). But in WICD's defense, the app does make it very easy to configure all of the settings for the network. I think it should just put all of the manual IP stuff in a second groupbox.

The big feature that keeps me with WICD is the ability to create your own network (aka wpa_supplicant.conf) templates. As an example, one public network that I am on frequently uses an odd combination of authorization mechanisms for the wireless network. NM never could connect to this. It was at this point that I made myself a little command-line app to do the job, because I did have a working wpa_supplicant config that would work. WICD wouldn't connect either because the template wasn't there, but after some poking, I was able to make my own template and use it in WICD with hardly any hassle.

If NM has that ability, I'll try it again. Otherwise, WICD is still the better app IMO.

---

### Post by 23meg on 2008-02-29
A good resolution for this can be to have WICD packaged (it's not even in the repositories), get it into Main, and include it on the desktop CD, but not install it by default. This way, people who need it can install it without running into the catch-22 of having to go online and download it. It can also be a good idea to advertise its presence in the documentation, to increase its discoverability a little.

The following would need to happen:

[list][*] Package [is made]("https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages") and goes into Universe ([needs-packaging bug for WICD]("https://bugs.launchpad.net/ubuntu/+bug/134410"))
[*] [Main incluison report is written]("https://wiki.ubuntu.com/MainInclusionProcess")
[*] Test CD builds are made and tested, possibly involving removal of existing packages to make room
[*] Results are posted to and discussed on the [ubuntu-devel-discuss mailing list]("https://lists.ubuntu.com/mailman/listinfo/Ubuntu-devel-discuss")
[/list]

Anyone up to the job?

---

### Post by enigma_0Z on 2008-03-01
The WICD devs have created ubuntu debs: [http://apt.wicd.net/pool/gutsy/extras/wicd_1.4.2-1-all.deb](http://apt.wicd.net/pool/gutsy/extras/wicd_1.4.2-1-all.deb)

I'm not sure what they have done to include this into ubuntu repos, but that package works perfecty in my (and AFAIK anyone else's) ubuntu installation.

---

### Post by imdano on 2008-03-02
I think Adam might have started going through the process of getting it in the repos for Hardy, though I'm not 100% sure on that.  I know that it is packed or is getting packaged for debian, gentoo, arch linux, zenwalk, linux mint, and a couple of other distros.

I guess I'll throw in my two cents on this as a wicd developer.  NetworkManager has been under development several years longer than wicd, and as such is a more mature app in a lot of ways.  I think we have a better approach in some areas (usually related to giving users more direct control over managing things), and that we're making up a lot of ground on them rapidly.  Plus it seems wicd just works for some people where NM doesn't (and vice versa, to be fair).

But for now it's probably better for a distro like Ubuntu to stick with an app like NM as the default, which has features like VPN plugins, dialup support, etc., that we don't have yet.   Features like that might not be important at all for a lot of users but they are important for Ubuntu to have included by default.  Until these things get integrated into wicd I don't think the Ubuntu team will make the switch.

If some people prefer our app, or if lightweight distros would rather ship with wicd, that's great, if not, that's fine too.  Linux is all about choice, right?

---

### Post by 23meg on 2008-03-02
[QUOTE=imdano]I think Adam might have started going through the process of getting it in the repos for Hardy, though I'm not 100% sure on that.[/QUOTE]

I haven't seen any progress in the needs-packaging bug or in REVU, and it's too late for Hardy anyway; what I said in my last post can be done for Intrepid.

---

### Post by kdw on 2008-03-05
WICD because it handles my "edge cases" perfectly, laptops with eth0/LAN & eth1/WLAN.
Wired interface must allow Default-static LAN profile, and a wired-DHCP profile for on the road. WLAN must handle WPA, WEP easily for novice users.
No configuration is needed after default profiles are set, so users can plug/unplug from the LAN without having to configure anything, just click "Connect".

Thanks WICD!  :)

---

### Post by TimelessRogue on 2008-03-26
I must agree with imdano ... wicd probably should not be the default network manager at this point due mostly to the fact that so many have become accustomed to NM's look and feel.  I wouldn't ask for that or even suggest it at this point.  My suggestion would be, however, that at least wicd be offered initially in the repositories as an alternative for those whose wireless is not recognized or is a pain in the tookus to use via wine or b43 (for Broadcom users) with proprietary wireless drivers.  At least then they would not have to go find and install it for themselves (wicd that is) ...

---

### Post by qamelian on 2008-03-26
> **enigma_0Z said:**
> The WICD devs have created ubuntu debs: [http://apt.wicd.net/pool/gutsy/extras/wicd_1.4.2-1-all.deb](http://apt.wicd.net/pool/gutsy/extras/wicd_1.4.2-1-all.deb)

I'm not sure what they have done to include this into ubuntu repos, but that package works perfecty in my (and AFAIK anyone else's) ubuntu installation.
No, it doesn't. If you've read through the whole thread, you will see where I've posted previously that Wicd does not work correctly on my laptop. I've just recently tried it again on the same laptop which is now running the  Hardy beta and Wicd is working worse than ever. It frequently and repeatedly breaks my connection, often refuses to see my router at all, and just generally doesn't work for me. NM, on the other hand, has always worked flawlessly on my laptop and still does. I agree that it would be great to have Wicd in the repos for those that need it, but I don't think I'll ever waste my time on it again.

---

### Post by enigma_0Z on 2008-03-26
Hmm... I wonder why one works for some people, while the other works for others...

AFAIK I have well-supported hardware (Intel Pro Wireless ABG 3945, iwl3945 driver), yet NM refuses to connect to a WPA2 AES/CCMP network. Furthermore, as far as I know, I can't add any special settings for obscure and specific networks (such as my school's).

I suppose that whatever most people are familiar with should be the default option, but it would be a lot nicer if WICD was:

1. In the repos.
2. Presented in the GUI as an alternative if N/M doesn't work (to make it easier for new users to try WICD)

---

### Post by imdano on 2008-03-27
Having wicd in the repos would be fine, but having both installed at once doesn't work out too well, since both try to take control of your connections.  It ends up causing problems.

---

### Post by doorknob60 on 2008-04-02
Earlier I posted that NM should be the default, but when I upgraded to Hardy on my laptop, I worked for hours to get wireless to work (using ndiswrapper mostly), but NM just wouldn't connect. I finally installed Wicd and everything worked perfect first time! So, Wicd should for sure be in the repositories, and there should be like a Wireless Help section easily findable to new Ubuntu users that explains ndiswrapper and tells about trying Wicd if NM doesn't work etc. That would make wireless much less painful for new users. EDIT: Just to clarify, I still think NM should be default :D

---

### Post by smartboyathome on 2008-04-02
Network Manager should be default, but I think WICD would be good to have on the CD repo (if there could be enough room).

---

### Post by ftgtf on 2008-04-03
One more vote for WICD here.

Reason: it doesn't try to reinvent the wheel. It uses wpasupplicant.conf style for configuration, so I was able to connect to an EAP-WPA-TLS network by creating my own template. WICD will simply connect to any wireless network that you can connect through CLI.

---

### Post by lindkvis on 2008-04-03
This is a very simplistic solution and if this solution was to be applied in general throughout Ubuntu we would end up with an inconsistent patch work of incompatible solutions.

Network Manager may not be perfect, but it has been designed in the right way.

It has an UI-agnostic core (so it supports both Ubuntu and Kubuntu), it has proper desktop and DBus integration and it has proper cross-distribution support. It has in other words been created to fit in with the rest of the OS.

If Network Manager doesn't work properly for some people (and according to this thread, WICD doesn't work for everyone either), then these are bugs in NM that needs to be fixed. Throwing away a perfectly well designed base is taking an extremely short term approach which has never worked in software engineering.

Linux distributions have traditionally been a patch work of solutions that all work individually but seems like a mess when combined together. A **LOT** of work has been put in to rectify this, and Ubuntu has helped greatly to bring this situation under control.

Replacing NM with WICD would be like a return to these dark ages and luckily the Ubuntu core developers are far to sensible for this poll to ever matter. 

Be glad that you yourself can replace NM with WICD if it works better for you, but it is never going to happen regardless of what this poll says.

---

### Post by qamelian on 2008-04-03
> **ftgtf said:**
> WICD will simply connect to any wireless network that you can connect through CLI.
People keep saying this but it simply isn't true. I can connect to my home wireless easily and reliably via networkmanager and via CLI. I cannot through Wicd. Either the connection is ridiculously unstable, dropping every few minutes and often refusing to restart, or it just doesn't work at all. I've tried Wicd on many occasions and it is definitely not the cure-all that some users make it out to be. Yes, it works fine for some people but for others it simply doesn't and it should not continue to be portrayed as "just working" because this is quite simply false.

---

### Post by Jussi Kukkonen on 2008-04-05
> **enigma_0Z said:**
> AFAIK I have well-supported hardware (Intel Pro Wireless ABG 3945, iwl3945 driver), yet NM refuses to connect to a WPA2 AES/CCMP network.

I wish that was well-supported, but unfortunately the driver is quite new (at least we don't have to live with ipw3945 anymore). The good thing is that development seems to be quite rapid: [http://intellinuxwireless.org/](http://intellinuxwireless.org/)

[QUOTE=qamelian]
I've tried Wicd on many occasions and it is definitely not the cure-all that some users make it out to be. Yes, it works fine for some people but for others it simply doesn't and it should not continue to be portrayed as "just working" because this is quite simply false. [/QUOTE]

Amen. I'm not sure why this issue seems to turn into a religious issue... Reminds me of gentoo-enthusiasts when that craze was at its worst (not trying to discredit the distro, just the zealots).

---

### Post by Vadi on 2008-04-05
Yeah, neither seems to be having a clear win here, so no advantage is gained by doing a *lot* of work to replace NM.

---

### Post by love2learn on 2008-05-04
IMHO NM blows, it may have it all together on the backend ( this i do not know ) but at a glance on the frontend wicd is sooo much better:

A) it shows the type of encryption
B) the channel all connections are on
C) the hidden SSID button
D) the multiple different connection types
E) it can run scripts 
F) you can set your static ips up right off the front end
G) you can set it to start up with your system (this was argued)
H) it has a system tray button (this was argued)
I) it even shows mac and IP addy on connect ( ip on hover )

This is all off of JUST the system tray icon... with NO extra configuration...
Can NM do ANY of that? ( okay maybe G,H, ) 

I went LOOKING for a wireless manager because NM didnt have what i wanted and I knew it lacked all of these things. I havent had WICD crash on any of the laptops i have installed it on so not even stability is a question.

Hands Down WICD.

---

### Post by [h2o] on 2008-05-04
> **love2learn said:**
> 
A) it shows the type of encryption
B) the channel all connections are on

Seriously, when do you need to know? 

> 
F) you can set your static ips up right off the front end

Which is being worked on, if I remember the blogosphere right.

> 
G) you can set it to start up with your system (this was argued)

I am automatically connected on login. What are you talking about?

> 
H) it has a system tray button (this was argued)

Uhm, so does NM?

> 
I) it even shows mac and IP addy on connect ( ip on hover )

"Connection Information" in NM shows all that.

---

### Post by enigma_0Z on 2008-05-04
After using WICD for quite a while (approx. 6 months+), it seems that there are a few outstanding issues with it.

The first is that autoconnect fails some times when ethtool reports wired connection status incorrectly (to be expected I suppose)

It also freezes some times if it's in the middle of an autoconnect--double-clicking on the tray icon sometimes doesn't bring up the GUI right away.

Still, the features that I need (custom wpa_supplicant config for one) are in WICD, and it shows great potential. WICD still has my vote.

---

### Post by love2learn on 2008-05-06
> **'[h2o] said:**
> Seriously, when do you need to know? 
Lets just say, "it is a nice feature for those who need to use it." and leave it at that.
 
 
> **'[h2o] said:**
>  Which is being worked on, if I remember the blogosphere right. 
Yeah, it is being worked on..... Meaning, it is not available yet. Why did you even try to defend this?
 
 
> **'[h2o] said:**
> 
I am automatically connected on login. What are you talking about? 
The "this was argued" points I made were in reference to the thread itself. People were arguing that WICD did not have these features.
 
> **'[h2o] said:**
> 
Uhm, so does NM? 
Uhm, read my statement above this one again.
 
> **'[h2o] said:**
>  "Connection Information" in NM shows all that. 
The key words I used is "on connect" in that sentence. Not, "after a few clicks". But that is okay.
 
 
NM has a better working backend ( so I am told ) and that is what they focused on. That is fine, but WICD works for me and my traveling laptop and I get an abundance of information right off the first page of the gui. That is the only real point I am getting at. 
 
IMHO, NM seems a bit windowish and tries to hide or not reveal the information at first glance. That is okay for people that just want the machine to work ( which is what Ubuntu is going for so why people are arguing for WICD to be put in the distro is a bit off to me )

---

### Post by quickshade on 2008-05-06
It's funny, I see developers saying that we should use network manager because it's easier to setup in the distro, yet they don't think about the end user and how they will see it. If I am a new user and spend 20 minutes trying to connect to the Internet via a wired connection compared to just clicking ok on Windows. I'm not saying that we should use a windows attempt to fix this problem. But we aren't thinking enough about the end users in most cases. Yea WICD might not be easy to add to the distro, but if it works better than network manager and is easier to use then why not?

Of course we should encourage developers trying to challenge each others app. As thats great for making both of them improve.

---

### Post by qamelian on 2008-05-06
> **quickshade said:**
> It's funny, I see developers saying that we should use network manager because it's easier to setup in the distro, yet they don't think about the end user and how they will see it. If I am a new user and spend 20 minutes trying to connect to the Internet via a wired connection compared to just clicking ok on Windows. I'm not saying that we should use a windows attempt to fix this problem. But we aren't thinking enough about the end users in most cases. Yea WICD might not be easy to add to the distro, but if it works better than network manager and is easier to use then why not?

Of course we should encourage developers trying to challenge each others app. As thats great for making both of them improve.
Read through the whole thread. Wicd is not easier and does not work better for some users, including me. It has never worked well for me, yet NM has always worked well for me right out of the box. The last couple of attempts at using Wicd have finally convinced me that I will never try it again.

---

### Post by quickshade on 2008-05-06
Not to be mean, but you should read through the whole thread, some people get NM to work, some don't. While some people get WICD to work, and some (like you) don't. All I was stating is that if WICD keeps improving like it does then the developers should rethink the whole "it's easy for us so why switch" saying. 
just because it doesn't work for you doesn't mean that it doesn't work for other people. I'm not saying it should be a replacement, but it should be added to the repo.

BTW I think your a little harsh on everyone here. Every thread post I've seen by you seems to criticize what other people think and praise what Ubuntu does. I hate to say it but Ubuntu is not the best OS ever created. It's a great Linux Distro, but there are far better options out there. And Ubuntu is far from perfect. People shouldn't fear change, otherwise Windows would be the only OS on the market.

---

### Post by imdano on 2008-05-06
> **quickshade said:**
> It's funny, I see developers saying that we should use network manager because it's easier to setup in the distro, yet they don't think about the end user and how they will see it. If I am a new user and spend 20 minutes trying to connect to the Internet via a wired connection compared to just clicking ok on Windows. I'm not saying that we should use a windows attempt to fix this problem. But we aren't thinking enough about the end users in most cases. Yea WICD might not be easy to add to the distro, but if it works better than network manager and is easier to use then why not?

Of course we should encourage developers trying to challenge each others app. As thats great for making both of them improve.We're working on improving support for distros that aren't debian based, though it's a little bit challenging with a small development team all of whom run Ubuntu.  But the backend is more stable and uses less CPU in the next version, and there is a very long list of new features and bug fixes as well.

---

### Post by qamelian on 2008-05-06
> **quickshade said:**
> Not to be mean, but you should read through the whole thread, some people get NM to work, some don't. While some people get WICD to work, and some (like you) don't. All I was stating is that if WICD keeps improving like it does then the developers should rethink the whole "it's easy for us so why switch" saying. 
just because it doesn't work for you doesn't mean that it doesn't work for other people. I'm not saying it should be a replacement, but it should be added to the repo.

BTW I think your a little harsh on everyone here. Every thread post I've seen by you seems to criticize what other people think and praise what Ubuntu does. I hate to say it but Ubuntu is not the best OS ever created. It's a great Linux Distro, but there are far better options out there. And Ubuntu is far from perfect. People shouldn't fear change, otherwise Windows would be the only OS on the market.
It isn't a matter of fearing change. I am really tired of hearing people boosting Wicd as some kind of cure-all that magically fixes all network woes when this is most assuredly not the case. When people stop spreading misinformation, I will stop criticizing that misinformation. You will find at least a couple of posts in this thread in which people specifically say the Wicd works every time. This is simply not true and to keep saying that it is does not help anyone. And if you did, in fact, bother to read my posts, I also agreed that Wicd should be an option in the  repos even though I don't support the idea of it being part of the default install. 

Are you trying to say that there is something wrong without pointing out blatant misinformation? That is all I have done and I will continue to do so when people make claims that I know to be completely false.

---

### Post by quickshade on 2008-05-06
You yourself said that Network manager works every time. and I'm not saying it should be default, I'm saying that if it keeps improving and more people find it easier to use then they should think about switching......your connection problem could be due to a bug, and with more people testing it the more likely these bugs are to be fixed.

---

### Post by quickshade on 2008-05-06
> **imdano said:**
> We're working on improving support for distros that aren't debian based, though it's a little bit challenging with a small development team all of whom run Ubuntu.  But the backend is more stable and uses less CPU in the next version, and there is a very long list of new features and bug fixes as well.
Do you have a link so I could read up on it?

---

### Post by imdano on 2008-05-06
You can take a look at the latest code at our [svn repository.](http://wicd.svn.sf.net)  The testing-1.5.0 branch will become the next release soon.  The experimental branch is less stable but has more/improved features (like a network list dropdown when you right click the tray icon, and a much faster backend).  The experimental branch also has the preliminary (read: mostly broken) work I started on better cross-distro support in the daemon's init scripts.  Here's a list of most of the new/improved stuff coming in 1.5.0:
```
Wicd 1.5.0 new Features:
- Improved GUI.
    - Moved advanced settings from an expander to it's own dialog window.
    - Replaced LinkButtons used for "Connect" and "Scripts" with actual gtk.Buttons.
    - Moved signal strength and MAC address to the top level of wireless network entries.
    - GUI network list becomes inactive while refreshing.

- Rewritten script system
    - Scripts are now in their own dialog box (which runs as a separate process from the GUI), instead of an expander.
    - Scripts now always run as root, and require root access to edit.
    - Scripts (hopefully) actually work all the time now.

- Combined gui.py and tray.py into one script called wicd.py.  It is still possible to run gui.py by itself, using the --no-tray argument.

- Ridiculous amount of refactoring of the code
    - Users won't notice this too much in use (although it may have fixed some bugs, and made implementing features easier), but the 
      source code is about 1000x more readable/modularized now.

- Added a suspend script so that wicd will stop polling network status when a laptop is hibernated/suspended.

- Wicd will now let you know if your wireless kill switch is active.

- More flexibility in external tool choice.
    - Multiple DHCP clients supported.
        - Wicd will try to choose between dhclient, dhcpcd, and pump. (Or the user can specify which).
    - Multiple link detection tools supported.
        - Wicd will try to choose between ethtool and mii-tool (or the user can pick).

- Added a check during the connection process to try and determine if your encryption information is correct.
    - This means a failed connection won't get all the way to the "Getting IP Address..." stage when a password
      is bad, and will give you a much better idea of where the problem lies.

- Added support for using global settings for a particular essid, so that settings for multiple APs with the same
  essid don't have to be copied over and over again.

- Wicd-Monitor automatically rescans for wireless networks every two minutes, and alerts the gui to update as well.
  
- Added a setup.py script for building from source that will try to put the init scripts in the right place, depending on the distro.

- Tray icon animations can now be turned off with a command line argument.

Bug Fixes:
- All the static IP/DNS problems should be ironed out.
- All unicode problems should be fixed.
- Wicd will verify that IP/Gateway/DNS addresses are valid before applying them to a network.
- Fixed bug where tray icon would sometimes disappear.
- You no longer have to create a wired profile on install before you can connect to a wired network (one is added by default).
- Fixed occasional failure to autoconnect to a wired network even when one is available.
- Fixed bug where autoconnect wouldn't fall back to wireless if a wired attempt failed.
- Fixed bug where wired-settings.conf would get corrupted sometimes, breaking the daemon.
- Greatly reduced the number of external program calls used in the connection monitoring process, which should reduce CPU usage.
- Moved all connection monitoring code to a separate process that gets launched by the daemon (you don't need the tray running for automatic reconnection to work properly anymore).
- Logging system doesn't spam as much and hopefully provides more useful output. (This still needs some work though)
- Debug mode improved (though still pretty spammy!)
- Hopefully some auto-reconnect after suspend issues will be fixed with the suspend script.
- Wicd now uses /sys/class/net/ to determine what wireless interfaces are available, instead of parsing ifconfig, saving resources and being more reliable.  Also use /sys/class/net/<iface> to get network activity for the tray, instead of /proc/net/wireless
```

---

### Post by quickshade on 2008-05-07
Thanks for the list. Looks like a lot of backend work to improve frontend stuff. Well done.

---

### Post by qamelian on 2008-05-07
> **quickshade said:**
> You yourself said that Network manager works every time. and I'm not saying it should be default, I'm saying that if it keeps improving and more people find it easier to use then they should think about switching......your connection problem could be due to a bug, and with more people testing it the more likely these bugs are to be fixed.
Please stop twisting my words. I did NOT say that Network Manager works every time. I specifically said that it has always worked flawlessly FOR ME and on every sytem I have used it on. No more and no less. It is extremely bad form to claim that I said something that I didn't and I find it extremely insulting when people do so.

I don't intend to test Wicd any further as I don't need to. It has never worked right for me, but NM does. Wicd offers no features that I consider compelling or relevant and so is of no benefit to me. If Wicd did offer me anything useful, I would test it as I have done other applications in which I have seen value. If you or others see value in it, by all means test away and help to improve the app. But don't expect me to do so when it provides me with no benefits over and above what I want and need from a network manager.

---

### Post by quickshade on 2008-05-07
Hence why this is a development section.

---

### Post by smartboyathome on 2008-05-07
> **quickshade said:**
> Hence why this is a development section.

Yes, but it isn't as easy to use as Network Manager either imo. Ubuntu tries to keep things simple so that it "just works", WICD doesn't do this. It would be fine to include it in the repository, or perhaps on the CD if there is space, but I don't think it would be very wise to include as default replacing network manager.

---

### Post by quickshade on 2008-05-07
I agree that it should be in the repo, but if it becomes more stable and easier to use (like he said about 1.5) then Ubuntu should think about testing both of them.

---

### Post by smartboyathome on 2008-05-07
I don't think that it will be as easy to use with 1.5. It does have the drop down list with it, but that is with a right click, and that isn't as easy as just clicking with network manager. Also, you can't test them side by side, and Network manager is getting new features as well with its up-and-coming release, so it may become better.

---

### Post by Whiffle on 2008-05-07
> **smartboyathome said:**
> Yes, but it isn't as easy to use as Network Manager either imo. Ubuntu tries to keep things simple so that it "just works", WICD doesn't do this. It would be fine to include it in the repository, or perhaps on the CD if there is space, but I don't think it would be very wise to include as default replacing network manager.


Simple and "just works" aren't the same thing.  Last time I used NM, which admittedly was a while ago, it didn't "just work," and I've even got one of the most well supported chipsets (ipw2200).  In fact, it worked, and then it didn't.  Not reliable at all.  On the other hand, WICD worked.  It still works, and its been _much_ less flakey than NM was.  NM manager could be awesome, and probably will be eventually, but every time I've used it, it wasn't reliable.

---

### Post by smartboyathome on 2008-05-07
Weird, I have never had that happen to me. The only problem is that it doesn't connect through my wireless extender (though neither does Windows).

---

### Post by rahulthewall3000 on 2008-05-13
OK, having started the thread, I can say some things about NM. My problems started since the days of development of feisty and since then I have always used WICD. I have an ipw3945 so it is pretty well supported. I have tested NM on gentoo, arch linux and ubuntu and it has never, i repeat never, worked completely (note completely) for me when it comes to wireless networks. For wired networks it is pretty cool as it works neatly and I have no complaints with it there. But when it comes to wireless networks it has a nasty habbit of connecting to some wireless networks and ignoring some. 
Even when it works, WICD is way faster that NM in connecting to wireless networks. Moreover, the refresh option in WICD works really well. This would be my partial opinion, but I would chose WICD as the default network manager over NM any day, simply because it just works.
But then, it does not work for some people and thus the idea has always remained that therefore we should keep NM as default. The question that has not still been answered is the fact that why not replace it with WICD since that seems to work for the same number of people (judging from the poll results). 

Rahul

---

### Post by smartboyathome on 2008-05-13
These poll results are biased. Most of the people who voted in the poll had problems with NM, while most of the people who don't vote in the polls decide not to because they have no problems and don't want to waste the effort. Also, I have a 4965 which works great with NM, and the only complaint I have is the lack of a refresh button (I think that they will work on that soon, at least I hope :roll:). I did use WICD when I had my old laptop with a 3945, though, during Feisty, but when Gutsy rolled around I no longer needed it due to the new laptop.

---

### Post by lcohen999 on 2008-05-14
Until WICD has integrated VPN support, this pool is useless (IMHO)

---

### Post by MemoryDump on 2008-05-14
I just tried installing WICD remotely and now I've lost my connection to my computer :(
it seems it took the interface down and hasn't brought it back up :(

was following the instructions from [https://help.ubuntu.com/community/WICD](https://help.ubuntu.com/community/WICD) replacing "gutsy" with "hardy" which seemed to have work as I was able to install it. (aparently)

*sigh*

---

### Post by smartboyathome on 2008-05-14
That is why you should keep a backup of your NM debs. :(

---

### Post by MemoryDump on 2008-05-14
> **smartboyathome said:**
> That is why you should keep a backup of your NM debs. :(

yeah.. the wiki fails to mention that.. and the fact that it'll take your network completely down :(

oh well.. live and learn

---

### Post by mringer on 2008-06-13
I think that NM would be enormously improved if properly documented.
(maybe it is, if so, where?)

2 examples.

1. Help file says that networking should Just Work. So, what should
I do if it Just Doesnt?

2. Apparently access is controlled on a per-user basis. So the 
super-user can specify what each user can do. How?

---

### Post by devnulljp on 2008-06-15
I jus installed wicd as I've been having a minor probelm with knetworkmanager (kde in kubuntu) and while I like the interface and would liek to keep it, I just can't get it to work with WEP or WPA on my router. 
I have an Intel 2200BG using ipw2200, which worked perfectly under knetworkmanager and will work with wicd as long as I turn off encryption (so the drivers and hardware are all fine). As soon as I turn on encryption on the network, it just won't work. I've tried with and without quotes on the WEP hex key, but it makes no difference. There are no characeters reqyiring escaping in the key, just all alphanumerics (and I've double checked the key is correct). 

Any ideas? I don't even know how to begin debugging it...

Those of you saying wicd has better wireless support -- in what way? I see thatit promises WPA, which would be nice, but how do you set it up to work with an encrypted network?

EDIT: I just ran through it again and this time did tail -f /var/log/syslog

```
Jun 15 20:40:38 hostname avahi-daemon[5010]: Interface eth0.IPv4 no longer relevant for mDNS.
Jun 15 20:40:38 hostname avahi-daemon[5010]: Withdrawing address record for fe80::20d:60ff:fec9:9060 on eth0.
Jun 15 20:40:38 hostname dhclient: receive_packet failed on eth0: Network is down
Jun 15 20:40:55 hostname kernel: [ 4286.906607] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 15 20:40:55 hostname kernel: [ 4286.910263] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jun 15 20:40:55 hostname dhclient: There is already a pid file /var/run/dhclient.pid with pid 3132
Jun 15 20:40:55 hostname dhclient: removed stale PID file
Jun 15 20:40:55 hostname dhclient: Internet Systems Consortium DHCP Client V3.0.6
Jun 15 20:40:55 hostname dhclient: Copyright 2004-2007 Internet Systems Consortium.
Jun 15 20:40:55 hostname dhclient: All rights reserved.
Jun 15 20:40:55 hostname dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Jun 15 20:40:55 hostname dhclient:
Jun 15 20:40:56 hostname dhclient: Listening on LPF/eth1/xx:xx:xx:xx:xx:xx
Jun 15 20:40:56 hostname dhclient: Sending on   LPF/eth1/xx:xx:xx:xx:xx:xx
Jun 15 20:40:56 hostname dhclient: Sending on   Socket/fallback
Jun 15 20:40:57 hostname dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Jun 15 20:41:01 hostname dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Jun 15 20:41:09 hostname dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
Jun 15 20:41:20 hostname dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Jun 15 20:41:27 hostname dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 1
Jun 15 20:41:28 hostname dhclient: No DHCPOFFERS received.
Jun 15 20:41:28 hostname dhclient: No working leases in persistent database - sleeping.
Jun 15 20:41:28 hostname avahi-autoipd(eth1)[7242]: Found user 'avahi-autoipd' (UID 103) and group 'avahi-autoipd' (GID 109).
Jun 15 20:41:28 hostname avahi-autoipd(eth1)[7242]: Successfully called chroot().
Jun 15 20:41:28 hostname avahi-autoipd(eth1)[7242]: Successfully dropped root privileges.
Jun 15 20:41:28 hostname avahi-autoipd(eth1)[7242]: fopen() failed: Permission denied
Jun 15 20:41:28 hostname avahi-autoipd(eth1)[7242]: Starting with address 169.254.4.40
Jun 15 20:41:33 hostname avahi-autoipd(eth1)[7242]: Callout BIND, address 169.254.4.40 on interface eth1
Jun 15 20:41:33 hostname avahi-daemon[5010]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.40.
Jun 15 20:41:33 hostname avahi-daemon[5010]: New relevant interface eth1.IPv4 for mDNS.
Jun 15 20:41:33 hostname avahi-daemon[5010]: Registering new address record for 169.254.4.40 on eth1.IPv4.
Jun 15 20:41:37 hostname avahi-autoipd(eth1)[7242]: Successfully claimed IP address 169.254.4.40
Jun 15 20:41:37 hostname avahi-autoipd(eth1)[7242]: fopen() failed: Permission denied
```

That fopen() failed looks suspicious. It looks like it kinda works, but not quite. It's trying to get an IP address by dhcp, what is weird is that  it gets an IP address of 169.254.4.40, which is not on my network (which is a standard 192.168.1.0/255 private network).
I did a who is on that IP and it bears no resemblance to my ISP / country or anything else either.
Doesn't work if I give it a static IP address either... 
Any ideas?

---

### Post by danboid on 2008-06-18
wicd should've been made the default a long time ago- I fully believe Ubuntu and Linux in general would be much more widely used and accepted if wicd was the default networking tool in the 'buntus and I was very disappointed that wicd didn't at least make it into the repos for 8.04. I can't believe its still missing from them too! In my experience, nm is only any good if you're connecting DHCP via ethernet- anything else it normally fails miserably with and you're left with cli connect or nothing. wifi-radar has been useless to me and I run GNOME or openbox normally so I avoid knetworkmanager.

NM is a joke to me- you can crow about its super-slick underbelly all you want but if its interface makes no sense and the app itself doesn't work in many common scenarios- people are going right back to Windows or Mac. Most will not take the time to hunt for a solution- they probably can't access the net anyway as all they've got is NM. Being able to easily connect to the net is of absolute prime importance to most computer users today.

The only problem I've encountered with wicd (current stable- I'll be trying the svn version soon) is that sometimes auto-connect stops working but I can cope with that as its just a case of clicking connect, instead of the multiple-password nightmare of nm.

nm may do dial-up and vpn (hopefully it does them much better than it handles ethernet and wifi connections!) but these really are only of interest to a minority of users. 99% of ubuntu users will be connecting to the net either via a wired ethernet connection or a protected wifi connection and this is where wicd excels and wins hands down in my experience.

I really appreciate Ubuntus large software repos but, because of NMs many shortcomings I couldn't recommend it yet to any Linux newb. No, I would have to recommend Mandriva as its net_applet has provided me with the only perfect Linux wifi/internet experience. Maybe if this new version of wicd made it into the standard ubuntu repos and became the default network tool I would recommend ubuntu instead - this is how important good wifi support is for an os these days!

Speaking of Mandrivas net_applet- can we not run this without porting all of drakconf over to ubuntu/debian? Surely not? Be good to have another choice under ubuntu!

---

### Post by billenbois on 2008-06-19
I never tried WICD so i'll try later.
NM looks fine but I do have some quirks with it:

- Sometimes it doesn't try to reconnect to the correct WLAN, eg I have a WPA-enabled WLAN which NM has the password for. Some guy has a freely accessible WLAN with no encryption/key. I turn on the laptop, usually it selects my WLAN. But sometimes, it doesn't, it selects the other one (which I used like once in my life).

Terribly annoying. Windows does not do that, neither MacOSX. They take the last used one all the time.

- VPN support is "funny". it doesnt really work in many cases. Often have to configure stuff by hand then NM is just a shortcut to my configuration instead of typing the command in the terminal.

- in wired mode, the ethernet cable wire on the icon sometimes blinks (probably to say "hi im still alive"). I hate this so much. When i'm working it distract my eye, like IM would do. Might even patch this myself.

---

### Post by smartboyathome on 2008-06-19
> **danboid said:**
> wicd should've been made the default a long time ago- I fully believe Ubuntu and Linux in general would be much more widely used and accepted if wicd was the default networking tool in the 'buntus and I was very disappointed that wicd didn't at least make it into the repos for 8.04. I can't believe its still missing from them too! In my experience, nm is only any good if you're connecting DHCP via ethernet- anything else it normally fails miserably with and you're left with cli connect or nothing. wifi-radar has been useless to me and I run GNOME or openbox normally so I avoid knetworkmanager.

This is the opposite of some users experiences (as stated above), though with mine I found both to work just fine, but prefer NM. The GUI is just better imo, though I have used WICD with enlightenment due to no system tray support for NM. I am guessing it depends on the card if WICD or NM would work for you.

> **danboid said:**
> NM is a joke to me- you can crow about its super-slick underbelly all you want but if its interface makes no sense and the app itself doesn't work in many common scenarios- people are going right back to Windows or Mac. Most will not take the time to hunt for a solution- they probably can't access the net anyway as all they've got is NM. Being able to easily connect to the net is of absolute prime importance to most computer users today.

Its interface DOES make sense. I find it much easier to use than WICD's. If they don't want to take time to learn NM, they won't want to learn WICD either. I know it is more like Mac's network tool than Windows' (which WICD is more like). I have let other people try it and they don't ask how to get online. They mostly ask how to install software or other things. They are thinking of including it on the CD so that if people can't connect, they can try out WICD to see if it is better.

> **danboid said:**
> The only problem I've encountered with wicd (current stable- I'll be trying the svn version soon) is that sometimes auto-connect stops working but I can cope with that as its just a case of clicking connect, instead of the multiple-password nightmare of nm.

I haven't had a multiple password "nightmare" that you seemed to experience. I only had to enter my password once for NM, and then GNOME's password keychain remembered it from then on. I do have a hiccup where I cannot connect to the internet sometimes unless I go by my main router (I run off an extender part of the time), but Windows has this problem too.

> **danboid said:**
> nm may do dial-up and vpn (hopefully it does them much better than it handles ethernet and wifi connections!) but these really are only of interest to a minority of users. 99% of ubuntu users will be connecting to the net either via a wired ethernet connection or a protected wifi connection and this is where wicd excels and wins hands down in my experience.

What about in still developing countries where Linux is of great interest? You giving them the boot because they have what you consider a "minority internet connection"?
That is your experience, but I have had different ones, and so has others above. Let me ask you this: Do you use the latest version of WICD? I know Ubuntu doesn't use the latest version of NM because it doesn't fit its stability requirements usually.

> **danboid said:**
> I really appreciate Ubuntus large software repos but, because of NMs many shortcomings I couldn't recommend it yet to any Linux newb. No, I would have to recommend Mandriva as its net_applet has provided me with the only perfect Linux wifi/internet experience. Maybe if this new version of wicd made it into the standard ubuntu repos and became the default network tool I would recommend ubuntu instead - this is how important good wifi support is for an os these days!

Ok, then. Don't you think you should at least TRY NM to see if it works on the people's computers? They ARE considering including WICD on the cd, like I said above, and 8.10 will be working on wireless support. So if you are recommending Mandrivia instead of also Ubuntu and others, it is only a loss to the users whom you recommend and are trying to find a distribution which fits them.

> **danboid said:**
> Speaking of Mandrivas net_applet- can we not run this without porting all of drakconf over to ubuntu/debian? Surely not? Be good to have another choice under ubuntu!

It runs on Qt, doesn't it? It would have to be programmed in GTK in order to get it in Ubuntu, which you might want to do. I wouldn't know if it would need drakconf, but if it is dependent on it in mandrivia, it may have to.

---

### Post by aysiu on 2008-06-19
Even though I'm a fan of Network Manager's interface, I did just recently switch to WICD, as there is some bug whereby I cannot autologin and have Gnome's keyring manager *not* prompt me for a password for my network.

In WICD, the network password is stored for me, and I'm not bothered by any prompts.

---

### Post by smartboyathome on 2008-06-19
> **aysiu said:**
> Even though I'm a fan of Network Manager's interface, I did just recently switch to WICD, as there is some bug whereby I cannot autologin and have Gnome's keyring manager *not* prompt me for a password for my network.

In WICD, the network password is stored for me, and I'm not bothered by any prompts.

Are you using GDM? I think if you don't use that it won't connect to the gnome keyring manager - this would happen for any app dependent on that.

---

### Post by aysiu on 2008-06-19
> **smartboyathome said:**
> Are you using GDM? I think if you don't use that it won't connect to the gnome keyring manager - this would happen for any app dependent on that.
But if it doesn't connect to Gnome's keyring manager, I'll just be prompted by Network Manager for the wireless key.

---

### Post by lithorus on 2008-06-20
> **aysiu said:**
> But if it doesn't connect to Gnome's keyring manager, I'll just be prompted by Network Manager for the wireless key.

And you have libpam-gnome-keyring installed?

---

### Post by aysiu on 2008-06-20
> **lithorus said:**
> And you have libpam-gnome-keyring installed?
Yes.

When you set to autologin (which makes sense on an Eee PC), you get prompted, even with *libpam-gnome-keyring* installed.

---

### Post by smartboyathome on 2008-06-20
Aysiu, I am testing autologin on my laptop and will see if I get the same results. I know I had to do the same when I broke GDM, but I fixed it and will be able to test it.

---

### Post by rahulthewall3000 on 2008-06-23
All I have to say is that the latest version of NM works for me as almost as well as WICD. It still has some issues whereby it will connect to the wireless in some places (like the CS lab at my university) but not at others. (like the lecture halls). Don't know why. Therefore I stick with WICD. Also, WICD stores passwords itself. No need of gnome-keyring-manager, which I anyhow do not like.
What I think is that WICD should be moved to the official repos. It just gives the users another viable option in case they do not like NM. No need to replace anything. And I know that it is very easy to add the wicd repo to the sources, but half the users who are new to Ubuntu would be afraid to experiment. (considering that many take the first steps into Linux through Ubuntu - which is the best part about Ubuntu.)

---

### Post by smartboyathome on 2008-06-23
Your post, rahulthewall, expresses very well why I advocate that WICD be included on the CD, but not default. It is there in case its needed, but not default and there is no need to replace anything.

---

### Post by _obelix_ on 2008-06-23
Network-Manager is great. I use them with network-manager-openvpn and network-manager-vpnc. WICD dosen't have VPN integration.

Regards

Obelix

---

### Post by rahulthewall3000 on 2008-06-24
Please, the network manager vpn has never worked for me. vpnc is the best in that regard.

---

### Post by sujoy on 2008-06-24
i use WICD in all the distros, works great, no hassle for me. :)

---

### Post by gfg on 2008-06-24
> **aysiu said:**
> Yes.

When you set to autologin (which makes sense on an Eee PC), you get prompted, even with *libpam-gnome-keyring* installed.

Set the gnome-keyring password for wireless to blank, and it will work.

---

### Post by Gina on 2008-06-26
I've never tried WICD - I find MN quite adequate.

---

### Post by Agent86 on 2008-06-27
I've been through the growing pains of Network Manager and for me and my network it works flawlessly in Hardy. I tried WICD in some of NM's darker days, and it didn't work either.

If you must have WICD, make it an optional install from the CD. But if there's only room for one, keep NM.

---

### Post by mringer on 2008-07-03
Neither WICD nor NM can be regarded as satisfactory without a lot more work.

1. Bugs. The man page for NM says that networking should Just Work. This implies that anybody who fails to connect with NM has encountered a bug. I suspect that there may be bugs in WI but I cannot claim that this is an established fact.

2. Documents. Neither WI nor NM  comes with any attempt at proper documents. At least, these should say:

How to install & configure. This lack is worse for WI which has a complicated UI with lots of options and therefore lots of scope for making mistakes. Presumably some of the unhappy non-users who populate this forum have made mistakes; whose fault is that?

When things fail, how to report bugs, what information to supply to give a useful bug report, and what action should you take to try to get connected.

3. Support. Is anybody working to remedy the defects?

---

### Post by imdano on 2008-07-03
> **mringer said:**
> Neither WICD nor NM can be regarded as satisfactory without a lot more work.

1. Bugs. The man page for NM says that networking should Just Work. This implies that anybody who fails to connect with NM has encountered a bug. I suspect that there may be bugs in WI but I cannot claim that this is an established fact.

2. Documents. Neither WI nor NM  comes with any attempt at proper documents. At least, these should say:

How to install & configure. This lack is worse for WI which has a complicated UI with lots of options and therefore lots of scope for making mistakes. Presumably some of the unhappy non-users who populate this forum have made mistakes; whose fault is that?

When things fail, how to report bugs, what information to supply to give a useful bug report, and what action should you take to try to get connected.

3. Support. Is anybody working to remedy the defects?The next release of wicd, 1.5.0, goes a long way in alleviating these issues.  Though I certainly can't say there are no bugs in 1.5.0, there is a very long list of fixes from the previous version, as well as many UI and backend improvements/new features.  It will ship with better documentation and pretty thorough man pages as well.

We do our best to offer support through our forum and irc channel, as well as through a bug track on launchpad.net.  Anyone interested in trying out the 1.5.0 release candidate can get it here: [www.wicd.net/latest](www.wicd.net/latest)

---

### Post by rahulthewall3000 on 2008-07-16
Out of curiosity, what is the default Wireless Manager in Xubuntu? There WICD would be perfect!

---

### Post by smartboyathome on 2008-07-16
The default is network manager. It works fine for me, same with Ubuntu. The only place I see WICD necessary is for WMs/DEs without a system tray (e17, I'm looking at you 8)).

---

### Post by user17 on 2008-07-17
Can Network Manager be made to refresh the list of available wireless networks? WICD does so on demand, and, once connected, updates your signal strength every few seconds.

---

### Post by rahulthewall3000 on 2008-07-17
> **smartboyathome said:**
> The default is network manager. It works fine for me, same with Ubuntu. The only place I see WICD necessary is for WMs/DEs without a system tray (e17, I'm looking at you 8)).

I am sorry, but I do not see the need for network-manager-gnome in Xubuntu. Xfce should not  install the libraries for the gnome panel by default and therefore the default in Xubuntu should be WICD.

---

### Post by rahulthewall3000 on 2008-07-17
> **user17 said:**
> Can Network Manager be made to refresh the list of available wireless networks? WICD does so on demand, and, once connected, updates your signal strength every few seconds.

No. There is no refresh option in Network Manager.

---

### Post by smartboyathome on 2008-07-17
> **rahulthewall3000 said:**
> I am sorry, but I do not see the need for network-manager-gnome in Xubuntu. Xfce should not  install the libraries for the gnome panel by default and therefore the default in Xubuntu should be WICD.

It *doesn't* install gnome-panel or very many gnome libraries at all in Xubuntu. Its just network-manager and a few libraries needed for it to run. I don't remember, but I am pretty sure it was just nm-applet and its dependancies installed, not network-manager-gnome.

> **rahulthewall3000 said:**
> No. There is no refresh option in Network Manager.

There is in Network Manager 0.7. I suggest you all try it using the guide in the community cafe. I find it great. :D
Also, network manager updates automatically for me, so I find no need for a refresh button. If it didn't I wouldn't use it.

---

### Post by benton on 2008-07-17
I've used both and no doubt wicd is the smarter, leaner, easier, sexier choice. I obviusly vote for wicd. 

Thanks wicd developers and community for such a nice piece of software!

---

### Post by rahulthewall3000 on 2008-07-18
> **smartboyathome said:**
> It *doesn't* install gnome-panel or very many gnome libraries at all in Xubuntu. Its just network-manager and a few libraries needed for it to run. I don't remember, but I am pretty sure it was just nm-applet and its dependancies installed, not network-manager-gnome.



There is in Network Manager 0.7. I suggest you all try it using the guide in the community cafe. I find it great. :D
Also, network manager updates automatically for me, so I find no need for a refresh button. If it didn't I wouldn't use it.

I stand corrected. However, if we are comparing with Network manager 0.7 then please give wicd 1.5 a go as well. I still think it is the better choice.

---

### Post by smartboyathome on 2008-07-18
> **rahulthewall3000 said:**
> I stand corrected. However, if we are comparing with Network manager 0.7 then please give wicd 1.5 a go as well. I still think it is the better choice.

I don't have my laptop now, and sent it back to school a few weeks ago, so sorry, I can't do that right now. :(

---

### Post by rahulthewall3000 on 2008-08-13
I do not have Ubuntu installed at the moment, however I have been using WICD-1.5.1 on my Gentoo box with the in tree iwlwifi drivers in 2.6.26. And I have no problems with WICD at the moment, it works like it is supposed to. I am auto connected to the LAN when I boot, when I connect to the wireless the wifi LED also works. And it connects to the wireless network without a hassle. 
And since WICD-1.5.1 has now gone stable while NM-0.7 is still under development I would not even put them on the same pedestal any more. As far as I am concerned, WICD is better than Network Manager. And I must repeat, I am only saying this from my personal experience. As documented in this thread, there have been instance where WICD has not worked at all while NM has flawlessly worked. However, that is not the case for me. 
I just want to say that if the fact that NM works for some people is strong enough for it to be the default in Ubuntu, the mere fact that it works for the 215 people in this thread should at least ensure that it is offered in the main repo and is documented as an alternative to NM on Ubuntu.

---

### Post by Steve1961 on 2008-09-13
Well just to add my 2 cents, I vote for nm.  Been using it now since it was first included in Ubuntu, and whilst it's far from perfect it generally works well on all my machines with wpa encryption, native and ndiswrapper drivers, hidden ssid, and connecting to a vpn.  Personally I've always found wicd to be less usable when I've tried  it.  I've often had problems with it freezing, there's no vpn support, and it won't auto-connect to hidden networks, which nm does without a problem.  So I suppose it's a case of whatever works for you, and that often depends on your hardware.  However, I would not want to see wicd replace nm as the default in ubuntu.

---

### Post by pietro_spina on 2008-09-20
I agree with the above poster. Auto connecting to a hidden SSID is important also VPN support. Why would I want to use something else to manage my vpn.

---

### Post by ItsManaged on 2008-10-02
Another thing I would like to see - be it NM or WICD is integration with third party connectors e.g. for Betavine 3G. Perhaps this can be done already, but I cannot see how.
Sooner or later we will start seeing laptops with 3G card slots, so the problem is growing.
On the subject - I use WICD because it behaved better than NM, however I notice recent NM has improved considerably, so I am definitely on the fence with this one.

---

### Post by swells5 on 2008-10-16
i like the automatic scripts in wicd which allow me to hook up to network servers automatically in xubuntu on a very old dell laptop from the mid 90s

---

### Post by enigma_0Z on 2008-10-16
Actually, I use the same functionality to start up synergy when I'm connecting to my work network, so I have one keyboard/mouse for several computers.

Also, it does seem that NM is being better, but not good enough. Scripting feature just kills it for me.

The main reason I don't use NM is because it doesn't allow me to create a custom encryption configuration. In particular, my school network uses 8021X authentication... This doesn't jive with NM who doesn't know that it exists. Unfortunately, this kills it with me for NM, so until NM supports more networks or custom networks, I'm not even considering it.

---

### Post by screaminj3sus on 2008-10-16
keep network manager because you shouldn't fix what isn't broken.

---

### Post by enigma_0Z on 2008-10-16
> **screaminj3sus said:**
> keep network manager because you shouldn't fix what isn't broken.

I really don't mean to sound like I'm trolling, but I can't help but laugh at this... The reason I am (along with approx. 40% of the voters here) are suggesting a switch or at least an option w/ WICD in the repos, is because for almost half of us, it *is* broken!

Case and point? As I stated above, NM has the VERY BAD lack of an "add your own type of wireless network" option. This creates a lack of functionality, and breaks NM for a lot of people, including myself. This means that NM simply does not work. It's not a "almost works" or a "kinda works." For the wireless network that I use on a daily basis, NM doesn't work. In my book that warrants a change.

Anyways, sorry 'bout the rant, but I still find your comment a bit humorous.

---

### Post by smartboyathome on 2008-10-16
> **enigma_0Z said:**
> I really don't mean to sound like I'm trolling, but I can't help but laugh at this... The reason I am (along with approx. 40% of the voters here) are suggesting a switch or at least an option w/ WICD in the repos, is because for almost half of us, it *is* broken!

Case and point? As I stated above, NM has the VERY BAD lack of an "add your own type of wireless network" option. This creates a lack of functionality, and breaks NM for a lot of people, including myself. This means that NM simply does not work. It's not a "almost works" or a "kinda works." For the wireless network that I use on a daily basis, NM doesn't work. In my book that warrants a change.

Anyways, sorry 'bout the rant, but I still find your comment a bit humorous.

I'm pretty sure that not many people will need to "add their own type of wireless network security", as not many people use oddball wireless security. And for some people WICD doesn't work, due to various reasons like VPN/dialup/etc which means going to WICD would put those users out in the cold.

---

### Post by gmclachl on 2008-10-18
I have been trawling through this thread with interest. I have only ever used NM, but have been thinking of using wicd. So I have installed it. 

First thoughts.

_Good Things_ 

[LIST]
[*]I like the fact you can easily add scripts to run when the if comes up. Don't tell me you can do this in NM as well. I know you can, but 1) it's not as easy. 2) It doesn't work.

[*]For some reason my connection speed is better. I wouldn't have thought it made a difference. As it is surely using the same drivers.

[*]wicd survives a reboot. I am using NM-0.7 and it randomly won't connect or will try to connect to another network.
[/LIST]
_Bad Things _

[LIST]
[*]I am getting random crashes when I open up the gui. Although it doesn't bring anything else down. 

[*]My ssid is hidden, for some reason it shows a hidden network and the one I specifed. These are the same router, so it duplicates it, which is a minor annoyance. Also for some reason it says the signal strength is better on the "hidden" network.
[/LIST]


Overall I think they are both much the same, they each have issues. if NM was working well for me I couldn't find a reason to move to wicd, and the reverse also applies.

---

### Post by rahulthewall3000 on 2008-11-02
> **smartboyathome said:**
> I'm pretty sure that not many people will need to "add their own type of wireless network security", as not many people use oddball wireless security. And for some people WICD doesn't work, due to various reasons like VPN/dialup/etc which means going to WICD would put those users out in the cold.

As I suggested long before in the thread - it was never my intention to leave the NM users "out in the cold". If you look at the polls WICD works better than NM for nearly 55% of the people. Your argument would apply that currently we are the ones that are being left out in the cold. 

What I do not understand is - how much time would it take to include WICD in the official repos and to have a suggestion like - "If you cannot connect to your wireless network , try using wicd. It can be simply installed through sudo apt-get install wicd." Moreover, this should be one of the deb that should be cached during installation - for if someone cannot connect to the internet how can he/she install another program.

Sadly, it has been more than a year since this thread has been active and yet there has been no change in the situation.

---

### Post by gnomeuser on 2008-11-02
> **rahulthewall3000 said:**
> As I suggested long before in the thread - it was never my intention to leave the NM users "out in the cold". If you look at the polls WICD works better than NM for nearly 55% of the people. Your argument would apply that currently we are the ones that are being left out in the cold. 

What I do not understand is - how much time would it take to include WICD in the official repos and to have a suggestion like - "If you cannot connect to your wireless network , try using wicd. It can be simply installed through sudo apt-get install wicd." Moreover, this should be one of the deb that should be cached during installation - for if someone cannot connect to the internet how can he/she install another program.

Sadly, it has been more than a year since this thread has been active and yet there has been no change in the situation.

You could also argue that WICD users would be additionally encouraged to vote here. Let's assume Network Manager works for most people, only a fraction of these people will vote in a poll like this, whereas people who experience issues with Network Manager are more encouraged to vote. This creates a large bias in WCID' favor thus the poll output should be correctly weighted.

The real problem is that we do no have solid numbers for the amount of people for whom it works, contra those for whom it does not. We also do not know for how many in the second pool the situation has improved since they voted making their vote likely invalid now. Additionally there must logically be a poll for whom neither solution works. We also don't know if the cause of the problem is a driver bug or an application bug (so if I update, get WCID and the kernel - I would be apt to credit WCID with fixing the problem when that might not be case, confirmation bias basically).

Proper statistical methods should be applied to this information before it's anywhere near useful.

---

### Post by yaknowwat on 2008-11-02
With intrepid the included network manager seems to handle things very well ans is quite simplified.  This thread is losing its value now.

---

### Post by AlphaMack on 2008-11-03
Losing its value?  Not exactly.  If it weren't for threads like these I wouldn't have known about Wicd.

Case in point:  I had just about flawless wifi networking under Gutsy and Hardy with my ThinkPad R61i.  NM occasionally acted a bit goofy but I tolerated it.  Did a clean install of Ibex only to find my wifi connection dropping every few minutes and NM throwing up its hands along with a prompt for the network password - already saved in my keyring.  I filed a bug only to find it marked as a dupe to a much larger bug report concerning Atheros cards utilizing ath5k/ath_pci and NM.  Out of desperation before wiping Ibex for Hardy, I installed Wicd from suggestions in the UF and elsewhere and what do you know?  No more dropped connections!  If it does drop, Wicd is quick to get it back up without the annoyance of that NM icon spinning around and around before giving up.

Sorry, but count me as another happy camper in the Wicd camp.  I only wish that I knew about it earlier so that I could make the switch.

---

### Post by Sorivenul on 2008-11-03
> **gnomeuser said:**
> This creates a large bias in WCID' favor thus the poll output should be correctly weighted.

Proper statistical methods should be applied to this information before it's anywhere near useful.

You make a great point, but as far as Forum polls go, I personally don't believe this is possible.  Your analysis of the WICD bias is spot on, and this seems to imply that correctly measuring poll results is not possible in this setting.

As far as proper statistical methods go, I wish this were possible, as it would make the the "correctly weighted" poll output a possibility.

---

### Post by gnomeuser on 2008-11-04
> **Sorivenul said:**
> You make a great point, but as far as Forum polls go, I personally don't believe this is possible.  Your analysis of the WICD bias is spot on, and this seems to imply that correctly measuring poll results is not possible in this setting.

As far as proper statistical methods go, I wish this were possible, as it would make the the "correctly weighted" poll output a possibility.

What I really wanted to show was that we should not let the technical decisions of Ubuntu rest in the hands of a few vocal users. This is also why Brainstorm for the most part is a horrible idea. The data gathered is invalid as best, but at worst it might lead us to make the wrong long term decisions. Thus it is directly harmful.

I what we can learn from the existance of such a poll and from things like brainstorm is that e.g. NetworkManager does not work for every one, big surprise. Now the productive approach would be talking to these users about their workflow and the problems they encounter then encouraging them to file bugs (or doing so on their behalf then subscribing them or the thread to the bug report), thus showing concern for their grievances and problems. It does not seem that bug reporting is the first stop for most people, instead they elect to advocate "solutions" such as replacing software (never mind that they forget that an equal proposition would then have the same problems with that and advocate going back). This does not however fix anything, and fixing stuff, making it better should after all be the objective.

---

### Post by Sorivenul on 2008-11-04
> **gnomeuser said:**
> This does not however fix anything, and fixing stuff, making it better should after all be the objective.

Well said.

---

### Post by rahulthewall3000 on 2008-12-16
> **gnomeuser said:**
> What I really wanted to show was that we should not let the technical decisions of Ubuntu rest in the hands of a few vocal users. This is also why Brainstorm for the most part is a horrible idea. The data gathered is invalid as best, but at worst it might lead us to make the wrong long term decisions. Thus it is directly harmful.

I what we can learn from the existance of such a poll and from things like brainstorm is that e.g. NetworkManager does not work for every one, big surprise. Now the productive approach would be talking to these users about their workflow and the problems they encounter then encouraging them to file bugs (or doing so on their behalf then subscribing them or the thread to the bug report), thus showing concern for their grievances and problems. It does not seem that bug reporting is the first stop for most people, instead they elect to advocate "solutions" such as replacing software (never mind that they forget that an equal proposition would then have the same problems with that and advocate going back). This does not however fix anything, and fixing stuff, making it better should after all be the objective.

In my previous post that I categorically stated that for more than half the people here, WICD works better in comparison to NM, and while some of the votes may have become invalid during the course of the year, it does not alter the fact that WICD is a viable option for quite a few people out there. While I agreed that replacing NM might not be the best option (as WICD lacks dial-up and VPN support) - it would be useful to atleast include WICD on the official repos or have a pointer somewhere which suggests WICD as an alternative to NM - what the problem with this, I do not know.

As for technical decisions and vocal users - the community is trying to make constructive suggestions here. If forum threads here cannot initiate even a small change, then might it not be better to close the section rather than give users the hope that they can make a difference. The technical decisions taken need to derive from user feedback, in my opinion.

Just my two cents
Rahul

---

### Post by imdano on 2008-12-16
> **rahulthewall3000 said:**
> it would be useful to atleast include WICD on the official repos or have a pointer somewhere which suggests WICD as an alternative to NM - what the problem with this, I do not know.1.5.2 is in the Jaunty repos.

---

### Post by rahulthewall3000 on 2008-12-18
> **imdano said:**
> 1.5.2 is in the Jaunty repos.
My bad then.

---

### Post by Izek on 2008-12-18
I voted for wicd, and stand by it. Though, getting the tray to autostart is a small annoyance.

---

### Post by oygle on 2009-01-06
I can't use [ppp0 AND eth0 at the same time]("http://ubuntuforums.org/showthread.php?t=1022569") , in fact I had to disable the LAN card, just to get NM 0.7 to work in Intrepid.

Still, no eth0, and as I need to share the ppp0 connection (broadband wireless) with other computers, and also share files across the lan, and there definitely seems no fix/workaround to the problems others are having with NM, I 'll have to try WICD , and see what it is like.

WICD is not in the packages for Ubuntu, and I saw a post about an install msg stating it was not 'trusted'. Is wicd, err, 'safe' ?

There is a section at [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php) , for installing it in Ubuntu, looks like it is okay.

Oygle

---

### Post by oygle on 2009-01-06
> **yaknowwat said:**
> With intrepid the included network manager seems to handle things very well ans is quite simplified.  This thread is losing its value now.

Have you looked at the networking forum, and seen how many people are having trouble with NM 0.7 with Intrepid ?

---

### Post by Coombabah on 2009-01-06
> **yaknowwat said:**
> With intrepid the included network manager seems to handle things very well ans is quite simplified.  This thread is losing its value now.
Or this thread may be increasing it's value now.

If NM worked well there wouldn't be so much interest in threads like this one.

Things broken in NM 0.7 that worked in previous version of NM are making people look for alternatives like WICD.

NM 0.7 is too simplified. 

Eg. If you need to use TKIP to connect to your University network that option has gone :(

NM isn't perfect (yet) neither is WICD.

Having the option to setup NM or WICD from the install CD/DVD would seem friendlier than trying to download stuff when your network connection is broken. (Especially if you have to boot into Windows to do it)

Edit: just found a workaround using gconf-editor to get tkip working in NM 0.7 by removing ccmp entries leaving tkip :)
[http://ubuntuforums.org/showthread.php?t=1010650](http://ubuntuforums.org/showthread.php?t=1010650)

---

### Post by samjam on 2009-01-07
I have to have unmanaged wireless because my home directories are NFS based.

This means I CANNOT use network-manager for VPN.

I would guess this applies to ANYONE with NFS home directories.

VPN setup should work on any interface, not just managed interfaces.

---

### Post by danf_1979 on 2009-01-12
I have Dell Inspiron 9400, using jaunty. I began to notice that my laptop was very slow, so I began monitoring things. There was this "dellWirelessCtl" process which eated most of my CPU every few seconds. After googling it, I found out that dellWirelessCtl is was used by hall to poll the bios about the kill-switch.

Some guy contacted dell support and asked about this problem. Here's the response:

> I asked Micheal E. Brown from Dell about the issue and here's what he
>
> had to say:
> > This, unfortunately, is normal. The dellWirelessCtl program uses an SMI
> > interrupt to ask BIOS about the status, which causes BIOS to take over
> > from the OS to do its thing before it returns. You can probably set HAL
> > to run it less often.
> > --
> > Michael

Here's the complete story: [http://lists.freedesktop.org/archives/hal/2008-September/012241.html](http://lists.freedesktop.org/archives/hal/2008-September/012241.html)

After this, I remembered a friend of mine talking about wicd and how it fixed all his problems (other problems!), and thought I had nothing to lose. I installed wicd, and now I'm happy. My laptop does not use dellWirelessCtl anymore. 

This should be default, End.Of.Story.

---

### Post by HunterThomson on 2009-01-12
i just switched to see what it was like. I too have had many problems with network-manager. I have a DD-WRT with Hidden AP encrypted with WPA2-PSK with 20+ character pass-key. Network-manager takes a long time to connect. I have never liked the nm UI ether. 

I must say wicd UI is much better and fast as hell. However, It dose use 1.3% of my CPU and 2.3mb of ram on my box. (see specs below). A ps aux shows 6 python scripts running. I don't like that at all.... But it is way faster.

Tanks for the turn on :) 

Wicd should be the default

---

### Post by smartboyathome on 2009-01-12
> **HunterThomson said:**
> i just switched to see what it was like. I too have had many problems with network-manager. I have a DD-WRT with Hidden AP encrypted with WPA2-PSK with 20+ character pass-key. Network-manager takes a long time to connect. I have never liked the nm UI ether. 

I must say wicd UI is much better and fast as hell. However, It dose use 1.3% of my CPU and 2.3mb of ram on my box. (see specs below). A ps aux shows 6 python scripts running. I don't like that at all.... But it is way faster.

Tanks for the turn on :) 

Wicd should be the default

I have the same exact chipset, and WICD is one of the only things on Arch Linux which lets me connect to my WPA2 network on Arch Linux. Unfortunately, neither netcfg nor iwconfig work.

---

### Post by imdano on 2009-01-12
> **HunterThomson said:**
> A ps aux shows 6 python scripts running. I don't like that at all.... But it is way faster.What are the six scripts?  Wicd should only have 3 processes associated with it:
1) wicd-daemon.py (or just wicd)
2) monitor.py (or wicd-monitor)
3) wicd-client.py (or just wicd-client)

---

### Post by qamelian on 2009-01-12
> **danf_1979 said:**
> 
This should be default, End.Of.Story.
Except Wicd still does not work on my laptop, but network manager does. As I can see, Wicd is no more reliable than NM. It just works for a different group of people.

---

### Post by oygle on 2009-01-13
Is [UMTSmon]("http://umtsmon.sourceforge.net/") a suitable replacement for Network manager or WICD ?

I have been looking for a networking tool to replace NM, and need the stats and signal strength, and it seems this tool does it. It also 'controls' your connection, so I assume it can do what NM and WICD do, in terms of a connection.

Just why it has been excluded from the Ubuntu packages I don't know ??

Oygle

---

### Post by imdano on 2009-01-13
> UMTSmon is a tool to control and monitor a wireless mobile network card (GPRS, EDGE, WCDMA, UMTS, HSDPA) in a laptop running the Linux operating system.It looks like UMTSmon is for mobile modems only from its website.  If that's what you have, seems like it would be a good fit.  I would imagine its not in the repos for the same reason wicd isn't -- no one has gone through the steps to get it packaged.

---

### Post by Vadi on 2009-01-13
I withdraw my vote for WICD.

NM works beautifully now, has a better design and interface, and - quite important - has dbus integration. Meaning that programs can ask it, "are we online?" and it tells you. Great for improving the 'smartness' of programs. 

Pidgin, for example, will wait until you're online before it starts connecting. I also added this feature to several programs I'm making. It's great. Wicd doesn't have this - so if the user has it, well, the program is just as dumb as any other one and just keeps trying to connect / gives an error.

---

### Post by oygle on 2009-01-13
> **Vadi said:**
> 
NM works beautifully now,

With 438 [open bugs]("https://bugs.launchpad.net/ubuntu/+source/network-manager/") ?

---

### Post by imdano on 2009-01-13
> **Vadi said:**
> Pidgin, for example, will wait until you're online before it starts connecting. I also added this feature to several programs I'm making. It's great. Wicd doesn't have this - so if the user has it, well, the program is just as dumb as any other one and just keeps trying to connect / gives an error.Wicd actually does have this.  It uses dbus extensively for communication between the daemon, monitor, and UI, and it'd be very easy for an application to get the connection status from the dbus interface.  I don't know of any that make use of that functionality, though.

edit: here's some sample code for getting it on demand.  You can also add a callback for the "StatusChanged" signal to stay in sync.
```
>>> import dbus
>>> proxy_obj = dbus.SystemBus().get_object("org.wicd.daemon", "/org/wicd/daemon")
>>> daemon = dbus.Interface(proxy_obj, "org.wicd.daemon")
>>> daemon.GetConnectionStatus()
dbus.Struct((dbus.UInt32(2L), dbus.Array([dbus.String(u'192.168.1.104'), dbus.String(u'ourhouse'), dbus.String(u'83'), dbus.String(u'0')], signature=dbus.Signature('s'))), signature=None)

```

---

### Post by smartboyathome on 2009-01-14
> **oygle said:**
> With 438 [open bugs]("https://bugs.launchpad.net/ubuntu/+source/network-manager/") ?

That doesn't mean anything. Some of those bugs could have been resolved and no one reported it solved.

---

### Post by oygle on 2009-01-14
> **smartboyathome said:**
> _Some_ of those bugs _could have_ been resolved and no one reported it solved.

I agree, but neither you or I know, do we.  ;)

They also could all be legitimate bugs that still exist. But take a look around the wireless and networking forum, and see how many NM problems/bugs there are currently.

---

### Post by Vadi on 2009-01-14
> **imdano said:**
> Wicd actually does have this.  It uses dbus extensively for communication between the daemon, monitor, and UI, and it'd be very easy for an application to get the connection status from the dbus interface.  I don't know of any that make use of that functionality, though.

edit: here's some sample code for getting it on demand.  You can also add a callback for the "StatusChanged" signal to stay in sync.
```
>>> import dbus
>>> proxy_obj = dbus.SystemBus().get_object("org.wicd.daemon", "/org/wicd/daemon")
>>> daemon = dbus.Interface(proxy_obj, "org.wicd.daemon")
>>> daemon.GetConnectionStatus()
dbus.Struct((dbus.UInt32(2L), dbus.Array([dbus.String(u'192.168.1.104'), dbus.String(u'ourhouse'), dbus.String(u'83'), dbus.String(u'0')], signature=dbus.Signature('s'))), signature=None)

```

Ah, thanks for the info - I did not find it on the website.

Now, with nm being installed on ~93% ubuntu machines, and wicd on 0.01%... well, with linux itself having 1%, I suppose it'll be worth it to add support anyway. Thanks!

---

### Post by kivil on 2009-03-09
Hello,

I'd like to share my first hand experience.

I've been using Linux on my desktop since 1997. I've been using Debian since 2002 and Ubuntu since 2008.

Recently I bought a Medion akoya (MSI Wind rebrand) with rt2860 wireless driver.

I installed Ubuntu 8.10 with updated 2.6.27.11 kernel.

In order to avoid ndiswrapper I installed the driver following the instructions in the following page;

[http://bubuitalia.wordpress.com/2009/03/02/set-up-wifi-on-a-msi-wind-notebook/](http://bubuitalia.wordpress.com/2009/03/02/set-up-wifi-on-a-msi-wind-notebook/)

After the installation the module started fine but I was unable to connect to my hidden essid network via Network Manager.

Though I did not give much probability I changed my AP to publish my ESSID. And after that I was able to connect..

I do not want to disrespect any efford given, but this is nth time that I had a problem with Network Applet and I wanted to give a chance to WICD.

To my surprise WICD connected to the unannounced AP.

Upon this I'd like to say a few words concerning Network Manager.

In my humble oppinion NM is a very good efford in a wrong direction. Starting from the first time I've seen it, I felt that something was wrong.

This applet simply does not let enough freedom to Linux users. Which may in fact be perfectly fine with Windows or MAC users, but simply irritates the FLOSS community. 

First it does not let you know anything about current situation. If you are able to connect to the Ap and waiting for IP or what. Wicd does this.

If you want to connect to some networks manually, NM will simply override it. (Don't let me start talking about Avahi by the way :))

Then there is this circling animation, which is invulnarable to any combo breaker, in any case anything goes wrong. This combined with NM putting you in dark, it sometimes becomes really frustrating.

Wicd on the other hand is very user friendly. I think there is only one thing that we GNU/Linux users can not leave behind, that is the verbosity of the error messages/current situation. In my opinion this is simple politeness, which Windows or MacOs usually lacks.

There is also the ability of triggering scripts or choosing which dhcp client to use.

I don't want to get things bigger than life, but I think Wicd is the right effort in the right direction.

Thanks for supplying a good alternative.

This is what this whole open source business is about.

---

### Post by Fenris_rising on 2009-03-09
/Hi all

I have just reverted back from wicd to NM. Wicd seemed, to me, to be better with my wireless connection. So why did I change back? 

Because my main PC is wireless to the router and I also have a NIC with a static IP that connects to my Xbox one. Wicd could handle one or the other but not both at the same time.

NM can run both simultaneously so that gets my vote.

I do think Wicd is a more polished app and it is also more informative of what it's doing.

I now wait to be shot down in flames and told wicd can do both at the same time :D

regards

Fenris

---

### Post by lachild on 2009-03-09
I Vote for WICD... IF the UI is prettied up.  The version I am using the UI looks a little dated.  

However, I do like the fact that with WICD I was able to set a static IP on boot allowing me to setup a headless box painlessly.  You can not do this with Network Manager.  

On the other hand, Network manager does have less options which can mean it's less confusing to new users and the UI looks a little cleaner, but WICD would probibly get a face lift if something like Ubuntu decided to make it the default manager.


LaChild

---

### Post by imdano on 2009-03-10
> **Fenris_rising said:**
> I now wait to be shot down in flames and told wicd can do both at the same time.No, wicd won't handle two at once yet.  You'd have to configure one through wicd and then one through the command line.  We're working on supporting multiple connection at once for a future version, though.

---

### Post by digitalramble on 2009-04-10
What gets to me is that as far as I can tell it's Network Manager writing out cruddy config files that makes it impossible to use my broadcom wireless.  (Yeah, I know, broadcom; I was under the impression I was getting a different brand...anyway).  In 9.04, there is a proprietary driver available for my wireless (not an ndiswrapper thing) which I chose to install...and my wireless worked perfectly right up until NM decided to write out to a config file.   There's a post about this elsewhere but the basic end result is that NM utterly disables my wireless.

Gonna try wcid, thought this topic was a how to in case there were any oddities about installation...

---

### Post by yonas on 2009-04-12
WCID ALL THE WAY!!!!!!!!!!!!!!!!!!!!!!!!!! :KS

I'm using wcid because NM wouldn't reconnect to my router until I rebooted my laptop.....unacceptable :mad:

---

### Post by digitalramble on 2009-04-12
> **yonas said:**
> WCID ALL THE WAY!!!!!!!!!!!!!!!!!!!!!!!!!! :KS

I'm using wcid because NM wouldn't reconnect to my router until I rebooted my laptop.....unacceptable :mad:

I couldn't get wicd to work...it would do everything right up till it said "Getting IP address"... and it just sat there.  Reinstalled NM and found that if I didn't let it autoconnect (one of the preference options somewhere), it didn't give me any further trouble.  Really wierd.  NM just seems so... marginal given it's rather central importance in the scheme of things... hello?

---

### Post by Pedric on 2009-04-13
On the NetworkManager side, there is the new Bluetooth Manager called [blueman]("http://blueman-project.org/") that integrates Bluetooth Dialup and PAN devices into NetworkManager 0.7. Combined with VPN, multiple active devices and USB 3g modems, NM 0.7 features many things now that wicd [has only just thought about]("http://wicd.sourceforge.net/moinmoin/3GUsbModem"). So for now, while the wlan aspect of wicd may work better for some, NM 0.7 does much more than that. As mobile broadband usage rises, this is not something that Ubuntu can or will ignore, so there is no point in making wicd the default network manager.

---

### Post by lcohen999 on 2009-04-13
until WICD supports VPNs, it can be no sale

---

