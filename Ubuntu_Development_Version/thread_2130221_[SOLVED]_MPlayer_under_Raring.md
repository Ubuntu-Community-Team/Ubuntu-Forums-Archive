---
title: "[SOLVED] MPlayer under Raring"
date: 2013-03-28
forum: Ubuntu Development Version
---

### Post by andrew.46 on 2013-03-28
I have resurrected an old guide that early adopters of Raring might be interested in:

Howto: Build the svn MPlayer under the latest release version of Ubuntu
[http://www.andrews-corner.org/mplayer.html](http://www.andrews-corner.org/mplayer.html)

Any corrections or comments welcome...

---

### Post by mc4man on 2013-03-29
Basically seems ok, tried the full how-to though generally wouldn't do mencoder or gmplayer.
(the wget  ftp did initially fail to login, retrying a min or so later was ok.

Could consider adding libopus-dev to deps & to file under doesn't matter the grand quest to enable fstrans in Ubuntu has ended, the default now should be no

---

### Post by andrew.46 on 2013-03-29
Thanks for looking at the guide (again!). Interest in this guide has waned *hugely* since the old days but I guess I shall at the very least update with each change of Ubuntu versions. libopus-dev is added in and as for the fstrans saga I am glad that it has finally come to an end :).

---

### Post by mc4man on 2013-03-29
> **andrew.46 said:**
> Thanks for looking at the guide (again!). Interest in this guide has waned *hugely* since the old days but I guess I shall at the very least update with each change of Ubuntu versions..
May be that multimedia support has slowly but steadily gotten pretty good, either by default or easily enabled, compared to the past where people had to take care of themselves. So  less interest in alt. means  seems likely.

In any event good how-to's like your's are interesting in themselves, at least here.

---

### Post by SeijiSensei on 2013-03-29
I notice that mplayer2 seems to be the default version installed by Raring (at least for Kubuntu, but wouldn't that be true of all Raring flavors?).  Should you consider perhaps revising the guide to use the source at [www.mplayer2.org?](www.mplayer2.org?)

> **andrew.46 said:**
> Thanks for looking at the guide (again!). Interest in this guide has waned *hugely* since the old days

I've compiled a lot of copies of mplayer over the years, but if Ubuntu keeps current with mplayer2 development, I'll probably just use the version in the repositories.

---

### Post by andrew.46 on 2013-03-29
> **mc4man said:**
> May be that multimedia support has slowly but steadily gotten pretty good, either by default or easily enabled, compared to the past where people had to take care of themselves. So  less interest in alt. means  seems likely.

Could very well be, in which case many people are missing out on the joy of building their own media software as well as the knowledge gained in this undertaking.

> In any event good how-to's like your's are interesting in themselves, at least here.

My thanks :). I am drifting further away from Ubuntu these days so really just maintaining a foothold here and one firm foothold is building MPlayer under Ubuntu. I have been doing this for so long that it almost seems part of me.

---

### Post by andrew.46 on 2013-03-29
> **SeijiSensei said:**
> I notice that mplayer2 seems to be the default version installed by Raring (at least for Kubuntu, but wouldn't that be true of all Raring flavors?).  Should you consider perhaps revising the guide to use the source at [www.mplayer2.org?](www.mplayer2.org?)

The version of this guide on the community wiki has a section on MPlayer2, but I am unable to gauge if this has been useful as feedback from this has been very, very low. Could be that use for this particular guide is perhaps past its useful time but I am disinclined to alter the website version for the MPlayer fork. The wiki is of course fair game for anybody to change :).

> I've compiled a lot of copies of mplayer over the years, but if Ubuntu keeps current with mplayer2 development, I'll probably just use the version in the repositories.

Perhaps have a look at recent changes to GMPlayer which now has a dedicated developer and is becoming usable. Works nicely on my system although I tend to use the commandline rather than any gui...

---

### Post by ping-wu on 2013-03-29
With my "very limited experience", I have found VLC to be a better video/audio player.

---

### Post by andrew.46 on 2013-03-29
> **ping-wu said:**
> With my "very limited experience", I have found VLC to be a better video/audio player.

vlc is a great player :).

---

### Post by mc4man on 2013-03-29
> **andrew.46 said:**
>  as the knowledge gained in the undertaking.

Many times the more interesting side of the coin

---

### Post by akgrant on 2013-03-30
> **andrew.46 said:**
> I have resurrected an old guide that early adopters of Raring might be interested in:

Howto: Build the svn MPlayer under the latest release version of Ubuntu
[http://www.andrews-corner.org/mplayer.html](http://www.andrews-corner.org/mplayer.html)

Any corrections or comments welcome...

Hi Andrew,

Thanks very much for making this available.  I've always used mplayer from the Ubuntu repositories and never even thought of building it (I have built avconv to get some additional codecs), but it is great to have this available.

Cheers,
Alistair

---

### Post by andrew.46 on 2013-03-30
My pleasure Alistair! There is an older version on the Ubuntu Wiki that I may update soon....

---

### Post by andrew.46 on 2013-04-23
> **mc4man said:**
> Basically seems ok, tried the full how-to though generally wouldn't do mencoder or gmplayer.

Have you had a look at the script on steroids: h264enc? I have run it a few times for curiosity and there has been a large amount of work done on it over many years. Does not make MEncoder any more of an option but it is interesting nevertheless...

---

### Post by mc4man on 2013-04-23
> **andrew.46 said:**
> Have you had a look at the script on steroids: h264enc? I have run it a few times for curiosity and there has been a large amount of work done on it over many years. Does not make MEncoder any more of an option but it is interesting nevertheless...

Yeah, though it's been a few years it seems (from froggy1 over at doom9 iirc
Atm my only linux machine is an aging laptop that tends to get real hot while doing encoding unless i keep the room at mid 50's or less
(my new laptop does great at h264 encoding but as of yet haven't decided how to partition, ect. to install a linux distro & still keep win 7

---

### Post by mc4man on 2013-04-23
Just to note - 
libggi-target-fbdev was removed from raring repositories on 04/19

---

### Post by andrew.46 on 2013-04-23
> **mc4man said:**
> Just to note - 
libggi-target-fbdev was removed from raring repositories on 04/19

The perils of jumping in early with a guide :). BTW well worth a look at xvidenc as well...

---

### Post by monkeybrain2012 on 2013-04-24
> **ping-wu said:**
> With my "very limited experience", I have found VLC to be a better video/audio player.

Not so for me, mplayer2 (with Smplayer as front end ) is always faster and smoother, and if you have a Nvidia card it is much more efficient to use vdpau with mplayer2 (or mplayer) than with VLC. Only thing that goes for VLC for my purpose is that it plays some formats that doesn't play in other players and for streaming some contents.

---

### Post by monkeybrain2012 on 2013-04-24
I am intetested in compiling mplayer with vaapi support. :)

---

### Post by andrew.46 on 2013-04-27
I have just run the guide on a fresh installation of the release version of Raring and all seems well. Thanks for all who had a look!

---

