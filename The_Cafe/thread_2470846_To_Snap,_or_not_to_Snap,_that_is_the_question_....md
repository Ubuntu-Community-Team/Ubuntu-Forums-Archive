---
title: "To Snap, or not to Snap, that is the question ..."
date: 2022-01-13
forum: The Cafe
---

### Post by Daveski17 on 2022-01-13
OK, I've discovered that the next LTS version of Ubuntu will have a snap version of Firefox by default. [OMG! Ubuntu!]("https://www.omgubuntu.co.uk/2021/09/ubuntu-makes-firefox-snap-default").

So, in a nutshell, what are the advantages over the PPA version?

---

### Post by yetimon_64 on 2022-01-13
Snaps are the first thing in a new install to be removed for me, so from 22.04 and on I'll be downloading the "firefox.xx.x.tar.bz" file directly from Mozilla rather than using another PPA. Download page [[COLOR=#0000ff]--here--[/COLOR]]("https://www.mozilla.org/en-GB/firefox/all/#product-desktop-release"), see screenshot below.

For firefox, I trust Mozilla enough to run firefox from my home directory "bin" folder and have done so with "Nightly" versions in the past. I try to limit the number of PPAs installed when possible (Edit: for security reasons). With respect to keeping it updated, this version auto updates like the firefox version used with the tor browser bundle; or can be manually checked from the Help menu > "About Firefox" in a running browser window. There are options in the "Edit Menu" > "Settings > "General Tab" for how updating is done, either automatically install or just check etc.

It is easy enough to create a firefox profile and a launcher for the downloaded firefox. At the moment I've got the standard distro "95" version and the latest "96" version (running from my home folder) both here; running side by side in the second screenshot below. Cheers, yeti :).

---

### Post by GhX6GZMB on 2022-01-13
I do the same.
The first action after a fresh install is removing snapd.
My solution is using Brave instead. FF has become so bloated over time that it's probably the heaviest and slowest browser out there.

---

### Post by deadflowr on 2022-01-13
Advantage of snaps over PPA is strongly a development/developers advantage.
snaps only need a single version which will run across all releases. 
From a developer point of view it makes dealing with issues easier, since they do not have to deal with multiple releases and multiple versions.

Snaps are mostly isolated outside the normal system, so what they do usually does not affect the rest of the system.
PPA are normal apt packages, so what they can do can greatly affect the system.

Snaps by default are built to be untrusted. So they are very locked down in terms of what can and cannot be accessed by the user or the system.
Creating snap packages which require more access than the defaults allowed have to be thoroughly reviewed before they can be published into the store.

PPAs insist that you understand they are untrusted, but do nothing beyond that.
Anyone can create a PPA of a package and that package can have unfettered system access if installed.

Of course access can be a two-way street as sometimes unfettered access is needed in order for your program to run as you need it to.
I find this to be the biggest issue with snaps as sometimes you need the snap to have access to some part of your system which it cannot access.

Beyond that snaps have a few issues that keep popping up here and there.
which are basically
1)snaps are slow to start and drag out boot times.
2)snap updates cannot be fully controlled, they just update on their own so the user has little to no means to stop it or delay it.
(snaps can be set to delay updates but only for a limited time)

As far as PPAs go one major issue with them is abandonment.
launchpad is littered with PPAs that are dead.


So I guess you can take some of that as a few of the advantages and disadvantages of both.

---

### Post by CatKiller on 2022-01-13
> **Daveski17 said:**
> So, in a nutshell, what are the advantages over the PPA version?
Over the PPA version? Not much. Over the repository version, it gets updates much quicker than packaging up seven versions through the Stable Release Updates mechanism, which is why Mozilla asked them to provide it as a snap rather than packaging it in the repositories.

