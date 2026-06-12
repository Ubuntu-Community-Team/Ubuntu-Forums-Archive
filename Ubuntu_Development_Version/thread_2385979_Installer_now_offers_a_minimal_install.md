---
title: "Installer now offers a minimal install"
date: 2018-02-27
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2018-02-27
I haven't tried it yet but I needed to perform a fresh install for bug testing so used 20180227 and noticed on the same page where you can select whether or not to download updates and install third party goodies you can also select a minimal install .............. cool :D

I'd last used 20180220 and it wasn't there so this is pretty darn new.

---

### Post by sudodus on 2018-02-27
Which installer(s) - Ubuntu Desktop or Ubuntu Server or both?

---

### Post by harry332 on 2018-02-27
I suppose the minimal install is bootable into a console, but does not contain any desktop.

---

### Post by kansasnoob on 2018-02-27
> **sudodus said:**
> Which installer(s) - Ubuntu Desktop or Ubuntu Server or both?

I've only tried the desktop version. But i needed a full install so haven't tried it yet myself.

---

### Post by kansasnoob on 2018-02-27
> **harry332 said:**
> I suppose the minimal install is bootable into a console, but does not contain any desktop.

It says you get a basic DE and browser. I'll see if I have time to try it later today.

---

### Post by kansasnoob on 2018-02-27
Here's what I'm talking about:

[ATTACH=CONFIG]278697[/ATTACH]

I just completed an installation so now it's time to dig deeper. I did see upon booting that both Ubuntu and Ubuntu with Wayland are available at login.

---

### Post by cruzer001 on 2018-02-27
I prefer a minimal install and add my packages to it, so I have ubuntu-desktop installed using --no-recommends.

Could you tell me if this is what the minimal install is doing or is it lighter than that?  Just curious about how its built, I do not intend to use it.  I find the gnome-core install more to my liking, but I would just like to know.

---

### Post by kerry_s on 2018-02-27
minimal desktop = what

is a trim gnome or some other de

---

### Post by kerry_s on 2018-02-27
wow, my Internets slow today. it'll take a hour to download for me.

i'll try it & report back. :)

---

### Post by kerry_s on 2018-02-27
okay have it installed. it's a basic gnome setup, but still ubuntu.

[ATTACH=CONFIG]278701[/ATTACH][ATTACH=CONFIG]278702[/ATTACH][ATTACH=CONFIG]278703[/ATTACH]

there were 11 updates, from this daily install.

my thoughts:

i love it!
it's pretty damn fast without the bloat. 
still double icon issue when adding the terminal to dock, still 17.10 look & feel.

---

### Post by cruzer001 on 2018-02-27
And here's what ubuntu-desktop looks like without the recommended packages.

[ATTACH=CONFIG]278705[/ATTACH][ATTACH=CONFIG]278704[/ATTACH]

Thanks kerry_s

---

### Post by kerry_s on 2018-02-27
how did you get it with out the recommends? i didn't see that option.

---

### Post by cruzer001 on 2018-02-27
No, its not an option.  You would need to use the mini or server iso.

---

### Post by kerry_s on 2018-02-27
alright. i much prefer ubuntu this way, i hope they keep the minimal option.

---

### Post by kansasnoob on 2018-02-28
My best guess is they're doing this so a person can choose between a pure(ish) Ubuntu and a pure(ish) GNOME. Totem is still there as both use Totem, but there is no Thunderbird so you can choose Evolution if you prefer. That's just one noticeable difference. I don't see any difference in meta-packages. Oh, and no Libre Office! I loved Abiword but development has been slow and the Ubuntu maintainers have a bad habit of pulling in horrifically buggy (unstable or experimental) versions.

---

### Post by sudodus on 2018-02-28
Thanks for sharing this information :-)

I agree that this minimal installation option is a good one.

---

### Post by kerry_s on 2018-02-28
yeah, it's great. my favorite is elementary os for its speed & no bloat.

having all that extra stuff in the ubuntu install really turned me away, i don't want a lot of stuff i'm never going to use.

this i can use. i installed chrome, geary, kodi & plank, that's the main stuff i use.

forgot to add pic of how i have it now:
[ATTACH=CONFIG]278709[/ATTACH]

---

### Post by slickymaster on 2018-02-28
For those interested there's also Xubuntu Core. It's  a slimmed down version of Xubuntu that doesn&#8217;t come with all the additional features of a full and modern desktop. We essentially only ship Xfce and the basic look and feel of Xubuntu, so there will be no office suite, media players, et cetera.

