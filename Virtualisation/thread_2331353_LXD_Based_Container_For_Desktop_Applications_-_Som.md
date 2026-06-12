---
title: "LXD Based Container For Desktop Applications - Some Success - Help (need more)"
date: 2016-07-21
forum: Virtualisation
---

### Post by redger on 2016-07-21
I'm trying to use an LXD based  container to run desktop applications on my standard desktop, in much the same way as this
[https://www.stgraber.org/2014/02/09/lxc-1-0-gui-in-containers/](https://www.stgraber.org/2014/02/09/lxc-1-0-gui-in-containers/)
I know about, and use firejail, but like to use this method for operational reasons. I feel the solution is so close .. I'm just missing something to make it work.
I can run a complete session via X2Go or VNC (tigervnc if you want to run Unity or KDE.... but any VNC for Mate, LXDE etc) .. but this is NOT what I want for my intended use case (i want the appearance of desktop integration)

So far I can run an application in a Xephyr screen (essentially an X "subscreen") but not on the host desktop (ultimate aim). Xephy afaik is X avvess on a subscreen, so if this works, why doesn't access to the host screen (DISPLAY=:0 or DISPLAY=:0.0) ?

For a Xephyr screen
1) Install Xephyr
2) run Xephyr with "Xephyr -a -br -noreset -name xephyr_screen_101 -title Browse_Danger -screen 1800x1080 :101"
3) log into the container and run the program, directing output to display 101 ie.
   a) lxc exec <container-name> bash
   b) DISPLAY=:101 firefox
4) Firefox will duly appear on the Xephyr screen

To run this from outside the container
1) Create shell program inside the container, containing just the command in 3b ie.
   #!/bin/bash
   DISPLAY=:101 firefox
2) Make the program executable ie. chmod ug+x <shell-program-above> and possibly change ownership
2) Execute with
   lxc exec <container-name> su <user name> -- <shell-program-above>

The minimum config required to make this work seems to be

    ```

    withname: <container-name>
    profiles:
    - default
    config:
     raw.lxc: lxc.aa_profile=lxc-container-default-with-mounting
    devices:
     root:
       path: /
       type: disk
     x11-unix:
       path: /tmp/.X11-unix
       source: /tmp/.X11-unix
       type: disk
    ephemeral: false
```


by adding a few more mounts we can get a full desktop for user = <user> to run in Xephyr eg.

    ```
 
    devices:
      dri:
        path: /dev/dri
        source: /dev/dri
        type: disk
      iceauthority-<user>:
        path: /home/<user>/.ICEauthority
        source: /home/<user>/.ICEauthority
        type: disk
      root:
        path: /
        type: disk
      x11-unix:
        path: /tmp/.X11-unix
        source: /tmp/.X11-unix
        type: disk
      xauthority-<user>:
        path: /home/<user>/.Xauthority
        source: /home/<user>/.Xauthority
        type: disk
    ephemeral: false
```

Obviously we needed to have added <user> first and ensure the home directory was created (should be created when using "adduser") and then run the desktop whilst logged in as <user>

No matter what I do I cannot get a program to display on the host screen eg. DISPLAY=:0 firefox. This return an error message

   ```
 
    $ DISPLAY=:0 firefox
    No protocol specified
    Failed to connect to Mir: Failed to connect to server socket: No such file or directory
    Unable to init server: Could not connect: Connection refused
    Error: cannot open display: :0
```

These messages turn up in the host dmesg ... but I'm a bit suspicious of the apparmor messages, they may be red herrings (should I be?)

  ```
  
    508499.335953] audit: type=1400 audit(1469067007.731:3225): apparmor="STATUS" operation="profile_load" profile="unconfined" name="lxd-xenial-browse-danger-test_</var/lib/lxd>" pid=29368 comm="apparmor_parser"
    [508499.342613] device vethO9YPDN entered promiscuous mode
    [508499.342650] IPv6: ADDRCONF(NETDEV_UP): vethO9YPDN: link is not ready
    [508499.385405] eth0: renamed from vethE393S7
    [508499.408826] IPv6: ADDRCONF(NETDEV_CHANGE): vethO9YPDN: link becomes ready
    [508499.408877] lxcbr0: port 4(vethO9YPDN) entered forwarding state
    [508499.408886] lxcbr0: port 4(vethO9YPDN) entered forwarding state
    [508499.438414] audit: type=1400 audit(1469067007.835:3226): apparmor="DENIED" operation="mount" info="failed type match" error=-13 profile="lxc-container-default-with-mounting" name="/sys/fs/cgroup/systemd/" pid=29377 comm="systemd" fstype="cgroup" srcname="cgroup" flags="rw, nosuid, nodev, noexec"
    [508499.438529] audit: type=1400 audit(1469067007.835:3227): apparmor="DENIED" operation="mount" info="failed type match" error=-13 profile="lxc-container-default-with-mounting" name="/sys/fs/cgroup/systemd/" pid=29377 comm="systemd" fstype="cgroup" srcname="cgroup" flags="rw, nosuid, nodev, noexec"
    [508514.445340] lxcbr0: port 4(vethO9YPDN) entered forwarding state
```

