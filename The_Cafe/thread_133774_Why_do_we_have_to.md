---
title: "Why do we have to?"
date: 2006-02-20
forum: The Cafe
---

### Post by Sirin on 2006-02-20
Why aren't we able to upgrade apps when it's released? I've wanted to upgrade to Firefox 1.5.0.1 for a long time. Then I found out that I have to upgrade to Dapper just to get it. Why do we have to keep upgrading to get updates of apps. I was using Hoary, and when I wanted to upgrade GIMP to a newer POINT RELEASE from 2.2.2 to 2.2.8, I found out that I had to upgrade to Breezy JUST TO GET A POINT RELEASE UPGRADE. Why is this? With Windows, I was able to upgrade Firefox from 1.0.7 to 1.5.0.1 with an easy installer. With Ubuntu, I have to wait three months to get the Dapper install CD and upgrade to the new version JUST to get a new point release. Why are we being pushed so hard to upgrade to the newest version of Ubuntu? Isn't this like Microsoft, where we HAVE to upgrade to get the newest versions of the apps? Is it because Linux is so manual that it is IMPOSSIBLE to get 1.5.0.1 on Breezy? I'm running 1.5.0.1 right now from my /home/firefox folder, but I'm looking for a system-wide version.

The Automatix release of Firefox 1.5 ruined my system, by the way, so that's out of the question. :cry:

---

### Post by Deaf_Head on 2006-02-20
[https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28firefox%29](https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28firefox%29)


no you don't, and the thing in the wiki about totem-mozilla not working is outdated. All this stuff is realy easy too, basically all your doing is downloading and unzipping into your /opt folder than setting everything up so ubuntu realized a new version of firefox is installed

---

### Post by Sirin on 2006-02-20
[QUOTE=Deaf_Head][https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28firefox%29](https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28firefox%29)


no you don't, and the thing in the wiki about totem-mozilla not working is outdated. All this stuff is realy easy too, basically all your doing is downloading and unzipping into your /opt folder than setting everything up so ubuntu realized a new version of firefox is installed[/QUOTE]

Yeah, but that is upgrading it manually, which I don't have that much problem with. I was wondering why the new version was not in the repos.

---

### Post by dickohead on 2006-02-20
Well... Due to the rapid change of so many different programs within any Linux distribution, certain libraries, for example: Glibc, will be updated, allowing programs to do more, faster and better than before, but sometimes the trade-off for this is that the old version is not backwards compatible, or certain features will not work. So you need to upgrade to Glibc version X.Y.Z before Firefox X.Y.Z will work, but gnome 2.0 doesn't like Glibc X.Y.Z so it needs to be upgraded to 2.X.Y, but that's not released for Breezy, so you need to go to Dapper...... Yes it's annoying, yes it's confusing and yes thiongs will get better.

Windows has complete control over their system libraries, so they only update them when needed, and they ensure that they are backwards compatible, or the old ones are still available, in some respects the microsoft way is better for users, less hastle to install new programs, because the new programs KNOW that you will have version X of program Y because windows makes sure of that.

But with a Linux system, so many different people have so many different projects all with different release dates and different dependencies, trust me when I say this - it used to be a WHOLE lot worse!

---

### Post by DigitalDuality on 2006-02-20
It'll get put there eventually.  I dunno.. i don't see the problem with doing it manually.  It's not like the old versions of Gimp or FF are that unable to do waht they're intended to do anyways.

Curious.. would you like to manage the repos and drop the upgrade in every single time one of the thousands of apps recieved an upgrade?

---

### Post by dickohead on 2006-02-20
This problem perhaps highlights the need for cross-distribution packages, or systems like that of (insert name) that resolve dependencies for certain systems for you automatically. I don't remember that name of the system, but someone will fill it in for me I'm sure.

Binary compatability is the term I think, it allows multiple systems to use the same file for installation, which is a brilliant idea for users.

---

### Post by majikstreet on 2006-02-20
Use fireupdate?

I dunno, but it must have something to do with that dude in your avatar; he looks evil.

---

### Post by Sirin on 2006-02-20
[QUOTE=dickohead]But with a Linux system, so many different people have so many different projects all with different release dates and different dependencies, trust me when I say this - it used to be a WHOLE lot worse![/QUOTE]