[https://discourse.ubuntu.com/t/feature-freeze-exception-seeding-the-official-firefox-snap-in-ubuntu-desktop/24210](https://discourse.ubuntu.com/t/feature-freeze-exception-seeding-the-official-firefox-snap-in-ubuntu-desktop/24210)

---

### Post by GhX6GZMB on 2022-01-13
@deadflowr:
Thanks for an informed reply.

So snap is like Win 10: never let a user make his/her own decisions. All power to the developers. All users are idiots.

My dislike of snap was just a gut feeling at first, heightened by the messy look of my storage system (loop this, loop that...) when using it. And stacking abstraction layers on top of each other is totally user-unfriendly. Ubuntu is complicated enough as it is.

Thank You.

---

### Post by VMC on 2022-01-13
Not Snap 4 me. Regarding Firefox. Go to Mozilla, download Firefox , unzip to "/opt". Don't need Snap or PPA.

edit-Yetimon basically answered Firefox Q.

---

### Post by TheFu on 2022-01-13
> **Daveski17 said:**
> OK, I've discovered that the next LTS version of Ubuntu will have a snap version of Firefox by default. [OMG! Ubuntu!]("https://www.omgubuntu.co.uk/2021/09/ubuntu-makes-firefox-snap-default").

So, in a nutshell, what are the advantages over the PPA version?

Snap questions have been asked and answered in these forums the last few years extensively. The good and the bad for snaps has been discussed at length. Best to go read those threads and ask specific questions AFTER.

I'm anti-snap. If I want extra security that snaps force on all packages, to the point of actually breaking functionality, then I'll add it with another cgroup management tool like firejail.  Snaps prevent other cgroup management tools from working for that program and don't provide the same capabilities, especially related to privacy that other tools provide.

I think snaps will be like Unity.  After 5 yrs of being forced, Canonical will walk away and we'll all start using flatpaks instead.  Flatpaks allow local control, unlike snaps.  There are also AppImages for when no added security is desired. All three are trying for the "download once and use on any Linux" solution.  IME, snaps work about 20% of the time, but I don't have standard desktops, nor do I use default security settings for systems.

If you want a feel today for what snaps are like, on any Ubuntu system, try to install chromium-browser. It will be a snap.  Now try to run the browser from a different computer, but display it locally.  It will crash without some manual steps.  Is your HOME directory somewhere other than /home?  No snaps will work at all. Period.  In a corporate environment, /home just isn't used. Also, HOME directory storage is mounted over NFS from storage servers. This means that a user can walk into a room with 100 computers, sit behind any one of them, login and have it "feel" like his computer. All his settings and files are there, as expected, in his HOME.  For a few years, there was an issue with NFS storage ... now they just have another hard-coded issue that storage not under /mnt/ or /media/ cannot be accessed by snaps.  Where storage for data is located needs to be under local control.

---

### Post by Daveski17 on 2022-01-13
> **yetimon_64 said:**
> Snaps are the first thing in a new install to be removed for me, so from 22.04 and on I'll be downloading the "firefox.xx.x.tar.bz" file directly from Mozilla rather than using another PPA. Download page [[COLOR=#0000ff]--here--[/COLOR]]("https://www.mozilla.org/en-GB/firefox/all/#product-desktop-release"), see screenshot below.

For firefox, I trust Mozilla enough to run firefox from my home directory "bin" folder and have done so with "Nightly" versions in the past. I try to limit the number of PPAs installed when possible (Edit: for security reasons). With respect to keeping it updated, this version auto updates like the firefox version used with the tor browser bundle; or can be manually checked from the Help menu > "About Firefox" in a running browser window. There are options in the "Edit Menu" > "Settings > "General Tab" for how updating is done, either automatically install or just check etc.

It is easy enough to create a firefox profile and a launcher for the downloaded firefox. At the moment I've got the standard distro "95" version and the latest "96" version (running from my home folder) both here; running side by side in the second screenshot below. Cheers, yeti :).

OK, thanks for the info.

---

### Post by Daveski17 on 2022-01-13
> **ml9104 said:**
> I do the same.
The first action after a fresh install is removing snapd.
My solution is using Brave instead. FF has become so bloated over time that it's probably the heaviest and slowest browser out there.

Brave looks like an alternative, although the snap Firefox might be OK. Vivaldi's buggy on Ubuntu. I may use Chrome more. :eek:

---

### Post by Daveski17 on 2022-01-13
> **deadflowr said:**
> Advantage of snaps over PPA is strongly a development/developers advantage.
snaps only need a single version which will run across all releases. 
From a developer point of view it makes dealing with issues easier, since they do not have to deal with multiple releases and multiple versions.

Snaps are mostly isolated outside the normal system, so what they do usually does not affect the rest of the system.
PPA are normal apt packages, so what they can do can greatly affect the system.

Snaps by default are built to be untrusted. So they are very locked down in terms of what can and cannot be accessed by the user or the system.
Creating snap packages which require more access than the defaults allowed have to be thoroughly reviewed before they can be published into the store.

PPAs insist that you understand they are untrusted, but do nothing beyond that.
Anyone can create a PPA of a package and that package can have unfettered system access if installed.

Of course access can be a two-way street as sometimes unfettered access is needed in order for your program to run as you need it to.
I find this to be the biggest issue with snaps as sometimes you need the snap to have access to some part of your system which it cannot access.

Beyond that snaps have a few issues that keep popping up here and there.
which are basically
1)snaps are slow to start and drag out boot times.
2)snap updates cannot be fully controlled, they just update on their own so the user has little to no means to stop it or delay it.
(snaps can be set to delay updates but only for a limited time)

As far as PPAs go one major issue with them is abandonment.
launchpad is littered with PPAs that are dead.


So I guess you can take some of that as a few of the advantages and disadvantages of both.

Thanks for the detailed and informative reply. I run the snap versions of some apps like GIMP and Pinta and they seem fine. I tried the snap Opera and it was slow to start-up and there were issues running videos. Hopefully the snap Fx will be greatly improved.

---

### Post by Daveski17 on 2022-01-13
> **CatKiller said:**
> Over the PPA version? Not much. Over the repository version, it gets updates much quicker than packaging up seven versions through the Stable Release Updates mechanism, which is why Mozilla asked them to provide it as a snap rather than packaging it in the repositories.

