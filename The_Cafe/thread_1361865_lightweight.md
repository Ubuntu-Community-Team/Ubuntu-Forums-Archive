---
title: "lightweight"
date: 2009-12-22
forum: The Cafe
---

### Post by dzon65 on 2009-12-22
I've been trying for days now to install puppy on this prehistoric compaq pressario.For one,I just wanted to see how fast this distro works.Unfortunately,the only option (after trying the whole bunch:smart boot manager,wakepup,unetbootin.....since there's no cd-boot option) take out the hard drive and install it through another pc.
Anyway,it's too bad the ubuntu family has no real leightweight (lighter than xubuntu,lite or flux),installable on old ,low spec pc's.(<128mb ram) AND if possible,even installable with wubi.(tried wubi to install xubuntu and it worked,far to low specs though)
Might be wrong,but I heard xubuntu is on a diet,lowering the requirements,but still.Some very leightweight version,with a seamonkey or that fluxbuntu browser,leight editors....would be very nice.

---

### Post by Grifulkin on 2009-12-22
> **dzon65 said:**
> I've been trying for days now to install puppy on this prehistoric compaq pressario.For one,I just wanted to see how fast this distro works.Unfortunately,the only option (after trying the whole bunch:smart boot manager,wakepup,unetbootin.....since there's no cd-boot option) take out the hard drive and install it through another pc.
Anyway,it's too bad the ubuntu family has no real leightweight (lighter than xubuntu,lite or flux),installable on old ,low spec pc's.(<128mb ram) AND if possible,even installable with wubi.(tried wubi to install xubuntu and it worked,far to low specs though)
Might be wrong,but I heard xubuntu is on a diet,lowering the requirements,but still.Some very leightweight version,with a seamonkey or that fluxbuntu browser,leight editors....would be very nice.

They do have a lightweight version.  It is called Arch.

JK

---

### Post by cariboo on 2009-12-22
Have you had a look at [Lubuntu]("https://wiki.ubuntu.com/Lubuntu")?

---

### Post by gutterslob on 2009-12-22
You could try CrunchBang Lite
Might not be as skinny as Puppy or DSL, but it's based on Jaunty.

If Ubuntu origins aren't required, then you can try Vector Linux.

Minimal Debian or Arch + lightweight WM is probably the ideal solution if you're up to the task.

---

### Post by LowSky on 2009-12-22
He need to be able to even use it, and if he cant boot from the CD then he needs to use a floppy drive to boot the dsc
AND look what is available for Puppy
[http://pupweb.org/wikka/WakePUP](http://pupweb.org/wikka/WakePUP)

With this you make a bootable floppy and it will start up Puppy on the medium of choice, usb, CD, etc

---

### Post by Glenn nl on 2009-12-22
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Install the CLI and then install the following packages:

```
xorg
gdm
xfce4
gdebi
epiphany-browser
thunderbird
xfce4-terminal
synaptic
gpaint
abiword
gnumeric
xubuntu-default-settings
xubuntu-restricted-extras
xfce4-taskmanager
xfce4-screenshooter
dmz-cursor-theme
file-roller
pidgin
mousepad
ristretto
xfburn
xfce4-notifyd
xfmedia
```

It installs a minimal Xubuntu which runs in about 60 mb of ram.

---

### Post by dzon65 on 2009-12-22
> **LowSky said:**
> He need to be able to even use it, and if he cant boot from the CD then he needs to use a floppy drive to boot the dsc
AND look what is available for Puppy
[http://pupweb.org/wikka/WakePUP](http://pupweb.org/wikka/WakePUP)

With this you make a bootable floppy and it will start up Puppy on the medium of choice, usb, CD, etc
Tried it,no use.Ran through options,all distros are great but I just can't install them....for now.I'll try to install with switching drives.
Oh,that xubuntu leight looks nice.In the mean time I read a bit about u-lite (former ubuntu lite),takes about 197 ram.

---

### Post by dzon65 on 2009-12-22
> **Glenn nl said:**
> [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Install the CLI and then install the following packages:

```
xorg
gdm
xfce4
gdebi
epiphany-browser
thunderbird
xfce4-terminal
synaptic
gpaint
abiword
gnumeric
xubuntu-default-settings
xubuntu-restricted-extras
xfce4-taskmanager
xfce4-screenshooter
dmz-cursor-theme
file-roller
pidgin
mousepad
ristretto
xfburn
xfce4-notifyd
xfmedia
```It installs a minimal Xubuntu which runs in about 60 mb of ram.
By no means there's a cd boot option available unless I upgrade the bios and that's a bit of a mess.So,a live cd is a non goer for now.

---

### Post by snowpine on 2009-12-22
All hardware becomes obsolete eventually. The first version of Ubuntu came out in 2004, so in my opinion, Canonical should not waste their time "tweaking" Ubuntu for computers more than 5 years old.

---

### Post by K.Mandla on 2009-12-22
> **dzon65 said:**
> I've been trying for days now to install puppy on this prehistoric compaq pressario.For one,I just wanted to see how fast this distro works.Unfortunately,the only option (after trying the whole bunch:smart boot manager,wakepup,unetbootin.....since there's no cd-boot option) take out the hard drive and install it through another pc.
Anyway,it's too bad the ubuntu family has no real leightweight (lighter than xubuntu,lite or flux),installable on old ,low spec pc's.(<128mb ram) AND if possible,even installable with wubi.(tried wubi to install xubuntu and it worked,far to low specs though)
Might be wrong,but I heard xubuntu is on a diet,lowering the requirements,but still.Some very leightweight version,with a seamonkey or that fluxbuntu browser,leight editors....would be very nice.
[http://ubuntuforums.org/showthread.php?t=575456](http://ubuntuforums.org/showthread.php?t=575456)
> **snowpine said:**
> All hardware becomes obsolete eventually. The first version of Ubuntu came out in 2004, so in my opinion, Canonical should not waste their time "tweaking" Ubuntu for computers more than 5 years old.
Yes, Canonical should not. The rest of us will.

[http://kmandla.wordpress.com/projects/](http://kmandla.wordpress.com/projects/)

---

### Post by dzon65 on 2009-12-23
> **snowpine said:**
> All hardware becomes obsolete eventually. The first version of Ubuntu came out in 2004, so in my opinion, Canonical should not waste their time "tweaking" Ubuntu for computers more than 5 years old.

Never said they SHOULD.Just suggested it would be nice.By standards of hardware capability,do you have any idea how many hardware's been throwed away just because the specs aren't sufficient enough to run nowadays OS'es?Every year each school dumps their pc's just because it fits in their budget and they're used to xp which,so they're being told just won't do it anymore and upgrading even the ram is out of the question.This laptop I'm using right now has what,2gb ram and 120gb storage but it has this "ancient"nvidia 6150 card which is by today's standards "obsolete".Why on earth would I dump it if their was a change I could give it to that kid wearing a five year old jeans and hasn't seen a holiday in years.Sorry kid,nocando,this laptop is obsolete.If you want to browse a little,chat alittle....you'll just have to wait for that brand new computer costing only 50 euros.
Of course canonical shouldn't spend it's time focusing on that.Again,it would be nice,when all install options fail one could still use some "obsolete" pc by using wubi for example,if only it would be for a year.
Indeed,hardware becomes obsolete eventually,unfortunately,some's weird ideas just don't.

---

### Post by dzon65 on 2009-12-23
Oh,by the way.Thanks guys for the suggestions you made.Since I'm used to ubuntu I'll give that xubuntu light a try,that is,if I can put it on the HD.(Which should work.)

---

