---
title: "Ubuntu Trusty Partial Updates on New Install?"
date: 2014-01-27
forum: Ubuntu Development Version
---

### Post by Redalien0304 on 2014-01-27
Just installed Ubuntu Trusty via Live CD 1/18/2014. Updated then got list of Partial Updates. Have NOT installed Anything, Just LiveCD install & thats it.
is this normal or what?
here is the Partial upgrade List:

raig@craig-Latitude-D830:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  account-plugin-aim account-plugin-jabber account-plugin-salut
  account-plugin-yahoo cheese cheese-common empathy empathy-common
  evolution-data-server evolution-data-server-common evolution-data-server-goa
  evolution-data-server-uoa gir1.2-javascriptcoregtk-3.0 gir1.2-totem-1.0
  gir1.2-webkit-3.0 gstreamer1.0-clutter ibus-pinyin ibus-pinyin-db-android
  libcamel-1.2-45 libcheese-gtk23 libcheese7 libclutter-1.0-0
  libclutter-gst-2.0-0 libclutter-gtk-1.0-0 libjavascriptcoregtk-3.0-0
  libnm-gtk-common libnm-gtk0 libnss3 libqt5core5 libqt5dbus5 libqt5gui5
  libqt5network5 libqt5opengl5 libqt5printsupport5 libqt5sql5
  libqt5sql5-sqlite libqt5test5 libqt5widgets5 libqt5xml5 libtotem0
  libwebkitgtk-3.0-0 linux-generic linux-headers-generic linux-image-generic
  mcp-account-manager-uoa modemmanager nautilus-sendto-empathy network-manager
  network-manager-gnome python-pil totem totem-common totem-mozilla
  totem-plugins unity-webapps-service
0 upgraded, 0 newly installed, 0 to remove and 55 not upgraded.

---

### Post by Frogs Hair on 2014-01-27
Partial updates are often part of per-release testing. ***Moved to Ubuntu + 1 ***

---

### Post by OrangeCrate on 2014-01-27
Do this, in this exact order:

sudo apt-get update

sudo apt-get upgrade

sudo apt-get dist-upgrade

sudo apt-get update

sudo apt-get clean

sudo apt-get autoclean

sudo apt-get autoremove

That should do it.

(And yes, you can combine some of those command together with &&, but, let's keep it simple.)

Reference for all things APT, so that you have some idea of what you just did:

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

---

### Post by Cavsfan on 2014-01-27
You can also make aliases out of those CLI update/upgrade commands:

**gedit ~/.bashrc** in terminal.

add the blue lines after the other lines and save the file:  

```
# some more ls aliases
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'


[COLOR=#0000ff]# update aliases[/COLOR]
[COLOR=#0000ff]alias ud='sudo apt-get update && sudo apt-get upgrade && sudo apt-get clean'[/COLOR]
[COLOR=#0000ff]alias ud2='sudo apt-get dist-upgrade'[/COLOR]
[COLOR=#0000ff]alias ud3='sudo apt-get autoremove'[/COLOR]



```

Logout and back in and then all you have to do is enter **ud** and your password in terminal to get your updates.
If there is anything held back after getting all of the above updates, enter **ud2**.

That will pull in upgraded packages that also need to install new packages. A new kernel is a good example of where you would use **ud2**.

Then if you see it says you have unnecessary packages installed and it says enter **apt-get autoremove** to get rid of them just enter **ud3** and that will do the job.

This is how I always get my updates and it works well. :)

---

### Post by zika on 2014-01-28
> **OrangeCrate said:**
> Do this, in this exact order:

sudo apt-get update

sudo apt-get upgrade

sudo apt-get dist-upgrade

sudo apt-get update

sudo apt-get clean

sudo apt-get autoclean

sudo apt-get autoremove

That should do it.

(And yes, you can combine some of those command together with &&, but, let's keep it simple.)

Reference for all things APT, so that you have some idea of what you just did:

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)When using```
sudo apt-get dist-upgrade
```also be very awake and look very carefully if some of package You might need are going to be removed...

---

### Post by grahammechanical on 2014-01-28
I hope we have not forgotten this advice

