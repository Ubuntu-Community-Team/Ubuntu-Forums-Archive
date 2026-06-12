---
title: "update removed wine1.3 and install 1.2"
date: 2011-01-25
forum: Wine
---

### Post by beew on 2011-01-25
I am using Ubuntu10.10. In yesterday's update, wine was downgraded to version 1.2 from 1.3 because 1.3 appears to be in conflict with some other things being updated. One such thing may be lmms-vst, removing lnms-vst updates wine to a higher version of 1.3x successfully in one of my installations,  but on my second Maverick installation the same thing happens even though lmms is not installed. Does anyone experience the same thing?

---

### Post by Halzen on 2011-01-25
That's odd. Why would LMMS conflict with a Wine package change at all? They seem completely unrelated to my third-person eyes.

---

### Post by jscherer26 on 2011-01-26
I'm getting the following:

[INDENT]sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  wine1.3
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  wine1.3 wine1.3-gecko
The following NEW packages will be installed:
  wine1.2 wine1.2-gecko
0 upgraded, 2 newly installed, 2 to remove and 0 not upgraded.
Need to get 19.3MB of archives.
After this operation, 11.3MB disk space will be freed.
Do you want to continue [Y/n]? n[/INDENT]

I'm not sure why and haven't downgraded yet.

---

### Post by sweener on 2011-01-27
I'm currently experiencing the same problem.

---

### Post by YokoZar on 2011-01-27
Ah hah!  I was wondering if there would be any side effects.  I recently removed the "Provides: wine1.2" line because I discovered it was possible to have wine1.2-gecko and wine1.3 installed simultaneously, which is a bad situation.

lmms-vst has a dependency on wine1.2 -- it should depend on wine1.2 OR wine (a virtual/dummy package which is then provided by wine1.3).

I'll make some updates to the ppa package, put a fixed lmms-vst into the ppa so the dependencies work, and also upload a fix to Natty.

Thanks!

---

### Post by sweener on 2011-01-27
> **YokoZar said:**
> Ah hah!  I was wondering if there would be any side effects.  I recently removed the "Provides: wine1.2" line because I discovered it was possible to have wine1.2-gecko and wine1.3 installed simultaneously, which is a bad situation.

lmms-vst has a dependency on wine1.2 -- it should depend on wine1.2 OR wine (a virtual/dummy package which is then provided by wine1.3).

I'll make some updates to the ppa package, put a fixed lmms-vst into the ppa so the dependencies work, and also upload a fix to Natty.

Thanks!

Thank you YokoZar for you lightning quick response! Cheers!

---

### Post by YokoZar on 2011-01-27
> **sweener said:**
> Thank you YokoZar for you lightning quick response! Cheers!

Hmm a lmms update might not be needed as it already depends on just the nonspecific wine package.

So I'm putting up a new wine1.2 now.

---

### Post by YokoZar on 2011-01-27
Should be built now.  Is it working for you?

---

### Post by rajeev1204 on 2011-01-27
Well, i just let it remove 1.3 a day or 2 ago, but today i manually installed 1.3 from synaptic and it seems to install fine.

1.3.12 .

---

### Post by sweener on 2011-01-27
> **YokoZar said:**
> Should be built now.  Is it working for you?

Using the Update Manager it still wants to remove wine1.3 and install wine1.2

Ran in the terminal sudo apt-get update && sudo apt-get upgrade and then wine1.3 was listed as an upgrade

Ran the upgrade and the issue is resolved.

Thank you for the help everyone. Cheers.

---

### Post by beew on 2011-01-27
Yokozar,

Thanks for the quick response. I have previously upgraded to wine1.3.12  and removed lmms-vst. Now I am trying to reinstall lmms-vst from  synaptic and it still insists that I have to downgrade wine to 1.2.

---

### Post by bdamon on 2011-01-27
I am having this downgrade issue as well. I do not have lmms-vst installed.

---

### Post by YokoZar on 2011-01-28
How about dssi-vst?  That may be a problem as well.

---

### Post by dudetime on 2011-01-28
I did the same thing yet i had unmet dependencies...

---

### Post by bdamon on 2011-01-28
> **YokoZar said:**
> How about dssi-vst?  That may be a problem as well.

That package is not installed either.

Here is what it wants to do


The following packages will be REMOVED:
  wine1.3
The following NEW packages will be installed:
  linux-headers-2.6.35-25 linux-headers-2.6.35-25-generic linux-image-2.6.35-25-generic wine1.2
