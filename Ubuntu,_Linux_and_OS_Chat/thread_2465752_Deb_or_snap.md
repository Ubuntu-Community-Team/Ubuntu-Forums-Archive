---
title: "Deb or snap"
date: 2021-08-10
forum: Ubuntu, Linux and OS Chat
---

### Post by thumper76 on 2021-08-10
It now seems that almost every package has the option to be installed as as a Deb or a Snap. Deb is the older way and can have a problem with dependencies while Snap is guaranteed to have all the dependencies, but seems to be bloated as dependencies are duplicated in each package. So what do people prefer Deb or Snap?

---

### Post by The Cog on 2021-08-10
I strongly dislike snaps:
* They are slow to start up
* They don't always work, can't read/save files sometimes
* They fill up df, lsblk, mount command output with garbage
* They won't necessarily get updated when vulnerabilities in libraries get fixed

---

### Post by deadflowr on 2021-08-10
*Thread moved to **Ubuntu, Linux and OS Chat***

---

### Post by ajgreeny on 2021-08-10
I do not have any snap packages on my Xubuntu 20.04 and have removed snapd so the complete snap system is gone from my installation. This is just my personal view of the snap system and I am very well aware than many other users do not have any problem installing and using snaps.

I originally installed chromium using apt, not realising at that time that even doing that installed the snap version, and I did not look in detail at the terminal output when installing; big mistake!
Only when I attempted to connect chromium to parts of the filesystem not allowed by snaps did I realise that I actually had a snap version. I also did not like the totally automatic and forced upgrade of snap versions with no control by the user.

So I removed the snap and everything else related to snaps and in the case of chromium I now use a PPA version, a .deb package, which is working with no difficulties or problems.

The current snaps have, I believe, moved on and there are ways to make or allow the applications to connect with the filesystem, or at least with the users home folders, though I may even be incorrect about that, and I don't have any snaps to test that theory.

There have been numerous discussions on the merits (or not) of snaps which you can read in great detail using ***Advanced Search*** at the top right of every forum page using snap as search term searching for Titles only. That way you can make up your own  mind.

---

### Post by The Cog on 2021-08-10
@ajgreeny How do you get that chromium PPA? I thought the PPAs had been discontinued. 
I use one web site that appears to work better in chromium than in firefox.

---

### Post by ajgreeny on 2021-08-10
Sorry, I should have said where the chromium comes from but forgot when I finished the post.

The PPA I use is [https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev](https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev) which has versions for all current supported Ubuntu versions.
Curently in 20.04 it is supplying ***Version 92.0.4503.0 (Developer Build) Ubuntu 20.04 (64-bit)*** which means it is a higher version than the snap which shows in the repos, though not in my repos as I have removed snapd so chromium is not showing, only chromium-browser from the PPA.

---

### Post by The Cog on 2021-08-10
Thank you for the link. I will use that.

---

### Post by monkeybrain20122 on 2021-08-10
debs are smaller and have better integration with the system but tend to be outdated. So if I want something to be always up to date my first choice would be a ppa, if that doesn't exist and I don't want to or can't compile from source then I would look for a flatpak. Flatpak. I don't like the fact that snap mounts a whole bunch of volumes at startup and all the time and managing access seems to be complicated, flatpak is much cleaner and you can easily control access with a unified gui (flatseal)

---

### Post by monkeybrain20122 on 2021-08-10
> **ajgreeny said:**
> Sorry, I should have said where the chromium comes from but forgot when I finished the post.

The PPA I use is [https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev](https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev) which has versions for all current supported Ubuntu versions.
Curently in 20.04 it is supplying ***Version 92.0.4503.0 (Developer Build) Ubuntu 20.04 (64-bit)*** which means it is a higher version than the snap which shows in the repos, though not in my repos as I have removed snapd so chromium is not showing, only chromium-browser from the PPA.