[http://ubuntuforums.org/showthread.php?t=2181769](http://ubuntuforums.org/showthread.php?t=2181769)

I have only once accepted the offer to run a partial upgrade when using the development branch. Never again! In the early weeks of the development cycle not all the repositories are open and we get a message about that. Later on in the cycle we get the partial upgrade message. Such is life.

Regards.

---

### Post by OrangeCrate on 2014-01-28
Lighten up kids, the OP is trying to sort out a fresh install.

> Just installed Ubuntu Trusty via Live CD

If you have a better scheme on helping him out with his problem, post a solution, not some apocalyptic warning about taking a partial upgrade.

On the other hand, he hasn't responded to any of the posts, so, maybe the world did end for him.

:)

---

### Post by Cavsfan on 2014-01-28
> **OrangeCrate said:**
> Lighten up kids, the OP is trying to sort out a fresh install.



If you have a better scheme on helping me out of his problem, post a solution, not some apocalyptic warning about taking a partial upgrade.

On the other hand, he hasn't responded to any of the posts, so, may the world did end for him.

:)

+1 LoL! :P

---

### Post by Redalien0304 on 2014-01-30
ok Updated with Partial Upgrade no Problems. Even installed Cinnamon Desktop Nightly. No problems there either. Thanks OrangeCrate for full lis of commands. Cavsfan i skipped on making aliases out of the command, no need to make more complicated. thanks all

---

### Post by Cavsfan on 2014-01-30
> **Redalien0304 said:**
> Cavsfan i skipped on making aliases out of the command, no need to make more complicated. thanks all

Glad to see you got it going but, the aliases were to make it easier not more complicated lol. :lol:

---

### Post by OrangeCrate on 2014-01-30
> **Redalien0304 said:**
> ok Updated with Partial Upgrade no Problems. Even installed Cinnamon Desktop Nightly. No problems there either. **Thanks OrangeCrate for full list of commands.** Cavsfan i skipped on making aliases out of the command, no need to make more complicated. thanks all

You're most welcome, glad you got it worked out.

On other than a fresh install, please do pay close attention to the guidance/warnings from zilka and grahammechanical. It is quite possible to screw yourself up instantly, if the partial upgrade removes critical packages.

---

### Post by Cavsfan on 2014-01-31
> **OrangeCrate said:**
> You're most welcome, glad you got it worked out.

On other than a fresh install, please do pay close attention to the guidance/warnings from zilka and grahammechanical. It is quite possible to screw yourself up instantly, if the partial upgrade removes critical packages.

Ironically the CLI update methods mentioned cannot do a "partial upgrade". ;)

---

### Post by DougieFresh4U on 2014-01-31
> **OrangeCrate said:**
> Lighten up kids, the OP is trying to sort out a fresh install.



If you have a better scheme on helping him out with his problem, post a solution, not some apocalyptic warning about taking a partial upgrade.

On the other hand, he hasn't responded to any of the posts, so, maybe the world did end for him.

:)

Thank you.

---

### Post by bcschmerker on 2014-01-31
I'm currently testing UbuntuGNOME® Trusty Tahr™ (14.01a2 as of 31 January 2014) on an eMachines®/Acer® EL1210-09 upgraded with a 500W Shuttle® PSU and EVGA® low-profile VDA (nVIDIA® GT218 GPU), and the only packages held back on software updates at my end are _usb-modeswitch_ and _usb-modeswitch-data_.  Presumably the Development Release Team is working on fixing the packaging for the latest updates thereof, as upgradeing _usb-modeswitch-data_ to the latest version (as of 31 Jan) breaks _usb-modeswitch_. :oops: Complicating, that....

---

### Post by OrangeCrate on 2014-02-01
> **Cavsfan said:**
> Ironically the CLI update methods mentioned cannot do a "partial upgrade". ;)

Sorry, I'm not following you. Are you commenting about an apt-get dist-upgrade? If so, an apt-get dist-upgrade **is** a partial upgrade. Could you please explain your comment a bit further?

