---
title: "nautilus new behavior"
date: 2012-06-11
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ronacc on 2012-06-11
What happened to nautilus ? I have a 6 drive box with many partitions . Only / and /home are mounted by fstab anything else I mount as needed by clicking on the partition in the nautilus sidebar as user . In a root nautilus the partitions would not show unless previously mounted by user . in precise and before I then could access the drives from a root nautilus or root gedit , this is no longer so , is this intentional or a bug ? IF this is intentional and cannot be circumvented it renders Ubuntu totally useless to me .

---

### Post by mc4man on 2012-06-11
I think this happened a bit ago, pre A1?. Not too sure it's nautilus per se, I remember booting to a live session, downgrading nautilus to precise's version & still saw the same.

It's actually a bit worse here - no internal/external drives ever show in a root nautilus browser, stopped doing so when gvfs updated & media started mounting in /run
(maybe the never show with current gvfs is a local condition, wouldn't know here till a fresh install

Not sure if intentional or just some current state, with no easily reviewed changelogs never know what's doing what

---

### Post by ronacc on 2012-06-11
it looks like it came from upstream , my debian sid install (installed yesterday) acts the same way . This is disheartening . I first noticed it early on and just thought it would clear up with updates . I really needed it today which is what prompted the post .

---

### Post by jerrylamos on 2012-06-12
A couple of times during quantal pre-Alpha 1 I've gotten so frustrated with Nautilus I installed Pcmanfm.  That's wierd, Pcmanfm must have a zillion bug reports, but at the time was running better than Nautilus.

Anyone have any idea why the difficulty of "fixing" Nautilus?

Thanks, Jerry

---

### Post by balloons on 2012-06-12
> **jerrylamos said:**
> A couple of times during quantal pre-Alpha 1 I've gotten so frustrated with Nautilus I installed Pcmanfm.  That's wierd, Pcmanfm must have a zillion bug reports, but at the time was running better than Nautilus.

Anyone have any idea why the difficulty of "fixing" Nautilus?

Thanks, Jerry

You remember how long tabs in nautilus took right? Presumably it was (or is) a crufty codebase that had a steep learning curve and required you to know C. Hence, the lack of developers willing to invest in it. (To be clear, I've no direct knowledge on this; it was the explanation offered to me) I don't know where it stands now given the gtk3 and gnome3 changes. On this issue, I'm wondering why you need to run a root nautilus and root gedit?

---

### Post by sgage on 2012-06-12
> **guitara said:**
> You remember how long tabs in nautilus took right? Presumably it was (or is) a crufty codebase that had a steep learning curve and required you to know C. Hence, the lack of developers willing to invest in it. (To be clear, I've no direct knowledge on this; it was the explanation offered to me) I don't know where it stands now given the gtk3 and gnome3 changes. On this issue, I'm wondering why you need to run a root nautilus and root gedit?

For any file management I do as root that "needs" a GUI, I use Filerunner, just as I have been since the 90's  :KS

---

### Post by MG&amp;TL on 2012-06-12
> **guitara said:**
> ...Presumably it was (or is) a crufty codebase that had a steep learning curve and required you to know C. Hence, the lack of developers willing to invest in it. (To be clear, I've no direct knowledge on this; it was the explanation offered to me)

In defence of Gnome, their code is usually a shining example of clarity and efficiency. I think nautilus is probably unloved because it's not as glamorous or interesting as, say, Shell, or gnome-games.  

And a *lot* of devs know C. ;) 

Just in defence of Gnome, not a bite at you. :)

---

### Post by sgage on 2012-06-12
> **MG&TL said:**
> In defence of Gnome, their code is usually a shining example of clarity and efficiency. I think nautilus is probably unloved because it's not as glamorous or interesting as, say, Shell, or gnome-games.  

And a *lot* of devs know C. ;) 

Just in defence of Gnome, not a bite at you. :)

