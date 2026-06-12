---
title: "kvm-72 packages for gutsy, hardy and intrepid available"
date: 2008-08-01
forum: Virtualisation
---

### Post by IntuitiveNipple on 2008-08-01
I've just built a set of packages for kvm-72. They include support for VDE (Virtual Distributed Ethernet) and the new kvm/qemu audio configuration options. They are [available from my PPA](https://edge.launchpad.net/~intuitivenipple/+archive).

If you would like to test them and provide feedback... :)

To install them, either add my PPA to your apt sources or download the .deb files directly from my PPA
```

$ sudo sh -c "echo 'deb http://ppa.launchpad.net/intuitivenipple/ubuntu $(lsb_release -sc) main' >/etc/apt/sources.list.d/intuitivenipple.list"
$ sudo apt-get update

$sudo apt-get install kvm

```
Changelog for Intrepid and Hardy:
```

kvm (1:72+dfsg-0ubuntu1~ppa1h) hardy; urgency=low

  * New upstream release
    - Update upstream changelog
    - Add patches (90_ & 91_) to support configuring audio devices and pass-
       through of options to qemu/configure from ./configure.
    - Added patch (92_) to report qemu/configure arguments, but left inactive
       (not listed in quilt's debian/patches/series). This is related to the
       diagnosing of the problems fixed by 90_ and 91_).
    - debian/rules: re-order clean: make ... calls (fixes config.mak being
       needed after it was deleted by qemu/Makefile).
    - debian/rules: add missing make vgabios clean (fixes biossums failures
       due to previously built binary remaining - which can be for a different
       architecture).
    - debian/rules: re-order clean: 'rm' after qemu distclean not before
       (fixes clean failure due to qemu/$(BUILD_CPU)-softmmu missing).
    - debian/rules: conditionally execute clean: for qemu and kvm only if
       config.mak exists. (fixes failure of debian/rules clean on
       already-clean directory).
    - debian/rules: Configure to support VDE.
    - debian/rules: Configure to support mixemu.
    - debian/rules: Configure to support audio cards (ac97 adlib cs4231a gus).
    - debian/rules: Configure to support audio drivers (oss alsa esd pa).
    - debian/control: Add Build-Depends libpulse-dev, libesd0-dev, libvdeplug2-dev.
    - debian/rules: Add ppc_rom.bin to needed_bios_files for powerpc target.
    - Build-Depend on "sysv-rc (>= 2.86.ds1-14.1ubuntu2)" to accomodate
      TearDown.
    - debian/control: Suggest ubuntu-vm-builder instead of debootstrap.

 -- TJ <ubuntu@tjworld.net>   Fri, 1 Aug 2008 00:04:00 +0100

```
Changelog for Gutsy:
```

kvm (1:72+dfsg-0ubuntu1~ppa1g) gutsy; urgency=low

  * New upstream release
    - Update upstream changelog
    - Add patches (90_ & 91_) to support configuring audio devices and pass-
       through of options to qemu/configure from ./configure.
    - Added patch (92_) to report qemu/configure arguments, but left inactive
       (not listed in quilt's debian/patches/series). This is related to the
       diagnosing of the problems fixed by 90_ and 91_).
    - debian/rules: re-order clean: make ... calls (fixes config.mak being
       needed after it was deleted by qemu/Makefile).
    - debian/rules: add missing make vgabios clean (fixes biossums failures
       due to previously built binary remaining - which can be for a different
       architecture).
    - debian/rules: re-order clean: 'rm' after qemu distclean not before
       (fixes clean failure due to qemu/$(BUILD_CPU)-softmmu missing).
    - debian/rules: conditionally execute clean: for qemu and kvm only if
       config.mak exists. (fixes failure of debian/rules clean on
       already-clean directory).
    - debian/rules: Configure to support VDE.
    - debian/rules: Configure to support mixemu.
    - debian/rules: Configure to support audio cards (ac97 adlib cs4231a gus).
    - debian/rules: Configure to support audio drivers (oss alsa esd).
    - debian/control: Add Build-Depends libpulse-dev, libesd0-dev, libvdeplug2-dev.
    - debian/rules: Add ppc_rom.bin to needed_bios_files for powerpc target.
    - Build-Depend on "sysv-rc (>= 2.86.ds1-14.1ubuntu2)" to accomodate
      TearDown.

 -- TJ <ubuntu@tjworld.net>   Fri, 1 Aug 2008 00:04:00 +0100

```

---

### Post by samiux on 2008-08-01
I just installed kvm-72.  However, I don't know how to configure the sound device.  I am running Ubuntu 8.04.1.

