---
title: "Kernel 3.6.1"
date: 2012-10-07
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by VinDSL on 2012-10-07
The Linux 3.6.1 mainline kernel is out now.

Works exceptionally well in GS!  Will try Unity, next ...  ;)


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-7-oct-2012-2(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-7-oct-2012-2.png")[/INDENT]

---

### Post by sonnet on 2012-10-07
> **VinDSL said:**
> The Linux 3.6.1 mainline kernel is out now.

Works exceptionally well in GS!  Will try Unity, next ...  ;)


what do you mean exactly?
are you implying it works better than 3.5? If that's the case, would you specify which improvements did you notice?

---

### Post by VinDSL on 2012-10-07
> **sonnet said:**
> what do you mean exactly?
are you implying it works better than 3.5?
I upgraded from 3.6.0 --> 3.6.1

You never know what you'll get with mainline kernels, and I've only been running this for an hour and a half.  However, my immediate impression is positive.  This machine is acting V sprightly on 3.6.1.

I digress: Dailys are a real crapshoot.  I quit installing them, a long time ago.  I don't know why I'm telling you this, but it's yours for free.  On topic...

Linux 3.6.0 was pulling-in part of Plymouth, which is always irritating... watching boot messages pop-up all over a faded, low-res purple screen.  Plymouth is black @ boot, with 3.6.1, and black is beautiful, as they say.

I would swear that the display is sharper and faster now, although this is probably a placebo affect at play. I haven't cleaned my eyeglasses since last night, so that isn't a factor.

Guayadeque was flash crashing on me, with 3.6.0.  Boom!  Gone!  Hasn't happened yet with 3.6.1.  Maybe, I'll try some Dubstep.

Hate to say it but, GS is running circles around Unity.  Sometimes it takes apps so long to load in Unity, that I *think* I didn't click them.  So, I click them again, and again, and finally 2-3 instances pop-up.  Or, I try to scroll a window in a browser, and it just sits there.

Basically, 3.6.1 *feels* faster, and more responsive than 3.6.0, and that's a good thing.  But, GS now *feels* faster than Unity, which is a bad thing.  LoL!  :D

Anyway, give it a try, and see what you think.  You can always go back to <whatever> kernel at the GRUB menu. ;)

---

### Post by geolab on 2012-10-08
How did you install it ?

---

### Post by sonnet on 2012-10-08
> **VinDSL said:**
> I upgraded from 3.6.0 --> 3.6.1

You never know what you'll get with mainline kernels, and I've only been running this for an hour and a half.  However, my immediate impression is positive.  This machine is acting V sprightly on 3.6.1.

I digress: Dailys are a real crapshoot.  I quit installing them, a long time ago.  I don't know why I'm telling you this, but it's yours for free.  On topic...

Linux 3.6.0 was pulling-in part of Plymouth, which is always irritating... watching boot messages pop-up all over a faded, low-res purple screen.  Plymouth is black @ boot, with 3.6.1, and black is beautiful, as they say.

I would swear that the display is sharper and faster now, although this is probably a placebo affect at play. I haven't cleaned my eyeglasses since last night, so that isn't a factor.

Guayadeque was flash crashing on me, with 3.6.0.  Boom!  Gone!  Hasn't happened yet with 3.6.1.  Maybe, I'll try some Dubstep.

Hate to say it but, GS is running circles around Unity.  Sometimes it takes apps so long to load in Unity, that I *think* I didn't click them.  So, I click them again, and again, and finally 2-3 instances pop-up.  Or, I try to scroll a window in a browser, and it just sits there.

Basically, 3.6.1 *feels* faster, and more responsive than 3.6.0, and that's a good thing.  But, GS now *feels* faster than Unity, which is a bad thing.  LoL!  :D

Anyway, give it a try, and see what you think.  You can always go back to <whatever> kernel at the GRUB menu. ;)
Thanks for your detailed reply.
I'm currently  on 3.5 (kubuntu) and your comment made me very curious.
Actually this latest kubuntu build which I have installed, is going extremely well.
Finally a *buntu distro boots up in 10-15 seconds on my pc as it should have done already in the past.
So I want to keep this configuration for now, for better testing. But surely I'll try the 3.6.x for 2-3 days, before going for the final installation.
I'm just waiting to see a non-beta fgrlx for the distro (along with the Libreoffice issues, which I think will be solved very shortly), see that there are no problem and then install.

