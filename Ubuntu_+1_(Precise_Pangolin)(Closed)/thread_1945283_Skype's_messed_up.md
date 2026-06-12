---
title: "Skype's messed up"
date: 2012-03-22
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by tehowe on 2012-03-22
So I've been using the latest Skype (beta 2.2) from the .deb file and wish it would work properly. I doubt it's appropriate to file a bug against something that isn't even in the partner repository as of yet... and it would probably be futile to seek out the Skype team since I'm running a beta OS. But I thought I'd raise the flag here and see if anyone else had encountered this issue... 

The first problem, is that it no longer seems to recognize bluetooth devices on Precise the way it did in 10.04 on the netbook before, or on 11.04 on my desktop. No bluetooth for Skype = no good! I can get everything else running through my earpiece but launch skype and it ignores the system sound settings and uses the speaker and netbook microphone. (Default sound in/out settings in Skype)

Second problem, it's also been crashing a lot lately.

No one I know actually uses Jabber, so it would be a Good Thing to get Skype working reliably, or reverse engineer the protocol for FOSS or something... :S Easy for me to say, I'm still working on figuring out hello world level stuff in python hehe

---

### Post by Baldrick_NZ on 2012-03-22
I wonder if the two issues you have are connected?

I don't use bluetooth, and the 2.2 deb file works fine for me.

Maybe try it with a wired head-set and see if that makes any difference? Could be a good starting point.

---

### Post by kostkon on 2012-03-23
> **tehowe said:**
> The first problem, is that it no longer seems to recognize bluetooth devices on Precise the way it did in 10.04 on the netbook before, or on 11.04 on my desktop. No bluetooth for Skype = no good! I can get everything else running through my earpiece but launch skype and it ignores the system sound settings and uses the speaker and netbook microphone. (Default sound in/out settings in Skype)
Could you be more specific? But yeah that's bad, if indeed Skype ignores the default input and output devices that you have set. Have you actually set your bluetooth device as the default input and or output device for your system?

Anyway, the fact is that Skype doesn't really enumerate the devices that PulseAudio has detected, and doesn't really present you with an option to select these devices, thus you have to install the PulseAudio Volume Control utility, start a call in Skype and then manually send the inputs and/or outputs coming from Skype to your bluetooth device. PulseAudio will remember your choices, so you only have to do this once.

Hope that helps.

---

### Post by tehowe on 2012-03-24
> **kostkon said:**
> Could you be more specific? But yeah that's bad, if indeed Skype ignores the default input and output devices that you have set. Have you actually set your bluetooth device as the default input and or output device for your system?

Anyway, the fact is that Skype doesn't really enumerate the devices that PulseAudio has detected, and doesn't really present you with an option to select these devices, thus you have to install the PulseAudio Volume Control utility, start a call in Skype and then manually send the inputs and/or outputs coming from Skype to your bluetooth device. PulseAudio will remember your choices, so you only have to do this once.

Hope that helps.

It appears that bluetooth has slid backwards since then - I can't even get my earpiece to connect now, I suppose I'll go check to see if a bug's been filed for that, 'bluez' is it? I'll revisit this Skype problem once that's dealt with. But, yeah, it sounds like I'll have to use the volume control utility you mention.

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-24
Can you also mention which Computer model you have? Is it a laptop? There is a known issue with Linux kernel and some of bluetooth hardware vendors (Foxconn), used in several laptop models (Acer included).

---

### Post by tehowe on 2012-03-25
> **&#1058 said:**
> Can you also mention which Computer model you have? Is it a laptop? There is a known issue with Linux kernel and some of bluetooth hardware vendors (Foxconn), used in several laptop models (Acer included).

Yes, it's an Acer 1410 Olympic special edition 'netbook', the one with the dual Celeron.

[http://ncix.com/products/?sku=45412](http://ncix.com/products/?sku=45412)

Not sure how to get any better info on the Bluetooth, 'rfkill list' outputs

0: acer-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
6: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

Can't see anything that obviously says 'bluetooth' using lspci -v but assuming it's on the same device as the wifi, that's 

02:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
        Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN
        Flags: bus master, fast devsel, latency 0, IRQ 44
        Memory at d2500000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>
        Kernel driver in use: iwlwifi
        Kernel modules: iwlwifi

Hope that helps!

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-25
I'm a beginner myself, so can't be of much help to you, unfortunately. Since I got my Acer TimelineX 5830, I haven't been able to get Bluetooth working, with or without Skype. Apparently, the Linux 3.2 kernel is missing drivers for Foxconn Bluetooth devices. If I'm not mistaking, this issue wasn't resolved in 3.3 either. There is a solution which requires compiling of Linux kernel, but that's Greek to me.

For more information, please visit this bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/898826](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/898826)

I'm not sure if this is what you're experiencing, but if it is and you manage to solve it, I'd be happy to know how you did it.

---

### Post by tehowe on 2012-03-27
> **&#1058 said:**
> I'm a beginner myself, so can't be of much help to you, unfortunately. Since I got my Acer TimelineX 5830, I haven't been able to get Bluetooth working, with or without Skype. Apparently, the Linux 3.2 kernel is missing drivers for Foxconn Bluetooth devices. If I'm not mistaking, this issue wasn't resolved in 3.3 either. There is a solution which requires compiling of Linux kernel, but that's Greek to me.

For more information, please visit this bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/898826](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/898826)

I'm not sure if this is what you're experiencing, but if it is and you manage to solve it, I'd be happy to know how you did it.

The relevant command is 'lsusb' to list your adapter it turns out. I have a ...

```
Bus 006 Device 002: ID 0a5c:2151 Broadcom Corp. Bluetooth
```