[https://discourse.ubuntu.com/t/feature-freeze-exception-seeding-the-official-firefox-snap-in-ubuntu-desktop/24210](https://discourse.ubuntu.com/t/feature-freeze-exception-seeding-the-official-firefox-snap-in-ubuntu-desktop/24210)

Thanks. I should have specified the repo version as well, so you've answered that. I just hope the snap Fx will be OK.

---

### Post by Daveski17 on 2022-01-13
> **ml9104 said:**
> @deadflowr:
Thanks for an informed reply.

So snap is like Win 10: never let a user make his/her own decisions. All power to the developers. All users are idiots.

My dislike of snap was just a gut feeling at first, heightened by the messy look of my storage system (loop this, loop that...) when using it. And stacking abstraction layers on top of each other is totally user-unfriendly. Ubuntu is complicated enough as it is.

Thank You.

I'm not sure what my gut's telling me about a snap default browser. I am a little concerned. Probably need Andrew's Liver Salts ... lol.

---

### Post by Daveski17 on 2022-01-13
> **VMC said:**
> Not Snap 4 me. Regarding Firefox. Go to Mozilla, download Firefox , unzip to "/opt". Don't need Snap or PPA.

edit-Yetimon basically answered Firefox Q.

Thanks, I will consider this.

---

### Post by Daveski17 on 2022-01-13
> **TheFu said:**
> Snap questions have been asked and answered in these forums the last few years extensively. The good and the bad for snaps has been discussed at length. Best to go read those threads and ask specific questions AFTER.

I'm anti-snap. If I want extra security that snaps force on all packages, to the point of actually breaking functionality, then I'll add it with another cgroup management tool like firejail.  Snaps prevent other cgroup management tools from working for that program and don't provide the same capabilities, especially related to privacy that other tools provide.

I think snaps will be like Unity.  After 5 yrs of being forced, Canonical will walk away and we'll all start using flatpaks instead.  Flatpaks allow local control, unlike snaps.  There are also AppImages for when no added security is desired. All three are trying for the "download once and use on any Linux" solution.  IME, snaps work about 20% of the time, but I don't have standard desktops, nor do I use default security settings for systems.

If you want a feel today for what snaps are like, on any Ubuntu system, try to install chromium-browser. It will be a snap.  Now try to run the browser from a different computer, but display it locally.  It will crash without some manual steps.  Is your HOME directory somewhere other than /home?  No snaps will work at all. Period.  In a corporate environment, /home just isn't used. Also, HOME directory storage is mounted over NFS from storage servers. This means that a user can walk into a room with 100 computers, sit behind any one of them, login and have it "feel" like his computer. All his settings and files are there, as expected, in his HOME.  For a few years, there was an issue with NFS storage ... now they just have another hard-coded issue that storage not under /mnt/ or /media/ cannot be accessed by snaps.  Where storage for data is located needs to be under local control.

I already run snaps. I ran the Opera snap. I eventually uninstalled it. I'm not interested in hierarchical binary arguments (no pun intended lol). I am a bit concerned about Firefox as a snap default. Opera was slow and buggy. GIMP and Pinta seem fine. I can't tell the difference between some PPA's and Snaps. As this is The Cafe my intention wasn't to get into a long polarised debate. Perhaps I should have been more specific. My *real* concern is how the snap Firefox will run as a default browser when I upgrade to a bog-standard 21.04 LTS. I held on to 14.04 for a long time as many told me everything after it was a disaster. It wasn't true. Mostly, it seems to me, Ubuntu is steadily improving. I'm a bit ambivalent about a snap Firefox though. Thanks for your input.

---

### Post by iamjiwjr on 2022-01-14
I delete the Firefox snap. Then I install no other snaps either. Then I install Synaptic via the terminal (I stay away from the Ubuntu software app). I open Synaptic and install the .deb Firefox from the Ubuntu repo.

I'd be fine with snaps except that, on my computer, I've not found them to be any where near as reliable as flatpaks. Buggy. Not really ready for prime time on the desktop side. I do hear on podcasts that they work well on the server side, though.

Weird. Ubuntu makes its money in servers, I read, so I guess that makes sense.

ps-along with Firefox, my first-thing-to-do package installs? After the Ubuntu distro install, using Synaptic, I install: Flatpak, Gnome-tweaks, Gnome-extensions, Gdebi, Ubuntu restricted add-ons and Ubuntu restricted-extras. I then open Firefox and install: Gnome extensions add-on and (via terminal) the flathub repo from the flathub website. Then I reboot and I'm ready to continue with my setup. Flatpaks can be installed from the flathub website via copy-paste into the terminal.

On my Dell Precision desktop at least, Ubuntu, for all the heat it takes, is at the top of the Gnome distro class for reliability over time, speed, low temps, and memory efficiency. But my Dell was birthed with Ubuntu on it so that might make sense. Anyway, it's my experience.

---

### Post by Daveski17 on 2022-01-14
> **iamjiwjr said:**
> I delete the Firefox snap. Then I install no other snaps either. Then I install Synaptic via the terminal (I stay away from the Ubuntu software app). I open Synaptic and install the .deb Firefox from the Ubuntu repo.

I'd be fine with snaps except that, on my computer, I've not found them to be any where near as reliable as flatpaks. Buggy. Not really ready for prime time on the desktop side. I do hear on podcasts that they work well on the server side, though.

Weird. Ubuntu makes its money in servers, I read, so I guess that makes sense.

ps-along with Firefox, my first-thing-to-do package installs? After the Ubuntu distro install, using Synaptic, I install: Flatpak, Gnome-tweaks, Gnome-extensions, Gdebi, Ubuntu restricted add-ons and Ubuntu restricted-extras. I then open Firefox and install: Gnome extensions add-on and (via terminal) the flathub repo from the flathub website. Then I reboot and I'm ready to continue with my setup. Flatpaks can be installed from the flathub website via copy-paste into the terminal.

On my Dell Precision desktop at least, Ubuntu, for all the heat it takes, is at the top of the Gnome distro class for reliability over time, speed, low temps, and memory efficiency. But my Dell was birthed with Ubuntu on it so that might make sense. Anyway, it's my experience.

OK, thanks. I think I'll have to wait and see. Apparently Mozilla wanted the snap of Firefox. Maybe they'll sort out any problems. I don't particularly want to switch from Ubuntu to another distro. I never thought I'd start to consider Mint though. I can live with some snaps. I mean, they can only get better, right? :(

---

### Post by TheFu on 2022-01-14
> **Daveski17 said:**
>  My *real* concern is how the snap Firefox will run as a default browser when I upgrade to a bog-standard 21.04 LTS. 

21.04 support ended. Don't install that.

---

### Post by Daveski17 on 2022-01-14
> **TheFu said:**
> 21.04 support ended. Don't install that.

Sorry, I meant 22.04 LTS.

---

### Post by DuckHook on 2022-01-16
> **iamjiwjr said:**
> I delete the Firefox snap. Then I install no other snaps either. Then I install Synaptic via the terminal (I stay away from the Ubuntu software app). I open Synaptic and install the .deb Firefox from the Ubuntu repo.
This technique will no longer work come Jammy. The FF "app" in the repos will only be a stub that installs snap, then the snap version of FF. No getting around it.

The only alternatives then will be to install the self-updating .deb or one of the Mozilla Team versions via their PPA. See this thread: [https://ubuntuforums.org/showthread.php?t=2470573](https://ubuntuforums.org/showthread.php?t=2470573)

---

### Post by DuckHook on 2022-01-16
> **Daveski17 said:**
> OK, thanks. I think I'll have to wait and see. Apparently Mozilla wanted the snap of Firefox. Maybe they'll sort out any problems. I don't particularly want to switch from Ubuntu to another distro. I never thought I'd start to consider Mint though. I can live with some snaps. I mean, they can only get better, right? :(
They are a very mixed bag.

In addition to the pros and cons you've read above, consider the following:

Pros:

[LIST=1]
[*]Additional layer of sandboxing. This has to be acknowledged. Despite the fact that they give fits to gurus like TheFu, for most ordinary users who install with the ordinary defaults, running apps in even a quasi sandbox offers a little more security. Granted, the various holes might give a *false* sense of security, but most users are not aware enough of the finer details to have any sense of security one way or the other. More security is usually good, but can also be a double edged sword (see further below).
[*]More apps available. A lot of devs don't bother trying to qualify their apps for the repos. But they don't object to offering them as snaps, since the fees to join that club are so much lower (I'm speaking figuratively—there are no monetary fees imposed to getting on the repos).
[*]Faster updates, more current apps. You no longer have to wait for the repo maintainers to vet anything. And universe/multiverse apps never get updated at all.
[/LIST]
Cons:

[LIST=1]
[*]Absurd (in my opinion) app bloat. See this thread: [https://ubuntuforums.org/showthread.php?t=2470573](https://ubuntuforums.org/showthread.php?t=2470573)
[*]Loss of control over app integrity/auditing. One of the big points of snaps was to take the responsibility of maintenance off the shoulders of distro gatekeepers—which leaves you at the mercy/good graces of the devs alone. To me, this is a big deal and undermines trustworthiness and the whole concept of a distro.
[*]Loss of fine control/flexibility/options. The disadvantages of default sandboxing. Most snap apps ship with limited options for manipulating the sandbox. The devs assume some defaults which work for most users, but are often too limiting for power users and will break apps in non-default environments.
[/LIST]
As for your last (rhetorical?) question: actually, there is little impetus towards continual evolvement for the better. I suspect that the snap delivery mechanism itself will get "better" in the sense that bugs will keep getting squashed, but consider: how is taking away the auditing and oversight traditionally needed to get an app committed to the repos going to enhance either care or discipline on the part of third party devs?

---

### Post by Daveski17 on 2022-01-16
> **DuckHook said:**
> They are a very mixed bag.

In addition to the pros and cons you've read above, consider the following:

Pros:

[LIST=1]
[*]Additional layer of sandboxing. This has to be acknowledged. Despite the fact that they give fits to gurus like TheFu, for most ordinary users who install with the ordinary defaults, running apps in even a quasi sandbox offers a little more security. Granted, the various holes might give a *false* sense of security, but most users are not aware enough of the finer details to have any sense of security one way or the other. More security is usually good, but can also be a double edged sword (see further below).
[*]More apps available. A lot of devs don't bother trying to qualify their apps for the repos. But they don't object to offering them as snaps, since the fees to join that club are so much lower (I'm speaking figuratively—there are no monetary fees imposed to getting on the repos).
[*]Faster updates, more current apps. You no longer have to wait for the repo maintainers to vet anything. And universe/multiverse apps never get updated at all.
[/LIST]
Cons:

[LIST=1]
[*]Absurd (in my opinion) app bloat. See this thread: [https://ubuntuforums.org/showthread.php?t=2470573](https://ubuntuforums.org/showthread.php?t=2470573)
[*]Loss of control over app integrity/auditing. One of the big points of snaps was to take the responsibility of maintenance off the shoulders of distro gatekeepers—which leaves you at the mercy/good graces of the devs alone. To me, this is a big deal and undermines trustworthiness and the whole concept of a distro.
[*]Loss of fine control/flexibility/options. The disadvantages of default sandboxing. Most snap apps ship with limited options for manipulating the sandbox. The devs assume some defaults which work for most users, but are often too limiting for power users and will break apps in non-default environments.
[/LIST]
As for your last (rhetorical?) question: actually, there is little impetus towards continual evolvement for the better. I suspect that the snap delivery mechanism itself will get "better" in the sense that bugs will keep getting squashed, but consider: how is taking away the auditing and oversight traditionally needed to get an app committed to the repos going to enhance either care or discipline on the part of third party devs?

Thanks for the comprehensive reply. I don't fully understand the technicalities and implications of snaps. I'm not a guru, or even much of an anorak. Basically I'm a bog-standard punter who a few years ago ditched Windows for Unix. I replaced Vista on my old Belnea notebook for Trusty and was well and truly converted. The next laptop I bought had Ubuntu pre-installed. I'd used Ubuntu before but 14.04 LTS was the first distro that I ran as a *day* *to* *day* OS. The security aspect was a big factor. Being able to use a computer without an AV was liberating. I've never trusted anti-virus programs and was more concerned about them eviscerating my hard drive accidentally than actual malware. I've never ran a third party security program that hasn't produced false positives. I actually run some snaps now. Mostly they seem fine. Opera was bad though. If Firefox works as well as a snap as it does now I think it should be OK. I have a few about:config tweaks and a few extensions. Otherwise I'll return to Chrome or another non-snap alternative.

---

### Post by TheFu on 2022-01-16
> **DuckHook said:**
> They are a very mixed bag.

In addition to the pros and cons you've read above, consider the following:

Pros:

[LIST=1]
[*]Additional layer of sandboxing. This has to be acknowledged. Despite the fact that they give fits to gurus like TheFu, for most ordinary users who install with the ordinary defaults, running apps in even a quasi sandbox offers a little more security. Granted, the various holes might give a *false* sense of security, but most users are not aware enough of the finer details to have any sense of security one way or the other. More security is usually good, but can also be a double edged sword (see further below).
[*]More apps available. A lot of devs don't bother trying to qualify their apps for the repos. But they don't object to offering them as snaps, since the fees to join that club are so much lower (I'm speaking figuratively&#8212;there are no monetary fees imposed to getting on the repos).
[*]Faster updates, more current apps. You no longer have to wait for the repo maintainers to vet anything. And universe/multiverse apps never get updated at all.
[/LIST]
Cons:

[LIST=1]
[*]Absurd (in my opinion) app bloat. See this thread: [https://ubuntuforums.org/showthread.php?t=2470573](https://ubuntuforums.org/showthread.php?t=2470573)
[*]Loss of control over app integrity/auditing. One of the big points of snaps was to take the responsibility of maintenance off the shoulders of distro gatekeepers&#8212;which leaves you at the mercy/good graces of the devs alone. To me, this is a big deal and undermines trustworthiness and the whole concept of a distro.
[*]Loss of fine control/flexibility/options. The disadvantages of default sandboxing. Most snap apps ship with limited options for manipulating the sandbox. The devs assume some defaults which work for most users, but are often too limiting for power users and will break apps in non-default environments.
[/LIST]
As for your last (rhetorical?) question: actually, there is little impetus towards continual evolvement for the better. I suspect that the snap delivery mechanism itself will get "better" in the sense that bugs will keep getting squashed, but consider: how is taking away the auditing and oversight traditionally needed to get an app committed to the repos going to enhance either care or discipline on the part of third party devs?

I don't have any issue with sandboxing. Actually, it is a good thing, provided it doesn't break workflows with other applications or prevent access to other storage areas or force all user HOME directories to be in /home.

There are 3 different solutions for "single file packaging."  Snaps is one.  Flatpaks is another and AppImages.  Flatpaks has Redhat behind it, has sandboxing, but also allows local control. Flatpaks have an ecosystem around them to provide automatic updates or updates on-demand - like APT does. Snaps force updates in the MSFT/Google way where they come without asking.  AppImages lack sandboxing and updates.  AppImages are like the old setup.exe which is both clear on the use and terrible to keep updated.  Canonical could have selected the flatpak system and used it, but they have NIH syndrome again - like they did with the Unity DE.  Without local control, we give up the flexibility for which Linux is famous. That flexibility is a key reason why many people choose Linux.

There is currently only 1 snap-store. Canonical's.  I know of 1 group that likes that situation.  Even Android has multiple, alternative AppStores.  Do we prefer Apple's 1-and-only appstore where they've effectively pushed F/LOSS out or would we rather have a bazaar with lots of options?

Almost all of my problems with snap packages are related to lack of local control for allowing access to storage locations outside what the snap team thinks is ok.  

I don't mind a little broken work-flows between applications. For example, I use firejail in private mode for online banking.  This prevents writing files, including downloaded statements, anywhere on the real storage.  That's can be a problem, since I want to keep my bank statements for historical and tax reasons.  Firejail has an obtuse method to access the "private" storage overlay and copy those files out to non-private storage. It is cumbersome, but with a little scripting, not too bad.  It doesn't have any GUI and it doesn't work with normal bash file globbing. Exact names of files and locations of those files for the source are necessary. It is a pain.  I can live with it, since the location for my bank statements isn't somewhere that any snap package will allow me to save files.  Bank statements aren't really too bad - dropping them in ~/Downloads if using a snap is possible with firejail that isn't running in private mode, but then I've lost some important security in allowing access to my HOME.  Plus, on some systems, my HOME directories aren't in /home/ ... they are on NFS and under /u/ <--- I prefer shorter directory names.  For years, NFS wasn't supported by snaps at all. It seems they may have corrected that for some situations, just not user HOMEs.

Without local control for what is and isn't allowed in a snap package, it is just too inflexible. I have no issue if they want default, non-tech, installs with snaps. That's a good idea, but don't handcuff 50% of the users who have 20+ yrs experience and don't do things the way that Canonical demands.  If I want an OS like that, I'd run OSX.

---

### Post by Tadaen_Sylvermane on 2022-01-16
I personally like them. Prevents dependency hell when trying to do certain things. It's not always straightforward to compile it oneself.

Like anything they have their issues as well. I don't like browsers in them. I like my default downloads folder where it is.

---

### Post by Daveski17 on 2022-01-16
> **Tadaen_Sylvermane said:**
> I personally like them. Prevents dependency hell when trying to do certain things. It's not always straightforward to compile it oneself.

Like anything they have their issues as well. I don't like browsers in them. I like my default downloads folder where it is.

Yes, I have no real issues with some snaps I use. Downloading and running the PPA Pinta is hard work for me, yet the snap is fine. I am particularly concerned about a snap Firefox. My experience with snap browsers is not good. I'll probably return to Chrome. Although SRWare Iron could be an alternative. I ran it years ago in Windows.

---

### Post by DuckHook on 2022-01-16
> **Daveski17 said:**
> Yes, I have no real issues with some snaps I use. Downloading and running the PPA Pinta is hard work for me, yet the snap is fine. I am particularly concerned about a snap Firefox. My experience with snap browsers is not good. I'll probably return to Chrome. Although SRWare Iron could be an alternative. I ran it years ago in Windows.
The FF workarounds are simple and easy (see above&#8209;referenced thread)—unless you actually prefer Chrome.

It's an admittedly personal bias, but I wouldn't trust any browser from the world's largest data slurper. However, to each their own.

---

### Post by Daveski17 on 2022-01-16
> **DuckHook said:**
> The FF workarounds are simple and easy (see above&#8209;referenced thread)—unless you actually prefer Chrome.

It's an admittedly personal bias, but I wouldn't trust any browser from the world's largest data slurper. However, to each their own.

Simple and easy for you maybe lol. I'm sure I'll figure it out. I'm banking on the 'Snapfox' being fine by the time I upgrade. Yeah, I'm not a huge fan of Google. Chrome is reliable at least. I've run Vivaldi on Ubuntu since it was released. It's always been a bugfest. IIRC SRWare Iron was super fast but also a bit buggy (on Windows). Brave could be an alternative. The snap is supposed to be a bit pants though. I'll just have to wait and see what happens with 22.04 LTS.

---

### Post by DuckHook on 2022-01-16
> **Daveski17 said:**
> Simple and easy for you maybe lol. I'm sure I'll figure it out.
Actually, I'm sure that you will. But if it helps, then this is the Firefox site from where you can download the standalone package: [https://pkgs.org/download/firefox](https://pkgs.org/download/firefox)
Just choose your distro/version, download into directory of your choice, then: ```
sudo apt install /path/to/directory/name_of_pkg
```…I suspect you will agree that it's not that hard.

Alternately, as per one of the posts in the other thread mentioned: ```
sudo add-apt-repository ppa:mozillateam/ppa
sudo apt update
sudo apt install firefox-esr
```This will add the Mozilla Team's PPA to your install, then install the ESR version of Firefox. You will need to remove your existing FF first—I suspect that the two don't like to coexist alongside each other, though I haven't actually experimented with it that way. If you don't want the ESR version and want to stick to vanilla FF, then your best bet is the first option.
> I've run Vivaldi on Ubuntu since it was released. It's always been a bugfest.
Interesting: the few times I've tried it, I've never had problems.
> Brave could be an alternative. The snap is supposed to be a bit pants though.
Don't know about the snap and have no real interest, but adding the Brave repo is not hard either. Instructions here: [https://brave.com/linux/](https://brave.com/linux/)
I am exceedingly impressed with Brave. It is my fallback browser and has never failed me. I would use it for my main browser except that I am already so invested in FF and have grown so used to it. I'm a big Brave booster.
> I'll just have to wait and see what happens with 22.04 LTS.
Or you could fire up a VM and have a look at it now. Though still in development, it is more than usable enough for you to get a sense of how FF runs within it.

---

### Post by Daveski17 on 2022-01-16
> **DuckHook said:**
> Actually, I'm sure that you will. But if it helps, then this is the Firefox site from where you can download the standalone package: [https://pkgs.org/download/firefox](https://pkgs.org/download/firefox)
Just choose your distro/version, download into directory of your choice, then: ```
sudo apt install /path/to/directory/name_of_pkg
```…I suspect you will agree that it's not that hard.

Alternately, as per one of the posts in the other thread mentioned: ```
sudo add-apt-repository ppa:mozillateam/ppa
sudo apt update
sudo apt install firefox-esr
```This will add the Mozilla Team's PPA to your install, then install the ESR version of Firefox. You will need to remove your existing FF first—I suspect that the two don't like to coexist alongside each other, though I haven't actually experimented with it that way. If you don't want the ESR version and want to stick to vanilla FF, then your best bet is the first option.

Interesting: the few times I've tried it, I've never had problems.

Don't know about the snap and have no real interest, but adding the Brave repo is not hard either. Instructions here: [https://brave.com/linux/](https://brave.com/linux/)
I am exceedingly impressed with Brave. It is my fallback browser and has never failed me. I would use it for my main browser except that I am already so invested in FF and have grown so used to it. I'm a big Brave booster.

Or you could fire up a VM and have a look at it now. Though still in development, it is more than usable enough for you to get a sense of how FF runs within it.

OK thanks. I don't use the Terminal often. I'm not even sure what directory I'd download to for the first link. Would I have to make one? I have run a version of [Stellarium]("https://stellarium.org/en_GB/") on macOS from a directory/folder I created on the desktop. I'll have to look at running Firefox like this more intently. I really am a bog-standard non-anorak Linux user. I installed the PPA version of Stellarium on Ubuntu and considered it an accomplishment. Especially when it then updated lol. 

The bugs in Vivaldi aren't huge, but others have reported the same issues. It worked perfectly on Windows and Mac. It would be a great default Ubuntu browser otherwise. I live in hope.

I've seen that Brave link before. Would I copy/paste that Terminal code in five steps exactly as it is written?

---

### Post by DuckHook on 2022-01-16
> **Daveski17 said:**
> OK thanks. I don't use the Terminal often. I'm not even sure what directory I'd download to for the first link. Would I have to make one?
It's your choice and very flexible. Most people just use their ~/Download directory. In a typical Ubuntu install it was created by the initial install routine so it already exists. It's also the default directory that most browsers shove their downloads into.
> Especially when it then updated lol.
If you use the second option (adding the PPA) then automatic updates will be a similar experience.

The first option doesn't work quite that way but is just as convenient. When FF gets installed using the first option, it doesn't install into /usr/bin like native distro apps. Instead, it installs into /opt which is the directory that convention dictates to be used for user installed apps. This all happens behind the scenes and has little real world impact on you. The not&#8209;so&#8209;big change you will need to get used to is that FF will not update in the usual way. Instead, it will check for new updates every time you open it. If a new update is available, it will either (depending on how you set it) download the update automatically in the background then ask you if you want to install it, or ask you if you want to download the new upgrade. If you answer "yes" to either, then the next time you open FF, it will be the new one. Easy peasy.
> I've seen that Brave link before. Would I copy/paste that Terminal code in five steps exactly as it is written?
I would suggest that, for the sake of learning and security, you first take a bit of time to parse through what at first glance looks like gobbledegook, do some websearching to at least get a general idea of what those lines do, but then, it really is as simple as opening a terminal session, then copying and pasting those five lines into your terminal one after the other.

A summary of the five lines:

[LIST=1]
[*]You don't really need this one. These apps are already part of a typical Ubuntu desktop install (any flavour). Brave adds them for redundancy and because not all Debian type distros may have them.
[*]This adds Brave's gpg key to your keyring (very important for security and nothing will be permitted to happen without it).
[*]This adds Brave's repo to your sources.list.d so that apt can find it.
[*]This updates apt and allows it to find the new repo.
[*]This actually installs Brave.
[/LIST]

---

### Post by Daveski17 on 2022-01-16
> **DuckHook said:**
> It's your choice and very flexible. Most people just use their ~/Download directory. In a typical Ubuntu install it was created by the initial install routine so it already exists. It's also the default directory that most browsers shove their downloads into.

If you use the second option (adding the PPA) then automatic updates will be a similar experience.

The first option doesn't work quite that way but is just as convenient. When FF gets installed using the first option, it doesn't install into /usr/bin like native distro apps. Instead, it installs into /opt which is the directory that convention dictates to be used for user installed apps. This all happens behind the scenes and has little real world impact on you. The not&#8209;so&#8209;big change you will need to get used to is that FF will not update in the usual way. Instead, it will check for new updates every time you open it. If a new update is available, it will either (depending on how you set it) download the update automatically in the background then ask you if you want to install it, or ask you if you want to download the new upgrade. If you answer "yes" to either, then the next time you open FF, it will be the new one. Easy peasy.

I would suggest that, for the sake of learning and security, you first take a bit of time to parse through what at first glance looks like gobbledegook, do some websearching to at least get a general idea of what those lines do, but then, it really is as simple as opening a terminal session, then copying and pasting those five lines into your terminal one after the other.

A summary of the five lines:

[LIST=1]
[*]You don't really need this one. These apps are already part of a typical Ubuntu desktop install (any flavour). Brave adds them for redundancy and because not all Debian type distros may have them.
[*]This adds Brave's gpg key to your keyring (very important for security and nothing will be permitted to happen without it).
[*]This adds Brave's repo to your sources.list.d so that apt can find it.
[*]This updates apt and allows it to find the new repo.
[*]This actually installs Brave.
[/LIST]

OK thanks for the help and information. I really appreciate it.

---

### Post by John Nagle on 2022-01-16
Is there some way to report a bug in a snap? "Remarkable", in Snap form, is broken - it lacks the libraries that it needs to render the page. The author of Remarkable does not support the Snap. The Ubuntu Software Store has a botched version someone, not the developer, uploaded in 2019. So we don't even know what's in there. The Ubuntu software store does not seem to have a bug report area. 

Known problem on and off since 2016: [https://github.com/jamiemcg/Remarkable/issues/17](https://github.com/jamiemcg/Remarkable/issues/17)

---

### Post by Daveski17 on 2022-01-16
> **John Nagle said:**
> Is there some way to report a bug in a snap? "Remarkable", in Snap form, is broken - it lacks the libraries that it needs to render the page. The author of Remarkable does not support the Snap. The Ubuntu Software Store has a botched version someone, not the developer, uploaded in 2019. So we don't even know what's in there. The Ubuntu software store does not seem to have a bug report area. 

Known problem on and off since 2016: [https://github.com/jamiemcg/Remarkable/issues/17](https://github.com/jamiemcg/Remarkable/issues/17)

[This Remarkable?]("https://snapcraft.io/remarkable")

[There's this forum.]("https://forum.snapcraft.io")

---

### Post by Daveski17 on 2022-01-16
I've been experimenting with Vivaldi.

[ATTACH=CONFIG]289819[/ATTACH]

I think this may be a viable alternative to Firefox now I've figured out some workarounds.

---

### Post by Daveski17 on 2022-01-17
OK, Bugvaldi strikes again.

[ATTACH=CONFIG]289822[/ATTACH]

I've installed Brave from the Terminal. I'm officially impressed.

---

### Post by DuckHook on 2022-01-17
> **Daveski17 said:**
> &#8230;I've installed Brave from the Terminal. I'm officially impressed.
I was sold on it after visiting a streaming site (which shall remain nameless). Brave nuked all of the in&#8209;stream ads for my first experience of actual viewing bliss. This streaming site could detect ad blockers on other browsers and refused to stream until the blocker was turned off. But not with Brave. I believe that Brave does its magic mid stream, which won't prevent streams from starting, but will prevent them from interrupting with ads.

But it's main advantage is that it has no Google hooks. That's what makes it a no&#8209;brainer for me.

As I said, it would be my main browser were it not for the investment (and comfort) I've already made in FF. On my Android devices, Brave is my default browser.

---

### Post by Daveski17 on 2022-01-17
> **DuckHook said:**
> I was sold on it after visiting a streaming site (which shall remain nameless). Brave nuked all of the in&#8209;stream ads for my first experience of actual viewing bliss. This streaming site could detect ad blockers on other browsers and refused to stream until the blocker was turned off. But not with Brave. I believe that Brave does its magic mid stream, which won't prevent streams from starting, but will prevent them from interrupting with ads.

But it's main advantage is that it has no Google hooks. That's what makes it a no&#8209;brainer for me.

As I said, it would be my main browser were it not for the investment (and comfort) I've already made in FF. On my Android devices, Brave is my default browser.

Yes, I'm just getting used to it, but it does seem to be what I'm looking for. The Fx snap might be OK, but I feel happier now.

---

### Post by Daveski17 on 2022-01-17
How does the repo version of Brave update?

---

### Post by DuckHook on 2022-01-17
> **Daveski17 said:**
> How does the repo version of Brave update?
In the same way as all of your regular updates. Once you've gone through the process of adding an external repo to apt, it is treated in the same way as the standard repos that came along in your default install.

This is why security&#8209;savvy old&#8209;timers always tell people to not add external repos or PPAs willy nilly. After that initial decision to add the repo/PPA, it has the same access to your system as the default Ubuntu repos.

You don't have to do anything further at this point. From now on, when you (or the unattended-upgrade process) checks for updates, the Brave repo will be checked along with all of the others. If there is a new version or security patches, they will get installed automagically.

---

### Post by Daveski17 on 2022-01-17
> **DuckHook said:**
> In the same way as all of your regular updates. Once you've gone through the process of adding an external repo to apt, it is treated in the same way as the standard repos that came along in your default install.

This is why security&#8209;savvy old&#8209;timers always tell people to not add external repos or PPAs willy nilly. After that initial decision to add the repo/PPA, it has the same access to your system as the default Ubuntu repos.

You don't have to do anything further at this point. From now on, when you (or the unattended-upgrade process) checks for updates, the Brave repo will be checked along with all of the others. If there is a new version or security patches, they will get installed automagically.

OK thanks. I think Brave rocks. :guitar:

---

### Post by #&amp;thj^% on 2022-01-28
> **deadflowr said:**
> Advantage of snaps over PPA is strongly a development/developers advantage.
snaps only need a single version which will run across all releases. 
From a developer point of view it makes dealing with issues easier, since they do not have to deal with multiple releases and multiple versions.




So I guess you can take some of that as a few of the advantages and disadvantages of both.
Well Kind of I guess.
> The difference between a major and minor release is its planning, preparation and motivation. There is a major release cycle every few weeks, but sometimes we need an intermediate minor version release containing smaller changes and fixes.
[https://snapcraft.io/docs/snapd-release-process](https://snapcraft.io/docs/snapd-release-process)

> **ml9104 said:**
> @deadflowr:
Thanks for an informed reply.

[B][U]My dislike of snap was just a gut feeling at first, heightened by the messy look of my storage system (loop this, loop that...) when using it. And stacking abstraction layers on top of each other is totally user-unfriendly. Ubuntu is complicated enough as it is.
[/U][/B]
Thank You.

Kind of made me smile. 
I have machines that I need the snaps, But mostly on all other machines I run are Snap Free.:P

---

### Post by Tadaen_Sylvermane on 2022-01-29
> [COLOR=#000000]The FF workarounds are simple and easy (see above&#8209;referenced thread)—unless you actually prefer Chrome.[/COLOR][COLOR=#000000]

I know I'm a week behind the conversation here. Sometimes I'm just not in the mood to "work around". I'll hack at stuff often but get sick of it too. Just want it to work like it's supposed to sometimes.

I have exactly 2 complaints with Linux (far less than Windows obviously). They are as follows.

1. Working around various issues. It should just work to borrow the Apple tagline. Most of the time it does. In my experience though quite often I have to screw with something to get it to work.
2. Even with AMD working to provide the open source Mesa GPU drivers I still get worse gpu peformance than I do on Windows in almost everything. I rarely game these days but when I do it's a decent fps hit. Proton / Wine / Lutris makes this more noticeable.

To be fair with #1 though in Windows if something doesn't work then that is it. Linux at least you have some opportunity or ability to work around it.

[/COLOR]

---

### Post by kmkwood on 2023-01-25
Snap trashed my opera setting - bookmarks - passwords. I have yet to hear a SINGLE positive thing about snaps.
How can I get my settings back?

---

### Post by monkeybrain20122 on 2023-01-26
> **iamjiwjr said:**
> I delete the Firefox snap. Then I install no other snaps either. Then I install Synaptic via the terminal (I stay away from the Ubuntu software app). I open Synaptic and install the .deb Firefox from the Ubuntu repo.
.

There is no .deb for firefox in the Ubuntu repo. What you find in synaptic is a script that installs the firefox snap (like Chromium). There are some ppas for FF around, but I think they are either for the nightly or the esr (old) version, I haven't really checked.

You don't need any ppa or snap for Firefox, just grab the tarball from Mozilla, click on firefox then you are good to go. If you make ff the default browser it will create a .desktop file in ~/.local/share/applications (you may have to move it to /usr/local/share/applications if you use nautilus because I think it doesn't allow .desktop files to run in $HOME, I use nemo here) It will stay even if you choose other browsers as default later. When there is new version available, it gets updated automatically when you restart FF, or you can manually check for and upgrade by clicking  Help > About Firefox.

I also purged snap and I use some flatpaks.

---

### Post by Frogs Hair on 2023-01-30
To snap, or not to snap, that is the question:
Whether 'tis nobler in the mind to suffer
The slings and arrows of ,containerized software packages
Or to take arms against a sea of possible troubles
And by opposing end them...;)

I think flatpak and snap are going to be part of Linux package management for the foreseeable future.I have been running Firefox from the tarball folder for some time which works well in Budgie adding the icons in the main menu application. I found difficulty in adding an icon to favorites in Gnome except via plank dock.

---

### Post by DuckHook on 2023-01-31
> **kmkwood said:**
> …I have yet to hear a SINGLE positive thing about snaps…
[LIST=1]
[*]They do a pretty decent job of sandboxing an app so that rogue apps have a significant hurdle to overcome before they can infect your system.
[*]They allow the snap developer to maintain the app in a more timely fashion than relying on overworked Canonical mainline repo maintainers to get around to it.
[*]They allow more recent libraries or conflicting libs to be installed without clobbering your base system.
[/LIST]
I have not bothered listing the cons given that you are already aware of them but let's not just focus on the negatives. All new tech has pluses and minuses. I'm still on the fence about snaps in general, but trying to keep an open mind.
> **monkeybrain20122 said:**
> …There are some ppas for FF around, but I think they are either for the nightly or the esr (old) version…
The official Mozilla Team maintains a ppa that actually has the latest FF. However, this version will get clobbered by the Canonical repo version every time you run an update, thus replacing it with the snap version. There is [a workaround]("https://ubuntuhandbook.org/index.php/2022/04/install-firefox-deb-ubuntu-22-04/") which I've excerpted and summarize below:

[LIST=1]
[*]Add the Mozilla Team PPA:```
sudo add-apt-repository ppa:mozillateam/ppa
```
[*]Create the file:```
sudo nano /etc/apt/preferences.d/mozillateamppa
```
[*]Fill it with the following, which will set the PPA to a higher priority than the snap version of FF:```
Package: firefox*
Pin: release o=LP-PPA-mozillateam
Pin-Priority: 501
```
[*]Run the usual update:```
sudo apt update
```
[*]Install FF which should now draw the binary from the PPA instead of the standard repos:```
sudo apt install firefox
```
[/LIST]
TBH, while the workaround is not difficult, I have not actually implemented it. I find the ESR version of FF to be more than satisfactory. I don't need the latest and greatest, and the long term stability of the ESR is an unexpected bonus to me.

> You don't need any ppa or snap for Firefox, just grab the tarball from Mozilla, click on firefox then you are good to go.Many forum members use exactly this technique and report good results.
> **Frogs Hair said:**
> To snap, or not to snap, that is the question:
Whether 'tis nobler in the mind to suffer
The slings and arrows of ,containerized software packages
Or to take arms against a sea of possible troubles
And by opposing end them...;)
Frogs Hair: I love The Bard and don't know whether to laugh or to cry. I'll settle for just a small giggle. :p
> I think flatpak and snap are going to be part of Linux package management for the foreseeable future.
I recently had to nuke a snap app in Mrs DH's computer. I had set her up with a small and separate /var directory which ran out of room because of one snap app. I don't recall why I had originally hived off her /var into its own small partition, but there was a reason at the time and, usually, /var remains small unless a log file gets spammed.

This is yet another instance of snaps cause unnecessary trouble: they are resource pigs and make assumptions that will break some setups.

---

### Post by monkeybrain20122 on 2023-02-01
So I just accidentally stumbled on this problem and the fix, it may be of interest here.

If you apt remove snapd  forgetting the --purge flag  

you will find errors in your boot log that look like this
```

apparmor.systemd[468]: Error: At least one profile failed to load
systemd[1]: apparmor.service: Main process exited, code=exited, status=1/FAILURE
systemd[1]: apparmor.service: Failed with result 'exit-code'.
systemd[1]: Failed to start Load AppArmor profiles.
```

The fix is just running (if you have already removed snapd without --purge)
```
sudo dpkg --purge snapd
```

[https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1773515](https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1773515)


@DuckHook

Thanks for the info, but I am quite happy with running firefox standalone now. It updates automatically (unless you disable it) on restart.  I don't really see the point of a ppa (or snap or flatpak) It just add overheads and complications.

---

### Post by SeijiSensei on 2023-02-01
[quote[The official Mozilla Team maintains a ppa that actually has the latest FF. However, this version will get clobbered by the Canonical repo version every time you run an update, thus replacing it with the snap version. There is a workaround which I've excerpted and summarize below:[/quote]

Thanks for this, DuckHook. May all your future drives go straight.

I had a preferences file, but it had a 1001 priority. Changing it to 501 fixed the problem.

---

### Post by #&amp;thj^% on 2023-02-01
> **Frogs Hair said:**
> To snap, or not to snap, that is the question:
Whether 'tis nobler in the mind to suffer
The slings and arrows of ,containerized software packages
Or to take arms against a sea of possible troubles
And by opposing end them...;)

I think flatpak and snap are going to be part of Linux package management for the foreseeable future.I have been running Firefox from the tarball folder for some time which works well in Budgie adding the icons in the main menu application. I found difficulty in adding an icon to favorites in Gnome except via plank dock.

I flat Love it....):P
Frogs Hair way to think it out..:D

---

### Post by DuckHook on 2023-02-02
> **SeijiSensei said:**
> …Thanks for this, DuckHook. May all your future drives go straight.
That is about as likely as my winning the Nobel prize, but I appreciate your kind sentiment.

And may your future pupils be as worthy as their Sensei.

---