and from the host Syslog

    ```

    Jul 21 12:10:07 virt-host kernel: [508499.438414] audit: type=1400 audit(1469067007.835:3226): apparmor="DENIED" operation="mount" info="failed type match" error=-13 profile="lxc-container-default-with-mounting" name="/sys/fs/cgroup/systemd/" pid=29377 comm="systemd" fstype="cgroup" srcname="cgroup" flags="rw, nosuid, nodev, noexec"
    Jul 21 12:10:07 virt-host kernel: [508499.438529] audit: type=1400 audit(1469067007.835:3227): apparmor="DENIED" operation="mount" info="failed type match" error=-13 profile="lxc-container-default-with-mounting" name="/sys/fs/cgroup/systemd/" pid=29377 comm="systemd" fstype="cgroup" srcname="cgroup" flags="rw, nosuid, nodev, noexec"
```

If I then change the apparmor profile to unconfined and re-run, I see the following in the host dmesg

    ```

    [508796.382044] audit: type=1400 audit(1469067304.766:3230): apparmor="DENIED" operation="open" profile="/usr/sbin/cupsd" name="/etc/ld.so.preload" pid=5259 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
    [508796.395527] audit: type=1400 audit(1469067304.782:3231): apparmor="DENIED" operation="open" profile="/usr/sbin/cupsd" name="/etc/ld.so.preload" pid=5266 comm="cups-exec" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
    [508796.395578] audit: type=1400 audit(1469067304.782:3232): apparmor="DENIED" operation="open" profile="/usr/sbin/cupsd" name="/etc/ld.so.preload" pid=5265 comm="cups-exec" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
    [508796.395778] audit: type=1400 audit(1469067304.782:3233): apparmor="DENIED" operation="open" profile="/usr/sbin/cupsd" name="/etc/ld.so.preload" pid=5265 comm="dbus" requested_mask="r" denied_mask="r" fsuid=7 ouid=0
    [508796.398616] audit: type=1400 audit(1469067304.782:3234): apparmor="DENIED" operation="open" profile="/usr/sbin/cupsd" name="/etc/ld.so.preload" pid=5266 comm="dbus" requested_mask="r" denied_mask="r" fsuid=7 ouid=0
```

It's worth noting that the legacy LXC approach outlined in the first link above still works on this host (so I have a legacy style lxc container which works). The legacy style config is notably different in its id maps

   ```
 
    lxc.id_map = u 0 100000 1000
    lxc.id_map = g 0 100000 1000
    lxc.id_map = u 1000 1000 1
    lxc.id_map = g 1000 1000 1
    lxc.id_map = u 1001 101001 64535
    lxc.id_map = g 1001 101001 64535

```
vs the default.
If I try to use the above map, the container won't start. I can use the following map (created a new profile and then created the test container using that profile + default)  and it will start, but doesn't address the access problem

   ```
 
    lxc.id_map = u 400000 1000 1
    lxc.id_map = g 400000 1000 1
```

I also tried adding

   ```
 
    lxc.id_map = u 1001 401001 64535
    lxc.id_map = g 1001 401001 64535
```

But that didn't help and the 1000 1000 mapping prevented the container from starting
It seems odd that Xephyr screens are painted ok but the host screen :0 isn't .... And if it's an apparmor problem, how come "unconfined" is confining it ?

DOES ANYONE HAVE ANY INSIGHTS SUGGESTIONS ?

---

### Post by TheFu on 2016-07-21
TL;DR .... check out **firejail**. Makes it trivial to run apps, including GUIs in a different container.  Wasn't in 14.04, but was available in 16.04.

---

### Post by redger on 2016-07-21
thanks Fu,
as noted I know of and use Firejail (see line 3 in initial note). This use case requires more than Firejail offers

I've also successfully used X2Go and TigerNVC. 
I tried Spice (unsuccessfully so far).

---

### Post by DuckHook on 2017-01-29
I realize this is borderline necroposting but the OP's question remains relevant and topical, and the answers out there are both exceedingly obscure and arcane.

The main issues are these:

