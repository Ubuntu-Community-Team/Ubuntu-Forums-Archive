---
title: "Oh Snap!"
date: 2019-09-19
forum: Ubuntu, Linux and OS Chat
---

### Post by tinker123 on 2019-09-19
I was not aware of Ubuntu Snap until I read this very short article today

[https://betanews.com/2019/09/19/ubuntu-canonical-5-snaps-linux/](https://betanews.com/2019/09/19/ubuntu-canonical-5-snaps-linux/)

Do I correctly understand what Snap is?

Instead of downloading an rpm, deb, etc an linux os would download a snap, a zip file in a format any distro can handle.
Once downloaded the native package manager would unzip it and distribute the files per the eccentricities of the particular distro?

Thanks.

---

### Post by Frogs Hair on 2019-09-19
If using a current version of Ubuntu the terminal is handy for locating and installing snaps. Snap packages pose a security concern for some users, but have had no problems. Some default packages are now snap and to locate them use the snap list command.     [https://snapcraft.io/store](https://snapcraft.io/store)

```
snap find 
``` ```
snap find package-name
``` ```
sudo snap install package-name
``````
sudo snap remove package-name
``````
 snap list
```

---

### Post by Dennis N on 2019-09-19
You don't download them manually; they are installed by the snap manager, which is already installed and ready to go. First thing to install is the snap-store so you can browse the available packages.

```
snap install snap-store
```

note that sudo isn't needed here!

---

### Post by deadflowr on 2019-09-19
snaps are not zips.
snaps are their own file structure.
snaps require snapd to be installed.

snaps have their own package management system.

---

### Post by mastablasta on 2019-09-20
it is kind of like portable apps in windows. not really but they act similarly. self contained and for that reason you can have multiple versions of same app on linux.

similar stuff: flatpack, appimage, zero install...

---

### Post by Shibblet on 2019-09-20
I personally like the idea of Snaps.  They are [COLOR="#FF0000"]***supposed to be***[/COLOR] completely self-contained, and require no additional dependencies.

---

### Post by deadflowr on 2019-09-20
I think appimages are the only format that are truly (or at least as close to as possible) self-contained.
Snaps and flatpaks both require runtimes outside of the snaps.

---

### Post by #&amp;thj^% on 2019-09-20
> **deadflowr said:**
> I think appimages are the only format that are truly (or at least as close to as possible) self-contained.
Snaps and flatpaks both require runtimes outside of the snaps.

+1 I'm glad you added that.
 The key idea of the AppImage format is one app = one file. Every AppImage contains an app and all the files the app needs to run. In other words, each AppImage has no dependencies other than what is included in the targeted base operating system(s).

AppImage format is ideal for upstream packaging, which means that you get the software directly from the original author(s) without any intermediaries, exactly in the way the author(s) intended. And quickly.

---

### Post by Skaperen on 2019-09-20
the snaps i've seen are too small to be completely self-contained.

what does "self-contained" mean?  that it runs with nothing else needed?  not even a kernel?  as in a VM? oh wait, it needs a VM?

---

### Post by mastablasta on 2019-09-23
> **Skaperen said:**
> 
what does "self-contained" mean?  that it runs with nothing else needed?  not even a kernel?  as in a VM? oh wait, it needs a VM?

it's sand box. stuff inside doesn't affect the OS. yes it seems it does have some overhead.

kind of similar like jail in BSD or similar but not the same as sand box in Comodo security suite (on windows).

i wonder, could you then use Ubuntu 12.04 with latest stuff packed in appimage?

---

### Post by lammert-nijhof on 2019-09-23
Snaps
- do run on any distro, except the obsolete ones not supporting snaps (Ubuntu first support 14.04). 
- run sandboxed, so in a kind of container, 
- are more secure against attacks 
- can't crash the system 
- comes with its own package manager snapd
- runs from a kind of read only virtual disk.
- are updated automatically and only the modified parts of the virtual disk are sent.
- you will have the newest version of the App, also if for deb files only an older version is supported,
- full automatic and manual snapshot support and rollback to a previous version of that virtual disk
- have a central storage for distribution, to avoid websites that distribute malware.

Flatpack and Appimage are more vulnerable for attacks and both do not support snapshots. Flatpack only supports KDE, Gnome and FreeDesktop and their security is somewhat questionable. Appimage can be run on any distro by making the file executable, but then you have to add a link to the image in the menus or docks yourself. "Appimaged" should solve that, but than you have to install it like snapd. AppImage programs are not sandboxed.

---

### Post by mastablasta on 2019-09-24
well that pretty much explains it all. thank you.

snaps seem to be safer, better option. 
appimage seems to be an option for apps not needing the internet connection.

---

### Post by hk42 on 2019-10-05
I found that appimage packages can even run if they are stored on a 
samba NTFS share.
So yes they are big but you can share them between several machines.
In my case (mini PC)it is quite helpful.

---

### Post by dustyt on 2020-02-18
I haven't decided which side of the fence I am on with this.

I do get the suggestion that this is good for app development and deployment across distros and that sort of thing, you know the positive stuff that is put on our dish to eat up.

I do wonder though what the flip side of this package management is though? 

I am all for furthering things, more better easier, yada yada. I just can't help but think of this though. I guess it is because I changed mobile platforms a short time ago and I'm not to happy. I am noticing exploitation, and also less functionality and capability with the same things on a different platform. I didn't foresee that coming when I changed. So maybe that makes me be more questioning on this sort of stuff now. IDK.

---

### Post by mastablasta on 2020-02-18
> **dustyt said:**
> 
I do wonder though what the flip side of this package management is though? 


- larger packages for application (so app get's bigger in size).
- certain things need to be running and loaded. as i understand this increases boot time and potentially burdens the system with additional services running in background. 

i guess it depends on how much of this is added to the OS. if the difference is tiny then it is not that important as the benefits should be a lot bigger. but if we talk 10% CPU load increase and huge apps size then it's an issue.

perhaps there are more downsides but these get mentioned often.

---

