---
title: "When I check if i have falsh installed this is what I get  message .... &quot;its virtual&quot;"
date: 2019-08-10
forum: Security
---

### Post by jedi123 on 2019-08-10
$   [B] apt show adobe-flashplugin
[/B]

Package: adobe-flashplugin
State: not a real package** (virtual)**
N: Can't select candidate version from package adobe-flashplugin as it has no candidate
N: Can't select versions from package 'adobe-flashplugin' as it is purely** virtual**
N: No packages found

What does virtual mean, I am virtually perplexed.

---

### Post by cruzer001 on 2019-08-11
Maybe this will explain it.
> Pure virtual packages is the number of packages that exist only as a virtual package name; that is, packages only "provide" the virtual package name, and no package actually uses the name. For instance, "mail-transport-agent" in the Debian system is a pure virtual package; several packages provide "mail-transport-agent", but there is no package named "mail-transport-agent".

Single virtual packages is the number of packages with only one package providing a particular virtual package. For example, in the Debian system, "X11-text-viewer" is a virtual package, but only one package, xless, provides "X11-text-viewer".

Mixed virtual packages is the number of packages that either provide a particular virtual package or have the virtual package name as the package name. For instance, in the Debian system, "debconf" is both an actual package, and provided by the debconf-tiny package.
```
man apt-cache
```

---

### Post by jedi123 on 2019-08-11
Thanks.

---

### Post by deadflowr on 2019-08-11
More likely you don't have the Canonical Partners repos enabled.
That's where the adobe-flashplugin package is and it's not enabled by default.

The virtual package output is probably because Ubuntu does have another flash installer package in a repo that is enabled.
flashplugin-installer is in the universe repository.
Both package provide flashplugin-nonfree.

The difference between the adobe-flashplugin package and the flashplugin-installer package is the flashplugin-installer package installs the old npapi (firefox plugins) only.
Whereas adobe-flashplugin installs both the npapi version and chrome's ppapi version (aka pepperflash)


EDIT:
For what it's worth
```
apt show <package>
```
does not show or tell anything about installed packages.
It only outputs information about packages in the archives.

Now
```
 apt policy <package>
```
will show whether a package is installed or not.

---

### Post by jedi123 on 2019-08-11
Thanks . The reason why I ask this is because I added "restricted-extras" packages, then 15 minutes later , foudn out that "flash" is in the restricted packages. Wiped ubuntu again, then reinstalled then  added codecs like this 

[B]
 
 sudo apt install  chromium-codecs-ffmpeg-extra gstreamer1.0-fluendo-mp3  gstreamer1.0-libav gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly  lame libavcodec-extra libdvdread4
[/B]
Thats where the question comes from.  Would you see any danger by addding codecs this way ?

---

### Post by deadflowr on 2019-08-11
Not a problem.
Ubuntu-restricted-extras is just a meta-package that makes it easy to install those packages in one fell swoop.
(And truly, that's all it does.
It never gets updated but the packages it provides do.)

Also, fwiw if you want to play restricted dvds you might consider installing the libdvd-pkg package.
See here about that:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")

---

### Post by jedi123 on 2019-08-11
Just once clarification, even if I install the  restricted-extras package, **it would by default still ask me to activate  flash per each individual use **, and **not automatically activate flash** ..correct?

---

### Post by cruzer001 on 2019-08-11
In Firefox

    Click on the FireFox menu and go to Add-ons
    Then select Plugins, r-click on flash and choose "Ask first"

---

### Post by walts48 on 2019-08-12
Something to be aware of for the next version of Firefox.

[https://www.fxsitecompat.dev/en-CA/docs/2019/flash-player-can-no-longer-always-be-activated/](https://www.fxsitecompat.dev/en-CA/docs/2019/flash-player-can-no-longer-always-be-activated/)

---

### Post by cruzer001 on 2019-08-12
> **walts48 said:**
> Something to be aware of for the next version of Firefox.[/url]
I'm not surprise with flash reaching EOL next year.  I do manage to stay away from changes by running[ FF ESR.   ]("https://www.mozilla.org/en-US/firefox/organizations/")

---