[LIST=1]
[*]So far, almost all of the tutorials/user guides for LXD have been geared to a CLI server environment, since LXD's main application up to now has been massive industrial-scale usages like cloud computing.
[*]But there is a very big need (and case) for use of LXD on the desktop.
[*]It is especially useful for isolating/containing/sandboxing GUI apps on machines not powerful enough to run VMs.
[*]Moreover, because it runs at bare metal speed and efficiency, it is superior to VMs in so many other respects.
[*]Ideally, one could run LXD-contained apps with the appearance of native desktop apps instead of boxed into a remote desktop window.
[*]
[/LIST]
After days of Googling and experimenting, I've cobbled together the steps needed to implement what @redger set out to do:

[LIST=1]
[*]The key step is to create the container with display output already set to ${DISPLAY}. This is done as follows:```
lxc launch ubuntu:16.04 name_of_container -c environment.DISPLAY=${DISPLAY}
```
Thereafter, all GUI output will be directed to the user's primary display. Theoretically, by creating containers with display outputs &#8800; ${DISPLAY}, we could launch whole contained DEs into other TTYs and use up those higher slots like <Ctrl>+<Alt>+<F8>&#8230;<F12>. This has long been a goal of mine, but I'm digressing.

[*]Next, edit your host X11 config to allow X11 forwarding. In Ubuntu Xenial, the file is */etc/lightdm/users.conf.* Add the following section:```
[security]
DisallowTCP=false
```
[*]Next, set X on the host to run promiscuously with:```
xhost +
```
This will disable whatever rudimentary security/privacy measures X provides, but since X is a security/privacy sieve anyways, it really isn't much of a loss. This must be done. Otherwise, xhost will deny connection access to the container. Setting *xhost* to promiscuous must be done every time you boot because it resets to secure mode after every reboot. I suppose this can be changed permanently in some config file, but that will require more research.
[*]Then:```
lxc config device add name_of_container x disk source=/tmp/.X11-unix/ path=/tmp/.X11-unix/
```
[/LIST]
To test this, just install a GUI app into the container that isn't part of a default install: say, midori:```
lxc exec name_of_container -- apt install midori -y
``````
lxc exec name_of_container midori
```
On my system, it runs perfectly.

I suppose that it's possible to change the *environment.DISPLAY* value in an existing container, but I haven't figured out how to do that yet.

It is worth noting that @redger's remote desktop method has one immense advantage over the method just outlined above: it is far more secure. A remote desktop like Xephyr runs as a separate xsession. Therefore, quite aside from not having to disable xhost, apps of distinct xsessions have a much harder time peering into another xsession than they do on a commonly shared xsession. This alone makes the remote desktop approach superior for anything that is sensitive. Since one of the purposes of containment is to sandbox, it seems counterproductive to run a contained app in an environment that compromises such containment. This is another example of why Wayland or Mir is being developed to replace X.

BTW, the above info was mainly gleaned from Stephane Graber's following github post: [https://github.com/lxc/lxd/issues/1129#issuecomment-239902931](https://github.com/lxc/lxd/issues/1129#issuecomment-239902931)
It's the only clear example that I could find.

---

### Post by TheFu on 2017-01-29
It isn't necroposting when it is THIS useful!

Using **xhost +** is really bad.  We used to change people's root window background if they had that allowed and security could never find a trace.  There is a huge difference between allowing any remote X connection and allowing the host OS IP via X.  xhost + {local IP} shouldn't be hard for anyone going through these steps to add and would make X/Windows 254x more secure. ;)

I use remote X so much that until any other X/Windows replacement supports it, I just cannot consider switching.  The machine I'm physically using is seldom very powerful whereas the there are other networked systems that have lots and lots of power.

That doesn't take away the usefulness of this technique at all.  Plan to play with it this week.
BTW, the SELF Basic Container Security presentation was just posted here: [https://www.youtube.com/playlist?list=PLvG1nXgsl22FhL55suZtb7RIjEJtkYYC5](https://www.youtube.com/playlist?list=PLvG1nXgsl22FhL55suZtb7RIjEJtkYYC5) with a number of other container best-practice videos.

---

### Post by DuckHook on 2017-01-29
> **TheFu said:**
> Using **xhost +** is really bad…There is a huge difference between allowing any remote X connection and allowing the host OS IP via X.
I agree it's bad. But I haven't been able to get it to work using any variation or combination of xhost + {local IP}
> xhost + {local IP} shouldn't be hard for anyone going through these steps to add and would make X/Windows 254x more secure…Plan to play with it this week.
Please let us know if you solve the *xhost +* problem. I will note that disabling xhost security is very problematic in a multiuser work environment, but in a reasonably well-secured single-user home environment (such as mine), it isn't as much of an issue. Still, it does not constitute good practice, and for that reason alone, I would like to get to the bottom of it.
> BTW, the SELF Basic Container Security presentation was just posted here: [https://www.youtube.com/playlist?list=PLvG1nXgsl22FhL55suZtb7RIjEJtkYYC5](https://www.youtube.com/playlist?list=PLvG1nXgsl22FhL55suZtb7RIjEJtkYYC5) with a number of other container best-practice videos.
Thanks for the link!

---

### Post by DuckHook on 2017-01-29
We're getting closer! \\:D/

A better solution is:```
xhost +local:
```
This is probably still broader than TheFu would like, but at least it stops any network access to X. As already mentioned, if strict X containment is a requirement, then don't use this method to start with and use a remote desktop instead.

---

### Post by DuckHook on 2017-01-30
Thought I would provide update:

While the above procedures work graphically, I've hit a ](*,) on the audio. Despite days of experimentation, I haven't been able to map container sound onto host pulseaudio. This is a known issue with LXD and the desktop, and there's very little on the net on how to put it all together. If others have had success, please do share.

Here's what I've done so far:

[LIST=1]
[*]
[*]Added to host /etc/pulse/system.pa:```
load-module module-native-protocol-tcp auth-ip-acl=127.0.0.1;10.41.45.0/24
auth-anonymous=1
load-module module-zeroconf-publish