[http://askubuntu.com/questions/31047/how-do-i-know-if-apt-get-is-going-to-do-a-partial-upgrade](http://askubuntu.com/questions/31047/how-do-i-know-if-apt-get-is-going-to-do-a-partial-upgrade)

[https://wiki.ubuntu.com/U%2B1/partial_upgrade](https://wiki.ubuntu.com/U%2B1/partial_upgrade)

---

### Post by Cavsfan on 2014-02-01
> **Cavsfan said:**
> You can also make aliases out of those CLI update/upgrade commands:

**gedit ~/.bashrc** in terminal.

add the blue lines after the other lines and save the file:  

```
# some more ls aliases
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'


[COLOR=#0000ff]# update aliases[/COLOR]
[COLOR=#0000ff]alias ud='sudo apt-get update && sudo apt-get upgrade && sudo apt-get clean'[/COLOR]
[COLOR=#0000ff]alias ud2='sudo apt-get dist-upgrade'[/COLOR]
[COLOR=#0000ff]alias ud3='sudo apt-get autoremove'[/COLOR]



```

Logout and back in and then all you have to do is enter **ud** and your password in terminal to get your updates.
If there is anything held back after getting all of the above updates, enter **ud2**.

That will pull in upgraded packages that also need to install new packages. A new kernel is a good example of where you would use **ud2**.

Then if you see it says you have unnecessary packages installed and it says enter **apt-get autoremove** to get rid of them just enter **ud3** and that will do the job.

This is how I always get my updates and it works well. :)

> **OrangeCrate said:**
> Sorry, I'm not following you. Are you commenting about an apt-get dist-upgrade? If so, an apt-get dist-upgrade **is** a partial upgrade. Could you please explain your comment a bit further?

[http://askubuntu.com/questions/31047/how-do-i-know-if-apt-get-is-going-to-do-a-partial-upgrade](http://askubuntu.com/questions/31047/how-do-i-know-if-apt-get-is-going-to-do-a-partial-upgrade)

[https://wiki.ubuntu.com/U%2B1/partial_upgrade](https://wiki.ubuntu.com/U%2B1/partial_upgrade)

**sudo apt-get dist-upgrade** _**is not**_ a partial update. It is quite something else.

I'm saying that you can get a partial update from **update-mangler** but not from the CLI method I mentioned.
If you enter **sudo apt-get update && sudo apt-get upgrade** and get all of the updated packages presented and you see there are packages held back.
Then enter **sudo apt-get dist-upgrade** you will usually see that in addition to the packages that displayed as needing updating there are some NEW packages that need to also be installed displayed as well.

If there are still packages being held back then they are waiting on something. But, those packages cannot be installed via this method, thus no partial upgrade will occur.

A good example of this is when a new kernel needs to be installed. No harm has ever befallen me and this is the only update method I use. I also use this method every day on a development os.

I have seen a package still held back and maybe a day or so later the rest of the dependencies get put into place and the packages are then upgraded or whatever.

From **man apt-get**:
```
dist-upgrade
           dist-upgrade in addition to performing the function of upgrade, also intelligently handles changing dependencies with new versions of packages; apt-get has a "smart" conflict resolution system,
           and it will attempt to upgrade the most important packages at the expense of less important ones if necessary. The dist-upgrade command may therefore remove some packages. The
           /etc/apt/sources.list file contains a list of locations from which to retrieve desired package files.
```

---

### Post by OrangeCrate on 2014-02-01
^,

Thanks for your response.

---

### Post by Cavsfan on 2014-02-01
> **OrangeCrate said:**
> ^,

Thanks for your response.

You are welcome! :)

---

### Post by zika on 2014-02-01
I can still remember days (well documented here on these forums, easy to find...) when a bad day in U+1 wanted via dist-upgrade to rip almost all essential parts of our systems... That is why we've learned (hard way, sometimes) to follow changelogs and all similar stuff... Be awake, that is all that is needed... Do not judge all by these happy days and the fact that production is now much better than before... Daemon of bad dist-upgrade is lurking behind bushes... Trust me... ;) But that is almost the best and greatest fun in Testing... &#8222;Proposed&#8220; took some of it from Testing... ;) And made dis-upgrade just a tool after all...
> **Cavsfan said:**
> Ironically the CLI update methods mentioned cannot do a "partial upgrade". [IMG]http://ubuntuforums.org/images/smilies/icon_wink.gif[/IMG]OK, Your statement might depend on definition of &#8222;partial upgrade&#8220;... You might also say: O tempora, o mores, for old testing periods... ;)

---

### Post by Cavsfan on 2014-02-02
> **zika said:**
> I can still remember days (well documented here on these forums, easy to find...) when a bad day in U+1 wanted via dist-upgrade to rip almost all essential parts of our systems... That is why we've learned (hard way, sometimes) to follow changelogs and all similar stuff... Be awake, that is all that is needed... Do not judge all by these happy days and the fact that production is now much better than before... Daemon of bad dist-upgrade is lurking behind bushes... Trust me... ;) But that is almost the best and greatest fun in Testing... „Proposed“ took some of it from Testing... ;) And made dis-upgrade just a tool after all...
OK, Your statement might depend on definition of „partial upgrade“... You might also say: O tempora, o mores, for old testing periods... ;)

I know about the warning of doing a partial upgrade. But, that generally will occur more often with update manager than with cli commands. Perhaps dist-upgrade became more intelligent which is what this (already mentioned) text from man apt-get says:
```
dist-upgrade
    dist-upgrade in addition to performing the function of upgrade, also intelligently handles changing dependencies with new versions of packages; apt-get has a "smart" conflict resolution system,
    and it will attempt to upgrade the most important packages at the expense of less important ones if necessary. The dist-upgrade command may therefore remove some packages. The
    /etc/apt/sources.list file contains a list of locations from which to retrieve desired package files. See also apt_preferences(5) for a mechanism for overriding the general settings for
    individual packages.
```

It's not that difficult. Don't enable the Proposed repository (we've been warned and know what that does). Don't follow through with a dist-upgrade if something like ubuntu-desktop, etc. is going to be removed.
Otherwise I haven't had any problems and I have been testing since I believe Lucid. There are probably a lot of things that "used to" happen out there. But one cannot live in the past.

You should not have that much invested in a development install any way and I don't myself. I could copy and paste everything I might miss from another partition if need be. ;)
So I don't scare easily. ;)

---

### Post by cariboo on 2014-02-02
The partial upgrade warning has been carried over from Maverick development, when we were seeing quite a few posts where someone had done a partial upgrade, and basically made their systems useless. As Cavsfan says things have changed  for the better over the last several years, and now a partial upgrade doesn't seem to be as bad as they once were, and they seem to be much easier to recover from.

---

### Post by Cavsfan on 2014-02-02
> **cariboo907 said:**
> The partial upgrade warning has been carried over from Maverick development, when we were seeing quite a few posts where someone had done a partial upgrade, and basically made their systems useless. As Cavsfan says things have changed  for the better over the last several years, and now a partial upgrade doesn't seem to be as bad as they once were, and they seem to be much easier to recover from.

+1^
Thanks for that affirmation. :) 
I think I started participating in the development cycle when Precise was being developed. My first Ubuntu install was Ubuntu Jaunty Jackalope 9.04 as I recall.
Then I remember backing everything up and doing a fresh install of Ubuntu Karmic Koala 9.10.
Then when Ubuntu Lucid Lynx 10.04 LTS came out I stuck with that until about when Ubuntu 11.10 (Oneiric Ocelot) was released and I realized I wasn't able to support the different versions of grub for the custom grub wiki unless I installed each supported version.

Maybe that is why I never encountered any real partial upgrade. Ranch hand told me to always update with the cli commands and I never had a problem. He's the one that came up with update-mangler. :)
I've learned pretty much all I know from kind people here in this forum. Cariboo907, thanks for the things you have taught me like having only one swap partition. I went through hard times with a swap file for every install. /etc/fstab headaches one right after the other. :(
Also simply copying ~/.mozilla and ~/.thunderbird to a backup location and preserving everything I had. Before that I saved a json file for my bookmarks and had to re-install all of the other stuff the hard way.
Think I exported and imported all of my email before this. #-o

Then I figured out I could do the same with ~/.config/chromium.

Thank you! :guitar:

---

### Post by Hazzabin on 2014-02-02
Update mangler??

I know I'm thick as a brick, but this one is unknown to me. Where do I/we get it

---

### Post by Cavsfan on 2014-02-02
> **Hazzabin said:**
> Update mangler??

I know I'm thick as a brick, but this one is unknown to me. Where do I/we get it

Ranch hand, a guy in this forum that taught me all about grub and many other things used to call update manager update mangler for obvious reasons... ;)

