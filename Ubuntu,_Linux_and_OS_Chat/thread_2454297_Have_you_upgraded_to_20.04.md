---
title: "Have you upgraded to 20.04?"
date: 2020-11-26
forum: Ubuntu, Linux and OS Chat
---

### Post by michael351 on 2020-11-26
Have you upgraded to 20.04?

Did you use 'do-release-upgrade' or
perform a clean install?

I have tried upgrading from 18.04 to 20.04 and have been unsuccessful.
Just curious how others have upgraded.

---

### Post by CelticWarrior on 2020-11-26
I almost always perform a clean install.

---

### Post by deadflowr on 2020-11-26
*Thread moved to **Ubuntu, Linux and OS Chat***

---

### Post by tea for one on 2020-11-26
Clean install every two years with LTS version.

---

### Post by CatKiller on 2020-11-26
I've moved one of my computers up to 20.04. I'll upgrade my HTPC when I get round to it, and my desktop when I've emotionally committed to saying goodbye to Amarok.

I upgrade rather than fresh install unless it's at the same time as a hardware change, or if it's been a while since I did a fresh install. I've not had any problems.

---

### Post by Impavidus on 2020-11-26
Normally I upgrade, but this time, going from 19.10 to 20.04, I did a fresh install. The system had been incrementally upgraded from 16.10, so I thought is was about time for a fresh install. In a few weeks I'll upgrade to 20.10.

---

### Post by ajgreeny on 2020-11-26
Clean install here as well.

I have only upgraded from one version to the next once, and that was last week, from a KVM virtual install of 20.10 to 21.04, which went very well.
This update was carried out by manually editing the sources.list file from **groovy** to **hirsute** as at this time there is no other software means for a version upgrade as far as I'm aware.

---

### Post by Frogs Hair on 2020-11-26
Never done an LTS to LTS upgrade .

---

### Post by pantazi on 2020-11-26
No problem here upgrading from 16.04 through 18.04 to 20.04 on my aging HP 8460p

---

### Post by TheFu on 2020-11-26
I have many systems.
 
In June did a fresh install of 20.04, then restored my desktop data, settings, and list of apt packages into it from a 16.04 system. That was fine, but about 2 months later, after weekly patching, it failed to boot. I spent about 30 minutes troubleshooting. When that failed, I wiped it, did a fresh install and restored from backups taken about 8 hrs earlier. Never figured out the issue. The 20.04 install does require about 2x more storage than 16.04. I started out wth 22G on the 16.04 desktop. Decided 30G would provide a little headroom for 20.04, only to find that snaps were eating 10G+ and all that headroom was gone.  Added 10G more (thanks LVM) and everything has been ok.

That system is working today, though a number of problems broke some of my workflows.  Firefox and thunderbird have both been extremely unstable over remote X11, which has been working for decades - literally. When they are working, they are terribly slow.  Don't bother right-clicking unless you have 2 minutes free for the popup menu. This is specific to 20.04.

Chromium is useless. They broke the code so firejail doesn't work with or without the snap. Snaps seldom work over remote X11. Sad. 

Backup software was hit by python3 incompatibilities with my backup server. Ended up porting the python2 code to 20.04 and that is working. The root issue was with a change in serialization between p2 and p3. On disk, the data is stored the same as always, so there aren't data incompatibilities. 

For my servers, I only run LTS releases and always attempt an lts-to-lts upgrade for existing, complex, systems. This is done into VMs as a trial. I always read the Release Notes before attempting and research differences BEFORE starting. Previously, about 85% have worked, including minor changes needed for mariadb, nginx, or apache versions.  The few that failed , I'd attempt a few more times in test situations. Only once did I need to start over completely with a fresh install and data, settings, migration.  1 time, no upgrade or migration worked at all. I ended up switching the software used to something better supported. No need to stay with server programs that don't handle migrations well. We have plenty of choices for most things.

When the server migrations start will mainly be determined by zimbra support of 20.04. Sometimes, they take a year to support a new lts.  We're on 16.04 still with zibra.  Last upgrade was from 12.04 --> 14.04 --> 16.04 in 2 hrs. That worked well, with just a few bumps (perl version changes) after a few weeks testing the migration process.

Only my VPN server runs 18.04. No upgrade has been attempted. 18.04 network changes were lacking for my needs until about a year ago when it started working after a netplan patch. Because my vpn deployment is only for a few people and fewer than 20 devices, I was willing to try that first. I has turned out fine.  I am sligtly concerned over less tan great network performance in 20.04. Don't know if that is kernel or driver related. Did some tests a fw days ago and saw tat 20.04 was throttled by 30% nside a VM compared to other releases. Instead of 30 Gbps, I was seeing only 20 Gbps.  On real hardware, with GigE connections, it doesn't matter.