```
[*]Created in my ${HOME} directory the file *.asoundrc* with the following:```
pcm.!default {
 type plug
 slave.pcm {
 type hw
 card 1
 device 0
 }
}

defaults.ctl.card 1
```Your card and device numbers may be different.
[*]Installed *paprefs* in the host &#8594; Under "Network Server" tab &#8594; checked "Enable network access to local sound devices", and "Don't require authentication".
[*]In container, added both root and ubuntu user to the groups *pulse*, *audio* and *pulse-access*
[/LIST]
So far, no joy.

---

### Post by DuckHook on 2017-01-30
There is this directly from Stephane Graber: [https://github.com/lxc/lxd/issues/2343#issuecomment-245115628](https://github.com/lxc/lxd/issues/2343#issuecomment-245115628)

Of especial note is his comment:> &#8230;it sounds like you really should stick to LXC itself as that's the only tool which lets you create containers as your own user right now and so is a good fit for this use case.

&#8230;so I am getting discouraged. It appears that LXD is designed from the ground up to remap IDs, NAT, apparmor and otherwise box the container so robustly that the only way to get it to work with apps "naturally" is to open up holes so large that it defeats the point and purpose of containing the app in the first place. First, I had to open up xhost. Now I've got to poke holes in pulseaudio. Not feeling good about this security-wise.

Will continue playing with it, but has dropped significantly in priority. If OP is still reading, did audio work with Zephyr?

---

### Post by bmullan2 on 2017-02-20
LXD (LXC v2) is terrific and a big improvement over LXC v1.

It supports so much more including local & remote servers, CRIU, btrfs/zfs, new networking features like VLAN, VxLAN etc.

If you use Reddit check out the LXD sub-reddit as there is a lot of information there.

[https://www.reddit.com/r/LXD/](https://www.reddit.com/r/LXD/)

Also, I'd highly recommend joining the lxc-users mailer alias as the LXD (and LXC) developers monitor it and answer questions daily.

[https://lists.linuxcontainers.org/listinfo/lxc-users](https://lists.linuxcontainers.org/listinfo/lxc-users)

Finally, Stephane Graber's (he's the lead LXD dev) 12+ part Blog post on LXD is pretty great in explaining alot of what its capable of and how to do things.

[https://stgraber.org/2016/03/11/lxd-2-0-blog-post-series-012/](https://stgraber.org/2016/03/11/lxd-2-0-blog-post-series-012/)

---

### Post by DuckHook on 2017-02-21
Thanks for the links. Will definitely look into them.

I understand LXD's potential. But at the moment, it is still the province of the gurus and not ready for general desktop use. I suppose that it will only get there if enough people like me take up the challenge of bringing it to the masses, but that is one ***big*** challenge.

I appreciate your input. Will try to work up the courage, energy and enthusiasm to tackle eating this elephant.

---

### Post by DuckHook on 2017-02-21
@bmullan2

You clever, wonderful rascal…

Your own post in that reddit thread made audio work for me: [https://www.reddit.com/r/LXD/comments/5thixf/desktop_environment_within_lxc_container/](https://www.reddit.com/r/LXD/comments/5thixf/desktop_environment_within_lxc_container/)

Combined with the process in #4 above: [https://ubuntuforums.org/showthread.php?t=2331353&p=13600531#post13600531](https://ubuntuforums.org/showthread.php?t=2331353&p=13600531#post13600531)

…and the result is both audio and video from my containerized FF. \\:D/

Thanks for the breakthrough. You've just made my week!

**EDIT**

Unfortunately, procedure described above does not actually work and I jumped the gun in thinking it solved. The mistake arose because I already had FF running in my host and then forget to invoke the contained FF with the -no-remote flag. Without the -no-remote flag, FF will just launch another host-based FF session. Once I used -no-remote, the containerized FF was still missing sound.

Will continue to tinker.

---

### Post by redger on 2017-05-04
woohoo .. **breakthrough**. From LXD V2.7 it's possible ... see the following link (available via email from Simos on LXC mailing list, updated email 04/05/17 09:04)
[https://blog.simos.info/how-to-run-graphics-accelerated-gui-apps-in-lxd-containers-on-your-ubuntu-desktop/]("https://blog.simos.info/how-to-run-graphics-accelerated-gui-apps-in-lxd-containers-on-your-ubuntu-desktop/")

I am currently unable to test as I am running "stock" Xenial / 16.04 so LXD still at V 2.0.9 .... but Backports is up to 2.12 (higher than 2.7) ... does anyone have the higher version - able to test ?

---

### Post by KillerKelvUK on 2017-05-04
Hey redger, yup this worked for me albeit I had no .Xauthority file so had to symlink one from /run/user/1000/gdm/Xauthority.

```