---

### Post by Hazzabin on 2014-02-02
Ohhhhh ok thanks Cav, yeah well I did say I was as thick as, should of seen that :redface:

---

### Post by Cavsfan on 2014-02-03
> **Hazzabin said:**
> Ohhhhh ok thanks Cav, yeah well I did say I was as thick as, should of seen that :redface:

Or you could try this:

```
sudo apt-get install update-mangler
```

See how that works out for you. :P LoL

---

### Post by Hazzabin on 2014-02-04
yup I tried that too, it installed all un-necessary updates, totally re-configured the 'source list' and a ton of other stuff I didn't need  :guitar:

---

### Post by Cavsfan on 2014-02-04
> **Hazzabin said:**
> yup I tried that too, it installed all un-necessary updates, totally re-configured the 'source list' and a ton of other stuff I didn't need  :guitar:

LoL :lol:

---

### Post by Cavsfan on 2014-02-08
@[COLOR=#000000]cariboo907 I can see that apt-get is indeed getting more intelligent because previously when an an old kernel was still installed it would say use **apt-get autoremove** to remove the parts of the kernel but it wouldn't remove all of it. I used that method a few times only to find a couple of pieces left installed.
Now it seems like is much better at removing the whole kernel as I get this a lot after a new kernel is installed at least on Trusty when entering **sudo apt-get update && sudo apt-get upgrade** or in my case **ud**:
[/COLOR]```
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  [COLOR=#0000ff]linux-headers-3.13.0-6 linux-headers-3.13.0-6-generic linux-image-3.13.0-6-generic linux-image-extra-3.13.0-6-generic[/COLOR]
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  gir1.2-ibus-1.0 ibus ibus-gtk ibus-gtk3 libibus-1.0-5 python-ibus
6 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 417 kB of archives.
After this operation, 41.0 kB of additional disk space will be used.
Do you want to continue? [Y/n]

```

However, I still rely on a text file with all of the kernel components each time one is installed. Then I use it to remove that old one and mark it as deleted.

---

### Post by cariboo on 2014-02-08
I use a script on my headless server to remove old kernels, that works well for me:

```
dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get purge
```

Does a dry run, without removing anything, if everything looks good, then run:

```
dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge
```

**Note:** the only difference between the two commands is that the -y option is added before the purge option in the second command.

---

### Post by Cavsfan on 2014-02-09
> **cariboo907 said:**
> I use a script on my headless server to remove old kernels, that works well for me:

```
dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get purge
```

Does a dry run, without removing anything, if everything looks good, then run:

```
dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge
```

**Note:** the only difference between the two commands is that the -y option is added before the purge option in the second command.

Interesting.... Is that supposed to remove the previous kernel as I have 2 kernels installed at present - 3.13.0-8-generic and 3.13.0-7-generic.
When I ran the first part it said it was going to remove the 3.13.0-7-generic which would leave me with only one.

You would probably only use this if you knew a new kernel was just installed and you had 3 at the time you ran the script. Is that accurate?
That is pretty nice. :)