One of the things I miss about Windows, where they included the dependencies IN THE SAME INSTALLATION FILE as the app that required them. :cry: If DEBs/RPMs did the same things, "Dependency Hell" wouldn't even exist. :rolleyes:

---

### Post by endersshadow on 2006-02-20
[QUOTE=Sirin]Why aren't we able to upgrade apps when it's released? I've wanted to upgrade to Firefox 1.5.0.1 for a long time. Then I found out that I have to upgrade to Dapper just to get it. Why do we have to keep upgrading to get updates of apps. I was using Hoary, and when I wanted to upgrade GIMP to a newer POINT RELEASE from 2.2.2 to 2.2.8, I found out that I had to upgrade to Breezy JUST TO GET A POINT RELEASE UPGRADE. Why is this? With Windows, I was able to upgrade Firefox from 1.0.7 to 1.5.0.1 with an easy installer. With Ubuntu, I have to wait three months to get the Dapper install CD and upgrade to the new version JUST to get a new point release. Why are we being pushed so hard to upgrade to the newest version of Ubuntu? Isn't this like Microsoft, where we HAVE to upgrade to get the newest versions of the apps? Is it because Linux is so manual that it is IMPOSSIBLE to get 1.5.0.1 on Breezy? I'm running 1.5.0.1 right now from my /home/firefox folder, but I'm looking for a system-wide version.

The Automatix release of Firefox 1.5 ruined my system, by the way, so that's out of the question. :cry:[/QUOTE]

Perhaps you'd be best suited with Gentoo.  If you are unwilling to compile new versions of programs yourself in between releases, then don't use Ubuntu.  The Ubuntu vision is to make the best OS available, and it does that not by updating a version that's out, but focusing totally on the next release.  Much of the time, things are backported, and you can check them out there.  However, Firefox cannot be backported because of the dependencies on the 1.0.x Gecko engine throughout Gnome.  Ergo, you need to install 1.5.x separate from your original Firefox installation, so as not to overwrite needed SO's and the like.

Ubuntu is an OS that redefines itself every six months, with the focus on stability and usefulness.  If you want a continuously evolving OS, try Gentoo, or even Arch.  You get the latest packages, as soon as they come out, and each thing is updated one at a time.

Or, just learn how to compile manually.  Pick the right OS for you.  Don't pick an OS and then start disagreeing with its philosophy and development when there are other, more viable choices out there for your needs and preferences.

---

### Post by briancurtin on 2006-02-20
if you want bleeding edge stuff, you are either going to have to do it on your own or find another distro. as said earlier, gentoo and arch are good for having pretty new stuff all the time.

---

### Post by Kvark on 2006-02-20
[QUOTE=Sirin]One of the things I miss about Windows, where they included the dependencies IN THE SAME INSTALLATION FILE as the app that required them. :cry: If DEBs/RPMs did the same things, "Dependency Hell" wouldn't even exist. :rolleyes:[/QUOTE]
But then you would download, install on the hard disk and load into memory a separate version of each lib for each program that depends on it.

I don't see any big problem in being a couple months after. When using Windows I waited even longer before buying the new version of a program.

---

### Post by dickohead on 2006-02-20
6 Months to wait for new programs is not such a bad trade off to be a couple of version behind, hell people are still using internet explorer 5.5 and windows 98!!!

If you do really NEED firefox 1.5 or other bleeding edge programs, you can always install them yourself, or figure out why automatix didn't work.

But.... the bigger issue is that this shouldn't be a problem, and eventually might not be!

---

### Post by imagine on 2006-02-20
[QUOTE=Sirin]One of the things I miss about Windows, where they included the dependencies IN THE SAME INSTALLATION FILE as the app that required them. :cry: If DEBs/RPMs did the same things, "Dependency Hell" wouldn't even exist. :rolleyes:[/QUOTE]
On the other hand static linking leads to bigger packages, uses more memory and harddisk space. And if a security hole is found in a library which is used in many different versions on many different places on your computer then good luck.

---

### Post by Iandefor on 2006-02-20
In one way, it does suck, but in another way, keeping the same packages for six months at a time keeps it nice and stable. 

