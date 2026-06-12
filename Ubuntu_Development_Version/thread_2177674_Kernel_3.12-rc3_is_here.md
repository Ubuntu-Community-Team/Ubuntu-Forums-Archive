---
title: "Kernel 3.12-rc3 is here"
date: 2013-09-29
forum: Ubuntu Development Version
---

### Post by paul_in_london on 2013-09-29
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-rc3-saucy/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-rc3-saucy/)

---

### Post by pqwoerituytrueiwoq on 2013-09-29
running good on my sandy bridge based laptop, may have better temps than rc2, could be a slightly lower ambient temp though

---

### Post by paul_in_london on 2013-09-30
Have been compiling my own kernel lately in an efffort to keep my system as lean as possible. Even on this old box it's fairly quick, thanks to localmodconfig.

```
paul@lubuntu-64:~$ cd /usr/src
paul@lubuntu-64:/usr/src$ tar jxvf ~/Downloads/linux-3.12-rc3.tar.bz2 # downloaded from https://www.kernel.org/pub/linux/kernel/v3.x/testing/
paul@lubuntu-64:/usr/src$ cd linux-3.12-rc3
paul@lubuntu-64:/usr/src/linux-3.12-rc3$ make-kpkg clean
paul@lubuntu-64:/usr/src/linux-3.12-rc3$ make localmodconfig # only enable what is needed for running system
paul@lubuntu-64:/usr/src/linux-3.12-rc3$ make menuconfig # no further changes made
paul@lubuntu-64:/usr/src/linux-3.12-rc3$ time fakeroot make-kpkg -j3 --initrd --append-to-version=-custom2 kernel-image kernel-headers # member of src group so not compiling as root
   ...

  dpkg-gencontrol -isp -DArchitecture=amd64 -plinux-headers-3.12.0-rc3-custom2 \
                                          -P/usr/src/linux-3.12-rc3/debian/linux-headers-3.12.0-rc3-custom2/
create_md5sums_fn () { cd $1 ; find . -type f ! -regex './DEBIAN/.*' ! -regex './var/.*'      -printf '%P\0' | xargs -r0 md5sum > DEBIAN/md5sums ; if [ -z "DEBIAN/md5sums" ] ; then rm -f "DEBIAN/md5sums" ; fi ; } ; create_md5sums_fn                   /usr/src/linux-3.12-rc3/debian/linux-headers-3.12.0-rc3-custom2
chown -R root:root                  /usr/src/linux-3.12-rc3/debian/linux-headers-3.12.0-rc3-custom2
chmod -R og=rX                      /usr/src/linux-3.12-rc3/debian/linux-headers-3.12.0-rc3-custom2
dpkg --build                        /usr/src/linux-3.12-rc3/debian/linux-headers-3.12.0-rc3-custom2 ..
dpkg-deb: building package `linux-headers-3.12.0-rc3-custom2' in `../linux-headers-3.12.0-rc3-custom2_3.12.0-rc3-custom2-10.00.Custom_amd64.deb'.
cp -pf debian/control.dist          debian/control
make[2]: Leaving directory `/usr/src/linux-3.12-rc3'
make[1]: Leaving directory `/usr/src/linux-3.12-rc3'