---

### Post by cariboo on 2014-02-09
I usually ignore my server, and just use it, it's only when I log into via ssh that I see a new kernel has been installed. I also only reboot, when I think about it. There is no access to this server from the outside world, so there's no problem with only rebooting occasionally. As you can see from the uprecords output, I've had several kernals installed:

```
uprecords
     #               Uptime | System                                     Boot up
----------------------------+---------------------------------------------------
     1    98 days, 19:58:28 | Linux 3.2.0-53-generic    Wed Sep 11 20:20:19 2013
     2    54 days, 07:33:04 | Linux 3.2.0-39-generic    Thu Mar 28 14:00:52 2013
     3    48 days, 00:51:53 | Linux 3.2.0-57-generic    Thu Dec 19 15:19:27 2013
     4    43 days, 11:40:26 | Linux 3.2.0-34-generic    Fri Dec  7 11:24:15 2012
     5    32 days, 01:57:36 | Linux 3.2.0-39-generic    Sat Aug 10 18:22:56 2013
     6    25 days, 21:37:33 | Linux 3.2.0-36-generic    Sun Jan 20 15:05:28 2013
     7    21 days, 03:24:31 | Linux 3.2.0-39-generic    Thu Jul 11 17:41:29 2013
     8    12 days, 22:32:40 | Linux 3.2.0-37-generic    Fri Feb 15 12:42:21 2013
     9    12 days, 17:49:17 | Linux 3.2.0-38-generic    Sat Mar  2 16:05:51 2013
    10    11 days, 19:51:40 | Linux 3.2.0-39-generic    Sun Jun  2 19:38:53 2013
----------------------------+---------------------------------------------------
->  16     4 days, 02:47:31 | Linux 3.2.0-58-generic    Wed Feb  5 16:09:46 2014
----------------------------+---------------------------------------------------
1up in     0 days, 16:34:33 | at                        Mon Feb 10 11:31:49 2014
t10 in     7 days, 17:04:10 | at                        Mon Feb 17 12:01:26 2014
no1 in    94 days, 17:10:58 | at                        Thu May 15 13:08:14 2014
    up   424 days, 12:05:30 | since                     Fri Dec  7 11:24:15 2012
  down     4 days, 19:27:32 | since                     Fri Dec  7 11:24:15 2012
   %up               98.879 | since                     Fri Dec  7 11:24:15 2012
```