> 
One of the things I miss about Windows, where they included the dependencies IN THE SAME INSTALLATION FILE as the app that required them. :cry: If DEBs/RPMs did the same things, "Dependency Hell" wouldn't even exist. :rolleyes: True, but it's inefficient. You'd wind up with about 300 copies of some libraries, like maybe the GTK libraries, and every program would probably load their own special version of those libraries every time you ran it.
That gets messy really fast.

---

### Post by Robgould on 2006-02-20
The point is a good one.  This is the only real "complaint" that I have with Ubuntu.  You either have to do with out, manually install, or wait.

---

### Post by MetalMusicAddict on 2006-02-20
[QUOTE=Sirin]One of the things I miss about Windows...[/QUOTE]
One thing converts _must_ wrap their head around around is "Linux is not windows". Like Apple we must "Think Different".

I think there at least 2 guides here to help you get 1.5 on Breezy.

---

### Post by UbuWu on 2006-02-20
For some apps there are backports of newer versions.

---

### Post by Jucato on 2006-02-21
Also, you have to take into account that Windows is only one OS. While Linux has loads of distributions. So it necessarily takes time for devs to make sure that a particular installation won't break the stability of the system. I think that's a lot better than having the latest stuff but not being able to use them properly because the system was ruined by the installation. The "easy" installation of Windows has a price to pay, though. You basically have no control of what happens here. DLL's are installed automatically and are sometimes duplicated, overwritten, etc. (I have yet to see a Windows installer that lets you see what exactly will be installed). Besides, have you noticed how many libraries are installed in a single app installation, versus installing through the repositories?

But then, you still have a choice what to do when it comes to getting the latest stuff. You could stick with the version in the repository, compile it yourself, or install it manually (like in the case of Firefox). I prefer this last method versus Automatix, especially if you take the time to understand what you're doing. But if in you're in a rush, that's a different matter.

---

### Post by Sirin on 2006-02-21
[QUOTE=MetalMusicAddict]One thing converts _must_ wrap their head around around is "Linux is not windows". Like Apple we must "Think Different".[/QUOTE]

Apple's Mac OS X is not Windows, yet they have an easy packaging system. The  DEB packaging system, IMO, is somewhat messed up. The only easy and independent way to do it is via Apt, which you have to wait for them to update the repositories to add/update that specific app. Unlike Windows SP upgrades, there is no way to upgrade the distribution via Internet, so you're going to need a CD.

---

### Post by Sirin on 2006-02-21
[QUOTE=Fenyx]I have yet to see a Windows installer that lets you see what exactly will be installed. Besides, have you noticed how many libraries are installed in a single app installation, versus installing through the repositories?
[/QUOTE]

I have yet to see a DEB that will let me see what exactly will be installed.

---

