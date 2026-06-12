---
title: "DeVeDe/Brasero Question"
date: 2010-01-05
forum: Ubuntu Studio
---

### Post by watson524 on 2010-01-05
Hi all,

I'm very new to Linux and even moreso to Multimedia stuff on linux - Typically I used Windoze (FAVC and Nero) for what I'm about to describe.

I installed DeVeDe today and the package installed a few extraneous things such as Brasero.

I took an AVI file and ripped it to an ISO (like I would using FAVC on my other computer). Before burning, I went to my Windoze machine (a laptop which I sometimes watch in Bed) and tried to play the ISO using virtual clone drive and try to play it. It says that Windoze can't access the disk and to make sure it's a format that Windoze recognizes. Ok I thought, let me burn it... so I burn it with Brasero and it plays just fine on my Linux Box (Ubuntu Hardy) but when I take that disk and put it in my laptop, no go.... similar message and basically doesn't show any files there (no audio_ts or video_us).

I figured the file format would be universal but perhaps not? Am I expecting too much? I'd like to use the Linux box for authoring and such because it's sitting idle otherwise (it's acting as more of a file server for me right now).

thanks in advance!

---

### Post by alegallo on 2010-01-05
I remember having had the same problem in Hardy.
It was a genisoimage bug, which made a perfectly readable image for linux and any standalone player, but completely useless for win.
Also burning the image did not help.
I remember solving it by installing an older version of genisoimage (I guess it was the gutsy version, but no guarantee: I have karmic installed and can't check anymore).
Try searching for it in the multimedia production forum.

---

### Post by watson524 on 2010-01-05
> **alegallo said:**
> I remember having had the same problem in Hardy.
It was a genisoimage bug, which made a perfectly readable image for linux and any standalone player, but completely useless for win.
Also burning the image did not help.
I remember solving it by installing an older version of genisoimage (I guess it was the gutsy version, but no guarantee: I have karmic installed and can't check anymore).
Try searching for it in the multimedia production forum.

Sorry for the newbie question but what is genisoimage? I'm assuming that's some program that came down with the package that I don't directly see being used but it's used to make the iso?

thanks!

---

### Post by watson524 on 2010-01-05
After reading around some more, it appears a solution is to downgrade to genisoimage 1.1.2 from the Ubuntu repositories but honestly, I haven't a clue how to do that. I've never installed anything other than what came by going to applications -> add/remove.

Can anyone give me some guidance?

thanks!

---

### Post by howefield on 2010-01-05
The earliest version I see for Ubuntu is 1.1.6 from Ubuntu 8.04.

[http://packages.ubuntu.com/hardy/genisoimage](http://packages.ubuntu.com/hardy/genisoimage)

The version you are asking for can be downloaded here, from the Debian repository. Double click the download when finished to start the install. (Ensure you get the right package for your system architecture)

[http://packages.debian.org/etch/genisoimage](http://packages.debian.org/etch/genisoimage)

Hopefully it'll install ok.

---

### Post by watson524 on 2010-01-05
> **howefield said:**
> 

Hopefully it'll install ok.

Sorry to be a pain but.... will it just install over what's there on its own if all goes well? I'd like to not hose my system since I know so little about to fix anything in here at my current stage of learning.

And something else, how do I know what architecture to download? I have an AMD Hammer Family processor according to "sudo lshw".

---

### Post by howefield on 2010-01-05
> **watson524 said:**
> ... will it just install over what's there on its own if all goes well?

I would uninstall the version that you have, you can do that from Synaptic Package Manager. Choose the "mark for complete removal" option.

---

### Post by howefield on 2010-01-05
> **watson524 said:**
> And something else, how do I know what architecture to download? I have an AMD Hammer Family processor according to "sudo lshw".

Are you running 32 bit Ubuntu edition or 64 bit ?

amd64 link for 64 bit.
i386 for 32 bit.

If you are not sure which, you are likely running 32 bit, but to make sure, type the following in a terminal 

```
uname -m
```

---

### Post by watson524 on 2010-01-05
> **howefield said:**
> Are you running 32 bit Ubuntu edition or 64 bit ?

amd64 link for 64 bit.
i386 for 32 bit.

If you are not sure which, you are likely running 32 bit, but to make sure, type the following in a terminal 

```
uname -m
```

64 Bit so I guess that answers that.

```
michele@michele-linux:~$ uname -m
x86_64
michele@michele-linux:~$
```

---

### Post by watson524 on 2010-01-05
Ok before I go applying the mark for complete removal, it says it's also going to remove brasero, devede, dvd+rw tools, nautilus-cd-burner, and ubuntu-desktop (the last one worries me).

that being said, when I install the lower version, will it put all those back? Or would I have to find them and install them one by one. Devede I just installed today and I'm wondering if the rest came with it and I didn't notice.

thanks!

---

### Post by alegallo on 2010-01-06
You will have to install them back, but I can remember that I used a different system.
If I am not wrong, I added the Gutsy repos to my Synaptic sources list, then I forced the install of the old version, informing Synaptic that it should not try to update it to a newer one.
If you uninstall the Hardy version and update it with another one the system may try to restore the Hardy version, or so I think.

Sorry, but I can't check how I did it, but I am sure that there were some posts of mine, either here in the international forums or maybe in the Italian one ... 
Are you by chance Italian? 
Mica sei italiano, per caso?

---

### Post by watson524 on 2010-01-06
> **alegallo said:**
> You will have to install them back, but I can remember that I used a different system.
If I am not wrong, I added the Gutsy repos to my Synaptic sources list, then I forced the install of the old version, informing Synaptic that it should not try to update it to a newer one.
If you uninstall the Hardy version and update it with another one the system may try to restore the Hardy version, or so I think.

Sorry, but I can't check how I did it, but I am sure that there were some posts of mine, either here in the international forums or maybe in the Italian one ... 
Are you by chance Italian? 
Mica sei italiano, per caso?

I had been reading this thread ([http://ubuntuforums.org/showthread.php?t=787299&page=4](http://ubuntuforums.org/showthread.php?t=787299&page=4)) where you talked about the fix and trying to follow it but this is all pretty fuzzy to me so I'm not sure if I'm brave enough to try or just keep using the Windoze box to make the iso.

I don't know how to add repositories and force it to not upgrade etc etc or where to get the other softwares though I might scan the list and see if they're on it before I toast them thinking they'd show up as uninstalled after.

And nope, not Italian. I'm in the northeast part of the US in the state of Pennsylvania.

---

### Post by alegallo on 2010-01-06
Yes, you're right, it is exactly what I meant ;)
Well, I'm a noob too, so if I did it you can do it too, it's really not that hard.

I thought you might be Italian because I saw "michele" in your terminal ... ;)

---

### Post by watson524 on 2010-01-06
Nope, Michele is my first name :-) My parents spelled it with just the one L vs the normal 2 Ls

I'm hoping to research some things tonite before I go uninstalling anything.....

---

### Post by alegallo on 2010-01-06
Oh, so I guess you are a lady! 
Well, in Italy Michele (1 L) is a male name (Michael), used quite a lot, especially in the south ;)

But don't worry about installing the gutsy version, it's really easy.
I think I saw a very good guide in the wiki, but again I don't remember if it was the Italian or the international one.

I will have to play with my 3 1/2 years old son this evening (he's quite excited about his presents, today it's a holiday in Italy), but I'll try to find something ;)

Try in the community guides, in "synaptic" or in "repositories"

---

### Post by watson524 on 2010-01-06
> **alegallo said:**
> Oh, so I guess you are a lady! 
Well, in Italy Michele (1 L) is a male name (Michael), used quite a lot, especially in the south ;)
Yep, if I was a boy they were going to name me Michael. I was almost "Molly" but my dad talked my mom out of it.

> **alegallo said:**
> 
I will have to play with my 3 1/2 years old son this evening (he's quite excited about his presents, today it's a holiday in Italy), 

Ahhh... Happy Epiphany! Some of my friends celebrate that as their Christmas because they are Catholic, but not Roman Catholic. We always make sure our Christmas decorations stay up until at least the Epiphany out of respect for our friends.

---

### Post by watson524 on 2010-01-06
I added the gutsy repository using the info at the link [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources) but but gutsy in the link where they have karmic and restarted synaptic and all, but I don't see a lower version of genisoimage on the list anywhere. I see my version in the installed and all list but nothing else...... Would it be taken out of a repository? Or maybe there's a way to see which software is coming from a certain repos? I thought maybe in origin or custom filters but I can't seem to find anything.

---

### Post by alegallo on 2010-01-06
Thanks for the Happy Epiphany, nowadays it's more a day for children, but what's important for us parents is that the Christmas holidays end today :(
Luckily I still have a couple of free days till Monday ;)

hmm, so, let me think ...

well, you should have added the following line to the repos, right? 
[FONT="Courier New"]
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free[/FONT]

Now, search for genisoimage in synaptic, and in the "Version" tab you should see both the hardy and gutsy ones.

I think I did actually remove the old genisoimage (and, I am afraid, whatever goes with it), and reinstalled it all forcing the old version of genisoimage from the "Package" menu in Synaptic.

From the same menu you should also check "Lock Version" for the same package, otherwise your system will always try to reinstall the newest one.

After doing it all you should be OK, or so I hope! ;)

Maybe you could also try to install the intrepid version, or even the jaunty or karmic one, but I am too noob to guess if it could be done!

I'd love to get expert hint, if any should stumble upon this thread ;)

---

### Post by watson524 on 2010-01-06
> **alegallo said:**
> 
well, you should have added the following line to the repos, right? 
[FONT="Courier New"]
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free[/FONT]
Yep that's what I put in on the 3rd party tab (because I couldn't see anywhere else to put it) in settings -> repositories. And then I got the key issue sorted and all that and it said updating and such....

> **alegallo said:**
> 
Now, search for genisoimage in synaptic, and in the "Version" tab you should see both the hardy and gutsy ones. 
And that's where it's a no go. I go to search at the top, but in genisoimage and leave "look in" at name. It finds one (currently installed). Then I go to package -> properties and on the versions tab, it just lists the Hardy one. It says at the bottom to install a version different from the default one, chose package -> force version from the menu but that's grayed out.

---

### Post by alegallo on 2010-01-07
If synaptic asked you to update and refresh, it should all be OK

Now you could try to check with a different package, whatever it may be, it's enough NOT to have it already, to see if the two versions are proposed.
If you check a package for installation, synaptic will try to use hardy's version, so you will have to force the gutsy one in the menu.

> ... that's grayed out.

Yes, it's grayed out because you already have it installed.
Uninstalling the Hardy version should allow you to install the gutsy one.

But please check before doing major changes to your system, y'know, just out of security ;)

---

### Post by alegallo on 2010-01-09
watson, I found a way to do it ;)
This should be the way I used for my system, I found it back in the Italian forum.

Locking a package version can be done by editing the file /etc/apt/preferences. 
If the file does not exist you will have to create it.

Add one extra section, separated by a blank line, which should be like this:

Package: <package name>
Pin: <pin definition>

In this case it should be:

Package: genisoimage
Pin: 1.1.6-1ubuntu3

I found this solution in the Debian how-to, suggested by a hero member of the Italian forum, and worked perfectly for me.
The only thing was that, in my system, ManDVD and k3b were uninstalled, but I reinstalled them.

I hope it solves your issue ;)

---