real	36m42.756s
user	41m18.607s
sys	7m10.499s
```

```
paul@lubuntu-64:/usr/src/linux-3.12-rc3$ cd ..
paul@lubuntu-64:/usr/src$ sudo dpkg -i li*.deb # install the debs and reboot
```

```
paul@lubuntu-64:~$ uname -a
Linux lubuntu-64 3.12.0-rc3-custom2 #1 SMP Mon Sep 30 20:34:24 BST 2013 x86_64 x86_64 x86_64 GNU/Linux
paul@lubuntu-64:~$
```

```
paul@lubuntu-64:~$ paul@lubuntu-64:~$ locate "*.ko" | grep 3.12.0-rc3-custom2 |wc -l
78
paul@lubuntu-64:~$
``` compared with:

```
paul@lubuntu-64:~$ locate "*.ko" | grep 3.11.0-9-generic |wc -l
3954
paul@lubuntu-64:~$
``` and

```
paul@lubuntu-64:~$ locate "*.ko" | grep 3.12.0-031200rc3-generic |wc -l
3817
paul@lubuntu-64:~$
```

There may be "use single pass kallsyms" changes coming to speed up kbuild (perhaps too late for this cycle):

[http://comments.gmane.org/gmane.linux.kbuild.devel/10450](http://comments.gmane.org/gmane.linux.kbuild.devel/10450)

EDIT: Just in case you're interested, here are the actual modules installed:

```
/lib/modules/3.12.0-rc3-custom2/kernel/arch/x86/kernel/microcode.ko
/lib/modules/3.12.0-rc3-custom2/kernel/crypto/xor.ko
/lib/modules/3.12.0-rc3-custom2/kernel/drivers/acpi/video.ko
/lib/modules/3.12.0-rc3-custom2/kernel/drivers/ata/acard-ahci.ko
/lib/modules/3.12.0-rc3-custom2/kernel/drivers/ata/ahci.ko
/lib/modules/3.12.0-rc3-custom2/kernel/drivers/ata/ahci_platform.ko
/lib/modules/3.12.0-rc3-custom2/kernel/drivers/ata/libahci.ko
/lib/modules/3.12.0-rc3-custom2/kernel/drivers/gpio/gpio-ich.ko
/lib/modules/3.12.0-rc3-custom2/kernel/drivers/gpu/drm/drm.ko
/lib/modules/3.12.0-rc3-custom2/kernel/drivers/gpu/drm/drm_kms_helper.ko
/lib/modules/3.12.0-rc3-custom2/kernel/drivers/gpu/drm/nouveau/nouveau.ko
/lib/modules/3.12.0-rc3-custom2/kernel/drivers/gpu/drm/ttm/ttm.ko
/lib/modules/3.12.0-rc3-custom2/kernel/drivers/hid/hid-logitech.ko
/lib/modules/3.12.0-rc3-custom2/kernel/drivers/hid/hid.ko
/lib/modules/3.12.0-rc3-custom2/kernel/drivers/hid/usbhid/usbhid.ko
/lib/modules/3.12.0-rc3-custom2/kernel/drivers/hwmon/lm90.ko
/lib/modules/3.12.0-rc3-custom2/kernel/drivers/i2c/i2c-core.ko
/lib/modules/3.12.0-rc3-custom2/kernel/drivers/i2c/algos/i2c-algo-bit.ko
/lib/modules/3.12.0-rc3-custom2/kernel/drivers/input/ff-memless.ko
/lib/modules/3.12.0-rc3-custom2/kernel/drivers/mfd/lpc_ich.ko
/lib/modules/3.12.0-rc3-custom2/kernel/drivers/net/ethernet/broadcom/tg3.ko
/lib/modules/3.12.0-rc3-custom2/kernel/drivers/platform/x86/mxm-wmi.ko
/lib/modules/3.12.0-rc3-custom2/kernel/drivers/platform/x86/wmi.ko
/lib/modules/3.12.0-rc3-custom2/kernel/drivers/pps/pps_core.ko
/lib/modules/3.12.0-rc3-custom2/kernel/drivers/ptp/ptp.ko
/lib/modules/3.12.0-rc3-custom2/kernel/drivers/video/output.ko
/lib/modules/3.12.0-rc3-custom2/kernel/drivers/xen/tmem.ko
/lib/modules/3.12.0-rc3-custom2/kernel/drivers/xen/xen-privcmd.ko
/lib/modules/3.12.0-rc3-custom2/kernel/fs/btrfs/btrfs.ko
/lib/modules/3.12.0-rc3-custom2/kernel/kernel/configs.ko
/lib/modules/3.12.0-rc3-custom2/kernel/lib/libcrc32c.ko
/lib/modules/3.12.0-rc3-custom2/kernel/lib/raid6/raid6_pq.ko
/lib/modules/3.12.0-rc3-custom2/kernel/net/ipv4/netfilter/ip_tables.ko
/lib/modules/3.12.0-rc3-custom2/kernel/net/ipv4/netfilter/ipt_REJECT.ko
/lib/modules/3.12.0-rc3-custom2/kernel/net/ipv4/netfilter/iptable_filter.ko
/lib/modules/3.12.0-rc3-custom2/kernel/net/ipv4/netfilter/iptable_nat.ko
/lib/modules/3.12.0-rc3-custom2/kernel/net/ipv4/netfilter/nf_conntrack_ipv4.ko
/lib/modules/3.12.0-rc3-custom2/kernel/net/ipv4/netfilter/nf_defrag_ipv4.ko
/lib/modules/3.12.0-rc3-custom2/kernel/net/ipv4/netfilter/nf_nat_ipv4.ko
/lib/modules/3.12.0-rc3-custom2/kernel/net/netfilter/nf_conntrack.ko
/lib/modules/3.12.0-rc3-custom2/kernel/net/netfilter/nf_conntrack_broadcast.ko
/lib/modules/3.12.0-rc3-custom2/kernel/net/netfilter/nf_conntrack_ftp.ko
/lib/modules/3.12.0-rc3-custom2/kernel/net/netfilter/nf_conntrack_netbios_ns.ko
/lib/modules/3.12.0-rc3-custom2/kernel/net/netfilter/nf_nat.ko
/lib/modules/3.12.0-rc3-custom2/kernel/net/netfilter/nf_nat_ftp.ko
/lib/modules/3.12.0-rc3-custom2/kernel/net/netfilter/x_tables.ko
/lib/modules/3.12.0-rc3-custom2/kernel/net/netfilter/xt_LOG.ko
/lib/modules/3.12.0-rc3-custom2/kernel/net/netfilter/xt_addrtype.ko
/lib/modules/3.12.0-rc3-custom2/kernel/net/netfilter/xt_conntrack.ko
/lib/modules/3.12.0-rc3-custom2/kernel/net/netfilter/xt_limit.ko
/lib/modules/3.12.0-rc3-custom2/kernel/net/netfilter/xt_nat.ko
/lib/modules/3.12.0-rc3-custom2/kernel/net/netfilter/xt_tcpudp.ko
/lib/modules/3.12.0-rc3-custom2/kernel/sound/soundcore.ko
/lib/modules/3.12.0-rc3-custom2/kernel/sound/core/snd-hwdep.ko
/lib/modules/3.12.0-rc3-custom2/kernel/sound/core/snd-page-alloc.ko
/lib/modules/3.12.0-rc3-custom2/kernel/sound/core/snd-pcm.ko
/lib/modules/3.12.0-rc3-custom2/kernel/sound/core/snd-rawmidi.ko
/lib/modules/3.12.0-rc3-custom2/kernel/sound/core/snd-timer.ko
/lib/modules/3.12.0-rc3-custom2/kernel/sound/core/snd.ko
/lib/modules/3.12.0-rc3-custom2/kernel/sound/core/seq/snd-seq-device.ko
/lib/modules/3.12.0-rc3-custom2/kernel/sound/core/seq/snd-seq-midi-event.ko
/lib/modules/3.12.0-rc3-custom2/kernel/sound/core/seq/snd-seq-midi.ko
/lib/modules/3.12.0-rc3-custom2/kernel/sound/core/seq/snd-seq-virmidi.ko
/lib/modules/3.12.0-rc3-custom2/kernel/sound/core/seq/snd-seq.ko
/lib/modules/3.12.0-rc3-custom2/kernel/sound/drivers/snd-virmidi.ko
/lib/modules/3.12.0-rc3-custom2/kernel/sound/pci/hda/snd-hda-codec-analog.ko
/lib/modules/3.12.0-rc3-custom2/kernel/sound/pci/hda/snd-hda-codec-ca0110.ko
/lib/modules/3.12.0-rc3-custom2/kernel/sound/pci/hda/snd-hda-codec-ca0132.ko
/lib/modules/3.12.0-rc3-custom2/kernel/sound/pci/hda/snd-hda-codec-cirrus.ko
/lib/modules/3.12.0-rc3-custom2/kernel/sound/pci/hda/snd-hda-codec-cmedia.ko
/lib/modules/3.12.0-rc3-custom2/kernel/sound/pci/hda/snd-hda-codec-conexant.ko
/lib/modules/3.12.0-rc3-custom2/kernel/sound/pci/hda/snd-hda-codec-hdmi.ko
/lib/modules/3.12.0-rc3-custom2/kernel/sound/pci/hda/snd-hda-codec-idt.ko
/lib/modules/3.12.0-rc3-custom2/kernel/sound/pci/hda/snd-hda-codec-realtek.ko
/lib/modules/3.12.0-rc3-custom2/kernel/sound/pci/hda/snd-hda-codec-si3054.ko
/lib/modules/3.12.0-rc3-custom2/kernel/sound/pci/hda/snd-hda-codec-via.ko
/lib/modules/3.12.0-rc3-custom2/kernel/sound/pci/hda/snd-hda-codec.ko
/lib/modules/3.12.0-rc3-custom2/kernel/sound/pci/hda/snd-hda-intel.ko
```

---

### Post by sammiev on 2013-09-30
So far no issues here. Temps seem to be much the same but good and snappy. :p

---

### Post by VinDSL on 2013-10-01
> **paul_in_london said:**
> [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-rc3-saucy/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-rc3-saucy/)
Drat!

I'm 982 miles away from my +1 box, right now. LoL!  :D

Guess I could try it on this (Peppermint 4 OS / Raring powered) Dell D620.

I'll give it a whirl in the morning, between meetings.  Might solve my AT&T WiFi problem in this hotel...

---

### Post by VinDSL on 2013-10-01
w00t!

Just installed 3.12-rc3 on this laptop, and the wifi is now working.

It was working all across the country, but not at this hotel.

Will little wonders never cease?!?!?!?

EDIT

Man, this is great.  Been running all over the hotel, for 5 hours. 

Every WAP I've run across is connecting now -- zero worked before.

Two thumbs up for 3.12  \\:D/

---

### Post by QDR06VV9 on 2013-10-02
> **VinDSL said:**
> w00t!

Just installed 3.12-rc3 on this laptop, and the wifi is now working.

It was working all across the country, but not at this hotel.

Will little wonders never cease?!?!?!?

EDIT

Man, this is great.  Been running all over the hotel, for 5 hours. 

Every WAP I've run across is connecting now -- zero worked before.

Two thumbs up for 3.12  \\:D/
Nice!!!
Even better for me at least nvidia-325 installed(H@llYEAH!)

---

### Post by fooman on 2013-10-02
yeah!  nvidia drivers are working with 3.12rc3!! 

```
Current Date/Time: Wed Oct  2 17:24:35 EDT 2013
Distro Release: Ubuntu Saucy Salamander (development branch)
Kernel Release: Linux 3.12.0-031200rc3-generic
Gnome Release: GNOME Shell 3.8.4
Unity Release: unity 7.1.1

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce GTX 480/PCIe/SSE2
OpenGL version string:  4.3.0 NVIDIA 325.15
```

---

### Post by rimez on 2013-10-06
@Paul_in_London

Wow. Thanks for the post (#3).  This was the easiest kernel compiling how-to I've seen in a long time. Are there any caveats about this method that users should be aware of (beside no support from Ubuntu of course)? 

Cheers,
Harry in Prague

---

### Post by VinDSL on 2013-10-06
> **paul_in_london said:**
> Have been compiling my own kernel lately in an efffort to keep my system as lean as possible. Even on this old box it's fairly quick, thanks to localmodconfig.
Worked a treat, Paul.

@rimez: Thanks.   I totally missed Paul's post, when I was on the trot, last week.

I quit compiling kernels, some time ago.  The method I was using took around 4 hours on this box -- almost as long as doing security updates on a winders machine. LoL!  :D

I used Linux 3.10.15 as a test.  It was a nail-biter.  I thought I had plenty of space on my root partition, but by the time it completed, I was at 0% (.25 GB remaining).  Whew!

I never did get a 'time' reading, but I judge it took <= an hour.  w00t!

I'm running under Linux 3.10.15 right now...

```
vindsl@Zuul:~$ uname -aLinux Zuul 3.10.15-custom2 #1 SMP Sun Oct 6 10:13:10 MST 2013 i686 i686 i686 GNU/Linux 
```

Can't wait to try it on 3.12-rc4.  ;)

---

### Post by VinDSL on 2013-10-06
BTW, I just created a Gnote file, for safekeeping.

Here's the drill I used.  I'm compiling the kernel & building the debs in /home...

```
# Downloaded tar from this pool: [https://www.kernel.org/pub/linux/kernel/v3.x/ ]("https://www.kernel.org/pub/linux/kernel/v3.x/")