### Post by GeneralZod on 2006-02-21
Are there any "rolling" distros around that are continously upgraded, apart from Gentoo? The ideal (for me!) would be one that has a good KDE implementation, is debian based (I don't know why, but haven't tasted apt/debs I just don't want to go back to yum/urpmi/rpm!), and gives you proper upgrades all the time you use it.  Mepis may or may not be a candidate -  I can't tell from their site whether they share the "freeze the version, issue security updates only" system with Ubuntu.

Edit:

[QUOTE=Sirin]I have yet to see a DEB that will let me see what exactly will be installed.[/QUOTE]


As far as I'm aware, all proper .debs have a manifest of included files, either contained in the .deb itself (which seems likely) or at [http://pdo.debian.net/cgi-bin/search_contents.pl?searchmode=filelist&word=gimp&version=testing&arch=i386](http://pdo.debian.net/cgi-bin/search_contents.pl?searchmode=filelist&word=gimp&version=testing&arch=i386) 

Hopefully, someone will write a decent GUI for dpkg that includes this info, if they haven't done so already.  Synaptic already does this for files that have already been installed.

---

### Post by Jucato on 2006-02-21
[QUOTE=Sirin]I have yet to see a DEB that will let me see what exactly will be installed.[/QUOTE]

A .deb file, AFAIK, only installs that particular package. It doesn't download and resolve any dependencies. That's why you will get dependency errors sometimes. In KDE, the contents of a deb file can be examined using Ark. And you will notice that there won't be anything that isn't part of the package, even libraries are not there.

In installing through repositories, apt-get, Synaptic, Adept, etc. show you what files will be installed along side the package that you chose. Even if you can't unselect them without ruining your installation, at least you can see what will be added to your system.

Windows installers, on the other hand, come in binary/executable forms, unless they are one of those self-extracting installers. They will install any and all files included in the installer, without you knowing what's in them.

The Linux way of installing things may be a bit more difficult, if you're coming from the Windows world. But it's a small price to pay for security and integrity. That's why, sometimes, I find shortcut installers to be more of a danger than the "old ways."

---

### Post by Robgould on 2006-02-21
We can quit with the windows is not linux line.  That has nothing to do with this.  Fedora is linux and in Fedora you can keep your packages updated between releases.  You have to use non standard repos, but you can do it.
 
This is not a limitation in Ubuntu...it is not something that could not be done.  It is a decision that was made by the Ubuntu management team to NOT do it.  Apparently they want to put most of theri energy into making their standard release work well, or work on a new release instead of spending a great deal of time reworking the relase for every new update that comes along.  I can see the point.

---

### Post by hashimoto on 2006-02-21
[QUOTE=Sirin]Unlike Windows SP upgrades, there is no way to upgrade the distribution via Internet, so you're going to need a CD.[/QUOTE]

You can upgrade to the next version via internet, no CD needed. Just edit your /etc/apt/sources.list to point to the new version (Dapper now in the works), then 
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Stormy Eyes on 2006-02-21
[QUOTE=Robgould]This is not a limitation in Ubuntu...it is not something that could not be done.  It is a decision that was made by the Ubuntu management team to NOT do it.  Apparently they want to put most of theri energy into making their standard release work well, or work on a new release instead of spending a great deal of time reworking the relase for every new update that comes along.  I can see the point.[/QUOTE]

Don't forget that if it's really important, it's probably in backports.

---

### Post by Jucato on 2006-02-21
[QUOTE=hashimoto]You can upgrade to the next version via internet, no CD needed. Just edit your /etc/apt/sources.list to point to the new version (Dapper now in the works), then 
```
sudo apt-get update
sudo apt-get upgrade
```[/QUOTE]
or
```
sudo apt-get dist-upgrade
```

Actually, I think Sirin has it the other way around. It's Windows that you can't upgrade without using a CD. Has anyone upgraded from Windows ME to XP using the internet? The so-called "Windows Updates" are just security patches that are needed to keep your system protected. We also have that, but less of it (because we have less security issues... but I'm not going there).

Stormy Eyes is right. If it's a very important update, it will probably be in the backports. But sometimes, even if it's important (like Firefox 1.5 or 1.5.0.1), it's not there because of some conflicting dependencies or stuff like that. Still, there are other ways to install it.

---

### Post by aysiu on 2006-02-21
It's just a different culture, I think.

People on dial-up prefer CDs, but people with broadband can use online updates.

Personally, I prefer updating things online instead of having to insert this CD and then that CD and then this CD again.

Unfortunately, Firefox is an extremely popular application with Ubuntu users, and there is also a large contingent of those users who aren't satisfied with 1.0.7 for whatever reason but don't feel like copying and pasting a few commands from the Wiki.

Maybe these users should consider Automatix?

---

### Post by TeeAhr1 on 2006-02-21
[QUOTE=aysiu]Unfortunately, Firefox is an extremely popular application with Ubuntu users, and there is also a large contingent of those users who aren't satisfied with 1.0.7 for whatever reason but don't feel like copying and pasting a few commands from the Wiki.[/QUOTE]
Well, it's probably because the pre-loaded version of 1.0.7 really really sucks, takes three days to load, *never* releases unused memory without a manual kill (at least on my box, YMMV), and is now incompatible with half the extensions out there.  Unfortunately, Gecko is tied in all over the place and removing 1.0.7 breaks all kinds of stuff, as I learned firsthand.

As to the second half of your comment, I totally agree.  [It's not that hard, people.]("https://wiki.ubuntu.com/FirefoxNewVersion")  Ten minutes, tops.

---

