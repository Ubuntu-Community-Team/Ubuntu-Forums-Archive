---
title: "How is virtualbox and virtualbox-ose different?"
date: 2012-12-24
forum: Virtualisation
---

### Post by Holmes.Sherlock on 2012-12-24
After installing virtualbox package, I found there is one more package called virtualbox-ose which installed some additional 22.2KBs of download. How are these packages different? I am running Ubuntu 12.04.

---

### Post by haqking on 2012-12-24
> **Holmes.Sherlock said:**
> After installing virtualbox package, I found there is one more package called virtualbox-ose which installed some additional 22.2KBs of download. How are these packages different? I am running Ubuntu 12.04.

ose = open source addition (includes source code)

best to download from [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

make sure you get the Extensions pack also

---

### Post by Holmes.Sherlock on 2012-12-24
> **haqking said:**
> ose = open source addition (includes source code)

best to download from [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

make sure you get the Extensions pack also
I am confused. Why are there so many sources to install the same package? Then what does the package in the repository contain?  BTW, it is already up and running.

---

### Post by haqking on 2012-12-24
> **Holmes.Sherlock said:**
> I am confused. Why are there so many sources to install the same package? Then what does the package in the repository contain?  BTW, it is already up and running.

The one in the repos is old i expect, i dont use Ubuntu so dont know, you can add an upto date repo from [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

So many sources ? There is Virtualbox.org and now Oracle (as Oracle own it now) that is it as far as official sources go.

But if its up and running , if its not broke then dont fix it ;-)

---

### Post by Holmes.Sherlock on 2012-12-24
> **haqking said:**
> The one in the repos is old i expect...
Help-->About shows "VirtualBox Graphical Interface Version 4.1.12_Ubuntu r77245".

---

### Post by haqking on 2012-12-24
> **Holmes.Sherlock said:**
> Help-->About shows "VirtualBox Graphical Interface Version 4.1.12_Ubuntu r77245".

as i said it is old, it is 4.2.6 now

The repo for upto date versions is on the link i posted above.

your Sherlock Holmes Skills need updating too ;-)

Peace

---

### Post by Holmes.Sherlock on 2012-12-24
> **haqking said:**
> as i said it is old, it is 4.2.6 now
The repo for upto date versions is on the link i posted above.

Will give it a try.

> 
...your Sherlock Holmes Skills need updating too :wink:

Ahh! This Sherlock is new to Ubuntu. :P

---

### Post by Holmes.Sherlock on 2012-12-24
BTW, should I download the .DEB package directly or add a repository like "
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) precise contrib" and then fetch from it?

---

### Post by haqking on 2012-12-24
> **Holmes.Sherlock said:**
> BTW, should I download the .DEB package directly or add a repository like "
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) precise contrib" and then fetch from it?

whatever you prefer.

If you download a .deb it will stay at that version, if you add a repo and apt-get update using that repo it will stay upto date

So if you are running Ubuntu 12.04 then add the

```
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) precise contrib
```to your sources

---

### Post by haqking on 2012-12-24
> **Holmes.Sherlock said:**
> BTW, should I download the .DEB package directly or add a repository like "
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) precise contrib" and then fetch from it?

yes add the repo if you want it to stay upto date

---

### Post by Holmes.Sherlock on 2012-12-24
> **haqking said:**
> yes add the repo if you want it to stay upto date
Why is it showing the lines in [COLOR=Red]RED[/COLOR]?
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libwvstreams4.6-base libgsoap1 libuniconf4.6 libwvstreams4.6-extras
Use 'apt-get autoremove' to remove them.
[COLOR=Red][B]The following packages will be REMOVED:
  virtualbox virtualbox-dkms virtualbox-ose virtualbox-qt[/B][/COLOR]
The following NEW packages will be installed:
  virtualbox-4.2
0 upgraded, 1 newly installed, 4 to remove and 242 not upgraded.
Need to get 62.9 MB of archives.
After this operation, 67.8 MB of additional disk space will be used.
Do you want to continue [Y/n]? 

```

---

### Post by haqking on 2012-12-24
> **Holmes.Sherlock said:**
> Why is it showing the lines in [COLOR=Red]RED[/COLOR]?
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libwvstreams4.6-base libgsoap1 libuniconf4.6 libwvstreams4.6-extras
Use 'apt-get autoremove' to remove them.
[COLOR=Red][B]The following packages will be REMOVED:
  virtualbox virtualbox-dkms virtualbox-ose virtualbox-qt[/B][/COLOR]
The following NEW packages will be installed:
  virtualbox-4.2
0 upgraded, 1 newly installed, 4 to remove and 242 not upgraded.
Need to get 62.9 MB of archives.
After this operation, 67.8 MB of additional disk space will be used.
Do you want to continue [Y/n]? 

```

Because those packages will be removed funnily enough ;-)

You said you already have it installed, and you are now installing an upto date version

---