vindsl@Zuul:~$ cd ~/Downloads/Kernels

vindsl@Zuul:~$ tar zxvf ~/Downloads/Kernels/linux-3.10.15.tar.gz

vindsl@Zuul:~$ cd linux-3.10.15

# Copy & paste your .config file here, before running the make commands [paul_in_london]

vindsl@Zuul:~$ make-kpkg clean

vindsl@Zuul:~$ make localmodconfig

vindsl@Zuul:~$ make menuconfig  

# If you get menuconfig errors, make sure libncurses5-dev libncursesw5-dev are installed [VinDSL]

vindsl@Zuul:~$ time fakeroot make-kpkg -j3 --initrd --append-to-version=-vindsl-custom kernel-image kernel-headers
```

---

### Post by paul_in_london on 2013-10-06
> **VinDSL said:**
> Worked a treat, Paul.

@rimez: Thanks.   I totally missed Paul's post, when I was on the trot, last week.

I quit compiling kernels, some time ago.  The method I was using took around 4 hours on this box -- almost as long as doing security updates on a winders machine. LoL!  :D

I used Linux 3.10.15 as a test.  It was a nail-biter.  I thought I had plenty of space on my root partition, but by the time it completed, I was at 0% (.25 GB remaining).  Whew!

I never did get a 'time' reading, but I judge it took <= an hour.  w00t!

I'm running under Linux 3.10.15 right now...

```
vindsl@Zuul:~$ uname -aLinux Zuul 3.10.15-custom2 #1 SMP Sun Oct 6 10:13:10 MST 2013 i686 i686 i686 GNU/Linux 
```

Can't wait to try it on 3.12-rc4.  ;)

Hi Vin,

Wait no longer. :)

Compiling 3.12-rc4 now from here:

[https://www.kernel.org/pub/linux/kernel/v3.x/testing/](https://www.kernel.org/pub/linux/kernel/v3.x/testing/)

Remember to copy your .config file into /usr/src/linux-3.12-rc4 before you run the make commands. Another point is to make yourself a member of the src group (log out and back in for the change to take effect) and then you don't need to compile as root. Or of course just untar somewhere in your home directory and compile there instead.

The debs haven't appeared in ppa kernel mainline yet, but it shouldn't be long...

Cheers,

Paul

EDIT: Ok. Done:

```
...dpkg-deb: building package `linux-headers-3.12.0-rc4-custom' in `../linux-headers-3.12.0-rc4-custom_3.12.0-rc4-custom-10.00.Custom_amd64.deb'.
cp -pf debian/control.dist          debian/control
make[2]: Leaving directory `/usr/src/linux-3.12-rc4'
make[1]: Leaving directory `/usr/src/linux-3.12-rc4'

