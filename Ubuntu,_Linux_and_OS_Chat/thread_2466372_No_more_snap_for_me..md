---
title: "No more snap for me."
date: 2021-08-26
forum: Ubuntu, Linux and OS Chat
---

### Post by forcecore on 2021-08-26
First i am glad that snap is not force-tie-in with Ubuntu and i hope it stays that way. I removed all snap systems and stuff 100% after it made great costly bill with forced refresh updates on mobile wifi hotspot device. Idea is great but forced upgrades and slowness is not for me and i just use pure barebone Ubuntu desktop and portable apps from now on. I update my system with Synaptic when i need and have prepared to update.

---

### Post by GhX6GZMB on 2021-08-26
I'm with you.
The first thing I do after a fresh install is remove snapd. Useless.

---

### Post by mikewhatever on 2021-08-26
Namebench is a python2 program for DNS testing. It is no longer available in Ubuntu 20.04 forward, as well as in Debian 11, but is available as a snap. So, yesterday I ran <sudo snap install namebench-snap>, and tested what was needed. It was useful, practical and easy. I also use a mate-welcome snap, ... much recommended.

Now, the notion of being forced to use something, or something being force-tied comes up from time to time. So, Ubuntu has APT, Gnome3, the linux kernel and GNU tools by default. Are you foced to use them? In a way, yes, certainly, some more then the others, but unremovable snaps - no way.

---

### Post by grahammechanical on 2021-08-27
If we update/upgrade through the terminal snap apps do not get updated. A special command is needed to update/refresh snap apps and Software Updater runs it as well as update & upgrade. Software Updater also runs the autoremove command. So, if we stop using Software Updater we should run

```
sudo apt autoremove
```

from time to time to remove excess Linux kernels. Whether was want to remove snapd to prevent bandwidth being used to update it, is our choice.

Regards

---

### Post by zebra2 on 2021-08-28
Post #4 sounds right to me. I have three laptops, one on 21.04 and two on 21.10. Snapd is installed and active on all three. I do all of my system management at the command line and my  snapd list is empty other than snap it's self.  If I need an application I use apt-get and if I want to install a deb I use Gdebi. If it turns out that I have to use a snap for some reason then snapd is there and I will use it. So far doing fine without it.

---

### Post by forcecore on 2021-09-20
I just hope that Canonical never ever force snap installation and thus cannot be removed 100%. Canonical please never be like Microsoft who becomes more and more enforcing. Canonical be light, be configurable and always allow people to remove & remaster. Thanks.

---

### Post by grahammechanical on 2021-09-20
In my opinion the future for Linux is Flatpack or Snap (or both) but not rpm or deb. 

Some years ago Canonical produced a version called Ubuntu Personal. It was a snap based OS that had Over The Air updates and it was set up so that an update could never break the OS. I had it installed. It had Mir for the display driver and Unity 8 for the user interface. And it worked too! And looked good. It only had Click apps available in the App store and they did not work.

Canonical never transitioned Personal on to the next Ubuntu version. Canonical still has a Snap based OS. It is called Ubuntu Core. It is at version 20. What does it need to become a fully snap based distribution of Ubuntu? A snap desktop environment; a snap user interface and the standard default applications compiled as snap applications. There is a snap version of LibreOffice and now we have an official snap version of Firefox.

I see a vision of the future. Redhat or Canonical or small independent community developed distributions. Oh, by the way, Redhat has been working on something similar for years. It is an immutable OS. That means the user cannot do much configuration. It is called Silverblue.

