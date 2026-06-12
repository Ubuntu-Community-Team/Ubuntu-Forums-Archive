---
title: "call for unity7 testing, maintainers"
date: 2017-06-15
forum: Ubuntu Development Version
---

### Post by ventrical on 2017-06-15
Hi All,

  To keep unity7 viable we have to test it alongside GNOME and report any breakage.

  Also it has been brought to my attention that unity7 may break throughout  the current development version, specifically, as mentioned here,

> 
Hi Dale, Mark,
 
 Just to add a little more background here:
 
 
 
 Unity 7 in 16.04 LTS will naturally be supported until 2021 by the  Desktop team with security updates and critical bug fixes.  These would  very likely be forward-portable to Unity 7 in 17.04, 17.10 etc.
 
 
 The problems for U7 arise in 17.10 and beyond because of the way we  have patched the Gtk libraries & apps to get them to integrate well  with Unity 7.  For example, we patch out header bars and client side  decorations & patch in support for the global menus.  This are fundamentally incompatible with GNOME Shell, and so we need to  make a decision about whether to add more patches to make these apps  work well in both Unity 7 and GNOME Shell or drop the patches and focus  on the GNOME Shell experience.  The current preference is drop the patches.
 
 
 There are some other incompatibilities in the desktop session  between GNOME Settings Daemon & Unity Settings Daemon, or GNOME  Online Accounts & Ubuntu Online Accounts.  We need to use the GNOME  version in the GNOME session, so these would be prime candidates for a community team to maintain in the future for the U7 session.
 
 
 Where does this leave Unity 7 in 17.10 then?  At the moment we are  testing Unity 7 alongside GNOME Shell to spot when something we land  causes Unity 7 to break.  While we can probably work around some of  these issues, the overall experience will be hampered by the incompatibility between our U7 patches & services and GNOME  Shell, and this will, unfortunately, degrade the U7 experience on  17.10.  We're still looking at what changes could be made to keep U7  working in the archive so I can't make any promises of functionality yet.  I'd like to make that call before Beta 1 so people  know what to expect.
 
 
 Any community teams who'd be interested in helping out with that  would be very welcome and I'd be very happy to help get them set up with  the access they need and support from the Desktop Team.
 
 
 Cheers, Will

So anyone who would like to be part of this testing or has experience in the areas, as which Will is pointing out, then please join in the discussion here. If we contribute to the community effort it could help ensure unity7's viability in the 18.04 release cycle.

Regards..
Dale

---

### Post by kc1di on 2017-06-15
Will unity 7 play with wayland which seems to be what will be the coming default x server?

---

### Post by ventrical on 2017-06-15
> **kc1di said:**
> Will unity 7 play with wayland which seems to be what will be the coming default x server?

I did a lot of testing of wayland in the early days. Then mir came along and I tested that too. Well .. the rest of the story is just re-hashing old ground. You asked a good question and I think you hit the nail on the head. But, what if we brainstorm, I mean , perhaps we can build a simple roll-back compositor to handle unity7 when it is logged into without affecting system resources too much. Or can unity7 be made into a snap? Or perhaps we can modify unity7 to become a 'unity7classic' rollback. Could we possibly jockey compositors? For example stay x11 while wayland is running and stay wayland while x11 is running concurrently? So it would be like two impermeable sandboxes not affecting each other - a filter developed capable of doing that. Or we can have dynamic-depends that have a global code but are filterable and  intuitive. or perhaps unity-greeter or the entire login process can be modified to insert unity7 into a container running on a rolled back x11 with legacy compatible depends? There is nothing wrong with using older reliable code in newer conceptuals if you can simply teach the new core to read the older code. It doesn't always have to be bare metal forensics to make a doable and workable multi-purpose compositor, does it?

Regards..

---

### Post by amano on 2017-06-15
I like the idea with the Unity 7 Snap. Probably the only viable way to get the supported 16.4 Unity to 18.4.

---

### Post by Yahoé on 2017-06-20
As of this morning 2017-06-20 after dist-upgrading my system which, removed ubuntu-session, upon restart, I cannot access the Gnome session. Since I had to have a desktop environment, I reinstalled ubuntu-session which reinstalled some unitygtk2 packages, I think. Anyhow, I now can load Unity, but the display is acting up on me.

---

### Post by Frogs Hair on 2017-06-20
> **Yahoé said:**
> As of this morning 2017-06-20 after dist-upgrading my system which, removed ubuntu-session, upon restart, I cannot access the Gnome session. Since I had to have a desktop environment, I reinstalled ubuntu-session which reinstalled some unitygtk2 packages, I think. Anyhow, I now can load Unity, but the display is acting up on me.

I have a fully functional unity session after removal of this package though it is no longer listed as default in the greeter.

---

### Post by ventrical on 2017-06-20
> **Frogs Hair said:**
> I have a fully functional unity session after removal of this package though it is no longer listed as default in the greeter.

If you installed unity7 alongside a 17.10 artful-desktop install then unity would never have been default. Is your install an upgrade from 17.04?

regards..

---

### Post by ventrical on 2017-06-20
> **Yahoé said:**
> As of this morning 2017-06-20 after dist-upgrading my system which, removed ubuntu-session, upon restart, I cannot access the Gnome session. Since I had to have a desktop environment, I reinstalled ubuntu-session which reinstalled some unitygtk2 packages, I think. Anyhow, I now can load Unity, but the display is acting up on me.

[s]Yep .. my ubuntu is gone!![/s]

[s]Nope .. you have to hit the back arrow in the greeter and there is unity[/s]

Unity is gone. It rolls right to gnome-shell.

Regards..

---

### Post by ventrical on 2017-06-20
OK.. so I reinstalled ubuntu-session

```

ventrical@ventrical-MS-7850:~$ sudo apt-get install ubuntu-session
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  evolution-data-server-online-accounts libcamel-1.2-59 libdbusmenu-qt5
  libebook-1.2-16 libgsettings-qt1 libqt5sql5 libqt5sql5-sqlite libsigsegv2
  libunity-gtk2-parser0 libunity-gtk3-parser0
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  hud unity-gtk-module-common unity-gtk2-module unity-gtk3-module
The following NEW packages will be installed:
  ubuntu-session
0 upgraded, 1 newly installed, 4 to remove and 0 not upgraded.
Need to get 0 B/2,820 B of archives.
After this operation, 1,136 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 147709 files and directories currently installed.)
Removing hud (14.10+17.10.20170619-0ubuntu1) ...
Removing unity-gtk2-module:amd64 (0.0.0+17.04.20170918-0ubuntu1) ...
Removing unity-gtk3-module:amd64 (0.0.0+17.04.20170918-0ubuntu1) ...
Removing unity-gtk-module-common (0.0.0+17.04.20170918-0ubuntu1) ...
Selecting previously unselected package ubuntu-session.
(Reading database ... 147679 files and directories currently installed.)
Preparing to unpack .../ubuntu-session_3.24.1-0ubuntu2_all.deb ...
Unpacking ubuntu-session (3.24.1-0ubuntu2) ...
Processing triggers for libglib2.0-0:amd64 (2.53.1-1) ...
Setting up ubuntu-session (3.24.1-0ubuntu2) ...
ventrical@ventrical-MS-7850:~$ 

```

---

### Post by ventrical on 2017-06-20
Re-installed ubuntu-session, reboot and works just fine. I don't get what al the fuss was. Why it had to pull ubuntu-session?

---

### Post by Yahoé on 2017-06-20
Yes it's an 17.04 upgrade.

---

### Post by Yahoé on 2017-06-20
I guess they removed ubuntu-session by mistake, lets hope, since it broke the UI for many users most likely

---

### Post by ventrical on 2017-06-20
> **Yahoé said:**
> I guess they removed ubuntu-session by mistake, lets hope, since it broke the UI for many users most likely

Yes .. i have seen this before in previous cycles. Mid cycle correction. But maybe there is more to it.

Regards..

---

### Post by Frogs Hair on 2017-06-20
I can't locate ubuntu-session in synaptic after some more upgrades. I am in unity at the moment , I'll see after reboot. 

```
apt-cache search ubuntu-session
blubuntu-session-splashes - Blubuntu look - Session splashes



```

---

### Post by Frogs Hair on 2017-06-20
Though ubuntu-session badge is missing in the greeter it is still listed and working. Shrug

---

### Post by ventrical on 2017-06-20
> **Frogs Hair said:**
> Though ubuntu-session badge is missing in the greeter it is still listed and working. Shrug

I re-installed ubuntu-session like yahoe and I have the ubuntu-badge. You have to hit the back-arrow in the greeter. It will not come up unless you install ubuntu-session.

It appears that unity-greeter has a bug..

regards..

[https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/1699357](https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/1699357)

---

### Post by Frogs Hair on 2017-06-20
```
 sudo apt install ubuntu-session
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ubuntu-session is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  unity-session

```
```
sudo apt install unity-session
Reading package lists... Done
Building dependency tree       
Reading state information... Done
unity-session is already the newest version (3.24.1-0ubuntu3).
unity-session set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

I have proposed enabled.

---

### Post by ventrical on 2017-06-20
> **Frogs Hair said:**
> ```
 sudo apt install ubuntu-session
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ubuntu-session is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  unity-session

```
```
sudo apt install unity-session
Reading package lists... Done
Building dependency tree       
Reading state information... Done
unity-session is already the newest version (3.24.1-0ubuntu3).
unity-session set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

I have proposed enabled.

Wow. I see it now. 
Ahh yes.. thanks for sharing this.

Regards..

---

### Post by dino99 on 2017-06-21
gnome-session (3.24.1-0ubuntu3) artful; urgency=medium

  * Rename ubuntu-session into unity-session

devs have started removing unity; that's it.

---

### Post by jbicha on 2017-06-21
The ubuntu-session package will install a GNOME session in Ubuntu 17.10. Assuming the Ubuntu session is customized for Ubuntu, that's leaves a gnome-session package that could provide a more upstream version of GNOME if someone wants to maintain that.

Therefore, a unity-session package had to be introduced for people to be able to run Unity.

These -session packages provide the files needed for the login screen to show you a desktop option and let you log in to it.

---

### Post by Yahoé on 2017-06-21
> **jbicha said:**
> The ubuntu-session package will install a GNOME session in Ubuntu 17.10. Assuming the Ubuntu session is customized for Ubuntu, that's leaves a gnome-session package that could provide a more upstream version of GNOME if someone wants to maintain that.

Therefore, a unity-session package had to be introduced for people to be able to run Unity.

These -session packages provide the files needed for the login screen to show you a desktop option and let you log in to it.

Ok Jeremy, thanks for the explanation. This is all very nice, but as of 08:30 (eastern time), with unity-session installed, I still can't log into Unity from lightdm after yesterday's changes.

---

### Post by ventrical on 2017-06-21
@yahoe and  all

From Will Cooke;

