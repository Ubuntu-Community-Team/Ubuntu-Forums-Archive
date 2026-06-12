---
title: "Snaps are causing confusion and bad ratings"
date: 2022-01-07
forum: The Cafe
---

### Post by Leslie Viljoen on 2022-01-07
I have noticed that Snaps are causing a lot of confusion and bad ratings in the Ubuntu Software manager.
I'd like to provide an example but I can't seem to add images here, and this is the second attempt to post this message after I spent an hour typing and then lost it all because apparently didn't have a security token.

In short, for the app "deadbeef-vs":

1. "This application is unconfined" and yet it can't open files from the second drive. The reason is Snap permissions, but few people seem to realise that because there are 11 1-star reviews for the app, most talking about how the app is crap because it can't open files.
2. Permissions for this app are very odd:
a. "Play and record sound" is listed twice and doesn't prevent playing audio.
b. "Play audio" is a separate permission which conflicts with that.
c. "Read/write files on removable storage devices" is misnamed because my second drive is not removable.

Wouldn't it be better if Snap apps asked for their relevant permissions, or at the very least popped up the permissions dialog after install? That would put Ubuntu apps on par with Android apps.

---

### Post by CharlesA on 2022-01-07
Moved to the Cafe as this didn't seem to fit elsewhere.

---

### Post by poorguy on 2022-01-08
I personally have nothing against Snaps and the few I have installed and used seem to work okay however the initial start of a Snap App does seem to be slow at opening but once opened seemed to work well.

I think eventually Snaps may turn out to be a good thing but for now seem to have a few issues.

I prefer to use the **Terminal **or **Synaptic Package Manager **to install software.

Just my 25 cents worth.


Life is good. ;)

---

### Post by DuckHook on 2022-01-08
> **Leslie Viljoen said:**
> …Wouldn't it be better if Snap apps asked for their relevant permissions, or at the very least popped up the permissions dialog after install?…
Yours isn't the only problem with snaps. [On a separate thread]("https://ubuntuforums.org/showthread.php?t=2470573"), I recently had to deal with the known issue of runaway app bloat.

There are still many issues with snap that need working out. Due to the nature of the beast, some of them may never be.