The following packages will be upgraded:
  brasero brasero-cdrkit brasero-common bsdutils evolution-data-server evolution-data-server-common evolution-data-server-dbg fuse-utils google-chrome-beta hpijs hplip
  hplip-data ia32-libs icedtea-6-jre-cacao icedtea6-plugin jockey-common jockey-gtk libblkid1 libbrasero-media1 libcamel1.2-14 libebackend1.2-0 libebook1.2-9
  libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-7 libedataserver1.2-13 libedataserverui1.2-8 libegroupwise1.2-13 libfuse2 libgdata-google1.2-1 libgdata1.2-1 libhpmud0
  libnautilus-extension1 libsane-hpaio libsmbclient libuuid1 libvlc5 libvlccore4 libwbclient0 linux-firmware linux-generic linux-headers-generic linux-image-generic
  linux-libc-dev mount mozilla-plugin-vlc nautilus nautilus-data nautilus-dbg nvidia-96-modaliases openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib openssh-client
  python-apt samba-common samba-common-bin smbclient ssh-askpass-gnome sudo tar ttf-symbol-replacement-wine1.3 util-linux util-linux-locales uuid-runtime vlc vlc-data
  vlc-nox vlc-plugin-notify vlc-plugin-pulse winbind xserver-common xserver-xorg-core xserver-xorg-input-evdev
74 upgraded, 4 newly installed, 1 to remove and 0 not upgraded.

---

### Post by ooburns on 2011-01-28
Same here. After an apt-get update:

```
The following packages will be REMOVED:
  wine1.3
The following NEW packages will be installed:
  wine1.2
The following packages will be upgraded:
  apparmor apparmor-utils computer-janitor computer-janitor-gtk gimp gimp-data
  google-chrome-beta grub-common grub-pc hpijs hplip hplip-cups hplip-data
  libapparmor-perl libapparmor1 libc-bin libc-dev-bin libc6 libc6-dev
  libgimp2.0 libhpmud0 libsane-hpaio libvlc5 libvlccore4 linux-generic
  linux-headers-2.6.35-25 linux-headers-2.6.35-25-generic
  linux-headers-generic linux-image-2.6.35-25-generic linux-image-generic
  linux-libc-dev python-gtkspell rhythmbox rhythmbox-plugin-cdrecorder
  rhythmbox-plugins transmission-common transmission-gtk
  ttf-symbol-replacement-wine1.3 upstart vlc vlc-data vlc-nox
  vlc-plugin-notify vlc-plugin-pulse youtube-dl
45 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
```

Or maybe the mirror I'm using just hasn't updated itself yet?

Edit: I don't have dssi-vst or lmms-vst installed.

---

### Post by YokoZar on 2011-01-29
Do you guys have wine1.2-gecko installed or wine1.3-gecko?

---

### Post by bdamon on 2011-01-29
> **YokoZar said:**
> Do you guys have wine1.2-gecko installed or wine1.3-gecko?

I have wine1.3-gecko installed here.

---

### Post by beew on 2011-02-06
Hi, YokoZar,

Hope you are still reading.. Yesterday got an update for wine1.3. Still cannot install lmms-vst. Got the message "depends on wine1.2 but it is not to be installed". Maybe it is a problem on lmms-vst's end?

---

### Post by bdamon on 2011-02-06
I am not sure what happened but today I was able to update without downgrading to 1.2. Something changed as I have been holding out doing updates to see if this was resolved and it has been at least for me.

---

### Post by Dark_Oppressor on 2011-02-17
I'm currently having this same issue in Maverick.  I have wine1.3, as well as wine1.3-gecko installed.  I'm trying to install lmms-vst, but it's wanting to uninstall wine1.3 and install wine1.2.  At one point I tried letting it do this and then updating and upgrading through apt-get but it said there was nothing to upgrade.  I also noticed after letting it install wine1.2 that wine1.3-gecko was still installed.

---

### Post by YokoZar on 2011-02-18
> **Dark_Oppressor said:**
> I'm currently having this same issue in Maverick.  I have wine1.3, as well as wine1.3-gecko installed.  I'm trying to install lmms-vst, but it's wanting to uninstall wine1.3 and install wine1.2.  At one point I tried letting it do this and then updating and upgrading through apt-get but it said there was nothing to upgrade.  I also noticed after letting it install wine1.2 that wine1.3-gecko was still installed.

Can you please:

```
dpkg -s wine
```

for me?

lmms-vst depends on "wine" which should be satisfied in several ways.  Wine1.3 package provides "wine" (ie, a virtual package), and the new PPA "wine" package depends on either wine1.2 or wine1.3 (which should be satisfied if wine1.3 is installed).

---

### Post by rajeev1204 on 2011-02-20
Hi i have a question a bit different from original topic.
Why does wine ppa offer its own version of ia 32 libs for 64 bit users?

I got a new version a few days ago and team fortress 2 started working after almost half a year of not starting up.

---

### Post by YokoZar on 2011-02-20
> **rajeev1204 said:**
> Hi i have a question a bit different from original topic.
Why does wine ppa offer its own version of ia 32 libs for 64 bit users?

I got a new version a few days ago and team fortress 2 started working after almost half a year of not starting up.
Because maverick's bundled version is missing some libraries

---