### Post by MoebusNet on 2012-12-24
> **Holmes.Sherlock said:**
> After installing virtualbox package, I found there is one more package called virtualbox-ose which installed some additional 22.2KBs of download. How are these packages different? I am running Ubuntu 12.04.

To directly answer your question:

> Before version 4.0, there were two editions of VirtualBox: a full binary containing all features and an "Open Source Edition" (OSE) with source code. With version 4.0, there is only one version any more, which is open source, and the closed-source components have been moved to a separate extension pack.

[https://www.virtualbox.org/wiki/Editions](https://www.virtualbox.org/wiki/Editions)

The extension pack mentioned provides shared host <> guest cut/paste capability and I believe USB funtionality in the Guest machine.

---

### Post by Holmes.Sherlock on 2012-12-24
> **haqking said:**
> Because those packages will be removed funnily enough ;-)

Ahaha...I can read English. :P
But what I am asking is

[LIST=1]
[*]Why four components will be replaced by one?
[*]How is this package conflict resolved? Means how apt knows that the following have to be removed though the package names being different?
[*]How this "repository" things work? Aren't they always in sync with the official software vendor's repository?
[/LIST]

---

### Post by haqking on 2012-12-24
> **Holmes.Sherlock said:**
> Ahaha...I can read English. :P
But what I am asking is

[LIST=1]
[*]Why four components will be replaced by one?
[*]How is this package conflict resolved? Means how apt knows that the following have to be removed though the package names being different?
[*]How this "repository" things work? Aren't they always in sync with the official software vendor's repository?
[/LIST]


1. cos its an upto date all in one version
2. they have to be removed cause they are old versions and you are installing a new version
3. no they arent in sync, they have nothing to do with Ubuntu or Canonical, if you want the old out of date version then use then one from from Official repos provided by canonical/ubuntu, if you want the latest then get it from the official source virtualbox/oracle

---

### Post by Holmes.Sherlock on 2012-12-24
> **haqking said:**
> 
2. they have to be removed cause they are old versions and you are installing a new version

The other two replies are OK. But for #2, I am asking that, "In spite of the package names being different, how does apt know that the version I am installing is an updated version of these four older packages?"

---

### Post by haqking on 2012-12-24
> **Holmes.Sherlock said:**
> The other two replies are OK. But for #2, I am asking that, "In spite of the package names being different, how does apt know that the version I am installing is an updated version of these four older packages?"

because it checks to see what you have installed by version and checks to see if there is an upto date version with what you are trying to install.

Each file in the package will be different to ones installed.

otherwise apt-get update would never work would it

read about apt

---

### Post by Holmes.Sherlock on 2012-12-24
[LEFT]I installed virtualbox
```

sudo apt-get install virtualbox

```followed by virtualbox-ose
```

sudo apt-get install virtualbox-ose

```and then from official Oracle repository

At the third step, I get the following message
```

Reading package lists... 
Done Building dependency tree        
Reading state information... 
Done The following packages were automatically installed and are no longer required:   
libwvstreams4.6-base libgsoap1 libuniconf4.6 libwvstreams4.6-extras 
Use 'apt-get autoremove' to remove them. [COLOR=Red][B]
The following packages will be REMOVED:   
virtualbox virtualbox-dkms virtualbox-ose virtualbox-qt[/B][/COLOR] 
The following NEW packages will be installed:  
 virtualbox-4.2 
0 upgraded, 1 newly installed, 4 to remove and 242 not upgraded. 
Need to get 62.9 MB of archives. A
After this operation, 67.8 MB of additional disk space will be used.
Do you want to continue [Y/n]?

```Why does apt-get try to remove packages?

[/LEFT]

---

### Post by ibjsb4 on 2012-12-24
I do not run the ose, but my guess is the open source edition simply will not use those packages.

Do you really want ose?

Here's the scoop  :)

