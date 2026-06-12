---
title: "borked system after last set of updates"
date: 2012-03-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by rburkartjo on 2012-03-18
update this sunday am went fine until i tried to reboot then ubuntu fals to load. tried to the recover mode and dropped down to root shell and tried apt-get update && apt-get upgrade and also apt-get update && apt-get dist-uprade. but that didnt work. any ideas? it is definately problem with 12.04 because my linux mint partition works fine. tks

---

### Post by rburkartjo on 2012-03-18
note i cant even get to the login screen.

---

### Post by kansasnoob on 2012-03-19
Mine's borked too. I updated earlier today, then did some chores, checked a few things on the web, checked mail, etc, then shut the puter down to take a nap.

Now Precise won't boot up, haven't examined it very closely, but I booted right into Oneiric on the same box w/o trouble ;)

I think tomorrow or the next day I'll try some fresh installs anyway to see if I can reproduce any of the recently mentioned installer problems.

---

### Post by shuttleworthwannabe on 2012-03-19
I am curious, what hardware specs are you guys having? nvidia/ati cards??

---

### Post by kansasnoob on 2012-03-19
Intel Atom CPU 230 @ 1.60GHz w/Intel 82945G/GZ Integrated Graphics here. Didn't show any problems prior to shutdown, now just a black screen.

I may dink around a bit in a chroot, but I'm really curious to check out the installer(s) soon anyway due to the number of installer complaints I've noticed lately ;)

---

### Post by Harry33 on 2012-03-19
And may someone of you list the the updates that did this?
When using a dev version, it is a good practice to update the setup very often, in order to avoid updating a large number of packages at the same time.
If you have a long list of updates to run, however, please update them only in small groups.

Well, anyway I have three setups (also one with Intel graphics card), 32-bit and 64-bit.
I have run all the latest updates and there is no problem what so ever.
It is true that I do not have all the default packages installed, the latest update being mesa (8.0.1-0ubuntu5).

---

### Post by ventrical on 2012-03-19
Same here Harry. I have 8 machines with different settings and they are all working as if they were LTS releases... and I think even that the 'bug of the century' has been fixed ! :) *edit* Nope .. nada still there.

---

### Post by PaulW2U on 2012-03-19
> **Harry33 said:**
> If you have a long list of updates to run, however, please update them only in small groups.

Good advice Harry, this is what I do and have done for some time now.

I update using synaptic after sorting the updates by version number. Then I update four of five packages at a time, sometimes more, based on either the package name, version number or both. Large updates such as LibreOffice are always left to last and then upgraded all in one go.

When updating Kubuntu I always update the KDE packages separately from the Kubuntu packages. It makes it a whole lot easier that way to identify where problems lie.

At the moment both Kubuntu and Ubuntu 12.04 are running fine here.

---

### Post by neu5eeCh on 2012-03-19
Did you do a dist-upgrade or just an upgrade? (Sorry if that's a stupid question.)

**Edit: **I ask because there are currently 34 packages being held back (since yesterday). They are:

empathy empathy-common gir1.2-rb-3.0 gnome-online-accounts gvfs
  gvfs-backends gvfs-bin gvfs-common gvfs-daemons gvfs-fuse gvfs-libs
  libgoa-1.0-0 libidl0 libpackagekit-glib2-14 libpurple0 librhythmbox-core5
  libtotem-plparser17 libunity-2d-private0 linux-generic-pae
  linux-headers-generic-pae linux-image-generic-pae nautilus-sendto-empathy
  python-ubuntuone-control-panel rhythmbox rhythmbox-data
  rhythmbox-plugin-cdrecorder rhythmbox-plugins rhythmbox-ubuntuone
  ubuntuone-control-panel ubuntuone-control-panel-common
  ubuntuone-control-panel-gtk unity-2d-panel unity-2d-shell unity-2d-spread

---

### Post by PaulW2U on 2012-03-19
> **VTPoet said:**
> Did you do a dist-upgrade or just an upgrade? (Sorry if that's a stupid question.)

I **never** do a dist-upgrade. ;)

I generally have a poke around with synaptic or aptitude to get a feel of what should or shouldn't be removed. I suppose synaptic and aptitude both do the equivalent of a dist-upgrade behind the scenes though.

**Edit**: You edited your post while I was writing mine. :)