:~$ lxc list
+---------+---------+----------------------+------+------------+-----------+
|  NAME   |  STATE  |         IPV4         | IPV6 |    TYPE    | SNAPSHOTS |
+---------+---------+----------------------+------+------------+-----------+
| guiapps | RUNNING | 192.168.1.203 (eth0) |      | PERSISTENT | 0         |
+---------+---------+----------------------+------+------------+-----------+

:~$ lxc exec guiapps -- sudo --login --user ubuntu

ubuntu@guiapps:~$ export DISPLAY=:0

ubuntu@guiapps:~$ glxinfo -B
name of display: :0
display: :0  screen: 0
direct rendering: Yes
Extended renderer info (GLX_MESA_query_renderer):
    Vendor: Intel Open Source Technology Center (0x8086)
    Device: Mesa DRI Intel(R) Haswell Desktop  (0x412)
    Version: 12.0.6
    Accelerated: yes
    Video memory: 1536MB
    Unified memory: yes
    Preferred profile: core (0x1)
    Max core profile version: 3.3
    Max compat profile version: 3.0
    Max GLES1 profile version: 1.1
    Max GLES[23] profile version: 3.0
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Haswell Desktop 
OpenGL core profile version string: 3.3 (Core Profile) Mesa 12.0.6
OpenGL core profile shading language version string: 3.30
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL version string: 3.0 Mesa 12.0.6
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL ES prpfile version string: OpenGL ES 3.0 Mesa 12.0.6
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.00

ubuntu@guiapps:~$ glxgears 
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
310 frames in 5.0 seconds = 61.929 FPS
301 frames in 5.0 seconds = 60.001 FPS

ubuntu@guiapps:~$ uname -a
Linux guiapps 4.10.0-20-generic #22-Ubuntu SMP Thu Apr 20 09:22:42 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

ubuntu@guiapps:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial

```

My host is...

```

:~$ uname -a
Linux blackserver 4.10.0-20-generic #22-Ubuntu SMP Thu Apr 20 09:22:42 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 17.04
Release:    17.04
Codename:    zesty

