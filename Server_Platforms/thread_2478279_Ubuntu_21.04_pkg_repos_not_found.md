---
title: "Ubuntu 21.04 pkg repos not found"
date: 2022-08-22
forum: Server Platforms
---

### Post by bad-nixguy on 2022-08-22
Hello all,

Trying to find some answer here. Will be really appreciate any idea/help.

My server runs on OVH Cloud and has Ubuntu 21.04 hirsute. When I'm trying to update repos or install any pkg - I see this:


```

sudo apt-get update
Get:1 https://download.docker.com/linux/ubuntu hirsute InRelease [48.9 kB]
Ign:2 http://security.ubuntu.com/ubuntu hirsute-security InRelease
Ign:3 http://nova.clouds.archive.ubuntu.com/ubuntu hirsute InRelease
Err:4 http://security.ubuntu.com/ubuntu hirsute-security Release
  404  Not Found [IP: 91.189.91.38 80]
Ign:5 http://nova.clouds.archive.ubuntu.com/ubuntu hirsute-updates InRelease
Ign:6 http://nova.clouds.archive.ubuntu.com/ubuntu hirsute-backports InRelease
Err:7 http://nova.clouds.archive.ubuntu.com/ubuntu hirsute Release
  404  Not Found [IP: 91.189.91.122 80]
Err:8 http://nova.clouds.archive.ubuntu.com/ubuntu hirsute-updates Release
  404  Not Found [IP: 91.189.91.122 80]
Err:9 http://nova.clouds.archive.ubuntu.com/ubuntu hirsute-backports Release
  404  Not Found [IP: 91.189.91.122 80]
Hit:10 http://ppa.launchpad.net/neovim-ppa/unstable/ubuntu hirsute InRelease
Reading package lists... Done
E: The repository 'http://security.ubuntu.com/ubuntu hirsute-security Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://nova.clouds.archive.ubuntu.com/ubuntu hirsute Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://nova.clouds.archive.ubuntu.com/ubuntu hirsute-updates Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://nova.clouds.archive.ubuntu.com/ubuntu hirsute-backports Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

```

sudo apt-get install zip
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libice6 libmsgpackc2 libsm6 libtermkey1 libunibilium4 libvterm0 libxmu6 libxt6 lua-luv python3-greenlet
  python3-msgpack python3-neovim python3-pynvim x11-common xclip
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  zip
0 upgraded, 1 newly installed, 0 to remove and 28 not upgraded.
Need to get 162 kB of archives.
After this operation, 646 kB of additional disk space will be used.
Err:1 http://nova.clouds.archive.ubuntu.com/ubuntu hirsute/main amd64 zip amd64 3.0-12
  404  Not Found [IP: 91.189.91.122 80]
E: Failed to fetch http://nova.clouds.archive.ubuntu.com/ubuntu/pool/main/z/zip/zip_3.0-12_amd64.deb  404  Not Found [IP: 91.189.91.122 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

I'm confused... since current OS release is NOT LTS so after "expiration" date they will remove all repos and user will no longer have ability even to update system to 21.10?
Maybe there is a solution how to repoint pkg manager to archived repos of particular release? (I don't need new pkgs, I'm fine with a snapshot of what repos have as of now).
I don't believe maintainers just remove each time whole pkgs base for non LTS releases.

Any thoughts?

---

### Post by guiverc on 2022-08-22
Ubuntu 21.04 (*along with all flavor*s) is [B][I]End-of-Life

