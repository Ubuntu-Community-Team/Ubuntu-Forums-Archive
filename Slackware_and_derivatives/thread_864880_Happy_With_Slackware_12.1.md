---
title: "Happy With Slackware 12.1"
date: 2008-07-20
forum: Slackware and derivatives
---

### Post by Vince4Amy on 2008-07-20
I just downloaded and installed the first three discs of Slackware 12.1 selecting packages during the installation using the menu option.

This is a brilliant operating system, it's very fast, very stable and the closed source ATI Driver works perfectly without any tweaking needed. I think this is the only distribution which properly detects my monitor too.

I'm also pleased with the way that the installer allowed me to choose packages along the way, however I'm not sure how to remove KDE components I don't need such as kopete, kontact etc...

It's not as hard as I heard to get anything done, I don't know why this is a common thing I hear about Slack, it's just as easy as any distro. Just a little bit of research and Repositories, Swaret and updates were set up. Easy.

Installing tgz packages are easier than installing .debs or .rpms IMO and it is certainly faster at doing so. For example Firefox 3 tgz took no more than a second to install.

LILO successfully detected my partitions and works great.

Changing init so that KDE would launch on startup was easy as well, this is a nice solid, stable OS which is very fast.

---

### Post by andrew.46 on 2008-07-20
Hi:

> **Vince4Amy said:**
> 

I'm also pleased with the way that the installer allowed me to choose packages along the way, however I'm not sure how to remove KDE components I don't need such as kopete, kontact etc... 

An easy way to do this is to run pkgtool as root and select 'Remove'. Can also be done manually with 'removepkg'.


> It's not as hard as I heard to get anything done, I don't know why this is a common thing I hear about Slack, it's just as easy as any distro. Just a little bit of research and Repositories, Swaret and updates were set up. Easy.

Installing tgz packages are easier than installing .debs or .rpms IMO and it is certainly faster at doing so.


Have a look at slackbuilds.org as well where there is an avalanche of well-crafted build scripts or 12.1.

> LILO successfully detected my partitions and works great.

I have long preferred lilo to grub. As you have experienced it is reliable, easy to configure, simple and just plain *works* :-).

   Andrew

---

### Post by kk0sse54 on 2008-07-20
If you want to remove packages the GUI way then just use kpackage as it will list all the packages that are installed and give you the option to uninstall those you don't need.> 
Have a look at slackbuilds.org as well where there is an avalanche of well-crafted build scripts or 12.1.
 +1 for SlackBuild it will make your life a lot easier especially when you try to install a software that has some obscure dependency which you don't realize until you try running it and it won't start.

---

### Post by Vince4Amy on 2008-07-20
I'll have a look at that. I'm going to give slamd64 a try.

---

### Post by Bachstelze on 2008-07-20
> **Vince4Amy said:**
> 
I'm also pleased with the way that the installer allowed me to choose packages along the way, however I'm not sure how to remove KDE components I don't need such as kopete, kontact etc...

You can't remove single KDE components like that in Slackware. Unlike most other distributions, Slackware distributes KDE by keeping the original packages (kdelibs, kdebase, kdenetwork, kdemultimedia, kdeartwork, kdegames, etc.) and not by splitting them to create one package for each application.

This means that if you want to remove e.g. Kopete, you'll have to remove the whole kdenetwork package, which might also remove other things you need.

---

### Post by BLTicklemonster on 2008-07-21
I'm looking across the room at a box that says, "slackware 7.1" on it. I bought that baby years ago when a person like myself interested in linux could go online and find a site where I could download slackware or any other flavor, but the whole thing was a totally disjointed mess. You click, "download" and it would take you to a page with a gazillion files. No rhyme nor reason to any of it. I never had any idea what to do with any of them. So when I saw that slackware in the store for 20 bucks or so, I figured it was worth a shot.

Yep, I got it installed, but I had no idea what to do at that point. It blew my mind that in the '90s there could be an operating system that people raved about that didn't have a user interface that you could use to do stuff like... see what's on the cd.

And getting the internet to work ... Well, I gave up and the box has sat where it is ever since.

Recently I realized that I have a spare hard drive with 31.5 gigs on it sitting there empty, and figured what the heck. I almost downloaded slackware to give it another shot, but I wonder: if I were to install it, would I still have the grub like menu where I could choose between Ubuntu, XP or slackware? Automatically? I have no desire nor need to "tweak" any settings or edit any files whatsoever, so if I would have to do that, forget it. As long as I'm asking, if it is automatic, are other distros like that? That's the main thing keeping me from trying out new ones. And what if I ever decide to do away with slackware? How would I boot up and get to Ubuntu or xp then?

