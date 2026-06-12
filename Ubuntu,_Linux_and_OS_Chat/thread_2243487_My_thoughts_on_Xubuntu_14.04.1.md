---
title: "My thoughts on Xubuntu 14.04.1"
date: 2014-09-09
forum: Ubuntu, Linux and OS Chat
---

### Post by allcoms on 2014-09-09
I installed Xubuntu 14.04.1 i386 on my granddads netbook for him over the weekend so I wanted to give some feedback. Xubuntu is a great, lightweight, modern Linux desktop OS which I think is ideal for machines with limited resources such as Atom-based netbooks but I ran into a few issues and things I think could be improved.

My granddad has always used sleep/suspend when running Windows (7) on his netbook so he wanted to do the same under Xubuntu but we discovered that we could not disable the password on resuming from suspend without fully disabling the XFCE Light Locker so the screen saver is disabled too AFAIK. Is this a known bug?

Ristretto is the default image viewer in Xubuntu but I think its a bit too lightweight as it lacks a print option. I realise Xubuntu includes The GIMP but that is overkill if all you want to do is view and/or print. Does Xubuntu include the gimp-gutenprint package GIMP requires to print? Regardless, I would like to see Ristretto replaced by eog or a more capable GTK image viewer that can at least print as this is a basic desktop app requirement IMO.

It appears to me that Ubuntu Software Centre cannot install .deb packages downloaded from the net ie stuff not available in the repos and Xubuntu doesn't make this process easy for users as it doesn't include gdebi. gdebi won't install packages without the user entering their root password so I don't see any reason not to include it by default as it is only small and new users wouldn't know about it nor how to use dpkg.

Finally, I'd like to see VLC included as standard. VLC is not only one of the best media players for Linux but it is one of the most-well known and heavily used bits of free software across all platforms so it has the advantage that most people already know how to use it.

Thanks for your hard work team Xubuntu!

---

### Post by EuclideanCoffee on 2014-09-09
I believe the suspend bug is known. I read it on Ubuntu planet that there will be a fix soon.

There are also many questions posted about it, so simply googling, you'll come across one or two solutions.