Actually I would suggest the [beta ppa]("https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-beta") over the -dev one. I don't use chromium myself but in answering a few threads on UF I temporarily installed it for some tests. It seems that some people use Chromium because it supposedly supports vaapi hardware decoding for intel and amd gpu so I tried to enable that. Turned out vaapi worked in beta but not the dev branch. In any case, vaapi now works in firefox and all chromium based browsers (google-chrome, brave-browser and Vivaldi except maybe Opera,--though I haven't tested it) so that may be less of a reason to use chromium (of course people might have other reasons)

---

### Post by guiverc on 2021-08-10
Don't forget *snaps* have security benefits, so running things like a browser in a *snap* achieves a *higher* level of security than running the same package from *deb*.

 As *snaps* run in containerized environments they tend to use more resources, so I personally avoid them on boxes with 2GB of RAM or less (*few boxes have that limited RAM anyway*), even consider not using them with 4GB - but they do have *security* benefits that make them worth of consideration if you've a machine with a decent RAM size.

In the end, it's your choice.   (*pros & cons as with everything*)

---

### Post by ajgreeny on 2021-08-11
I have used both the dev and beta PPAs from that same person and didn't find any differences between them of consequence.
I seldom use chromium anyway except for one or two sites where it works and firefox doesn't.

---

### Post by TheFu on 2021-08-11
> **thumper76 said:**
> It now seems that almost every package has the option to be installed as as a Deb or a Snap. Deb is the older way and can have a problem with dependencies while Snap is guaranteed to have all the dependencies, but seems to be bloated as dependencies are duplicated in each package. So what do people prefer Deb or Snap?

Snaps without all the dependencies are still common IME.  About 80% of snaps I've tried do not work on my systems. The logs usually show a cryptic (meaning I don't understand) message about apparmor=DENIED.  Not all dependencies are duplicated. Some of the larger packages that are dependencies have snap packages of their own and get used by many other snaps.

Snaps don't work with data outside HOME directories and refuse to work with **any** NFS provided data.  On our network, we have over 30TB of data available via NFS ... and none of that can be accessed by any snap package installed programs.  Exactly where do video editors expect people to have 20G video files?

I prefer deb/APT packages. If I want the constraints that are mandatory with snaps, then I can use firejail or some other technique to have those constraints. Mandated constraints without any override possibility is not the Linux/Unix way.  Power to the end-user!

There are competitors to snaps which either do not have these constraints (AppImages) or allow local control (flatpaks).  It is the tools that Canonical only provides as snaps which cause me the most pain. I'd love to use lxd more, but it is only provided as a snap. I've failed to get it working on 2 of 3 systems here.  They use home directories that are NFS.

Snaps patch when they like with the only way to prevent the patching is to cut off network access to the snap patch server(s).

And I miss the federated idea of PPAs.  Right now, there is only 1 snap application server - owned and run by Canonical. The lack of 3rd parties in control of snap delivery is very concerning.  Without PPAs, people who want to use Chromium-Browser would be stuck using the snap version provided by Canonical.  Thank DOG for PPAs!!!

The ideas that Snaps have are not bad. They seem to be designed from a cell-phone standpoint where external and networked storage just aren't possible.  I see where Ubuntu Core, which is their IoT effort, intends to only allow snap packages for application deployment.  I don't know enough to be afraid or if snaps are the greatest solution possible in that specific space. Probably both.

Some command aliases to remove the snap and some other crap in outputs.
```
alias lsblkt='lsblk -e 7 -o name,size,type,fstype,mountpoint'
alias dft='df -hT -x squashfs -x tmpfs -x devtmpfs'
```

---

### Post by monkeybrain20122 on 2021-08-11
> **TheFu said:**
> Snaps without all the dependencies are still common IME.  About 80% of snaps I've tried do not work on my systems. The logs usually show a cryptic (meaning I don't understand) message about apparmor=DENIED.  Not all dependencies are duplicated. Some of the larger packages that are dependencies have snap packages of their own and get used by many other snaps.

Snaps don't work with data outside HOME directories and refuse to work with **any** NFS provided data.  On our network, we have over 30TB of data available via NFS ... and none of that can be accessed by any snap package installed programs.  Exactly where do video editors expect people to have 20G video files?