[https://www.virtualbox.org/manual/ch01.html#intro-installing](https://www.virtualbox.org/manual/ch01.html#intro-installing)

---

### Post by snowpine on 2012-12-24
It's one or the other.

---

### Post by SeanBlader on 2012-12-24
Probably because those old virtualbox packages will cause the new virtualbox packages to fail. So if you want one of them to work it gives you a choice to install the new ones or skip the install entirely.

---

### Post by Holmes.Sherlock on 2012-12-24
Please let me be clearer in framing the question. My question is more related to apt than VirtualBox. It seems the newest version (4.2.6) which I installed from Oracle Repository has replaced those four components in RED because they belonged to older versions (4.1.23). But how does apt as a package manager know that those were bits and pieces of older version of the "same" package while the names being entirely different? In other words, what is that common parameter which helps apt to recognize packges of different versions the same software?

---

### Post by howefield on 2012-12-24
Threads merged.

---

### Post by CharlesA on 2012-12-24
> **Holmes.Sherlock said:**
> Why is it showing the lines in [COLOR=Red]RED[/COLOR]?
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libwvstreams4.6-base libgsoap1 libuniconf4.6 libwvstreams4.6-extras
Use 'apt-get autoremove' to remove them.
[COLOR=Red][B]The following packages will be REMOVED:
  virtualbox virtualbox-dkms virtualbox-ose virtualbox-qt[/B][/COLOR]
The following NEW packages will be installed:
  virtualbox-4.2
0 upgraded, 1 newly installed, 4 to remove and 242 not upgraded.
Need to get 62.9 MB of archives.
After this operation, 67.8 MB of additional disk space will be used.
Do you want to continue [Y/n]? 

```

The OSE version and the one from the VirtualBox site have different dependencies. I have seen more breakage with the OSE and conflicting dependencies than I have with the one from their site.

> **Holmes.Sherlock said:**
> Please let me be clearer in framing the question. My question is more related to apt than VirtualBox. It seems the newest version (4.2.6) which I installed from Oracle Repository has replaced those four components in RED because they belonged to older versions (4.1.23). But how does apt as a package manager know that those were bits and pieces of older version of the "same" package while the names being entirely different? In other words, what is that common parameter which helps apt to recognize packges of different versions the same software?

Check apt-rdepends if you want to see what dependencies a certain package has.
[http://www.ubuntugeek.com/how-to-check-package-dependencies-with-apt-rdepends-on-ubuntu.html](http://www.ubuntugeek.com/how-to-check-package-dependencies-with-apt-rdepends-on-ubuntu.html)

The reason for the removal is above.

---

### Post by Holmes.Sherlock on 2012-12-24
> **CharlesA said:**
> The OSE version and the one from the VirtualBox site have different dependencies. I have seen more breakage with the OSE and conflicting dependencies than I have with the one from their site.



Check apt-rdepends if you want to see what dependencies a certain package has.
[http://www.ubuntugeek.com/how-to-check-package-dependencies-with-apt-rdepends-on-ubuntu.html](http://www.ubuntugeek.com/how-to-check-package-dependencies-with-apt-rdepends-on-ubuntu.html)

The reason for the removal is above.

How does apt know that virtualbox (basically this is vbox 4.1) and Virtualbox-4.2 (v4.2) are different version of the same package.

---

### Post by CharlesA on 2012-12-24
> **Holmes.Sherlock said:**
> How does apt know that virtualbox (basically this is vbox 4.1) and Virtualbox-4.2 (v4.2) are different version of the same package.

They aren't the same package - one is the OSE (included in the Ubuntu repos) and the other is the one from the VirtualBox site.

Different versions with different dependencies.

---

### Post by snowpine on 2012-12-24
Unpack the .deb using your favorite archive manager and read the /DEBIAN/control file. Not to sound like a know-it-all but this is basic "how to make a .deb 101" stuff. :)

```
Package: virtualbox-4.2
Version: 4.2.6-82870~Ubuntu~quantal
Architecture: i386
Maintainer: Oracle Corporation <info@virtualbox.org>
Installed-Size: 134192
Pre-Depends: debconf (>= 1.1) | debconf-2.0
Depends: libc6 (>= 2.15), libcurl3 (>= 7.16.2), libdevmapper1.02.1 (>= 2:1.02.20), libgcc1 (>= 1:4.1.1), libgl1-mesa-glx | libgl1, libpng12-0 (>= 1.2.13-4), libpython2.7 (>= 2.7), libqt4-network (>= 4:4.5.3), libqt4-opengl (>= 4:4.7.2), libqtcore4 (>= 4:4.8.0), libqtgui4 (>= 4:4.8.0), libsdl1.2debian (>= 1.2.11), libssl1.0.0 (>= 1.0.0), libstdc++6 (>= 4.6), libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxinerama1, libxml2 (>= 2.7.4), libxmu6, libxt6, zlib1g (>= 1:1.1.4), psmisc, adduser
Recommends: libasound2, libpulse0, libsdl-ttf2.0-0, dkms, linux-headers, gcc, make, binutils, pdf-viewer, libgl1, python-central
Conflicts: virtualbox, virtualbox-guest-additions-iso, virtualbox-ose
Replaces: virtualbox
Provides: virtualbox
Section: contrib/misc
Priority: optional
Description: Oracle VM VirtualBox
 VirtualBox is a powerful PC virtualization solution allowing you to run a
 wide range of PC operating systems on your Linux system. This includes
 Windows, Linux, FreeBSD, DOS, OpenBSD and others. VirtualBox comes with a broad
 feature set and excellent performance, making it the premier virtualization
 software solution on the market.
Python-Version: >= 2.4
```

(note the "Conflicts" and "Replaces" lines)

---

### Post by Holmes.Sherlock on 2012-12-24
> **snowpine said:**
> Unpack the .deb using your favorite archive manager and read the /DEBIAN/control file. Not to sound like a know-it-all but this is basic "how to make a .deb 101" stuff. :)

You are the man!!! This is the line I was hunting for since last evening. Marked thread as solved. Thanks a lot. Probably I was not enough clear in framing my question.

---