```

---

### Post by redger on 2017-05-04
Fantastic, thx Kelv :)
PS long time no see ..... glad to see you're also on the LXC / LXD bandwagon as well as KVM ... they complement one another nicely

Did you install the newer version of LXD from a PPA or from Backports ?  Has it been stable for you (don't want to mess my main server up)
thanks again

---

### Post by KillerKelvUK on 2017-05-04
You know I think the last time we chatted you were getting the rest of us to test out new solutions for you :lol: 

Yeah started taking a look and dabbling a few months back, always looking for ways to improve and optimise, its bloody quick I know that...beats KVM guest setup times easily!!

No all stock 17.04, I keep my host as clean as possible even tho its not production I'm still a little OCD with it :-/ . But I haven't spent much time testing yet so I can't really comment on stability and I haven't tested the audio routing yet either.  However I've plenty of time on my hands at the moment so will dig into this more tomorrow.

---

### Post by redger on 2017-05-06
Mate, I don't know what I'd do without you :P

I remain on 16.04 for stability and it's generally working well.

LXC/LXD is really useful where you want additional "control" and a bit more security. I run the following containers permanently and have done for the last 3 years -
- Mythtv server - records TV and cuts advertisements etc. Useful to be able to restart, upgrade etc.and confine processing 
- Every day browsing. Includes desktop integration and VPN
- Other browsing. Via X2Go with VPN
- Downloads. With VPN
- Programming. Nicely confined (in case I write a hard loop or heavy duty machine learning etc) via X2GO
plus various other special purpose containers which i start when needed.

It's convenient to be able to easily constrain resource allocation and maintain host stability with heavier processing tasks. Also convenient to be able to run multiple different VPNs simultaneously

I confine all containers to processors 1-3, leaving processor 0 available for the host.

For "real" security and separation I use KVM (and currently for GPU passthough) .... but there are no permanently running KVM machines, they're all started and stopped as required - unlike containers ... because containers are so light-weight / low processing overhead (in relative terms).
Anyway ... give them a go - you might like them :)

---

### Post by KillerKelvUK on 2017-05-06
I only have the one kvm guest running 24x7 the rest are spun up as needed but that one 24x7 machine could transition into a container although my reading says one application per container as best practice which just doesn't make practical sense for my needs.  Regardless I need to spend more time learning so its a good pass time.  Have you looked into qubes ([https://www.qubes-os.org/](https://www.qubes-os.org/)) before?

---

### Post by TheFu on 2017-05-06
I've looked at Qubes. Last week, they reported a huge security issue with their Xen implementation that allowed one PV to have access to all the memory on the system, including the host.  They are frustrated with the Xen project.  Let me see if I can find that CVE post somewhere.
BTW, I ran Xen for 3 yrs in production with PVs. A few times a year, there were major issues - like refusing to boot any PV. Happened after kernel updates and never when it was convenient.  Always had to roll-back to an older kernel for 1-2 weeks which entailed modifying the VM XML files running on the machine.

[https://www.theregister.co.uk/2017/05/03/xen_bugs/](https://www.theregister.co.uk/2017/05/03/xen_bugs/) is the original story I caught.
[https://www.qubes-os.org/security/bulletins/](https://www.qubes-os.org/security/bulletins/) have the related bugs #29/#30.

I'm still using KVM/QEMU here. It isn't perfect, but nothing is.  It has issues too:
[https://www.cvedetails.com/vulnerability-list/vendor_id-7506/Qemu.html](https://www.cvedetails.com/vulnerability-list/vendor_id-7506/Qemu.html)

---

### Post by KillerKelvUK on 2017-05-06
Actually I think it was your post Fu on another thread that introduced me to qubes.  I've only used Xen minimally as an application vendors preferred virt choice in their appliances so my background is pretty much just KVM/QEMU, but like you say nothing is completely secure, defence in depth needed for sure!

---

### Post by redger on 2017-05-07
thx for the info - Qubes looks interesting. When I set all this up I referred primarily to EAL security ratings ... which led me to KVM (preferably via RedHat / Centos) .... and then Ubuntu since I had previously been a little frustrated with Red Hats offerings.
[https://en.wikipedia.org/wiki/Evaluation_Assurance_Level]("https://en.wikipedia.org/wiki/Evaluation_Assurance_Level")

I have stayed with KVM-QEMU for security and "real" isolation. As Fu says, everything has its issues - this is essentially a constantly evolving predator-prey ecosystem (or parasitism if you prefer) so the balance is always changing (have a look at recent advances in machine learning based security if you want some sleepless nights).
[http://www.bbc.com/news/technology-36980307]("http://www.bbc.com/news/technology-36980307")     (turn this around and consider malevolent hackers using the same/similar techniques)

At the end of the day Intel and AMD have already installed root kits on every PC and there's nothing we can do about that ... we're all open to state sponsored intrusion and surveillance with no real alternative. And I'm not THAT paranoid (I don't have razor wire and total camera surveillance to exclude physical intrusion either :) ) 
[https://libreboot.org/faq.html#intel]("https://libreboot.org/faq.html#intel")


In my case I'm happy with the degree of isolation provided for LXC/LXD for most of my processing it offers many of the advantages of security thru separation without the overheads of full virtualisation ... and it's operationally "easy" which is worth a lot (mine is just a home processing environment). 
Worth noting also that i don't worry too much about full application isolation (that's a Docker style approach) either, not too big a deal for me. Don't let "perfect" obstruct "good enough" ... my comparator is an "normal desktop" rather than a military grade server or commercial hosting service ;)

This 2012 Los Alamos paper is worth reading (for anyone stumbling on this discussion) ... a bit old perhaps ... still  [http://permalink.lanl.gov/object/tr?what=info:lanl-repo/lareport/LA-UR-12-25508]("http://permalink.lanl.gov/object/tr?what=info:lanl-repo/lareport/LA-UR-12-25508")

---

### Post by KillerKelvUK on 2017-05-08
So got the audio working, again minor adaptation from the guide, maybe obvious points but new packages to me...

Set paprefs on the host but needed to logout/login to get the tcp port listening.
Inside the container I needed to install the pulseaudio package which isn't mentioned.

Only stability issue I have so far isn't with the container but with conky on my host.  It craps out completely when I run certain lxc commands which is really odd, its stable 100% of the time when I'm not using LXD.

---

### Post by KillerKelvUK on 2017-05-08
Well redger I'd say its pretty stable, just been playing Half Life for quite sometime and no hiccups whatsoever.

---

### Post by redger on 2017-05-09
bewdy ... just the ticket. 

Thanks for following through :)

---

### Post by DuckHook on 2018-01-14
Bumping a very useful thread to keep it relevant.

---

### Post by simosx on 2018-01-15
> **DuckHook said:**
> Bumping a very useful thread to keep it relevant.

Just found out about this thread. 

I have written a guide at [https://blog.simos.info/how-to-run-graphics-accelerated-gui-apps-in-lxd-containers-on-your-ubuntu-desktop/](https://blog.simos.info/how-to-run-graphics-accelerated-gui-apps-in-lxd-containers-on-your-ubuntu-desktop/)
on how to get GUI apps on the host X server (graphics acceleration and audio support). 
You can run apps like browsers (Firefox, Chrome), Wine and Steam (counterstrike, etc).

If you use Wayland, make sure you have installed **xwayland**.

---

### Post by TheFu on 2018-01-15
Are there known security issues with allowing containers access to the host's audio, video, and clipboard devices?  How do we lock those down as much as possible?

Can someone compare using LXD to Firejail or mbox?

I use firejail both with a tmpfs overlay and just restrictions to subdirs under HOME for write.  It is really, really, easy.  Very lite.  Haven't tried wayland - ever. 

Anyways, all of this is great even if nothing is perfect, each is a step in the right direction to lock down risky processes just a little more than before.  Golf claps all around! Very nice.

---

### Post by DuckHook on 2018-01-15
> **simosx said:**
> I have written a guide at [https://blog.simos.info/how-to-run-graphics-accelerated-gui-apps-in-lxd-containers-on-your-ubuntu-desktop/](https://blog.simos.info/how-to-run-graphics-accelerated-gui-apps-in-lxd-containers-on-your-ubuntu-desktop/)
on how to get GUI apps on the host X server (graphics acceleration and audio support). 
You can run apps like browsers (Firefox, Chrome), Wine and Steam (counterstrike, etc).

If you use Wayland, make sure you have installed **xwayland**.
Thank you so much for your guide, simosx. redger had already linked to it above and, indeed, it is the main reason that I bumped this thread.

It's a pleasure to have you on the forums.

---

### Post by simosx on 2018-01-15
> **TheFu said:**
> Are there known security issues with allowing containers access to the host's audio, video, and clipboard devices?  How do we lock those down as much as possible?

Can someone compare using LXD to Firejail or mbox?

I use firejail both with a tmpfs overlay and just restrictions to subdirs under HOME for write.  It is really, really, easy.  Very lite.  Haven't tried wayland - ever. 

Anyways, all of this is great even if nothing is perfect, each is a step in the right direction to lock down risky processes just a little more than before.  Golf claps all around! Very nice.

I tried all three of them. They all use the same Linux kernel security features to enforce the separation of processes. The main difference for me is in the usability to the end-user. 

LXD is similar to Docker/Moby in that both are about containers. LXD differs from Docker/Moby in that it offers **machine containers**. That is, it's containers that behave just like additional servers/computers, inside your computer.
The purpose of LXD is to be a very light-weight KVM or Virtualbox. I am running now ten LXD *machine containers* on my desktop and they do not cause any degradation in performance.

LXD is meant to be used for services (servers), but it can be used for GUI apps as well. 
My tutorial to get GUI apps on LXD is at [https://blog.simos.info/how-to-run-graphics-accelerated-gui-apps-in-lxd-containers-on-your-ubuntu-desktop/](https://blog.simos.info/how-to-run-graphics-accelerated-gui-apps-in-lxd-containers-on-your-ubuntu-desktop/)
This tutorial tries to be simple, and re-uses the desktop X session (GPU and Pulseaudio server). It does not offer security separation over the low-level desktop X session. For security separation, it would need to use Xephyr instead.

Here are some use-cases for using LXD with GUI apps:

1. You want to install an app in Wine, but you do not want to mess with your desktop by installing all those 32-bit dependencies and what not. You install Wine in a LXD container instead. 

2. You want to install Steam, and again do not want to mess with 32-bit packages and other stuff that get installed. You then have 2+ steam accounts and want an easy way to switch from one to the other. You just make a copy of the container and set up the new account. 

3. You want to try a nodejs app (an example without GUI) but do not want to install all sort of dependencies. You install it in a LXD machine container and access over HTTP. For example, [https://blog.simos.info/how-to-install-a-node-js-app-in-a-lxd-container/](https://blog.simos.info/how-to-install-a-node-js-app-in-a-lxd-container/) This provides good security separation.

Compared to *mbox*, here is how to do this with LXD,

```
$ lxc launch ubuntu:16.04 mytest
Creating mytest
Starting mytest

