---
title: "Adept PM Ready For Testing (Hoary/Breezy)"
date: 2005-08-23
forum: The Cafe
---

### Post by drizek on 2005-08-23
First release of adept according to the devs blog

 [http://blog.mornfall.net/tech/ekhis/adept-hits-alpha.html](http://blog.mornfall.net/tech/ekhis/adept-hits-alpha.html)

If you didnt know, Adept is going to be replacing kynaptic in breezy for kubuntu(although im sure it works in gnome as well).

---

### Post by SGC on 2005-08-23
My problems with Adept:
- It want to remove synaptic in order to install.
- Need to download 22 MB and will uses 85 MB of disk space (To much for a package manager)

---

### Post by drizek on 2005-08-23
[QUOTE=SGC]My problems with Adept:
- It want to remove synaptic in order to install.
- Need to download 22 MB and will uses 85 MB of disk space (To much for a package manager)[/QUOTE]
 if you dont like it or if it doesnt work, you just have to do apt-get install synaptic and it will bring it back to the way it was.

---

### Post by amastronardi on 2005-08-23
Besides the 22mb needed, it looks really interesting  :-) 

It isn't an amd64 package yet and I don't want to do it myself... Will need to wait a bit to enjoy it :-k

Cheers, Adrian.

---

### Post by cowlip on 2005-08-23
[QUOTE=amastronardi]Besides the 22mb needed, it looks really interesting  :-) 

It isn't an amd64 package yet and I don't want to do it myself... Will need to wait a bit to enjoy it :-k

Cheers, Adrian.[/QUOTE]

Oh lord...I am really beginning to understand why people bash installing software on Linux..
> 
$ sudo apt-get install adept
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
  adept: Depends: debtags but it is not going to be installed
         Depends: libapt-pkg-libc6.3-5-3.10
E: Broken packages



---

### Post by amastronardi on 2005-08-23
```
sudo dpkg --install libapt-pkg-libc6.3-5-3.10.deb adept_xxx.deb debtags_xxx.deb
```

do the same if they have more dependencies.

Cheers, Adrian.

---

### Post by drizek on 2005-08-23
[QUOTE=cowlip]Oh lord...I am really beginning to understand why people bash installing software on Linux..[/QUOTE]
 i installed it just fine through synaptic in kubuntu. it is a little buggy and hte search interface doesnt work very well ATM. but overall, i like it. it seems to be a pretty prmising app, and is already much much better than kynaptic. it is also very stable, which is good considring it is still the first alpha release.

---

### Post by cowlip on 2005-08-23
[QUOTE=amastronardi]```
sudo dpkg --install libapt-pkg-libc6.3-5-3.10.deb adept_xxx.deb debtags_xxx.deb
```

do the same if they have more dependencies.

Cheers, Adrian.[/QUOTE]
 HI...where do I get those .deb files from? (other than the adept.deb)

---

### Post by amastronardi on 2005-08-24
[QUOTE=cowlip]HI...where do I get those .deb files from? (other than the adept.deb)[/QUOTE]

Here you have the ino: [http://blog.mornfall.net/tech/ekhis/adept-hits-alpha.html](http://blog.mornfall.net/tech/ekhis/adept-hits-alpha.html). You have (at least) two options:

Option 1.- include below repository in you /etc/apt/sources.list, include just one line depending on which ubuntu version you are running:
deb [http://pdx.freedesktop.org/~mornfall/adept/hoary/](http://pdx.freedesktop.org/~mornfall/adept/hoary/) ./
deb [http://pdx.freedesktop.org/~mornfall/adept/breezy/](http://pdx.freedesktop.org/~mornfall/adept/breezy/) ./

to modify the file do:

```

hit ALT+F2
kdesu kate /etc/apt/sources.list

```

Using this option, you should be able to use apt-get, synaptic, kpackage, etc.

Option 2.- go to the url and download files manually, later use dpkg. Again use the url that matches with you version.

[http://pdx.freedesktop.org/~mornfall/adept/hoary/](http://pdx.freedesktop.org/~mornfall/adept/hoary/)
[http://pdx.freedesktop.org/~mornfall/adept/breezy/](http://pdx.freedesktop.org/~mornfall/adept/breezy/)


Cheers, Adrian.

---

### Post by cowlip on 2005-08-25
Thank you for your detailed guide :) I wil ltry it

---

### Post by mornfall on 2005-09-02
[QUOTE=SGC]My problems with Adept:
- It want to remove synaptic in order to install.
- Need to download 22 MB and will uses 85 MB of disk space (To much for a package manager)[/QUOTE]
For the first, that is a problem with library dependencies -- adept needs a new apt to work and synaptic old apt. And you can't have them both (yet?). For the second, it is built with debugging symbols on. The final builds should be MUCH smaller (order of few megabytes disk space at most).

Anyway, i am working on getting beta out of the door, so :). More details on progress etc on [http://web.ekhis.org/adept.html](http://web.ekhis.org/adept.html)

Yours, Peter.

---