Didn't nautilus come out of the Helix project? (Not the Real media Helix project, but some outfit that was going to make Linux great - I think they had some ex-Apple folks.) I remember a lot of hype about it, how it was going to be some sort of unique innovative approach to file management.

That's getting to be a long time ago...

---

### Post by philinux on 2012-06-12
> **ronacc said:**
> What happened to nautilus ? I have a 6 drive box with many partitions . Only / and /home are mounted by fstab anything else I mount as needed by clicking on the partition in the nautilus sidebar as user . In a root nautilus the partitions would not show unless previously mounted by user . in precise and before I then could access the drives from a root nautilus or root gedit , this is no longer so , is this intentional or a bug ? IF this is intentional and cannot be circumvented it renders Ubuntu totally useless to me .

Yep. In precise my second internal hard drive root partition gets mounted in /media and shows up as it's uuid I think.

In quantal nothing in /media at all via gksu nautilus.

---

### Post by Morbius1 on 2012-06-12
> **guitara said:**
> On this issue, I'm wondering why you need to run a root nautilus and root gedit?
Especially since Gnome Central Command forbids it:

A selected quote from the following bug report: [https://bugs.launchpad.net/ubuntu/+s...it/+bug/838404]("https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/838404")

                                                      > [Sam_ (and-sam)]("https://launchpad.net/%7Eand-sam")             wrote             on 2011-10-09:                                                            [ #2]("https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/838404/comments/2")                                                               Quote comment from upstream developer:
< You shouldn't start GNOME programmes with elevated privileges, it's not
supported. In any case, not a gnome-terminal bug. >

              
                                                                                                                                      [Sean Fitzpatrick (sean-fitzpatrick)]("https://launchpad.net/%7Esean-fitzpatrick")             wrote             on 2011-10-09:                                                            [ #3]("https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/838404/comments/3")                                   
                            I see.  So does  that make the official  GNOME position "editing system files should be  done with nano or  similar" or "system files?  why would a user want to  edit a system  file?"

              
     
                                                                                                                                [Sam_ (and-sam)]("https://launchpad.net/%7Eand-sam")             wrote             on 2011-10-09:                                                            [ #4]("https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/838404/comments/4")                                   
                            Yep, from my understanding they don't agree with running graphical apps as root. [Bug #805682]("https://bugs.launchpad.net/bugs/805682")

              


---

### Post by ronacc on 2012-06-12
> **guitara said:**
>  On this issue, I'm wondering why you need to run a root nautilus and root gedit?

I have a multi disk , multi partition , multi distro test box and sometimes need to do some filemanagement / editing as root on a different install . It is much more convenient to be able to get in to a crippled install from a working one and do what I need to do . That is the main reason , a lesser reason but even more important to me is that I have a very low tolerance for " I'm sorry Dave ,I can't do that ." I know the opinions about running as root I'm a big boy it's my box and I can take responsibility for my own actions I don't need a nanny OS telling me "no no you might burn yourself".

---

### Post by balloons on 2012-06-12
> **MG&TL said:**
> In defence of Gnome, their code is usually a shining example of clarity and efficiency. I think nautilus is probably unloved because it's not as glamorous or interesting as, say, Shell, or gnome-games.  

And a *lot* of devs know C. ;) 

Just in defence of Gnome, not a bite at you. :)

Yep, I'll gladly stand corrected (I hope the codebase is elegant :-) )-- your explanation also makes sense. Specifically to my tabs example, at the time, gnome devs were unsure how to best create tabs without confusing the user, so they didn't add the feature until it become so pervasive they worried less about confusion of implementation. If I remember correctly, at one point the default nautilus behavior was to always open a new window when you clicked a folder.. those were the days...

---

### Post by balloons on 2012-06-12
> **ronacc said:**
> I have a multi disk , multi partition , multi distro test box and sometimes need to do some filemanagement / editing as root on a different install . It is much more convenient to be able to get in to a crippled install from a working one and do what I need to do . That is the main reason , a lesser reason but even more important to me is that I have a very low tolerance for " I'm sorry Dave ,I can't do that ." I know the opinions about running as root I'm a big boy it's my box and I can take responsibility for my own actions I don't need a nanny OS telling me "no no you might burn yourself".

Looking at the bug report linked to on nautilus root access, it does make me a bit sad to see this as unsupported by design :-(

---

### Post by philinux on 2012-06-12
> **guitara said:**
> Looking at the bug report linked to on nautilus root access, it does make me a bit sad to see this as unsupported by design :-(


Time for a new file manager maybe. What are the alternatives?

And as for nano to edit system files well that is a bit bare metal to me. I've never had an issue with gksu gedit.

---

### Post by ronacc on 2012-06-12
> **philinux said:**
> Time for a new file manager maybe. What are the alternatives?

And as for nano to edit system files well that is a bit bare metal to me. I've never had an issue with gksu gedit.

the file requestor in gedit acts the same way as nautilus , it don't see drives that aren't mounted by fstab . so any files on those drives can't be reached by a root gedit .

---

### Post by sgage on 2012-06-12
> **philinux said:**
> Time for a new file manager maybe. What are the alternatives?

And as for nano to edit system files well that is a bit bare metal to me. I've never had an issue with gksu gedit.

Like I said, I've used Filerunner since forever, though it seems no longer to be in the repos (it was through Oneiric). It was no problem to google up a deb package for it, though. EmelFM2 is also a good one, in the repos.

---

### Post by mc4man on 2012-06-12
> **ronacc said:**
>  In a root nautilus the partitions would not show unless previously mounted by user . in precise and before **I then could** access the drives  .

I never use gksu nautilus or gksu gedit <no specified file> too much so mis-read/understood your post & mistakenly assumed that you could find/mount volumes from your root window. (obviously not

This current change is from the recent upgrade of .gvfs to monitor udisks2 instead of udisks.

Some you could, at least for a while, downgrade gvfs to last version that used udisks. Volumes will be mounted in /media & accessible from your root gui's
(whether any unintended consequences don't know

Also no reason not to file a bug against any or all of the involved, can't hurt, it's not like a root browser or gedit isn't allowed to browse to /run/media/username/<whatever> & do anything you want.

packages to downgrade if desired on 64 bit

gvfs_1.13.0-0ubuntu1_amd64.deb 
gvfs-common_1.13.0-0ubuntu1_all.deb
gvfs-libs_1.13.0-0ubuntu1_amd64.deb
gvfs-backends_1.13.0-0ubuntu1_amd64.deb 
gvfs-daemons_1.13.0-0ubuntu1_amd64.deb 
gvfs-bin_1.13.0-0ubuntu1_amd64.deb
gvfs-fuse_1.13.0-0ubuntu1_amd64.deb

---

### Post by ronacc on 2012-06-12
thanks for the info ,  I'll keep things as they are at least until release , I don't like to mess with default files during testing ( although I'll add the kitchen sink and the drain pipes too ):p

---

### Post by mc4man on 2012-06-12
> **ronacc said:**
> thanks for the info ,  I'll keep things as they are at least until release
Same here or I'll keep 2 installs, 1 straight up, one not so to keep up with mods I know I want & or the inevitable bugs with fixes that don't get fixed in a timely fashion. 
As far as the new /run/ don't have any issue with, hasn't affected anything as far as access, & for root business tend to use the context menu options anyway.

( the new gvfs/udisks2 has this annoying deal with logging out/in with mounted media in Unity, doubles up the icons,  but that's not affecting your GS.

---

### Post by ronacc on 2012-06-12
like you I normally keep 2 sometimes 3 installs , right now I'm on my upgraded precise I had an install of the very first daily but when I went to overwrite it the installer crashed and has been doing it since , eventually they'll get it fixed .

---