The last time I cleaned out old kernels, there were three to be removed after I determined that it booted into the latest one successfully.

---

### Post by Cavsfan on 2014-02-10
> **cariboo907 said:**
> I usually ignore my server, and just use it, it's only when I log into via ssh that I see a new kernel has been installed. I also only reboot, when I think about it. There is no access to this server from the outside world, so there's no problem with only rebooting occasionally. As you can see from the uprecords output, I've had several kernals installed:

```
uprecords
     #               Uptime | System                                     Boot up
----------------------------+---------------------------------------------------
     1    98 days, 19:58:28 | Linux 3.2.0-53-generic    Wed Sep 11 20:20:19 2013
     2    54 days, 07:33:04 | Linux 3.2.0-39-generic    Thu Mar 28 14:00:52 2013
     3    48 days, 00:51:53 | Linux 3.2.0-57-generic    Thu Dec 19 15:19:27 2013
     4    43 days, 11:40:26 | Linux 3.2.0-34-generic    Fri Dec  7 11:24:15 2012
     5    32 days, 01:57:36 | Linux 3.2.0-39-generic    Sat Aug 10 18:22:56 2013
     6    25 days, 21:37:33 | Linux 3.2.0-36-generic    Sun Jan 20 15:05:28 2013
     7    21 days, 03:24:31 | Linux 3.2.0-39-generic    Thu Jul 11 17:41:29 2013
     8    12 days, 22:32:40 | Linux 3.2.0-37-generic    Fri Feb 15 12:42:21 2013
     9    12 days, 17:49:17 | Linux 3.2.0-38-generic    Sat Mar  2 16:05:51 2013
    10    11 days, 19:51:40 | Linux 3.2.0-39-generic    Sun Jun  2 19:38:53 2013
----------------------------+---------------------------------------------------
->  16     4 days, 02:47:31 | Linux 3.2.0-58-generic    Wed Feb  5 16:09:46 2014
----------------------------+---------------------------------------------------
1up in     0 days, 16:34:33 | at                        Mon Feb 10 11:31:49 2014
t10 in     7 days, 17:04:10 | at                        Mon Feb 17 12:01:26 2014
no1 in    94 days, 17:10:58 | at                        Thu May 15 13:08:14 2014
    up   424 days, 12:05:30 | since                     Fri Dec  7 11:24:15 2012
  down     4 days, 19:27:32 | since                     Fri Dec  7 11:24:15 2012
   %up               98.879 | since                     Fri Dec  7 11:24:15 2012
```

The last time I cleaned out old kernels, there were three to be removed after I determined that it booted into the latest one successfully.

Pretty sweet! I'll keep this in mind. :)

---