> 
Hi Dale, 
 
 We're in the middle of changing the Ubuntu session to use GNOME  instead of Unity.  There will be a period of weirdness while this is  competed.
 
 
 You can follow the high-level progress here: [https://trello.com/c/TLheyL5G](https://trello.com/c/TLheyL5G)
[TABLE="width: 90%"]
[TR]
[TD="colspan: 2"][COLOR=#0078D7][FONT=&amp][Trello]("https://trello.com/c/TLheyL5G")[/FONT][/COLOR]
[COLOR=#666666][FONT=&amp]trello.com[/FONT][/COLOR]
[COLOR=#666666][FONT=&amp]Organize  anything, together. Trello is a collaboration tool that organizes your  projects into boards. In one glance, know what's being worked on, who's  working on what, and where something is in a process.[/FONT][/COLOR][/TD]
[/TR]
[/TABLE]

 
 
 I think that should have all the details, but let me know if you have more questions.
 
 
 Cheers, Will




Regards..

---

### Post by ventrical on 2017-06-21
> **Yahoé said:**
> Ok Jeremy, thanks for the explanation. This is all very nice, but as of 08:30 (eastern time), with unity-session installed, I still can't log into Unity from lightdm after yesterday's changes.

[s]Are you using proposed?[/s]

 I have had an awesomely smooth transition here to unity-session.

---

### Post by ventrical on 2017-06-21
> **dino99 said:**
> gnome-session (3.24.1-0ubuntu3) artful; urgency=medium

  * Rename ubuntu-session into unity-session

devs have started removing unity; that's it.

Actually it appears that they are doing a lot of testing/discussion on unity7 as they are converting ubuntu-session over to unity-session. This is an awesome development I think.  If all goes well there may be a better than good chance that unity7 will be in the universe during 18.04. testing.

 I am still hoping we can get a small group of persons from our team to take up maintaining/testing some of the unity depends. I appreciate all the work you do in testing this in conversion, however I  wonder if there are still any out there who would like to try a commit to this (other than Jeremy) because Jeremy has his hands full with gnome-shell dev. 

Regards..

---

### Post by ventrical on 2017-06-21
Re-booted and now I have 'unity-default' in the greeter.

Regards..

---

### Post by Yahoé on 2017-06-21
At 11:45 (eastern time), after the latest updates to gnome-session and to unity-session, Unity is still a no go. The greeter is there, but after entering the password, wait, wait, wait...

---

### Post by ventrical on 2017-06-21
> **Yahoé said:**
> At 11:45 (eastern time), after the latest updates to gnome-session and to unity-session, Unity is still a no go. The greeter is there, but after entering the password, wait, wait, wait...

Could you perhaps remove unity-session and reinstall ?

---

### Post by Yahoé on 2017-06-21
> **ventrical said:**
> Could you perhaps remove unity-session and reinstall ?

After dist-upgrading the system at 02:45 (eastern), gnone-session and unity-session where yet again updated, but I still couldn't log into Unity. I then purged unity*, reinstalled ubuntu-session, and was finally able to log into Unity.

---

### Post by amano on 2017-06-22
> **ventrical said:**
>  If all goes well there may be a better than good chance that unity7 will be in the universe during 18.04. testing.

The question is: In what state? Chances are that it will get broken more and more over time without active maintenance. Cohesion and stability will decrease with every Unity patch dropped from the GNOME packages. 

The only way I see a working Unity from 18.04 onwards is by including it as a 16.4. based snap.

---

### Post by ventrical on 2017-06-22
> **amano said:**
> The question is: In what state? Chances are that it will get broken more and more over time without active maintenance. Cohesion and stability will decrease with every Unity patch dropped from the GNOME packages. 

The only way I see a working Unity from 18.04 onwards is by including it as a 16.4. based snap.

Well.. I am still trying to get volunteers to take up the maintainers position.

Maybe you could help before I ask Will.

1. How many persons does it usually take to maintain patches to, say , unity7.
2. What kind of commitment is involved?
3. Can you give me a short list of 'things we need to know'.
4. Can you volunteer as a maintainer?

Regards..

---

### Post by #&amp;thj^% on 2017-06-23
> **ventrical said:**
> Well.. I am still trying to get volunteers to take up the maintainers position.

Maybe you could help before I ask Will.

1. How many persons does it usually take to maintain patches to, say , unity7.
2. What kind of commitment is involved?
3. Can you give me a short list of 'things we need to know'.
4. Can you volunteer as a maintainer?

Regards..
This I "hope" this dose not get overlooked or a shrug shoulders and move on approach.
 But the first question asked here is the biggest hurtle I fear. 
> **ventrical said:**
> 1. How many persons does it usually take to maintain patches to, say , unity7.

 I knew Mark employed over 300 people at one time, And I don't know ATM how many are currently still are employed.
 But how many of them that were strictly/assigned or working on Unity is unknown to me. I think you get my drift here as far a people power involved 
 Now the second question:
 > **ventrical said:**
> 
2. What kind of commitment is involved?

Not sure how to answer, as this seems to be a loaded question...but my first thought here would be forever.
The third question is unknown to me at least.
> **ventrical said:**
> 
3. Can you give me a short list of 'things we need to know'.

This would have to come from those involved IE Canonical or even the Devs.
The fourth question:
> **ventrical said:**
> 
4. Can you volunteer as a maintainer?

I myself have some personal health issues going on, not to mention lacking skills.
But would be happy to help where I can.
Thanks Vent for a great idea that could be done with all of the above in place.
Deepest Respects

---

### Post by ventrical on 2017-06-23
> **1fallen said:**
> This I "hope" this dose not get overlooked or a shrug shoulders and move on approach.
 But the first question asked here is the biggest hurtle I fear. 

I myself have some personal health issues going on, not to mention lacking skills.
But would be happy to help where I can.
Thanks Vent for a great idea that could be done with all of the above in place.
Deepest Respects

@1fallen,

Thanks for your reply. Will Cooke has offered up a great bunch of help and direction including even asking some desktop team members to help out and get me started.  My formal training is using a C type programming language called Turing which I used on a VAX/UNIX mainframe so  the language is very familiar to me.  Working with Linus Torvalds on his first boot disk back in 1995 also gives me some background , but, the language has certainly changed over the past 1/4 century so I am doing a crash-brush-up with the Eclipse program software. :) lol 

 Currently they are doing a session migration and Will has cautioned me that this will not take place overnight so that will give me time to brush up and etc..

  I guess my goal is that I can commit time and energy to the 18.04 testing cycle to unity7 which will start sometime after final release of 17.10 and I know that all hands on deck will be focusing on getting GNOME ready to be the flagship distro of ubuntu once again  .. so yes . it may be an uphill battle but I guess that is the joy of it all :)

Most of the work is done it launchpad and I know you are well texted in that area so I am certain you can offer some pointers when I get the list of packages than need to be maintained.

Regards..
Ventrical

---

### Post by #&amp;thj^% on 2017-06-23
Thanks for sharing that with me ( Will Cooke);)...I better get my IRC sorted out to better stay informed on this matter. 
Thanks for the prod to do so.
Regards

---

### Post by ventrical on 2017-06-23
Anyone wanting to join unity7maintainers team please join here: [https://launchpad.net/~unity7maintainers](https://launchpad.net/~unity7maintainers)

Regards..

---

### Post by jbicha on 2017-06-23
ventrical, here's [something interesting]("https://sunweavers.net/blog/node/58"). Debian MATE developer Mike Gabriel is now maintaining a fork of the indicators for use in Debian MATE. Since nobody is currently developing Ubuntu's indicators, it would be interesting if Mike's work could also work for Unity 7 in Ubuntu.

I don't believe Mike has a Unity 7 install so I think he could use some help testing and integrating those indicators in to Unity. He has renamed the packages so it will need work in Unity to adapt if the indicators are compatible.

Or maybe a rename isn't necessary since the Ubuntu indicator and D-Bus names are already well-established and the Ubuntu projects need someone to take over maintenance.

---

### Post by ventrical on 2017-06-23
> **jbicha said:**
> ventrical, here's [something interesting]("https://sunweavers.net/blog/node/58"). Debian MATE developer Mike Gabriel is now maintaining a fork of the indicators for use in Debian MATE. Since nobody is currently developing Ubuntu's indicators, it would be interesting if Mike's work could also work for Unity 7 in Ubuntu.

I don't believe Mike has a Unity 7 install so I think he could use some help testing and integrating those indicators in to Unity. He has renamed the packages so it will need work in Unity to adapt if the indicators are compatible.

Or maybe a rename isn't necessary since the Ubuntu indicator and D-Bus names are already well-established and the Ubuntu projects need someone to take over maintenance.

Awesome read.  I see there are also other links.  I must be forward with you , I  only use MATE to mostly experiment with on older machines but I do not see a reason why not to help the dev you have mentioned in question. I did some experimenting with unity panel icons during 12.04 cycle but I would need  to study this a bit further

 You also brought up a good point about re-naming programs.  I have a problem with this but I think my problem does not apply to the ubuntu-linux set.  After I beta tested Torvalds first boot disk (which didn't work) I was also doing another project on Microsoft, boot-sector viruses and a system restore tool.  I had no choice but to start renaming files so that I could test my theory. All worked well but eventually, unless global settings were changed  for all then it would break. So I discovered that re-naming conventions were sloppy and could cause problems if all objects/depends were not completely  examined for pointers to original filenames.

---


 I am going to study this a bit further.

thanks ! 

regards..

---

### Post by #&amp;thj^% on 2017-06-23
Emperors New Blinders! Great Read...Wish I could find that again. :(
Way off Topic Sorry. :p

---

### Post by ventrical on 2017-06-23
> **1fallen said:**
> Emperors New Blinders! Great Read...Wish I could find that again. :(
Way off Topic Sorry. :p

And then I found Hardy Heron! :)

Regards..

---

### Post by ventrical on 2017-07-24
After updating a GNOME3 install with unity7 as an alternate desktop I am finding  more stability and refinement, dare I say, with wayland! Unity is working like it always does with barely a burp, bump or fidget.

```

ventrical@ventrical-Precision-WorkStation-T3400:~$ inxi -Fxz
System:    Host: ventrical-Precision-WorkStation-T3400 Kernel: 4.11.0-10-generic x86_64 (64 bit gcc: 6.3.0)
           Desktop: Gnome 3.24.3 (Gtk 3.22.17-0ubuntu1)
           Distro: Ubuntu Artful Aardvark (development branch)
Machine:   Device: desktop System: Dell product: Precision WorkStation T3400
           Mobo: Dell model: 0TP412 BIOS: Dell v: A03 date: 01/31/2008
CPU:       Quad core Intel Core2 Quad Q6600 (-MCP-) cache: 4096 KB
           flags: (lm nx sse sse2 sse3 ssse3 vmx) bmips: 19151
           clock speeds: max: 2393 MHz 1: 2393 MHz 2: 2393 MHz 3: 2393 MHz
           4: 2393 MHz
Graphics:  Card: NVIDIA GF119 [GeForce GT 610] bus-ID: 01:00.0
           Display Server: wayland (X.Org 1.19.3) drivers: nouveau (unloaded: modesetting,fbdev,vesa)
           Resolution: 1440x900@59.75hz
           OpenGL: renderer: Gallium 0.4 on NVD9
           version: 4.3 Mesa 17.1.2 Direct Render: Yes
Audio:     Card-1 NVIDIA GF119 HDMI Audio Controller
           driver: snd_hda_intel bus-ID: 01:00.1
           Card-2 Intel 82801I (ICH9 Family) HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.11.0-10-generic
Network:   Card: Broadcom Limited NetXtreme BCM5754 Gigabit Ethernet PCI Express
           driver: tg3 v: 3.137 bus-ID: 04:00.0
           IF: enp4s0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 160.0GB (5.8% used)
           ID-1: /dev/sda model: ST3160815AS size: 160.0GB
Partition: ID-1: / size: 74G used: 8.7G (13%) fs: ext4 dev: /dev/sda1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 42.0C mobo: N/A gpu: 32.0
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 192 Uptime: 5 min Memory: 689.0/3883.1MB
           Init: systemd runlevel: 5 Gcc sys: 6.3.0
           Client: Shell (bash 4.4.121) inxi: 2.3.23 
ventrical@ventrical-Precision-WorkStation-T3400:~$ 

```

---

### Post by Chanath on 2017-07-27
Are you having Unity 7 in Artful?

I have a Ubuntu 17.04 zesty install. I keep it as its the last real Ubuntu release. I just looked in it and updated/upgraded it. Its eof is somewhere at the end of this year, but maybe the repos would stay open. It'll be kept as a remembrance. Feel bit sorry that people had forgotten Unity so quickly. For my day to day work, I use Openbox. I'm going to use Unity 7 whole day today. 

If Unity can be installed in 17.10 and in upcoming 18.04, it'd be nice.

---

### Post by ventrical on 2017-07-27
> **Chanath said:**
> Are you having Unity 7 in Artful?

You can install unity7 in artful now.

```


sudo apt-get install unity-session

```

At the moment it is wait and see. I am hoping we will test unity-session from the universe during the 18.04 development cycle. I have been told to be patient. The devs will get back to me with a list of todos sometime.  As long as unity7 does not cause problems for GNOME then it's in. If it does cause problems .. it's pulled.
Regards..

---

### Post by Chanath on 2017-07-27
> **ventrical said:**
> 
At the moment it is wait and see. I am hoping we will test unity-session from the universe during the 18.04 development cycle. I have been told to be patient. The devs will get back to me with a list of todos sometime.  As long as unity7 does not cause problems for GNOME then it's in. If it does cause problems .. it's pulled.
Regards..

So, it would be 17.10 the last one with Unity 7.  I have a 17.10 Ubuntu install for testing. I'd install Unity 7 and try uninstall Gnome shell in the evening. If Unity 7 would stay in 18.04, I'd do the same thing.

---

### Post by ventrical on 2017-07-27
> **Chanath said:**
> So, it would be 17.10 the last one with Unity 7.  I have a 17.10 Ubuntu install for testing. I'd install Unity 7 and try uninstall Gnome shell in the evening. If Unity 7 would stay in 18.04, I'd do the same thing.

The idea of current testing is to see how unity7 works with GNOME, GNOME which is now default desktop. Perhaps in the future you can do that but we need to monitor how  it affects GNOME.

Regards..

---

### Post by ventrical on 2017-07-27
Hey:) so far, so good.! :)

[http://news.softpedia.com/news/canonical-makes-it-easy-to-install-unity7-on-ubuntu-17-10-gnome-remains-default-516638.shtml](http://news.softpedia.com/news/canonical-makes-it-easy-to-install-unity7-on-ubuntu-17-10-gnome-remains-default-516638.shtml)

If we keep testing/contributing it may make it to the universe for 18.04 cycle. That would be awesome. Even though no new feature we would get security updates to carry it along until 2024!

Regards..

---

### Post by Chanath on 2017-07-27
> **ventrical said:**
> The idea of current testing is to see how unity7 works with GNOME, GNOME which is now default desktop. Perhaps in the future you can do that but we need to monitor how  it affects GNOME.

Regards..

I understand that Canonical had decided to embrace Gnome shell for Ubuntu. Like I wrote earlier, I'd keep Unity in 17.04 as a remembrance. I'd try install Unity in 17.10 later in the evening. If it works nicely, I'll uninstall Gnome shell. I'd be checking Unity working with 17.10 time to time, without that interest in Gnome. 

BTW, I've been using Ubuntu 17.04 for last 9 hours and didn't have a single problem. It was snappy. Would you be able to create a group to look after Unity?

---

### Post by ventrical on 2017-07-27
> **Chanath said:**
> I understand that Canonical had decided to embrace Gnome shell for Ubuntu. Like I wrote earlier, I'd keep Unity in 17.04 as a remembrance. I'd try install Unity in 17.10 later in the evening. If it works nicely, I'll uninstall Gnome shell. I'd be checking Unity working with 17.10 time to time, without that interest in Gnome. 

BTW, I've been using Ubuntu 17.04 for last 9 hours and didn't have a single problem. It was snappy. Would you be able to create a group to look after Unity?

A few weeks back..

[https://launchpad.net/~unity7maintainers](https://launchpad.net/~unity7maintainers)

It is moderated team, CoC required. I invite all to join but please do not expect too much as I am waiting on what the devs will do . Perhaps there may not be any activity there until after the release of 17.10.


Regards..

---

### Post by ventrical on 2017-07-27
> **Chanath said:**
> I understand that Canonical had decided to embrace Gnome shell for Ubuntu. Like I wrote earlier, I'd keep Unity in 17.04 as a remembrance. I'd try install Unity in 17.10 later in the evening. If it works nicely, I'll uninstall Gnome shell. 


Let me know how it goes. I think it will cause breakage.

Regards..

---

### Post by Chanath on 2017-07-27
> **ventrical said:**
> Let me know how it goes. I think it will cause breakage.

Regards..

Just installed Unity on 17.10. Before installing checked Ubuntu session. Web browser started slowly, Files too. Same web browser and same Files in 17.04. Rebooted into Unity. Logout didn't have it. Checked in Xsessions. In unity.desktop it says, 

```
Exec=/usr/lib/gnome-session/run-systemd-session unity-session.target
```

In ubuntu.desktop, it says

```
Exec=gnome-session --session=ubuntu
```

So, it looks like I can uninstall as much as possible of Gnome, but can't uninstall gnome-session. I maybe wrong in my deductions. 
Anyway, Ubuntu 17.10 with Gnome is much slower than Ubuntu 17.04 with Unity. After using 17.04 for last 9 hours, using Ubuntu 17.10 is like going back in time. I use 17.10 with Openbox, and I know how fast it is. I also know how fast Xubuntu 17.10. Out of all Gnome is the slowest. Even Kubuntu 17.10 is faster. This is only the way I see or feel it.

---

### Post by Chanath on 2017-07-27
Well, I uninstalled Gnome shell, and with it went gnome-session and gdm. Unity greeter came back, which is good. I have a DE called Unity. Files, web browser is start bit slower than in 17.04. I'll come back later. Have to do some other work.

---

### Post by jbicha on 2017-07-27
> **ventrical said:**
>  we would get security updates to carry it along until 2024!


Sorry, but Canonical does not support universe packages.

Ubuntu flavors put some effort into supporting packages shipped in their default installs but for other packages there may be no security support at all. For Ubuntu 16.04 LTS, the only non-Canonical flavor to offer more than 3 years of [support]("https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#Support_lifespan") is Ubuntu Kylin which was basically Ubuntu with a bit extra on top for that release. (Ubuntu Kylin 17.04 has diverged more.)

For instance I help maintain Ubuntu GNOME but I'm not really doing any updates for Ubuntu GNOME 14.04 LTS any more because it is [End of Life]("https://lists.ubuntu.com/archives/ubuntu-gnome/2017-March/004211.html"), but I might occasionally do an update for a package that is in main if it's an important enough issue that is easy enough to fix.

---

### Post by Chanath on 2017-07-27
Testing Unity DE or Unity Session on 17.10 without gnome shell, gnome session, gdm etc for last hour or so.  Now, 17.10 looks more like Ubuntu. Its the other way around than it was before; people installed gnome shell (ppa) on Ubuntu, here I installed real Ubuntu over Gnome Ubuntu and uninstalled the Gnome shell. If it'd be still working, I'll use it for work, the whole day.

I wasn't a Unity guy, mostly because I like Openbox more. I still very strongly think that Ubuntu should not kill Unity. Gnome shell is just Gnome shell, every distro out there has it.

---

### Post by Chanath on 2017-07-28
First day without Gnome-shell in Ubuntu 17.10. Booted in to Unity without any hassle. Opera-beta opened quickly, much more quickly than it was with Gnome. The first start with Files (Nautilus) is slow, but the consequent starts are snappier, not as snappy as Thunar. Gimp started quite fast. LibreOffice too. Gnome Software is still quite slow in populating itself. I won't be using this software anyway - usually look for software in Synaptic. 

Life without Gnome-tweak-tool, Gnome-extensions in (real) Ubuntu. Upgraded in the morning. Upgrades would be checked few times in the day. A full working day with Ubuntu 17.10 Unity. Yesterday, the one-click workspaces (Ubuntu 17.04) helped me to organise my work flow. How many clicks, mouse movements to have few workspaces in Gnome?

Ubuntu was unique, but with Gnome-shell only, it won't be unique. It would most likely be seen as playing catching up with Fedora. Most people were attracted to *that* uniqueness. Who need a full screen menu?

---

### Post by ventrical on 2017-07-28
> **jbicha said:**
> Sorry, but Canonical does not support universe packages.

Ubuntu flavors put some effort into supporting packages shipped in their default installs but for other packages there may be no security support at all. For Ubuntu 16.04 LTS, the only non-Canonical flavor to offer more than 3 years of [support]("https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#Support_lifespan") is Ubuntu Kylin which was basically Ubuntu with a bit extra on top for that release. (Ubuntu Kylin 17.04 has diverged more.)

For instance I help maintain Ubuntu GNOME but I'm not really doing any updates for Ubuntu GNOME 14.04 LTS any more because it is [End of Life]("https://lists.ubuntu.com/archives/ubuntu-gnome/2017-March/004211.html"), but I might occasionally do an update for a package that is in main if it's an important enough issue that is easy enough to fix.

What I meant was that the maintainers would do most of the support work, the idea, having it the universe.

Regards..

---

### Post by ventrical on 2017-07-28
> **Chanath said:**
> First day without Gnome-shell in Ubuntu 17.10. Booted in to Unity without any hassle. Opera-beta opened quickly, much more quickly than it was with Gnome. The first start with Files (Nautilus) is slow, but the consequent starts are snappier, not as snappy as Thunar. Gimp started quite fast. LibreOffice too. Gnome Software is still quite slow in populating itself. I won't be using this software anyway - usually look for software in Synaptic. 

Life without Gnome-tweak-tool, Gnome-extensions in (real) Ubuntu. Upgraded in the morning. Upgrades would be checked few times in the day. A full working day with Ubuntu 17.10 Unity. Yesterday, the one-click workspaces (Ubuntu 17.04) helped me to organise my work flow. How many clicks, mouse movements to have few workspaces in Gnome?

Ubuntu was unique, but with Gnome-shell only, it won't be unique. It would most likely be seen as playing catching up with Fedora. Most people were attracted to *that* uniqueness. Who need a full screen menu?

@chanath.

 I really do appreciate all your testing and experiments but the topic of the thread to to test unity7 alongside GNOME to see if it causes trouble with GNOME.

> 
To keep unity7 viable we have to test it alongside GNOME and report any breakage.


Thanks..

---

### Post by jbicha on 2017-08-09
If anyone is looking to help maintain Unity, a relatively easy task is to update  unity-control-center's Details page to show 17.10 instead of 17.04.

A  bit more complicated way to fix it is to use gnome-control-center's  ubuntu-gnome-version.patch so that it will pick up the correct version  number automatically instead of needing to update the hard-coded version  for every Ubuntu release.

---

### Post by ventrical on 2017-08-10
> **jbicha said:**
> If anyone is looking to help maintain Unity, a relatively easy task is to update  unity-control-center's Details page to show 17.10 instead of 17.04.

A  bit more complicated way to fix it is to use gnome-control-center's  ubuntu-gnome-version.patch so that it will pick up the correct version  number automatically instead of needing to update the hard-coded version  for every Ubuntu release.

Just getting back from vacation. Got locked out.  Ill be looking at this.

Thanks..

---

### Post by ventrical on 2017-08-12
> **jbicha said:**
> If anyone is looking to help maintain Unity, a relatively easy task is to update  unity-control-center's Details page to show 17.10 instead of 17.04.

A  bit more complicated way to fix it is to use gnome-control-center's  ubuntu-gnome-version.patch so that it will pick up the correct version  number automatically instead of needing to update the hard-coded version  for every Ubuntu release.

So we have to manually put in the version number ??

```

m4_define([unity_control_center_version], 14.04.3)
AC_INIT([unity-control-center], [unity_control_center_version])


```
[http://bazaar.launchpad.net/~unity-control-center-team/unity-control-center/trunk/view/head:/configure.ac](http://bazaar.launchpad.net/~unity-control-center-team/unity-control-center/trunk/view/head:/configure.ac)

Or do I need to go to a different page?

As I see it , the code should use a 'get' -ubuntu-version-number-whatever  in the code but this particular source has it hemmed in
.

regards..

---

### Post by ventrical on 2017-08-12
> **jbicha said:**
> so that it will pick up the correct version  number automatically instead of needing to update the hard-coded version  for every Ubuntu release.

Not sure why they did it this way.
Don't make sense.

Regards..

---

### Post by Chanath on 2017-08-12
When you install Unity Session, you install the last Unity session, that is 17.04. Unity being a DE, it doesn't really matter, what number of the distro it came last, as far as it works. Unity as DE works quite well with artful and without the gnome-shell. Now that the pressure if off on developing Unity, maybe the devs (few, who'd still care) would keep it stable and working. Ubuntu should have its own flagship DE, whatever its name, not someone else's.

---

### Post by ventrical on 2017-08-12
> **jbicha said:**
> If anyone is looking to help maintain Unity, a relatively easy task is to update  unity-control-center's Details page to show 17.10 instead of 17.04.

A  bit more complicated way to fix it is to use gnome-control-center's  ubuntu-gnome-version.patch so that it will pick up the correct version  number automatically instead of needing to update the hard-coded version  for every Ubuntu release.

@jbicha,

Can you at least point me to the source file at launchpad, the *specific* file that deals with this issue. 

Regards..

---

### Post by ventrical on 2017-08-12
> **Chanath said:**
> When you install Unity Session, you install the last Unity session, that is 17.04. Unity being a DE, it doesn't really matter, what number of the distro it came last, as far as it works. Unity as DE works quite well with artful and without the gnome-shell. Now that the pressure if off on developing Unity, maybe the devs (few, who'd still care) would keep it stable and working. Ubuntu should have its own flagship DE, whatever its name, not someone else's.

Yes I understand this. It is a hard coded file and I need to see if I can merge it or use another command to 'get' the version number. I actually worked on this during 12.04 development, to prempt the <lsb_release -a> after version code was updated but I dropped it because it was a closed team at that time, I could work a hack on my own box but it wasn't implemented. There are tons of issues and guaranteed there will be more come 18.04.

It will break.

Regards..

---

### Post by ventrical on 2017-08-12
Never ceases to amaze me.....

---

### Post by ventrical on 2017-08-12
Ok.. got mine fixed temp :)

---

### Post by ventrical on 2017-08-12
Trying a different motif  ... photo taken by me at Public Gardens, Halifax NS.

Regards..

---

### Post by ventrical on 2017-08-12
Trim shot ...

---

### Post by Chanath on 2017-08-13
Did you simply change /usr/share/unity-control-center/ui/UbuntuLogo.png? 
Also, do you think 18.04 would break Unity?

Edit: I'll keep on using 17.10 only with Unity to see how far it'd live on. I am using it now all the time, without using other Ubuntu 17.10 (Openbox, Xubuntu, KDE) installs. They get upgraded once a week. Ubuntu Unity 17.10 gets upgraded everyday, if any available.

---

### Post by flocculant on 2017-08-13
> **Chanath said:**
> ... Do you think that Cannonical is all out to get rid of Unity?

I very much doubt that. Probably got more important things to worry about.

But given that they're not using it now - they probably don't care much, other than dealing with it in currently released versions. Hence the comments from Canonical people at the beginning of this which pretty much said - if you want to use it, maintain it. If it ends up with no maintainers from the community then it'll go the way of anything else that is unmaintained.

I guess that it will end up in Universe.

---

### Post by Chanath on 2017-08-13
> **flocculant said:**
> I very much doubt that. Probably got more important things to worry about.



You've answered my post just before I edited it. I deleted that line you quoted as an unnecessary one. Sorry to trouble you.

---

### Post by ventrical on 2017-08-13
> **Chanath said:**
> Did you simply change /usr/share/unity-control-center/ui/UbuntuLogo.png? 


Yes. That was a simple maintain. I had thought it was being called from the system but it is called from a .png file. If it ain't broke, don't fix it :) I'll have to wait  most likely until end of this cycle  to see what list Will Cooke will send me up. I got two solid and experienced persons to help me. It may take more and I am sure others will jump in.

Regards..

---

### Post by ventrical on 2017-08-13
> **flocculant said:**
> I very much doubt that. Probably got more important things to worry about.


I guess that it will end up in Universe.

Well we are at least hoping for that much. We will know more in the coming weeks. I know your hands are full with xubuntu but you are certainly invited to join the team.

Regards..

---

### Post by Chanath on 2017-08-13
> **ventrical said:**
> Yes. That was a simple maintain. I had thought it was being called from the system but it is called from a .png file. If it ain't broke, don't fix it :) I'll have to wait  most likely until end of this cycle  to see what list Will Cooke will send me up. I got two solid and experienced persons to help me. It may take more and I am sure other will jump in.

Regards..

Wish you luck with the project!:D

---

### Post by ventrical on 2017-08-13
> **Chanath said:**
> Did you simply change /usr/share/unity-control-center/ui/UbuntuLogo.png? 
Also, do you think 18.04 would break Unity?



There are bugs and issues.  Some a dog's breakfast. The 18.04  cycle will be mainly focused on GNOME as flagship unless Canonical changes their mind. (highly unlikely) and this may cause a bad experience with unity7 if it is not maintained. Therefore we need maintainers for the cycle. The more , the merrier. As I say .. all who have signed the CoC are invited to join the unity7 maintainers team. If we have a solid team core with some experience and willing to learn then we may get more help than expected from Canonical. If nobody joins and expects me and my two other members to handle all bugs and upgrades during 18.04 then that is a lot to ask don't you think? And if individuals want to work on corner cases... that just plain defeats the whole concept of the community spirit.

Regards..

---

### Post by ventrical on 2017-08-13
> **Chanath said:**
> Wish you luck with the project!:D

Hey :) Thanks ;)

regards..

---

### Post by jbicha on 2017-08-13
> **ventrical said:**
> @jbicha,

Can you at least point me to the source file at launchpad, the *specific* file that deals with this issue. 

Regards..

For the easy fix, look in debian/rules

I already provided the filename for the more complicated fix in comment #55. "Easy" is fine, it's what Ubuntu has been doing for several years.

---

### Post by Chanath on 2017-08-13
> **ventrical said:**
> If we have a solid team core with some experience and willing to learn then we may get more help than expected from Canonical. If nobody joins and expects me and my two other members to handle all bugs and upgrades during 18.04 then that is a lot to ask don't you think? Regards..

Three good people are better than 100 average! :p

---

### Post by mc4man on 2017-08-13
> **ventrical said:**
> @jbicha,

Can you at least point me to the source file at launchpad, the *specific* file that deals with this issue. 

Regards..
I see he told you.
I suspect in the case of a debian/ file change you'd need to present as a debdiff (patches are source only i believe

So read up on that. You'd also need to be able to sign your changes (the harder part of this though you'll only need to set up once..). Then start a bug & attach the debdiff inc. bug # in change description. (if this is the method..
For this deal you'd need at least devscripts, cdbs, gnome-pkg-tools  installed.
 I'll see if I can find you a page on debdiff creation.

edit; this is laid out ok, noting in this case you're neither applying or creating a patch.
[http://blog.mathieu-leplatre.info/apply-debian-patches-step-by-step.html](http://blog.mathieu-leplatre.info/apply-debian-patches-step-by-step.html)

---

### Post by jbicha on 2017-08-13
@mc4man, for Unity packages, I'd prefer a merge proposal against the bazaar branch for the specific project being fixed.

---

### Post by jbicha on 2017-08-13
> **flocculant said:**
> Hence the comments from Canonical people at the beginning of this which pretty much said - if you want to use it, maintain it. If it ends up with no maintainers from the community then it'll go the way of anything else that is unmaintained.

I guess that it will end up in Universe.

Hi. Just to be clear: unity has been in universe for a couple months. If there are no maintainers, there is a real risk of Unity being completely removed from Ubuntu. This already happened to Unity8.

---

### Post by ventrical on 2017-08-13
> **jbicha said:**
> For the easy fix, look in debian/rules



??


[http://bazaar.launchpad.net/~unity-control-center-team/unity-control-center/trunk/view/head:/debian/rules](http://bazaar.launchpad.net/~unity-control-center-team/unity-control-center/trunk/view/head:/debian/rules)

Edit: Oh yeah.. I see it now..

---

### Post by ventrical on 2017-08-13
> **jbicha said:**
> @mc4man, for Unity packages, I'd prefer a merge proposal against the bazaar branch for the specific project being fixed.

So here's the siimple fix from file 'rules'

```

#!/usr/bin/make -f

include /usr/share/cdbs/1/rules/debhelper.mk
include /usr/share/cdbs/1/rules/utils.mk
include /usr/share/cdbs/1/class/gnome.mk
include /usr/share/gnome-pkg-tools/1/rules/gnome-version.mk
include /usr/share/gnome-pkg-tools/1/rules/clean-la.mk

export DEB_BUILD_MAINT_OPTIONS = hardening=+all
export DEB_LDFLAGS_MAINT_APPEND = -Wl,-z,defs -Wl,-O1 -Wl,--as-needed
include /usr/share/dpkg/buildflags.mk

DEB_CONFIGURE_SCRIPT := ./autogen.sh
DEB_CONFIGURE_EXTRA_FLAGS += --libdir=\$${prefix}/lib/$(DEB_HOST_MULTIARCH) \
                             --disable-update-mimedb

DEB_DH_MAKESHLIBS_ARGS_unity-control-center = --no-act
DEB_DH_MAKESHLIBS_ARGS_libunity-control-center1 += -- -c4

binary-post-install/unity-control-center::
    ./panels/info/logo-generator --logo panels/info/UbuntuLogoBlank.png --text "ubuntu 17.10" --output debian/unity-control-center/usr/share/unity-control-center/ui/UbuntuLogo.png

common-binary-post-install-arch:: list-missing

```

Do I have to join the Ubuntu Desktop Team?

Could you simply walk me through 'merge proposal' ie; what do I need to do now?

Regards..

---

### Post by ventrical on 2017-08-13
> **mc4man said:**
> I see he told you.
I suspect in the case of a debian/ file change you'd need to present as a debdiff (patches are source only i believe

So read up on that. You'd also need to be able to sign your changes (the harder part of this though you'll only need to set up once..). Then start a bug & attach the debdiff inc. bug # in change description. (if this is the method..
For this deal you'd need at least devscripts, cdbs, gnome-pkg-tools  installed.
 I'll see if I can find you a page on debdiff creation.

edit; this is laid out ok, noting in this case you're neither applying or creating a patch.
[http://blog.mathieu-leplatre.info/apply-debian-patches-step-by-step.html](http://blog.mathieu-leplatre.info/apply-debian-patches-step-by-step.html)

So I just filed a bug with the fix but I got the feeling that more needs to be done. I don't have privlidges  to upload the new file. Could someone +1 this bug.

 [URL="https://bugs.launchpad.net/ubuntu/+source/unity-control-center/+bug/1710519"]https://bugs.launchpad.net/ubuntu/+source/unity-control-center/+bug/1710519
[/URL]

---

### Post by ventrical on 2017-08-13
Applied for membership of those two teams, ubuntu destop team, unity-control-center team.

---

### Post by jbicha on 2017-08-13
You don't need to be a member of those teams to contribute. And in fact, you can't join those teams until you contribute first! ;)

[Here's more information]("https://wiki.ubuntu.com/DesktopTeam/Developers") about joining the Ubuntu Desktop team.

---

### Post by ventrical on 2017-08-14
> **jbicha said:**
> You don't need to be a member of those teams to contribute. And in fact, you can't join those teams until you contribute first! ;)

[Here's more information]("https://wiki.ubuntu.com/DesktopTeam/Developers") about joining the Ubuntu Desktop team.

As I review , this is not going to happen overnight and it will be the desktop team that will make the merge requests. I'm trying to rally a couple of sponsors.

Thanks for the link.

Regards..

---

### Post by Chanath on 2017-08-14
> **jbicha said:**
> Hi. Just to be clear: unity has been in universe for a couple months. If there are no maintainers, there is a real risk of Unity being completely removed from Ubuntu. This already happened to Unity8.

Let's imagine there are no maintainers, and Unity is taken off the repos. (This is different from Unity 8 matter. Unity 8 didn't work that well for anyone to play with it.) As Unity 7 works quite well with 17.10, and might work the same way with 18.04, whoever who has Unity could just upgrade the repos to 18.04 and keep on using Unity, right? Or would apt start demanding to uninstall Unity, unity-session etc?

---

### Post by cariboo on 2017-08-14
The only reason Unity wouldn't install in later versions is because on unmet dependencies, I don't have a list handy of all the Unity dependencies, but if any of them are updated separately they may make unity uninstallable.

---

### Post by ventrical on 2017-08-15
> **cariboo said:**
> The only reason Unity wouldn't install in later versions is because on unmet dependencies, I don't have a list handy of all the Unity dependencies, but if any of them are updated separately they may make unity uninstallable.

As I understand it I am supposed to get a list after this session migration is over but I am cautioned that it may take a little time. I am not sure if they will be the list of depends of which you mention but I am assuming they will be.

Regards..

> 
Will Cooke wrote:

We need to get the session migration finished, and then we can run a  diff to work out a full list of the packages which are changing.  We'll  get this list over to you as soon as we can.
 


---

### Post by Chanath on 2017-08-15
> **cariboo said:**
> The only reason Unity wouldn't install in later versions is because on unmet dependencies, I don't have a list handy of all the Unity dependencies, but if any of them are updated separately they may make unity uninstallable.

It maybe a good idea to have a list of all the dependencies, and block them from upgraded.

---

### Post by Chanath on 2017-08-15
Today there was one Unity package upgrade, libunity-control-center1 and now the  Details say it is Ubuntu 17.10. :)