You can grab it here: [https://unit193.net/xubuntu/core/pending/](https://unit193.net/xubuntu/core/pending/)

---

### Post by kerry_s on 2018-02-28
thanks i grabbed the torrent, i'll put it on a usb to play with later. i want to keep ubuntu 18 mini at least a day. :)

---

### Post by corradoventu on 2018-02-28
according [https://www.omgubuntu.co.uk/tag/ubuntu-18-04-lts](https://www.omgubuntu.co.uk/tag/ubuntu-18-04-lts) i should find minimal install [https://www.omgubuntu.co.uk/2018/02/ubuntu-18-04-minimal-install-option](https://www.omgubuntu.co.uk/2018/02/ubuntu-18-04-minimal-install-option) and ubuntu data collection [https://www.omgubuntu.co.uk/2018/02/ubuntu-data-collection-opt-out](https://www.omgubuntu.co.uk/2018/02/ubuntu-data-collection-opt-out) shouls i download and install last ISO for these new features?

---

### Post by TheFu on 2018-02-28
Golf clap for Canonical listening to all of us who don't want the *kitchen-sink* experience.  If it is a core part of the installer, even better.  Being able to get a minimal desktop across the entire set of flavors is a VERY good thing.

I'm looking forward to getting a newer 18.04 alpha - appears I grabbed the 2/26 version and missed it by 1 day.

So ... loaded the 2/26 version into a VM with 3G of RAM.  Gnome-shell was using all the RAM still. For shame.
Need to find a zsync source to update the ISO. Really don't want to grab the entire 1.6G again.

---

### Post by cruzer001 on 2018-02-28
Any idea what the minimal install package is called, I haven't been able to find it on line @packages.ubuntu.

---

### Post by vasa1 on 2018-02-28
I think you have to download the full 1.6 GB iso. The option for a minimal install is then available as in post #6.

---

### Post by cruzer001 on 2018-02-28
I would think there's a meta-pack out there somewhere.

---

### Post by jbicha on 2018-02-28
There is no metapackage for the minimal install currently. It's implemented at [https://bazaar.launchpad.net/~ubuntu-core-dev/ubuntu-seeds/ubuntu.bionic/view/head:/desktop.minimal-remove](https://bazaar.launchpad.net/~ubuntu-core-dev/ubuntu-seeds/ubuntu.bionic/view/head:/desktop.minimal-remove)

---

### Post by jbicha on 2018-02-28
> **corradoventu said:**
>  i should find … ubuntu data collection [https://www.omgubuntu.co.uk/2018/02/ubuntu-data-collection-opt-out](https://www.omgubuntu.co.uk/2018/02/ubuntu-data-collection-opt-out) shouls i download and install last ISO for these new features?

The data collection feature was proposed but not implemented yet.

The minimal option is present in today's daily ISOs for Ubuntu only (although other flavors may adopt the feature too).

---

### Post by cruzer001 on 2018-02-28
> **jbicha said:**
> There is no metapackage for the minimal install currently. It's implemented at [https://bazaar.launchpad.net/~ubuntu-core-dev/ubuntu-seeds/ubuntu.bionic/view/head:/desktop.minimal-remove](https://bazaar.launchpad.net/~ubuntu-core-dev/ubuntu-seeds/ubuntu.bionic/view/head:/desktop.minimal-remove)

Thanks jbicha

---

### Post by TheFu on 2018-02-28
Just installed with the minimal option (zsync worked nice, BTW). Checkbox on the top of the "add extras/install updates" screen. 

Took 10 minutes and included the amazon stuff.  Mouse is sluggish in the VM.  1vCPU, 3G RAM, KVM.  The prior install didn't have mouse issues.
Gnome-shell is using all 3G of RAM (virtual size), 300MB real.

Purged amazon link from the left-bar and the firefox h.264 plugin. Appears there is more to be removed looking in the software list, but there are probably some dependencies that I haven't discovered at this point.  Nice job, though removing the Amazon link in the favorites would gain some good will, even if it is just 50 bytes.

Love that the terminal has this:
```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.
```

---

### Post by vasa1 on 2018-02-28
@TheFu, also see [https://ubuntuforums.org/showthread.php?t=2385979&p=13744155#post13744155](https://ubuntuforums.org/showthread.php?t=2385979&p=13744155#post13744155) for a Xubuntu version.

---

### Post by cruzer001 on 2018-02-28
TheFu
> Golf clap for Canonical listening to all of us who don't want the kitchen-sink experience.
Yes, a very positive step.  Installing Ubuntu without the recommended packages is of course doable, but you end up installing a lot of those left out recommends.  A minimal install offered in the iso is a much better choice for most users.  I dare say even me :)
> Gnome-shell is using all 3G of RAM (virtual size)
Wonder why yours is so high.  Currently running on a full install of Ubuntu and using about half of what your using.

2vCPU, 3G ram, vBox

---

### Post by TheFu on 2018-02-28
```
PID USER      PR  NI    VIRT    RES    SHR S %CPU %MEM     TIME+ COMMAND
 1447 tf        20   0 3080920 349924  93848 S  1.3 11.3   0:43.76 gnome-shell
```

Perhaps I'm seeing it wrong?

Purged a few more extras. * nano gedit gnome-bluetooth gnome-todo-common  gnome-screenshot eog* ZERO use for those on a minimal desktop.  We all have different needs, I suppose.

---

### Post by cruzer001 on 2018-02-28
> **TheFu said:**
> Perhaps I'm seeing it wrong?

Or maybe I am :)

```
PID USER      PR  NI    VIRT    RES    SHR S %CPU %MEM     TIME+ COMMAND
1030 gcore     20   0 3666904 453108  94812 S   3.3 14.7   8:02.17 gnome-shell

free -m

              total        used        free      shared  buff/cache   available
Mem:           3001        2026         175          61         799         998
Swap:           567           0         567
```

I'm on my gnome-core install at the moment.  I expected similar results, but got this.

---

### Post by kansasnoob on 2018-02-28
> **jbicha said:**
> There is no metapackage for the minimal install currently. It's implemented at [https://bazaar.launchpad.net/~ubuntu-core-dev/ubuntu-seeds/ubuntu.bionic/view/head:/desktop.minimal-remove](https://bazaar.launchpad.net/~ubuntu-core-dev/ubuntu-seeds/ubuntu.bionic/view/head:/desktop.minimal-remove)

I'm guessing that this may ease Ubuntu GNOME Xenial -> Ubuntu Bionic upgrades? Just guessing with no knowledge of nuthin' :redface:

I assume the installer will still offer upgrades if certain protocols are met :confused:

---

### Post by flocculant on 2018-02-28
> **TheFu said:**
> ...  If it is a core part of the installer, even better.  Being able to get a minimal desktop across the entire set of flavors is a VERY good thing... .

iirc - to get this minimal desktop experience - each flavour has to supply a hardcoded list of packages to remove, it's not an automatic thing for anyone. The current Xubuntu Daily doesn't even show the option.

---

### Post by jbicha on 2018-03-17
> **TheFu said:**
> 
*gnome-todo-common  gnome-screenshot eog* ZERO use for those on a minimal desktop.

I respectfully disagree.

Except for gnome-todo-common. That was removed today. I appreciate your suggestion!

The intent is to provide a mostly bare-bones desktop but with a web browser and common system utilities.

---

### Post by Chanath on 2018-03-19
> **slickymaster said:**
> For those interested there's also Xubuntu Core. It's  a slimmed down version of Xubuntu that doesn&#8217;t come with all the additional features of a full and modern desktop.

He also makes Xebian, the minimal Xubuntu like based on Debian. 

> **slickymaster said:**
> We essentially only ship Xfce and the basic look and feel of Xubuntu, so there will be no office suite, media players, et cetera.


When you say "we," has Xubuntu-core already become official? Or are you doing it together with Unit193?

---

### Post by slickymaster on 2018-03-19
> **Chanath said:**
> He also makes Xebian, the minimal Xubuntu like based on Debian. 



When you say "we," has Xubuntu-core already become official? Or are you doing it together with Unit193?We = Xubuntu Team

---

### Post by Chanath on 2018-03-19
> **slickymaster said:**
> We = Xubuntu Team

That I understand. But, what I wanted to know is, whether the Unit 193's Xubuntu-Core is official or not?

This is what you wrote;
> **slickymaster said:**
> For those interested there's also Xubuntu Core. It's a slimmed down version of Xubuntu that doesn&#8217;t come with all the additional features of a full and modern desktop. We essentially only ship Xfce and the basic look and feel of Xubuntu, so there will be no office suite, media players, et cetera.

You can grab it here: [https://unit193.net/xubuntu/core/pending/](https://unit193.net/xubuntu/core/pending/)

---

### Post by flocculant on 2018-03-19
> **Chanath said:**
> That I understand. But, what I wanted to know is, whether the Unit 193's Xubuntu-Core is official or not?

This is what you wrote;

No - it's not 'official', if it was then it would be provided as other official flavours are. However, it is as 'official' as it's possible to get in the current circumstances.

---

### Post by Chanath on 2018-03-20
> **flocculant said:**
> No - it's not 'official', if it was then it would be provided as other official flavours are. However, it is as 'official' as it's possible to get in the current circumstances.

As it is not official, then the link to such a distro should not be posted here, I believe, even if it is better than the official Xubuntu, right?

---

### Post by kerry_s on 2018-03-20
> **Chanath said:**
> As it is not official, then the link to such a distro should not be posted here, I believe, even if it is better than the official Xubuntu, right?

what? let it go it's just a link. some of us other people enjoy trying new things.

---

### Post by Chanath on 2018-03-20
> **kerry_s said:**
> what? let it go it's just a link. some of use other people enjoy trying new things.

**I quite like what Unit 193 is doing.** As far as I am concerned, users should be given a chance to see other distros remixed from the official ones here, especially, if they are based on upcoming development release. But, if we are not supposed to give links and discuss any other distros based on the development release, then posting this link here is not exactly correct.

---

### Post by cariboo on 2018-03-20
> **Chanath said:**
> As it is not official, then the link to such a distro should not be posted here, I believe, even if it is better than the official Xubuntu, right?

I'm not sure what you are trying to do, but the minimal install is part of the official Xubuntu iso, it's not being released as a separate distribution. I'd suggest you read the whole thread, instead of jumping in at the end, and trying to start something.

---

### Post by Chanath on 2018-03-20
> **cariboo said:**
> I'm not sure what you are trying to do, but the minimal install is part of the official Xubuntu iso, it's not being released as a separate distribution. I'd suggest you read the whole thread, instead of jumping in at the end, and trying to start something.

The link given here, [https://ubuntuforums.org/showthread.php?t=2385979&page=2/#18](https://ubuntuforums.org/showthread.php?t=2385979&page=2/#18) is not of an official Ubuntu derivative. That link takes you to Unit 193's personal work. 

*I always read the threads from top to bottom, and that's why I noticed this. *

---

### Post by VMC on 2018-03-20
> **cariboo said:**
> I'm not sure what you are trying to do, but the minimal install is part of the official Xubuntu iso, it's not being released as a separate distribution. I'd suggest you read the whole thread, instead of jumping in at the end, and trying to start something.
I wish there were "Likes" for times like this. ;)

I'm interested in the link regarding xubuntu-core. Saved it, and think I will give it a go. I have a script I use to purge out a ton of programs I don't use on a full xubuntu. Let me see how the core works. I'll be back.

---

### Post by VMC on 2018-03-20
zsync didn't work for me:
```
$ zsync -i /media/vmc/SAVE/ISO/xubuntu-bionic-desktop-amd64.iso https://unit193.net/xubuntu/core/pending/xubuntu-18.04-core-amd64.iso.zsync
failed on url https://unit193.net/xubuntu/core/pending/xubuntu-18.04-core-amd64.iso.zsync could not read control file from URL https://unit193.net/xubuntu/core/pending/xubuntu-18.04-core-amd64.iso.zsync
```

---

### Post by flocculant on 2018-03-20
> **VMC said:**
> zsync didn't work for me:
```
$ zsync -i /media/vmc/SAVE/ISO/xubuntu-bionic-desktop-amd64.iso https://unit193.net/xubuntu/core/pending/xubuntu-18.04-core-amd64.iso.zsync
failed on url https://unit193.net/xubuntu/core/pending/xubuntu-18.04-core-amd64.iso.zsync could not read control file from URL https://unit193.net/xubuntu/core/pending/xubuntu-18.04-core-amd64.iso.zsync
```

try with http instead of https

---

### Post by VMC on 2018-03-20
> **flocculant said:**
> try with http instead of https
OK, that must be it. Thanks

 I already downloaded the whole file. I'm using it right now. It uses almost 1Gb less space. Just now finding what files are missing or what files I need.

---

### Post by VMC on 2018-03-20
I noticed the core has a date of March 9th. Is that a one time ISO, or do they plan to update it? No complaints just curious.

```
The following NEW packages will be installed:  fonts-opensymbol fonts-symbola libblockdev-fs2 libblockdev-loop2 libblockdev-part-err2 libblockdev-part2 libblockdev-swap2 libblockdev-utils2 libblockdev2 libisl19 libparted-fs-resize0 linux-headers-4.15.0-12
  linux-headers-4.15.0-12-generic linux-image-4.15.0-12-generic linux-image-extra-4.15.0-12-generic netplan.io
The following packages will be upgraded:
  at-spi2-core bind9-host binutils binutils-common binutils-x86-64-linux-gnu bsdutils command-not-found command-not-found-data cpp-7 dnsutils e2fslibs e2fsprogs fdisk fwupd gcc-7-base gcc-8-base gcr geoip-database
  gir1.2-atk-1.0 gir1.2-gdkpixbuf-2.0 gir1.2-packagekitglib-1.0 glib-networking glib-networking-common glib-networking-services gnome-keyring gnome-keyring-pkcs11 gstreamer1.0-plugins-base gstreamer1.0-plugins-good
  gstreamer1.0-pulseaudio gstreamer1.0-x gucharmap gvfs gvfs-common gvfs-daemons gvfs-libs hicolor-icon-theme humanity-icon-theme iproute2 libappstream-glib8 libatk-bridge2.0-0 libatk1.0-0 libatk1.0-data libatspi2.0-0
  libbind9-160 libbinutils libblkid1 libcapnp-0.6.1 libcom-err2 libcomerr2 libcurl3-gnutls libdns-export169 libdns169 libext2fs2 libfdisk1 libfreetype6 libfwupd2 libgcc1 libgck-1-0 libgcr-base-3-1 libgcr-ui-3-1
  libgdbm-compat4 libgdbm5 libgdk-pixbuf2.0-0 libgdk-pixbuf2.0-bin libgdk-pixbuf2.0-common libgnutls30 libgomp1 libgraphite2-3 libgstreamer-plugins-base1.0-0 libgstreamer-plugins-good1.0-0 libgstreamer1.0-0
  libgucharmap-2-90-7 libirs160 libisc-export166 libisc166 libisccc160 libisccfg160 libisl15 libjavascriptcoregtk-4.0-18 liblouis-data liblouis14 liblwres160 libmount1 libmpg123-0 libnm0 libpackagekit-glib2-18
  libpam-gnome-keyring libpam-modules libpam-modules-bin libpam-runtime libpam0g libpulse-mainloop-glib0 libpulse0 libpulsedsp libpython3.6-minimal libpython3.6-stdlib libsigc++-2.0-0v5 libsmartcols1 libsoup-gnome2.4-1
  libsoup2.4-1 libss2 libstdc++6 libthunarx-2-0 libudisks2-0 libuuid1 libwebkit2gtk-4.0-37 lightdm-gtk-greeter linux-firmware linux-generic linux-headers-generic linux-image-generic mount nano network-manager nplan
  packagekit packagekit-tools pulseaudio pulseaudio-utils python3-commandnotfound python3-distutils python3-gdbm python3-lib2to3 python3-pil python3-pkg-resources python3-update-manager python3.6 python3.6-minimal rfkill
  snapd squashfs-tools thunar thunar-data ubuntu-minimal ubuntu-standard udisks2 unattended-upgrades update-manager-core util-linux uuid-runtime xfce4-indicator-plugin xfce4-pulseaudio-plugin xfce4-settings xfonts-utils
  xserver-common xserver-xorg-core xserver-xorg-legacy xubuntu-core xubuntu-default-settings xubuntu-docs
150 upgraded, 16 newly installed, 0 to remove and 0 not upgraded.
Need to get 207 MB of archives.
After this operation, 347 MB of additional disk space will be used.



```

---

### Post by flocculant on 2018-03-20
> **VMC said:**
> I noticed the core has a date of March 9th. Is that a one time ISO, or do they plan to update it? No complaints just curious.

```
The following NEW packages will be installed:  fonts-opensymbol fonts-symbola libblockdev-fs2 libblockdev-loop2 libblockdev-part-err2 libblockdev-part2 libblockdev-swap2 libblockdev-utils2 libblockdev2 libisl19 libparted-fs-resize0 linux-headers-4.15.0-12
  linux-headers-4.15.0-12-generic linux-image-4.15.0-12-generic linux-image-extra-4.15.0-12-generic netplan.io
The following packages will be upgraded:
  at-spi2-core bind9-host binutils binutils-common binutils-x86-64-linux-gnu bsdutils command-not-found command-not-found-data cpp-7 dnsutils e2fslibs e2fsprogs fdisk fwupd gcc-7-base gcc-8-base gcr geoip-database
  gir1.2-atk-1.0 gir1.2-gdkpixbuf-2.0 gir1.2-packagekitglib-1.0 glib-networking glib-networking-common glib-networking-services gnome-keyring gnome-keyring-pkcs11 gstreamer1.0-plugins-base gstreamer1.0-plugins-good
  gstreamer1.0-pulseaudio gstreamer1.0-x gucharmap gvfs gvfs-common gvfs-daemons gvfs-libs hicolor-icon-theme humanity-icon-theme iproute2 libappstream-glib8 libatk-bridge2.0-0 libatk1.0-0 libatk1.0-data libatspi2.0-0
  libbind9-160 libbinutils libblkid1 libcapnp-0.6.1 libcom-err2 libcomerr2 libcurl3-gnutls libdns-export169 libdns169 libext2fs2 libfdisk1 libfreetype6 libfwupd2 libgcc1 libgck-1-0 libgcr-base-3-1 libgcr-ui-3-1
  libgdbm-compat4 libgdbm5 libgdk-pixbuf2.0-0 libgdk-pixbuf2.0-bin libgdk-pixbuf2.0-common libgnutls30 libgomp1 libgraphite2-3 libgstreamer-plugins-base1.0-0 libgstreamer-plugins-good1.0-0 libgstreamer1.0-0
  libgucharmap-2-90-7 libirs160 libisc-export166 libisc166 libisccc160 libisccfg160 libisl15 libjavascriptcoregtk-4.0-18 liblouis-data liblouis14 liblwres160 libmount1 libmpg123-0 libnm0 libpackagekit-glib2-18
  libpam-gnome-keyring libpam-modules libpam-modules-bin libpam-runtime libpam0g libpulse-mainloop-glib0 libpulse0 libpulsedsp libpython3.6-minimal libpython3.6-stdlib libsigc++-2.0-0v5 libsmartcols1 libsoup-gnome2.4-1
  libsoup2.4-1 libss2 libstdc++6 libthunarx-2-0 libudisks2-0 libuuid1 libwebkit2gtk-4.0-37 lightdm-gtk-greeter linux-firmware linux-generic linux-headers-generic linux-image-generic mount nano network-manager nplan
  packagekit packagekit-tools pulseaudio pulseaudio-utils python3-commandnotfound python3-distutils python3-gdbm python3-lib2to3 python3-pil python3-pkg-resources python3-update-manager python3.6 python3.6-minimal rfkill
  snapd squashfs-tools thunar thunar-data ubuntu-minimal ubuntu-standard udisks2 unattended-upgrades update-manager-core util-linux uuid-runtime xfce4-indicator-plugin xfce4-pulseaudio-plugin xfce4-settings xfonts-utils
  xserver-common xserver-xorg-core xserver-xorg-legacy xubuntu-core xubuntu-default-settings xubuntu-docs
150 upgraded, 16 newly installed, 0 to remove and 0 not upgraded.
Need to get 207 MB of archives.
After this operation, 347 MB of additional disk space will be used.



```
We do update it - but irregularly, usually in response to a change.

Possibly they are both updating now - will let you know when I do.

---

### Post by flocculant on 2018-03-20
> **flocculant said:**
> We do update it - but irregularly, usually in response to a change.

Possibly they are both updating now - will let you know when I do.

They have - both available.

---

### Post by VMC on 2018-03-20
> **flocculant said:**
> They have - both available.
Yes, your right. Now back to zsync.

---

### Post by zhanglini on 2018-03-22
I installed mate 18.04 minimal 20 days ago, all seem good.  The only prob I have is it drops wifi every few hours, and I have to restart the PC to fix it --- since I did not move/change anything else, it must be the OS.

---

### Post by VMC on 2018-03-22
> **slickymaster said:**
> We = Xubuntu Team
I was trying to figure out who is "Unit 193". So its the Xubuntu Team. Xubuntu-core is great by the way! That's how I will install it from now on.

---

### Post by kerry_s on 2018-03-23
hey, just a quick question.
does snaps work on the xubuntu core install?

just wondering, while i'm getting ready to install it.

---

### Post by jbicha on 2018-03-23
Snaps should work on any flavor.

Lubuntu is the only desktop flavor that doesn't install **snapd** by default. (I think they should install it, because the framework itself shouldn't be consuming any resources until someone actually installs a snap.)

---

### Post by flocculant on 2018-03-23
> **VMC said:**
> I was trying to figure out who is "Unit 193". So its the Xubuntu Team. Xubuntu-core is great by the way! That's how I will install it from now on.

[https://launchpad.net/~xubuntu-team/+members#active](https://launchpad.net/~xubuntu-team/+members#active)

That's the current list of reprobates involved in it :)

---

### Post by flocculant on 2018-03-23
> **kerry_s said:**
> hey, just a quick question.
does snaps work on the xubuntu core install?

just wondering, while i'm getting ready to install it.

> **jbicha said:**
> Snaps should work on any flavor.

Lubuntu is the only desktop flavor that doesn't install **snapd** by default. (I think they should install it, because the framework itself shouldn't be consuming any resources until someone actually installs a snap.)

@kerry_s - should work, manifest shows snapd.

@jbicha - our Core isn't official - till we try (again and again and again seemingly) with Release once more.

---

### Post by sgage on 2018-03-23
I just did a minimal install with today's build of Ubuntu MATE, and it went fine (and quickly!).

---

### Post by kerry_s on 2018-03-23
yeah, i have it installed with firefox snap working.

i had a hell of a time trying to get xubuntu-core installed. took me 3 tries, the installer is still buggy as hell.
i figured out it does not like me using a custom partition setup with xfs, i normally do efi,boot,root. tried install at boot up, then install from live desktop.
i finally just chose erase disk from the live desktop install & it made it through.

---

### Post by VMC on 2018-03-23
Xubuntu-Core works great, except '*zsync*'. It just hangs. Obviously, I have zsync installed. Tried using lubuntu, and it works. Is there another package not installed?
I can download any of the ISO's, but zsync nothing.

---

### Post by sudodus on 2018-03-23
> **VMC said:**
> Xubuntu-Core works great, except '*zsync*'. It just hangs. Obviously, I have zsync installed. Tried using lubuntu, and it works. Is there another package not installed?
I can download any of the ISO's, but zsync nothing.

Please describe how you used zsync (with the command line), and I will test if/how it works. (I am often using zsync to get various daily iso files.)

---

### Post by VMC on 2018-03-23
From manjaro, zsync'ing lubuntu, I used this (SAVE is mounted)
```
zsync -i /run/media/vmc/SAVE/ISO/lubuntu-bionic-desktop-amd64.iso http://cdimage.ubuntu.com/lubuntu/daily-live/current/bionic-desktop-amd64.iso.zsync
```
From lubuntu, zsync'ing xubuntu, I used this:
```
zsync -i /media/vmc/SAVE/ISO/xubuntu-bionic-desktop-amd64.iso http://cdimage.ubuntu.com/xubuntu/daily-live/current/bionic-desktop-amd64.iso.zsync
```

They both work and started immediately. Using xubuntu-core, I used either method above, and it evenually started 5-7 minutes later, but then stopped.

edit: I just installed today's Xubuntu, and 'zsync' worked perfectly. I wonder if its Xubuntu-core networking that's the issue.

---

### Post by sudodus on 2018-03-24
@VMC,

The first attempt from my 'production system' (a Xubuntu + Lubuntu system based on 16.04.1 LTS) failed. Selecting the url via Firefox gave me ```
[COLOR="#cc0000"]https[/COLOR]://unit193.net/xubuntu/core/pending/xubuntu-18.04-core-amd64.iso.zsync
``` and

```

$ zsync https://unit193.net/xubuntu/core/pending/xubuntu-18.04-core-amd64.iso.zsync
failed on url https://unit193.net/xubuntu/core/pending/xubuntu-18.04-core-amd64.iso.zsync
could not read control file from URL https://unit193.net/xubuntu/core/pending/xubuntu-18.04-core-amd64.iso.zsync

```

does not work. But I tried without the 'security s',

```

$ zsync http://unit193.net/xubuntu/core/pending/xubuntu-18.04-core-amd64.iso.zsync
#################### 100.0% 0.0 kBps DONE    

No relevent local data found - I will be downloading the whole file. If that's not what you want, CTRL-C out. You should specify the local file is the old version of the file to download with -i (you might have to decompress it with gzip -d first). Or perhaps you just have no data that helps download the file
downloading from http://unit193.net/xubuntu/core/pending/xubuntu-18.04-core-amd64.iso:
#################### 100.0% 11437.3 kBps DONE     

verifying download...checksum matches OK
used 0 local, fetched 693109046

```

and it works, I could repeat it,

```

$ zsync http://unit193.net/xubuntu/core/pending/xubuntu-18.04-core-amd64.iso.zsync
#################### 100.0% 0.0 kBps DONE    

reading seed file xubuntu-18.04-core-amd64.iso: ***************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************Read xubuntu-18.04-core-amd64.iso. Target 100.0% complete.      
verifying download...checksum matches OK
used 693108736 local, fetched 0

```

You are showing that you use http (not https). So I think you are right, that there was a temporary glitch in the internet connection, when you tried and failed.

**Edit:**

I continued to test this current daily Xubuntu-Core iso file.

- It works well live-only 'Try Xubuntu'
- I installed it in an internal drive and the installed system works well.
- I made a persistent live USB 3 pendrive and it works well :-)

---

### Post by VMC on 2018-03-24
sudodus,

I keep getting "No route to host" using xubuntu-core, but not the other three.

```

$ zsyncl
cdimage.ubuntu.com: No route to host
#################### 100.0% 328.6 kBps DONE     

reading seed file /media/vmc/SAVE/ISO/lubuntu-bionic-desktop-amd64.iso: ********************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************Read /media/vmc/SAVE/ISO/lubuntu-bionic-desktop-amd64.iso. Target 100.0% complete.      
verifying download...checksum matches OK
used 1007681536 local, fetched 0
$ zsyncb
cdimage.ubuntu.com: No route to host
#################### 100.0% 370.1 kBps DONE     

reading seed file /media/vmc/SAVE/ISO/xubuntu-bionic-desktop-amd64.iso: ************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************Read /media/vmc/SAVE/ISO/xubuntu-bionic-desktop-amd64.iso. Target 89.2% complete.      
downloading from http://cdimage.ubuntu.com/xubuntu/daily-live/current/bionic-desktop-amd64.iso:
#################--- 89.2%cdimage.ubuntu.com: No route to host
#################--- 89.2% 2.2 kBps         
#################--- 90.0% 439.1 kBps 5:28 ETA  cdimage.ubuntu.com: No route to host
##################-- 90.8% 440.1 kBps 5:01 ETA  cdimage.ubuntu.com: No route to host
##################-- 92.4% 441.6 kBps 4:00 ETA  cdimage.ubuntu.com: No route to host
###################- 96.8% 412.5 kBps            

downloading from http://cdimage.ubuntu.com/xubuntu/daily-live/current/bionic-desktop-amd64.iso:
###################- 96.8%cdimage.ubuntu.com: No route to host
###################- 100.0% 428.9 kBps           

downloading from http://cdimage.ubuntu.com/xubuntu/daily-live/current/bionic-desktop-amd64.iso:
###################- 100.0%cdimage.ubuntu.com: Connection timed out
#################### 100.0% 0.4 kBps DONE    A  

verifying download...checksum matches OK
used 1244057600 local, fetched 151130119
$ 
```

(The zsyncl and zsyncb are aliases.)

---

### Post by sudodus on 2018-03-24
@VMC,

What exactly is the alias that you try to use to zsync xubuntu-core?

---

### Post by VMC on 2018-03-24
> **sudodus said:**
> @VMC,

What exactly is the alias that you try to use to zsync xubuntu-core?

I don't have an alias for core, just use zsync. Its not just zsync core, but any zsync I try.

---

### Post by jbicha on 2018-03-24
> **kansasnoob said:**
> Totem is still there.

Not any more as of today!

The minimal install option is literally what it says it is: a desktop environment with a web browser and some utilities.

That way you can install whatever music player you like!

---

### Post by kerry_s on 2018-03-24
i find xubuntu-core & ubuntu-mate minimal install are still a bit buggy. i really hope they work that out before release.

i'm still using the mate minimal install at the moment, i'm running the mutiny setup so it still feels like ubuntu. :)