(sorry for the hijack)

---

### Post by Bachstelze on 2008-07-21
> **BLTicklemonster said:**
> 
Recently I realized that I have a spare hard drive with 31.5 gigs on it sitting there empty, and figured what the heck. I almost downloaded slackware to give it another shot, but I wonder: if I were to install it, would I still have the grub like menu where I could choose between Ubuntu, XP or slackware?

Yes, Slackware will prompt you during installation about whether you want to install LILO to the MBR. Just say Skip and your GRUB will not be touched. I repeat, it will **not** be touched: when you'll reboot, you will have the exact same boot screen you had before, no mention of Slackware on it, so you **will** have to edit GRUB's config file. But anyway, if you don't like to tinker with stuff, Slackware is not for you.

---

### Post by BLTicklemonster on 2008-07-21
Okay, that much tinkering I don't mind. :)

---

### Post by Bachstelze on 2008-07-21
> **BLTicklemonster said:**
> Okay, that much tinkering I don't mind. :)

Then I guess you could give it a try. As you might have guess, there is nothing particular to do if you want to get rid of it. Since you will install it on a separate hard drive, unplugging it and removing Slackware from your GRUB is all it will take to have your system back to how it was before you installed it.

---

### Post by empcrono on 2008-08-27
Slackware is the bomb ^_^

---

### Post by Vince4Amy on 2008-08-31
Slackware seems to be the only distro which is happy with my ATI card using the closed source drivers, there's not even the checkboard effect with WINE apps on the latest drivers.

---

### Post by factotum218 on 2008-11-02
Nice thing about Slacky. A prime example of functional simplicity. Yet people wonder why so little has changed since it's conception. Read a review about any release and it's usually the same.

It's still Slackware, it's still the same, and we will not let pkgtool be considered a package manager because it doesn't download from a remote repository where there is expected to be no less that 10,000 pre-packaged applications to pick from.

May the source be with you.

Also check [THIS]("http://rute.2038bug.com/index.html.gz") out. I kept it around for a long time and it has made my Slackware experience educational and fun.

---

### Post by kathem_1 on 2008-11-03
I heared before that slack is almost to be the oldest version of linux bofore Redhat or Debian is that right? I'm very intersted to use it .

---

### Post by factotum218 on 2008-11-03
> **kathem_1 said:**
> I heared before that slack is almost to be the oldest version of linux bofore Redhat or Debian is that right? I'm very intersted to use it .

Yes, Slackware pre dates Redhat and Debian...wow..I feel old.

---

### Post by kk0sse54 on 2008-11-03
> **kathem_1 said:**
> I heared before that slack is almost to be the oldest version of linux bofore Redhat or Debian is that right? I'm very intersted to use it .

Yes Slackware is the oldest surviving Linux Distribution and was originally based off of Softlanding Linux System which was the largest distro in it's time.

---

### Post by Vince4Amy on 2008-11-04
OpenSUSE is based on Slackware isn't it?

---

### Post by kk0sse54 on 2008-11-04
> **Vince4Amy said:**
> OpenSUSE is based on Slackware isn't it?

Yes indirectly, Suse was based off Slackware and was then bought by Novell  where it got renamed to openSUSE as they made it a bit more open source. These days though the only thing openSUSE has in common with Slackware is that they are both linux distros :p

on a side note: 500 posts :KS

---

### Post by xarte on 2009-01-01
I'm dead keen to try Slack, but I'm just SO clueless I'm sure I'm going to screw it up. At this point I need like a n00b-proof hand-holding walk-through where even the most obvious stuff is explained.

My experience of linux so far is that I learn by having things not work then googling to find out what the fix is. But it's such a slow way to do things! It must have taken a couple of hours before I found out that I didn't have build-essentials installed.  I think I've spent about two days trying to install webcam drivers. 

I'm starting to get a *small clue regarding partitioning, so that's a start, but I'll have to go google lilo, grub and bootloading first I think.

When I looked at the Slackware downloads and saw two files for each disk, and several disks, I figured I might be out of my depth. So far it's just been choose either 64 or 32 bit, download an ISO, burn it and off you go.

Edited to add: my ISP's unmetered download page has a DVD iso of Slackware ..so... in a few hours (!) .... deep breath and dive in!

---