Ye these are some of the issues (among others) with snaps. I think you can configure their access to volumes and file systems with some obscure ways (I don't know since I don't use snaps) and there are issues for external plugins. By looking at the gimp snap threads on github it seems that they have to support plugins on a case by case, ad hoc basis. I don't know whether you can install an adblocker on chromium snap. At least in terms of configuring file access flatpak is much better.

---

### Post by TheFu on 2021-08-11
> **monkeybrain20122 said:**
> Ye these are some of the issues (among others) with snaps. I think you can configure their access to volumes and file systems with some obscure ways (I don't know since I don't use snaps) and there are issues for external plugins. By looking at the gimp snap threads on github it seems that they have to support plugins on a case by case, ad hoc basis. I don't know whether you can install an adblocker on chromium snap. At least in terms of configuring file access flatpak is much better.

Specific locations are hard coded inside the snap constraint system.
/home/ is enabled by default

Both /mnt/ and /media/ can be allowed by the snap creator or not.  Often, snap creators need to be pressured into allowing ... let me look it up ... _removable-media_ connections.  For example, 
```
snap connect chromium:removable-media
```
If the chromium snap wasnt setup by the snap creator to allow that access, then it won't be possible. Period.

[Https://snapcraft.io/docs/snap-confinement](Https://snapcraft.io/docs/snap-confinement) has more information about the constraints, defaults and options.

Again, there is no way to allow NFS storage access, even if it is put under /mnt/ or /media/ or even /home/.

With something like firejail, we can make a virtual file system overlay that is what a program sees or provide that with write access to 1 directory of our choosing or allow read-access to everything or allow read-access to nearly everything an write access to 1 location.  It is all under our control.  Want to setup a browser with addons that cannot be modified inside the environment and nothing newly installed will be saved, fine. That is possible.

In all honestly, much of my complaint about snaps is they don't allow saving to /tmp/ by default.  Old-Unix guys have used /tmp/ for downloads and other temporary files for decades.  That's sorta the entire purpose for /tmp which is castrated by snaps.  I try things out in /tmp/ when I'm not certain it works.  /tmp/ is integral to my work-flow ... along with using NFS storage.

How important is NFS?
```
Filesystem                      Type  Size  Used Avail Use% Mounted on
istar:/d/D1                     nfs4  3.5T  3.5T  3.4G 100% /d/D1
istar:/d/D2                     nfs4  3.6T  3.5T   37G  99% /d/D2
istar:/d/D3                     nfs4  3.6T  3.6T   43G  99% /d/D3
romulus:/Data/r2                nfs4  1.3T  1.2T   15G  99% /S
romulus:/raid/media/Music       nfs4  1.8T  1.7T   19G  99% /M
romulus:/raid/media             nfs4  1.8T  1.7T   19G  99% /R
```
Only about 20TB of importance.  Also note how none of that storage is under /mnt/ or /media/?  That is because I follow standards, unlike Canonical.
[https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard#Directory_structure](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard#Directory_structure) 
>     /media	Mount points for removable media such as CD-ROMs (appeared in FHS-2.3 in 2004).
    /mnt	Temporarily mounted filesystems. 

---

### Post by grahammechanical on 2021-08-11
I do not wish to get involved in this discussion except to say this: I  use the zoom-client snap. After installing, when I locate zoom-client in  Ubuntu Software there is a tab that gives me control over a variety of  permissions. So, I suggest that some of the issues that have been raised  regarding snap apps might be resolved by opening up the snap app's page  in Ubuntu Software.

Snaps apps developed out of the "click" app  packaging method that was used on early versions of Unity 8 for the  Ubuntu phone OS. There was an idea to have on the phone a "media hub."  If an app tried to access folders outside its defined area the media hub  would trigger a request for user authentication.  This idea has not  been implemented on Ubuntu Desktop and is not necessary on IoT devices  which usually only run one application. 

It is certainly possible  for developers other than Canonical to setup snap stores. The Canonical  snap store is a convenient way for a developer to get their snap app to  market. An organization can have its own IoT app store. And since IoT  Ubuntu is snap based Ubuntu core those apps will be snaps.

[https://ubuntu.com/internet-of-things](https://ubuntu.com/internet-of-things)

Regards

---