And the bug you were kind enough to refer me too is about not detecting any devices. However there's some discussion of other adapters have similar problems, so looks like this needs more research, yeah. I'll open a bug if it turns out to be justified. Hope it gets fixed! It's kind of a disaster for me if the kernel suddenly doesn't support my bluetooth, and in an LTS release no less, as I use it all the time.

---

### Post by tehowe on 2012-03-28
> **tehowe said:**
> The relevant command is 'lsusb' to list your adapter it turns out. I have a ...

```
Bus 006 Device 002: ID 0a5c:2151 Broadcom Corp. Bluetooth
```And the bug you were kind enough to refer me too is about not detecting any devices. However there's some discussion of other adapters have similar problems, so looks like this needs more research, yeah. I'll open a bug if it turns out to be justified. Hope it gets fixed! It's kind of a disaster for me if the kernel suddenly doesn't support my bluetooth, and in an LTS release no less, as I use it all the time.

Update, my earpiece is connecting again and usb-devices gives more useful information about one's bluetooth adapter.

I've a Broadcom BCM2046. Audio is now choppy and unlistenable, so I've opened a bug [here]("https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/967250") against bluez for those interested.

System audio, though very poor, routes through my bluetooth earpiece but the Skype still routes through the netbook speaker and mic.

---

### Post by tehowe on 2012-04-03
> **tehowe said:**
> Update, my earpiece is connecting again and usb-devices gives more useful information about one's bluetooth adapter.

I've a Broadcom BCM2046. Audio is now choppy and unlistenable, so I've opened a bug [here]("https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/967250") against bluez for those interested.

System audio, though very poor, routes through my bluetooth earpiece but the Skype still routes through the netbook speaker and mic.

System Bluetooth issues have been resolved via updates. Skype still won't recognize the (Broadcom) bluetooth device which otherwise works fine now.

I've since uninstalled (also autoremoved all the 32 bit kruft) and reinstalled Skype using apt-get now that it's shown up in the software centre. It's now presenting me with the TOS page every time and often crashing besides. Sometimes when it tries to report an error it says it can't since the package isn't installed, although I've installed it from the Software Center. *confused*

Maybe I can bribe my friends to convert to Jabber...

---

### Post by tehowe on 2012-04-17
So bluetooth is working well, audio seems to be great. The icon's even been converted to a structured image rather than the blocky bitmap. Nice work, whoever's maintaining this.

The only odd couple of remaining issues I can see are that you have to accept the TOS every time you launch Skype, and then there's the little matter of it slamming syslog with error messages

```
Apr 17 11:34:45 galt kernel: [ 1085.240506] Valid eCryptfs headers not found in file header region or xattr region, inode 5918527
Apr 17 11:34:45 galt kernel: [ 1085.240512] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO
Apr 17 11:34:47 galt kernel: [ 1087.240870] Valid eCryptfs headers not found in file header region or xattr region, inode 5918528
Apr 17 11:34:47 galt kernel: [ 1087.240880] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO
Apr 17 11:34:47 galt kernel: [ 1087.240951] Valid eCryptfs headers not found in file header region or xattr region, inode 5918527
Apr 17 11:34:47 galt kernel: [ 1087.240957] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO
 
```

It just keeps doing that while it's running.

---

### Post by dcordeiro on 2012-04-19
Are you using the 32 or the 64bit version of Ubuntu?
It seems that lots of people are having problems with Skype when using Ubuntu 64bit, even when downloading from the partner repository.

See the bug I have filled in [https://bugs.launchpad.net/ubuntu/+source/skype/+bug/980320](https://bugs.launchpad.net/ubuntu/+source/skype/+bug/980320) (and please mark as affecting you if it is the case) and this thread on the Skype Community forum [http://community.skype.com/t5/Linux/Skype-silently-crashes-on-Ubuntu/td-p/1162](http://community.skype.com/t5/Linux/Skype-silently-crashes-on-Ubuntu/td-p/1162) .

Unfortunately I don't have much hope about getting an official response from Microsoft Skype about their Linux version.

> **tehowe said:**
> So I've been using the latest Skype (beta 2.2) from the .deb file and wish it would work properly. I doubt it's appropriate to file a bug against something that isn't even in the partner repository as of yet... and it would probably be futile to seek out the Skype team since I'm running a beta OS. But I thought I'd raise the flag here and see if anyone else had encountered this issue... 

Second problem, it's also been crashing a lot lately.

No one I know actually uses Jabber, so it would be a Good Thing to get Skype working reliably, or reverse engineer the protocol for FOSS or something... :S Easy for me to say, I'm still working on figuring out hello world level stuff in python hehe

---

### Post by tehowe on 2012-04-19
> **dcordeiro said:**
> Are you using the 32 or the 64bit version of Ubuntu?
It seems that lots of people are having problems with Skype when using Ubuntu 64bit, even when downloading from the partner repository.

See the bug I have filled in [https://bugs.launchpad.net/ubuntu/+source/skype/+bug/980320](https://bugs.launchpad.net/ubuntu/+source/skype/+bug/980320) (and please mark as affecting you if it is the case) and this thread on the Skype Community forum [http://community.skype.com/t5/Linux/Skype-silently-crashes-on-Ubuntu/td-p/1162](http://community.skype.com/t5/Linux/Skype-silently-crashes-on-Ubuntu/td-p/1162) .

Unfortunately I don't have much hope about getting an official response from Microsoft Skype about their Linux version.

It's 64bit. I don't think that's the same issue as my Skype is working for the most part now. But a lot of wierd stuff, regressions etc, has definitely been going on as Precise libraries get upgraded around it I guess.

---

