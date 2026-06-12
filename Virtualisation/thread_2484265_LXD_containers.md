---
title: "LXD containers"
date: 2023-02-21
forum: Virtualisation
---

### Post by demonenero84 on 2023-02-21
With the help of this guide [https://ubuntuforums.org/showthread.php?t=2438709](https://ubuntuforums.org/showthread.php?t=2438709) I made a container (ubuntu:18.04) to run gui apps. It runs great even if I had to use nvidia open source drivers, I can watch 1080p60 videos on youtube (dropping more or less 1% frames) with perfect audio.
I tried to make another container (ubuntu:22.04), everything looks fine until I get this message
[ATTACH=CONFIG]291822[/ATTACH]
I can install firefox and run it, however I cannot get the audio working
Any suggestions ?
Here are my specs

[FONT=monospace][COLOR=#5454ff]**OS**[/COLOR][COLOR=#000000]: Kubuntu 22.04.1 LTS x86_64[/COLOR]
[/FONT][FONT=monospace][COLOR=#5454ff]**CPU**[/COLOR][COLOR=#000000]: Intel i5-7400 (4) @ 3.500GHz[/COLOR]
[/FONT][FONT=monospace][COLOR=#5454ff]**GPU**[/COLOR][COLOR=#000000]: NVIDIA GeForce GTX 1050 [/COLOR]
[/FONT][FONT=monospace][COLOR=#000000]lxd version [/COLOR]5.10
[/FONT][FONT=monospace][COLOR=#000000]lxc [/COLOR]Client version: 5.10
[/FONT]
thanks a lot in advance

---

### Post by TheFu on 2023-02-22
check the system log files.

---

### Post by demonenero84 on 2023-02-22
thanks a lot for the reply
I will check system logs of my pc and container. But I think to test everything inside a vm since I do not want to use open source drivers

---

### Post by DuckHook on 2023-02-22
LXD in Ubuntu 22.04 has made audio more difficult. For some reason, it does not set the PulseAudio cookie properly in the default /home location. You need to work around this limitation by setting the cookie in some system directory. I have chosen to do so under the /var directory, so my new x11 profile looks like this:```
config:
  environment.DISPLAY: :0
  environment.PULSE_SERVER: unix:/var/pulse-native
  user.user-data: |
    #cloud-config
    runcmd:
      - 'sed -i "s/; enable-shm = yes/enable-shm = no/g" /etc/pulse/client.conf'
    packages:
      - x11-apps
      - mesa-utils
      - pulseaudio
    write_files:
      - owner: root:root
        permissions: '0644'
        append: true
        content: |
          PULSE_SERVER=unix:/var/pulse-native
        path: /etc/environment
description: GUI LXD profile
devices:
  PASocket1:
    bind: container
    connect: unix:/run/user/1000/pulse/native
    gid: "1000"
    listen: unix:/var/pulse-native
    mode: "0777"
    security.gid: "1000"
    security.uid: "1000"
    type: proxy
    uid: "1000"
  X1:
    bind: container
    connect: unix:@/tmp/.X11-unix/X0
    listen: unix:@/tmp/.X11-unix/X0
    security.gid: "1000"
    security.uid: "1000"
    type: proxy
  mygpu:
    type: gpu
name: x11
used_by:
```
I shall update my tutorial to include the new workaround.

It is also important to note that things will change yet again after 22.04. Jammy will be the last version to use Pulse Audio. All future versions will use pipewire. I haven't even started experimenting with pipewire yet. Moral of the story is: if you want to use the instructions in my tutorial, it is unlikely to work past 22.04

Forum housekeeping:

I've moved your thread to the "Virtualisation" subforum for a better fit with the subject matter.

---

### Post by demonenero84 on 2023-02-22
Now I get these errors in my vm
```

Feb 22 18:02:57 virt-Standard-PC-Q35-ICH9-2009 tracker-extract[6881]: Task for 'file:///usr/share/applications/io.snapcraft.SessionAgent.desktop.dpkg-new' finished with error: Error when getting information for file \u201c/usr/share/applications/io.snapcraft.SessionAgent.desktop.dpkg-new\u201d: No such file or directory
Feb 22 18:02:57 virt-Standard-PC-Q35-ICH9-2009 tracker-extract[6881]: Task for 'file:///usr/share/applications/io.snapcraft.SessionAgent.desktop.dpkg-tmp' finished with error: Error when getting information for file \u201c/usr/share/applications/io.snapcraft.SessionAgent.desktop.dpkg-tmp\u201d: No such file or directory
Feb 22 18:02:57 virt-Standard-PC-Q35-ICH9-2009 tracker-extract[6881]: Task for 'file:///usr/share/applications/snap-handle-link.desktop.dpkg-new' finished with error: Error when getting information for file \u201c/usr/share/applications/snap-handle-link.desktop.dpkg-new\u201d: No such file or directory
Feb 22 18:02:57 virt-Standard-PC-Q35-ICH9-2009 tracker-extract[6881]: Task for 'file:///usr/share/applications/snap-handle-link.desktop.dpkg-tmp' finished with error: Error when getting information for file \u201c/usr/share/applications/snap-handle-link.desktop.dpkg-tmp\u201d: No such file or directory
Feb 22 18:04:04 virt-Standard-PC-Q35-ICH9-2009 systemd[1]: Condition check resulted in Process error reports when automatic reporting is enabled (file watch) being skipped.
Feb 22 18:04:04 virt-Standard-PC-Q35-ICH9-2009 systemd[1]: Condition check resulted in Process error reports when automatic reporting is enabled (timer based) being skipped.
Feb 22 18:06:00 virt-Standard-PC-Q35-ICH9-2009 systemd[1]: Condition check resulted in Process error reports when automatic reporting is enabled (file watch) being skipped.
Feb 22 18:06:00 virt-Standard-PC-Q35-ICH9-2009 systemd[1]: Condition check resulted in Process error reports when automatic reporting is enabled (timer based) being skipped.
Feb 22 18:06:00 virt-Standard-PC-Q35-ICH9-2009 udisksd[548]: Error probing device: Error sending ATA command IDENTIFY PACKET DEVICE to '/dev/sr0': Unexpected sense data returned:#0120000: 70 00 05 00  00 00 00 0a  00 58 00 01  21 04 00 00    p........X..!...#0120010: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00    ................#012 (g-io-error-quark, 0)

```
and these inside my vm's container
```

Feb 22 17:20:03 icefox udevadm[71]: hardware_error_device: Failed to write 'add' to '/sys/bus/acpi/drivers/hardware_error_device/uevent': Permission denied
Feb 22 17:21:37 icefox udevadm[81]: hardware_error_device: Failed to write 'add' to '/sys/bus/acpi/drivers/hardware_error_device/uevent': Permission denied
Feb 22 17:22:41 icefox mount[864]: mount: /var/snap/firefox/common/host-hunspell: filesystem was mounted, but any subsequent operation failed: Unknown error 5005.

```

---

### Post by demonenero84 on 2023-02-22
thanks a lot I tried using the new profile you posted, unfortunately I cannot get the audio to work (I get the same error message).

---

### Post by DuckHook on 2023-02-22
[LIST=1]
[*]Try restarting the container. Also, try rebooting your host.
[*]From within container, please post results of:```
pactl info
```You may need to do this two or three times to get any output.
[*]Audio may be problematic in Firefox because FF is now a snap. I don't use snap version of FF in my containers. Instead, I use the ESR version from the Mozilla Team PPA.
[*]Sometimes, for reasons unknown, my FF fails to produce sound unless I shut it down, then relaunch. Not often, but sometimes, I need to stop/start the container too.
[*]Wait about a minute after a restart before launching FF.
[/LIST]

---

### Post by DuckHook on 2023-02-22
> **demonenero84 said:**
> thanks a lot I tried using the new profile you posted, unfortunately I cannot get the audio to work (I get the same error message).
The error message that you show ought to have nothing to do with Pulseaudio, but stranger dependencies have reared their heads before, so ¯\_(&#12484;)_/¯

It's up to you, but I disable unattended upgrades altogether. I don't like any process that "automatically" monkeys around with the most important parts of my OS. Of course, if you decide to do so, you will need to adopt the habit of routinely instigating upgrades manually. Otherwise, you negate the very security that you are trying to enhance in the first place through the use of containers.

---

### Post by demonenero84 on 2023-02-22
thanks a lot :)
so if I install firefox as a deb Package the audio still does not work, however if a install mpv and play a mp3 file it works :guitar:
here is the output for pactl info
```

root@firefox:/# pactl info
Server String: unix:/var/pulse-native
Library Protocol Version: 35
Server Protocol Version: 35
Is Local: yes
Client Index: 27
Tile Size: 65472
User Name: virt
Host Name: virt-Standard-PC-Q35-ICH9-2009
Server Name: pulseaudio
Server Version: 15.99.1
Default Sample Specification: s16le 2ch 44100Hz
Default Channel Map: front-left,front-right
Default Sink: alsa_output.pci-0000_00_1b.0.analog-stereo
Default Source: alsa_input.pci-0000_00_1b.0.analog-stereo
Cookie: 3078:0ee3


```
thanks :)

---

### Post by DuckHook on 2023-02-22
> **demonenero84 said:**
> …so if I install firefox as a deb Package the audio still does not work, however if a install mpv and play a mp3 file it works…
Your audio obviously works. Both pactl and your own experiment with mpv demonstrate this. The problem is restricted to FF. The good news is that the LXD setup is fine. Nothing wrong with that. The bad news is that snap FF is problematic. But that is a solvable problem.

Unless you add the PPA and install the ESR version of FF, you cannot install a deb version of FF in 22.04. What you think is a deb package is actually just a stub that installs the snap version. Many forum threads have been devoted to the problems with snap FF and I think you have just found another one. Note that what you (and I) are doing—using LXD to run FF— constitutes an edge case that very few others are doing. There are a few ways to work around the problem:

[LIST=1]
[*]Download the standalone version of FF from the Mozilla site and install that. This is the simplest solution and the one recommended by many old timers on these forums.
[*]Add the Mozilla Team PPA to your container and then install the ESR version of FF. This is what I do. I don't need the latest version of FF and the ESR version tends to be more stable anyways. I prefer this workaround at least in part because it also gives me the latest version of TBird, which the Ubuntu repos do not, so it's a double win as far as I'm concerned.
[*]Same as above, but reconfigure your container's apt settings to give precedence to the Mozilla Team PPA over the Canonical repos. If you do that, you can install the latest FF because the Mozilla Team PPA actually has the latest version (it just gets clobbered by the snap version unless you take those special measures).
[/LIST]
You can find instructions for all of the above using a websearch, but if you have trouble, just post back with whichever of the above that you choose and we will try to help.

---

### Post by demonenero84 on 2023-02-22
> **DuckHook said:**
> 
 What you think is a deb package is actually just a stub that installs the snap version.

Indeed I thought that I was using a deb package :oops: the standalone version of FF from the Mozilla site works fine with audio :guitar:
I guess this makes the thread solved, thanks a lot and one more thing, [https://stgraber.org/](https://stgraber.org/) is a nice way to start learning about LXD, do you have any other suggestions

thanks a lot

---

### Post by DuckHook on 2023-02-22
> **demonenero84 said:**
> Indeed I thought that I was using a deb package :oops: the standalone version of FF from the Mozilla site works fine with audio :guitar:
I guess this makes the thread solved, thanks a lot and one more thing, [https://stgraber.org/](https://stgraber.org/) is a nice way to start learning about LXD, do you have any other suggestions

thanks a lot
Stephane Graber is the lead developer of LXD. Yes, his site is awesome.

Simos Xenitellis's site is another. I gather that Simos is another on the LXD team, but I don't know for sure: [https://blog.simos.info/](https://blog.simos.info/)
Simos's site gives lots of practical step&#8209;by&#8209;step howtos, although he hasn't updated them for some time.

The general LXD site is here: [https://linuxcontainers.org/](https://linuxcontainers.org/)
It has a forum/discussion section that holds a lot of really good stuff, though you will have to go looking for the gems hidden deep inside. From time to time, you will find me on it.

---

### Post by demonenero84 on 2023-02-22
thanks for the advice:P

---

### Post by DuckHook on 2023-02-22
Good Luck and Happy Ubuntu-ing.

---