---

### Post by IntuitiveNipple on 2008-08-01
The available audio options are reported by:
```

$ kvm -audio-help
Audio options:
  QEMU_AUDIO_DAC_FIXED_SETTINGS: boolean, default = 1
    Use fixed settings for host DAC
  QEMU_AUDIO_DAC_FIXED_FREQ: integer, default = 44100
    Frequency for fixed host DAC
  QEMU_AUDIO_DAC_FIXED_FMT: format, default = S16, (one of: U8 S8 U16 S16 U32 S32)
    Format for fixed host DAC
  QEMU_AUDIO_DAC_FIXED_CHANNELS: integer, default = 2
    Number of channels for fixed DAC (1 - mono, 2 - stereo)
  QEMU_AUDIO_DAC_VOICES: integer, default = 1
    Number of voices for DAC
  QEMU_AUDIO_ADC_FIXED_SETTINGS: boolean, default = 1
    Use fixed settings for host ADC
  QEMU_AUDIO_ADC_FIXED_FREQ: integer, default = 44100
    Frequency for fixed host ADC
  QEMU_AUDIO_ADC_FIXED_FMT: format, default = S16, (one of: U8 S8 U16 S16 U32 S32)
    Format for fixed host ADC
  QEMU_AUDIO_ADC_FIXED_CHANNELS: integer, default = 2
    Number of channels for fixed ADC (1 - mono, 2 - stereo)
  QEMU_AUDIO_ADC_VOICES: integer, default = 1
    Number of voices for ADC
  QEMU_AUDIO_TIMER_PERIOD: integer, default = 0
    Timer period in HZ (0 - use lowest possible)
  QEMU_AUDIO_PLIVE: boolean, default = 0
    (undocumented)
  QEMU_AUDIO_LOG_TO_MONITOR: boolean, default = 0
    print logging messages to monitor instead of stderr

Available drivers:
Name: oss
Description: OSS http://www.opensound.com
Theoretically supports many playback voices
Theoretically supports many capture voices
Options:
  QEMU_OSS_FRAGSIZE: integer, default = 4096
    Fragment size in bytes
  QEMU_OSS_NFRAGS: integer, default = 4
    Number of fragments
  QEMU_OSS_MMAP: boolean, default = 0
    Try using memory mapped access
  QEMU_OSS_DAC_DEV: string, default = /dev/dsp
    Path to DAC device
  QEMU_OSS_ADC_DEV: string, default = /dev/dsp
    Path to ADC device
  QEMU_OSS_DEBUG: boolean, default = 0
    Turn on some debugging messages

Name: alsa
Description: ALSA http://www.alsa-project.org
Theoretically supports many playback voices
Theoretically supports many capture voices
Options:
  QEMU_ALSA_DAC_SIZE_IN_USEC: boolean, default = 0
    DAC period/buffer size in microseconds (otherwise in frames)
  QEMU_ALSA_DAC_PERIOD_SIZE: integer, default = 0
    DAC period size (0 to go with system default)
  QEMU_ALSA_DAC_BUFFER_SIZE: integer, default = 1024
    DAC buffer size (0 to go with system default)
  QEMU_ALSA_ADC_SIZE_IN_USEC: boolean, default = 0
    ADC period/buffer size in microseconds (otherwise in frames)
  QEMU_ALSA_ADC_PERIOD_SIZE: integer, default = 0
    ADC period size (0 to go with system default)
  QEMU_ALSA_ADC_BUFFER_SIZE: integer, default = 0
    ADC buffer size (0 to go with system default)
  QEMU_ALSA_THRESHOLD: integer, default = 0
    (undocumented)
  QEMU_ALSA_DAC_DEV: string, default = default
    DAC device name (for instance dmix)
  QEMU_ALSA_ADC_DEV: string, default = default
    ADC device name
  QEMU_ALSA_VERBOSE: boolean, default = 0
    Behave in a more verbose way

Name: esd
Description: http://en.wikipedia.org/wiki/Esound
Theoretically supports many playback voices
Theoretically supports many capture voices
Options:
  QEMU_ESD_SAMPLES: integer, default = 1024
    buffer size in samples
  QEMU_ESD_DIVISOR: integer, default = 2
    threshold divisor
  QEMU_ESD_DAC_HOST: string, default = (not set)
    playback host
  QEMU_ESD_ADC_HOST: string, default = (not set)
    capture host

Name: pa
Description: http://www.pulseaudio.org/
Theoretically supports many playback voices
Theoretically supports many capture voices
Options:
  QEMU_PA_SAMPLES: integer, default = 1024
    buffer size in samples
  QEMU_PA_DIVISOR: integer, default = 2
    threshold divisor
  QEMU_PA_SERVER: string, default = (not set)
    server address
  QEMU_PA_SINK: string, default = (not set)
    sink device name
  QEMU_PA_SOURCE: string, default = (not set)
    source device name

Name: none
Description: Timer based audio emulation
Theoretically supports many playback voices
Theoretically supports many capture voices
No options

Name: wav
Description: WAV renderer http://wikipedia.org/wiki/WAV
One playback voice
Does not support capture
Options:
  QEMU_WAV_FREQUENCY: integer, default = 44100
    Frequency
  QEMU_WAV_FORMAT: format, default = S16, (one of: U8 S8 U16 S16 U32 S32)
    Format
  QEMU_WAV_DAC_FIXED_CHANNELS: integer, default = 2
    Number of channels (1 - mono, 2 - stereo)
  QEMU_WAV_PATH: string, default = qemu.wav
    Path to wave file

Options are settable through environment variables.
Example:
  export QEMU_AUDIO_DRV=wav
  export QEMU_WAV_PATH=$HOME/tune.wav
(for csh replace export with setenv in the above)
  qemu ...

```
To get the supported sound cards:
```

$ kvm -soundhw ?
Valid sound card names (comma separated):
pcspk       PC speaker
sb16        Creative Sound Blaster 16
cs4231a     CS4231A
adlib       Yamaha YM3812 (OPL2)
gus         Gravis Ultrasound GF1
ac97        Intel 82801AA AC97 Audio
es1370      ENSONIQ AudioPCI ES1370

```
See the [local QEMU Manual]("file:///usr/share/doc/kvm/qemu-doc.html") for how to select them.