I'd love to play with that lot. I'm sure that I've applied all those updates, some yesterday in fact.

---

### Post by kaldor on 2012-03-19
> **VTPoet said:**
> Did you do a dist-upgrade or just an upgrade? (Sorry if that's a stupid question.)

**Edit: **I ask because there are currently 34 packages being held back (since yesterday). They are:

empathy empathy-common gir1.2-rb-3.0 gnome-online-accounts gvfs
  gvfs-backends gvfs-bin gvfs-common gvfs-daemons gvfs-fuse gvfs-libs
  libgoa-1.0-0 libidl0 libpackagekit-glib2-14 libpurple0 librhythmbox-core5
  libtotem-plparser17 libunity-2d-private0 linux-generic-pae
  linux-headers-generic-pae linux-image-generic-pae nautilus-sendto-empathy
  python-ubuntuone-control-panel rhythmbox rhythmbox-data
  rhythmbox-plugin-cdrecorder rhythmbox-plugins rhythmbox-ubuntuone
  ubuntuone-control-panel ubuntuone-control-panel-common
  ubuntuone-control-panel-gtk unity-2d-panel unity-2d-shell unity-2d-spread

No issues for me. Though, I also have lots held back (some of which have been held back for a few days):

```

 empathy empathy-common gnome-online-accounts gvfs gvfs:i386 gvfs-backends
  gvfs-bin gvfs-common gvfs-daemons gvfs-fuse gvfs-libs gvfs-libs:i386
  ia32-libs-multiarch:i386 libgoa-1.0-0 libidl0 libpackagekit-glib2-14
  libpurple0 libtotem-plparser17 libunity-2d-private0 linux-generic
  linux-headers-generic linux-image-generic nautilus-sendto-empathy udisks
  unity-2d-panel unity-2d-shell unity-2d-spread wine1.4 wine1.4-amd64
  wine1.4-common wine1.4-i386:i386

```

---

### Post by neu5eeCh on 2012-03-19
I don't use synaptic or the aptitude command. I just so totally **know** I'm going to shoot my foot off. I do apt-get update & upgrade and that's that; so I was wondering whether I should expect the same.

---

### Post by kansasnoob on 2012-03-19
I'd love to spend the time to try and figure out what went wrong on mine ............. I really would, but then who's going to test fresh installs?

With both Xubuntu and Lubuntu rebuilding to go "non-pae" someone must test. And Evan Dandrea is considering changes:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/775124](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/775124)

I hate to see ubiquity messed with this late in the dev process :(

---

### Post by larrypg on 2012-03-19
Hello,

Maybe I missed something but aren't those revisions refering to oneric?  Probably my eyeballs just did not see correctly.

---

### Post by chubbtech on 2012-03-19
where do I look for an update log?  I'm having trouble with Oneiric since last update (I think)

---

### Post by kansasnoob on 2012-03-19
> **larrypg said:**
> Hello,

Maybe I missed something but aren't those revisions refering to oneric?  Probably my eyeballs just did not see correctly.

What revisions are you talking about?

---

### Post by Gregory Lee on 2012-03-19
Following what I believe were recommendations of you experienced users, starting from the Alpha2 amd64 DVD, I've used "aptitude update;aptitude safe-upgrade" exclusively, several times a day.  No removing packages or any dist-upgrade (except a couple of times aptitude did remove something, presumably something unused).  I'm all up to date, now, except for 6 packages which have been held back for several days: empathy, empathy-common, kde-l10n-engb, language-pack-kde-en, libpurple0, nautilus-sendto-empathy.  I don't think I use any of these.  I have had some crashes, but no problem today, yet.

---

### Post by larrypg on 2012-03-19
The revisions in this...[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/775124](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/775124)

---

### Post by kansasnoob on 2012-03-19
> **larrypg said:**
> The revisions in this...[https://bugs.launchpad.net/ubuntu/+s...ty/+bug/775124](https://bugs.launchpad.net/ubuntu/+s...ty/+bug/775124).

You're link is broken, but regardless look at the last two or three comments:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/775124/comments/21](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/775124/comments/21)

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/775124/comments/22](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/775124/comments/22)

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/775124/comments/23](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/775124/comments/23)