---

### Post by lucazade on 2012-10-08
I'm still wondering what is the correlation between a kernel (3.6 in this case) and a desktop environment (gshell or unity).

They do not talk to each other neither share any resources.

btw nice setup VinDSL ;)

---

### Post by VinDSL on 2012-10-08
> **lucazade said:**
> I'm still wondering what is the correlation between a kernel (3.6 in this case) and a desktop environment (gshell or unity).

They do not talk to each other neither share any resources.

btw nice setup VinDSL ;)
Thanks, lucazade!  ;)

I don't really understand the correlation either, nor why one kernel works better or worse than another.

Why does Plymouth (somewhat) work with one mainline kernel, but not the next?  I've never seen Plymouth fully work on any of them.

Maybe it has something to do with the way they were compiled, e.g. built.  Who knows?!?!?

I've been running GS all day (and all night).  I guess I should go try Unity...

---

### Post by dino99 on 2012-10-08
hey, 3.6.1 is a bug fix release, explaining better experience :p

and i'm surprised it only use 260 Mib ram with gnome-classic, thats very low :p

---

### Post by VinDSL on 2012-10-08
> **geolab said:**
> How did you install it ?
I just use a "shotgun" approach.  It's very simple...

Using Linux 3.6.1 as an example:

[LIST]
[*]Download the binaries from:
 [INDENT][http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.1-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.1-quantal/)[/INDENT]

(In my case, I downloaded the 3 files ending in **[COLOR="DarkRed"]_i386.deb[/COLOR]** & the 1 file ending in **[COLOR="DarkRed"]_all.deb[/COLOR]**, e.g. 4 files total.)


[*]Place these 4 .deb files in a folder, all by themselves.
[*]Open a terminal (command line interface [aka CLI]).
[*]Navigate (change directory) to the folder containing the 4 files.
[*]Install them using "dpkg".  I simply use:  **[COLOR="DarkRed"]sudo dpkg -i *.deb[/COLOR]**
[*]If all goes well (and it usually does)... reboot.
[*]If all does not go well, fix the problem(s) before rebooting.
[/LIST]

---

### Post by sonnet on 2012-10-08
> **dino99 said:**
> hey, 3.6.1 is a bug fix release, explaining better experience :p

and i'm surprised it only use 260 Mib ram with gnome-classic, thats very low :p

Did you install gnome-shell/classic on top of a command line installation, or are you running it on top of the desktop (with all unity..) installation?
It should make a substantial difference

---

### Post by dino99 on 2012-10-08
> **sonnet said:**
> Did you install gnome-shell/classic on top of a command line installation, or are you running it on top of the desktop (with all unity..) installation?
It should make a substantial difference

gnome-classic is my default choice

---

### Post by pqwoerituytrueiwoq on 2012-10-08
> **VinDSL said:**
> I just use a "shotgun" approach.  It's very simple...

Using Linux 3.6.1 as an example:

[LIST]
[*]Download the binaries from:[INDENT][http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.1-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.1-quantal/)[/INDENT](In my case, I downloaded the 3 files ending in **[COLOR=DarkRed]_i386.deb[/COLOR]** & the 1 file ending in **[COLOR=DarkRed]_all.deb[/COLOR]**, e.g. 4 files total.)
[*]Place these 4 .deb files in a folder, all by themselves.
[*]Open a terminal (command line interface [aka CLI]).
[*]Navigate (change directory) to the folder containing the 4 files.
[*]Install them using "dpkg".  I simply use:  **[COLOR=DarkRed]sudo dpkg -i *.deb[/COLOR]**
[*]If all goes well (and it usually does)... reboot.
[*]If all does not go well, fix the problem(s) before rebooting.
[/LIST]