FWIW, this is not the place to make suggestions to Canonical. Ours is a user supported forum and the devs rarely if ever visit here. The venue where the devs hang out is: [https://discourse.ubuntu.com/](https://discourse.ubuntu.com/)

As for your specific issue: though I really dislike the idea of recommending PPAs and don't normally condone it, the whole snaps imbroglio is forcing more and more people back to this (questionable) platform. There is a PPA for your app that appears to be recently maintained:  [https://launchpad.net/~starws-box/+archive/ubuntu/deadbeef-player](https://launchpad.net/~starws-box/+archive/ubuntu/deadbeef-player)

:!: **CAUTION** :!:
I don't use deadbeef and know nothing about this maintainer. As with all PPAs do your research and proceed at your own risk.

---

### Post by Leslie Viljoen on 2022-01-12
Thanks for the pointers everyone! I did get DeaDBeeF working fine but the package management caused a bad experience and I think Ubuntu is going to lose many new users if pretty much every application has these issues. I'll try discourse.

---

### Post by Skaperen on 2022-01-12
i avoid snaps primarily because i don't thoroughly understand how they run.  i don't mean how to start them but what kind context they run in.

---

### Post by Leslie Viljoen on 2022-01-16
Bug reported here, is anyone wants to follow along:
[https://bugs.launchpad.net/snap-store-desktop/+bug/1957715](https://bugs.launchpad.net/snap-store-desktop/+bug/1957715)

---

### Post by bernard010 on 2022-01-28
Excellent job. If a Snap has any problems file a bug report.
That is how to get them working. 
If they do not know there is a problem, they will not be fixed.

---

### Post by TheFu on 2022-01-28
> **bernard010 said:**
> Excellent job. If a Snap has any problems file a bug report.
That is how to get them working. 
If they do not know there is a problem, they will not be fixed.

I consider privacy to be very important. Every time I login to any online service, I consider whether that service is worth the lack of privacy or not.  Last time I looked, the barrier to provide a bug report required setting up a new account first. That's for landscape and github and most other locations - like Mozilla.

For me, that barrier is too high for bug reporting, for a program that isn't working and will likely not work on my system due to "snap" anyway.  About 80% of snaps haven't worked for me or break important, but non-standard, workflows.

---

### Post by #&amp;thj^% on 2022-01-29
> **Leslie Viljoen said:**
> I have noticed that Snaps are causing a lot of confusion and bad ratings in the Ubuntu Software manager.
I'd like to provide an example but I can't seem to add images here, and this is the second attempt to post this message after I spent an hour typing and then lost it all because apparently didn't have a security token.

In short, for the app "deadbeef-vs":

1. "This application is unconfined" and yet it can't open files from the second drive. The reason is Snap permissions, but few people seem to realise that because there are 11 1-star reviews for the app, most talking about how the app is crap because it can't open files.
2. Permissions for this app are very odd:
a. "Play and record sound" is listed twice and doesn't prevent playing audio.
b. "Play audio" is a separate permission which conflicts with that.
c. "Read/write files on removable storage devices" is misnamed because my second drive is not removable.

Wouldn't it be better if Snap apps asked for their relevant permissions, or at the very least popped up the permissions dialog after install? That would put Ubuntu apps on par with Android apps.

Although I agree Snaps are a Royal pain in the Rear.
There is a small work-around.

```
sudo snap connect deadbeef-vs:removable-media
```
Check Connections with:>>(DeadBeef should be running before hand)
```

snap connections deadbeef-vs
```
Should show something like:
```
Interface        Plug                         Slot                     Notes
alsa             deadbeef-vs:alsa             -                        -
audio-playback   deadbeef-vs:audio-playback   :audio-playback          -
dbus             -                            deadbeef-vs:dbus-daemon  -
desktop          deadbeef-vs:desktop          :desktop                 -
desktop-legacy   deadbeef-vs:desktop-legacy   :desktop-legacy          -
gsettings        deadbeef-vs:gsettings        :gsettings               -
home             deadbeef-vs:home             :home                    -
network          deadbeef-vs:network          :network                 -
network-bind     deadbeef-vs:network-bind     :network-bind            -
optical-drive    deadbeef-vs:optical-drive    :optical-drive           -
pulseaudio       deadbeef-vs:pulseaudio       :pulseaudio              -
removable-media  deadbeef-vs:removable-media  :**_removable-media         manual_**
unity7           deadbeef-vs:unity7           :unity7                  -
wayland          deadbeef-vs:wayland          :wayland                 -
x11              deadbeef-vs:x11              :x11                     -


             -

```
If you need more information see: [https://askubuntu.com/questions/1034030/how-to-get-access-to-usb-storage-from-an-application-installed-as-snap](https://askubuntu.com/questions/1034030/how-to-get-access-to-usb-storage-from-an-application-installed-as-snap)
> **Leslie Viljoen said:**
> 

Wouldn't it be better if Snap apps asked for their relevant permissions, or at the very least popped up the permissions dialog after install? That would put Ubuntu apps on par with Android apps.
I believe Gnome-Software has this Option

---

### Post by uninvolved on 2022-01-29
I'm a moderator at another sizable Linux forum, so I see a lot of comments - some of them about Snaps.

One kinda legitimate complaint that I see fairly regularly is that they all show up as loop devices, clogging terminal output for commands like 'lsblk'. It'd be nice if there was a way to exclude snaps from that output, or at least remove a few complaints.

---

### Post by TheFu on 2022-01-29
In the snap package world, removable-media means stuff mounted under /media/ or /mnt/, nowhere else.  That is unfortunate.

Linux File System Hierarchy Standards (2015 version; the latest).
[https://refspecs.linuxfoundation.org/FHS_3.0/fhs/index.html](https://refspecs.linuxfoundation.org/FHS_3.0/fhs/index.html)
> 3.11. /media : Mount point for removable media
3.11.1. Purpose

This directory contains subdirectories which are used as mount points for removable media such as floppy disks, cdroms and zip disks.

For /mnt, the standards say:
> 3.12. /mnt : Mount point for a temporarily mounted filesystem
3.12.1. Purpose

This directory is provided so that the system administrator may temporarily mount a filesystem as needed. The content of this directory is a local issue and should not affect the manner in which any program is run.

This directory must not be used by installation programs: a suitable temporary directory not in use by the system must be used instead.

---

### Post by TheFu on 2022-01-29
> **uninvolved said:**
> I'm a moderator at another sizable Linux forum, so I see a lot of comments - some of them about Snaps.

One kinda legitimate complaint that I see fairly regularly is that they all show up as loop devices, clogging terminal output for commands like 'lsblk'. It'd be nice if there was a way to exclude snaps from that output, or at least remove a few complaints.

lsblk has an exclude capability:
```
alias lsblkt='lsblk -e 7 -o name,size,type,fstype,mountpoint'
```
So does df
```
alias dft='df -hT -x squashfs -x tmpfs -x devtmpfs'

```

No need to see the junk from snaps or other "pseudo-file systems" that aren't real storage.

---

### Post by uninvolved on 2022-01-29
> **TheFu said:**
> lsblk has an exclude capability:

Yeah I know why they get listed in lsblk, just that the clutter bugs (some subset of) people. 

Now that I didn't know - about excluding it. I'll definitely be referring to this in the future, as it's sure to come up again, and again, and again.

Thanks!

---

### Post by #&amp;thj^% on 2022-02-01
> **uninvolved said:**
> Yeah I know why they get listed in lsblk, just that the clutter bugs (some subset of) people. 

Now that I didn't know - about excluding it. I'll definitely be referring to this in the future, as it's sure to come up again, and again, and again.

Thanks!
+1 I will as well.
@TheFu Nice informational Addition.

---

### Post by TheFu on 2022-02-01
> **uninvolved said:**
> Yeah I know why they get listed in lsblk, just that the clutter bugs (some subset of) people. 

Now that I didn't know - about excluding it. I'll definitely be referring to this in the future, as it's sure to come up again, and again, and again.

Thanks!

Why would you need to return here?  Just put those lines into your aliases file and include it in your backups. It won't disappear and will always be there for 1 extra character of effort.
I don't go too crazy with aliases - some people have entire functions that feed into other functions in their environment aliases for their shell.  I just have about 20 aliases for commonly needed things.

I even alias ls to be **ls -F** - which shows directories, symbolic links, and executable files. I disable colors, since the dark blue can't be viewed in my terminals. Then there are 4 other aliases based off the ls alias.  du, df, lsblk, lpr, psg, vi, and some for mispellings of PAGERS.  I have a few to quickly cd into about 5 directories that are used all the time for different projects too. Lastly, some programs need to be run inside a sandbox with some options I don't want to need to know, so those get aliases too.  

No need to remember these things. Just put commands with options you use more than a few times into your alias list.

---

### Post by #&amp;thj^% on 2022-02-01
> **TheFu said:**
> Why would you need to return here?  
To give source and credit..:P

---

### Post by TheFu on 2022-02-01
> **1fallen said:**
> To give source and credit..:P

We all "stand on the shoulders of GIANTS" who came before.

---

### Post by iamjiwjr on 2022-02-01
I start out deleting the snaps Firefox and never let any of them darken my doorway afterwards. I delete the snaps directory in my file manager. I install Synaptic, gdebi, and flatpak via the terminal. Then I install Firefox as a deb. After installing the flatpak repo and rebooting, I can install flatpaks via the terminal from the flathub site. Then I can install anything else I need without ever needing to use the Ubuntu software store. Everything works great.

I have found snaps to be quite buggy, crashy, and slow as molasses. Yuck! My opinion is it's a failed experiment on the desktop side. I do read and hear that it works well on the enterprise side and is useful there.

---

### Post by simonsaysthis on 2022-02-02
> **iamjiwjr said:**
> 

I have found snaps to be quite buggy, crashy, and slow as molasses. Yuck! My opinion is it's a failed experiment on the desktop side. I do read and hear that it works well on the enterprise side and is useful there.

Such generalisations help nobody.

Neither snap nor flatpak as a technology are 100% there yet. The experience of an app for any of these technologies depends largely on how they are packaged, maintained and by who.

---

### Post by vanadium on 2022-02-02
> **TheFu said:**
> It won't disappear and will always be there for 1 extra character of effort.
Eliminate the extra character of effort by naming the alias the same as the command:

```

alias lsblk='lsblk -e 7 -o name,size,type,fstype,mountpoint'

```

If at one point, you want to execute the original command rather than the alias, use an extra character as:

```

\lsblk

```

Most annoying for me is the slow cold startup of snaps. The "snap"  folder in the center of the home directory is outright bad design. Now and then, some snap package won' t run. The situation may have improved - it is over half a year that I fully removed snap from my system.

---

### Post by uninvolved on 2022-02-02
> **TheFu said:**
> Why would you need to return here?  Just put those lines into your aliases file and include it in your backups.

Because it won't be for my sake. So, I can just link 'em here to see your post, rather than typing it up all over again. I don't need to add it to my aliases, at a personal level.

Personally, I could not care less about the clutter. It's other people who care - not me. In some cases, it's their only excuse for disliking snaps - or so they say. Your information can help get them over the hurdle. Or, if nothing else, give them one less thing to complain about.

---

### Post by TheFu on 2022-02-02
> **vanadium said:**
> Eliminate the extra character of effort by naming the alias the same as the command:

Yes, this is possible and lots of people do it. Cough, including me.

However, it is often a really bad idea, because aliases don't work in scripts (especially run from crontabs) and it is just so easy to get stuck troubleshooting script issues over something dumb.

But we each have to decide which aliases are safe to over-ride and which would be terrible.  For me, I override 'ls' aliases because I'll never, ever, use those in a script. There are better file globbing methods in every scripting language that what 'ls' does already. Hopefully, everyone scripting has learned **NOT** to use *ls* in any script and has learned the globbing techniques to get a list of files/directories for processing without it.

But most of us are adults here, at least by age.  Sometimes I revert to a 10 yr old myself. ;)  Good times.

---

### Post by #&amp;thj^% on 2022-02-02
> **TheFu said:**
> Yes, this is possible and lots of people do it. Cough, including me.

However, it is often a really bad idea, because aliases don't work in scripts (especially run from crontabs) and it is just so easy to get stuck troubleshooting script issues over something dumb.

But we each have to decide which aliases are safe to over-ride and which would be terrible.  For me, I override 'ls' aliases because I'll never, ever, use those in a script. There are better file globbing methods in every scripting language that what 'ls' does already. Hopefully, everyone scripting has learned **NOT** to use *ls* in any script and has learned the globbing techniques to get a list of files/directories for processing without it.

But most of us are adults here, at least by age. **_ Sometimes I revert to a 10 yr old myself. ;)  Good times._**

Guilty as well....:lolflag:
I have some need of this rarely, 
```
alias lt='ls --human-readable --size -1 -S --classify'
```

---

### Post by TheFu on 2022-02-02
> **1fallen said:**
> Guilty as well....:lolflag:
I have some need of this rarely, 
```
alias lt='ls --human-readable --size -1 -S --classify'
```

Oh, you mean 
```
du -sh * | sort -h
```
or
```
ls -hsSF
```

My 'ls' aliases build on each other, so 
```
alias ls='ls -F'
alias ll='ls -al'
alias lm='ll |more '
alias lrt='ls -rt'
alias ltm='ls -alt| more'

```
Order matters for those aliases.  ls --> ll --> lm

I'm torn between using more and less as the pager.  I like everything about less, except that it wipes the screen when done. More doesn't do that.  Sure, there is **less -X** and I could override less with an alias for that option. ... and I should just make all the more aliases --> less -X (I have aliases for misspellings of more/mreo/mroe and a few others, so I don't have to bother fixing them.  When I'm teaching with my screen on a projector and misspell more, people really want to correct the command before I hit <enter>.  I do it often enough that it just wasn't worth my time - call it autocorrect from the 1990s.

---