real	38m7.549s
user	41m24.346s
sys	7m16.676s
paul@lubuntu-64:/usr/src/linux-3.12-rc4$
```

```
paul@lubuntu-64:~$ uname -a
Linux lubuntu-64 3.12.0-rc4-custom #1 SMP Sun Oct 6 22:56:59 BST 2013 x86_64 x86_64 x86_64 GNU/Linux
paul@lubuntu-64:~$
```

---

### Post by VinDSL on 2013-10-06
> **paul_in_london said:**
> Hi Vin,

Wait no longer. :)

Compiling 3.12-rc4 now from here:

[https://www.kernel.org/pub/linux/kernel/v3.x/testing/](https://www.kernel.org/pub/linux/kernel/v3.x/testing/)
Hi Paul,

Thanks for the pointers.  I compiled it in /home this time.  :)

[LIST]
[*]/home had 10GB free
[*]/usr/src had 2GB free
[/LIST]

All's well, that ends well...

```
vindsl@Zuul:~$ uname -a
Linux Zuul 3.12.0-rc4-vindsl #1 SMP Sun Oct 6 17:35:52 MST 2013 i686 i686 i686 GNU/Linux
```

```
vindsl@Zuul:~$
<SNIP>

make[2]: Leaving directory `/home/vindsl/Downloads/Kernels/linux-3.12-rc4'
make[1]: Leaving directory `/home/vindsl/Downloads/Kernels/linux-3.12-rc4'

real	25m26.610s
user	32m45.696s
sys	3m36.172s
```

This is a great way of doing things!

Cheers.  ;)

---