how do you find out about security updates/patches
i made a script to install it :)
```
#!/bin/bash

WHERE="http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.1-quantal"
VER_A="3.6.1-030601"
VER_B="201210071322"

mkdir /tmp/kernel-$VER_A
cd /tmp/kernel-$VER_A
if [ "`uname -m`" == "x86_64" ];then
    arch="amd64"
else
    arch="i386"
fi
wget $WHERE/linux-{image-extra,headers,image}-$VER_A-generic_$VER_A."$VER_B"_$arch.deb
wget $WHERE/linux-headers-$VER_A."$VER_B"_all.deb
if [ `ls linux-*.deb | wc -l` -lt 4 ];then
    echo "Failed to download all needed files"
    exit
fi
sudo dpkg -i ./linux-*.deb
```

---

### Post by pqwoerituytrueiwoq on 2012-10-08
> **dino99 said:**
> hey, 3.6.1 is a bug fix release, explaining better experience :p

and i'm surprised it only use 260 Mib ram with gnome-classic, thats very low :p
as in the entire system as soon as you login?
i am using almost 490 on xfce (using 64bit with 4gb ram 300mb shared with gpu)
also using nvidia drivers

---

### Post by VinDSL on 2012-10-08
> **dino99 said:**
> hey, 3.6.1 is a bug fix release, explaining better experience :p

and i'm surprised it only use 260 Mib ram with gnome-classic, thats very low :p
Aha!  Bug fix, eh?  That explains it.

I read, somewhere, that everyone MUST update 3.6.0 --> 3.6.1

I assumed it was a security patch, because of the ARM stuff that they added.

Anyway, it is what it is.  It works better or worse, and that's all that matters to me.  :)

> **sonnet said:**
> Did you install gnome-shell/classic on top of a command line installation, or are you running it on top of the desktop (with all unity..) installation?
It should make a substantial difference
I always start with a normal Ubu dev release, then add the GS and LXDE DEs to the mix.  Then, it's off to the races...

I've played around with other DEs, but those are the ones I prefer on Ubuntu installs (Unity, GS, LXDE).

> **pqwoerituytrueiwoq said:**
> as in the entire system as soon as you login?

i am using almost 490 on xfce (using 64bit with 4gb ram 300mb shared with gpu) also using nvidia drivers
We're talking apples n' oranges, I suppose -- gnome-classic vs gnome-shell vs xfce, but...

GS, on top of kernel 3.6.1 has been very stingy on resources (depending on what you're doing, of course).

Here's an htop screenie, from a few minutes ago...


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-8-oct-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-8-oct-2012-1.png")[/INDENT]


They say, a picture is worth 1000 words, but this requires a note of explanation. ;)

I started my PC an hour ago.  After logging into GS, I played a flash game on Facebook that's horribly resource-intensive.  It uses all of my CPU, all of my RAM, and most of my SWAP. Flash and/or my browser occasionally run out of memory, requiring a screen refresh.  For the most part, it brings this machine to its knees!

After I logged out of Facebook, I came over here, read this thread, and took the screenshot.  So, there is no doctoring-up of the results.  I didn't just login to the desktop.  And, this PC just went through an epic battle with the meanest, nastiest, flash game known to mankind.  LoL!

Check it out.  Everything recovered nicely...

All I care about is resident memory and CPU usage.  

Sitting (basically) idle @ my desktop, with htop running in a terminal, GS has simmered down single-digit CPU usage, and it's consuming only 249 MiB of resident RAM.

I still haven't logged into Unity yet, since installing 3.6.1.  This is just too enjoyable...  :)

---

### Post by mcellius on 2012-10-08
I followed VinDSL's instructions for installing the 3.6.1 kernel on QQ.  So far I had stuck with the kernels provided in the QQ updates and was satisfied with testing those.  But I was intrigued by what VinDSL reported about improved performance so I decided to give it a shot.

I'm using Unity and VinDSL is using Gnome, but I have to say that Unity has been noticeably snappier on my system.  It was noticeable immediately with the first window I opened (Teminal) and so far has continued with everything else I've opened.  I'm very impressed.  It is a very definite improvement, at least so far.

---

### Post by paul_in_london on 2012-10-12
3.6.2 is out:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.2-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.2-quantal/)

---

### Post by pqwoerituytrueiwoq on 2012-10-12
thanks for the notice :)
*installs & attaches installer*

---

### Post by Starks on 2012-10-12
I roll my own.

Linux gensokyo 3.6.0-rc4-prime-pm #1 SMP Tue Sep 11 14:51:44 EDT 2012 x86_64 x86_64 x86_64 GNU/Linux