$ lxc exec mytest /bin/bash
root@mytest:~# cd /
root@mytest:/# ls
bin   dev  home  lib64  mnt  proc  run   snap  sys  usr
boot  etc  lib   media  opt  root  sbin  srv   tmp  var
root@mytest:/# rm -fr *
root@mytest:/# ls
bash: /bin/ls: No such file or directory
root@mytest:/# echo *
dev proc run sys var
root@mytest:/# exit

$ lxc stop --force mytest
$ lxc delete mytest
$ 
```

In this example, we created a machine container called *mytest* with a brand-new and clean Ubuntu 16.04 installation. Then, we invoked a root shell in *mytest*. The next step was to rm -fr all files. Being a machine container, we only removed files inside the machine container.
We then exit the machine container, and we force-stop it. Finally, we delete "mytest" and that's it. All gone!

Here is the list of Linux distributions that are supported (as "guests") in LXD machine containers, [https://us.images.linuxcontainers.org/](https://us.images.linuxcontainers.org/)

Overall, the main benefit of LXD to me is that it is simpler to use and you are less likely to make a mistake when using it. 
For even easier GUI on LXD with proper X11 separation, it should be possible to take the code of Xephyr and create a lightweight clone of Virtualbox!

---

### Post by TheFu on 2018-01-15
For complex dependencies, I understand why a container/VM would be useful. Same for applications that cannot be installed outside the default locations in an OS.  That fits most webapp needs.  Since I don't game or use WINE (anymore), the other examples don't mean much to me.  It is easier to just keep 1 Win7 VM around for those Windows tools I haven't found replacements for, yet.

BTW, you showed lxc, not lxd in the commands. Was that intentional?

```
$ firejail --private /path/to/thunderbird

