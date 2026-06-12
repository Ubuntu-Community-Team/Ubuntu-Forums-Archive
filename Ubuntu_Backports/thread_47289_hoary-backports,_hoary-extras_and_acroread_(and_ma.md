---
title: "hoary-backports, hoary-extras and acroread (and maybe others)"
date: 2005-07-08
forum: Ubuntu Backports
---

### Post by magoo on 2005-07-08
Hello,

I just discovered the hoary-extras project and I think it is great. I came across it when trying to correct the issues I had with the marillat repository :-).

I understand the idea behind but something is still unclear to me:
the relationship between the backports and the extras repository.

I do not wish to upgrade every package available on the backports repository if it is not needed. I need the mplayer,dvd,encoding stuff, java, realplayer...

Here is an example (I only have hoary-extras in my sources.list):

```
magnus@themachine:~$ sudo apt-get install acroread
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  acroread: Depends: libgcc1 (>= 1:4.0.0-7) but 1:4.0-0pre6ubuntu7 is to be installed
E: Broken packages
magnus@themachine:~$
```


We see that acroread has as dependency libgcc1 in a version not available for "classic" ubuntu users.

I am afraid that adding the backports repository will solve my problem but upgrade a bunch of stuff I do not need nor want to be upgraded.

Should hoary-extras only be based on standard ubuntu libraries?

thanks in advance for your answers.

Magoo

---

### Post by Mez on 2005-07-08
ah, obviously my version of acroread wasn't used.

I'll fix that and upload in a mo

---

### Post by magoo on 2005-07-08
It is version 7.0-0.9~5.04ubp1 of acroread I am trying to install. AFAIK it is the version from hoary-extras. Ubuntu's got version 5 which is completely buggy and does not work.

```

magnus@machine:~$ apt-cache show acroread
Package: acroread
Version: 7.0-0.9~5.04ubp1
Priority: optional
Section: text
Maintainer: Christian Marillat <marillat@debian.org>
Depends: libatk1.0-0 (>= 1.9.0), libc6 (>= 2.3.2.ds1-4), libgcc1 (>= 1:4.0.0-7), libglib2.0-0 (>= 2.6.0), libgtk2.0-0 (>= 2.6.0), libpango1.0-0 (>= 1.8.1), libstdc++5 (>= 1:3.3.4-1), libx11-6 | xlibs (>> 4.1.0), libxext6 | xlibs (>> 4.1.0), zlib1g (>= 1:1.2.1), libldap2
Recommends: acroread-plugins
Suggests: mozilla-acroread
Conflicts: acroread-debian-files (<= 0.0.8), acroread-plugins (<= 7.0-0sarge0.3)
Provides: pdf-viewer, postscript-preview
Replaces: acroread-debian-files (<= 0.0.8), acroread-plugins (<= 7.0-0sarge0.3)
Architecture: i386
Filename: dists/hoary-extras/restricted/binary-i386/acroread_7.0-0.9~5.04ubp1_i386.deb
Size: 23434996
MD5sum: d564d2fa25a4a9e04b2563a8ba5f89ff
Description: Adobe Acrobat Reader: Portable Document Format file viewer
 Adobe Acrobat Reader for viewing and printing Adobe Portable Document
 Format (PDF) files.
 .
 Home Page: http://www.adobe.com/products/acrobat/readermain.html
installed-size: 53838

Package: acroread
Priority: optional
Section: multiverse/text
Installed-Size: 25228
Maintainer: Christian Marillat <marillat@debian.org>
Architecture: i386
Version: 5.10-0.2
Provides: pdf-viewer, postscript-preview
Depends: libc6 (>= 2.2.4-4), libx11-6 | xlibs (>> 4.1.0), libxext6 | xlibs (>> 4.1.0), libxp6 | xlibs (>> 4.1.0), libxt6 | xlibs (>> 4.1.0), acroread-debian-files (>= 0.0.4)Filename: pool/multiverse/a/acroread/acroread_5.10-0.2_i386.deb
Size: 9171168
MD5sum: 1d8b5f47e5c997272987fd7159117fd3
Description: Adobe Acrobat Reader: Portable Document Format file viewer
 Adobe Acrobat Reader for viewing and printing Adobe Portable Document
 Format (PDF) files.
 .
 Home Page: http://www.adobe.com/products/acrobat/readermain.html
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

magnus@machine:~$

```