But my anecdotal stories aren't as good as a place running 1,000+ systems doing upgrades for desktops and servers.

---

### Post by pushbike06 on 2020-11-26
I have upgraded 4 systems from 18.04 LTS to 20.04 LTS , all 64bit, without any problems. Process took about 4 hours for each system. One of the four is a Server. I would have liked to download one instance of upgrade to a local repository but I don't know how to do that.
A fifth system Lubuntu 18.04 could not be upgraded to 20.04 as 20.04 does not support the Toshiba NB550 processor, an AMD dual core C50. I think Lubuntu 18.04 LTS is supported to 2023.
So, as with the NB550 processor, maybe your processor(s) are no longer supported.

---

### Post by pushbike06 on 2020-11-26
Sorry about this dual post but was not aware that the latest post is placed at top and not appended. Also there is a statement above postings saying that I was posting in the wrong forum???

I have upgraded 4 systems from 18.04 LTS to 20.04 LTS, one of which is a server. No problems just took about 4 hours for each system. Would have liked to download a single instance to a local repository but don't know how.
Could not upgrade Lubuntu 18.04 to 20.04 as 20.04 does not support the Toshiba NB550 processor, AMD dual core C50.
So maybe your processor(s) are no longer supported.

---

### Post by DuckHook on 2020-11-26
> **TheFu said:**
> …Chromium is useless. They broke the code so firejail doesn't work with or without the snap. Snaps seldom work over remote X11. Sad…
I'm unhappy with some of the changes to Chromium too. My workaround was to spin up a Bionic LXD container and run Chromium within that. Chromium was still a standard repo install in Bionic; not a snap. However, I don't know if this is enough to allow it to play nicely with Firejail.

---

### Post by Bashing-om on 2020-11-26
Clean install of (x)ubuntu-core 20.04

As I do not trust snaps on my desktop , and chromium was my preferred browser, well; I went with a 3rd party spin (slimjet) as my browser.

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by CatKiller on 2020-11-26
> **pushbike06 said:**
> Also there is a statement above postings saying that I was posting in the wrong forum???
That's not a message about **your** post, it's a message about **all** posts: this section is for chat rather than help. Your post is chatting rather than asking for help, so it's in the right place.

---

### Post by DuckHook on 2020-11-26
> **Bashing-om said:**
> …I went with a 3rd party spin (slimjet) as my browser…
Bashing, did you add it with a PPA or just install a .deb file?

---

### Post by TheFu on 2020-11-26
> **DuckHook said:**
> I'm unhappy with some of the changes to Chromium too. My workaround was to spin up a Bionic LXD container and run Chromium within that. Chromium was still a standard repo install in Bionic; not a snap. However, I don't know if this is enough to allow it to play nicely with Firejail.

I run Chromium over remote X11 on a 16.04 VM inside a firejail - almost always a private firejail so nothing touches storage from that process.

---

### Post by Bashing-om on 2020-11-26
DuckHook; Hey