Based on Airlie's branches.

---

### Post by PaulW2U on 2012-10-13
> **paul_in_london said:**
> 3.6.2 is out:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.2-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.2-quantal/)

Thanks.

Downloaded, installed, rebooted. Everything has been running fine for the last ten hours or so.

Does this mean I'm already testing 13.04? :grin:

---

### Post by VinDSL on 2012-10-13
> **PaulW2U said:**
> Thanks.

Downloaded, installed, rebooted. Everything has been running fine for the last ten hours or so.

Does this mean I'm already testing 13.04? :grin:
Heh!  I really *think* Linux 3.6 et al. should have been included in 12.10.  It's stable enough, IMO, but...

It's like watching a duck, sitting  on water.

Everything looks calm on the surface, but there's a lot going on underneath, you know?

But, yes, you're ready for 13.04, I'm sure.  I know I am.  ;)

How many more days now? =< 2 weeks, if I remember correctly...

---

### Post by AK44 on 2012-10-14
Hoping someone here can help me. I get the following error when trying to udpate to 3.6.x. Any ideas of how to fix? 

make[2]: *** [/var/lib/dkms/virtualbox-guest/4.1.18/build/vboxvideo/vboxvideo_drm.o] Error 1
make[1]: *** [/var/lib/dkms/virtualbox-guest/4.1.18/build/vboxvideo] Error 2
make: *** [_module_/var/lib/dkms/virtualbox-guest/4.1.18/build] Error 2

---

### Post by pqwoerituytrueiwoq on 2012-10-14
you probably did not install all 4 packages
there is a script in this post
[http://ubuntuforums.org/showpost.php?p=12292826&postcount=17](http://ubuntuforums.org/showpost.php?p=12292826&postcount=17)

---

### Post by AK44 on 2012-10-14
> **pqwoerituytrueiwoq said:**
> you probably did not install all 4 packages
there is a script in this post
[http://ubuntuforums.org/showpost.php?p=12292826&postcount=17](http://ubuntuforums.org/showpost.php?p=12292826&postcount=17)

If you were replying to me, yes all 4 were installed.

---

### Post by rtalcott on 2012-10-14
Linux 3.7-rc1 is out.

---

### Post by Miykel on 2012-10-14
Just installed 3.6.2......bootiful.....
Regards Miykel

---

### Post by pqwoerituytrueiwoq on 2012-10-14
I made a update checker script, i wrote it in php, as i know it better than bash so you will need php5-cli and notify-osd to run it
```
sudo apt-get install php5-cli notify-osd
```this script will make a bash update script
you can run it from a script like this
```
#!/bin/bash
updateChecker.php > /tmp/kernel-update
chmod +x /tmp/kernel-update
if [ `cat /tmp/kernel-update | wc -l` -gt 3 ];then
   notify-send "To Upgrade" "Run this in a terminal:\n/tmp/kernel-update"
fi
```EDIT:
added new version of script in attachments section, this version handles missing deb files better (now it will generate the script correctly if the all.deb is missing)
it also supports a argument "-no-rc" this makes it ignore release candidate kernel versions
edit:
here is a self installing copy (it will use -no-rc by default)
[http://ubuntuforums.org/attachment.php?attachmentid=225636&d=1350414482](http://ubuntuforums.org/attachment.php?attachmentid=225636&d=1350414482)

---

### Post by pqwoerituytrueiwoq on 2012-10-14
> **AK44 said:**
> If you were replying to me, yes all 4 were installed.
I was and i am running 12.10 with linux 3.6.2 and nvidia 304.51 and my virtualbox is working just fine
i installed it with the script i posted which is based on VinDSL's instructions

---

### Post by AK44 on 2012-10-14
> **pqwoerituytrueiwoq said:**
> I was and i am running 12.10 with linux 3.6.2 and nvidia 304.51 and my virtualbox is working just fine
i installed it with the script i posted which is based on VinDSL's instructions

Ok. I am still unclear how that helps my error though? As I said, all 4 pieces were included. This error occurs on any 3.6 based kernels.

---

### Post by AK44 on 2012-10-15
Hmm well I decided to say 'what the hell' and rebooted after the error anyway, and it boots fine so I guess that error isn't a big deal. Still curious to know how to fix it but oh well. Thanks for anyone's time anyway.

---

### Post by pqwoerituytrueiwoq on 2012-10-15
> **AK44 said:**
> Hmm well I decided to say 'what the hell' and rebooted after the error anyway, and it boots fine so I guess that error isn't a big deal. Still curious to know how to fix it but oh well. Thanks for anyone's time anyway.
i have seen this error before on my 10.04 when trying to use natty's kernel
it makes virtualbox not work

---

### Post by zika on 2012-10-15
> **rtalcott said:**
> Linux 3.7-rc1 is out.Waiting for mainline ...

---

### Post by rtalcott on 2012-10-15
I am too...I think I am hooked on new kernels!

---

### Post by zika on 2012-10-15
> **rtalcott said:**
> I am too...I think I am hooked on new kernels!Tell me about it... For a week or so daily is not complete so...
To lazy to compile myself. Or, better, afraid that addiction would escalate...

---

### Post by lohengrin1870 on 2012-10-16
> **rtalcott said:**
> Linux 3.7-rc1 is out.
hello, where the kernel is? I didn't see here : [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) , thx

---

### Post by VinDSL on 2012-10-16
> **lohengrin1870 said:**
> hello, where the kernel is? I didn't see here : [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) , thx
Linux 3.7-rc1 is available here: [http://news.softpedia.com/news/Linux-Kernel-3-7-RC1-Brings-Full-ARM-Support-Download-Now-299280.shtml](http://news.softpedia.com/news/Linux-Kernel-3-7-RC1-Brings-Full-ARM-Support-Download-Now-299280.shtml)

But, you're going to have to compile it yourself, patch it, or whatever.

I'm with zika.  I'll wait for it to hit the mainline kernel PPA. ;)

---

### Post by zika on 2012-10-16
> **VinDSL said:**
> I'm with zika.  I'll wait for it to hit the mainline kernel PPA. ;)Nail-biting... ;)

---

### Post by rtalcott on 2012-10-16
3.6 would not work on 12.04 for me...anyone have any luck?

I like to keep a couple machines very stable.

---

### Post by JMB74 on 2012-10-16
3.7 RC1

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc1-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc1-quantal/)