```is pretty easy.  However, that isn't too useful with an email program - even with IMAP servers. I haven't played with any webapps and firejail. I'm a perl webapp dev. Shouldn't be too hard, since they all run in a self-contained area (including their own perl) and only use tcp connections between their cluster servers and the reverse proxy.

Good discussion. Appreciated.

---

### Post by simosx on 2018-01-15
> **TheFu said:**
> For complex dependencies, I understand why a container/VM would be useful. Same for applications that cannot be installed outside the default locations in an OS.  That fits most webapp needs.  Since I don't game or use WINE (anymore), the other examples don't mean much to me.  It is easier to just keep 1 Win7 VM around for those Windows tools I haven't found replacements for, yet.

I think you phrased it in a way that pushes the discussion forward. I listed the issues that were important and interesting to me.
The way to discuss this, would be to get use-cases and describe which solution would be better suited.

> ```
$ firejail --private /path/to/thunderbird

```is pretty easy.  However, that isn't too useful with an email program - even with IMAP servers. I haven't played with any webapps and firejail. I'm a perl webapp dev. Shouldn't be too hard, since they all run in a self-contained area (including their own perl) and only use tcp connections between their cluster servers and the reverse proxy.

Good discussion. Appreciated.

Thunderbird would be OK for LXD as you get persistent storage.

It would be more interesting to use LXD with webapps.
You can deploy your app in all sort of Linux distributions, [https://us.images.linuxcontainers.org/](https://us.images.linuxcontainers.org/) and automate the testing.
While developing the webapp in a machine container, you can take a snapshots of the container.
Then, you can continue developing and easily switch between snapshots of the container.
See more at [https://stgraber.org/2016/03/30/lxd-2-0-image-management-512/](https://stgraber.org/2016/03/30/lxd-2-0-image-management-512/)

> **TheFu said:**
> BTW, you showed lxc, not lxd in the commands. Was that intentional?

The LXC 1.0 commands have the form of "lxc-create", "lxc-attach" and so on. See more of them at [https://linuxcontainers.org/lxc/manpages/index.html](https://linuxcontainers.org/lxc/manpages/index.html)
However, in LXD there is the **lxd** executable that is the hypervisor (server), and the **lxc** executable that is the client. LXC 1.0 did not have a "lxc" executable, so LXD started using it for the client of these Linux containers.

At [https://discuss.linuxcontainers.org/t/comparing-lxd-vs-lxc/24](https://discuss.linuxcontainers.org/t/comparing-lxd-vs-lxc/24) you can see the differences between LXD and LXC 1.0 (they use the term "LXC").

---