---

### Post by VMC on 2018-03-24
> **kerry_s said:**
> i find xubuntu-core & ubuntu-mate minimal install are still a bit buggy. i really hope they work that out before release.

i'm still using the mate minimal install at the moment, i'm running the mutiny setup so it still feels like ubuntu. :)
What's buggy about mate-core?

---

### Post by kerry_s on 2018-03-24
> **VMC said:**
> What's buggy about mate-core?

there's a mate-core?

i did the minimal option from the mate 18 install.
stuff just randomly crashes, brisk menu the most.
i think most was due to composting, so i disabled. haven't seen a crash for awhile.[ATTACH=CONFIG]279075[/ATTACH][ATTACH=CONFIG]279076[/ATTACH]

---

### Post by VMC on 2018-03-24
My bad, I confused myself with mate minimum with core.

---

### Post by VMC on 2018-03-25
**Xubuntu-core zsync** is working perfectly now. Don't know what happened. Same code both days. I wish I could find ubuntu-traffic-data to see if something was up on that period of time.

---

### Post by kerry_s on 2018-03-25
it is all work in progress. just a timing thing. some sites are slower certain times of the day. (peak hours) or could be someone was just working on the file, maybe even to many people accessing at the same time.

---

### Post by sudodus on 2018-03-25
> **VMC said:**
> I don't have an alias for core, just use zsync. Its not just zsync core, but any zsync I try.

I see.

---

### Post by sudodus on 2018-03-25
> **kerry_s said:**
> it is all work in progress. just a timing thing. some sites are slower certain times of the day. (peak hours) or could be someone was just working on the file, maybe even to many people accessing at the same time.

+1 (I think so too)

---