But again, not complete. The _all header package is missing.

---

### Post by zika on 2012-10-16
> **JMB74 said:**
> 3.7 RC1

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc1-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc1-quantal/)

But again, not complete. The _all header package is missing.Thank You!
So, we'll wait for tomorrow... ;)

---

### Post by paul_in_london on 2012-10-16
> **zika said:**
> Thank You!
So, we'll wait for tomorrow... ;)

Been looking out for this.

Might be the longer than that actually! When there's an incomplete set of mainline debs for rcN things typically seem to stay that way until rcN+1 or longer.

Maybe we'll get a complete daily build before 3.7-rc2. Who knows?!

---

### Post by zika on 2012-10-16
> **paul_in_london said:**
> Been looking out for this.

Might be the longer than that actually! When there's an incomplete set of mainline debs for rcN things typically seem to stay that way until rcN+1 or longer.

Maybe we'll get a complete daily build before 3.7-rc2. Who knows?!I'm hoping that may favorite (daily) will recover. What undermines my hope is that there was no _all.deb and working daily for days... Or should I be fair and say: weeks... ;)

---

### Post by paul_in_london on 2012-10-16
> **zika said:**
> I'm hoping that may favorite (daily) will recover. What undermines my hope is that there was no _all.deb and working daily for days... Or should I be fair and say: weeks... ;)

Hard to say, but when I've seen this sort of thing before the dailies often suffer the same problem until the next rc. :(

---

### Post by zika on 2012-10-16
> **paul_in_london said:**
> Hard to say, but when I've seen this sort of thing before the dailies often suffer the same problem until the next rc. :(Any idea what is happening with _all.deb file?

---

### Post by paul_in_london on 2012-10-16
> **zika said:**
> Any idea what is happening with _all.deb file?

Only that it's missing I'm afraid! :lolflag:

---

### Post by JMB74 on 2012-10-16
Can only imagine that the build script/packaging needs updating to cope with the new 3.7 based RCs and dailys.