[http://askubuntu.com/questions/453372/suspend-is-not-working-after-updating-to-ubuntu-14-04-from-13-10](http://askubuntu.com/questions/453372/suspend-is-not-working-after-updating-to-ubuntu-14-04-from-13-10)

---

### Post by ajgreeny on 2014-09-09
Try gthumb for image viewing and management. It willmprint and edit images,and photos easily and quickly, and it is fairly small and gtk based.

---

### Post by deadflowr on 2014-09-09
> [COLOR=#000000]It appears to me that Ubuntu Software Centre cannot install .deb packages downloaded from the net ie stuff not available in the repos [/COLOR]

Don't know about that.
Though the software center is much slower than either gdebi or dpkg, I do use it to install 3rd party deb packages.
(None of which have either been in the repos or will never be in the repos.)

but perhaps you've run into a few dependency issues...

---

### Post by Tar_Ni on 2014-09-09
> **allcoms said:**
> Ristretto is the default image viewer in Xubuntu but I think its a bit too lightweight as it lacks a print option. I realise Xubuntu includes The GIMP but that is overkill if all you want to do is view and/or print. Does Xubuntu include the gimp-gutenprint package GIMP requires to print? Regardless, I would like to see Ristretto replaced by eog or a more capable GTK image viewer that can at least print as this is a basic desktop app requirement IMO.

I think you should install **Shotwell** or **gThumb **then. The reason that Ristretto is provided as the default image viewer is because it is considered lightweight and intergrate perfectly with Xfce desktop environment. It doesn't mean you have to use it though. There other options available in the Software Center.

> **allcoms said:**
> It appears to me that Ubuntu Software Centre cannot install .deb packages downloaded from the net ie stuff not available in the repos and Xubuntu doesn't make this process easy for users as it doesn't include gdebi. gdebi won't install packages without the user entering their root password so I don't see any reason not to include it by default as it is only small and new users wouldn't know about it nor how to use dpkg.

Yes it can. I have downloaded Chrome and the Google Talk plugin on Xubuntu 14.04 as .deb packages from Google's website without any problem. Once you click on it, you have to wait about 30 secs before the download appears in the Software Center though. Skype download works as well.

> **allcoms said:**
> Finally, I'd like to see VLC included as standard. VLC is not only one of the best media players for Linux but it is one of the most-well known and heavily used bits of free software across all platforms so it has the advantage that most people already know how to use it.

I use VLC exclusively for watching videos too. I think it's the best video player around these days. But I don't think it is considered ''lightweight'' that is probably why the Xubuntu team does not shipped it as default but offer Parole instead.

Still, one of the first thing I do on Xubuntu/Lubuntu is to remove the default video player and install VLC and Banshee (for music management) instead. It takes a few more minutes but it's not the end of the world. ;)

BTW Totem (included as default in Ubuntu) is a great video player too. I think it comes down to a matter of preference.

---

### Post by allcoms on 2014-09-10
Thanks for the responses!

I've been using KDE/fluxbox pretty much exclusively for a number of years now so I'd forgot about gthumb - I use gwenview under KDE. gthumb, like eog, would be a better default image viewer than Ristretto.

It's good to hear USC does let you install debs. I think I only tried one (an EPSON scanner driver package) and when that failed to install I presumed this was an unsupported feature and it was a job for gdebi or dpkg.

ruze:

As I said in the OP, I did get suspend working without prompting for a password but only after disabling Light Locker, as is recommended in the link you posted. It's likely an upstream bug rather than something specific to Xubuntu.

Tar_Ni:

I realise Xubuntu is targetted at lower spec machines and so most of the apps are quite lightweight (eg Abiword instead of LO Writer) but that is not a hard and fast rule for the distro as proved by the inclusion of both Firefox and GIMP. There are much more lightweight alternatives to these two apps but the team have done the sensible thing in foregoing lightweight for functionality in some cases and I'd recommend they do the same for VLC. Both FF and GIMP are more bloated, heavyweight apps than VLC - VLC runs perfectly well on older machines or machines with a restrictive amount of RAM whilst there most definitely are browsers that use less RAM etc than Firefox.

I'm just thinking about first impressions and people new to Linux who may not put the time into researching for alternative apps and just presume the distro will include the best apps for the job, which it should.

---

### Post by Tar_Ni on 2014-09-10
> **allcoms said:**
> I realise Xubuntu is targetted at lower spec machines and so most of the apps are quite lightweight (eg Abiword instead of LO Writer) but that is not a hard and fast rule for the distro as proved by the inclusion of both Firefox and GIMP. There are much more lightweight alternatives to these two apps but the team have done the sensible thing in foregoing lightweight for functionality in some cases and I'd recommend they do the same for VLC. Both FF and GIMP are more bloated, heavyweight apps than VLC - VLC runs perfectly well on older machines or machines with a restrictive amount of RAM whilst there most definitely are browsers that use less RAM etc than Firefox.

I really don't know why GIMP has been choosed over something more lightweight such as mtPaint Graphic Editor. That's a good question.

As for Firefox though, I think it's reasonable to say that people wants a full-featured browser for their everyday uses. Firefox is known to work pretty decently on older hardware and has a LOT of extensions for basically every need. Plugins support is another matter to consider. You just don't get that with the Midori browser for exemple. There is no third-party extensions available and the browser is not fully compatible with various online services.

> **allcoms said:**
> I'm just thinking about first impressions and people new to Linux who may not put the time into researching for alternative apps and just presume the distro will include the best apps for the job, which it should.

Well there is no Linux distros that will satisfy everyone in terms of preinstalled apps. The devs offer what they think could work best for people according to the desktop environment and the aims of the OS. That can be a very subjective process. But in the end, just like for Windows or OSX, you still have to install the apps you need and prefer and in some cases, remove what you don't want. In the Ubuntu family, users have access to a Software Center which is very easy to use which offer *many* open-source apps, that can be installed with a single click.

You may like VLC as many people do, but what if others prefer Totem or Mplayer instead? Both are great video players too.

---

### Post by Elfy on 2014-09-11
> **allcoms said:**
> [snip]  I'd recommend they do the same for VLC[snip] 

[https://wiki.ubuntu.com/Xubuntu/StrategyDocument#Seeds_.26_Composition](https://wiki.ubuntu.com/Xubuntu/StrategyDocument#Seeds_.26_Composition)

---

### Post by allcoms on 2014-09-11
Tar_Ni:

I agree that mtpaint makes more sense to include than the GIMP for a distro that aims to be lightweight.

I don't fully trust any browser except FF/Iceweasel. Everything else (inc. Chrome / Chromium) is too buggy, instable or incomplete so I'm gad they relax their rules sometimes.

Elfy:

Thanks for the link. I only ever use VLC or smplayer for media playback but it seems neither of those will ever be included in Xubuntu as they're both Qt apps.

---

### Post by Tar_Ni on 2014-09-11
> **allcoms said:**
> Tar_Ni:I don't fully trust any browser except FF/Iceweasel. Everything else (inc. Chrome / Chromium) is too buggy, instable or incomplete so I'm gad they relax their rules sometimes.

It has never been my experience that Chrome or Chromium were too buggy or unstable for daily usages, all the contrary actually. In my opinion, they are the best browsers available for Linux at this point. Plus, both have the latest Pepper Flash plugin (15.0.0.52) and a great PDF viewer. :)

---

### Post by mastablasta on 2014-09-12
there is an imageviewer that is called imageviewer I believe or similar. lightweight and works well. I use it on KDE, I think gvenview is too heavy and also you can really easily change the picture and save changes by accident.

VLC is a QT (used in KDE, LXQT...) application  while XFCE uses GTK (used in Gnome, XFCE...) applications.

---