Check the[ Qemu forums]("http://qemu-forum.ipi.fi/index.php") for lots of useful advice on using kvm/qemu.

VDE networking is supported directly now so it doesn't have to be wrapped using vdeq any more.

---

### Post by samiux on 2008-08-01
I am using virt-manager.  How can I configure the sound with it?  I am a newbie, thanks.

By the way, the number pad does not work in the guest also.

---

### Post by IntuitiveNipple on 2008-08-02
> **samiux said:**
> I am using virt-manager.  How can I configure the sound with it?  I am a newbie, thanks.


Unfortunately virt-manager is reliant upon [libvirt0](http://libvirt.org/) for managing and monitoring virtual machines through a standard API.

libvirt is still very much a work-in-progress and its standard XML configuration doesn't appear to support configuring of devices in the way that the QEMU/KVM hypervisors allow.

I launch VMs from links in the Applications > Virtual Machines menu that I've created myself. The links execute simple shell scripts that launch a fully configured Virtual Machine.

The scripts use [qemuctl](http://qemuctl.sourceforge.net/) to provide simple GUI VM management if necessary.

The host runs a VDE (Virtual Distributed Ethernet) network interface (kvm0) with dnsmasq bound to it providing DNS and DHCP services. The interface is then connected to the LAN (and outside world) with a netfilters MASQUERADE rule added using iptables when the interface starts.

An example start-up script (uses the qemuctl GUI) that uses ALSA sound and VDE networking:
```

#!/bin/bash
export QEMU_AUDIO_DRV=alsa
qemuctl -qemu kvm -name WindowsXP-SP2 -boot c -m 768 -std-vga \
 -hda /media/mobile120/home/all/VirtualMachines/WindowsXP-SP2.ovl \
 -cdrom '/dev/cdrom' -k en-gb -serial /dev/ttyUSB0 -soundhw es1370 -usb \
 -net nic,model=rtl8139,macaddr=56:44:45:30:31:32,vlan=0 \
 -net vde,sock=/var/run/kvm0.ctl,vlan=0 \
 $@

```

---

### Post by IntuitiveNipple on 2008-08-02
Before I forget the last year's experiences in configuring and using VDE with VMs I have documented how it is done in my Wiki, in the article "[Virtual Machines With VDE Networking]("http://tjworld.net/wiki/Linux/Ubuntu/VirtualMachinesWithVDENetworking")"

I hope it is useful for others trying to get the best configuration for network development and testing.

---

### Post by nzgreen on 2009-01-12
Sorry for re-opening this old thread, but I just wanted to report that I have enabled sound in a Windows VM using virsh (not virt-manager) using this directive in the config:
<sound model='es1370' />

---