It is a .deb file. Thus far easily maintained app.
[https://www.slimjet.com/](https://www.slimjet.com/)
And exactly functional as compared to chromium.

once installed ( sudo dpkg -i slimjet_amd64.deb) then:
```

sudo apt-get -f install

```
to pick up any additional dependencies.

[INDENT][INDENT]me, happy camper
[/INDENT][/INDENT]

---

### Post by TheFu on 2020-11-26
```
sudo apt install ./slimjet_amd64.deb
```
will pull in the dependencies automatically without needing the 2nd command.

But .deb files can introduce frozen dependencies that cause issues later, in a few months.

---

### Post by DuckHook on 2020-11-26
> **TheFu said:**
>  .deb files can introduce frozen dependencies that cause issues later, in a few months.
You anticipated my exact concerns. I'm always very hesitant about .debs for this reason. I'm also hesitant because updating now becomes a problem for other reasons.
> **Bashing-om said:**
> &#8230;[https://www.slimjet.com/](https://www.slimjet.com/)
And exactly functional as compared to chromium&#8230;
Thanks, Bashing, I might try this in the safe confines of a container.

---

### Post by DuckHook on 2020-11-26
> **michael351 said:**
> …Just curious how others have upgraded.
I have upgraded both ways on various machines with varying success for either method.

[LIST]
[*]My main box is multi&#8209;boot. On that box, my main and second partitions have been successfully network upgraded from Precise to Trusty to Bionic and now to Focal. That's 3 LTS upgrades with only minor problems along the way. Nothing that could not be figured out with a little cussedness and the help of fellow forum members.
[*]The third partition is more experimental: it contains a standard release on LVM for easy snapshots. This one has had bigger problems, sometimes necessitating scratch upgrades. Most network upgrades go well, but not all. Because they are standard releases, the problems do not surprise me.
[*]Mrs DuckHook's machine and any of half dozen assorted laptops, spare desktops, R-PIs, etc are usually network upgraded with only minor problems.
[*]I run a half dozen different servers. They are typically network upgraded with few problems. This is also expected since they are much simpler, with no GUIs and stripped down to only the most minimal services. There's simply less that can go wrong.
[/LIST]
I suppose I should explain what I mean by "minor problems". I don't consider the following to be a big deal. They just require a bit of tuning or a workaround:
[LIST=1]
[*]Broken sound (fixed by nuking old pulseaudio config)
[*]Dropped printers (fixed with newer hplip database)
[*]Strange artefacts in DE (fixed by clearing out old caches)
[*]Poor, stuttering video with dropouts (fixed by changing from Totem to VLC)
[*]
[/LIST]
Bigger problems have been:
[LIST=1]
[*]No video at all (regression in kernel)
[*]No network (driver dropped from kernel)
[*]End of 32-bit support (still 2 years of breathing space, but will ultimately be forced to use Debian)
[/LIST]
Bigger problems can stump me. Sometimes, as in the case of 32-bit EoL, there's no other option but to drop Ubuntu altogether.

---

### Post by davehk on 2020-11-27
Tried upgrading 8.04 to 12.04 - failed miserably so did a fresh instal. Since then, I just back-up my data and do a fresh install of the LTS. I generally only upgrade to every other LTS version.

---

### Post by coffeecat on 2020-11-27
> **pushbike06 said:**
> Sorry about this dual post but was not aware that the latest post is placed at top and not appended. 

Not with the default thread display mode, it doesn&#8217;t. Have you changed your thread display mode under general settings in your profile settings? Default is oldest first. Sounds like you may have changed it to newest first. There are two other display mode settings, which I&#8217;ve never found useful. Beware.

---

### Post by michael351 on 2020-11-27
What is the main benefit of upgrading to 20.04 over 18.04 in your case?

---

### Post by DuckHook on 2020-11-27
> **michael351 said:**
> What is the main benefit of upgrading to 20.04 over 18.04 in your case?
Because I help out on these forums, I must keep reasonably current. That's an unusual motivation for most folks.

To be frank, were it not for this reason, there's not a lot of incentive to upgrade. Mrs DH had been happily running on Precise (16.04) until I upgraded her last month. Since Precise is EoL in April, I convinced her it was time, but barring that, she would have been perfectly happy staying with a four&#8209;year old version.

I still have servers running Bionic. Many of the power users here are still running 18.04. There's no reason not to.

I suppose that, because the world is addicted to the latest and greatest, you will tend to find better support on the forums with the latest LTS release, but if 18.04 is running rock steady for you, then there's no need for support in the first place.

There's nothing wrong with running 18.04. And in the case of my 32-bit server, upgrading is not even an option.

---

### Post by TheFu on 2020-11-27
> **michael351 said:**
> What is the main benefit of upgrading to 20.04 over 18.04 in your case?

Since you didn't specify a specific person and we can't read your mind, I'll answer too.

If I need to replace an OS, then I want to minimize the number of times I have do that.  I want systems that run, for as long at possible, with the minimal number of hassles.  Changing an OS is a hassle.  With 5 yrs of support, it isn't hard to skip an entire LTS (releases are every 2 yrs), which reduces the hassle-factor 50% just with that single choice.

Plus, by avoiding being an early adopter for important systems, most of the major stuff that is broken will be fixed in a few months after an LTS release.  Businesses are known to wait until the .1 of an LTS release happens.  For 20.04, the .1 happened a few months ago.

My networking needs are often a little more complex than that for a typical home Ubuntu user. This means when some of the more complex network capabilities don't work with an LTS, as happened with 18.04 (which took over 18 months to get to the point I could us it), then any incentive to run that OS are lowered.  When I needed a new email gateway server and 18.04 networking wasn't ready, I deployed a Debian server instead.  OTOH, when I wanted to deploy a pi-hole into an LXD container last April, 20.04 wasn't ready for my needs, so it got 18.04.  I think that's the only 18.04 system I have today. 

Today, if I were deploying any new desktop or new server for someone else, I'd go with 20.04.1 - unless they hated Snap packages, then for desktops, I would push them towards Linux-Mint or Debian Stable.  If they don't know anything about snap packages, then Ubuntu is fine. They may or may not have issues, but that is a bridge every individual will fall from in their own time.

---

### Post by pantazi on 2020-11-27
I'm a typical average user but both my wife and I find 20.04 looks good and is a little smoother (for want of a better word) than 18.04. My wife's laptop was pre-loaded with 20.04 ( Starlabs Labtop) and after using it for a while, I upgraded mine to 20.04.1.  It's pretty customisable and my ageing HP8460p  brick is running pretty slick.

Just tried Mate and Xubuntu in Virtualbox, but for our needs Ubuntu does it all.

---

### Post by yetimon_64 on 2020-11-28
> **michael351 said:**
> Have you upgraded to 20.04?...
Not yet for myself; though I did do an Xubuntu 20.04 install (clean/fresh install) for another person a few months ago; it ran very well.

I'll probably wait until Xenial is EOL in April 2021 before I finally do one for myself as my 2 installs of Bionic (Ubuntu Mate and Lubuntu) are running fine. I have Ubuntu Xenial 16.04, Ubuntu Mate 18.04 and Lubuntu 18.04 multi-booting off of my laptop drive. Actually I may end up having to replace Mate and Lubuntu about the same time as the flavors are only supported for 3 years IIRC.

> **michael351 said:**
> ...Did you use 'do-release-upgrade' or
perform a clean install?...
With my multi-booting and my tendency to use PPA's I always do a fresh/clean install after backing up, either by "tar-balling" or with "dd", the old installation being replaced.

I haven't done an in place upgrade since about 2009 / 2010. The last 10 to 11 years I've always done fresh installs after backing up the older one.

---

### Post by mastahsplintah on 2020-11-29
Yea I have been on 20.10 for a while now, it's been stable and pretty great. I actually forced the upgrade to get it early and I don't recommend doing this.

---

### Post by wmcl on 2020-11-29
Upgraded from 18.04 using do-release-upgrade about a week ago. Ran into the expected graphics issues because I had to resort to using a PPA for graphics drivers, but installing the more recent graphics drivers for my card which are available with 20.04 sorted that out.

> **TheFu said:**
> 
Chromium is useless. They broke the code so firejail doesn't work with or without the snap. Snaps seldom work over remote X11. Sad. 


While I don't use firejail or remote X11, so I didn't run into those problems, I also found the chromium snap abhorrent, mostly due to the sluggishness and lacking integration in the existing GUI (different mouse cursor in chromium, WTF?). Fortunately, apparently there are more people who don't like the chromium snap out there, so a quick search for "chromium snap" yielded [this nice manual on how to install a proper chromium deb package from a PPA]("http://ubuntuhandbook.org/index.php/2020/06/install-chromium-via-deb-ubuntu-20-04/"), which solved my problems. Also I promptly uninstalled snapd.

---

### Post by EuclideanCoffee on 2020-11-29
Switching from 18.04 LTS to 20.04 LTS was a headache for the enterprise. But for home, it was so simple. The new kernel really improved my experience on my HP as well, running newish amd of two years ago. HWE kernel caused a few blips. So switching to 20.04 LTS has been almost flawless. I know everyone hates the new containerized apps, but I've been using snap. Not at all efficient, but it's easy to use. Security nightmare for sure. I may have to revise my decisions, but home computing is quite low risk. And all the security precautions I do in enterprise really don't apply at home.

---

### Post by DuckHook on 2020-11-29
> **EuclideanCoffee said:**
> Switching from 18.04 LTS to 20.04 LTS was a headache for the enterprise.
What did you find to be some of the more important enterprise headaches (that might prove useful for others thinking of the move)?

---

### Post by mikewhatever on 2020-11-29
Yes I have, and no, clean install is not an upgrade.

---

### Post by EuclideanCoffee on 2020-11-29
Aside from the entire rebuilding of the install scripts, so I have to use yaml instead of debian installer commands in the preseed. Yes, it's "easier" to use yaml, but I still have to redo all of the hours of work I've done for the former configuration. Without a clear path to reconfigure this, it takes hours of research and development. Ignore all the research and development I need to put into application development. The heavy reliance on snaps without a way to maintain the snap catalog is the biggest headache. I'm not sure why Canonical thinks it's okay that enterprise users can install anything and whatever they want from the repository. I believe Debian has done a valiant effort to categorize each application as free or non-free, but Canonical confuses me with the main and universe branches (ignore updates and security, ugh). I have to review each application. But with the snap catalog, it becomes impossible to prevent applications. I know it's not impossible, but the audit of the applications included in the repository is already impossible in sense that it requires 6 hours of human power to review just one application for security, legal, and privacy documentation. Blocking off all applications then is essential, so I can expand the pool of applications via dpkg.

---

### Post by kurt18947 on 2020-11-30
My experience with a Ryzen machine is that 20.04 is more stable than 18.04. 18.04 was a real problem for me with an Asrock B350 board and APU (Ryzen 3 2200G). I had enough problems - mostly video related I think - that it eventually became unbootable. The file system remained intact so no data loss.  I have no idea about 16.04 but 20.04 has been fine with no tinkering.

---