[/I][/B] - [https://fridge.ubuntu.com/2022/01/21/ubuntu-21-04-hirsute-hippo-end-of-life-reached-on-january-20-2022/](https://fridge.ubuntu.com/2022/01/21/ubuntu-21-04-hirsute-hippo-end-of-life-reached-on-january-20-2022/)

- [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Only the first releases on an *even* year (ie. 6.06, 8.04, 10.04, 12.04, 14.04, 16.04, 18.04, 20.04 & 22.04) are LTS releases.

**After** a release reaches EOL, mirrors are free to *drop* the release, whilst the main archive gets moved to old-releases.

You had six months from EOL to perform the *release-upgrade*, but that door closed once [21.10 reached EOL]("https://fridge.ubuntu.com/2022/07/19/ubuntu-21-10-impish-indri-end-of-life-reached-on-july-14-2022/").

In future, remember 21.04 tells you it's the 2021-April release, with 9 months of support, thus adding 9 to 2021-April gives 2022-January for EOL even if you don't know the day of the month. Most releases are 3rd Thursday if you need that; though release notice & warning notices of EOL (six weeks before EOL) give the actual date.   The QA-tested & supported upgrade path itself is gone if the next release isn't a LTS release six months after that (*when 21.10 or 2021-October + 9 months reaches EOL*).

[I]Note:  I added bold to the word **after**, as the date on which these moves drops occurs isn't defined, except it occurs AFTER the EOL, so it maybe the next day (as per 17.04), or months later... The period can vary depending on any issues discovered in the releases final days.  

See the provided EOLUpgrades link[/I]

---

### Post by bad-nixguy on 2022-08-22
Thank you for the info, it's really very useful for me!

Does community have any info about available mirrors/repositories which I can try to search for 21.04 support?

---

### Post by bad-nixguy on 2022-08-22
Found this [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)
Will take a look maybe it's what I'm looking for.

---

### Post by guiverc on 2022-08-22
That is a **list of mirrors** for *supported* releases, as 21.04 (*hirsute*) is EOL, none are required to provide support for *hirsute*, but note if any do have support for it, they may not be *updated (ie. poorly maintained* *given it's not been dropped*), and support can be dropped anytime.

I'd use the moved main archive ([https://old-releases.ubuntu.com/](https://old-releases.ubuntu.com/)) as per the EOLUpgrades link I provided.   But note, many tools check status via the [https://changelogs.ubuntu.com/meta-release](https://changelogs.ubuntu.com/meta-release) which shows 21.04 is EOL, as is 21.10 where *release-upgrade* was intended to go.

---

### Post by bad-nixguy on 2022-08-22
Before your last post googled another one blog which says replace existing links in /etc/apt/sources.list to be based on old-releases.ubuntu.com url, also double checked your EOLUpgrades link (sorry didn't pay enough attention to it before) and yes, it says the same.

Yesterday I was reading this instruction [https://help.ubuntu.com/community/ImpishUpgrades](https://help.ubuntu.com/community/ImpishUpgrades) and there was no info about this step. Now I tried to follow different links on it and finally 2nd jump was to EOLUpgrades. Oh, it's harder then Arch :)

Long story short - after I've done with all url replaces I was able to do "apt update" and install small pkg.

Thank you for your help!

---

### Post by guiverc on 2022-08-22
Well done, but I hope your system is **off-line** given you're using an *unsupported* and *unpatched *(*for security flaw*s) kernel & packages.

The *ImpishUpgrades* link (*just like later JammyUpgrades link for upgrading 21.10 to 22.04*) assume you're running the upgrade **before** the release goes EOL as intended (*when QA & support ends for the release*) and this EOLUpgrades isn't required.  

Post-EOL upgrades aren't encouraged, as all QA (*Quality Assurance testing*) has completed; and thus its possible extra problems can occur that weren't considered during the supported period of the release.

---

### Post by bad-nixguy on 2022-09-06
All systems are up as of now, because I was able to update them, thank you again.

These are steps which helped me out (in case of someone will be reading this for the same purpose):

1. in case of using EOL release - tweak /etc/apt/sources.list to have **old-releases** in all urls (to be like [http://](http://)[COLOR=#333333][FONT=Ubuntu]**old-releases**.ubuntu.com/*)
[/FONT][/COLOR]2. ```
sudo apt-get update && sudo apt-get dist-upgrade
```
3. ```
sudo apt install update-manager-core
```
4. ```
sudo shutdown -r now
``` (think optional, but nice to have in case of new kernel was available or similar important stuff occurred)
5. ```
do-release-upgrade
``` will do update/migration for you (sometimes it's not possible and you need to download upgrade tool for your current release and use it)

As was mentioned before by guiverc - more info about EOL update process is [here]("https://help.ubuntu.com/community/EOLUpgrades")

P.S Only one strange thing I have with one server - gnome env. was installed for some reason...
I was using xfce desktop env. for one user but after update to jammy I've notice that gnome DE was installed for admin's account automatically.
And that's not a huge problem I think, but the real problem was that server was down after some time of being in front of "virtual monitor". I tried to find any power saving settings and saw "Automatic Suspend" option was turned on.
So the server was down because if it (even if some processes were working). That's not right.

---