---

### Post by ventrical on 2017-08-15
> **Chanath said:**
> Today there was one Unity package upgrade, libunity-control-center1 and now the  Details say it is Ubuntu 17.10. :)

Thank you Jeremy:)

---

### Post by Chanath on 2017-08-15
The login screen still says it is Ubuntu 17.04.

---

### Post by ventrical on 2017-08-15
> **Chanath said:**
> The login screen still says it is Ubuntu 17.04.

I'll look into it.

regards..

---

### Post by mc4man on 2017-08-15
> **ventrical said:**
> I'll look into it.

regards..
That's probably /usr/share/unity-greeter/logo.png, part of unity-greeter which I guess needs lightdm, if so maybe drifting a bit from your intent..?

---

### Post by ventrical on 2017-08-15
> **mc4man said:**
> That's probably /usr/share/unity-greeter/logo.png, part of unity-greeter which I guess needs lightdm, if so maybe drifting a bit from your intent..?

I first looked at that file in nautilus and it was just a blank space in a square - so naturally I thought it was not the file I was looking for and I assumed it was called  (as like debian/rules is hardcoded). After seeing your message I double clicked and there it is. So I'll use gimp , change it , push it and do a merge request.

As always .. thanks for pointing that out.

Regards..

---

### Post by ventrical on 2017-08-15
> **mc4man said:**
> That's probably /usr/share/unity-greeter/logo.png, part of unity-greeter which I guess needs lightdm, if so maybe drifting a bit from your intent..?

I first looked at that file in nautilus and it was just a blank space in a square - so naturally I thought it was not the file I was looking for and I assumed it was called  (as like debian/rules is hardcoded). After seeing your message I double clicked and there it is. So I'll use gimp , change it , push it and do a merge request.

As always .. thanks for pointing that out.

edit: made a merge request but that one was a little tricky as they have hardcoded that file also in /rules.. but at least it is getting me up to speed.

Regards..

---

### Post by Chanath on 2017-08-31
Greetings!

How is the project developing?

---

### Post by ventrical on 2017-08-31
> **Chanath said:**
> Greetings!

How is the project developing?

 As far  I know, it is still in a holding pattern as far as the team I created is concerned . I have one new member on the team so that makes 4 of us. I had been asked originally to have patience and that lists and more information will be forthcoming.

 I can say for certain atm that there are a lot of developers doing a lot of heavy lifting maintaining the current (unity7) stack for this development cycle. Since  wayland is not completely ready for default, this may be a double edged sword. Either resources will be siphoned away from unity7 maintenance and used to focus on wayland or Canonical may decide to keep unity7 in the universe as an alternate DE for the 18.04 cycle. Daily updates of unity7 stack are there so, it is all a good sign.

 If I hear of anything I'll let the forums  and U+1 team know.

Regards..

---

### Post by ventrical on 2017-08-31
edit:

Sebastien tells me that it is "expected" to remain in the universe for 18.04 unless it become 'buggy and unmaintained" at which point it will be removed.

There is not active development on Unity7 atm.

Regards..

---

### Post by Chanath on 2017-08-31
Maintenance updates has to be given for Ubuntu 16.04 until 2021, so someone has to look after Unity 7, I believe. If that's the case, it should live in 18.04 and further.

---

### Post by ventrical on 2017-08-31
> **Chanath said:**
> Maintenance updates has to be given for Ubuntu 16.04 until 2021, so someone has to look after Unity 7, I believe. If that's the case, it should live in 18.04 and further.

This is not how it works. The depends have to be maintained and updated with regular updates consecutively to the last cycle.  They do not run concurrently on a different framework unless you use a VM, but perhaps there are other test cases. I am just in standby mode.  The decision is ultimately up to the devs. 

Regards..

---

### Post by mc4man on 2017-08-31
> **Chanath said:**
> Maintenance updates has to be given for Ubuntu 16.04 until 2021, so someone has to look after Unity 7, I believe. If that's the case, it should live in 18.04 and further.
There hasn't been an update for unity in 16.04 in almost a year, I do see maybe 1 more update & that may be it.. (unless there is some serious security issue that comes up, unlikely..
And there isn't that much of interest there, maybe a couple..
[https://code.launchpad.net/~unity-team/unity/x-sru5/+merge/326916](https://code.launchpad.net/~unity-team/unity/x-sru5/+merge/326916)

(- here in 16.04 I use a patched version that probably would be it also, maybe something to cherrypick from current, probably not. Works quite well..

---

### Post by Chanath on 2017-09-01
> **ventrical said:**
> The decision is ultimately up to the devs. Regards..

> **mc4man said:**
> There hasn't been an update for unity in 16.04 in almost a year, I do see maybe 1 more update & that may be it.. (unless there is some serious security issue that comes up, unlikely..

Its going to be a business matter, not a developer(s) matter. 17.10 is not yet released officially, and when it happens, Cannonical would see the interest or the lack of on the default Ubuntu. 17.10 would be the testing field. People are interested in stock Ubuntu, much less on the official derivatives, Ubuntu Mate and Kubuntu are higher in the interest radar than Ubuntu Gnome. Even Ubuntu Budgie is catching up faster and now being installed in dedicated hardware. There is Pop! OS in System 76, but that's their own Gnome. 

There appears to be (or might be) some trivial matters with Unity, [https://wiki.ubuntu.com/Unity/NotDefaultIssues?_ga=2.196487084.1408644008.1504204998-1292979098.1498031622](https://wiki.ubuntu.com/Unity/NotDefaultIssues?_ga=2.196487084.1408644008.1504204998-1292979098.1498031622)

---

### Post by ventrical on 2017-09-01
> **Chanath said:**
> Its going to be a business matter, not a developer(s) matter. 17.10 is not yet released officially, and when it happens, Cannonical would see the interest or the lack of on the default Ubuntu. 17.10 would be the testing field. People are interested in stock Ubuntu, much less on the official derivatives, Ubuntu Mate and Kubuntu are higher in the interest radar than Ubuntu Gnome. Even Ubuntu Budgie is catching up faster and now being installed in dedicated hardware. There is Pop! OS in System 76, but that's their own Gnome. 

There appears to be (or might be) some trivial matters with Unity, [https://wiki.ubuntu.com/Unity/NotDefaultIssues?_ga=2.196487084.1408644008.1504204998-1292979098.1498031622](https://wiki.ubuntu.com/Unity/NotDefaultIssues?_ga=2.196487084.1408644008.1504204998-1292979098.1498031622)

Yes. I am aware of this.  I tried to test Mate and Kubuntu and they are bad experiences for me. That does not mean to say they are bad experiences for others.  Unity is the desktop for me  but I am not a Canonical employee. I have no powers or privileges with the exception that I  can fix some bugs and request merges. I tired to do my best as Team captain of U+1 wiki. I tried to build bridges with Canonical developers and ubuntuforums. Unless there is a larger public, end_user reaction to the discontinuance of Unity7 then I don't think there is much else that could be done.  Unity7 is expected to be in the universe for 18.04 so this is a start.



Regards..

---

### Post by Chanath on 2017-09-01
> **ventrical said:**
> Unless there is a larger public, end_user reaction to the discontinuance of Unity7 then I don't think there is much else that could be done. 
Regards..

This can be said about the default Ubuntu with gnome shell. End user reaction for Gnome-shell is not that much. At least you can see by the amount of people coming here to discuss gnome shell problems. That lively day-to-day discussion had gone from this forum. In Unity, you couldn't do much with the Launcher or with the top panel. You just can't do that with Gnome-shell. Immediately, users would go looking for those extensions. Once they go looking for extensions, what'd left would the Ubuntu base, not the "configured" gnome-shell--just another DE with Ubuntu base. Unity was Cannonical's own, but Gnome-shell is not. Good that Cannonical is trying this out with 17.10, at least they'd know what to expect from the users in 18.10. Paid developers would come and go, but Ubuntu as a brand has to stay. Gnome shell is someone else's brand.

---

### Post by monkeybrain20122 on 2017-09-01
> **ventrical said:**
> Unless there is a larger public, end_user reaction to the discontinuance of Unity7 then I don't think there is much else that could be done.  Unity7 is expected to be in the universe for 18.04 so this is a start.



Hi, thanks for keeping Unity alive. I do plan to get involved with testing in the 18.04 cycle (right now too overwhelmed with work and life/no life :)) I would also like to do some maintenance work but don't know where to start. I have some python and C programming experience and that's it. So it would be great if you can point me to some source to learn the necessary basics.

---

### Post by rrnbtter on 2017-09-01
Greetings,
Unity has been about "convergence" from the very start. The idea was to have the relative same desktop on pc, phone, and tablet. What failed here was not the Unity Desktop, it was the complete inability to crack the Android market share of phones and tablets. Android is so embedded that Apple and MS themselves have a dismal impact. So Unity as a concept was dropped by Canonical to allow resources to go to IOT and Cloud. It's that simple. The Unity Desktop was about the "Unity" of gadgets and that idea failed not so much the desktop it's self. Gnome Shell and Wayland is a very good drop-in replacement and any deficiencies it may have are rapidly being corrected. I find that to be obvious from my day to day usage over the current dev cycle. Ubuntu as a brand should be just fine especially since they (Canonical) think that they are really an IOT and Cloud/Server company. At least that is where their aspirations seem to be based on their statement at the end of the last cycle regarding dropping Unity for desktop.

---

### Post by monkeybrain20122 on 2017-09-01
> **rrnbtter said:**
> Greetings,
Gnome Shell and Wayland is a very good drop-in replacement and any deficiencies it may have are rapidly being corrected.

I don't know about that. I keep a Fedora partition with the most up to date GS. I wouldn't say deficiencies are being corrected, rapidly or not. A lot of those "corrections", when they occur, are just reversing ill advised changes from previous iterations after a lot of complaints. I don't want to turn this into a rant thread so I would just leave it at that. :)

---

### Post by rrnbtter on 2017-09-01
Greetings,

> **monkeybrain20122 said:**
> I don't know about that. I keep a Fedora partition with the most up to date GS. I wouldn't say deficiencies are being corrected, rapidly or not. A lot of those "corrections", when they occur, are just reversing ill advised changes from previous iterations after a lot of complaints. I don't want to turn this into a rant thread so I would just leave it at that. :)

My experience with Fedora is the same. I have tried it from time to time over the years and couldn't get it off the ground. Ubuntu just seemed to work so I have stuck with it. The current Ubuntu (17.10) even in its unfinished state is a smooth robust system. This should be a good release which Canonical could use. The last one seemed to terminate in the middle of some unknown at release time.

---

### Post by Chanath on 2017-09-01
There is an announcement of Ubuntu 17.10 beta 1 releases in today's Distrowatch, but I don't find any beta 1 of default Ubuntu anywhere in the internet.

---

### Post by amano on 2017-09-01
The alpha and beta releases are just for the flavours that opt in. Standard Ubuntu doesn't (for a few years already). Thus there is no beta release. Use a cirrent daily instead.

---

### Post by ventrical on 2017-09-01
> **monkeybrain20122 said:**
> Hi, thanks for keeping Unity alive. I do plan to get involved with testing in the 18.04 cycle (right now too overwhelmed with work and life/no life :)) I would also like to do some maintenance work but don't know where to start. I have some python and C programming experience and that's it. So it would be great if you can point me to some source to learn the necessary basics.

Hi monkeybrain,

Here is unity7 team. If you have signed CoC you can join. : [https://launchpad.net/~unity7maintainers](https://launchpad.net/~unity7maintainers)

Some work example is ie; doing a fix/merge request: [https://code.launchpad.net/~dale-f-beaudoin/unity-greeter/logopng_version_update/+merge/329084](https://code.launchpad.net/~dale-f-beaudoin/unity-greeter/logopng_version_update/+merge/329084)

so I am assuming that I will get a list of todos and things that need to be maintained after the release of this cycle. Your offer of help very welcomed.

Regards..

---

### Post by ventrical on 2017-09-01
> **Chanath said:**
> This can be said about the default Ubuntu with gnome shell. End user reaction for Gnome-shell is not that much. At least you can see by the amount of people coming here to discuss gnome shell problems. That lively day-to-day discussion had gone from this forum. In Unity, you couldn't do much with the Launcher or with the top panel. You just can't do that with Gnome-shell. Immediately, users would go looking for those extensions. Once they go looking for extensions, what'd left would the Ubuntu base, not the "configured" gnome-shell--just another DE with Ubuntu base. Unity was Cannonical's own, but Gnome-shell is not. Good that Cannonical is trying this out with 17.10, at least they'd know what to expect from the users in 18.10. Paid developers would come and go, but Ubuntu as a brand has to stay. Gnome shell is someone else's brand.

Well you see Chanath, while unity7, unity8 and mir and 'convergence'  was the flagship hallamark  of Canonical, it created an atmosphere of extreme competitiveness and this in turn caused some division and a bad mojo in the development community. I do not want to itemize  all the failures, hurdles and difficulties that confronted the convergence flowchart and there is certainly no pointing of fingers at any one segment of any given project but the basic idea of why unity was pulled was because it had a unique exclusivity from the other DEs and this led to a sense that it may be counter-community and we all know that Ubuntu is a community where the sum of it's parts are it's whole. The unity8 and convergence story came to a head when it was pointed out that Canonical would have to carry the financial brunt of the development resources required as well as the physical infrastructure. So, despite the fact that Unity was the Ubuntu brand it meant that further development unity8 and the unity project as a whole would be  a financial burden to the company.

  So the founders looked back to the days of maverick meercat and how well Gnome2 worked on the Ubuntu stack and decided  that perhaps it would be more prudent and feasible to roll back on convergence and go with the status quo for now. It took a lot of bad air  out of the development shacks and so we have a more cohesive, friendly and productive development environment. They decided that Gnome3 was able to incorporate more novel concepts and graphical ideas that are more mainstream and current and so , in this light, gnome-shell (with or without wayland) presents a more competitive and efficient DE than unity may have provided. However, unity and mir are still in the alcoves being maintained and there is no telling that perhaps in the near future it may actually become a singular spin of it's own like xubuntu or lubuntu for example but this would depend greatly on community involvment.

Regards..

---

### Post by ventrical on 2017-09-01
> **monkeybrain20122 said:**
> I don't know about that. I keep a Fedora partition with the most up to date GS. I wouldn't say deficiencies are being corrected, rapidly or not. A lot of those "corrections", when they occur, are just reversing ill advised changes from previous iterations after a lot of complaints. I don't want to turn this into a rant thread so I would just leave it at that. :)

Good points. Fedora has always ran much slower in my experience. Beautiful themes. I am not being biased here but I actually left Fedora for Unity which is probably the snappiest and quickest DE on the planet (with the exception of xubuntu and lubuntu) on slower, more legacy boxes.

Regards..

---

### Post by Chanath on 2017-09-02
I've been using Unity 7 for 8-9 hour work since I said I'd do that. You need a reliable distro for work and Ubuntu Unity in 17.10 had been really good. I didn't have a single problem with it. I had been using mostly Openbox and Xubuntu, and had let go of Unity for quite some time. I found such a liking for Unity. Not Mir, not Unity 8, but Unity 7. Unity was the trademark of Ubuntu, the rest being following ons.  Nowadays, when you open [https://www.ubuntu.com](https://www.ubuntu.com), you see Desktop in the 4th place, and that tells a story.

---

### Post by wgarcia on 2017-09-12
I just updgraded to Ubuntu 17.10 from 17.04, and of course after restart I got gdm3  and only the option to start the Gnome desktop. To go back to Unity I had to issue
```
sudo dkpg-reconfigure lightdm
```
to set up lightdm again as manager, and there I had the option to start Unity, which was still configured exactly as I left it in 17.04. The only bug I got so far is:

[https://bugs.launchpad.net/ubuntu/+source/indicator-printers/+bug/1703046](https://bugs.launchpad.net/ubuntu/+source/indicator-printers/+bug/1703046)

So now I'm in the ship of testing Unity along Gnome in 17.10.

---

### Post by ventrical on 2017-09-12
> **wgarcia said:**
> I just updgraded to Ubuntu 17.10 from 17.04, and of course after restart I got gdm3  and only the option to start the Gnome desktop. To go back to Unity I had to issue
```
sudo dkpg-reconfigure lightdm
```
to set up lightdm again as manager, and there I had the option to start Unity, which was still configured exactly as I left it in 17.04. The only bug I got so far is:

[https://bugs.launchpad.net/ubuntu/+source/indicator-printers/+bug/1703046](https://bugs.launchpad.net/ubuntu/+source/indicator-printers/+bug/1703046)

So now I'm in the ship of testing Unity along Gnome in 17.10.

Thanks  so much! :) and all testers testing gnome and the other DEs.

@wgarcia,,

 I am going to put this up in sticky for sudo helpers.

---

### Post by wgarcia on 2017-09-13
I think 
```
sudo dpkg-reconfigure gdm3
```
would also work, but I haven't tried it.

---

### Post by Chanath on 2017-09-13
Using default Ubuntu.
1) Log into Ubuntu with Xorg to use Synaptic.
2) Search for lightdm, mark it, click apply. Don't click enter yet.
3) Find out what gets installed together with lightdm. Some of them are unnecessary. Unmark them, if you want.
4) Move to lightdm and click apply and enter.
5) Reboot and you have the Unity Greeter. The ugly GDM is gone.

Unity Greeter is default Ubuntu, so that's what should come with Ubuntu.:)

---

### Post by Chanath on 2017-09-17
Greetings!

If there are no more updates for Unity, just download the whole package and keep it somewhere. It'd be the repo for making any future Ubuntu a Unity one.

---

### Post by ventrical on 2017-09-17
unity-session still has upgrades.
unity-session is proprietary software -- so I can't add development tweaks unless I jump through hoops :)

---

### Post by Chanath on 2017-09-17
> **ventrical said:**
> unity-session still has upgrades.
unity-session is proprietary software -- so I can't add development tweaks unless I jump through hoops :)

Could be, but you can download and keep it in a private repo. It doesn't have to be named unity-session...

---

### Post by ventrical on 2017-09-17
> **Chanath said:**
> Greetings!

If there are no more updates for Unity, just download the whole package and keep it somewhere. It'd be the repo for making any future Ubuntu a Unity one.

Where?
Point me too it.

---

### Post by Chanath on 2017-09-17
> **ventrical said:**
> Where?
Point me too it.

People do that, don't they, keep a private repo?

---

### Post by ventrical on 2017-09-17
> **Chanath said:**
> People do that, don't they, keep a private repo?

Point me to the link where the packages are! please and thank-you.

---

### Post by Chanath on 2017-09-17
You can find them through Synaptic. It'd show, what packages, dependencies etc.
***Unity is a desktop experience that sings!***

---

### Post by ventrical on 2017-09-17
> **Chanath said:**
> You can find them through Synaptic. It'd show, what packages, dependencies etc.
***Unity is a desktop experience that sings!***

Nope. Thats not it Chanath.

 Look. I'll take a search later on this.

Regards..

---

