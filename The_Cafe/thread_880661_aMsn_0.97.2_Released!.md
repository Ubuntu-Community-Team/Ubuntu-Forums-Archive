---
title: "aMsn 0.97.2 Released!"
date: 2008-08-05
forum: The Cafe
---

### Post by Kosimo on 2008-08-05
Hello guys, aMSN folks has just released the second Bugfix release for 0.97.x branch witch solves several bugs.

Good amesening!  


Downlowd it from here

[http://www.amsn-project.net/](http://www.amsn-project.net/)

---

### Post by claw123 on 2008-08-05
Anyone seen deb packages for this version?

I haven't been able to log in through amsn for the last 2 days.  I believe M$ changed the protocol and am of the understanding that this release should address the change.

I've been hunting around in packages.ubuntu and packages.debian for and up-to-date deb, but they and the sources are out of date (0.97 rc1, etc).

And no, installing an "autopackge" is not an option.  That stuff will rot your brain ... or at the very least corrupt a stable machine. :lolflag:

---

### Post by Kosimo on 2008-08-05
There has been some issues to log in using 0.97 version, At the moment I don´t see any .deb for 0.97.2, but during that time you can give it a try with the 0.97.1 witch solves this problem, letting you log in ´till (probably getdeb) release an easy .deb for the latest version.

Get aMSN 0.97.1 from here: [http://www.getdeb.net/release.php?id=2875](http://www.getdeb.net/release.php?id=2875)

> **claw123 said:**
> Anyone seen deb packages for this version?

I haven't been able to log in through amsn for the last 2 days.  I believe M$ changed the protocol and am of the understanding that this release should address the change.

I've been hunting around in packages.ubuntu and packages.debian for and up-to-date deb, but they and the sources are out of date (0.97 rc1, etc).

And no, installing an "autopackge" is not an option.  That stuff will rot your brain ... or at the very least corrupt a stable machine. :lolflag:

---

### Post by nakki on 2008-08-05
Hi guys,
i have compiled the sources of the new amsn'release and maked a deb for i386.
I've installed it and it works!

just execute /usr/bin/amsn


If you to try it at your own risk, you can [download it here]("http://www.megaupload.com/?d=L1PN35B8")

	
I hope will become useful and sorry for my english...

---

### Post by claw123 on 2008-08-06
Just a follow up ...

I tried amsn from getdeb (version 0.97.1) which resolved my immediate problem of logging into MSN.  However, retrieving offline messages stopped working for me.  YMMV when using 0.97.1.

I checked packages.ubuntu.com this morning and saw a branding spanking new 0.97.2.  Yah!  Here are my notes on how to get it working on Hardy:

Ok, so you will need to download the following from packages.ubuntu.com, found in Intrepid distribution:
[LIST]
[*]amsn_0.97.2
[*]amsn-data_0.97.2
[*]tcl-tls_1.5.0
[/LIST]

De-install amsn (if it's already installed).

Make sure you have the following installed (if not just use apt-get or Synaptic to fetch and install - no need to download Intrepid's packages for these):
[LIST]
[*]tcl8.5
[*]tk8.5
[*]libsnack2
[/LIST]

Install with the following:
```
sudo dpkg -i tcl-tls_1.5.0.dfsg-9_i386.deb amsn-data_0.97.2~debian0ubuntu1_all.deb amsn_0.97.2~debian-0ubuntu1_i386.deb
```

A note about tcl-tls and tcltls packages.  tcl-tls is a new package designed to be used with tcl8.5.  The tcltls is heavily dependent on tcl8.4/tcl8.3.  On my setup, I de-installed all versions of tcl and tk currently installed (I had no other programs that used version 8.4 of tcl and tk).  I don't know whether tcl-tls and tcltls can co-exist on the same machine - I would presume so, but YMMV.

HTH,
claw

---

### Post by Kosimo on 2008-08-07
Guys...
The best thing you can do (if you don't like to compile)

Is going to getdeb: [http://www.getdeb.net/release/3001](http://www.getdeb.net/release/3001)

Finally 0.97.2 available!

---

### Post by Claus7 on 2008-08-07
Hello,

or install 0.98b and get over with it. And only via a script without having to download anything: 
[http://ubuntuforums.org/showpost.php?p=4851276&postcount=3](http://ubuntuforums.org/showpost.php?p=4851276&postcount=3)
The versions of amsn are becoming a lot!

Regards!

---

### Post by Belerophon on 2008-08-07
Backport team or something won't get a new version of amsn to hardy?? I mean, I just can't login, shouldn't there be an update to hardy?

If not, does anyone know how to add the the version of amsn found in intrepid's sources to the sources of hardy, so we can just install it through synaptic?
...I've done this for some program I can't recall a while ago, but I can't remember how to do it...


By the way, for the .deb package:
```
sudo dpkg -i *.deb
```

this is enough to install the thing?? Should I uninstall the previous version first??

Thanks!

---

### Post by deathrail on 2008-08-08
where i keep getting lost is everything everyones talking about is 32bit and im now 64, anyone have a direction to point me in?
thanks

---

### Post by JonaLinux on 2008-08-08
For a faster download of this patch amsn_0.97.2-1~getdeb1_i386.deb
you can go to my linux mirror at [www.linuxfreedom.com](www.linuxfreedom.com) and click on the red
link which will download the patch directly.

---

### Post by perce on 2008-08-09
a new amsn which solves the connecting bug is in Hardy's proposed upgrades.

---

### Post by growingneeds on 2008-08-13
Hey guys,

This process did it for me:
[LIST=1]
[*]Check **pre-released updates (hardy proposed repositories)** in **Synaptic Package Manager**;
[*]Reload repositories when prompted;
[*]Mark **aMSN** for installation. It should be version **0.97+final-0ubuntu5.1 (hardy-proposed)**;
[*]After installation, uncheck **hardy proposed repositories** in **Synaptic Package Manager**. Otherwise, all packages in the distribution will be updated to the latest version as provided by the **hardy proposed repositories**. This is because the option **Always prefer the highest version** is checked in **Package upgrade behaviour**. Reload repositories once more.
[/LIST]

Hope this helps.

---