Those are from today!

And if they start playing with ubiquity this late in a dev cycle we're in for trouble!!!!!!!!!!!!!!

---

### Post by cariboo on 2012-03-19
@kansasnoob

Did you miss this email?

> Greetings everyone. As mentioned in last week's meeting, the ubiquity
team is having an installer sprint starting today and ending on Weds. As
a qa community, we have the opportunity to help participate and confirm
bug fixes, as well as get possible critical bugs that are still
outstanding fixed. The idea is to test the daily iso's specifically for
the bugs the team has created fixes for. A summary of each day's changes
can be found on this page:
[http://pad.ubuntu.com/ubuntu-installer-sprint](http://pad.ubuntu.com/ubuntu-installer-sprint). If your curious about
following along in "realtime", visit and idle in the #ubuntu-installer
channel on freenode.  For testing purposes, we will use the daily iso
builds on the iso tracker to test; using the bugs mentioned as focal
points for testing. We will coordinate our testing in the
#ubuntu-testing channel. If you find a bug has not been fixed that
should have been fixed as part of the changes, please report directly
against that bug. If you find a new issue, report it against ubiquity as
usual.

The current plan is as follows:

Monday, Mar 19th.
    Ubiquity team sprints and fixes bugs / tests the installer
    Ubiquity teams fixes are documented and incorporated into the build
for tomorrow's iso
Tuesday, Mar 20th
    QA community tests the daily iso, specifically ensuring it works on
there hardware, and the targeted bugs are no longer present
    Ubiquity team sprints and fixes bugs / tests the installer
    Ubiquity teams fixes are documented and incorporated into the build
for tomorrow's iso
Wednesday, Mar 21st
    QA community tests the daily iso, specifically ensuring it works on
there hardware, and the targeted bugs are no longer present
    Ubiquity team sprints and fixes bugs / tests the installer
    Ubiquity teams fixes are documented and incorporated into the build
for tomorrow's iso
Thursday, Mar 22nd
    QA community tests the daily iso, specifically ensuring it works on
there hardware, and the targeted bugs are no longer present

Lastly, since our coverage is not intended nor likely to be completely
comphrehensive, this is a good time to test more exotic / problematic or
undertested hardware. People who have physical access to such hardware
(such as powerpc's, or mac intels and other EFI booting hardware, wubi
and dual booting, etc) are especially encouraged to take part and make
sure there hardware has good support for precise. If you've never done
iso testing before, this is also a good time to try it out. The schedule
and pace will be much more relaxed with iso's only occurring once a day,
and the tests being targeted for specific issues.

Thanks everyone and happy testing!

Nicholas

---

### Post by rburkartjo on 2012-03-22
still messed up but at least i can get to a virtual terminal. does anyone know how i can try to fix from the command line. if i try to update from the command line i get the error message that no sources will load. willing to try anything. note i still cant get to the login screen

---

### Post by tehowe on 2012-03-22
> **rburkartjo said:**
> still messed up but at least i can get to a virtual terminal. does anyone know how i can try to fix from the command line. if i try to update from the command line i get the error message that no sources will load. willing to try anything. note i still cant get to the login screen

So I assume you've tried

```
sudo apt-get update && sudo apt-get upgrade
```

from your terminal.

I don't know if this will help, but here's the package list on my notebook

[http://pastebin.com/97NFNfG2](http://pastebin.com/97NFNfG2)

As a last resort you could (back up your files first) then copy this over to your home directory as plaintext by pasting it into nano, then save it as 'packagelist' and from the terminal

```
sudo dpkg --set-selections < packagelist
```

then 

```
sudo aptitude dselect-upgrade 
```

That will install everything on my notebook onto your machine. It may pull in some packages unrelated to your display hardware (this Acer has some Intel chip in it) but at least it's a snapshot of a working system. With a bunch of extra stuff like kdenlive and scribus, but oh well. Good luck!

(I'm assuming you're browsing these forums from another machine and that you can get a file into your ailing machine with a USB key via the terminal from /media/somewhere)

---

### Post by rburkartjo on 2012-03-23
te tks may give it a try. if cant get to work can just do a reinstall when the final comes out. just trying to see if it can be fixed first. all my important files are on my linux mint 12 partition

---

### Post by jerrylamos on 2012-03-23
This is "development" of an "unstable" product until final release.  Expect serious crashes (often).

So what I do is make a new partition(s) and install various levels into them.  Pre-Alpha done by a new install of Oneiric + modifying sources.list, Alpha 1, Alpha 2, Beta 1, ...

I always have a past partition available when doing anything involving a new level.

So far in "precise?" pangolin I've had "install" bork not only the test partition but screw up grub so I couldn't even get the initial grub menu.

Solution was to boot CD Live and install a Lucid LTS into an old partition which fixed grub so I could boot "precise?" pangolin again.

I have a relatively current notebook and netbook, plus the older ones laying around.  

Lately precise pangolin has installed successfully.

Why don't I do an "update" once I'm past the "sources.list" stage?

1. No matter what, update from an older release has -always- gobbled up more space on the hard drive.

2. Installs "ubiquity" is fertile ground for lots of bugs to report.

3. I'm learning a lot of practical linux chasing bugs.....

Jerry

---

### Post by rburkartjo on 2012-03-31
found out what messed my system. just reinstalled 12.04 this time b2. i was carefull and alway did safe update but somehow a partial didnt go thru. i noticed when i went to 12.04 b2 i had to run
sudo rm -rf /var/cache/apt/archives/partial
to fix

---

### Post by ScientificProp on 2012-04-04
I also had a problem booting after allowing the Important Security Updates to install. I had previously installed all of them, but only a few at a time. Then, this time there were several, I think about 18?, so I just clicked on the main box for Important Security Updates to install all of them. (Probably won't do that again) They seemed to install OK, I was asked to enter my password then afterwards I was instructed to reboot the system. Included in the list of updates was a Linux kernel #17 and related stuff.
When I rebooted all I got was a purple screen. So I CTRL-ALT-Delete and rebooted, this time in the RECOVER option. It seemed to boot OK, at least to a command prompt. Another regular boot, however, gave me the same purple screen. So, I did another reboot via CTRL-ALT-Delete, but this time selected the option to boot a previous version and selected the kernel number 16. It booted fine and allowed to login and see my GUI screen.

I'm running 11.10 64-bit with NVidia drivers to run my 520 Nvidia graphics card. Do I have to reinstall drivers whenever the kernel is updated?

So, What Happened? I am glad that I was able to recover the system, but I'd like to better understand the Updates process. How do I know when updates are safe to install?

---

### Post by cariboo on 2012-04-05
> **ScientificProp said:**
> I also had a problem booting after allowing the Important Security Updates to install. I had previously installed all of them, but only a few at a time. Then, this time there were several, I think about 18?, so I just clicked on the main box for Important Security Updates to install all of them. (Probably won't do that again) They seemed to install OK, I was asked to enter my password then afterwards I was instructed to reboot the system. Included in the list of updates was a Linux kernel #17 and related stuff.
When I rebooted all I got was a purple screen. So I CTRL-ALT-Delete and rebooted, this time in the RECOVER option. It seemed to boot OK, at least to a command prompt. Another regular boot, however, gave me the same purple screen. So, I did another reboot via CTRL-ALT-Delete, but this time selected the option to boot a previous version and selected the kernel number 16. It booted fine and allowed to login and see my GUI screen.

I'm running 11.10 64-bit with NVidia drivers to run my 520 Nvidia graphics card. Do I have to reinstall drivers whenever the kernel is updated?

So, What Happened? I am glad that I was able to recover the system, but I'd like to better understand the Updates process. How do I know when updates are safe to install?

You do realize that we are discussing 12.04 in this sub-forum? Any problems with with older versions should be addressed in [General Help]("http://ubuntuforums.org/forumdisplay.php?f=331"), or [ABT]("http://ubuntuforums.org/forumdisplay.php?f=326").

---