I'm sure the kernel team will sort it in due course.

---

### Post by zika on 2012-10-16
> **JMB74 said:**
> Can only imagine that the build script/packaging needs updating to cope with the new 3.7 based RCs and dailys.

I'm sure the kernel team will sort it in due course._all.deb is MIA for weeks now... Long before 3.7 window was even threatening to be closed... ;)

---

### Post by zika on 2012-10-16
> **paul_in_london said:**
> Only that it's missing I'm afraid! :lolflag::lolflag: BAY... ;)

---

### Post by JMB74 on 2012-10-16
> **zika said:**
> _all.deb is MIA for weeks now... Long before 3.7 window was even threatening to be closed... ;)

The daily builds come from the tip of the master branch, which would  include all the 3.7 merges up to that date since the opening of the window. Doesn't wait for the window to close.

3.7 merge window opened on 3rd October IIRC.

_all.debs went MIA on the daily builds from 8th October onwards.

So while the 3.7 merge was not complete at that point, a fair part of it had been already pulled.

---

### Post by zika on 2012-10-16
> **JMB74 said:**
> The daily builds come from the tip of the master branch, which would  include all the 3.7 merges up to that date since the opening of the window. Doesn't wait for the window to close.

3.7 merge window opened on 3rd October IIRC.

_all.debs went MIA on the daily builds from 8th October onwards.

So while the 3.7 merge was not complete at that point, a fair part of it had been already pulled.Mea culpa. I've got fooled with 3.6 marker on them... ;)
Thank You...

---

### Post by pqwoerituytrueiwoq on 2012-10-16
i updated my kernel update checker script 
[http://ubuntuforums.org/showpost.php?p=12295834&postcount=26](http://ubuntuforums.org/showpost.php?p=12295834&postcount=26)

---

### Post by JMB74 on 2012-10-16
> **zika said:**
> Mea culpa. I've got fooled with 3.6 marker on them... ;)
Thank You...

Yep. Looks like they don't bump the version number on those builds until the window closes and the first RC is out.

---

### Post by zika on 2012-10-16
> **JMB74 said:**
> Yep. Looks like they don't bump the version number on those builds until the window closes and the first RC is out.While we are at this subject: what is the relation of daily-intel-experimental (994) to 999?

---

### Post by Vrroom on 2012-10-17
3.7 rc1 is now available. However there is no linux-header_all.deb file this time and only three files per architecture. Should I go ahead and install them?

---

### Post by zika on 2012-10-17
> **vrroom said:**
> 3.7 rc1 is now available. However there is no linux-header_all.deb file this time and only three files per architecture. Should i go ahead and install them?goto #38... ;)

---

### Post by Vrroom on 2012-10-17
> **zika said:**
> goto #38... ;)

Ok I get it. But it is so hard to wait once you get this addiction :)

---

### Post by VinDSL on 2012-10-17
> **Vrroom said:**
> 3.7 rc1 is now available. However there is no linux-header_all.deb file this time and only three files per architecture. Should I go ahead and install them?
For giggles, I went ahead and installed Linux 3.7-rc1, sans the all.deb file.

It didn't install correctly, of course -- unmet dependencies, thus broken header file -- but, it did boot and run in fallback mode, e.g. no 3D, so called.

Unity had no dash nor panel, but Conky (system monitoring app) worked. LoL!

Gnome-shell was in fallback mode, e.g. Gnome Classic.  Other than no 3D display, it seemed to be fully functional.

LXDE/Openbox worked fine.  Go figure.

Ultimately, I purged 3.7-rc1 (not fully cooked yet), reinstalled the nVidia 304.51 drivers (from edger's PPA), and all is normal again, under Linux 3.6.2.

Bottom line:  I don't recommend installing 3.7-rc1, unless you want to push Humpty Dumpty off the wall (and put him back together again).  ;)

---

### Post by zika on 2012-10-17
> **VinDSL said:**
> LXDE/Openbox worked fine.  Go figure.It works for me, I use OB or FB all the time...
Installed 3 files. Removed headers after image was created. It booted OK. Writing from 3.7...
Now I'll try to find some time to compile it following Milos_SD instructions on our LOCO Forum...

---