### Post by ventrical on 2017-09-17
[https://launchpad.net/ubuntu/+source/gnome-session/3.26.0-0ubuntu1/+build/13375728](https://launchpad.net/ubuntu/+source/gnome-session/3.26.0-0ubuntu1/+build/13375728)

 I want to wait until the release of this cycle. So I just have to trust that Will and Sebastien will send me a list for maintainers work.

---

### Post by ventrical on 2017-09-17
...and so here is what we are dealing with..

[https://www.theregister.co.uk/2017/04/10/mark_shuttleworth_says_some_free_software_contributors_are_deeply_anti_social/](https://www.theregister.co.uk/2017/04/10/mark_shuttleworth_says_some_free_software_contributors_are_deeply_anti_social/)

so I worked with Torvald's OS in 95 , Microsoft since 88 and Association of Shareware Professionals and I seen it all.  So when I found Ubuntu I found an amazing peace of mind so I tend to lean towards some of Mark's feelings on this.

---

### Post by Chanath on 2017-09-17
OK. Lot of people would thank you for maintaining Unity and if possible creating a Unity as a derivative of Ubuntu.

---

### Post by ventrical on 2017-09-17
> **Chanath said:**
> OK. Lot of people would thank you for maintaining Unity and if possible creating a Unity as a derivative of Ubuntu.

There are 4 of us on the team so far. There is still some instructional development I need to learn.  There are currently a lot of helpers from the ubuntu-desktop-team to help us. Mark is back as CEO so that might help a little as he has put so much of his genius, efforts and talents in creating
 it but I do not think he will be developing unity, just advocating it's maintenance, hopefully.

regards..

---

### Post by Chanath on 2017-09-17
> **ventrical said:**
> There are 4 of us on the team so far. There is still some instructional development I need to learn.  There are currently a lot of helpers from the ubuntu-desktop-team to help us. Mark is back as CEO so that might help a little as he has put so much of his genius, efforts and talents in creating
 it but I do not think he will be developing unity, just advocating it's maintenance, hopefully.

regards..

Its his project. Ubuntu 4.10 showed me path to Linux. I hope, he'd find calm and come back to his project. And, ignore the "muppets."

---

### Post by Chanath on 2017-09-17
Your link send me to another, [https://plus.google.com/+MarkShuttleworthCanonical/posts/7LYubpaHUHH](https://plus.google.com/+MarkShuttleworthCanonical/posts/7LYubpaHUHH)
Maga Laan replying to Mark says a lot.

---

### Post by ventrical on 2017-09-18
> **Chanath said:**
> Your link send me to another, [https://plus.google.com/+MarkShuttleworthCanonical/posts/7LYubpaHUHH](https://plus.google.com/+MarkShuttleworthCanonical/posts/7LYubpaHUHH)
Maga Laan replying to Mark says a lot.
  

 It's a very negative diatribe. 

Regards..

---

### Post by Chanath on 2017-09-18
> **ventrical said:**
> It's a very negative diatribe. 

Regards..

It was written in April, and maybe most [COLOR=#000000]"general Ubuntu users" thought that way those days, maybe even now. Most users might not even know that default Ubuntu is moving to Gnome. There'd be lot of comments after 16th October in the 'net, I believe.

I am glad that Mark is back at the helm. [/COLOR]

---

### Post by ventrical on 2017-09-18
Uubuntu with Unity 9 and beyond:

I was just brainstorming with the idea of a separate distro of Unity Ubuntu or Uubuntu with Unity 9 DE development for desktops/laptops only. Going through some of the threads I notice that 60+ percent of the threads deal with Unity current in 14.04 and 16.04 so Unity is still a very popular DE.  In the next 10 years a lot of PC form factors that are current now could still be viably used with an Unity DE so there is , after all, a market for UnityDE and it is more than just nostalgic. If this were solely a community project it would not  draw  too many resources from Canonical devs as they will be focused on gnome default.

Gnome 17.10 + Unity:

So far, so good here.

Kubuntu 17.10 + Unity

A complete fail here.

If anyone else is testing Unity on Xubuntu or Lubuntu then please feel free to report in here or if you would like to test those options then please do if you have spare time.

Regards..

---

### Post by Chanath on 2017-09-18
I like the idea of Ubuntu Unity as separate distro. Even though I like to use minimum DEs or no DEs, Unity is something Ubuntu is. 
Xubuntu and Lubuntu are great distros and they have their firm place in the Ubuntu family. Unity can be installed in Xubuntu and Lubuntu, and they work quite happily alongside. I have tried that earlier. Unity also works well with Openbox. (Lubuntu is also Openbox based.)

Ubuntu Unity should live on!
You'd be surprised how many users would embrace that.
And, it'd be an overnight success!

---

### Post by ventrical on 2017-09-18
In some of my earlier research I had found that I could run concurrent desktops, that were actually using two different kernels. This was taking advantage of the vChip technology that comes with intell/AMD processors. 16GBs of Ram works exceptionally well running two concurrent desktops. In the past we could (and still can) run several DEs from the Unity Greeter or GDM, ie; Unity, Gnome Classic, Kubuntu, Lubuntu etc.

So in my brainstorming came up a concept for building a DE hypervisor manager called Harmony, The idea would be that you could use Harmony DEM(c) (Desktop Experience Manager) to switch desktops without rebooting!! This could potentially eliminate a lot of breakage and conflicts that are known to happen while running several DEs on a distribution  designed for one specific DE. Of course HarmonyDEM would be designed to replace current lightdm and gdm. 

Regards...

---

### Post by ventrical on 2017-09-18
> **Chanath said:**
> I like the idea of Ubuntu Unity as separate distro. Even though I like to use minimum DEs or no DEs, Unity is something Ubuntu is. 
Xubuntu and Lubuntu are great distros and they have their firm place in the Ubuntu family. Unity can be installed in Xubuntu and Lubuntu, and they work quite happily alongside. I have tried that earlier. Unity also works well with Openbox. (Lubuntu is also Openbox based.)


Thanks for your testings. Perhaps it would not be so bad if we could even get the Xubuntu community to take on some of the Unity7 maintenance duties. I have always asked the question as to why one distribution or another has to be so centric to a specific themed DE. Why does there have to be this big stumbling block in between them? Why can't the depends be slipstreamed and jockeyed using something like the conceptual Harmony DEM?

Regards..

---

### Post by flocculant on 2017-09-18
> **ventrical said:**
> ...
If anyone else is testing Unity on Xubuntu or Lubuntu then please feel free to report in here or if you would like to test those options then please do if you have spare time.

Regards..

I can have a look on a used and abused xubuntu instance and see what gives, before the partition is blitzed. Though it's not a standard Xubuntu by any stretch of the imagination, it has a whole bunch of Gtk3 packages either from ppa or built from git.
> **ventrical said:**
> ...Perhaps it would not be so bad if we could even get the Xubuntu community to take on some of the Unity7 maintenance duties...

If by Xubuntu community you mean the official Xubuntu team then this is extremely unlikely, we've only just got enough time to do what we need to for Xubuntu, in addition the devs we do have are heavily involved with porting Xfce to Gtk3.

---

### Post by Chanath on 2017-09-18
> **ventrical said:**
> I have always asked the question as to why one distribution or another has to be so centric to a specific themed DE. Why does there have to be this big stumbling block in between them? Regards..

There had been an idea that became a distro. Hybryde Evolution, Hybryde Fusion and 2 more before. You can watch it at work Hybryde Evolution [https://www.youtube.com/watch?v=oT5EN0knSt4](https://www.youtube.com/watch?v=oT5EN0knSt4) (based on Ubuntu 12.04) and here  Hybryde Fusion [https://www.youtube.com/watch?v=uXj44XmMz5k](https://www.youtube.com/watch?v=uXj44XmMz5k) (based on Ubuntu 13.04)

---

### Post by ventrical on 2017-09-18
> **flocculant said:**
> I can have a look on a used and abused xubuntu instance and see what gives, before the partition is blitzed. Though it's not a standard Xubuntu by any stretch of the imagination, it has a whole bunch of Gtk3 packages either from ppa or built from git.


If by Xubuntu community you mean the official Xubuntu team then this is extremely unlikely, we've only just got enough time to do what we need to for Xubuntu, in addition the devs we do have are heavily involved with porting Xfce to Gtk3.

 I appreciate your forwardness and honesty.

Thanks..

Regards..

---

### Post by ventrical on 2017-09-18
> **Chanath said:**
> There had been an idea that became a distro. Hybryde Evolution, Hybryde Fusion and 2 more before. You can watch it at work Hybryde Evolution [https://www.youtube.com/watch?v=oT5EN0knSt4](https://www.youtube.com/watch?v=oT5EN0knSt4) (based on Ubuntu 12.04) and here  Hybryde Fusion [https://www.youtube.com/watch?v=uXj44XmMz5k](https://www.youtube.com/watch?v=uXj44XmMz5k) (based on Ubuntu 13.04)

Those are not what I had in mind. I assume they are using high end machines.  I was thinking more middle of the road desktop PCs. But thanks for pointing out that the concept is not a new one.

Regards..

---

### Post by ventrical on 2017-09-18
> **flocculant said:**
> I can have a look on a used and abused xubuntu instance and see what gives, before the partition is blitzed. Though it's not a standard Xubuntu by any stretch of the imagination, it has a whole bunch of Gtk3 packages either from ppa or built from git.


Only bug so far is that I can't paste files to unity desktop using xubuntu distro.  uhh but when you have time to test unity ..:) Thanks

---

### Post by Chanath on 2017-09-18
> **ventrical said:**
> Those are not what I had in mind. I assume they are using high end machines.  I was thinking more middle of the road desktop PCs. But thanks for pointing out that the concept is not a new one.

Regards..

Worked on ordinary laptop. That distro is no more. If you want, I can send you the link, where you can download the i386 Hybryde Evolution iso. I can't find the Hybryde Fusion.

---

### Post by ventrical on 2017-09-18
I have been working PCs now for many years. Because of this I find I am a little more prone to eyestrain while working in too graphical a desktop experience and I wear glasses during all my login sessions. Unity7 (as are other DEs also) has a left justified panel that I can keep on all the time. I do not choose auto-hide or tweaks such as those so it is good enough for me to just pin apps to the panel and leave them there. Basically what I am sharing is that the default unity theme is so easy on my eyes it is unbelievable ! So too graphical stuff hurts my eyes:)

Regards..

---

### Post by ventrical on 2017-09-18
> **Chanath said:**
> Worked on ordinary laptop. That distro is no more. If you want, I can send you the link, where you can download the i386 Hybryde Evolution iso. I can't find the Hybryde Fusion.

No. Please .. that won't be neccessary.

Thanks anyways.

Regards.

---

### Post by ventrical on 2017-09-20
Gnome+Unity7 testing  working very well here. Unity works as if it were an LTS release. Gnome-shell has greatly advanced  with 3.26 and there does not seem to be any conflict between the two DEs. One note : On some of my installs I will notice that the unity dash will remember last apps used but , then on others it will not remember. This perhaps  a zietgiest issue.

Regards..

---

### Post by joshi2 on 2017-09-20
1. Unity Tweak Tool doesn't work. Says something about missing schema.
2. Appindicators doesn't work, Slack, Skype etc.
3. User name on top bar doesn't work although it's enabled from the settings.

---

### Post by ventrical on 2017-09-20
> **joshi2 said:**
> 1. Unity Tweak Tool doesn't work. Says something about missing schema.
2. Appindicators doesn't work, Slack, Skype etc.
3. User name on top bar doesn't work although it's enabled from the settings.

Thanks for pointing those out. Certainly there are issues. So user name on top bar - that would be unity-settings- daemon    I believe.

Regards..

---

### Post by ventrical on 2017-09-20
Just a refresh on listed issues:

> 

There are some other incompatibilities in the desktop session  between  GNOME Settings Daemon & Unity Settings Daemon, or GNOME  Online  Accounts & Ubuntu Online Accounts.  We need to use the GNOME   version in the GNOME session, so these would be prime candidates for a  community team to maintain in the future for the U7 session.
 
 
 Where does this leave Unity 7 in 17.10 then?  At the moment we are   testing Unity 7 alongside GNOME Shell to spot when something we land   causes Unity 7 to break.  While we can probably work around some of   these issues, the overall experience will be hampered by the  incompatibility between our U7 patches & services and GNOME  Shell,  and this will, unfortunately, degrade the U7 experience on  17.10.   We're still looking at what changes could be made to keep U7  working in  the archive so I can't make any promises of functionality yet.  I'd  like to make that call before Beta 1 so people  know what to expect.
 
 
 Any community teams who'd be interested in helping out with that  would  be very welcome and I'd be very happy to help get them set up with  the  access they need and support from the Desktop Team.
 

And as we are long past Beta 1 I will check up on this.

Regards..

---

### Post by ventrical on 2017-09-20
I am told that  Canonical developers will NOT be maintaining unity7 in 17.10 or 18.04 Basically we are just testing  Unity7 in 17.10 currently to see if there are any show-stoppers.  I have done two commits and merge request with both (non-critical) fixes released. As I gather it , that is the core of any activity in maintenance  of unity7 atm with the exception of all the helpers from jbicha, sebastien and didrocks.  I requested a clarification on all of this. As it stands there is still a small group of  maintainers on the ready -. Soon as I get clarification on this I'll post it.

Regards..

---

### Post by ventrical on 2017-09-20
As it stands currently:
from Dale Beaudoin to will Cooke;

> 
[FONT=Calibri][SIZE=3][COLOR=black][FONT=Calibri]Could you please clarify if Unity7 will be available in universe for 18.04?
 
 
 Here is link to small list of current probs.
 
 
 
 
 [https://ubuntuforums.org/showthread.php?t=2363847&page=15&p=13688879#post13688879](https://ubuntuforums.org/showthread.php?t=2363847&page=15&p=13688879#post13688879)

[/FONT][/COLOR][/SIZE][/FONT][FONT=Calibri][SIZE=3][COLOR=black][FONT=Calibri]

Will Cooke to [FONT=Calibri]D[/FONT]ale Beaudoin:



Thanks for the link, I'll ask QA to take a look. 
 
 At this point it's hard to say if it will be there or not.  I  /think/ it probably will be, if it continues to generally work (and I  fully expect it to) then I think it will be safe to leave it in  Universe)
 
 
 Cheers, Will

[FONT=Calibri]

Regards..

[/FONT]




[/FONT][/COLOR][/SIZE][/FONT]

---

### Post by ventrical on 2017-09-20
> **ventrical said:**
> Anyone wanting to join unity7maintainers team please join here: [https://launchpad.net/~unity7maintainers](https://launchpad.net/~unity7maintainers)

Regards..

3 persons have joined up on the team so far.  I have requested from Will Cooke if he still needs a team as such to let me know. As I hear more I will post back here.

Thanks..

Regards..

---

### Post by ventrical on 2017-09-20
As I see it at the moment we will most likely be *testing* unity7 on gnome-default into 18.04. 

Regards..

---

### Post by mc4man on 2017-09-20
I'd think the 1st. decent roadblock would be if the current unity source is built for 18.04 repo rather than just packages copied over from 17.10

If it's the former then the strong odds are it'll fail to build... (- currently in 17.10 it will no longer build.

---

### Post by ventrical on 2017-09-20
> **mc4man said:**
> I'd think the 1st. decent roadblock would be if the current unity source is built for 18.04 repo rather than just packages copied over from 17.10

If it's the former then the strong odds are it'll fail to build... (- currently in 17.10 it will no longer build.

This is what I am waiting on atm.

Could you perhaps put up an abbreviated psudeo_code list of Todos? or even a listed flowchart so I can get some wind into the sails on this or at least have a better idea of what I have to commit to? 

Thanks ..regards..

---

### Post by mc4man on 2017-09-20
> **ventrical said:**
> This is what I am waiting on atm.

Could you perhaps put up an abbreviated psudeo_code list of Todos? or even a listed flowchart so I can get some wind into the sails on this or at least have a better idea of what I have to commit to? 

Thanks ..regards..
This would be the current 17.10 unity FTBFS, normally would file a bug  but now..
> .....
-- Checking for module 'compiz'
--   Found compiz, version 0.9.13.1
-- Checking for module 'compiz-opengl'
--   Found compiz-opengl, version 0.9.13.1
-- GSettings schemas will be installed into /usr/share/glib-2.0/schemas/
-- Checking for module 'compiz-composite'
--   Found compiz-composite, version 0.9.13.1
CMake Error at plugins/unityshell/CMakeLists.txt:1 (find_package):
  By not providing "FindCompiz.cmake" in CMAKE_MODULE_PATH this project has
  asked CMake to find a package configuration file provided by "Compiz", but
  CMake did not find one.

  Could not find a package configuration file provided by "Compiz" with any
  of the following names:

    CompizConfig.cmake
    compiz-config.cmake

  Add the installation prefix of "Compiz" to CMAKE_PREFIX_PATH or set
  "Compiz_DIR" to a directory containing one of the above files.  If "Compiz"
  provides a separate development package or SDK, be sure it has been
  installed.


-- Configuring incomplete, errors occurred!
..

( it's not from newer gcc/g++ or cmake, last build of the current unity source was on 2017-07-21

---

### Post by wgarcia on 2017-09-21
Thanks @mc4man. What package is this, exactly? I think it is still worth it to file a bug report.

---

### Post by ventrical on 2017-09-21
I am reading up on this : [http://packaging.ubuntu.com/html/fixing-ftbfs.html](http://packaging.ubuntu.com/html/fixing-ftbfs.html)

---

### Post by ventrical on 2017-09-21
> **mc4man said:**
> I'd think the 1st. decent roadblock would be if the current unity source is built for 18.04 repo rather than just packages copied over from 17.10

If it's the former then the strong odds are it'll fail to build... (- currently in 17.10 it will no longer build.

And that  brings us here - so I am assuming that packages will just be copied over and we will fix issues from there

from Will Cooke..

> 
We're not going to maintain U7 in 17.10 or 18.04, and that was never our intention. It will be maintained in 16.04 until 2021.
 
 
 What we are doing though is regular testing on U7 in 17.10 to make  sure it's still basically functional, and so far that testing hasn't  flagged up an serious issues, but, perhaps you know better?  Are there  some big problems at the moment?


..so I am still waiting for more clarification.  It could become arduous to maintain and that would be a bad experience.

Regards..

---

### Post by Chanath on 2017-09-21
> **ventrical said:**
> I am told that  Canonical developers will NOT be maintaining unity7 in 17.10 or 18.04 Basically we are just testing  Unity7 in 17.10 currently to see if there are any show-stoppers. 

If there are no developers to maintain Unity 7 further, it means its frozen. Unity works with Xorg and Xorg is not going to be taken off from the repos for a long time (Xubuntu, Ubuntu Studio etc). Unity can be installed on Ubuntu base and would work. As Xorg is not going anywhere, Unity 7 would keep on working.

---

### Post by ventrical on 2017-09-21
Well.. for example we could still do  fix,commit and merge requests when bugs arise during the 18.04 if it is , in fact, in the repo.  Thats all we were doing during this cycle. ie  changing the 17.04 to 17.10 in the log-on screen and changing 17.04 to 17.10  logo in the 'about ubuntu' unity-control-center. etc.. plus other fixes tweaks that jbicha and seb did. I don't have a crystal ball on this one .. so it's in the air.

---

### Post by mc4man on 2017-09-21
if it can't build then at least from my perspective you can stick a fork in it.
The initial ftbfs (configure error) is solved by a no change rebuild of compiz.
However that just exposes the next fail, likely on bamf and or glib
One ex. of a dozen or so
> unity-shared/BamfApplicationManager.cpp:382:4: [COLOR="#FF0000"]error:[/COLOR] no matching function for call to ‘unity::glib::SignalManager::Add<void, BamfView*, BamfView*>(unity::glib::Object<_BamfView>&, const char [14], unity::bamf::Application::Application(const unity::ApplicationManager&, const unity::glib::Object<_BamfApplication>&)::<lambda(BamfView*, BamfView*)>)’
   }[COLOR="#FF0000"])[/COLOR];
    [COLOR="#FF0000"]^[/COLOR]

As unity shares some libraries with gnome(shell) this is just likely to get worse..

---

### Post by ventrical on 2017-09-21
> **mc4man said:**
> if it can't build then at least from my perspective you can stick a fork in it.
The initial ftbfs (configure error) is solved by a no change rebuild of compiz.
However that just exposes the next fail, likely on bamf and or glib
One ex. of a dozen or so


As unity shares some libraries with gnome(shell) this is just likely to get worse..

which brings it back to square one-

> 
The problems for U7 arise in 17.10 and beyond because of the way we   have patched the Gtk libraries & apps to get them to integrate well   with Unity 7.  For example, we patch out header bars and client side   decorations & patch in support for the global menus.  This are  fundamentally incompatible with GNOME Shell, and so we need to  make a  decision about whether to add more patches to make these apps  work well  in both Unity 7 and GNOME Shell or drop the patches and focus  on the  GNOME Shell experience.  The current preference is drop the patches.
 
 
 There are some other incompatibilities in the desktop session  between  GNOME Settings Daemon & Unity Settings Daemon, or GNOME  Online  Accounts & Ubuntu Online Accounts.  We need to use the GNOME   version in the GNOME session, so these would be prime candidates for a  community team to maintain in the future for the U7 session.
 
 
 Where does this leave Unity 7 in 17.10 then?  At the moment we are   testing Unity 7 alongside GNOME Shell to spot when something we land   causes Unity 7 to break.  While we can probably work around some of   these issues, the overall experience will be hampered by the  incompatibility between our U7 patches & services and GNOME  Shell,  and this will, unfortunately, degrade the U7 experience on  17.10.   We're still looking at what changes could be made to keep U7  working in  the archive so I can't make any promises of functionality yet.  I'd  like to make that call before Beta 1 so people  know what to expect.


so what kind of workload (in your opinion) would it take to get the unity packages up to snuff so as to compile correctly? What would a community team need to do besides those things which Will has mentioned?



Regards..

---

### Post by ventrical on 2017-09-21
> **Chanath said:**
> If there are no developers to maintain Unity 7 further, it means its frozen. Unity works with Xorg and Xorg is not going to be taken off from the repos for a long time (Xubuntu, Ubuntu Studio etc). Unity can be installed on Ubuntu base and would work. As Xorg is not going anywhere, Unity 7 would keep on working.

A unity update is coming this week.


From Seb
> 
I'm not sure there is anything  specific that needs to be done. We are having an unity update with some  fixing landing this week in artful but otherwise patches/code  reviews/etc are always welcome


---

### Post by Chanath on 2017-09-21
> [COLOR=#000000]*The problems for U7 arise in 17.10 and beyond because of the way we have patched the Gtk libraries & apps to get them to integrate well with Unity 7. For example, we patch out header bars and client side decorations & patch in support for the global menus. This are fundamentally incompatible with GNOME Shell, and so we need to make a decision about whether to add more patches to make these apps work well in both Unity 7 and GNOME Shell or drop the patches and focus on the GNOME Shell experience. The current preference is drop the patches.*[/COLOR]

[COLOR=#000000]*Where does this leave Unity 7 in 17.10 then? At the moment we are testing Unity 7 alongside GNOME Shell to spot when something we land causes Unity 7 to break. While we can probably work around some of these issues, the overall experience will be hampered by the incompatibility between our U7 patches & services and GNOME Shell, and this will, unfortunately, degrade the U7 experience on 17.10.*[/COLOR]

If you want to keep Unity working, you have to go away from Gnome, the default Ubuntu. Unity has to live alone and with Xorg. With no gnome-shell stuff around, it'd survive. It maybe better to concentrate on creating a derivative. Today's Unity users might like to stick with Unity, even the frozen one, rather than migrating to Gnome. Not every user checks on development releases, or even the intermediate releases. When time comes for the present 16.04 users to leave Unity and move to Gnome, there'd be quite a lot of shouting. So, its better to create the derivative, of course, if the company gives the green light.

---

### Post by ventrical on 2017-09-21
> **Chanath said:**
> If you want to keep Unity working, you have to go away from Gnome, the default Ubuntu. Unity has to live alone and with Xorg. With no gnome-shell stuff around, it'd survive. It maybe better to concentrate on creating a derivative. Today's Unity users might like to stick with Unity, even the frozen one, rather than migrating to Gnome. Not every user checks on development releases, or even the intermediate releases. When time comes for the present 16.04 users to leave Unity and move to Gnome, there'd be quite a lot of shouting. So, its better to create the derivative, of course, if the company gives the green light.

There are some other steps first to do. I am working on this with another admin on the U7 maintainers team .

Thanks for your ideas on this. Many share the same sentiments.

regards..

---

### Post by mc4man on 2017-09-21
> **ventrical said:**
> which brings it back to square one-



so what kind of workload (in your opinion) would it take to get the unity packages up to snuff so as to compile correctly? What would a community team need to do besides those things which Will has mentioned?



Regards..
Atm, nothing,  I see activity in Bazaar  so there could be a newer build coming up
(- they definitely saw the issue with compiz-dev, gcc-7 so one would think anything else would be addressed, at least for the moment.

---

### Post by ventrical on 2017-09-21
> **mc4man said:**
> Atm, nothing,  I see activity in Bazaar  so there could be a newer build coming up
(- they definitely saw the issue with compiz-dev, gcc-7 so one would think anything else would be addressed, at least for the moment.

I had sent a link to your message and forwarded it to Sebastien Bacher. [https://ubuntuforums.org/showthread.php?t=2363847&page=16&p=13689012#post13689012](https://ubuntuforums.org/showthread.php?t=2363847&page=16&p=13689012#post13689012)

Could you point me to the link to file packages you are  doing builds from please?

Thanks..

Regards..

---

### Post by ventrical on 2017-09-21
> **wgarcia said:**
> Thanks @mc4man. What package is this, exactly? I think it is still worth it to file a bug report.

I think perhaps ..  [https://launchpad.net/ubuntu/+source/gnome-session/3.26.0-0ubuntu1](https://launchpad.net/ubuntu/+source/gnome-session/3.26.0-0ubuntu1)

---

### Post by mc4man on 2017-09-21
> **ventrical said:**
> I think perhaps ..  [https://launchpad.net/ubuntu/+source/gnome-session/3.26.0-0ubuntu1](https://launchpad.net/ubuntu/+source/gnome-session/3.26.0-0ubuntu1)
No, I was referring to unity source & [active branch]("https://code.launchpad.net/%7Eunity-team/unity/trunk/+activereviews") merge requests
Anyway was now able to get unity to build using what i found there in conjunction with a rebuilt compiz-dev.. 
(- it failed one test  so I had to disable it but that test would be likely to fail in a local build (headless x
So that's a positive thing..

---

### Post by mc4man on 2017-09-21
Mainly was wanting to rebuild to see if some application icons became functional & to see if I could still still enable the systray if need be..

---

### Post by Chanath on 2017-09-21
If your team is going to maintain Unity 7 in the future, what all these bug reports going to achieve? Actually, aren't those bugs have to directed to your team, as there are no Unity 7 devs in the company? I don't think one car maker would help the other car maker to make a better car than theirs.

---

### Post by mc4man on 2017-09-21
Curious if anyone seeing the old actions menu (r. click on nautilus launcher icon
Seeing here now as long as - 
Nautilus was opened once
The Dash not opened

So then if opening the Dash it returns to the  new no nothing action menu but as soon as nautilus is opened it returns..

---

### Post by ventrical on 2017-09-21
First, New windows/Files/unlock from launcher then open nautilus/ then  your screenshot posted. close nautilus/your screenshot once then New Windows/Files?unlock from launcher.

---

### Post by ventrical on 2017-09-21
> **mc4man said:**
> No, I was referring to unity source & [active branch]("https://code.launchpad.net/%7Eunity-team/unity/trunk/+activereviews") merge requests
Anyway was now able to get unity to build using what i found there in conjunction with a rebuilt compiz-dev.. 
(- it failed one test  so I had to disable it but that test would be likely to fail in a local build (headless x
So that's a positive thing..

Thanks for clarification.

---

### Post by ventrical on 2017-09-21
> **Chanath said:**
> If your team is going to maintain Unity 7 in the future, what all these bug reports going to achieve? Actually, aren't those bugs have to directed to your team, as there are no Unity 7 devs in the company? I don't think one car maker would help the other car maker to make a better car than theirs.

It is good to know they are still doing fixes.

Regards..

---

### Post by mc4man on 2017-09-21
> **ventrical said:**
> First, New windows/Files/unlock from launcher then open nautilus/ then  your screenshot posted. close nautilus/your screenshot once then New Windows/Files?unlock from launcher.
Yeah, seems from a login there are any number of 'triggers' 
Here it can stay awhile though if another window is opened like FF then goes back. Returns on nautilus opening again.

I'd like to find a way for it to stay...

---

### Post by Chanath on 2017-09-21
> **ventrical said:**
> It is good to know they are still doing fixes.

Regards..

Who is doing the fixes? You said there aren't any Unity devs? You mean the Gnome devs are doing the fixes?

---

### Post by ventrical on 2017-09-21
> **Chanath said:**
> Who is doing the fixes? You said there aren't any Unity devs? You mean the Gnome devs are doing the fixes?

I am doing fixes when i am pointed to one. The rest , it's the gnome devs and QA and desktop team - mostly jbicha, didrocks. seb and bregma for now. Don't ask me how they are doing it because I don't know. I think when they have time, they do a fix or assign a bug to someone. So perhaps they are merging upstream hacks   from 16.04  but that doesn't mean it is in development. When I get pointed to a file or bug  I look at the source, see if I can fix, make a commit, changelog and then request a merge. Thats it for now until I hear further from  one of the devs.

regards..

---

### Post by Chanath on 2017-09-21
Excellent!
And, thanks.

If a user sees something and post it here, a bug or something like that, you'd be the first to know. :)

BTW, I've installed unity-session on (practically) Ubuntu base. Checking it out at the moment.

---

### Post by ventrical on 2017-09-21
> **Chanath said:**
> Excellent!
And, thanks.

If a user sees something and post it here, a bug or something like that, you'd be the first to know. :)

BTW, I've installed unity-session on (practically) Ubuntu base. Checking it out at the moment.

It's a community team. I am just a small part volunteer. A lot of work&content done here at ubuntuforums gets shared with the devs so we are providing valuable database of bugs and discussions. Now I have to go and sing for my supper ! :)

Regards..

---

### Post by ventrical on 2017-09-22
> **mc4man said:**
> This would be the current 17.10 unity FTBFS, normally would file a bug  but now..

```
.....
-- Checking for module 'compiz'
--   Found compiz, version 0.9.13.1
-- Checking for module 'compiz-opengl'
--   Found compiz-opengl, version 0.9.13.1
-- GSettings schemas will be installed into /usr/share/glib-2.0/schemas/
-- Checking for module 'compiz-composite'
--   Found compiz-composite, version 0.9.13.1
CMake Error at plugins/unityshell/CMakeLists.txt:1 (find_package):
  By not providing "FindCompiz.cmake" in CMAKE_MODULE_PATH this project has
  asked CMake to find a package configuration file provided by "Compiz", but
  CMake did not find one.

  Could not find a package configuration file provided by "Compiz" with any
  of the following names:

    CompizConfig.cmake
    compiz-config.cmake

  Add the installation prefix of "Compiz" to CMAKE_PREFIX_PATH or set
  "Compiz_DIR" to a directory containing one of the above files.  If "Compiz"
  provides a separate development package or SDK, be sure it has been
  installed.


-- Configuring incomplete, errors occurred!
.. 			 		

```



( it's not from newer gcc/g++ or cmake, last build of the current unity source was on 2017-07-21



@mac4man

> 
That sounds like the user is  missing some build-depends, a new version should land in artful this  week as said and it's building fine
 
 Cheers,
 Sebastien Bacher


---

### Post by mc4man on 2017-09-22
> **ventrical said:**
> @mac4man
I already mentioned in posts after that the initial issue was compiz needed to be rebuilt with current cmake, subsequent errors were solved by picking some commits from the bazaar branches & had successfully rebuilt unity
(also was able to still patch in systray support for apps that either don't have an app indicator or whose app indicator was broken but can also use the systray.
[https://ubuntuforums.org/showthread.php?t=2363847&p=13689243&viewfull=1#post13689243](https://ubuntuforums.org/showthread.php?t=2363847&p=13689243&viewfull=1#post13689243)
[https://ubuntuforums.org/showthread.php?t=2363847&p=13689244&viewfull=1#post13689244](https://ubuntuforums.org/showthread.php?t=2363847&p=13689244&viewfull=1#post13689244)

---

### Post by ventrical on 2017-09-22
> **mc4man said:**
> I already mentioned in posts after that the initial issue was compiz needed to be rebuilt with current cmake, subsequent errors were solved by picking some commits from the bazaar branches & had successfully rebuilt unity
(also was able to still patch in systray support for apps that either don't have an app indicator or whose app indicator was broken but can also use the systray.
[https://ubuntuforums.org/showthread.php?t=2363847&p=13689243&viewfull=1#post13689243](https://ubuntuforums.org/showthread.php?t=2363847&p=13689243&viewfull=1#post13689243)
[https://ubuntuforums.org/showthread.php?t=2363847&p=13689244&viewfull=1#post13689244](https://ubuntuforums.org/showthread.php?t=2363847&p=13689244&viewfull=1#post13689244)

It was a belated reply from sebastien but I thought I would just put it up here anyways.

Thanks for all your help and research on this.

Regards..

---

### Post by Chanath on 2017-09-22
@ventrical & the team
What's actually is your plan on creating an Ubuntu Unity iso?

There are reasons, why Ubuntu Unity would be real success.

---

### Post by ventrical on 2017-09-22
> **Chanath said:**
> @ventrical & the team
What's actually is your plan on creating an Ubuntu Unity iso?

There are reasons, why Ubuntu Unity would be real success.

As you understand, I am not Canonical.  So I am saying that I am following the leads from current desktop team and will continue to test. I would like to take a leap and re-open development to unity9 .  There are currently 100 U+1 members in Ubuntu Development  Forums Testing and several non members who contribute all types of content and helpers and so there is an understanding that  the ubuntu- desktop- team can patch into this thread currently. I have polled the members of U+1 and several are participating , in their own time frames , here at the forum to help test current unity7 along. To make a UUbuntu spin (unity9.IOS) would take a lot of work and I only have 3 members on the team atm for maintainers (and am waiting to see where that goes).

As I understand free software concept, anyone can go ahead and make their own unity7.iso spin. I would guess they would need permission from Canonical as it is proprietary software.? I don't know.  I could most likely put an unity9.iso in a ppa. I would need some how to's and a few helpers. If I get a few helpers and how-tos I could ask Mark if we could do it. (Please note: I am C, Turing. ASICC, BASIC, GWBASIC, QBASIC programmer from way back .. and so I still need some instruction pointers and how tos  on launchpad navigation.) so if you are going to give me launchpad instructions you have to be specific with code, not vague with nomenclature. Then put in into pseudo code or a block diagram flowchart which I am trained to read  better and I can try to build something here.

Regards..

---

### Post by jbicha on 2017-09-22
> **ventrical said:**
> I would guess they would need permission from Canonical as it is proprietary software.?

Unity is open source, generally GPL-3 I believe. If you just want to make your own ISO, my understanding is the only permission you may need from Canonical is for trademark permission depending on what you name the release.

---

### Post by Chanath on 2017-09-22
@ventrical

Too bad that I haven't learned how to code. I'm too old to learn today. There had been lot of Remixes before with Unity, so there would be again. Basic info is here, [https://help.ubuntu.com/community/MakeALiveCD/DVD/BootableFlashFromHarddiskInstall](https://help.ubuntu.com/community/MakeALiveCD/DVD/BootableFlashFromHarddiskInstall) 
Some can be found in remastersys code. But, that's for those, who like to create remixes.

If your team decides to create Ubuntu Unity, it'd still be a success. I think its better done with/in agreement with Cannonical.

---

### Post by ventrical on 2017-09-22
> **jbicha said:**
> Unity is open source, generally GPL-3 I believe. If you just want to make your own ISO, my understanding is the only permission you may need from Canonical is for trademark permission depending on what you name the release.

Thanks Jeremy.

I'm just experimenting with it  atm.  uhh.. the unity9 thing would just be unity with some tweaks and bug fixes for *desktop* only. If unity7 gets pulled during 18.04 (which I hope it does't) then perhaps I can find a way to build it on the next stack. it doesn't have to be official .. but if it meets security requirements..etc.. perhaps it could get slippped back  into the universe if it gets pulled.

Regards..

---

### Post by Chanath on 2017-09-22
Jeremy can help you on how to create the live iso. This was how it first started, [http://ubuntu-gs-remix.sourceforge.net/p/home/](http://ubuntu-gs-remix.sourceforge.net/p/home/)

"Ubuntu Unity is an (un)official remix of the Ubuntu operating system where the Gnome desktop environment is replaced with the Unity desktop environment." Strange how things move in circles.

---

### Post by ventrical on 2017-09-22
> **Chanath said:**
> Jeremy can help you on how to create the live iso. This was how it first started, [http://ubuntu-gs-remix.sourceforge.net/p/home/](http://ubuntu-gs-remix.sourceforge.net/p/home/)

Already started a thread here. [https://ubuntuforums.org/showthread.php?t=2372237](https://ubuntuforums.org/showthread.php?t=2372237)

Searched on my own and found Ubuntu Customization Kit. I know there are others. One day at a time eh :)

regards..

---

### Post by jbicha on 2017-09-22
> **Chanath said:**
> Jeremy can help you on how to create the live iso.

Sorry, I don't use Unity any more and I have enough projects I'm working on.

> **Chanath said:**
> This was how it first started, [http://ubuntu-gs-remix.sourceforge.net/p/home/](http://ubuntu-gs-remix.sourceforge.net/p/home/)


Sorry about the name confusion. That link refers to an earlier project that is unrelated to what became Ubuntu GNOME. Ubuntu GNOME never used Sourceforge and its first [release]("https://ubuntugnome.org/") (as Ubuntu GNOME Remix) was 12.10.

---

### Post by Chanath on 2017-09-22
> **jbicha said:**
> Sorry, I don't use Unity any more and I have enough projects I'm working on.

Sorry about the name confusion. That link refers to an earlier project that is unrelated to what became Ubuntu GNOME. Ubuntu GNOME never used Sourceforge and its first [release]("https://ubuntugnome.org/") (as Ubuntu GNOME Remix) was 12.10.

Looks like its not yours.

EDIT: [https://en.wikipedia.org/wiki/Ubuntu_GNOME](https://en.wikipedia.org/wiki/Ubuntu_GNOME)
[http://ubuntugnome.org/ubuntu-gnome-12-10-released/](http://ubuntugnome.org/ubuntu-gnome-12-10-released/)

---

### Post by ventrical on 2017-09-22
> **Chanath said:**
> Jeremy can help you on how to create the live iso. This was how it first started, [http://ubuntu-gs-remix.sourceforge.net/p/home/](http://ubuntu-gs-remix.sourceforge.net/p/home/)

"Ubuntu Unity is an (un)official remix of the Ubuntu operating system where the Gnome desktop environment is replaced with the Unity desktop environment." Strange how things move in circles.


@Chanath
Jeremy has been a great help already. (as you too) This is community project if we could stay on topic please.

Regards..

---

### Post by mc4man on 2017-09-23
Noticed just before removing all my 17.10 installs (done with 17.10 for now) that in a unity session alt+print doesn't work
Probably something to do with hud

---

### Post by Chanath on 2017-09-24
> **mc4man said:**
> Noticed just before removing all my 17.10 installs (done with 17.10 for now) that in a unity session alt+print doesn't work
Probably something to do with hud

In ventrical's iso it works. In my Unity install it also works. The screeny is from ventrical's live iso in an UEFI laptop.

---

### Post by jbicha on 2017-09-29
Could you submit a merge proposal to have unity-control-center recommend activity-log-manager? (That should provide the Security & Privacy panel.)

---

### Post by ventrical on 2017-09-29
> **jbicha said:**
> Could you submit a merge proposal to have unity-control-center recommend activity-log-manager? (That should provide the Security & Privacy panel.)

Looking at this..

---

### Post by ventrical on 2017-09-29
> **jbicha said:**
> Could you submit a merge proposal to have unity-control-center recommend activity-log-manager? (That should provide the Security & Privacy panel.)

@jbicha

Could you check PM please..

thanks

---

### Post by Chanath on 2017-09-29
> **ventrical said:**
> 

> [IMG]https://ubuntuforums.org/images/ubuntu-VB4/misc/quote_icon.png[/IMG][COLOR=#000000] Originally Posted by [/COLOR]**jbicha**[COLOR=#000000] [/COLOR][URL="https://ubuntuforums.org/showthread.php?p=13691883#post13691883"][IMG]https://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG]
[/URL][COLOR=#000000]*Could you submit a merge proposal to have unity-control-center recommend activity-log-manager? (That should provide the Security & Privacy panel.)*[/COLOR]

Looking at this..

Is there any use of this merging? If everything goes "well" with Gnome as default, all that work (and thoughts) on trying to keep Unity on has any value?

---

### Post by ventrical on 2017-09-29
> **Chanath said:**
> Is there any use of this merging? If everything goes "well" with Gnome as default, all that work (and thoughts) on trying to keep Unity on has any value?

Of course it does have value. I have to take it one day at a time. I am trying to be involved in fixes and this will be important  that unity7 will be in 18.04.  I have to develop some skills in this fix/commit/merge in launchpad.


Regards..

---

### Post by Chanath on 2017-09-29
> **ventrical said:**
> Of course it does have value. I have to take it one day at a time. I am trying to be involved in fixes and this will be important  that unity7 will be in 18.04.  I have to develop some skills in this fix/commit/merge in launchpad.


Regards..

You see, in a team, say football, there is always one captain at a time. The other players vie for the captaincy. Once a new captain is chosen, the former captain always go away. He won't play under the new captain. If he'd play, he'd be a problem to the new captain. The new captain wouldn't won't the earlier captain to stay around, or even advice. 

Likewise, if you are interested in keeping Unity alive, you try to get help from the people, who genuinely use Unity in day to day work. There are people, who create Ubuntu based distros, with XFCE, with LXDE etc. None of them are against Xubuntu or Lubuntu. They love Xubuntu or Lubuntu, so they create those distros. *They don't want to substitute Xubuntu or Lubuntu.* They are genuine people. Sort them out in the net. They'd help you.  

You see, the majority of unity users never had to create Unity based distros. They had a very good distro, so they just used it, or tweaked it. Because of that they may not be of much help. The new default dev team is fully engaged in mimicking Unity. If Unity was not around, they wouldn't have to work on that. They fork a dock, immediately someone out there uploads an extension to disable it. Unity launcher didn't have that trouble. If Unity goes away, it'd be better as no one would compare. No one would remember. 

And, always ask the managing director. Not the branch managers, if you want the company to be interested. If you care to keep Unity on, then you need the backing of the top person. 

Regards!

---

### Post by ventrical on 2017-09-29
Hi Chanath,

 I have communicated with the head "dragon" so to speak on this issue. His slant is that Canonical is not a sacred cow and that Unity+Mir caused too much competition in the bullpen (bullpen is figure of speech for developers). Now that unity8 is no longer a responsibility that Canonical has to maintain, they can direct their resources elsewhere. The Founders and Head Dragon ultimately made this decision. I will reiterate, time and time again, that Head Dragon hopes that Unity7 will be in repos and that  the community will take up the task to maintain it.! Canonical , first and foremost, have to service their paying cutomers - otherwise SABDFL will not have the funds to maintain his generous benevolence as he currently does. So thats about written in stone unless someone has an epiphany to do otherwise (as stranger things have happened with Ubuntu development).

> 

You see, in a team, say football, there is always one captain at a time.  The other players vie for the captaincy. Once a new captain is chosen,  the former captain always go away. He won't play under the new captain.  If he'd play, he'd be a problem to the new captain. The new captain  wouldn't won't the earlier captain to stay around, or even advice. 


Ahhh .. yes.. nature does have a way of leveling out these ironic things that  happen in the hierarchy.  But with the "ubuntu" spirit we know that we all stand on the shoulders of giants and that each of us is equally important from the smallest to the largest. We are governed , in essence, by the sum of our parts. We welcome new captains, new ideas even though they are contrary to own own philosophies and new experience. It is not a mater of being as strong as our weakest link because the chain that binds the ubuntu circle and fortifies it  are it's weakest links! This is the difference in the dog eat dog world and the free open source  world, with the ubuntu philosophy.

 As for the /unity7maintainers.. well ,just because I created  this proposed team does not me it belongs just to me - it belongs to all of us including SABDFL and yourself.  Anyone can be captain. We have a community council and we can vote democratically in elections if you are a member.

> 
And, always ask the managing director. Not the branch managers, if you  want the company to be interested. If you care to keep Unity on, then  you need the backing of the top person. 


Well .. good point, but perhaps the leader of the band is tired and needs to come up for air and do other houskeeping - to survey and make sure that resources are spread equally around so that there is some fairness doctrine throughout the greater realm of things. You have brought up some good points here. I think the community is listening. Perhaps maybe even Canonical is listening..

Regards..

---

### Post by Chanath on 2017-09-30
When i mentioned the "team" I wasn't thinking of the Unity7 maintainers team, but the new "default" team. The resistance to Unity *didn't come from* Lubuntu, Kubuntu or Xubuntu users, but from few unhappy, but vociferous Gnome users. Gnome 2 didn't move to Gnome 3 in Ubuntu, but to a new animal Unity. Now that Gnome 3 is back, most of them comment on the net that they are happy that Unity is gone (or going). *If they got what they want, why should they?* Anyway, there are quite a lot of Unity users, who want to Unity to stay. And, some of them are showing enmity toward Gnome; the trend is rising. 

When I said, 17.10 default is an experiment, some were adamant that its not. The mimicking Unity shows exactly that. One mimics something, when one cannot achieve the original (I've read this term in the net). In a way, the new default has to look like Unity shows that Unity is not out of interest of the head dragon. I would've kept on using my Openbox install (or Xubuntu), if not for the feeling that Unity would be gone. Too bad that I didn't learn to code. I don't know how to create or maintain app package. But, I know how to create a live iso -- learned from discussions with Fragedelic, when he had the the forum and by reading the code (something I can do). 

Anyway, Unity is not just a DE, but a way of life. It is what made Ubuntu what it is today. Gnome 3 wouldn't do that. I am not a naysayer, but that what would be. There appears to be about 15% Ubuntu users are still interested in Gnome 3 and going down. Again, I read it somewhere in the net.

If your team can bring Unity back to life, there'd be lot of happy people, not only the free users, but also the paying users.

---

### Post by ventrical on 2017-09-30
> **Chanath said:**
> When i mentioned the "team" I wasn't thinking of the Unity7 maintainers team, but the new "default" team. The resistance to Unity *didn't come from* Lubuntu, Kubuntu or Xubuntu users, but from few unhappy, but vociferous Gnome users. Gnome 2 didn't move to Gnome 3 in Ubuntu, but to a new animal Unity. Now that Gnome 3 is back, most of them comment on the net that they are happy that Unity is gone (or going). *If they got what they want, why should they?* Anyway, there are quite a lot of Unity users, who want to Unity to stay. And, some of them are showing enmity toward Gnome; the trend is rising. 


Yes.. I was using myself as an example:) A greater percentage of persons that are involved with ubuntu, in most any aspect, are volunteers. That means there is a fluctuation of support at any time. It is very fluid and supporters may contribute a greater effort one day and then suddenly abandon a project. (the wikis are a good example of how the knowledge base can become fragmented) so many times we can say - "to each their own". Thing is , most oftentimes, someone will come in and pull up the slack. Ubuntu is a community based project and so lots of maintenance comes from the community of voluntary laborers.  The 'vociferous Gnome users' you speak of were , more or less, a large part of the Ubuntu community that felt it was being left out and that unity8 and convergence was drawing most of the development resources from salaried developers which are essential in keeping  and maintaining  the security and excellence of the whole of the ubuntu software infrastructure which , without, it would eventually be a very bad experience for most everybody. The bottom line could be , as I had wrote on this before, is that the unity concept presented an exclusivity rather than an alternative. In a  commercial model this makes perfect sense but ubuntu is not a commercial product, it is a free and open source product. We have to come to grips with the demarcation line being presented here. To analyze it  only causes more enmity betwixt the present resources available. This kind of lack of harmony certainly misrepresents any kind of unity within the community. However, I think your comments have a lot of merit and these will be proved out during the next cycle. Ubuntuforums will be the place to watch.  We can meter interest in gnome and unity by observing the persons who are testing it most. We can ask, "Is default ubuntu being tested by QA Canonical testers to a larger degree or are volunteer testers taking up the task in a greater portion."? Now there are 'members'  (like myself for instance) that like to follow a smooth flowchart (stay with me on this for a moment).  I have to look at the larger picture and deem it wiser to be part of the solution rather than part of the problem.  I cannot allow myself to get too bottled up on hypotheticals . If it turns out that the current design of the default flowchart choosen to be the wrong path, then so be it. The community at large will have spoken by refraining their efforts in testing the default stack and so this will greatly diminish the QA of that production cycle. However, we cannot allow ourselves to dwell on these negatives.  Well . .speaking for myself, I have to keep on and be positive 

> 
When I said, 17.10 default is an experiment, some were adamant that its  not. The mimicking Unity shows exactly that. One mimics something, when  one cannot achieve the original (I've read this term in the net). In a  way, the new default has to look like Unity shows that Unity is not out  of interest of the head dragon. I would've kept on using my Openbox  install (or Xubuntu), if not for the feeling that Unity would be gone.  Too bad that I didn't learn to code. I don't know how to create or  maintain app package. But, I know how to create a live iso -- learned  from discussions with Fragedelic, when he had the the forum and by  reading the code (something I can do). 

Anyway, Unity is not just a DE, but a way of life. It is what made  Ubuntu what it is today. Gnome 3 wouldn't do that. I am not a naysayer,  but that what would be. There appears to be about 15% Ubuntu users are  still interested in Gnome 3 and going down. Again, I read it somewhere  in the net.


Gnome is not an experiment. I have to disagree with you. Gnome has been around a lot longer than unity, but this in not the point really. I think you have some very valid points though. ummm .. how can I put it .. uh .. we sort of have to have some trust that the directors in the desktop team are doing all of this for the greater good of things. We can be rest assured that if gnome3 becomes extremely buggy and difficult to learn and handle by average end_users then we can be assured that the appropriate actions will be taken to remedy that. Now I know you are a good tester and excellent researcher and so , as admin of U+1, I continue to invite you to keep testing the new default experience and at least see where it goes to the end of the next cycle. All of our efforts combined , or lack of,  could make or break the success of the next cycle. Think about that.

Regards..

---

### Post by ventrical on 2017-09-30
> **Chanath said:**
> 
If your team can bring Unity back to life, there'd be lot of happy people, not only the free users, but also the paying users.

It's not my team. It's "our" team.

Some of the developers are trying to train and assist me in learning the launchpad techniques for commits and merge requests. So y'all have to help me stay focused :)

Regards..

---

### Post by mc4man on 2017-09-30
Seems the Dash no longer shows any recent for applications, as far as files & folder only ones that have been moved, not opened.
To really see use a new install though in current installs nothing new will be added.
(- nothing about the new compiz & unity builds just released will change this

---

### Post by ventrical on 2017-09-30
> **mc4man said:**
> Seems the Dash no longer shows any recent for applications, as far as files & folder only ones that have been moved, not opened.
To really see use a new install though in current installs nothing new will be added.
(- nothing about the new compiz & unity builds just released will change this

Wasn't zeitgiest running this?  I thought it was disabled by default.

edit:
Oddly I have installs that remember (Dash) and others that don't.

---

### Post by mc4man on 2017-09-30
> **ventrical said:**
> Wasn't zeitgiest running this?  I thought it was disabled by default.

edit:
Oddly I have installs that remember (Dash) and others that don't.
Well the ones that remember may just be using 'old' info. See if anything new is added, ex. open a file in gedit, then ck. the Dash > File & Folders, should be 1st. listed.

What I see is that only transfered files will be added, ex. copy & paste a file..

---

### Post by rrnbtter on 2017-09-30
Greetings,
It seems to me that the dropping of Unity as a desktop was not so much a desktop issue but a display server issue. Canonical was dropping Unity 7 anyway, aiming for Unity 8 and Mir. The object is to abandon X.  Since they could not get Unity8/Mir off the launchpad the course switched to Gnome3 and Wayland. As previously noted, Unity7 has had no development for quite a few generations. 
The current state is that Unity can barely function as a "pure Unity" since there is too much embedded Gnome Wayland. Hence the various behaviors of Dash. In one instance it behaves like native Dash and the next instance it behaves like the Gnome Search. I'm not experienced in the flavors but it seems to me that if one wanted to patch in Unity it would make sense to start with Xubuntu or some other version not so much linked to Gnome/Wayland. 
Also, and I struggling to be kind about this. If it was important for Unity to be available in 18.02 then Canonical would be working to put it there. I was long mesmerized and delighted with the Unity Desktop. It was a great run. But I also know that the only thing that stays the same is everything changes. 
Best of luck to you all but I think Wayland makes it (Unity) a deal breaker.  Gulp!

---

### Post by ventrical on 2017-09-30
> **mc4man said:**
> Well the ones that remember may just be using 'old' info. See if anything new is added, ex. open a file in gedit, then ck. the Dash > File & Folders, should be 1st. listed.

What I see is that only transfered files will be added, ex. copy & paste a file..

I get this..

---

### Post by ventrical on 2017-09-30
@mac4man

The one that has recall has the zietgiest-datahub. The one that does not have recall does not have the datahub active.

---

### Post by ventrical on 2017-09-30
> **rrnbtter said:**
> Greetings,
It seems to me that the dropping of Unity as a desktop was not so much a desktop issue but a display server issue. Canonical was dropping Unity 7 anyway, aiming for Unity 8 and Mir. The object is to abandon X.  Since they could not get Unity8/Mir off the launchpad the course switched to Gnome3 and Wayland. As previously noted, Unity7 has had no development for quite a few generations. 
The current state is that Unity can barely function as a "pure Unity" since there is too much embedded Gnome Wayland. Hence the various behaviors of Dash. In one instance it behaves like native Dash and the next instance it behaves like the Gnome Search. I'm not experienced in the flavors but it seems to me that if one wanted to patch in Unity it would make sense to start with Xubuntu or some other version not so much linked to Gnome/Wayland. 
Also, and I struggling to be kind about this. If it was important for Unity to be available in 18.02 then Canonical would be working to put it there. I was long mesmerized and delighted with the Unity Desktop. It was a great run. But I also know that the only thing that stays the same is everything changes. 
Best of luck to you all but I think Wayland makes it (Unity) a deal breaker.  Gulp!


@rrnbtter

:) No gulp . It is what it is.  A lot of people in the community, in the pool of working volunteers, feel a deep sense
 of abandonment. We worked really hard to make this work and when they pulled it without telling the community or asking the other parts of the community what we thought, well.. it was like being thrown under the bus, so there is a lot of disharmony  that was sowed by that decision. I think that eventually  a lot of people will get over it. By 18.04 release we will have a better view of it all.

As always .. thanks for your most valued input.

Regards..

---

### Post by mc4man on 2017-09-30
> **ventrical said:**
> @mac4man

The one that has recall has the zietgiest-datahub. The one that does not have recall does not have the datahub active.
I'm referring to the Application and Files &Folders scopes, do you get updated "Recent"(ly) there?

screens from 16.04

---

### Post by ventrical on 2017-09-30
> **mc4man said:**
> I'm referring to the Application and Files &Folders scopes, do you get updated "Recent"(ly) there?

screens from 16.04

yep .. certainly did update .. but there is a bug in the apps window. You have to open a non used recent app for it to kick in and also you have to click the dash button to clear the dash. Once it is kicked in by the new app , it will remember.. I used gimp as I hadn't used it since last boot.

---

### Post by ventrical on 2017-09-30
> **rrnbtter said:**
> Greetings,
It seems to me that the dropping of Unity as a desktop was not so much a desktop issue but a display server issue. Best of luck to you all but I think Wayland makes it (Unity) a deal breaker.  Gulp!

Just my opinion .. I don't think it was an X issue. Unity7 is a great RSI  and eye-strain reducer. We'll miss it when it's gone.

Regards..

---

### Post by mc4man on 2017-09-30
> **ventrical said:**
> yep .. certainly did update .. but there is a bug in the apps window. You have to open a non used recent app for it to kick in and also you have to click the dash button to clear the dash. Once it is kicked in by the new app , it will remember.. I used gimp as I hadn't used it since last boot.
I'll recheck in 17.10..

For curiosity just tried in a new 17.04 install. There no new additions to the File & Folders > Recent for any files opened in Home dir. Files opened from elsewhere show up.
For the Applications > Recently opened nothing unless opened from outside of $HOME, like going to /usr/share/applications & opening something.
So something started breaking down in this regard in 17.04..

---

### Post by ventrical on 2017-09-30
> **mc4man said:**
> I'll recheck in 17.10..

For curiosity just tried in a new 17.04 install. There no new additions to the File & Folders > Recent for any files opened in Home dir. Files opened from elsewhere show up.
For the Applications > Recently opened nothing unless opened from outside of $HOME, like going to /usr/share/applications & opening something.
So something started breaking down in this regard in 17.04..

Actually I am working on the unity-control-center file and edited in recommend 'activity-log-manager' which will bring up Privacy&Security pop as thats where zeitgiest is controlled from. *If you go to settings* in 17.10 you will not see P&S icon in the panel.

---

### Post by ventrical on 2017-09-30
@mac4man

Actually..
```


sudo apt-get install activity-log-manager

```

will put the security and privacy app in settings but it will not pull in zeitgiest-datahub which means it is still not working on some installs. I have several installs on different boxes. The two installs I mention here are from USB isos and not upgrades from 17.04

---

### Post by rrnbtter on 2017-09-30
Greetings,

> **ventrical said:**
> Just my opinion .. I don't think it was an X issue. Regards..

Well, in 17.10 default Ubuntu  Gnome and Wayland has been added and X is gone. To run an X11 app, X has to be called from Xwayland. No xwayland, no x11 app.  I think that to get Unity running properly one has to root out Gnome/Wayland/GDM and get back to X and lighdm since that is what Unity7 is natively ported to. Otherwise some undesirable Gnome traits will bleed over to Unity. Like the Dash recall problem. Gnome doesn't currently recall what has not been previously opened. I personally don't know enough about the methods of Zeitgeist to say what the problem might be with Dash but if it waddles like a Gnome and it quacks like a Gnome then it's a Gnome.  Dig into that Gnome hole and root that bugger out and Dash will behave like it is suppose to.

---

### Post by Chanath on 2017-09-30
I suppose, we are talking about Unity 7, not Unity 8 or Xmir. So, not Wayland or Xwayland.
Unity 7 lives well with Xorg, and Xorg is not going anywhere. So, even trying to test it with Wayland or Xwayland is useless. It should be just Unity, and without Gnome, without Xwayland. ***If you want Unity, you only concentrate on Unity. ***There's no either this or that.


(2nd part: About 17.10 default being an experiment. Gnome 3 might have been out there for a long time, but not with Ubuntu. Ubuntu moved to Unity straight from Gnome 2, and it was Unity that made Ubuntu known to practically everyone in the world. They have even heard about Unity, but...)

---

### Post by mc4man on 2017-09-30
So it was working (I had already installed relevant packages
What it was for files & folders, -  because it was a new, unpopulated install the most handy files to open (text) where either [COLOR="#FF0000"].[/COLOR] files or files in a [COLOR="#FF0000"].[/COLOR]folder.
I had forgotten such files don't ever show anyway...

As far as apps - I never use that feature as it's limited to last 6 & everything I would use would in in the launcher. That still seems a little sketchy, many apps show, some don't.  (new install from Ubuntu iso - seems better now..

---

### Post by ventrical on 2017-09-30
> **rrnbtter said:**
> Greetings,



Well, in 17.10 default Ubuntu  Gnome and Wayland has been added and X is gone. To run an X11 app, X has to be called from Xwayland. No xwayland, no x11 app.  I think that to get Unity running properly one has to root out Gnome/Wayland/GDM and get back to X and lighdm since that is what Unity7 is natively ported to. Otherwise some undesirable Gnome traits will bleed over to Unity. Like the Dash recall problem. Gnome doesn't currently recall what has not been previously opened. I personally don't know enough about the methods of Zeitgeist to say what the problem might be with Dash but if it waddles like a Gnome and it quacks like a Gnome then it's a Gnome.  Dig into that Gnome hole and root that bugger out and Dash will behave like it is suppose to.

Good write up here. I hope our team has a chance to  get to this. I'm trying to hone some launchpad skills. Got a prob with nano etc.. but I'm working on it. :)

thanks ! 

regards..

---

### Post by ventrical on 2017-09-30
> **Chanath said:**
> I suppose, we are talking about Unity 7, not Unity 8 or Xmir.

Yes.


> 
 So, not Wayland or Xwayland.
Unity 7 lives well with Xorg, and Xorg is not going anywhere. So, even trying to test it with Wayland or Xwayland is useless. It should be just Unity, and without Gnome, without Xwayland. ***If you want Unity, you only concentrate on Unity. ***There's no either this or that.


This may eventually have to be the staple rip if unity7 is in 18.04 repos because there is a lot of maintenance and the team will need lots of help.

regards..

---

### Post by rrnbtter on 2017-09-30
Greetings,
> **Chanath said:**
>  So, even trying to test it with Wayland or Xwayland is useless.

Test it yes, useless.  But with a lot of professional work it could be ported to Wayland and it that case X still gets left behind. Remember to keep your eye on the ball. The object should be to save Unity7 and not so much X. If it is ported it will drop-in on top of Ubuntu default. 

> **Chanath said:**
>  About 17.10 default being an experiment. Gnome 3 might have been out there for a long time, but not with Ubuntu. Ubuntu moved to Unity straight from Gnome 2, and it was Unity that made Ubuntu known to practically everyone in the world. They have even heard about Unity, but...)

In their effort toward convergence and a lot of energy given to Unity8/Mir Unity7 became patched and messy. Hence the stall in development of Unity7.  They wanted a top notch pure smooth OS and went with a modern new platform of Gnome/Wayland/GDM. I don't see a reason in the world not to continue with a Unity7 desktop if the demand is there but it can't be run as a drop-in on Ubuntu 17.10 without some magic.  But magic means sleigh of hand, delusion, not real Unity, just a look alike running on top of a disabled Gnome. 
So yes, I think to test Unity properly the start point can't be 17.10 default. It will be messy and just what Canonical is trying to avoid. 

The other thing is the continued development Unity7 to keep up with the changes of GTK, Python, etc. These libraries which make the OS functional are being updated every day while Unity7 desktop has been left behind, In my opinion there is more work here than mere packaging. 

The reason I say good luck to you and the rest on this matter is not that I wouldn't like to see a continued Unity desktop, It is because I'm an old geezer and don't have the energy for it all.

---

### Post by ventrical on 2017-09-30
> **rrnbtter said:**
> Greetings,
The reason I say good luck to you and the rest on this matter is not that I wouldn't like to see a continued Unity desktop, It is because I'm an old geezer and don't have the energy for it all.

Another good write up. :) started with olde IBM cash registers, then, game mechs on pinballs machines , filing contact points, etc.. then.. :) so I just can't  leave it alone. :) wired to lunity now I guess :)

Regards..

---

### Post by mc4man on 2017-09-30
> **rrnbtter said:**
> Greetings,



Well, in 17.10 default Ubuntu  Gnome and Wayland has been added and X is gone. To run an X11 app, X has to be called from Xwayland. No xwayland, no x11 app.  I think that to get Unity running properly one has to root out Gnome/Wayland/GDM and get back to X and lighdm since that is what Unity7 is natively ported to. .
One can run a unity session that's just been added to the Ubuntu install (gdm3), by & large it's ok. Biggest 'issue' I see is moving windows is a little strange, i.e. the window stays behind till you drop it (screen.
Clearly it's better on lightdm and  by & large a ubuntu session (wayland) or a ubuntu xorg session work ok with lightdm. Atm I'd pick lightdm over gdm3 as *currently* it shows less bugs. Though again if using gnome-shell one might as well use gdm3. (- unless using nvidia drivers via nvidia-prime & getting sick of the shutdown issues.

---

### Post by Chanath on 2017-10-01
> **rrnbtter said:**
> Greetings,

Test it yes, useless.  But with a lot of professional work it could be ported to Wayland and it that case X still gets left behind. Remember to keep your eye on the ball. The object should be to save Unity7 and not so much X. If it is ported it will drop-in on top of Ubuntu default. 

No one has to worry about saving X, for its still there and cannot be rid of, for its an "old geezer." Wayland had been here since 2008 and still not really fully usable on its own. Gnome 3 doesn't work well with Xorg -- jerky window movements etc. The jerky movements are still on so-called Xwayland. Gnome shell is good enough as DE, as far as you keep the "Dash" to 95% of its height--considering one might install Hide Top Bar extension. You can see how ugly Ubuntu Dock would look, if that extension is installed. [https://ubuntuforums.org/showthread.php?t=2372771&page=2#13](https://ubuntuforums.org/showthread.php?t=2372771&page=2#13) Whoever used Gnome before know about extensions and who would be doing it now, would find out about them. *No way to prohibit the new users from using extensions.* Once they do, they'd be clamouring "bug!" 

>  I don't see a reason in the world not to continue with a Unity7 desktop if the demand is there but it can't be run as a drop-in on Ubuntu 17.10 without some magic.  But magic means sleigh of hand, delusion, not real Unity, just a look alike running on top of a disabled Gnome. So yes, I think to test Unity properly the start point can't be 17.10 default. It will be messy and just what Canonical is trying to avoid. 

Between the time Ubuntu 17.10 is released and for the 18.04 to be, we'd see how it goes. If Distrowatch is any point of reference, Ubuntu is now in 4th place in the hit ranking list. The Ubuntu-Gnome is at 54th place. Lubuntu is at 21st, Ubuntu-Mate is at 26th, Ubuntu-Budgie is at 35th and Xubuntu is at 36th. One can see how popular Gnome is...

Ubuntu in that means Ubuntu with Unity...

---

### Post by ventrical on 2017-10-01
> **Chanath said:**
> 
Between the time Ubuntu 17.10 is released and for the 18.04 to be, we'd see how it goes. If it is any point of reference, if you look at Distrowatch, Ubuntu is now in 4th place in the hit ranking list. The Ubuntu-Gnome is at 54th place. Lubuntu is at 21st, Ubuntu-Mate is at 26th, Ubuntu-Budgie is at 35th and Xubuntu is at 36th. One can see how popular Gnome is...

Ubuntu in that means Ubuntu with Unity...

Well I did my 3rd commit/merge which was approved on debian/control file in unity-control-center and a couple of the devs have been extremely helpful. We'll see how it goes.  Yes. Things are looking good. I did a lot of experimenting on weston/wayland in the early days. I have some ideas I could propose. 

Regards..

---

### Post by jbicha on 2017-10-01
Here's another task to fix the zeitgeist issue mc4man mentioned (at least I think it helps; I don't use Unity on 17.10.)

Have unity-session recommend zeitgeist-datahub.

unity-session currently comes from the gnome-session source package. (My opinion is that it ought to be in the unity source package but that won't happen for 17.10).
gnome-session does not use Bileto but is currently maintained by the Ubuntu Desktop team in bzr.

[lp:~ubuntu-desktop/gnome-session/ubuntu]("https://code.launchpad.net/~ubuntu-desktop/gnome-session/ubuntu")

You'll need to update both debian/control.in and debian/control

---

### Post by ventrical on 2017-10-01
> **jbicha said:**
> Here's another task to fix the zeitgeist issue mc4man mentioned (at least I think it helps; I don't use Unity on 17.10.)

Have unity-session recommend zeitgeist-datahub.

unity-session currently comes from the gnome-session source package. (My opinion is that it ought to be in the unity source package but that won't happen for 17.10).
gnome-session does not use Bileto but is currently maintained by the Ubuntu Desktop team in bzr.

[lp:~ubuntu-desktop/gnome-session/ubuntu]("https://code.launchpad.net/~ubuntu-desktop/gnome-session/ubuntu")

You'll need to update both debian/control.in and debian/control

@jbicha

So which branch ??

```

bzr branch lp: ??

```

Thanks 

Regards..

---

### Post by jbicha on 2017-10-01
@ventrical I linked it for you in my original post (#231)

---

### Post by ventrical on 2017-10-01
> **jbicha said:**
> @ventrical I linked it for you in my original post (#231)

I was finally able to get that directory and make changes but now I can't push it. I tried several different ways but get errors. This link is not like  typing in the syntax:
unity-control-center/<name_of_branch>. I typed it in as link suggest but still get errors. So I am currently using the following method:

> 
The steps would be basically
$ bzr branch lp:unity-control-center
$ cd unity-control-center
$ editor debian/rules

do your changes

$ dch -i

write your changelog entry

$ bzr commit
$ bzr push lp:~<USER_ID>/unity-control-center/<BRANCH_NAME>

where USER_ID is your launchpad user id and BRANCH_NAME a name for your work
$ bzr lp-open

and do the merge proposal from the UI


Now the above works but if you notice the link you sent me  has :
```

lp:~/ubuntu-desktop/gnome-session/ubuntu

```

and so when I try to use the first method the (lp:~) seems to conflict because then I can't enter my username which requires (lp:~<user_id>)

I am using straight terminal.  I would rather use the first method that Seb sent up to me before  I use another advanced message.. so .. hope I am not causing extra work for you .. but at this point .. you have to spell it out for me :) 

So  I have changelog/commit ready to go ..just need the package (ie- like 'unity-control-center' in the first example to push it up.)

Thanks !

Regards..

---

### Post by jbicha on 2017-10-01
I suggest something like

```

bzr push lp:~/gnome-session/unity-recommend-zeitgeist

```

Git might be a bit easier to work with. Maybe next cycle we'll switch (it makes sense for Debian GNOME to switch to git first).

---

### Post by ventrical on 2017-10-01
> **jbicha said:**
> I suggest something like

```

bzr push lp:~/gnome-session/unity-recommend-zeitgeist

```

Git might be a bit easier to work with. Maybe next cycle we'll switch (it makes sense for Debian GNOME to switch to git first).

Hey .. thanks !

 I can perhaps try Git later but would rather use the current method of data editing/commit/mergerequest.

I did:

```

bzr lp-open

```

but don't get the  new /unity-recommend-zeitgeist branch.

```

ventrical@ventrical-MS-7798:~/ubuntu$ bzr push lp:~/gnome-session/unity-recommend-zeitgeist
Using default stacking branch /+branch-id/422566 at chroot-139710673744016:///~dale-f-beaudoin/gnome-session/
Created new stacked branch referring to /+branch-id/422566.                    
ventrical@ventrical-MS-7798:~/ubuntu$ bzr lp-open
Opening https://code.launchpad.net/~ubuntu-desktop/gnome-session/ubuntu/ in web browser
ventrical@ventrical-MS-7798:~/ubuntu$ 

```


regards..

---

### Post by ventrical on 2017-10-01
Noticed this:

```

Created new stacked branch referring to /+branch-id/422566.

```

so is there a way to just jump to that branch?

edit:

yes .. just put in my user ID. :)

[https://code.launchpad.net/~dale-f-beaudoin/gnome-session/unity-recommend-zeitgeist/+merge/331631](https://code.launchpad.net/~dale-f-beaudoin/gnome-session/unity-recommend-zeitgeist/+merge/331631)



Regards..

---

### Post by mc4man on 2017-10-01
I still can't figure what triggers this and how to either have all the time or never.
What i see here;
1. On a fresh boot or logout/in an immediate r. click check on icon returns the default minimal action menu
2. Opening a nautilus window directly after logging in still shows minimal action menu. If doing this then at some point the extended one will show up. Could just be time-base but it will show..
3. However if after logging in I wait 10 sec before doing anything then opening a nautilus window produces the extended menu
4. Once the extended menu shows it will stay showing in the icon action window (r. click) as long as a nautilus window is open
5. Once the extended menu shows, after closing any nautilus windows it will still show for about 10 secs when checking the action menu, after 10 sec it goes back to the default minimal until a nautilus window is opened.

Pretty odd as it seems there is something that takes a bit to happen on login (about 10 sec) & something that stays active for about 10 sec after nautilus windows are closed.

---

### Post by Chanath on 2017-10-02
Interesting how Nautilus is behaving...
But with Thunar, it works as should be. 
So, maybe we'd just let Gnome use Nautilus...and, maybe we'd use Thunar. Thunar is lighter than Nautilus, after all...

---

### Post by Chanath on 2017-10-02
Actually, what has Nautilus to do with Unity (or Ubuntu as it was)?

Edit: Purged Nautilus, Gnome-Software, Rhythmbox, Totem and installed VLC instead. Thunar was already installed. Now, Unity is much more useful.

---

### Post by ventrical on 2017-10-02
> **Chanath said:**
> Actually, what has Nautilus to do with Unity (or Ubuntu as it was)?

Edit: Purged Nautilus, Gnome-Software, Rhythmbox, Totem and installed VLC instead. Thunar was already installed. Now, Unity is much more useful.

How about pcmanfm.

---

### Post by Chanath on 2017-10-02
> **ventrical said:**
> How about pcmanfm.

Oh, yes!
 PCmanFM is a real gem!
Thunar too. :)

---

### Post by mc4man on 2017-10-02
> **Chanath said:**
> Actually, what has Nautilus to do with Unity (or Ubuntu as it was)?

Edit: Purged Nautilus, Gnome-Software, Rhythmbox, Totem and installed VLC instead. Thunar was already installed. Now, Unity is much more useful.
Maybe the fact that it is the default supplied file-manager & integrates better with Ubuntu.

---

### Post by Chanath on 2017-10-02
Also uninstalled "Disks" and installed Gparted.
Gnome guys are naming their apps in such a way, so a user won't know how they are really named. Disks is gnome-disk-utility, Videos is Totem and so on. 
apt-cache search disks or apt-cache search videos won't find anything. 
You can write sudo apt purge videos disks, but it won't do anything. 
What they are actually achieving is the purge of the users.

---

### Post by ventrical on 2017-10-02
> **Chanath said:**
> Also uninstalled "Disks" and installed Gparted.
Gnome guys are naming their apps in such a way, so a user won't know how they are really named. Disks is gnome-disk-utility, Videos is Totem and so on. 


Well I am not totally sure it was gnome-devs but this kind of behavior was going on during unity8+mir +libertine+xapps!! I had to go back to  14.04 trusty to get the right name of the gnome apps , games etc  to get them working (legacy) but for 17.04 all those apps names were changed so it was a real chaos. I had unity8 and libertine and xmir working just great. I could run 4 concurrent games of 3d dream chess and other games in background without a flinch. Then , all of a sudden, one day , after an update and it was broken.

Looks like you have found ways to streamline your unity install. Ubuntu , across all flavors. is so versatile.

Regards..

---

### Post by mc4man on 2017-10-02
> **Chanath said:**
> Also uninstalled "Disks" and installed Gparted.
Gnome guys are naming their apps in such a way, so a user won't know how they are really named. Disks is gnome-disk-utility, Videos is Totem and so on. 
.
That's nothing new, has been going on forever. Users see whatever the Name= line in the .desktop says. Many times that isn't the source or package name.

---

### Post by jbicha on 2017-10-02
> **Chanath said:**
> 
Gnome guys are naming their apps in such a way, so a user won't know how they are really named. Disks is gnome-disk-utility, Videos is Totem and so on. 
apt-cache search disks or apt-cache search videos won't find anything. 


The GNOME Disks and Videos apps are part of a complete GNOME system. The way you're supposed to uninstall them is via the GNOME Software app. It's as easy as clicking buttons; you don't have to worry about terminals and remembering the right syntax and package names.

But I don't expect most normal users would want to uninstall those apps anyway.

---

### Post by ventrical on 2017-10-03
> **jbicha said:**
> The GNOME Disks and Videos apps are part of a complete GNOME system. The way you're supposed to uninstall them is via the GNOME Software app. It's as easy as clicking buttons; you don't have to worry about terminals and remembering the right syntax and package names.

But I don't expect most normal users would want to uninstall those apps anyway.

Well, for testers, certainly not disks, as we here in U+1 use 'disks' <restore> as the approved method of creating/testing  bootable USBs from ubuntu  flavored  ISOs.

Regards..

---

### Post by Chanath on 2017-10-03
> **jbicha said:**
> The GNOME Disks and Videos apps are part of a complete GNOME system. The way you're supposed to uninstall them is via the GNOME Software app. It's as easy as clicking buttons; you don't have to worry about terminals and remembering the right syntax and package names.

But I don't expect most normal users would want to uninstall those apps anyway.

Actually, a normal Linux user would (or should) try the terminal. I suppose, there is a certain difference between "normal Linux users" and "normal users." 
If the idea of the Gnome devs to pull in normal click, click users from the Windows world, it maybe okay.:)

---

### Post by Chanath on 2017-10-03
If you want the file manager to look like (good old) Nautilus, you can always install Nemo or Caja.
The screenshot is with Nemo.

---

### Post by jbicha on 2017-10-03
> **Chanath said:**
> Actually, a normal Linux user would (or should) try the terminal. I suppose, there is a certain difference between "normal Linux users" and "normal users." 


GNOME (and Ubuntu) provides an easy way to uninstall apps. If you want to do things the hard way, then why are you complaining that it's too hard? ;)

---

### Post by ventrical on 2017-10-03
> **serumthiennhien said:**
> [COLOR=#000000]Greetings,[/COLOR]
[COLOR=#000000]Unity has been about "convergence" from the very start. The idea was to have the relative same desktop on pc, phone, and tablet. What failed here was not the Unity Desktop, it was the complete inability to crack the Android market share of phones and tablets. Android is so embedded that Apple and MS themselves have a dismal impact. So Unity as a concept was dropped by Canonical to allow resources to go to IOT and Cloud. It's that simple. The Unity Desktop was about the "Unity" of gadgets and that idea failed not so much the desktop it's self. Gnome Shell and Wayland is a very good drop-in replacement and any deficiencies it may have are rapidly being corrected. I find that to be obvious from my day to day usage over the current dev cycle. Ubuntu as a brand should be just fine especially since they (Canonical) think that they are really an IOT and Cloud/Server company. At least that is where their aspirations seem to be based on their statement at the end of the last cycle regarding dropping Unity for desktop.[/COLOR]

But most users of unity7 PC desktop can live without phones and tablets that do not have unity on them. I mean we are not going to stop riding our horses just because we have trains , planes and automobiles! Gizzmos and gadgets are as gizzmos and gadgets do but unity7 is as unity7 does:) so why ruin a good thing?:) A large percentage of Unity users were linux enthusiasts and it brought a lot of users into the fold where they really liked testing ubuntu. Unity made it EASY. It is a catalyst of sorts. Android, Apple and Microsoft are no comparison to the speed , ease of use and wide spectrum of hardware usable formfactors that unity showcased.

Regards..

---

### Post by ventrical on 2017-10-03
One of the devs sent me these:

[https://plus.google.com/+PopescuSorin/posts/c2c7CXH1Gvg](https://plus.google.com/+PopescuSorin/posts/c2c7CXH1Gvg)

[https://plus.google.com/+PopescuSorin/posts/Zxvh2Xw2Jry](https://plus.google.com/+PopescuSorin/posts/Zxvh2Xw2Jry)

Regards..

edit:

Please ignore the unity haters :)

---

### Post by Chanath on 2017-10-03
> **jbicha said:**
> GNOME (and Ubuntu) provides an easy way to uninstall apps. If you want to do things the hard way, then why are you complaining that it's too hard? ;)

Complaining?!
Ever heard me complaining about anything? 
Ubuntu provides and easy way...Of course!
But, Gnome 3...

If using the terminal is the hard way, we are not really Linux users...

---

### Post by mc4man on 2017-10-03
> **ventrical said:**
> One of the devs sent me these:

[https://plus.google.com/+PopescuSorin/posts/c2c7CXH1Gvg](https://plus.google.com/+PopescuSorin/posts/c2c7CXH1Gvg)

[https://plus.google.com/+PopescuSorin/posts/Zxvh2Xw2Jry](https://plus.google.com/+PopescuSorin/posts/Zxvh2Xw2Jry)

Regards..

edit:

Please ignore the unity haters :)
The nocsd is maybe good if one also disabled global menus, at least for nautilus. Otherwise it looks a little clunky for little gain. Myself have gotten used to the global menus & prefer them..

---

### Post by ventrical on 2017-10-03
> **Chanath said:**
> Complaining?!
Ever heard me complaining about anything? 
Ubuntu provides and easy way...Of course!
But, Gnome 3...

If using the terminal is the hard way, we are not really Linux users...

@Chanath,

 But you have to see it from the perspective or recruiting new converts. I have helped a lot of noobs migrate to Ubuntu and when they see the prospect of working in the terminal they would quickly rather have Windows and Anti-malware removal programs hijacking their systems. This is about outreach to new converts , not just about seasoned testers.

Regards..

---

### Post by ventrical on 2017-10-03
> **mc4man said:**
> The nocsd is maybe good if one also disabled global menus, at least for nautilus. Otherwise it looks a little clunky for little gain. Myself have gotten used to the global menus & prefer them..

The dev was actually commenting positively on the progress we are making with unity7 here in the thread. They are linked in at Canonical to this thread.

Regards..

---

### Post by ventrical on 2017-10-03
> **Chanath said:**
> Complaining?!
Ever heard me complaining about anything? 
Ubuntu provides and easy way...Of course!
But, Gnome 3...

If using the terminal is the hard way, we are not really Linux users...

@Chanath,

Gnome3 .. unity7... ?? We are all family here... :)

Regards..

---

### Post by Chanath on 2017-10-03
> **ventrical said:**
> unity7 is as unity7 does:) so why ruin a good thing?:) A large percentage of Unity users were linux enthusiasts and it brought a lot of users into the fold where they really liked testing ubuntu. Unity made it EASY. It is a catalyst of sorts. 
Regards..

Lot of people (users) are already clamouring in the internet against killing Unity. 
Ubuntu-Gnome never reached the 50th place in Distrowatch hit ranking. Now with Ubuntu default is Ubuntu-Gnome in a way, Ubuntu would fall down the ranking. Its already going down slowly. Less people check on Ubuntu now.

---

### Post by ventrical on 2017-10-03
> **Chanath said:**
> Lot of people (users) are already clamouring in the internet against killing Unity. 
Ubuntu-Gnome never reached the 50th place in Distrowatch hit ranking. Now with Ubuntu default is Ubuntu-Gnome in a way, Ubuntu would fall down the ranking. Its already going down slowly. Less people check on Ubuntu now.

Well .. in all fairness, we will have to help make it better. At least I am committed to so doing for now.

regards..

---

### Post by flocculant on 2017-10-03
> **Chanath said:**
> Lot of people (users) are already clamouring in the internet against killing Unity. 
Ubuntu-Gnome never reached the 50th place in Distrowatch hit ranking. Now with Ubuntu default is Ubuntu-Gnome in a way, Ubuntu would fall down the ranking. Its already going down slowly. Less people check on Ubuntu now.

If you use Distrowatch as some sort of metric - please use it as it is intended by Distrowatch. 

Hit's there mean someone looked - not installed, not thinking about installing - looked. 

I look at Gentoo there sometimes - am I going to install it - ever? Nope.

---

### Post by mc4man on 2017-10-03
> **ventrical said:**
> The dev was actually commenting positively on the progress we are making with unity7 here in the thread. They are linked in at Canonical to this thread.

Regards..
You lost me there, your links were just about the use of gtk3-nocsd..

---

### Post by Chanath on 2017-10-03
> **flocculant said:**
> If you use Distrowatch as some sort of metric - please use it as it is intended by Distrowatch. 

Hit's there mean someone looked - not installed, not thinking about installing - looked. 

I look at Gentoo there sometimes - am I going to install it - ever? Nope.

I once wrote, if Distrowatch can be considered as a point of reference...

---

### Post by mc4man on 2017-10-03
While I'm firmly a unity user I can clearly see a lot of interesting things in gnome-shell & likely more to come. No doubt it will prove attractive to many users especially once Ubuntu tidies up it's release for 18.04.

---

### Post by ventrical on 2017-10-03
> **mc4man said:**
> You lost me there, your links were just about the use of gtk3-nocsd..

Those links were sent  by a dev as a sort of inline  progress report.  I was just trying to elaborate a bit.

regards..

---

### Post by ventrical on 2017-10-03
> **Chanath said:**
> I once wrote, if Distrowatch can be considered as a point of reference...

I use ubuntuforums as a gauge for usage and demographics. There is more raw and real-time data. Just go to ubuntu help forums and do the numbers.  60%+ requests are mostly unity7. I live in North America, on the homestead of the Automotive Capitals of Canada and the U.S.  so I have a good feel for what is going on in N/A but Europe is totally a horse of a different color. Ubuntu is hot in this area. Most everyone has it on the side but they don't join the forums and LoCos. A lot of people like to keep it as their own best kept secret. Ubuntu  (in all of it's flavors) is still the next new shiny thing and I don't think that is going to fade any time soon.

Regards..

---

### Post by ventrical on 2017-10-03
> **mc4man said:**
> While I'm firmly a unity user I can clearly see a lot of interesting things in gnome-shell & likely more to come. No doubt it will prove attractive to many users especially once Ubuntu tidies up it's release for 18.04.

I really like what they have done with the panel and a lot of other things with motifs. I just hope they can port in some of the  more legacy ubuntu staples like synaptic or vokoscreen .etc.. as an example. I'll be here to test it.

Regards..

---

### Post by mc4man on 2017-10-03
> **ventrical said:**
> I really like what they have done with the panel and a lot of other things with motifs. I just hope they can port in some of the  more legacy ubuntu staples like synaptic or vokoscreen .etc.. as an example. I'll be here to test it.

Regards..

In regards to vokoscreen - due to it using ffmpeg (specifically x11grab) it will only work in an xorg session. gnome-shell has a built in recorder, there are a couple of screen capture apps that support wayland (probably webm/vp8 only) but nothing yet with extensive config. options.
In general multimedia is still far better served by xorg & will continue to be for a while yet.

---

### Post by ventrical on 2017-10-03
> **mc4man said:**
> In regards to vokoscreen - due to it using ffmpeg (specifically x11grab) it will only work in an xorg session. gnome-shell has a built in recorder, there are a couple of screen capture apps that support wayland (probably webm/vp8 only) but nothing yet with extensive config. options.
In general multimedia is still far better served by xorg & will continue to be for a while yet.

Yes .. actually you sent me the link to green-recorder ppa to work with wayland.

regards..

---

### Post by Chanath on 2017-10-03
> **ventrical said:**
> I use ubuntuforums as a gauge for usage and demographics. There is more raw and real-time data. Just go to ubuntu help forums and do the numbers.  60%+ requests are mostly unity7. Regards..

What might be the requests on Gnome 3?

> **ventrical said:**
> I really like what they have done with the panel and a lot of other things with motifs. 

One single extension can kill it, and that should be a problem, even if some devs might try ignore the problem.

---

### Post by ventrical on 2017-10-03
> **Chanath said:**
> What might be the requests on Gnome 3?



One single extension can kill it, and that should be a problem, even if some devs might try ignore the problem.

Any extension, really , can kill any distro/flavor. It's the nature of the beast. It is not exclusive to gnome3. We are testing a dry-run default. You know these breakages will be in release notes. Now from the (n) for natty-narwhal and (p) for precise pangolin there was just terrible breakage - and then to trusty tahr with the in between quantal and raring cycles and the llvmpipe which pretty well destroyed unity2D on older, legacy platforms.. and then they got rid of unity2D!! We endured those bugs and overcame because of our diligence. In the spirit of community we owe that same diligence to gnome3 during 18.04.

Regards..

---

### Post by mc4man on 2017-10-03
> **ventrical said:**
> Any extension, really , can kill any distro/flavor. It's the nature of the beast. It is not exclusive to gnome3. 
Exactly, remember the 'hullabaloo' for a while concerning ccsm?   It's potential for disaster to some users, (real or a bit unfairly anticipated) dwarfs the whole dock extension deal..

---

### Post by ventrical on 2017-10-03
> **mc4man said:**
> Exactly, remember the 'hullabaloo' for a while concerning ccsm?   It's potential for disaster to some users, (real or a bit unfairly anticipated) dwarfs the whole dock extension deal..

some hot debates with Jorge Castro for certain.. and they wanted to dump it completely.. but .. nada it survived .. to some degree.. enter the mir debate.. :) .. ya know .. snakes n' ladders, dungeons n' dragons.. :)

regards..

---

### Post by Chanath on 2017-10-03
> **ventrical said:**
> Any extension, really , can kill any distro/flavor. It's the nature of the beast. It is not exclusive to gnome3. We are testing a dry-run default. You know these breakages will be in release notes. Now from the (n) for natty-narwhal and (p) for precise pangolin there was just terrible breakage - and then to trusty tahr with the in between quantal and raring cycles and the llvmpipe which pretty well destroyed unity2D on older, legacy platforms.. and then they got rid of unity2D!! We endured those bugs and overcame because of our diligence. In the spirit of community we owe that same diligence to gnome3 during 18.04.

Regards..

Unity 2D, Unity were creations of Ubuntu. Ubuntu corrected its problems and went forward. In the mean time, Gnome 3 was there on the outside. People made extensions to gnome shell, while Ubuntu went on developing Unity. Even before the 17.10 is officially released, you have a Disable Ubuntu Dock extension, for example. These extensions, and any that would arrive in the future cannot be controlled. [I]This uncontrollable situation in itself is the bug.

[/I]Unity is/was an internal matter...

---

### Post by ventrical on 2017-10-03
> **Chanath said:**
> Unity 2D, Unity were creations of Ubuntu. Ubuntu corrected its problems and went forward. In the mean time, Gnome 3 was there on the outside. People made extensions to gnome shell, while Ubuntu went on developing Unity. Even before the 17.10 is officially released, you have a Disable Ubuntu Dock extension, for example. These extensions, and any that would arrive in the future cannot be controlled. [I]This uncontrollable situation in itself is the bug.

[/I]Unity is/was an internal matter...

Was internal.

Now it is comm-Unity matter !

We will fix that bug .. err Jeremy  will fix that bug :)

Regards..

---

### Post by Chanath on 2017-10-03
Its Unity Desktop.:p

The top left corner.

---

### Post by ventrical on 2017-10-03
> **Chanath said:**
> Its Unity Desktop.:p

The top left corner.

Hey ! How did you rate that one? :)

Regards..

---

### Post by mc4man on 2017-10-03
> **ventrical said:**
> Hey ! How did you rate that one? :)

Regards..

unity source panel/PanelMenuView.cpp line 80 would do that for a Ubuntu install

---

### Post by Chanath on 2017-10-04
> **mc4man said:**
> unity source panel/PanelMenuView.cpp line 80 would do that for a Ubuntu install

Where to find this unity source panel/PanelMenuView.cpp?

I got the Unity Desktop name by simply changing the Ubuntu Desktop in /usr/lib/os-release to Unity Desktop.

---

### Post by mc4man on 2017-10-04
> **Chanath said:**
> Where to find this unity source panel/PanelMenuView.cpp?

I got the Unity Desktop name by simply changing the Ubuntu Desktop in /usr/lib/os-release to Unity Desktop.
 I suspect based on the code what you did would have the same effect.

I was thinking you all wanted to differentiate a unity session from a ubuntu session in that manner. That could be done as mentioned in unity's source.
Screens show source file & line edited from Ubuntu Desktop to Unity Desktop. What you did may have been covered by lines 81 & 82

---

### Post by Chanath on 2017-10-05
> **mc4man said:**
> I suspect based on the code what you did would have the same effect.

I was thinking you all wanted to differentiate a unity session from a ubuntu session in that manner. That could be done as mentioned in unity's source.
Screens show source file & line edited from Ubuntu Desktop to Unity Desktop. What you did may have been covered by lines 81 & 82

Thanks, mc4man. 
Winter is around the corner. Will have more time to read all that. :P

---

### Post by JonPaul on 2017-10-05
Re: Ubuntu/Unity Desktop: Bearing in mind that in Nubuntu (sic) there is nothing to say that it is Ubuntu at all. The only thing that differentiates it from other distros is the theming.

---

### Post by sunny_sigara on 2017-10-05
> [COLOR=#000000]1. On a fresh boot or logout/in an immediate r. click check on icon returns the default minimal action menu[/COLOR]
[COLOR=#000000]2. Opening a nautilus window directly after logging in still shows minimal action menu. If doing this then at some point the extended one will show up. Could just be time-base but it will show..[/COLOR]
[COLOR=#000000]3. However if after logging in I wait 10 sec before doing anything then opening a nautilus window produces the extended menu[/COLOR]
[COLOR=#000000]4. Once the extended menu shows it will stay showing in the icon action window (r. click) as long as a nautilus window is open[/COLOR]
[COLOR=#000000]5. Once the extended menu shows, after closing any nautilus windows it will still show for about 10 secs when checking the action menu, after 10 sec it goes back to the default minimal until a nautilus window is opened.[/COLOR]

@[mc4man]("https://ubuntuforums.org/member.php?u=320715")

Now nautilus app is not same as nautilus-desktop. The desktop runs as a separate binary (from 17.04). Technically it is using dynamic quicklist as long as nautilus or org,gnome.Nautilus (depends on desktop name) is running or glib.mainloop is running.  After the mainloop quits the quicklist vanishes. The 10 sec delay is bit odd though.

---

### Post by mc4man on 2017-10-06
> **sunny_sigara said:**
> @[mc4man]("https://ubuntuforums.org/member.php?u=320715")

Now nautilus app is not same as nautilus-desktop. The desktop runs as a separate binary (from 17.04). Technically it is using dynamic quicklist as long as nautilus or org,gnome.Nautilus (depends on desktop name) is running or glib.mainloop is running.  After the mainloop quits the quicklist vanishes. The 10 sec delay is bit odd though.
I was under the impession these 'action' menu items where added in the past because of a patch to nautilus that's no longer being used.
(12_unity_launcher_support.patch
So why they show up know I dunno, though it would be nicer if they did all the time or never
(- if never then they can be added to the nautilus desktop file, as it stands if added then when they show up it causes a doubling of most items

---

### Post by sunny_sigara on 2017-10-06
> **mc4man said:**
> I was under the impession these 'action' menu items where added in the past because of a patch to nautilus that's no longer being used.
(12_unity_launcher_support.patch
So why they show up know I dunno, though it would be nicer if they did all the time or never
(- if never then they can be added to the nautilus desktop file, as it stands if added then when they show up it causes a doubling of most items


They still use the unity launcher patch. See here: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1711241](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1711241)
Only header-bar patch was dropped which I think is also related with separate nautilus-desktop binary. It would be nice if anyone else can look into it. Because gtk3-nocsd works fine with Nautilus 3.26 and the header-bar patch uses same logic as gtk3-nocsd.

About quicklist, what we are experiencing is the natural behavior, unless we keep running nautilus (the app) in background all the time. Other option is to use static quicklist. :(

---

### Post by mc4man on 2017-10-06
> **sunny_sigara said:**
> They still use the unity launcher patch. See here: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1711241](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1711241)
Only header-bar patch was dropped which I think is also related with separate nautilus-desktop binary. It would be nice if anyone else can look into it. Because gtk3-nocsd works fine with Nautilus 3.26 and the header-bar patch uses same logic as gtk3-nocsd.

About quicklist, what we are experiencing is the natural behavior, unless we keep running nautilus (the app) in background all the time. Other option is to use static quicklist. :(I see what you mean now, hadn't been paying any attention to nautilus since 16.04
Gnome moved handling the desktop to a binary (nautilus-desktop) & that's what's autorun at login & always running. 
Oh well, c'est la vie

---

### Post by sunny_sigara on 2017-10-11
Hi,

@ventrical

[B]1)
[/B]
I have few bugs to report, I will keep posting the link as I file them in launchpad. 
Here is one: [https://bugs.launchpad.net/ubuntu/+source/hud/+bug/1722713](https://bugs.launchpad.net/ubuntu/+source/hud/+bug/1722713)



**2) **There are many telepathy-related patches for apparmor are still pending but all are ignored. We should form a team to tackle those and if possible push it to the upstream.



**3)** But I rather want to discuss something important.

Ubuntu is removing patches intended for Unity, even if the patches are in good working condition. When we submit new patches they said the patches are not needed for gnome-shell. The patches are written in such a way that they don't affect non-unity shell at all. For example, they remove all the patches for empathy (which we still in our company) including ubuntu-online-accounts and indicator-messages support. Uoa is defunct but the patches for messaging-menu still working. Why don't they add it back or why don't they use ours?

[https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/1712535](https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/1712535)

The "Dragon" explicitly mentions that he is hopeful that community will pick up Unity development but if don't let us how would community be any help?

**4)**

We are a small IT company and we use Unity in all our systems and we will keep using it. I may convince our management to provide monetary support if needed. But even without being the part of the company, I, personally devote myself to contribute to Ubuntu in whichever way possible. 

Thanks.

---

### Post by jbicha on 2017-10-11
> **sunny_sigara said:**
> 

We are a small IT company and we use Unity in all our systems and we will keep using it. I may convince our management to provide monetary support if needed. But even without being the part of the company, I, personally devote myself to contribute to Ubuntu in whichever way possible. 



Canonical provides 5 years of LTS support only to packages in 'main'. Therefore, there are advantages to sticking with the default LTS desktop in business environments. (And because almost everybody uses some 'universe' packages, there are advantages to upgrading to newer LTSes after 3 years since community developers don't do much work on the old LTS.)

There's a new [empathy update]("https://launchpad.net/ubuntu/+source/empathy/3.25.90+really3.12.14-0ubuntu1") today. Does it fix your Unity integration issues?

By the way, could y'all stop with the Dragon thing? :rolleyes:

---

### Post by ventrical on 2017-10-11
> **sunny_sigara said:**
> Hi,

@ventrical

**3)** But I rather want to discuss something important.

Ubuntu is removing patches intended for Unity, even if the patches are in good working condition. When we submit new patches they said the patches are not needed for gnome-shell. The patches are written in such a way that they don't affect non-unity shell at all. For example, they remove all the patches for empathy (which we still in our company) including ubuntu-online-accounts and indicator-messages support. Uoa is defunct but the patches for messaging-menu still working. Why don't they add it back or why don't they use ours?

[https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/1712535](https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/1712535)

The "Dragon" explicitly mentions that he is hopeful that community will pick up Unity development but if don't let us how would community be any help?



Will Cooke addressed most of  the issues you mention in a letter quoted in the very first message of this thread:

 [https://ubuntuforums.org/showthread.php?t=2363847&p=13656483#post13656483](https://ubuntuforums.org/showthread.php?t=2363847&p=13656483#post13656483)

> 
**4)**

We are a small IT company and we use Unity in all our systems and we will keep using it. I may convince our management to provide monetary support if needed. But even without being the part of the company, I, personally devote myself to contribute to Ubuntu in whichever way possible. 

Thanks.

Thank you for  reporting your concerns.  I am so very grateful for all the ubuntu-associated resources, the vast and ever expanding knowledge base,  the volunteers from all walks of life, Canonical and their benevolent infrastructure loaned out to all of us, and , of course, the enthusiasms and encouragement of the founders. As a group , whether member, end_user, developer or beta tester, we all  contribute valuable works to the larger mosaic however large or small with the end result that ubuntu releases are the best operating systems in the world.  Of course , not enough can be said about ubuntuforums and the tremendous amount of freelance  IT services  that we provide to the community at large, once , a diamond in the rough and now  a polished gem as a service provider for migration assistance.

  As I currently understand it there is a small group of desktop developers who are doing a lot of the heavy lifting in keeping unity7 viable as 'unity-session' and that this will continue into the next cycle which is dependent upon community involvement in maintaining some of the structures as Will had mentioned in his letter at the beginning of this thread. I have started a unity7-maintianers team and I have about 5 volunteers (which you are one) so far who are willing to pick up some of the slack. Of course I would need their assistance in working the launchpad bells and whistles and do fix/commits and merge requests to many of the current bugs (or new bugs) that may send unity7 south!  The other alternative is to re-open development of unity and mark it as version 9 (unity9) which would be the next logical step for desktops as unity8 is no longer a viable alternative. This would take a lot of work and resource and persons  who have knowledge of and who had originally designed unity and mir. If we cannot get assistance from those developers then the next best thing might be to petition that unity be an official ubuntu spin on it's own, (like xubuntu,kubuntu, lubuntu etcc..)... but first things first.  Let's see how things progress once 17.10 is released and then methodically roll over to the next toolchain and see , if in fact, unity7 remains in the universe for testing. I think we have to practice patience here and we also have to be careful not to overshoot the runway.

 There is another fly in the ointment. Ubuntu Development Version Testing forum only deals with  current  distributions/flavors that are in current development  so  this might mean that someone may petition to have any thread mentioning unity7 in UDV removed. so we might need a special exemption in fairness to the other  flavors being tested.

Hope this helps..

Regards..

---

### Post by ventrical on 2017-10-11
@sunny-sigara,

Thanks for filing those bugs! 
Exactly the type of help we need.

@jbicha,

Thanks for all your help  on those bugs.

Regards..

---

### Post by Chanath on 2017-10-12
> **ventrical said:**
> This would take a lot of work and resource and persons  who have knowledge of and who had originally designed unity and mir.

If you look in /usr/bin/unity, you'd see who authored Unity. I don't think its in his heart to push Unity away 100%.

---

### Post by ventrical on 2017-10-12
> **Chanath said:**
> If you look in /usr/bin/unity, you'd see who authored Unity. I don't think its in his heart to push Unity away 100%.

Thanks for the point!
Regards..

---

### Post by ventrical on 2017-10-12
@testers, unity7maintainers,

>  ventrical
There is another fly in the ointment. Ubuntu Development Version Testing  forum only deals with  current  distributions/flavors that are in  current development  so  this might mean that someone may petition to  have any thread mentioning unity7 in UDV removed. so we might need a  special exemption in fairness to the other  flavors being tested.


OK. Got word that there should not be a problem with continuance of unity7 testing in the UDV ubuntuforums during  18.04. Some of the developers at Canonical are  linked into this and other threads at UDV so I think this is great news but we have try and be fair whilst testing other flavors and doing time shares.

Regards..

---

### Post by flocculant on 2017-10-12
That'll be me not bothering with this sub-forum then - pretty much pointless. 

What people coming here to see what's up with official development versions will think when they see half a dozen people rabbiting on about a dead de I don't know.

Shame to see this place come to this. Just glad I'm not Elfy anymore - because if I was you'd not be getting away with it.

On the other hand I do wonder why you weren't all desperately trying to keep gnome2 going when Unity happened.

Change happens - deal with it.

---

### Post by ventrical on 2017-10-12
> **flocculant said:**
> 

On the other hand I do wonder why you weren't all desperately trying to keep gnome2 going when Unity happened.



But I was!! I raved on about Maverick Meerekat, testimonial after testimonial and then they removed the testimonial thread. And I raved on about xubuntu and tested and tested. It's in the record. It's in the knowledge base. So now I am boosting unity7 and nobody will be able to say "nobody cared" about unity7, or at least nobody will be able to say I didn't care. if nobody else cares, well, thats not mine to worry about.  It just sets a bad example to noobs   what community spirit is all about.

Regards..

---

### Post by Chanath on 2017-10-17
With everyone saying something bad, *I'd like to say something good* -- my Ubuntu Unity install is doing quite well. Just upgraded few minutes ago. Apt asked, if I want to change to system maintainer's version for issue, issue.net and lsb-release, I said no. Nothing got broken. Just 2 days to go for the final release. Hope the default Ubuntu would come out well. :)

---

### Post by ventrical on 2017-10-17
> **Chanath said:**
> With everyone saying something bad, *I'd like to say something good* -- my Ubuntu Unity install is doing quite well. Just upgraded few minutes ago. Apt asked, if I want to change to system maintainer's version for issue, issue.net and lsb-release, I said no. Nothing got broken. Just 2 days to go for the final release. Hope the default Ubuntu would come out well. :)

Iv'e been saying something good  about unity since natty narwhal. Hope I'm not included in "everyone".

If you mean my reply to this:

Flocculant wrote:
> 
What people coming here to see what's up with official development  versions will think when they see half a dozen people rabbiting on about  a dead de I don't know.

Shame to see this place come to this. Just glad I'm not Elfy anymore - because if I was you'd not be getting away with it.

On the other hand I do wonder why you weren't all desperately trying to keep gnome2 going when Unity happened.


-it was to set the record straight. That the documentation proves otherwise. Also there are others who share the same sentiments as former council member Elfy, so you see that there is a lot of opposition to unity continuance/development. I don't have to rehash that point. The current admins say it's ok to continue.

As for my unity installs, I am having varied success. From the homemade spins to current installs. I am only noticing that  there is no notification when you eject a USB using the side panel. Otherwise it is working just fine here. Works best on lightdm here.

 I too hope default Ubuntu will come out swell. Just remember .. if it does come out well it is because we tested it well ! :)

Regards..

---

### Post by rrnbtter on 2017-10-17
Greetings,
For me, this has been the best dev cycle ever.  You guys are awesome.  Re-installs, dead wifi, no vbox, pointless kernels. Who could ask for more? I'm ready for the next evolution.

---

### Post by ventrical on 2017-10-18
> **rrnbtter said:**
> Greetings,
For me, this has been the best dev cycle ever.  You guys are awesome.  Re-installs, dead wifi, no vbox, pointless kernels. Who could ask for more? I'm ready for the next evolution.

 I think I downloaded the Lion's share of ISOs this cycle. It's been a real experience with gdm3 and nVidia and wayland.  Some real true breakage, but, this is good because from all of this brokenness we are filling the crucible with the bits and pieces left over from our testing the bare metal and certainly we will hammer this into gold like we did unity and the other flavors during previous cycles.

  If I am correct .. I really take your comments as a compliment towards the whole testing team and, I must say, that it is a must needed shot in the arm and  we need this so that we can steel ourselves for the next cycle. And I also want to thank everybody, the good , the bad and the ugly, from largest to smallest for all of your priceless volunteer contributions, especially to this thread. We were able to raise unity from the ashes like the proverbial phoenix for another season. It will be there for those who may need assistive technology into the roaring 20, 20s whilst we hone and tweak  the new gnome3 . 

Thanks 

Regards..

---

### Post by Chanath on 2017-10-18
> **ventrical said:**
> Iv'e been saying something good  about unity since natty narwhal. Hope I'm not included in "everyone".

Of course, you are! 
And mc4man and others, who found something good.
Because of you I got interested in Unity again. Mc4man helped me to get Unity installed clean without Gnome-shell stuff. I also found that I can make a live installable pure Unity iso without installing it. I used to create isos from installed ones before using a modified remastersys script. But, after the call to help creating a unity distro, I found the most simple way, also from a Ubuntu wiki. The result was Unity7N.iso, still in development branch - the Ubuntu release that didn't happen. 

I think whether or not Unity 7 and Gnome-shell might trouble each other, Unity 7 should be kept in the repos. 1) Gnome works on Wayland, so not a problem for Unity 7 that works on Xorg, vice versa 2) Unity had given the boost for Ubuntu's popularity. It brought in love and hate, but that hate made it even more popular. :)

---

### Post by ventrical on 2017-10-18
> **Chanath said:**
> 

I think whether or not Unity 7 and Gnome-shell might trouble each other, Unity 7 should be kept in the repos. 1) Gnome works on Wayland, so not a problem for Unity 7 that works on Xorg, vice versa 2) Unity had given the boost for Ubuntu's popularity. It brought in love and hate, but that hate made it even more popular. :)

Well said. It is going to be an interesting cycle. Gnome and unity were meant for each other. In fact some components of unity are being proposed to be ported to wayland even now. We have to be grateful that it is being kept in the repos for the next cycle. It may buy some time to recruit a handful of developers from the vast talent network at large and be able to put forth that the idea of a standalone unity distro is a viable option for Canonical's marketing perspectives, especially  because of unity's assistive technologies and RSI reduction strategy. There are large numbers of more senior set end_users that would lean more towards a unity desktop and to drop that set and cut them off would be bad mojo all around from a benevolence point of view.

Regards..

---

### Post by flocculant on 2017-10-18
I've no issue with people trying to keep on to make Unity work - at all. I might think it's beating a dead horse - that's just my opinion, but kudos for at least trying. 

My issue is with something not official being in this official flavours dev forum ;)

Please don't conflate the issues.

---

### Post by ubname on 2017-10-18
+1

and IMHO, it would be more effective to test and improve what will be the future of the next LTS release,
it seems to me that with some improvement this new Ubuntu Gnome can be as great as Ubuntu with Unity, just an idea.

have a nice day :)

---

### Post by ventrical on 2017-10-18
> **flocculant said:**
> I've no issue with people trying to keep on to make Unity work - at all. I might think it's beating a dead horse - that's just my opinion, but kudos for at least trying. 

My issue is with something not official being in this official flavours dev forum ;)

Please don't conflate the issues.

Issues not conflated. If you go through the data base in UDV Testing you will see often threads about using Xmonad or Cairo Dock or fvwm-crystal or RazorQT (which are all in the Universe and are all variants of Desktop Experiences) and yet you had never said anything about those threads. At this point , Unity is just another desktop, yes, but we are using it to experiment alongside gnome3 as Will Cooke has asked us to do. There may also be the possibility that it could become an official flavor if we get the right maintainers.

If you also do some searches on unity7 you will see there have been several attempts to fork it. I look at it this way, if it's stuck in the universe and not somewhere else , then thats a good thing. So I will commit to this - if I get word from Will Cooke or Didrocks that they no longer request that we test unity alongside gnome3 then I will ask Cariboo to close the thread.!

Regards..

---

### Post by JonPaul on 2017-10-18
> **ventrical said:**
> If you also do some searches on unity7 you will see there have been several attempts to fork it. 
Regards..

Like this one ? [https://artemis-project.github.io/](https://artemis-project.github.io/)

Keep it up ventrical. I for one hope that Unity can live on in some form or other. Sorry I am not a dev so can't help....

---

### Post by ventrical on 2017-10-18
> **ubname said:**
> +1

and IMHO, it would be more effective to test and improve what will be the future of the next LTS release,
it seems to me that with some improvement this new Ubuntu Gnome can be as great as Ubuntu with Unity, just an idea.

have a nice day :)

I totally agree. Contrary to the opinion of some, I am not trying to circumvent this process in any way. I have no control over the powers that be. I just think it is topical we should discuss the unity as developers are officially boosting this for 17.10.  If this does not become the case for 18.04 then , yes , close the thread on principled rules of the forum.

Regards..

---

### Post by ventrical on 2017-10-18
> **JonPaul said:**
> Like this one ? [https://artemis-project.github.io/](https://artemis-project.github.io/)

Keep it up ventrical. I for one hope that Unity can live on in some form or other. Sorry I am not a dev so can't help....

If I hear anything, you all here will be the first to know:)

Thanks for you positive remarks.

Regards..

---

### Post by rrnbtter on 2017-10-18
Greetings,
I don't get the point of this discussion regarding testing desktop. Gnome Shell is only a couple hundred kilobytes out of a total of gigabytes that make up Ubuntu OS,   If Thunderbird is the Default Email Client and I am having a problem with smtp in Claws Mail is my issue then not allowed since Claws is not default? In fact I haven't used Thunderbird in the entire eight years that I have been using Ubuntu. In my opinion default has nothing at all to do with testing the Ubuntu Development session. In fact it could be said that not using these other things amounts to "not testing".  There are a few thousand software components that need to be ported to upstream Ubuntu and the Final Release will occur with much of the job incomplete. 

I personally am no longer using Unity. I think that Gnome on Wayland is just about perfect and I never considered Unity perfect at all. But this whole issue of Unity Desktop has been an interesting learning opportunity.  Chanath and Ventrical and others have done a fine job here. It is testing at its best and directly related to the 17.10 release. I'm on the edge of my seat waiting for the next one. This is open source at its best. 
Just my opinion. You can delete this post if you want to.

---

### Post by ventrical on 2017-10-18
> **rrnbtter said:**
> Greetings,
I don't get the point of this discussion regarding testing desktop. Gnome Shell is only a couple hundred kilobytes out of a total of gigabytes that make up Ubuntu OS,   If Thunderbird is the Default Email Client and I am having a problem with smtp in Claws Mail is my issue then not allowed since Claws is not default? In fact I haven't used Thunderbird in the entire eight years that I have been using Ubuntu. In my opinion default has nothing at all to do with testing the Ubuntu Development session. In fact it could be said that not using these other things amounts to "not testing".  There are a few thousand software components that need to be ported to upstream Ubuntu and the Final Release will occur with much of the job incomplete. 

  I'm on the edge of my seat waiting for the next one. This is open source at its best. 


+1 :)

---

### Post by Chanath on 2017-10-18
Now that when upgrading, apt tries to change the issue, issue.net and lsb-release (since yesterday), what you get from upgrading is what you'd get when you download the final, when it'd be announced. Also, if today's downloaded daily turned to Unity only, it'd be the final Ubuntu Unity that didn't happen.

---

### Post by cariboo on 2017-10-18
Thread closed by request.

---