[https://fedoramagazine.org/what-is-silverblue/](https://fedoramagazine.org/what-is-silverblue/)

Regards

---

### Post by mikewhatever on 2021-09-20
> **forcecore said:**
> I just hope that Canonical never ever force snap installation and thus cannot be removed 100%. Canonical please never be like Microsoft who becomes more and more enforcing. Canonical be light, be configurable and always allow people to remove & remaster. Thanks.

With time and skill, you can remove and remaster all you like. Get rid of APT and Python, implement alternatives, write a new C compiler, through out all the GNU tools.
Complaining that you are foced to use things you don't want, is a fight against reality, and a way to blame others for your own shortcomings. Instead, look at the "glass half full" part of the deal.

---

### Post by kurt18947 on 2021-09-20
> **grahammechanical said:**
> 
I see a vision of the future. Redhat or Canonical or small independent community developed distributions. Oh, by the way, Redhat has been working on something similar for years. It is an immutable OS. That means the user cannot do much configuration. It is called Silverblue.

[https://fedoramagazine.org/what-is-silverblue/](https://fedoramagazine.org/what-is-silverblue/)

Regards

Would something like that be popular for enterprise use? Or perhaps schools?

---

### Post by grahammechanical on 2021-09-21
> Would something like that be popular for enterprise use? Or perhaps schools?

I think so. The experts use the term "immutable." It means that the OS is in its own partition and it is read-only. That prevents the user from changing system files. It might even prevent clever but stupid school students from breaking the school network. And then there are the self-important but unimaginative company managers who have their password on a sticky note attached to the screen.

I do not know about the method used by Redhat but Canonical uses two read-only partitions (A & B). The OS boots from partition A. The update goes into partition B and the OS boots from partition B. The next update will go into partition A and the OS will boot from partition A. And back and forth the updates and booting goes. If an update should fail the OS continues to boot from the partition it was booting from before the update began. That should mean that people come into work and do not find a broken OS due to a failed update that took place during the night.

I do not want to get into a debate on Flatpack verses Snap but surely it is better to have applications that are not allowed to access system directories and are severely restricted as to what directories they can access?

I do not think this will be popular. Change is never popular but then a new generation comes along who does not know any difference and what was unpopular is accepted as normal life. And so we live.

Regards

---

### Post by poorguy on 2021-09-21
[https://www.omgubuntu.co.uk/2021/09/ubuntu-makes-firefox-snap-default?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29](https://www.omgubuntu.co.uk/2021/09/ubuntu-makes-firefox-snap-default?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29)

---

### Post by poorguy on 2021-09-22
> **grahammechanical said:**
> 
Change is never popular but then a new generation comes along who does not know any difference and what was unpopular is accepted as normal life. And so we live.

You are a wise man grahammechanical. :cool:

---

### Post by forcecore on 2021-09-25
> **mikewhatever said:**
> With time and skill, you can remove and remaster all you like. Get rid of APT and Python, implement alternatives, write a new C compiler, through out all the GNU tools.
Complaining that you are foced to use things you don't want, is a fight against reality, and a way to blame others for your own shortcomings. Instead, look at the "glass half full" part of the deal.

.....Until you get hefty bill because snap downloaded massive updates without any asking.

---

### Post by Dennis N on 2021-09-25
Firefox snap has been reported as the default in Ubuntu 21.10, but in the just released beta (on Fri. the 24th), both the .deb and snap are installed by default. This may not be the case in the final release. Only the snap initially shows in the dock, so unless you look further at all applications, you would not see the other.

---

### Post by monkeybrain20122 on 2021-09-28
> **Dennis N said:**
> Firefox snap has been reported as the default in Ubuntu 21.10, but in the just released beta (on Fri. the 24th), both the .deb and snap are installed by default. This may not be the case in the final release. Only the snap initially shows in the dock, so unless you look further at all applications, you would not see the other.

It is easy to uninstall the firefox snap and then just grab the tarball  from Mozilla. Moreover I am sure there will be a ppa by 22.04 since debian will  not likely switch to snap so deb version will be there

---

### Post by vo-nguyen on 2021-10-30
I think snap is kind of clunky sometimes. But, I got Discord using snaps.

---

### Post by forcecore on 2022-05-06
My old thread, but still similar scenario almost happened, but this time i terminated snap before and that was wisest decision once again. Snap is clunky, slow, updates cannot be disabled easily. Ubuntu itself is still very good OS, almost just like OS X and it is open unlike Apple.

I use good old Synaptic to update system when i want. As for software, i use almost all software as a portable software depending of app type. Snap virtual machine should be re-written in hi-performance and lightweight C++(latest revision)

---

### Post by TenPlus1 on 2022-05-06
First thing I do is uninstall snaps and then use LibreWolf.net to install either the .deb or use .appimage depending on machine.

---

### Post by TheFu on 2022-05-06
> **grahammechanical said:**
> If we update/upgrade through the terminal snap apps do not get updated.  

This has not been my experience.  

Snap packages are checked for available updates daily, even though I have disabled all APT updates on the system.  Further, the default settings keep 3 versions of every snap package on the local system, so falling back to either of the prior 2 versions is possible.  I've modified the snap settings to only keep 2, but there's no way to keep just the current package. Another override that the snap team decided we weren't smart enough to decide for ourselves.  Haven't snaps use 3G of storage on a 16G system drive is offensive.

The only way I've been able to prevent snapd from checking for updates was to block the snap remote repo at the network layer.

Forcing a new package system isn't very nice, especially when the default constraints which cannot be locally changed, conflict with local policy choices.  For example, create a user's HOME directory in /u/{username} and try to run any snap - doesn't matter which - using that account. No snaps work.  This is a huge failure. It isn't like the /etc/passwd or LDAP HOME directory location shouldn't be trusted.  There are a number of other choices made in the name of 'security' which seem more about control, and less about true security.

But what do I know?  I just expect my workstations to allow users to do their jobs in the way they decide it should be done, not under the control of someone creating package tools.

Flatpak allows local controls WITH sandboxing.  That's the right mix of more security AND flexibility, IMHO.

So, here's an example:
```
$ snap list
Name      Version        Rev    Tracking       Publisher     Notes
core18    20220309       2344   latest/stable  canonical&#10003;    base
core20    20220329       1434   latest/stable  canonical&#10003;    base
lxd       5.0.0-b0287c1  22923  latest/stable  canonical&#10003;    -
snapd     2.55.3         15534  latest/stable  canonical&#10003;    snapd
wormhole  0.12.0         349    latest/stable  snapcrafters  -
```

I want to use wormhole to share a file with a buddy.  It works on other systems here. But not on this system:
```
$ /snap/bin/wormhole 
Sorry, home directories outside of /home are not currently supported. 
See https://forum.snapcraft.io/t/11209 for details.
```

See, we have users placed into different directories.  Local-only users can be in /home/, but LDAP users are placed on storage elsewhere using NFS mounts.  The suggestion to use a bind-mount to place those other directories over /home/ would break all the users already there.  Plus, their "workaround" requires that we change the HOME specified in LDAP to /home/{userid} ... which will break the users' access across all other systems where it works fine.  Most users have access to 20 other systems - that aren't Ubuntu.  Canonical needs to realize their desktop isn't the only system in a corporate environment. It is common to have AIX, Solaris, HP-UX, RHEL, and other systems too.

Local control for a few items in the constraints is needed. Until then, snaps are useful for IoT stuff without users. Desktops require much more flexibility.

Sigh.

---

### Post by Paddy Landau on 2022-05-06
I originally liked snaps, and I was puzzled by all the hate that it receives on Reddit. A number of posters claim, incorrectly, that Ubuntu forces you to use snap, and that removing it breaks Ubuntu. Utter nonsense.

However, since 22.04, snap's slowness has become an issue, even on a modern computer with plenty of RAM and everything on SSD. Compare Firefox or Opera in snap vs either flatpak or deb. Chalk and cheese.

Hence, now, I don't use snaps unless I have no choice. I'm not going to uninstall it; there's no point. But I won't use it unless I have to.

I don't think that snaps will become strictly enforced. For example, Linux Mint specifically comes without snap to cater for the snap-haters. (I personally don't understand why people go so far as to hate something; if you don't like it, just don't use it.)

---

### Post by #&amp;thj^% on 2022-05-06
Paddy Landau i totally agree, I myself *have* to use a few snaps like TheFu "snaps are useful for IoT stuff without users"
Those machines confuse my family to a high frustration, I then install snap free desktops for them to use, once again as TheFu points out "Desktops require much more flexibility."
My darling wife has threatened to leave me if I install 22.04 on anything she use's. ;)
NOTE: most of all hate/frustration based comments, come simply from the un-known, and others have a real performance complaint.

I'm by no means a fan of snaps, but I don't hate them.
I try to stay optimistic in hopes snaps become, not more polished but perfectly polished.

---

### Post by DuckHook on 2022-05-06
> **Paddy Landau said:**
> …(I personally don't understand why people go so far as to hate something; if you don't like it, just don't use it.)
Agreed. Hate is too strong an emotion to apply to anything as mundane as a computing component. But I also understand the irritation:

For the average user, snaps are no longer optional. Firefox comes only as a snap, hence, snapd is being foisted on all users as a necessary component. Of course, this can be worked around, but doing so requires further knowledge and effort that general users cannot be expected to have or to expend.

Moreover, there are system functions no longer possible without snaps. I rely on LXD. It only comes as a snap. Therefore, I have no choice in the matter.

The upshot is that I've had to increase my / partitions from 24 to 64 GB. The old saw that "storage is cheap these days" doesn't cut it. One of the strengths of Linux has always been its resource efficiency. Giving that up for a questionable packaging system is a bad trade.

I will live with snaps, but I won't like them. IMO, they are problematic, wasteful, slow, inefficient, inflexible and half&#8209;baked. Those are pretty serious drawbacks.

---

### Post by Paddy Landau on 2022-05-06
> **1fallen said:**
> My darling wife has threatened to leave me if I install 22.04 on anything she use's. ;)
Well, if it's her equipment, obviously it's her decision.

I've been running 22.04 in a VM prior to taking the leap, and in my experience, it's mostly solid. There are a few teething problems mainly to do with my preferred Gnome extensions that haven't yet been updated, but nothing that I can't work around or replace. I'm sure that when 22.04.1 comes in a few months, it'll be solid — except for those legacy icons.
> **1fallen said:**
> I try to stay optimistic in hopes snaps become, not more polished but perfectly polished.
They'll have to overcome the slowness, because on 22.04, it's stupidly slow compared to flatpak and deb. I watched a video introducing 22.04, and it said that it took a full 10 seconds to load Firefox. I thought, "Well, my machine's a lot faster than that." No, it wasn't!
> **DuckHook said:**
> For the average user, snaps are no longer optional. Firefox comes only as a snap, hence, snapd is being foisted on all users…
That is a good point. I hadn't considered this. Those users will complain, "But I thought you said that Linux was faster than Windows?"

Firefox on a snap is a debacle.
> **DuckHook said:**
> The upshot is that I've had to increase my / partitions from 24 to 64 GB.
That's a lot of extra storage. Just for snaps?

I tried to measure my snap folder, but I get contradictory results. Nautilus reports it as taking 213.9 Kb. But du reports it as taking 57 Mb. So, I don't know! Still, it's far less than even 1 Gb.

---

### Post by #&amp;thj^% on 2022-05-06
> **Paddy Landau said:**
> Well, if it's her equipment, obviously it's her decision.


Not her equipment, but it is her choice. I point that out because she is  the most grounded person i know.
it just struck me odd for her to have that strong of a statement.

---

### Post by DuckHook on 2022-05-06
> **Paddy Landau said:**
> …That's a lot of extra storage. Just for snaps?

I tried to measure my snap folder, but I get contradictory results. Nautilus reports it as taking 213.9 Kb. But du reports it as taking 57 Mb. So, I don't know! Still, it's far less than even 1 Gb.
The bloat isn't snapd itself. The real bloat occurs if I have to install further apps. They take insane amounts of storage. Here's an older thread that outlined the problem: [https://ubuntuforums.org/showthread.php?t=2470573](https://ubuntuforums.org/showthread.php?t=2470573)
So, I'm setting aside more storage to future proof my install. Who knows how many apps Canonical will decide to move to only snaps in the future? I don't want to have to wrestle with the problem at that point, so I'm setting aside sufficient space now.

As stated, it is irritating.

---

### Post by Paddy Landau on 2022-05-06
> **DuckHook said:**
> Who knows how many apps Canonical will decide to move to only snaps in the future?
I've found that nearly all apps are available from the repositories or flatpak, or failing that, as a deb download from the official website. Not many are snaps only.

Of course, if you generally need an up-to-date version, the standard repositories are no good.

Flatpak needs to be set up on Ubuntu, but once done, they're all available as an option on the Software store, which is, surprisingly, easier than using the command line. Flatpaks load as fast as standard debs.

It would make enormous sense for Canonical to move from snaps to flatpaks; the infrastructure is already solid with massive support.

---

### Post by TheFu on 2022-05-06
> **Paddy Landau said:**
>  
I don't think that snaps will become strictly enforced. For example, Linux Mint specifically comes without snap to cater for the snap-haters. (I personally don't understand why people go so far as to hate something; if you don't like it, just don't use it.)

Hate isn't really what they mean.  They just are frustrated and dislike not having a choice.  Normal users won't block defaults or default repos or add a PPA.  What should a non-technical 85 yr old do that doesn't require using a shell?  (Yes, I get the irony). ;)

So, what is a normal person supposed to do when the only way a program they need is only shipped as a snap package?  Are normal users supposed to rip the snap apart and directly run the program outside the snap environment?  

For example, please show me how to use the lxd v5.x snap without running in a snap environment? Please.  
I'd seriously like to know.

I've stayed away from my anti-snap stuff for a few months, but that doesn't mean it isn't still frustrating. I'm not really anti-snap either - I just want local control for some key things they've decided to hard-code and the ability to disable the protection-sandbox so I can use a better solution for a few programs.

---

### Post by TheFu on 2022-05-06
> **Paddy Landau said:**
>  It would make enormous sense for Canonical to move from snaps to flatpaks; the infrastructure is already solid with massive support.

From our perspective, it makes since. But not from Canonical's.  By being THE only snap repo (they claim it is 100% open and others can create snap repos, but nobody has done this ... why could that be?), they gain access to all sorts of "surveillance data" that they don't have to divulge.  Of course, nobody knows what, if any, data is captured or how it is used.

The best we can hope with snaps is that they go away like Unity eventually did, and flatpaks win.  That's the best case, since the problem trying to be solved is real, but not universal to all linux desktops.  Once again, Canonical is trying to fragment the Linux system market, trying to be a differentiator.  

AppArmor is another method that happened, but apparmor isn't as difficult to use (or ignore) as the competing SELinux, so we never hear about issues.  Actually, I see a number of apparmor errors related to snaps on all my systems daily. I can only guess it is because the apparmor profiles for different versions of different apps on different released aren't fully compatible/tested.

---

### Post by Paddy Landau on 2022-05-06
I'm going to backtrack a bit on flatpak. I've just measured my flatpak folder…

5.5 Gb

Tsk. This isn't good. It's better than snap, a lot better, but still, that's too much even for a modern computer.

---

### Post by Paddy Landau on 2022-05-06
> **TheFu said:**
> For example, please show me how to use the lxd v5.x snap without running in a snap environment?
Hmm, you're right. There's only the one option. That is frustrating.

---

### Post by VMC on 2022-05-06
I believe its fear instead of hate. Fear that in the future your going to be forced to use snaps.
[I use this to install Firefox.]("https://support.mozilla.org/en-US/kb/install-firefox-linux#w_install-firefox-from-mozilla-builds-for-advanced-users") I use gnumeric and Abiword instead of Libreoffice. It fits my needs,

---

### Post by Paddy Landau on 2022-05-06
> **VMC said:**
> [I use this to install Firefox.]("https://support.mozilla.org/en-US/kb/install-firefox-linux#w_install-firefox-from-mozilla-builds-for-advanced-users")
You can install Firefox as a flatpak, which is much easier.
 > **VMC said:**
> I use gnumeric and Abiword instead of Libreoffice. It fits my needs,
Likewise, you can install LibreOffice as a flatpak, or you can use their official PPA [FONT=courier new]ppa:libreoffice/ppa[/FONT]. Their PPA is usually about two, maybe three, weeks out of date, which is absolutely fine, because it means that the first teething problems are skipped. I've been using their PPA for a very long time.

---

### Post by DuckHook on 2022-05-06
> **Paddy Landau said:**
> I'm going to backtrack a bit on flatpak. I've just measured my flatpak folder…

5.5 Gb

Tsk. This isn't good. It's better than snap, a lot better, but still, that's too much even for a modern computer.
*All* of these newfangled "alternative" packaging systems cause obscene system bloat. How can they not? Their whole shtick is that they have all of the current libraries included so that they are entirely "self contained" little beasties. This means that the amount of duplication is now out of control. The old paradigm of efficiently sharing libraries even if this means making a few concessions is dying. Nobody gives a hoot about system elegance anymore. It's but an instance of the "I want what I want and I want it ***now***" mindset.

---

### Post by TheFu on 2022-05-06
> **Paddy Landau said:**
> I'm going to backtrack a bit on flatpak. I've just measured my flatpak folder…

5.5 Gb

Tsk. This isn't good. It's better than snap, a lot better, but still, that's too much even for a modern computer.

The nature of the solution to the 'run anywhere' problem is that specific support libraries need to be packaged.  In the old days, we'd call that a .deb package, but .deb packages are specific to a release, to the 2rd dot (.) in the library version. 

What does that mean?  If we have libxyz.so, then for 18.04, the library file/version could be
libxyz-1.3.4.so with a symlink to libxyz.so. This is so when bug fixes or security fixes for 18.04 are released, then the version can be libxyz-1.3.5.so.  
There's a gentleman's agreement that major API changes require changing the 1st level number (1 in this example), functionality changes, with the same API require changing the 2nd level number (3 in this example) and that the 3rd level number is increased to show it is newer with fixes.  
So going from libxyz-[COLOR="#008000"]1.3[/COLOR].5.so ---> libxyz-[COLOR="#FF0000"]1.4[/COLOR].0.so tells us that the API is the same, but functionality in at least one of the existing APIs has changed.  It is a warning for programmers and some admins.  The 1.4.x version wouldn't be included in 18.04, since it could break other dependent programs.

Jump forward to 20.04 and we have libxyz-1.4.3.so.  Of course, the library maintainers have been working on 2.0.x for a few years now. It is the greatest code ever written by anyone in all time. They can't believe anyone would still use 1.4.x code. That's all crap.  They know it. We know it, but we are on 18.04 still.  But lots of new programs have moved to use libxyz-2.0.8.so of the library.  But my 18.04 system can't use it.  

Snaps/flatpaks and appimages to the rescue!  By controlling the order of the LD_LIBRARY_PATH and putting the directory where libxyz-2.0.8.so exists before where libxyz-1.4.x.so is located, we can use the newer library for just that program, but not for any others.  This has been something we did for 35 yrs.  Snaps, flatpaks and AppImages just do it through the environment control, containers, and kernel cgroups.  They trade disk storage and RAM for convenience. 

Of course, 22.04 comes with libxyz-2.3.20.so they've been busy updating lots of APIs, but also introducing new bugs.  ".20" is a larger number than .3, btw.  The dots (.) are the separators. 

BTW, I left out that each new version of the library also changes the symlink to libxyz.so. This isn't automatic. It has to be handled by deb packages and snap, flatpacks, appimages, or our personal program start scripts, alike. It isn't hard, just a little accounting.

Say we have 2 different programs, each dependent on different libxyz.so versions.  That means that the snap or program startup script will place the specific path for the LD_LIBRARY_PATH before the other location so the desired libxyz.so gets loaded into RAM.  .so means it is a **s**hared **o**bject (i.e. a shared library).  If we have both of those running, the versions are understood by the linux library loader and placed into different code segments in RAM.  Effectively, we use 2x the RAM because there are 2x the libraries loaded.  For small libraries, that really isn't a big problem, but ... Qt and GTK+ versions are grouped as large packages.  Look at the snap list
[LIST]
[*]gnome-3-28-1804
[*]gnome-3-38-2004
[*]gtk-common-themes 
[/LIST]
The sizes of these are:
```
installed:          3.28.0-19-g98f9e67.98f9e67            (161) 172MB -
installed:          0+git.1f9014a             (99) 260MB -
installed:          0.1-59-g7bca6ae            (1519) 68MB -

```
So if I use a gtk app from 18.04 from a snap packaged version, it will also load ~172MB of library stuff into RAM.  If I run a gtk app from 20.04 from a snap packaged version, that becomes ~260MB.  Those are just the CS aspects.  DS, the data segment, which is for each program, separately will probably be about the same for all the GTK programs ... snaps or non-snaps alike.

I don't use gnome as a DE and my GUI doesn't use GTK+ code, so I save at least 170MB of RAM use, until the first GTK+ program gets run.  There are 'core' snap libraries for each release too.  These appear to be about 64MB each, so add those for non-GUI programs under each snap. Again, the DS for each program is separate.

After all, just running any snap will use 64MB of RAM to start, before the program gets loaded.  In top, the snap version of the chromium browser has grabbed "25.3GB" of RAM, which isn't really possible. The true amount of RAM used is just under 1G for chromium with 1 tab open to the chromium default location. Quite bloated.  Without the snap wrapper, running the exact same executable on the same system, the RAM use drops to about 500MB.  If there was an easy way to show all the chromium processes real RAM use, I'd run the command and post it. In top, I see 3 chrome processes and use my brain to add up the RES columns.

And this is why we need more than 640Kb of RAM on our computers.  Convenience.  

Phew.  I hope that's clear for someone.

---

### Post by #&amp;thj^% on 2022-05-06
> **DuckHook said:**
> It's but an instance of the "I want what I want and I want it ***now***" mindset.

Dang, way to make me take a beat, "confession" I'm guilty of that. (maybe more than I should):(

---

### Post by TheFu on 2022-05-06
> **1fallen said:**
> Dang, way to make me take a beat, "confession" I'm guilty of that. (maybe more than I should):(

Everyone has different requirements, wants and needs. Nothing wrong with that, unless you are system designer and force your needs onto millions of others who don't want it.

---

### Post by #&amp;thj^% on 2022-05-06
> **TheFu said:**
> Everyone has different requirements, wants and needs. Nothing wrong with that, unless you are system designer and force your needs onto millions of others who don't want it.
Agreed,
after a reflection back, I guess I'm more>> I want what I "had" (pre snaps && netplan) and I want it now. :lolflag:

---

### Post by Paddy Landau on 2022-05-06
> **TheFu said:**
> I hope that's clear for someone.
It was clear. And a bit frightening!

With the exponential decrease in hardware, you'd initially think that this won't be a problem in a couple of years, but it will — as hardware improves, so do users' demands.

I remember when PCs started to come with 640 Kb RAM (gasp!). Chatting with my work colleagues, we couldn't imagine a system ever needing that much RAM.

Here we are, needing at least 16 Gb to run a decent setup, which of course is more competent by several orders of magnitude than back then.

---

### Post by zebra2 on 2022-05-07
The OP in this thread is 9 months old which officially qualifies it as ancient.  As it stands right now snap itself does not appear to be optional.  It can ignore any systemctl command that would stop it from satisfying the snap app's dependencies. I haven't challenged it to any degree just yet but normal masking has no effect on Ubuntu 22.04 and will very likely further advance toward mandatory as 22.10 marches on. I really like Ubuntu 22.04 and 22.10 and it's possible that I may have to learn to tolerate these changes. It may come down to how much time I want to invest in outsmarting an OS that I actually like on three computers.  I may have to take a break from all of this and go check my mail or something.

---

### Post by Paddy Landau on 2022-05-07
> **zebra2 said:**
> As it stands right now snap itself does not appear to be optional.
Untrue! Snap is optional.

I signed onto my installation of Ubuntu 22.04.

I removed all installed snaps; deleted the ~/snap folder; uninstalled both gnome-software-plugin-snap and snapd itself; and restarted the machine.

The installation continued to work even after a reboot, both Wayland and X.Org.

---

### Post by VMC on 2022-05-07
> **Paddy Landau said:**
> You can install Firefox as a flatpak, which is much easier...Not for me it isn't. I don't use flatpak or snap; and won't.

---

### Post by Paddy Landau on 2022-05-07
> **VMC said:**
> Not for me it isn't. I don't use flatpak or snap; and won't.
Well, that's your choice. You can install Firefox from a DEB if you like. I saw some instructions earlier today, but I didn't take note of them, sorry.

---

### Post by oldfred on 2022-05-07
I posted this on removing Firefox snap which so far has worked well in Kubuntu 22.04 install.

[https://ubuntuforums.org/showthread.php?t=2474458](https://ubuntuforums.org/showthread.php?t=2474458)
and:
[https://ubuntuforums.org/showthread.php?t=2474557](https://ubuntuforums.org/showthread.php?t=2474557)

---

### Post by zebra2 on 2022-05-07
> **Paddy Landau said:**
> Untrue! Snap is optional.

I agree that optional may not be the right word here.  I quit using firefox years ago, it was optional and still is (snap remove firefox*).  You can still download firefox from the wild if you trust that.  It is like not using google play on a android phone and getting apps off the wild. You don't trust google to not mine your data but you trust the wild for the app and to not mine your data or even the extensions in firefox to not mine your data.  

But snap is not optional because without it you cannot use Ubuntu system add-on's that are only provided via snap such as the automatic kernel updates and the updating process in its entirety and what ever else they are doing via snap only. 

I believe that Canonical is attempting to provide a "Install it and Use it" OS aimed at the part of the user base that wants an OS option but doesn't have the technical ability to navigate what we are discussing here.  They just want a computer the works and is safe. My wife uses Ubuntu every day without complaint, but only because she has me.  Without me she would be using the original Windows 10 that came with the system and probably be paying ransom ware by now.  Some people want an OS experience that is safe and just works. I personal think snap or something like it provides that need even though I don't need it myself. 

Snap may be optional "still" in some respect but new users won't bother to question that, because they won't know to make it a problem.

---

### Post by Paddy Landau on 2022-05-07
> **zebra2 said:**
> … snap is not optional because without it you cannot use … automatic kernel updates and the updating process in its entirety…
I was not aware of that!

I think that I stand corrected.

---

### Post by #&amp;thj^% on 2022-05-07
I've not seen any problems testing my snapd free bed.
```
me@me-Standard-PC-Q35-ICH9-2009:~$ df -hT
Filesystem     Type   Size  Used Avail Use% Mounted on
tmpfs          tmpfs  393M  1.5M  392M   1% /run
/dev/vda3      ext4    24G  7.6G   16G  34% /
tmpfs          tmpfs  2.0G     0  2.0G   0% /dev/shm
tmpfs          tmpfs  5.0M  4.0K  5.0M   1% /run/lock
/dev/vda2      vfat   512M  5.3M  507M   2% /boot/efi
tmpfs          tmpfs  393M  124K  393M   1% /run/user/1000
```
```
me@me-Standard-PC-Q35-ICH9-2009:~$ apt policy snapd
snapd:
  Installed: (none)
  Candidate: 2.55.3+22.04ubuntu1
  Version table:
     2.55.3+22.04ubuntu1 500
        500 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
     2.55.3+22.04 500
        500 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 Packages

``` 
firefox:
```
me@me-Standard-PC-Q35-ICH9-2009:~$ apt policy firefox firefox-esr
firefox:
  Installed: (none)
  Candidate: 1:1snap1-0ubuntu2
  Version table:
     1:1snap1-0ubuntu2 500
        500 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
     100.0+build2-0ubuntu0.22.04.1~mt1 500
        500 https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu jammy/main amd64 Packages
firefox-esr:
  Installed: 91.9.0esr+build1-0ubuntu0.22.04.1
  Candidate: 91.9.0esr+build1-0ubuntu0.22.04.1
  Version table:
 *** 91.9.0esr+build1-0ubuntu0.22.04.1 500
        500 https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu jammy/main amd64 Packages
        100 /var/lib/dpkg/status

```
I'm not advising anything here>> just posting my *early* findings

---

### Post by Paddy Landau on 2022-05-07
> **1fallen said:**
> … posting my *early* findings
@zebra2 warns that core kernel updates won't come through. I'll see if I can test this.

---

### Post by #&amp;thj^% on 2022-05-07
I've not seen those problems everything as it should be.
If that means breaking the Ubuntu Advantage program then I would agree.

---

### Post by vanadium on 2022-05-07
> **zebra2 said:**
> 
But snap is not optional because without it you cannot use Ubuntu system add-on's that are only provided via snap such as the automatic kernel updates and the updating process in its entirety and what ever else they are doing via snap only. 

Running without snapd for over a year, and kernel updates and even bios updates (Dell laptop) keep coming in automatically. In 22.04, only Ubuntu Software and Firefox are delivered as a snap. In previous versions, some Gnome utilities like characters, etc. were packed as a snap. Ubuntu Software can easily be replaced by Gnome Software if there is a need.

---

### Post by Paddy Landau on 2022-05-07
> **1fallen said:**
> I've not seen those problems everything as it should be.
I guess that we'll find out the next time when the kernel is updated.

I've just created a fresh installation of Ubuntu 22.04 and immediately removed the snaps (there was only one, not even Firefox or Ubuntu Software) and uninstalled snapd. The kernel is 5.15.0-27. Comparing against another 22.04 with snaps intact and fully up-to-date, it's the same kernel.

So, it might be a while before there's a kernel update and we can be sure.

---

### Post by deadflowr on 2022-05-07
snap kernel updates apply only to the Canonical's livepatch system.
Regular apt updates for kernels are as they always have been. 

If you update normally, regularly, and reboot often then livepatching is mostly moot.
Since newer kernels will have all the patches that came for the livepatch built into them.

Livepatch is nice to have for systems that require very little downtime, but that is all it is; nice.
Not a required feature.

---

### Post by #&amp;thj^% on 2022-05-07
Nicely put deadflowr

---

### Post by Paddy Landau on 2022-05-07
> **deadflowr said:**
> snap kernel updates apply only to the Canonical's livepatch system.
Ah, thank you. I didn't realise that. Livepatch isn't relevant to me.

---

### Post by ajgreeny on 2022-05-07
Until about two weeks ago I had two separate installs of Xubuntu 22.04 from Nov 2021 when the Xubuntu ISOs first became bootable, on a desktop and laptop, both of which had all the snap infrastructure removed and ran with PPA  versions of chromium and the downloaded .tar.gz archives of firefox.
I accept that it is much more recently than Nov 2021 that firefox became available as snap only from the repos, and I'm also aware that Xubuntu uses fewer snaps than Ubuntu.  

However, both installed versions ran from Nov until late April with snaps removed and I saw absolutely no problems as a result of them being missing.
I keep away from snaps as my hardware is now rather elderly, the desktop being 9yrs old and the laptop 8yrs old, meaning snaps seemed to take forever to start the first time in a session, sometimes over a minute, which I was not prepared to live with.

I prefer to keep full control of all operations in my systems so unattended-upgrades package is removed and I do not even allow  the update-notifier to start and therefore run update/upgrade aliases just about every day to make sure all is up to date.  This all fits my way of working so I see no good reason to change from that.
You may feel differently, and I'm certainly not recommending that everyone does the same as me; I am simply saying that all seems to work without any detrimental results when removing all snaps.

---

### Post by zebra2 on 2022-05-07
I hope no one here thinks that Canonical embedded a system as extensive as Snap just to provide UA Kernels and Core and Firefox.  I expect that by time that the next LTS is released if not sooner there will be a new section on this forum called Snap.  It wouldn't hurt to have a shoe box full of workarounds handy for the new users. Actually there is already a good starting collection in this thread.

PS. Then again, it might just fall by the wayside like Unity 8 and Mir.

---

### Post by forcecore on 2022-05-08
I agree with Paddy Landau & DuckHook that do not hate it, but just do not use it and that's it. I hope it really do not become mandatory use and mandatory dependency ever or i would be forced to quit Ubuntu usage at all. Snap must, i repeat must be removable 100% without pulling other system apart.

I for example do not use Firefox at all and use bare Ungoogled Chromium that i downloaded and then extracted(registered as default browser too). Just like on Windows, if i want i extract and run and update when i want.

**Lets hope Canonical sees this and thinks twice for plans to mandate Snaps.**

---

### Post by mathipu on 2022-05-08
This 22.04 has been the worst upgrade for me since, idk, I can't even remember.  A decade?  Snap is a big part of it.  Specifically, the Firefox snap that I dove into.  But other snaps have been a problem too, that I've dealt with as they came up.  None as debilitating as this FF snap.

deb isn't broken for me.  In fact, it's pretty much awesome, mature and one of the joys of using Ubuntu.  I never wanted or needed a user-space package manager.  There's a reason I don't like OSX (many reasons, really).

---

### Post by Paddy Landau on 2022-05-08
> **mathipu said:**
> None as debilitating as this FF snap.
Canonical has messed up with Firefox. It might even be their achilles heel.

---

### Post by grahammechanical on 2022-05-08
> I believe that Canonical is attempting to provide a "Install it and Use  it" OS aimed at the part of the user base that wants an OS option but  doesn't have the technical ability to navigate what we are discussing  here.

It is more than that. The technical term is "immutable operating system." Canonical already have one of these. It is called Ubuntu Core. It does not have a desktop. So, it is not suitable for the user base that you mentioned. On the other hand Fedora are well on the way to providing an immutable desktop operating system. They call it SilverBlue.

> he operating system is delivered in images that are created by utilizing the *[rpm-ostree]("https://rpm-ostree.readthedocs.io/en/latest/")*[ project]("https://rpm-ostree.readthedocs.io/en/latest/"). The main benefits of the system are speed, security, atomic updates and immutability. 

[https://fedoramagazine.org/what-is-silverblue/](https://fedoramagazine.org/what-is-silverblue/)

The Ubuntu philosophy has always been "Ubuntu for humans." So, Ubuntu is already an "install it and use it" distribution. I believe that Canonical are content to put developer time into merging Linux, Debian and Gnome into Ubuntu and spend most to its money on developing Ubuntu for the Internet of Things, Server system, Networking and cloud computing. Read the blog on Ubuntu.com. You won't find much that relates to Ubuntu desktop.

Regards

---

### Post by zebra2 on 2022-05-08
Re post #59
Interesting post there. Thanks! I think we are all dancing around the same pole here. Only differences are personal preferences. I'm well aware of Canonical's IOT aspirations, Ubuntu core and the rest. 

The thing about this snap thread just to keep it here is that they (Canonical) made it about Firefox because they are aware of its wide linux acceptance.  I think they wanted to see what kind of acceptance/resistance they would get on the project. Firefox had to have volunteered to be involved because it had to have the snap port and shut down the deb port for Ubuntu.  If not this then why not just snap everything and be done with it.  Just musing here!

---

### Post by Paddy Landau on 2022-05-08
> **zebra2 said:**
> Firefox had to have volunteered to be involved because it had to have the snap port and shut down the deb port for Ubuntu.
It appears true that Mozilla created the snap ("snap find firefox" shows Mozilla as the verified publisher).

But, Canonical controls Ubuntu's repositories. So, Firefox might not have had a say in removing the DEB.

---

### Post by zebra2 on 2022-05-08
> **Paddy Landau said:**
>  Firefox might not have had a say in removing the DEB.


Agree, but they knew that it was firefox snap or nothing. I don't use firefox and am actually pretty satisfied with the release as it is without it. However this thread is mostly composed of some very competent Ubuntu users that are using workarounds so as to use the firefox deb version and even going to the extreme and removing snap completely. My interest in this is that after using Ubuntu for 13yrs and mostly the dev versions I know that nothing is static and is always in a state of development. If the advanced users in this thread that I do respect have problems with the concept (snap) that is being discussed here in the first place then it is bound to find its way around to me in the second place. Especially since I install the debs myself. At the same time the rank and file and new users may not even have a problem with the snap and possibly not even know that it is a snap in the first place, and no quesion that Canonical knows this. Thats why I am sure the whole snap project is advancing forward and it is what is next not just firefox that is the problem if it is a problem.

---

### Post by kagashe on 2022-05-09
I installed Ubuntu 22.04 and liked it except slow opening of Firefox. I downloaded Firefox from Mozilla and installed it in /opt and created a simlink in /usr/bin
```
$ sudo mv /usr/bin/firefox /usr/bin/firefox-snap
$ sudo ln -s /opt/firefox100/firefox /usr/bin/firefox
```

Then I removed all snap packages and finally snapd
```
$ sudo snap remove --purge firefox
$ sudo snap remove --purge snap-store
$ sudo snap remove --purge gnome-3-38-2004
$ sudo snap remove --purge gtk-common-themes
$ sudo snap remove --purge snapd-desktop-integration
$ sudo snap remove --purge bare
$ sudo snap remove --purge core20
$ sudo snap remove --purge snapd
```
Since removing Firefox snap also removed Firefox launcher I created Firefox Launcher on the Desktop.

Kamalakar

---

### Post by Paddy Landau on 2022-05-09
> **zebra2 said:**
> … the rank and file and new users may not even have a problem with the snap and possibly not even know that it is a snap…
You are probably right about everything, except that new users will have a problem with the snap. They won't know or care that it's a snap, but they will care that it takes so long to open.

Many years ago, when monitors were still connected to mainframes instead of PCs, and IBM was the dominant computer company, IBM researched ideal response times. They concluded that a delay of more than ¼ second was noticed by a user, and thus decided to attempt to reduce all response times to ¼ second.

While modern people have become accustomed to longer response times, generally accepting around 1 or 2 seconds, the Firefox response time of 10 seconds on a fast, modern machine, or much longer for old machines, is far beyond acceptable.

---

### Post by Paddy Landau on 2022-05-09
> **kagashe said:**
> ```
$ sudo mv /usr/bin/firefox /usr/bin/firefox-snap
```
This one step isn't needed, because it will be removed anyway when you purge snap's Firefox.
> **kagashe said:**
> … I downloaded Firefox from Mozilla and installed it in /opt and created a simlink in /usr/bin
How will you ensure that Firefox is kept up-to-date? It must be kept updated because of occasional critical security updates.

You can have Firefox kept automatically updated if, instead of using their DEB, you install their Flatpak version instead. You need to install Flatpak and enable auto-updates. If you don't know how to go about this, let me know and I'll give you the instructions.

---

### Post by zebra2 on 2022-05-09
> **Paddy Landau said:**
> 
While modern people have become accustomed to longer response times, generally accepting around 1 or 2 seconds, the Firefox response time of 10 seconds on a fast, modern machine, or much longer for old machines, is far beyond acceptable.

Yes, 10sec would be a drag.  My Brave browser opens in less than two seconds and actually so does most everything else on my system.  If this is the main complaint then it may have something to do with the slow roll out on Canonical's behalf.  The snap developers may be working on this. It would be irresponsible not to be. 

Thanks for your feed back on all of this. I have 22.10 on my primary machine. I may just put firefox.snap back on that machine and do some testing. 
Incidentally, the fastest OS I have ever used was Ubuntu Maverick. Seemed like everything happened in a click.  Then the next roll out was Natty and so here we are now.

---

### Post by Paddy Landau on 2022-05-09
> **zebra2 said:**
> If this is the main complaint then it may have something to do with the slow roll out on Canonical's behalf.
People have been complaining about snap's slow opening for a long time. This applies to all snap apps. On an older machine with Lubuntu 20.04, it was noticeably bad.

But this Firefox debacle has taken it to a new level.

To clarify, it's only on the first opening after a reboot; thereafter it's fine.
> **zebra2 said:**
> I have 22.10 on my primary machine. I may just put firefox.snap back on that machine and do some testing.
It will be interesting to find out what it's like on 22.10: slower, the same, or faster.

---

### Post by kagashe on 2022-05-09
> **Paddy Landau said:**
> This one step isn't needed, because it will be removed anyway when you purge snap's Firefox.
Yes I know but kept the step in case you decide to keep both versions of Firefox.
> How will you ensure that Firefox is kept up-to-date? It must be kept updated because of occasional critical security updates.
It updates through Help/About_Firefox.

> You can have Firefox kept automatically updated if, instead of using their DEB, you install their Flatpak version instead. You need to install Flatpak and enable auto-updates. If you don't know how to go about this, let me know and I'll give you the instructions.
When you download Firefox from Mozilla it is not .deb but firefox-100.0.tar.bz2 file and you only need to extract the Folder and move it to /opt. I know about how to install Flatpak but it is not needed for Firefox.

---

### Post by vanadium on 2022-05-09
Next to slow initial startup times, there is a keyboard issue with file dialogs. If you hit Ctrl+s to save a web page, first time in a session all is fine. Second time, the file dialog immediately looses keyboard focus after opening. Thus, the file name you are typing after hitting Ctrl+s disappears somewhere else, eventually on the URL bar if that was active before you opened the dialog. This problem is not restricted to Snap. It is common to all containerized formats. 

> **kagashe said:**
> 
It updates through Help/About_Firefox.

You will soon discover you are having the Snap version again. Once there is an update, the APT system will reinstall firefox. That will cause snapd and the snap version of firefox to be reinstalled again. Your link /usr/bin/firefox will be overwritten by the executable for the snap version.

---

### Post by Paddy Landau on 2022-05-09
> **kagashe said:**
> … kept the step in case you decide to keep both versions of Firefox.
If you reinstall the snap version, it will automatically reinstall the link. You absolutely don't need to keep the link.
> **kagashe said:**
> It updates through Help/About_Firefox.
That sounds horribly Windows-like, but you can do it that you way if you like. You'll need to remember to check it daily.
> **kagashe said:**
> I know about how to install Flatpak but it is not needed for Firefox.
True, you can do it your way, if you prefer. It's just easier to install Flatpak, as it's included in the Software Centre and automatic updates.
> **vanadium said:**
> If you hit Ctrl+s to save a web page…
Oof! That sounds awful. This should be reported as a bug.
> **kagashe said:**
> You will soon discover you are having the Snap version again. Once there is an update, the APT system will reinstall firefox.
People are saying this, and yet it hasn't happened to me.

I think that I know why…

I uninstalled the snap version of Firefox, and installed the flatpak system onto my system. Now, in the Software Centre, only the Flatpak version of Firefox is offered; the snap version isn't offered at all.

So, maybe the way to prevent the system from automatically reinstalling snap Firefox is as simple as installing the flatpak system.

When I get a bit of time, I'll check if my hypothesis stands.

---

### Post by zebra2 on 2022-05-09
> **Paddy Landau said:**
> To clarify, it's only on the first opening after a reboot; thereafter it's fine.

Glad you clarified! I just rebooted and it took Brave 20 seconds to fully open to Brave Desktop.  Office and everything else around 10 sec.  After that 2sec for everything. I'm using my 22.04 machine that has a swap file. I will try it in a while on my 22.10 machine that has a swap partition and see if there is a difference.  It sounds like a caching persistence problem to me.  The reason I didn't pickup on this problem is because I have my systems running and awake 24/7.

---

### Post by zebra2 on 2022-05-09
No deal!  22.10 6gig swap partition.  2sec before reboot, 10 sec on first open after reboot. Then back to the 2 sec open. I'll do some more digging.

---

### Post by kagashe on 2022-05-09
> **vanadium said:**
> 
You will soon discover you are having the Snap version again. Once there is an update, the APT system will reinstall firefox. That will cause snapd and the snap version of firefox to be reinstalled again. Your link /usr/bin/firefox will be overwritten by the executable for the snap version.
APT does not know about Firefox installed in /opt for APT Fireofox does not exist on the system so it can't update. By the way I have disabled installation of any snap package and snapd.
create a config file

```
$ sudo gedit /etc/apt/preferences.d/nosnap.pref

```
Paste the following:

    # To prevent repository packages from triggering the installation of snap,
    # this file forbids snapd from being installed by APT.

    Package: snapd
    Pin: release a=*
    Pin-Priority: -10

Save and refresh package cache
```
$ sudo apt update
```
Kamalakar

---

### Post by kagashe on 2022-05-09
> **Paddy Landau said:**
> 
That sounds horribly Windows-like, but you can do it that you way if you like. You'll need to remember to check it daily.
Actually Firefox insalled in /opt updates automatically. I just showed you how. By the way I am using Ubuntu since version 5.04 and used to have /opt version of Firefox and many other apps because Ubuntu was not updating them in time in old versions.

Kamalakar

---

### Post by zebra2 on 2022-05-09
I installed firefox snap on my 22.04 system and it's behavior is the same as everything else.  Slow after first boot, then 2 to 3 seconds. Might just boot my Windows partition and see what happens. Gee! then I'll have to spend half the day installing Windows updates. Forget it!

---

### Post by Dennis N on 2022-05-09
_Re: Automatic updates for the .tar.bz of Firefox from Mozilla_

If you use the .tar.bz from Mozilla for Firefox, it will update itself automatically if you just make yourself the owner of the firefox folder and its files. 
.
_Re: Automatic updates for the Flatpak version of Firefox_

The Flatpak will be automatically updated along with other packages if you use Gnome Software + it's Flatpak plugin instead of Ubuntu Software (which cannot manage Flatpak). 

FWIW, Personally I use the Flatpak version since I install a number of other Flatpaks as well.

---

### Post by poorguy on 2022-05-09
@zebra2 
Your experience with Firefox as a snap is the same as mine slow to open after system restart, then 2 to 3 seconds.

---

### Post by zebra2 on 2022-05-09
> **poorguy said:**
> @zebra2 
Your experience with Firefox as a snap is the same as mine slow to open after system restart, then 2 to 3 seconds.

Yes, and it is the same with the other big apps like libre office apps.  I don't think I will hack my system over this issue.  It is minor to nothing and I'm satisfied with the release.

---

### Post by poorguy on 2022-05-09
Yeah I've been researching AppImage,  Flakpak,  Snaps seems they all have good benefits and bad benefits.

I guess ya just have to check them all out see which fits your needs the best and choose.

AppImage,  Flakpak,  Snaps sound like the cure all to a lot of problems however we'll see anyway they kinda sound like a good idea, guess we'll find out.

---

### Post by zebra2 on 2022-05-09
> **poorguy said:**
>  AppImage,  Flakpak,  Snaps sound like the cure all to a lot of problems however we'll see anyway they kinda sound like a good idea, guess we'll find out.

I think everyone is struggling with the solution for security and since snap is "in house" Ubuntu I don't see any reason to go somewhere else when Im already using Ubuntu. I haven't had a security problem in the 13 years I've been using it with little more than a default firewall.a well disciplined pointer.

---

### Post by kagashe on 2022-05-09
> **Dennis N said:**
> _Re: Automatic updates for the .tar.bz of Firefox from Mozilla_

If you use the .tar.bz from Mozilla for Firefox, it will update itself automatically if you just make yourself the owner of the firefox folder and its files. 

Thanks. When you download and extract you automatically become the owner of the Firefox folder and the files. Although you move the folder to /opt using sudo you still own the folder and the files.

Kamalakar

---

### Post by Paddy Landau on 2022-05-09
> **poorguy said:**
> … AppImage,  Flakpak,  Snaps seems they all have good benefits and bad benefits.
Indeed.

Pros:

[LIST]
[*]No dependency hell.
[*]No searching for PPAs.
[*]Easy to install and uninstall.
[/LIST]
Cons:

[LIST]
[*]You need to set up automatic updates, but that's a one-off. In Ubuntu, it's already done for snaps; flatpaks are easy, and it's more complicated for AppImages.
[*]A surprisingly large amount of extra space, which is a problem for small systems, e.g. IoT and very old hardware.
[*]They use extra resources on the machine, only a problem for systems with low RAM.
[*]You have to add a few extra folders to your backups.
[*]Snaps in particular are slow, excruciatingly so for older hardware. I haven't noticed a significant slowdown for flatpaks and AppImages.
[/LIST]
> **zebra2 said:**
> … using Ubuntu. I haven't had a security problem in the 13 years I've been using it with little more than a default firewall.a well disciplined pointer.
My experience matches yours. Ubuntu's strong points are its usability and solidity (in its LTS versions, at least), which is why it has so many derivatives.

Ubuntu's weak point is Canonical's sometimes-cavalier attitude towards it users. With Unity, it was the deliberate and hard-coded cludge (against all programming standards) to disable legacy icons. In 22.04, its weak point is insisting on a super-slow setup for its default browser.

---

### Post by Dennis N on 2022-05-09
> **kagashe said:**
> Thanks. When you download and extract you automatically become the owner of the Firefox folder and the files. Although you move the folder to /opt using sudo you still own the folder and the files.

Kamalakar

Yes, that's true if you use **sudo mv**. But in case someone used **sudo cp -r**, the owner changes to root, and they would not get the automatic updates until they change the owner.

---

### Post by ajgreeny on 2022-05-09
I am one of the users who downloaded the firefox tar.gz from Mozilla and left it in my Downloads folder as I'm the only single user of the system and all of the firefox folder belongs to me as user.
If an update is available for the FF version a notification appears on screen and asks me to either accept or dismiss the upgrade. If dismissed the notification will appear again at next startup.

If I accept, the new version is downloaded and then a notification quickly appears telling me to restart firefox.
I sometimes dismiss but then, after finishing doing whatever I'm doing, I go to ***Help ->About Firefox*** and immediately accept the upgrade.  This seems to me not unlike the normal manner of updating packages which I do with command line apt update/upgrade daily so there's no need to worry about firefox becoming ouitdated.

---

### Post by #&amp;thj^% on 2022-05-09
> **Paddy Landau said:**
> 

Ubuntu's weak point is Canonical's sometimes-cavalier attitude towards it users.
+1

---

### Post by QIII on 2022-05-09
> **Paddy Landau said:**
> Ubuntu's weak point is Canonical's sometimes-cavalier attitude towards it users.

My opinion is the same.  However, after enough hue and cry from the community they generally get the message.  Better that such alarms were not needed.

---

### Post by poorguy on 2022-05-09
> **ajgreeny said:**
> I am one of the users who downloaded the firefox tar.gz from Mozilla and left it in my Downloads folder as I'm the only single user of the system and all of the firefox folder belongs to me as user.
If an update is available for the FF version a notification appears on screen and asks me to either accept or dismiss the upgrade. If dismissed the notification will appear again at next startup.

If I accept, the new version is downloaded and then a notification quickly appears telling me to restart firefox.
I sometimes dismiss but then, after finishing doing whatever I'm doing, I go to ***Help ->About Firefox*** and immediately accept the upgrade.  This seems to me not unlike the normal manner of updating packages which I do with command line apt update/upgrade daily so there's no need to worry about firefox becoming ouitdated.

I tried that method and when the update from FF99 to FF100 appeared I accepted and did a restart and nothing changed.

What I had in my download folder was 2 Firefox tar.gz folders so I apparently didn't do something the right way.
 To open FF I had to go into my downloads folder and open FF from the extracted files, I never could create a desktop link.

---

### Post by Shibblet on 2022-05-10
Watch in horror as you "apt install chromium," and it installs SnapD first, then uses SnapD to install Chromium.

---

### Post by VMC on 2022-05-10
> **poorguy said:**
> I tried that method and when the update from FF99 to FF100 appeared I accepted and did a restart and nothing changed.

What I had in my download folder was 2 Firefox tar.gz folders so I apparently didn't do something the right way.
 To open FF I had to go into my downloads folder and open FF from the extracted files, I never could create a desktop link.

poorguy, follow this link. That's what I use:
[https://support.mozilla.org/en-US/kb/install-firefox-linux#w_install-firefox-from-mozilla-builds-for-advanced-users](https://support.mozilla.org/en-US/kb/install-firefox-linux#w_install-firefox-from-mozilla-builds-for-advanced-users)

---

### Post by zebra2 on 2022-05-10
If Ubuntu 22.04 see's a snap it eyes will light up and the snap will install. Oh! snap! forget it!

---

### Post by poorguy on 2022-05-10
> **VMC said:**
> poorguy, follow this link. That's what I use:
[https://support.mozilla.org/en-US/kb/install-firefox-linux#w_install-firefox-from-mozilla-builds-for-advanced-users](https://support.mozilla.org/en-US/kb/install-firefox-linux#w_install-firefox-from-mozilla-builds-for-advanced-users)

Thanks for the link I give it a try tomorrow.


Thanks again

---

### Post by Paddy Landau on 2022-05-11
> **Shibblet said:**
> Watch in horror as you "apt install chromium," and it installs SnapD first, then uses SnapD to install Chromium.
That's interesting. I popped into my Ubuntu 22.04 system, where I've uninstalled Firefox and I've installed the flatpak system.

[LIST]
[*]When I open Software, it gives me only one option to install Firefox: The flatpak version. If I use it, it installs Firefox (flatpak).
[*]But, apt list firefox shows that Firefox would be a snap. (You can also see this in Synaptic Package Manager.)
[*]So, if use [FONT=courier new]apt install firefox[/FONT], it installs Firefox (snap).
[/LIST]
The same applies to Chromium; the Software GUI offers only the Flatpak version, whereas apt installs the snap.

I now 100% concur that Canonical has handled this in a poor way. Apps should not default to a system that causes users frustration through lengthy waits.

The workaround to this is not to uninstall snap itself (there is the occasional package that's unavailable on DEB or Flatpak, but is available on snap). The best workaround is:

[LIST=1]
[*]Uninstall the snap version of Firefox
[*]Install the flatpak system
[*]Allow non-technical users to install packages via the Software GUI, and install Firefox that way (or using the command line)
[*]Technical users install packages using whichever method they like
[/LIST]
It's a bit of a mess.

What is the best way to feedback to Canonical that the snap system isn't ready for prime time?

---

### Post by Dennis N on 2022-05-11
> That's interesting. I popped into my Ubuntu 22.04 system, where I've uninstalled Firefox and I've installed the flatpak system.

    When I open Software, it gives me only one option to install Firefox: The flatpak version. If I use it, it installs Firefox (flatpak)...

I think you overlooked the 2nd Firefox in (Gnome) Software. See the attachment. The red arrow is the Flatpak, the green arrow is the Snap.

---

### Post by Paddy Landau on 2022-05-11
> **Dennis N said:**
> I think you overlooked the 2nd Firefox in (Gnome) Software.
You're right, I did! My screen looks a little different. The first, "Firefox", is flatpak only, while the the second, "firefox-kiosk", and the third, "firefox", are snap only.

It's good that the top result is flatpak.

---

### Post by lammert-nijhof on 2022-05-13
The whole discussion about snaps is ridiculous, just another way to participate in the most popular Linux hobby: Hating Canonical. 

I'm happy with snaps, I use it on Ubuntu 16.04 ESM to have the latest Firefox and LibreOffice available. Snaps have a disadvantage, the first load takes too much time! But so does the preceding action booting the system. Besides most people will keep their browser loaded during the whole session having many tabs open. Loading Firefox the second time on my Ryzen 3 2200G takes 1 to 4 seconds and that 4 seconds I did measure in an Xubuntu VBox VM. 

The complaints about the snap updates is BS. I used the snap refresh and the upgrade on Ubuntu 16.04 ESM to Firefox 100 did take a few seconds, because only the binary difference with the previous version will be sent. The storage for those 3 versions/snapshots  is also limited, because only the binary differences between the snapshots will be stored. If for some reason you don't like the update, you can roll it back locally in a second. 

Educate yourself before you start complaining and participating in the most popular Linux hobby.

---

### Post by DuckHook on 2022-05-13
:)

I do see where you are coming from. But:

[LIST=1]
[*]It's a discussion thread, so it's okay to let our hair down on this topic,
[*]Hey, we're geeks. We have a reputation to uphold. If we didn't gripe about this, what else would we gripe about? :)
[/LIST]
Seriously though: there are legitimate issues with snaps. And while I don't *hate* snaps, I do find them irritating. I think the issues raised against them on this thread are all valid.

I'm truly happy for you that love snaps. I don't, but that's okay too. I suppose that our freedom to disagree over such a harmless topic is what adds to life's infinite variety.

BTW, the auto update issue is not BS. There needs to be finer grained control given to users. Auto updating is not a "feature". It is a drawback. I have been burned by apps that auto updated and could not be rolled back because part of the update process involved subtle changes to the accompanying info database that could not be undone. Upgrading was a one&#8209;way process—a real problem when you have multiple workstations sharing the same database.

Additionally, I would note that most of the people complaining are very knowledgeable about Linux, Ubuntu and snaps. In fact, many complaints are motivated by that very knowledge.

I do get your concern about general Ubuntu bashing though. We've had a number of recurring spells of that sort over the years.

---

### Post by poorguy on 2022-05-13
> **DuckHook said:**
> 
Hey, we're geeks. We have a reputation to uphold. If we didn't gripe about this, what else would we gripe about? :)


Hmm Nvidia comes to mind.

---

### Post by DuckHook on 2022-05-13
> **poorguy said:**
> Hmm Nvidia comes to mind.
[https://developer.nvidia.com/blog/nvidia-releases-open-source-gpu-kernel-modules/](https://developer.nvidia.com/blog/nvidia-releases-open-source-gpu-kernel-modules/)

nVidia users should be very happy.

---

### Post by QIII on 2022-05-13
> **lammert-nijhof said:**
> Hating Canonical.

I'm not sure who here is expressing that sentiment.

---

### Post by poorguy on 2022-05-13
> **DuckHook said:**
> [https://developer.nvidia.com/blog/nvidia-releases-open-source-gpu-kernel-modules/](https://developer.nvidia.com/blog/nvidia-releases-open-source-gpu-kernel-modules/)

nVidia users should be very happy.

Not really leaves us old Nvidia graphics card user out in the cold.*** Disappointing is how I see it.***
[URL="https://www.howtogeek.com/805004/nvidia-releases-open-source-linux-gpu-drivers-with-a-catch/"]https://www.howtogeek.com/805004/nvidia-releases-open-source-linux-gpu-drivers-with-a-catch/
[/URL]
**A Long Road Ahead**

 ***The open-source driver release might be disappointing for some,  especially for anyone still using older Nvidia graphics cards that  aren&#8217;t supported ([it has been a bit difficult to buy a new graphics card lately]("https://www.howtogeek.com/726236/why-is-it-so-hard-to-buy-a-graphics-card-in-2021/")). *** *However, this is an important step in the right direction, if only  because companies like Canonical and Red Hat have the opportunity to  help improve Nvidia&#8217;s code for the first time ever.*

---

### Post by poorguy on 2022-05-13
***My apologies ***for being facetious and going off topic don't want to get into trouble or make anyone mad.

---

### Post by Paddy Landau on 2022-05-14
> **lammert-nijhof said:**
> The whole discussion about snaps is ridiculous, just another way to participate in the most popular Linux hobby: Hating Canonical. 
…
I'm happy with snaps, I use it on Ubuntu 16.04…
There's the problem. I used to be happy with snaps, very happy indeed. But there has been a sea change in Ubuntu 22.04. It's no longer the same.

So, when you say…
 > **lammert-nijhof said:**
> Educate yourself before you start complaining…
I'll bounce that right back onto you.
> **QIII said:**
> I'm not sure who here is expressing that sentiment.
Not here, but you should see Reddit. The hate is sometimes extraordinary!

---

### Post by ajgreeny on 2022-05-14
> **lammert-nijhof said:**
> The whole discussion about snaps is ridiculous, just another way to participate in the most popular Linux hobby: Hating Canonical. 

I'm happy with snaps, I use it on Ubuntu 16.04 ESM to have the latest Firefox and LibreOffice available. Snaps have a disadvantage, the first load takes too much time! But so does the preceding action booting the system. Besides most people will keep their browser loaded during the whole session having many tabs open. Loading Firefox the second time on my Ryzen 3 2200G takes 1 to 4 seconds and that 4 seconds I did measure in an Xubuntu VBox VM. 

The complaints about the snap updates is BS. I used the snap refresh and the upgrade on Ubuntu 16.04 ESM to Firefox 100 did take a few seconds, because only the binary difference with the previous version will be sent. The storage for those 3 versions/snapshots  is also limited, because only the binary differences between the snapshots will be stored. If for some reason you don't like the update, you can roll it back locally in a second. 

Educate yourself before you start complaining and participating in the most popular Linux hobby.
Have you ever tried rolling back to a previous version of firefox after already having started a higher version?

You can not do so using the same older profile as Firefox does not allow that, or not without considerable palaver forcing it to do so which would mean many users losing all their bookmarks and extensions, etc, etc.

To many "non-geek" users that would be a disaster!

---

### Post by Paddy Landau on 2022-05-14
> **ajgreeny said:**
> Have you ever tried rolling back to a previous version of firefox after already having started a higher version?

You can not do so using the same older profile as Firefox does not allow that…
Well, that would be on Firefox, not on Ubuntu nor on snaps.

Besides, you are strongly advised against going backwards in the browser versions (Firefox and all Chromium browsers) because of the frequent vital security updates.

---

### Post by ajgreeny on 2022-05-14
> **Paddy Landau said:**
> Well, that would be on Firefox, not on Ubuntu nor on snaps.

Besides, you are strongly advised against going backwards in the browser versions (Firefox and all Chromium browsers) because of the frequent vital security updates.

I totally agree with your second point but I'm not sure what you mean by the first. However, lamert was suggesting that you can simply roll back to an earlier snap version if you do not like the newer snap version; is that possible using an existing profile?

I suspect not, but having never used a snap version of firefox I really don't know the answer to that.

---

### Post by TenPlus1 on 2022-05-14
Canonical should have held a poll before replacing key apps with snaps to see if the users actually wanted them.  A lot of the hate I see is not only from the slow loading and bloated filesizes, but the fact that each snap uses it's own libraries instead of shared which means more memory usage, as well as the propriatary underlay of the format.

I for one would welcome .deb's for all my apps and the well adopted flatpak as a close second.  Snaps should have really been a server only thing.

---

### Post by zebra2 on 2022-05-14
> **TenPlus1 said:**
> Canonical should have held a poll 

They already did the poll. If you are running 22.04 then you voted yes.  For my self, I switched to 22.10.  Right now, keeping my experience in quiet mode.  Re: Snap, Canonical has control of the updates on their own servers so that system will probably be smoothed out in time.  I have never used a release LTS or DEV that didn't have incomplete projects. LTS doesn't stand for "finished". Just look at Unity when it was released with Natty and all of the highchair banging over the demise of Gnome 2. When it was done there was a equal highchair banging with the demise of Unity and the switch to Gnome 3. I thought that Gnome was clunky and immature but Gnome and Canonical developed it into something that I can live with.  Jammy is a decent release with some incomplete projects (for sure). Be patient, couple of years from now you won't remember what today's problems were. 

PS. Or Not!

---

### Post by poorguy on 2022-05-14
> **Paddy Landau said:**
>  But there has been a sea change in Ubuntu 22.04. It's no longer the same.

You hit the nail on the head and it just ain't Snap a lot of things seem to not be the same and no I didn't write them down when I noticed them just mainly some of the settings in some of the software such as LibreOffice and others.

I'm using Lubuntu 22.04 and it sure has and still is taking some getting used to yeah it sure ain't the same as the previous versions of Lubuntu.


I use old outdated under powered computers so I expect Snaps to open a bit slower the first time after a system restart and I'm wondering if those of you with newer high powered computers experience the same slowness of Snaps opening for the first time after a system restart.

---

### Post by #&amp;thj^% on 2022-05-14
> **zebra2 said:**
> Be patient, couple of years from now you won't remember what today's problems were. 

**PS. Or Not!**
:lolflag:
As I age I lose my snap. ;)

---

### Post by poorguy on 2022-05-14
> **1fallen said:**
> :lolflag:
As I age I lose my snap. ;)

Me to. :lol:

---

### Post by Paddy Landau on 2022-05-14
> **poorguy said:**
> I use old outdated under powered computers … I'm wondering if those of you with newer high powered computers experience the same slowness of Snaps opening for the first time after a system restart.
I have a modern computer. On 20.04, the extra opening time was barely noticeable. But on 22.04, it's unacceptable. Something significant has changed. In future, I shall avoid snaps unless I have no reasonable alternative.

If you use low-spec computers, Ubuntu isn't really for you. I'd recommend a lighter derivative; I usually use Lubuntu for old computers. Lubuntu isn't as pretty, but it's solid, and uses way less RAM than Ubuntu does, plus less fancy graphics, which makes it noticeably faster.

Lubuntu is the lightest official derivative. To the best of my knowledge, Bodhi is the only (unofficial) derivative that's lighter still, albeit not by much.

---

### Post by DuckHook on 2022-05-14
> **ajgreeny said:**
> Have you ever tried rolling back to a previous version of firefox after already having started a higher version?

You can not do so using the same older profile as Firefox does not allow that, or not without considerable palaver forcing it to do so which would mean many users losing all their bookmarks and extensions, etc, etc.

To many "non-geek" users that would be a disaster!
I second your observation that FF is one of those apps that one cannot easily roll back to an earlier version. When I tried it on a .deb upgrade, the database automatically updated too, and changed enough that earlier versions of FF could not map to it. FF ended up creating a new profile and I had to spin up a VM to prep my old database and convert it. I don't see how that dynamic would be different just because FF is now a snap.

Were this only FF, I could actually live with it. But the same dynamic will apply to other apps too. They won't be as easy to recover from. I had this happen on GnuCash. In my case, that is a far more "critical" app. It may not be in daily use, but when I need it, I *really* need it. It must have a dependable, predictable and uncorrupted database. I had to restore from backups on that occasion. That is a terrible outcome for mission&#8209;critical apps and would have been even more of a disaster than some browser bookmarks and extensions. It would definitely be enough to sour a general user on using Ubuntu.

All in all, the idea of uncontrollable upgrades is a bad one. One of Linux's most important strengths has traditionally been the level of control that it has given to users. One could even apt-mark a package with *hold* (though this invited apt breakage). The overly automated default behaviour of snaps contains a lot of hidden land mines.

---

### Post by DuckHook on 2022-05-14
> **Paddy Landau said:**
> Lubuntu is the lightest official derivative. To the best of my knowledge, Bodhi is the only (unofficial) derivative that's lighter still, albeit not by much.
Bodhi is a great distro. Since I retired my really old laptop, I haven't used Bodhi for going on a couple of years, but it is slick, fast and (not least) surprisingly pretty. In my opinion, it looks a lot nicer than Lubuntu. The main thing that kept me from changing all of my older equipment over to it was the minor ways in which it didn't quite map to the Canonical repos. Midori was not available in the Canonical repos at the time, so this ended up being installed from Bodhi's own repos. I don't quite remember what problems this raised, but I do remember some problems, probably of the typical "mixing repos" kind.

---

### Post by Paddy Landau on 2022-05-14
> **DuckHook said:**
> Bodhi … is slick, fast and (not least) surprisingly pretty. In my opinion, it looks a lot nicer than Lubuntu.
Unquestionably. Lubuntu is solid, but it won't win awards for beauty!

I've never used Bodhi apart from experimentation, because (for convenience) I stick to the official Ubuntu derivatives. But it's good to know that Bodhi works well.

I see that Bodhi tends to be a little behind Ubuntu in its releases, which is fine.

When it comes to a 32-bit version for the seriously old computers, though, it looks as though Bodhi will no longer cut it. Such people will soon have to forego Ubuntu derivatives and move to Debian or Fedora, I think.

---

### Post by DuckHook on 2022-05-14
> **ajgreeny said:**
> I totally agree with your second point but I'm not sure what you mean by the first.
I think what Paddy is saying is that if Mozilla designs FF to be so brittle as to reject user databases once they have been run on newer versions, then the blame for such fragility lies with Mozilla and not with Canonical. He has a point there. I get the need for browser currency and updating religiously, but does the database itself need to be a one&#8209;way valve? At the very least, Mozilla's devs should apply such restrictions more judiciously:

[LIST=1]
[*]Make it irrevocable only if the upgrade involves an actual database layout change
[*]When such a case occurs, give fair warning to the user that the upgrade will change their profile irrevocably
[/LIST]
In the case of FF, this irrevocability exists whether the user is using .debs or snaps, so there is no difference either way.

In short, this is a Mozilla problem, not a snap problem.
> **Paddy Landau said:**
> When it comes to a 32-bit version for the seriously old computers, though, it looks as though Bodhi will no longer cut it. Such people will soon have to forego Ubuntu derivatives and move to Debian or Fedora, I think.
Very true. It's the dilemma in relying on the Canonical repos. Bodhi gets the benefit of Canonical doing the heavy lifting, but are at the mercy of Canonical's corporate direction. If Canonical decides to drop 32-bit support, Bodhi has to go along.

I have only one 32-bit machine left on my LAN, but it's one I would be reluctant to retire. It's an old thin client that just sips wattage and does its myriad jobs silently and dependably. I have until next year before I have to make a decision, at which point, I will either retire it or switch to Debian. Neither alternative is much to my liking, but there's no point in my griping about it. We faced the same issues when the world moved from 16-bit to 32-bit HW although, to be fair, the transition this time is less of a paradigm shift: unlike the last shift, 64-bit has not rendered 32-bit obsolete because 32-bit is still quite capable for all sorts of usage.

---

### Post by Frogs Hair on 2022-05-14
Have only used the same handful of snaps since the came and have had no problems. I have used FF ESR via ppa for some time now so not a problem yet.

---

### Post by DuckHook on 2022-05-14
> **Frogs Hair said:**
> I have used FF ESR via ppa for some time now so not a problem yet.
That's been my strategy too. I think you may even have been the one who taught me. (Can't remember—memory like a sieve these days.)

My only snap reliance is LXD, but it has become mission&#8209;critical, so I'm stuck with snapd. Apart from that, I have no other snap app installed.

It makes no sense to me to have a whole platform installed just to run another platform, but Canonical decided that this would be the only way. In the "old days" there was a distinction that, to my mind, is both logical and simple: a platform runs on the base OS. Apps that use that platform would then run on the platform. It's a simple hierarchy.

But nowadays, platforms on top of platforms on top of platforms just seems increasingly fragile and rickety to me. Example, it is possible to run KVM within LXD on top of snapd. I haven't tried this, but here's a [tutorial describing how]("https://blog.simos.info/how-to-run-a-windows-virtual-machine-on-lxd-on-linux/"). Erh… okay… how many such nestings can we get away with before the whole edifice becomes too fragile to be reliable? Then again, lots of people run platforms within cloud VMs, and what is that but multiple nesting layers too?

---

### Post by Frogs Hair on 2022-05-14
> But nowadays, platforms on top of platforms on top of platforms just  seems increasingly fragile and rickety to me. Example, it is possible to  run KVM within LXD on top of snapd. I haven't tried this, but here's a [tutorial describing how]("https://blog.simos.info/how-to-run-a-windows-virtual-machine-on-lxd-on-linux/").  Erh&#8230; okay&#8230; how many such nestings can we get away with before the whole  edifice becomes too fragile to be reliable? Then again, lots of people  run platforms within cloud VMs, and what is that but multiple nesting  layers too?              


I have setup win7 pro in VB on top of Zorin, but there is no reason to use unsupported operating systems.My VB usage consists trying different distros, so I think you're a bit over my head. I dual boot Win 11 and Linux on different drives so I don't have to jump through hoops to get various software to work and some never will. I have avoided wine and all of its derivatives some of which are flatpak.

---

### Post by #&amp;thj^% on 2022-05-14
I'm just thankful for Mark and the gang, so many contributions over the years they given to the world of Linux computer OS's.
But sometime it just takes a bit of patience for the recipe to get measured with just the right amount of gives and takes.
Yep right now I'm still waiting. :)

---

### Post by DuckHook on 2022-05-14
> **Paddy Landau said:**
> Unquestionably. Lubuntu is solid, but it won't win awards for beauty!
Re&#8209;reading your post, it occurred to me that this passage may very well describe me! Betcha didn't know that my middle name is "Lubuntu". :p
> **Frogs Hair said:**
> I have setup win7 pro in VB on top of Zorin, but there is no reason to use unsupported operating systems.My VB usage consists trying different distros, so I think you're a bit over my head. I dual boot Win 11 and Linux on different drives so I don't have to jump through hoops to get various software to work and some never will. I have avoided wine and all of its derivatives some of which are flatpak.
I doubt that anything goes over your head.

Your usage isn't really that different from mine. Substitute LXD for VBox and they are pretty much identical. The nesting I'm talking about would be like running, say, VMWare within VBox. AFAIK, this isn't possible with VMs, but it *is* possible with containers (which is yet another reason I like containers).

I use VMs to test drive distros too, but I find them too limiting when it comes to sandboxing apps. More secure but less flexible. For example, if I install one of the 'buntus in a VM then use LibreOffice for the purpose of secure document manipulation, it will perform that function well, but it becomes a pain to port LibreOffice and associated docs to another computer. Not impossible, but a pain. With containers, it's a piece of cake (once initially set up properly, which is another story altogether).

I can run WINE within a container and it's as fast as running it on bare metal. But, again, it's one platform (WINE) on top of another (LXD) on top of a third (snapd) on top of the bare metal. I can't help but wonder if such a long chain of platform layers increases brittleness. OTOH, no problems so far, so that's reassuring.
> **1fallen said:**
> I'm just thankful for Mark and the gang, so many contributions over the years they given to the world of Linux computer OS's.
But sometime it just takes a bit of patience for the recipe to get measured with just the right amount of gives and takes…
…and I think that's part of what motivated lammert-nijhof to post his remarks. Though I think the members here aren't of the sort he is criticizing, I do sympathize with his feelings.

Canonical has given us a lot over the years. Sometimes, we lose sight of how lucky we are when discussing its shortcomings. These folks have delivered an incredible product that continues to improve in general. Despite its lapses, Ubuntu provides phenomenal usability especially given that it runs on a FOSS model. It is far more powerful, flexible, capable and secure than the two big proprietary OSes. It is therefore discouraging when some people who derive so much benefit from it take to vehemently and indiscriminately bashing it.

Thanks for reminding us of Canonical's contributions. It's useful to keep the overall awesomeness of this distro in mind even when critiquing it.

---

### Post by Paddy Landau on 2022-05-15
> **DuckHook said:**
> The nesting I'm talking about would be like running, say, VMWare within VBox. AFAIK, this isn't possible with VMs…
It is possible; I've done it. I only use VirtualBox (because it's simpler, even though QEMU/KVM is faster), and in VB you set the option System > Processor > Enable Nested VT-x/AMD-V. Someone on another forum said that they have done it on QEMU/KVM. Of course, the efficiency is not good!
> **DuckHook said:**
> … it becomes a pain to port LibreOffice and associated docs to another computer.
Regarding the documents, why don't you just use a shared folder with the host computer? Then it becomes easy to port it on, say, a USB stick or via the network.

Regarding LibreOffice, I don't understand why you have to port it instead of just installing it on the other computer?
> **DuckHook said:**
> I can't help but wonder if such a long chain of platform layers increases brittleness.
You seem to be unaware of the long chain of layers that already exists in a standard computer. Hardware at the bottom, then firmware, then BIOS or equivalent, and quite a few layers before you even get to your keyboard and screen. Further layers still to get to your GUI.

Is it brittle? When you think about all of those layers, it does seem extraordinary that the whole thing doesn't come crashing down! For the success, we have to thank very many designers, developers and maintainers over many years.
> **DuckHook said:**
> Thanks for reminding us of Canonical's contributions. It's useful to keep the overall awesomeness of this distro in mind even when critiquing it.
I second this.

---

### Post by exploder on 2022-05-15
The only snap I have any real issues with is Firefox. I only have issues in a Wayland session, using x11 the browser works fine. I have supported hardware, AMD RX 560 graphics but Firefox goes crazy on certain sites, Facebook, YouTube for example and it crashes often! I switched back to x11 and other than slow starting the browser has been fine.

---

### Post by DuckHook on 2022-05-15
> **Paddy Landau said:**
> It is possible; I've done it. I only use VirtualBox (because it's simpler, even though QEMU/KVM is faster), and in VB you set the option System > Processor > Enable Nested VT-x/AMD-V. Someone on another forum said that they have done it on QEMU/KVM. Of course, the efficiency is not good!
I didn't know this! Thanks for sharing. Not that I would put it to real world use (I find the performance hit from one layer alone to be irritating enough) but I am curious and will try it out sometime, just for kicks and giggles.
> Regarding the documents, why don't you just use a shared folder with the host computer? Then it becomes easy to port it on, say, a USB stick or via the network.

Regarding LibreOffice, I don't understand why you have to port it instead of just installing it on the other computer?
The power of such porting comes when you start customizing. My LibreOffice setup is customized enough that duplicating it on four or five different machines is a royal pain. That's what I used to do, and it was always frustrating to have to remember the myriad customizing steps only to screw up one or two and then faced with debugging the problem. Similarly, saving docs onto the /home directory has limitations too. To port such docs, I would either have to sneaker&#8209;net from one machine to another or use some form of network exchange that needs to be set up and taken down (if I want minimal residual attack surface). By contrast, cloning a LXD container is truly effortless: a short one&#8209;liner that passes only the deltas. It can be done securely over the internet with key certificates, although I only do so over my LAN (my infamous paranoia at work there).

The ease and utility of LXD containers really have to be experienced to be fully appreciated. Because cloning is so easy, I can (and do) schedule my clones daily into a mirror machine that I use as my desktop backup. By [i]not[/[i] hiving off my docs to an outside directory, they get cloned too. When this ease of use is multiplied by the other apps and files that I do likewise with (browser settings, games and their save files, media playlists, etc) the time and energy savings are not only significant but highly stress reducing.

MS tried something similar decades ago. I believe they called it a "suitcase". It never achieved liftoff because the technology of the time wasn't ready and, not least, because MS is all thumbs when it comes to hard core geek implementations, but it's now easy to do (though *not* easy to set up) in Linux through the use of containers.
> You seem to be unaware of the long chain of layers that already exists in a standard computer. Hardware at the bottom, then firmware, then BIOS or equivalent, and quite a few layers before you even get to your keyboard and screen. Further layers still to get to your GUI.

Is it brittle? When you think about all of those layers, it does seem extraordinary that the whole thing doesn't come crashing down! For the success, we have to thank very many designers, developers and maintainers over many years.
True enough. I just tend to think of existing layers as proven whereas the snap&#8594;LXD&#8594;VM&#8594;platform&#8594;app chain is newer and more suspect. But it really isn't any more suspect than what you alluded to, especially when the bugs are worked out. More of my paranoia at work, I guess.

---

### Post by Paddy Landau on 2022-05-15
> **DuckHook said:**
> … I am curious and will try it out sometime, just for kicks and giggles.
If you have a machine with a load of RAM, you could, for fun, see how many levels deep you can get!
> **DuckHook said:**
> The ease and utility of LXD containers really have to be experienced to be fully appreciated.
I know nothing about containers other than that they exist. I've tried looking it up before, but I don't recall why I didn't take it further; I might have been too busy at the time.

---

### Post by VMC on 2022-05-15
> **DuckHook said:**
> Bodhi is a great distro. Since I retired my really old laptop, I haven't used Bodhi for going on a couple of years, but it is slick, fast and (not least) surprisingly pretty. In my opinion, it looks a lot nicer than Lubuntu. The main thing that kept me from changing all of my older equipment over to it was the minor ways in which it didn't quite map to the Canonical repos. Midori was not available in the Canonical repos at the time, so this ended up being installed from Bodhi's own repos. I don't quite remember what problems this raised, but I do remember some problems, probably of the typical "mixing repos" kind.

With your recommendation, I downloaded Bodhi, and it surly is beautiful. I do have Lubuntu installed but rarely use it. I think I will replace with Bodhi.

---

### Post by DuckHook on 2022-05-15
> **Paddy Landau said:**
> I know nothing about containers other than that they exist. I've tried looking it up before, but I don't recall why I didn't take it further; I might have been too busy at the time.
Perhaps because of how arcane and obscure it is? Once working, they are a dream, but getting there is like undergoing a root canal. At least, that's how I felt. If you are curious, take a look at the link in my sig. I need to change that tutorial a bit. The instructions on there are currently obsolete, but it will give you an idea of the steps involved.

---

### Post by DuckHook on 2022-05-15
> **VMC said:**
> With your recommendation, I downloaded Bodhi, and it surly is beautiful. I do have Lubuntu installed but rarely use it. I think I will replace with Bodhi.
Just be aware that it does have some differences with Ubuntu. For one thing, you will have to rely on Bodhi's forums for help rather than Ubuntu's. Last time I checked (years ago) they were not too active.

Also, as Paddy points out, Bodhi will have to migrate to 64-bit in short order. If you are installing for the sake of 32-bit support, then you may be better off going to something with a longer shelf life.

---

### Post by QIII on 2022-05-15
I can't find the post where it was mentioned (I admit I didn't look too hard!), but 32 bit Bodhi is legacy only.  The current supported releases are 64 bit.  Jeff was finally persuaded that his "32 bit forever" stance was just not realistic.

---

### Post by VMC on 2022-05-15
Yes, I got the 64bit Bodhi, and yes their forums are a far cry from Ubuntu's.

---

### Post by DuckHook on 2022-05-15
> **VMC said:**
> Yes, I got the 64bit Bodhi, and yes their forums are a far cry from Ubuntu's.
You are clearly well versed. Enjoy Bodhi. After you explore it a bit, tell us what you think.

---

### Post by Paddy Landau on 2022-05-16
> **DuckHook said:**
> … getting there is like undergoing a root canal.
I opened a VM to test this, and followed your steps from *Installation* to *Installing Firefox*. You're right about it being an extensive process!

Yes, the instructions are a tad out of date, but I worked around those bits. For example, I loaded Ubuntu 22.04 instead of 18.04, and observed that the Firefox installation used the snap version (no surprise there).

I noticed three small points for when you want to update the instructions:

[LIST]
[*]In *Configuring the LXD profile*, in [FONT=courier new]nano /home/duckhook/bin/x11.profile[/FONT], you can replace [FONT=courier new]/home/duckhook[/FONT] with [FONT=courier new]~[/FONT].
[*]In *Configuring the LXD profile*, [FONT=courier new]sudo reboot[/FONT] leaves you logged out, so you need to log in again before going to the next step. Otherwise, if  you don't notice, you end up doing the next steps on your primary machine instead of within LXD.
[*]In *Installing Firefox*, Firefox didn't require installing [FONT=courier new]libcanberra-gtk-module[/FONT] and [FONT=courier new]libcanberra-gtk3-module[/FONT]. The terminal threw a couple of errors, but it still worked. For fun, I installed the latter; nothing significant changed. I then installed the former. I needed to [FONT=courier new]sudo reboot[/FONT] before Firefox would work. It did work, but the terminal threw pages and pages of errors! So, that might need looking at.
[/LIST]
Thank you. I've bookmarked your instructions.

Question: What is the difference between LXD and Docker? Are they different concepts, or the same concept implemented differently? This is an area that I still find confusing. (I haven't tried Docker.)

---

### Post by Shibblet on 2022-05-16
> **lammert-nijhof said:**
> The whole discussion about snaps is ridiculous, just another way to participate in the most popular Linux hobby: Hating Canonical. 
Speaking for myself, I do not hate Canonical.  But you may need to be informed about what Hate actually is...  Hate is not constructive.  Most of the discussions on this forum are to find out how things work, and what can be changed for the better.  

> **lammert-nijhof said:**
> I'm happy with snaps, I use it on Ubuntu 16.04 ESM to have the latest Firefox and LibreOffice available. Snaps have a disadvantage, the first load takes too much time! But so does the preceding action booting the system. Besides most people will keep their browser loaded during the whole session having many tabs open. Loading Firefox the second time on my Ryzen 3 2200G takes 1 to 4 seconds and that 4 seconds I did measure in an Xubuntu VBox VM. 
I'm not happy with some of the aspects of Snaps.  They, of course, need refinement.  I do, however, see their potential.

> **lammert-nijhof said:**
> The complaints about the snap updates is BS. I used the snap refresh and the upgrade on Ubuntu 16.04 ESM to Firefox 100 did take a few seconds, because only the binary difference with the previous version will be sent. The storage for those 3 versions/snapshots  is also limited, because only the binary differences between the snapshots will be stored. If for some reason you don't like the update, you can roll it back locally in a second. 
So, exactly where should we go to discuss issues with Snaps?  Call Canonical directly on the phone?  "I want to speak with Mark Shuttleworth RIGHT NOW!"  No, of course not, we come to the Ubuntu Forums.  Primarily to see if there is anything we are doing wrong, and then secondly to find out what can be done, or change about it.

> **lammert-nijhof said:**
> Educate yourself before you start complaining and participating in the most popular Linux hobby.
Perhaps we should educate ourselves by going to a web-site where many people who use the same OS are available to help... What do you think?

---

### Post by DuckHook on 2022-05-16
> **Paddy Landau said:**
> I opened a VM to test this…
Your analysis is much appreciated!

I will get around to updating the tutorial and make it applicable to Jammy soon. In addition to your contributions, I've found that it needs a few further tweaks too.
> …What is the difference between LXD and Docker? Are they different concepts, or the same concept implemented differently? This is an area that I still find confusing. (I haven't tried Docker.)
Since I don't use Docker either, I also can't compare it to LXD, so, for what follows, I hope someone familiar with Docker can correct my mistakes. I don't want to leave the impression that I have any real expertise in containers (because I don't) but AFAIK, the main differences between LXD and Docker are as follows:

[LIST=1]
[*]Docker is intended for non-persistent use cases whereas LXD is designed for persistence. I take this to mean that Dockers are designed to spin up a fresh pristine environment with every boot whereas LXD will pick up where it left off when last closed.
[*]Docker is far more widely used than LXD. LXD is like snapd in the sense that it is driven by Canonical and not widely adopted outside of Ubuntu. I do believe, however, that it is available in RH repos and others as well.
[*]Docker is versatile enough to run on many different file systems. LXD really, really wants to use ZFS and only ZFS. Some consider this a limitation—understandably so—but I found it to be tolerable. In fact, it motivated me to switch a number of machines to ZFS which has, on the whole, proven beneficial due to ZFS's enhanced feature set over EXT4.
[*]Due to its wider usage, Docker offers a lot of preconfigured platforms that bypass the need for tedious setups. I believe that there are Docker images for Wordpress, email servers and webservers that one can download and run with just a bit of customization. I don't know how people can just trust such prebuilt servers, but that's another subject for another day. I am not aware of such prebuilt images for LXD. However, this may very well be due to my ignorance.
[/LIST]
To recapture some semblance of the original topic, LXD is only available as a snap. I haven't experienced any problems with it being such, but then, I use it only in a mainstream fashion without a lot of unusual demands. When it comes to LXD, snaps have not been a problem for me.

---