---

### Post by Mez on 2005-07-08
I pushed out acroread7.0-0.9~5.04ubp2 This morning.

> mez@apathy:~$ apt-cache show acroread
Package: acroread
**Version: 7.0-0.9~5.04ubp2**
Priority: optional
Section: text
Maintainer: Christian Marillat <marillat@debian.org>
Depends: libatk1.0-0 (>= 1.9.0), libc6 (>= 2.3.2.ds1-4), libgcc1 (>= 1:4.0-0pre6
ubuntu4), libglib2.0-0 (>= 2.6.0), libgtk2.0-0 (>= 2.6.0), libpango1.0-0 (>= 1.8
.1), libstdc++5 (>= 1:3.3.4-1), libx11-6 | xlibs (>> 4.1.0), libxext6 | xlibs (>
> 4.1.0), zlib1g (>= 1:1.2.1), libldap2
Recommends: acroread-plugins
Suggests: mozilla-acroread
Conflicts: acroread-debian-files (<= 0.0.8), acroread-plugins (<= 7.0-0sarge0.3)
Provides: pdf-viewer, postscript-preview
Replaces: acroread-debian-files (<= 0.0.8), acroread-plugins (<= 7.0-0sarge0.3)
Architecture: i386
Filename: dists/hoary-extras/restricted/binary-i386/acroread_7.0-0.9~5.04ubp2_i3
86.deb
Size: 23429428
MD5sum: 362062fcdedced1922400f20a2c85739
Description: Adobe Acrobat Reader: Portable Document Format file viewer
 Adobe Acrobat Reader for viewing and printing Adobe Portable Document
 Format (PDF) files.
 .
 Home Page: [http://www.adobe.com/products/acrobat/readermain.html](http://www.adobe.com/products/acrobat/readermain.html)
installed-size: 54476

This fixes your problem (I complained about this before I became a dev, I thought It had been fixed

---

### Post by jcohen on 2005-07-08
This also affects many other backport packages. I tried forcing the hoary version of libgcc1 and this is what I saw:

root@jasonslaptop:~# apt-get install  libgcc1=1:4.0-0pre6ubuntu7
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  abiword-common abiword-gnome abiword-help beagle dvdrip firefox
  firefox-gnome-support foomatic-db-hpijs g++-3.4 gnome gnome-core
  gnome-desktop-environment gnome-office hpijs kubuntu-desktop libgecko-cil
  libstdc++6 libstdc++6-dev mozilla mozilla-browser mozilla-dev
  mozilla-firefox mozilla-firefox-gnome-support mozilla-mailnews mozilla-psm
  openoffice.org2 openoffice.org2-calc openoffice.org2-common
  openoffice.org2-core openoffice.org2-debian-files openoffice.org2-draw
  openoffice.org2-evolution openoffice.org2-gnome openoffice.org2-impress
  openoffice.org2-l10n-en-us openoffice.org2-math openoffice.org2-writer
  transcode ubuntu-desktop yelp
The following packages will be DOWNGRADED:
  libgcc1
0 upgraded, 0 newly installed, 1 downgraded, 40 to remove and 0 not upgraded.
Need to get 81.7kB of archives.
After unpacking 379MB disk space will be freed.
Do you want to continue [Y/n]?

I checked the dependencies on Firefox and Mozilla from backports and they also requires libgcc1 4.0.0-7. This creates a sort of tital wave affect. mozilla-firefox includes many reverse  depends such as yelp. gnome-utils, gnome-panel, gnome-core and ubuntu-desktop . Of course, by downgrading libgcc1 to the hoary version, i would have to remove the other libraries dependant on libgcc1 such as libstdc++6. Once that package is removed, openoffice.org2 must also be uninstalled. In all,  most of gnome, mozilla, firefox, openoffice.org2, abiword and several other packages must be uninstalled simply to get back one hoary library. This is precisely why only applications should be backported and not libraries- espeically important libraries. 

jason@jasonslaptop:~$ apt-cache show firefox
Package: firefox
Version: 1.0.4-1ubuntu3~5.04ubp5
Priority: optional
Section: web
Maintainer: Eric Dorland <eric@debian.org>
Depends: fontconfig, psmisc, debianutils (>= 1.16), libart-2.0-2 (>= 2.3.16), libatk1.0-0 (>= 1.9.0), libbonobo2-0 (>= 2.8.0), libbonoboui2-0 (>= 2.5.4), libc6 (>= 2.3.2.ds1-4), libcairo1 (>= 0.3.0), libfontconfig1 (>= 2.2.1), libfreetype6 (>= 2.1.5-1), **libgcc1 (>= 1:4.0.0-7)**, libgconf2-4 (>= 2.9), libglib2.0-0 (>= 2.6.0), libgnome2-0 (>= 2.8.0), libgnomecanvas2-0 (>= 2.6.0), libgnomeui-0 (>= 2.8.0), libgnomevfs2-0 (>= 2.9.90), libgtk2.0-0 (>= 2.6.0), libice6 | xlibs (>> 4.1.0), libidl0, libjpeg62, libkrb53 (>= 1.3.2), liborbit2 (>= 1:2.12.0), libpango1.0-0 (>= 1.8.1), libpixman1 (>= 0.1.3), libpng12-0 (>= 1.2.8rel), libpopt0 (>= 1.7), libsm6 | xlibs (>> 4.1.0), libstdc++6 (>= 4.0.0-7), libx11-6 | xlibs (>> 4.1.0), libxft2 (>> 2.1.1), libxinerama1, libxml2 (>= 2.6.17), libxrender1, libxt6 | xlibs (>> 4.1.0), zlib1g (>= 1:1.2.1), mozilla-firefox

jason@jasonslaptop:~$ apt-cache show mozilla-browser
Package: mozilla-browser
Version: 2:1.7.8-1ubuntu2~5.04ubp2
Priority: optional
Section: web
Maintainer: Takuo KITAME <kitame@debian.org>
Depends: libatk1.0-0 (>= 1.9.0), libc6 (>= 2.3.2.ds1-4), libfontconfig1 (>= 2.2.1), libfreetype6 (>= 2.1.5-1),** libgcc1 (>= 1:4.0.0-7)**, libglib2.0-0 (>= 2.6.0), libgtk2.0-0 (>= 2.6.0), libpango1.0-0 (>= 1.8.1), libstdc++5 (>= 1:3.3.4-1), libx11-6 | xlibs (>> 4.1.0), libxext6 | xlibs (>> 4.1.0), libxft2 (>> 2.1.1), libxp6 | xlibs (>> 4.1.0), libxrender1, libxt6 | xlibs (>> 4.1.0), zlib1g (>= 1:1.2.1), libnspr4 (= 2:1.7.8-1ubuntu2~5.04ubp2), debconf (>= 1), psmisc

---

### Post by ewerx on 2005-07-09
I am also having this libgcc1 dependency problem when I try to install firefox 1.0.4 from backports on my Kubuntu Hoary 5.04.

```
$ apt-cache show firefox
Package: firefox
Version: 1.0.4-1ubuntu3~5.04ubp5
Priority: optional
Section: web
Maintainer: Eric Dorland <eric@debian.org>
Depends: fontconfig, psmisc, debianutils (>= 1.16), libart-2.0-2 (>= 2.3.16), libatk1.0-0 (>= 1.9.0), libbonobo2-0 (>= 2.8.0), libbonoboui2-0 (>= 2.5.4), libc6 (>= 2.3.2.ds1-4), libcairo1 (>= 0.3.0), libfontconfig1 (>= 2.2.1), libfreetype6 (>= 2.1.5-1), libgcc1 (>= 1:4.0.0-7), libgconf2-4 (>= 2.9), libglib2.0-0 (>= 2.6.0), libgnome2-0 (>= 2.8.0), libgnomecanvas2-0 (>= 2.6.0), libgnomeui-0 (>= 2.8.0), libgnomevfs2-0 (>= 2.9.90), libgtk2.0-0 (>= 2.6.0), libice6 | xlibs (>> 4.1.0), libidl0, libjpeg62, libkrb53 (>= 1.3.2), liborbit2 (>= 1:2.12.0), libpango1.0-0 (>= 1.8.1), libpixman1 (>= 0.1.3), libpng12-0 (>= 1.2.8rel), libpopt0 (>= 1.7), libsm6 | xlibs (>> 4.1.0), libstdc++6 (>= 4.0.0-7), libx11-6 | xlibs (>> 4.1.0), libxft2 (>> 2.1.1), libxinerama1, libxml2 (>= 2.6.17), libxrender1, libxt6 | xlibs (>> 4.1.0), zlib1g (>= 1:1.2.1), mozilla-firefox
Suggests: firefox-gnome-support (= 1.0.4-1ubuntu3~5.04ubp5), latex-xft-fonts, xprint
Provides: www-browser
Architecture: i386
Filename: dists/hoary-backports/main/binary-i386/firefox_1.0.4-1ubuntu3~5.04ubp5_i386.deb
Size: 8579308
MD5sum: 3590eaefa7add567518b395378481d6e
Description: lightweight web browser based on Mozilla
 Firefox is a redesign of the Mozilla browser component, similar to
 Galeon, K-Meleon and Camino, but written using the XUL user interface
 language and designed to be lightweight and cross-platform.
 .
 This browser was previously known as Firebird and Phoenix.
installed-size: 24312

```

When I try to install:

```
$ sudo apt-get install firefox
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  firefox: Depends: libgcc1 (>= 1:4.0.0-7) but 1:4.0-0pre6ubuntu7 is to be installed
           Depends: libstdc++6 (>= 4.0.0-7) but 4.0-0pre6ubuntu7 is to be installed
E: Broken packages

```

Is there a fix for this?

---

### Post by magoo on 2005-07-12
[QUOTE=Mez]I pushed out acroread7.0-0.9~5.04ubp2 This morning.
This fixes your problem (I complained about this before I became a dev, I thought It had been fixed[/QUOTE]

Yep it now works, thanks a lot!

transcode has the same problem, can you fix it too?

---

### Post by ironphil on 2005-07-21
Acroread (version 7) is currently not installable. It does not even show up if I do a search. I get the acroread-plugins and mozilla-acroread for version 7 but no acroread. Should I just wait? Here is what I get if I try to install mozilla-acroread:
> mozilla-acroread:
 Depends: acroread but it is not going to be installed 

I have of course enable the backports and extra repositories.

---

### Post by kb00heda on 2005-07-22
This happened to me as well: when I tried to install acroread earlier today, I was promted with the old version (i.e., 5 instead of 7). Just like you I had updated my sources, which do include the necessary backport repositories. 

However, I gave up trying to install via aptitude, and simply downloaded the two packages (acroread and acroread-plugins) manually (from my selected backport mirror), to have them successfully installed using "dpkg -i".

Hopefully I did not wreck anything --- at least it appears to work nicely.

---

### Post by ironphil on 2005-07-22
It seems to be back now. Just did a "Reload" and it is showing up. Thanks to those who fixed that, Ubuntu rocks!

---

### Post by magoo on 2005-07-26
Hello,

transcode is still uninstallable without the hoary-backports repository.
It is the same issue again:
```

The following packages have unmet dependencies:
  transcode: Depends: libgcc1 (>= 1:4.0.0-7) but 1:4.0-0pre6ubuntu7 is to be installed
E: Broken packages

```

Can you please fix it too?

Thanks in advance,

---

### Post by jdong on 2005-07-26
firefox **MUST** be compiled with GCC 4.0, or otherwise it segfaults like no other on some non-386 kernels.

As far as acroread and others, those can probably be repackaged.

---

### Post by magoo on 2005-07-28
Hello,

Is it possible to know when this could be done?

And also check the rest of the packages available on extras for the same issue.

Thanks in advance

---

### Post by magoo on 2005-08-10
Anyone?

---

### Post by Youdaman on 2005-09-02
Questions about hoary-backports and hoary-extras...

Why is there a package called firefox in addition to (and which relies on) mozilla-firefox in hoary-backports?

Why is there a package called firefox-gnome-support AND another called mozilla-firefox-gnome-support also in hoary-backports?

Why is it that after installing the acroread plug-in (mozilla acroread) from hoary-extras or hoary-backports that Firefox still prompts me to save or load a pdf in an external viewer?

Why does deleting my ~/.mozilla directory fix the above?

Why does making any changes to Firefox's settings (which I have to do after having deleted them!) then put me back in the situation where Firefox prompts me to save or load a pdf in an external viewer?! Another fix for this, apart from deleting my ~/.mozilla directory, is to load up the Firefox's plugins page (about:plugins -- that's about[colon]plugins ignore the smiley) page in the browser, and then re-try the pdf which then loads in the plug-in as it should (however next time the browser is started, the prompt returns).

My suspicion is the fact there's "firefox" and "mozilla-firefox" versions of both the browser and the gnome support files packages, and the fact there's inter/circular-dependencies between them, and they have common files that one or the other over-writes, thus creating the above problem! Another problem is that Gaim's mail notification doesn't launch a browser window once the packages from backports/extras are installed. Again, probably a result of the inter/circular-dependencies of these packages and the common files...

Solutions? I recall having everything working a little while back before these conflicting/redundant packages were created...

---

### Post by Youdaman on 2005-09-02
SOLUTION (maybe): go into Firefox's settings, Downloads, and click on the Plug-Ins button, then hit OK... after this, Firefox seems to load pdfs with the plug-in without prompting... fingers-crossed it keeps working! :D

However, Gaim still won't open Firefox with its mail notification. :(

---

### Post by Youdaman on 2005-09-03
Ok, after a fresh install of Ubuntu Hoary, I've added both hoary-extras and hoary-backports to my /etc/apt/sources.list, I've chosen not to upgrade/fix mozilla-firefox ormozilla-firefox-gnome-support.

Ubuntu Update Manager gave me this message:
> It is not possible to upgrade all packages.

This means that besides the actual upgrade of the packages some further action (such as installing or removing packages) is required. Please use Synaptic "Smart Upgrade" or "apt-get dist-upgrade" to fix the situation.

The following packages could not be upgraded:
mozilla-firefox
mozilla-firefox-gnome-support
 


Would it also be an idea to set up Synaptic to prefer a "safer" version? e.g.

Settings -> Preferences -> Distribution -> Prefer versions from: hoary-security

instead of "Always prefer the highest version" so I don't get prompted to install them? I suppose it wouldn't matter if I did that in Synaptic as the Ubuntu Update Manager is an altogether different animal.

My solution for now is to just leave things as they are, i.e. DO NOT  uninstall my current mozilla-firefox and mozilla-firefox-gnome-support which are both from hoary-security and install the latest ones from hoary-backports, but instead just leave the ones from hoary-security there... yeah, that'll do... I hope :) Everything now seems to work ("everything" being the acroread plugin and gaim's email notification) so I'm happy :)

---

### Post by Youdaman on 2005-09-03
Well my happiness was short-lived.

It turns out that whenever I restart Firefox I'm back to the problem of it prompting me to save or open a pdf in an external viewer.

The problem is only temporarily solved by bringing up the about : plugins (no spaces) page. Again, the pdf plugin is not listed in the Downloads/Plug-Ins pop-up window until that page is viewed, and nor will the pdfs load with the plugin until that page is viewed.

Weird. And annoying.

---

### Post by Youdaman on 2005-09-03
A dodgy solution is to make your homepage ```
about:plugins
``` so that you can load pdfs after you've started Firefox. However this doesn't solve the problem of starting Firefox with "firefox whatever.pdf" or via a pdf file icon in nautilus, both of which would still prompt you.

---

### Post by Youdaman on 2005-09-03
Eureka! :D

I've done it! I've worked it out!

* mozilla-acroread plugin doesn't work if you disable Java in Firefox's preferences *

* SOLUTION: leave Java enabled *

I'm guessing it's cos the start-up scripts for Firefox check to see if Java's enabled or something like that, and because it's not Firefox forgets to enable other plugins such as mozilla-acroread... anyway, I don't really care what the reason is because it now works! :D

---

### Post by grendelkhan on 2005-09-04
Am I the only person getting this message with acroread??

---

### Post by Youdaman on 2005-09-05
I've read elsewhere about acroread thinking it's expired... have you googled it?

How about uninstalling/reinstalling mozilla-acroread?

Or maybe deleting the ~/.adobe directory?

---

### Post by grendelkhan on 2005-09-05
Done both, same result.

I don't mind grabbing adobe's installer and putting it in that way. but I'd rather be using deb for all my installations.

---

