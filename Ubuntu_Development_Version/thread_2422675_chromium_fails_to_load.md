---
title: "chromium fails to load"
date: 2019-07-11
forum: Ubuntu Development Version
---

### Post by dino99 on 2019-07-11
Recent proposed upgrades (10/11 july) seem to disturb snap chromium installation.
When i click on the chromium icon or from the terminal, the loading process start and finally silently fails.

I have refreshed the snap chromium installation (no warning or error), but that does not help.
sudo snap refresh chromium --channel=candidate/from-source

Get the lines logged:
 chromium_chromium.desktop[1736]: cannot perform operation: mount --rbind /dev /tmp/snap.rootfs_8RyedF//dev: No such file or directory

No more idea to get around that issue. ;)

---

### Post by dino99 on 2019-07-11
Since the post above, i've made 2 cold boots, and the latest let chromium loading (but it takes a couple not expected seconds)

> oem@oem-desktop:~$ journalctl -b | grep chromium
juil. 11 17:15:15 oem-desktop audit[783]: AVC apparmor="STATUS" operation="profile_load" profile="unconfined" name="snap.chromium.chromium" pid=783 comm="apparmor_parser"
juil. 11 17:15:15 oem-desktop audit[788]: AVC apparmor="STATUS" operation="profile_load" profile="unconfined" name="snap.chromium.chromedriver" pid=788 comm="apparmor_parser"
juil. 11 17:15:15 oem-desktop audit[789]: AVC apparmor="STATUS" operation="profile_load" profile="unconfined" name="snap-update-ns.chromium" pid=789 comm="apparmor_parser"
juil. 11 17:15:14 oem-desktop systemd[1]: Mounted Mount unit for chromium, revision 784.
juil. 11 17:15:14 oem-desktop systemd[1]: Mounted Mount unit for chromium, revision 787.
juil. 11 17:15:21 oem-desktop snapd[973]: storehelpers.go:441: cannot refresh: snap has no updates available: "chromium", "core", "core18", "gtk-common-themes", "snapd"
juil. 11 17:15:37 oem-desktop dbus-daemon[1585]: apparmor="DENIED" operation="dbus_method_call"  bus="session" path="/org/freedesktop/secrets" interface="org.freedesktop.DBus.Properties" member="GetAll" mask="send" name="org.freedesktop.secrets" pid=2293 label="snap.chromium.chromium" peer_pid=1571 peer_label="unconfined"
juil. 11 17:15:40 oem-desktop audit[958]: USER_AVC pid=958 uid=103 auid=4294967295 ses=4294967295 msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/" interface="org.freedesktop.DBus.ObjectManager" member="GetManagedObjects" mask="send" name="org.bluez" pid=2060 label="snap.chromium.chromium"
juil. 11 17:15:40 oem-desktop kernel: audit: type=1107 audit(1562858140.207:38): pid=958 uid=103 auid=4294967295 ses=4294967295 msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/" interface="org.freedesktop.DBus.ObjectManager" member="GetManagedObjects" mask="send" name="org.bluez" pid=2060 label="snap.chromium.chromium"
juil. 11 17:15:40 oem-desktop dbus-daemon[1585]: [session uid=1000 pid=1585] Activating service name='io.snapcraft.Settings' requested by ':1.79' (uid=1000 pid=2337 comm="dbus-send --print-reply=literal --session --dest=i" label="snap.chromium.chromium (enforce)")
juil. 11 17:15:41 oem-desktop chromium_chromium.desktop[1764]: [2320:2320:0711/171541.228231:ERROR:sandbox_linux.cc(368)] InitializeSandbox() called with multiple threads in process gpu-process.
juil. 11 17:15:41 oem-desktop chromium_chromium.desktop[1764]: [2320:2320:0711/171541.847035:ERROR:buffer_manager.cc(488)] [.DisplayCompositor]GL ERROR :GL_INVALID_OPERATION : glBufferData: <- error from previous GL command

---

### Post by dino99 on 2019-07-13
Still the same mess:
- first chromium icon click after opening the session (shell on xorg): load fails after 3 seconds
- remove snap then reinstall: still fails to load
- refresh snap: does not help
- close the session and reboot: chromium finally load, but opening ubuntuforums, the password has been loast again  ](*,)

>  oem@oem-desktop:~$ journalctl -b | grep chromium
juil. 13 09:50:17 oem-desktop audit[719]: AVC apparmor="STATUS" operation="profile_load" profile="unconfined" name="snap.chromium.chromium" pid=719 comm="apparmor_parser"
juil. 13 09:50:17 oem-desktop audit[724]: AVC apparmor="STATUS" operation="profile_load" profile="unconfined" name="snap.chromium.chromedriver" pid=724 comm="apparmor_parser"
juil. 13 09:50:17 oem-desktop audit[725]: AVC apparmor="STATUS" operation="profile_load" profile="unconfined" name="snap-update-ns.chromium" pid=725 comm="apparmor_parser"
juil. 13 09:50:17 oem-desktop systemd[1]: Mounted Mount unit for chromium, revision 787.
juil. 13 09:50:39 oem-desktop chromium_chromium.desktop[1729]: Importing existing chromium profile from /home/oem/.config/chromium (version 74.0.3729.169)
juil. 13 09:50:41 oem-desktop chromium_chromium.desktop[1729]: Import done in 2.514 s
juil. 13 09:50:41 oem-desktop dbus-daemon[1561]: apparmor="DENIED" operation="dbus_method_call"  bus="session" path="/org/freedesktop/secrets" interface="org.freedesktop.DBus.Properties" member="GetAll" mask="send" name="org.freedesktop.secrets" pid=2290 label="snap.chromium.chromium" peer_pid=1547 peer_label="unconfined"
juil. 13 09:50:44 oem-desktop audit[967]: USER_AVC pid=967 uid=103 auid=4294967295 ses=4294967295 msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/" interface="org.freedesktop.DBus.ObjectManager" member="GetManagedObjects" mask="send" name="org.bluez" pid=2038 label="snap.chromium.chromium"
juil. 13 09:50:44 oem-desktop kernel: audit: type=1107 audit(1563004244.355:38): pid=967 uid=103 auid=4294967295 ses=4294967295 msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/" interface="org.freedesktop.DBus.ObjectManager" member="GetManagedObjects" mask="send" name="org.bluez" pid=2038 label="snap.chromium.chromium"
juil. 13 09:50:44 oem-desktop dbus-daemon[1561]: [session uid=1000 pid=1561] Activating service name='io.snapcraft.Settings' requested by ':1.78' (uid=1000 pid=2333 comm="dbus-send --print-reply=literal --session --dest=i" label="snap.chromium.chromium (enforce)")
juil. 13 09:50:45 oem-desktop chromium_chromium.desktop[1729]: [2317:2317:0713/095045.383962:ERROR:sandbox_linux.cc(368)] InitializeSandbox() called with multiple threads in process gpu-process.
juil. 13 09:50:46 oem-desktop chromium_chromium.desktop[1729]: [2317:2317:0713/095046.037956:ERROR:buffer_manager.cc(488)] [.DisplayCompositor]GL ERROR :GL_INVALID_OPERATION : glBufferData: <- error from previous GL command
juil. 13 09:50:57 oem-desktop chromium_chromium.desktop[1729]: [1:1:0713/095057.794085:ERROR:native_extension_bindings_system.cc(607)] Failed to create API on Chrome object.
juil. 13 09:50:57 oem-desktop chromium_chromium.desktop[1729]: [1:1:0713/095057.796046:ERROR:native_extension_bindings_system.cc(607)] Failed to create API on Chrome object.
juil. 13 09:50:57 oem-desktop chromium_chromium.desktop[1729]: LaunchProcess: failed to execvp:
juil. 13 09:50:57 oem-desktop chromium_chromium.desktop[1729]: xdg-desktop-menu
juil. 13 09:50:57 oem-desktop chromium_chromium.desktop[1729]: LaunchProcess: failed to execvp:
juil. 13 09:50:57 oem-desktop chromium_chromium.desktop[1729]: xdg-icon-resource
juil. 13 09:50:57 oem-desktop chromium_chromium.desktop[1729]: LaunchProcess: failed to execvp:
juil. 13 09:50:57 oem-desktop chromium_chromium.desktop[1729]: xdg-icon-resource
juil. 13 09:50:57 oem-desktop chromium_chromium.desktop[1729]: LaunchProcess: failed to execvp:
juil. 13 09:50:57 oem-desktop chromium_chromium.desktop[1729]: xdg-icon-resource
juil. 13 09:50:57 oem-desktop chromium_chromium.desktop[1729]: LaunchProcess: failed to execvp:
juil. 13 09:50:57 oem-desktop chromium_chromium.desktop[1729]: xdg-icon-resource
juil. 13 09:50:57 oem-desktop chromium_chromium.desktop[1729]: LaunchProcess: failed to execvp:
juil. 13 09:50:57 oem-desktop chromium_chromium.desktop[1729]: xdg-desktop-menu
juil. 13 09:51:07 oem-desktop chromium_chromium.desktop[1729]: [1:1:0713/095107.607682:ERROR:native_extension_bindings_system.cc(607)] Failed to create API on Chrome object.
juil. 13 09:51:07 oem-desktop chromium_chromium.desktop[1729]: [1:1:0713/095107.611250:ERROR:native_extension_bindings_system.cc(607)] Failed to create API on Chrome object.
 


Canonical, that snap packaging is way too sensitive to packages upgrades to be used without deb alternative.

---

### Post by PaulW2U on 2019-07-13
> **dino99 said:**
> snap packaging is way too sensitive to packages upgrades to be used without deb alternative.
I've haven't had any problems here at all.

Since the initial install/transition I've had an auto-update from version 75.0.3770.90 to 75.0.3770.100, I've also switched from the stable channel to the candidate channel and back again. Chromium has worked as expected. There are no serious issues being reported on the [Call for testing]("https://discourse.ubuntu.com/t/call-for-testing-chromium-browser-deb-to-snap-transition/11179") thread on the Community Hub either but just a few glitches that need to be worked out before 19.10 is released in October and/or the transition to a snap is rolled out to the remaining supported releases.

I think you need to file a bug report on Launchpad about this or at least add some comments to the Community Hub thread, referring to your posts here, and see what those working on Chromium have to say.

---

### Post by TenPlus1 on 2019-07-14
I removed the snap packages for Chromium and installed the 19.04 .deb files instead, they work better.

---

### Post by osomon on 2019-07-15
Thanks for the feedback @dino99. I answered on the [call for testing]("https://discourse.ubuntu.com/t/call-for-testing-chromium-browser-deb-to-snap-transition/11179/74"), please keep the feedback related to the chromium snap there or on the snapcraft forum, this will get the attention it deserves from the right developers. Thanks!

---

### Post by dino99 on 2019-07-15
thanks Osomon

nothing to blame today, upgrades have not broken chromium, but logs are still filled with:

> oem@oem-desktop:~$ journalctl -b | grep chromium
juil. 15 05:40:18 oem-desktop systemd[1]: Mounted Mount unit for chromium, revision 784.
juil. 15 05:40:18 oem-desktop systemd[1]: Mounted Mount unit for chromium, revision 787.
juil. 15 05:40:18 oem-desktop audit[651]: AVC apparmor="STATUS" operation="profile_load" profile="unconfined" name="snap.chromium.chromium" pid=651 comm="apparmor_parser"
juil. 15 05:40:18 oem-desktop audit[658]: AVC apparmor="STATUS" operation="profile_load" profile="unconfined" name="snap.chromium.chromedriver" pid=658 comm="apparmor_parser"
juil. 15 05:40:18 oem-desktop audit[659]: AVC apparmor="STATUS" operation="profile_load" profile="unconfined" name="snap-update-ns.chromium" pid=659 comm="apparmor_parser"
juil. 15 05:40:24 oem-desktop snapd[987]: storehelpers.go:441: cannot refresh: snap has no updates available: "chromium", "core", "core18", "gtk-common-themes", "snapd"
juil. 15 05:44:39 oem-desktop dbus-daemon[1600]: apparmor="DENIED" operation="dbus_method_call"  bus="session" path="/org/freedesktop/secrets" interface="org.freedesktop.DBus.Properties" member="GetAll" mask="send" name="org.freedesktop.secrets" pid=4614 label="snap.chromium.chromium" peer_pid=1586 peer_label="unconfined"
juil. 15 05:44:42 oem-desktop audit[932]: USER_AVC pid=932 uid=103 auid=4294967295 ses=4294967295 msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/" interface="org.freedesktop.DBus.ObjectManager" member="GetManagedObjects" mask="send" name="org.bluez" pid=4501 label="snap.chromium.chromium"
juil. 15 05:44:42 oem-desktop kernel: audit: type=1107 audit(1563162282.355:38): pid=932 uid=103 auid=4294967295 ses=4294967295 msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/" interface="org.freedesktop.DBus.ObjectManager" member="GetManagedObjects" mask="send" name="org.bluez" pid=4501 label="snap.chromium.chromium"
juil. 15 05:44:42 oem-desktop dbus-daemon[1600]: [session uid=1000 pid=1600] Activating service name='io.snapcraft.Settings' requested by ':1.83' (uid=1000 pid=4660 comm="dbus-send --print-reply=literal --session --dest=i" label="snap.chromium.chromium (enforce)")
juil. 15 05:44:43 oem-desktop chromium_chromium.desktop[1778]: [4643:4643:0715/054443.390235:ERROR:sandbox_linux.cc(368)] InitializeSandbox() called with multiple threads in process gpu-process.
juil. 15 05:44:43 oem-desktop chromium_chromium.desktop[1778]: [4643:4643:0715/054443.977331:ERROR:buffer_manager.cc(488)] [.DisplayCompositor]GL ERROR :GL_INVALID_OPERATION : glBufferData: <- error from previous GL command
juil. 15 06:32:34 oem-desktop chromium_chromium.desktop[1778]: [4643:4643:0715/063234.799512:ERROR:buffer_manager.cc(488)] [.DisplayCompositor]GL ERROR :GL_INVALID_OPERATION : glBufferData: <- error from previous GL command
juil. 15 06:32:48 oem-desktop chromium_chromium.desktop[1778]: [4643:4643:0715/063248.535542:ERROR:buffer_manager.cc(488)] [.DisplayCompositor]GL ERROR :GL_INVALID_OPERATION : glBufferData: <- error from previous GL command
juil. 15 06:33:46 oem-desktop chromium_chromium.desktop[1778]: [4643:4643:0715/063346.099964:ERROR:buffer_manager.cc(488)] [.DisplayCompositor]GL ERROR :GL_INVALID_OPERATION : glBufferData: <- error from previous GL command
juil. 15 06:34:09 oem-desktop chromium_chromium.desktop[1778]: [4643:4643:0715/063409.056553:ERROR:buffer_manager.cc(488)] [.DisplayCompositor]GL ERROR :GL_INVALID_OPERATION : glBufferData: <- error from previous GL command
juil. 15 06:34:36 oem-desktop dbus-daemon[1600]: apparmor="DENIED" operation="dbus_bind"  bus="session" name="org.mpris.MediaPlayer2.chromium.instance4501" mask="bind" pid=4501 label="snap.chromium.chromium"
juil. 15 06:34:36 oem-desktop chromium_chromium.desktop[1778]: [4501:4702:0715/063436.237435:ERROR:bus.cc(554)] Failed to get the ownership of org.mpris.MediaPlayer2.chromium.instance4501: Connection ":1.96" is not allowed to own the service "org.mpris.MediaPlayer2.chromium.instance4501" due to AppArmor policy
juil. 15 06:56:08 oem-desktop chromium_chromium.desktop[1778]: [4643:4643:0715/065608.800719:ERROR:gles2_cmd_decoder.cc(18461)] [.DisplayCompositor]GL ERROR :GL_INVALID_OPERATION : glCreateAndConsumeTextureCHROMIUM: invalid mailbox name
juil. 15 06:56:08 oem-desktop chromium_chromium.desktop[1778]: [4643:4643:0715/065608.801360:ERROR:gles2_cmd_decoder.cc(18461)] [.DisplayCompositor]GL ERROR :GL_INVALID_OPERATION : glCreateAndConsumeTextureCHROMIUM: invalid mailbox name
juil. 15 06:56:08 oem-desktop chromium_chromium.desktop[1778]: [4643:4643:0715/065608.801480:ERROR:gles2_cmd_decoder.cc(10734)] [.DisplayCompositor]RENDER WARNING: texture bound to texture unit 1 is not renderable. It maybe non-power-of-2 and have incompatible texture filtering.
juil. 15 06:56:08 oem-desktop chromium_chromium.desktop[1778]: [4643:4643:0715/065608.801509:ERROR:gles2_cmd_decoder.cc(10734)] [.DisplayCompositor]RENDER WARNING: texture bound to texture unit 2 is not renderable. It maybe non-power-of-2 and have incompatible texture filtering.


---

### Post by dino99 on 2019-07-19
Broken again ; get logged:
juil. 19 17:10:56 oem-desktop chromium_chromium.desktop[2022]: internal error, please report: running "chromium" failed: timeout waiting for snap system profiles to get updated

> oem@oem-desktop:~$ journalctl -b | grep snapd
juil. 19 17:07:17 oem-desktop systemd[1]: Mounted Mount unit for snapd, revision 3465.
juil. 19 17:07:17 oem-desktop mount[409]: mount: /snap/snapd/3646: /dev/loop1 already mounted or mount point busy.
juil. 19 17:07:17 oem-desktop kernel: audit: type=1400 audit(1563548837.599:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/snapd/snap-confine" pid=607 comm="apparmor_parser"
juil. 19 17:07:17 oem-desktop kernel: audit: type=1400 audit(1563548837.599:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/snapd/snap-confine//mount-namespace-capture-helper" pid=607 comm="apparmor_parser"
juil. 19 17:07:17 oem-desktop audit[607]: AVC apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/snapd/snap-confine" pid=607 comm="apparmor_parser"
juil. 19 17:07:17 oem-desktop audit[607]: AVC apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/snapd/snap-confine//mount-namespace-capture-helper" pid=607 comm="apparmor_parser"
juil. 19 17:07:17 oem-desktop audit[701]: AVC apparmor="STATUS" operation="profile_load" profile="unconfined" name="/snap/snapd/3646/usr/lib/snapd/snap-confine" pid=701 comm="apparmor_parser"
juil. 19 17:07:17 oem-desktop audit[701]: AVC apparmor="STATUS" operation="profile_load" profile="unconfined" name="/snap/snapd/3646/usr/lib/snapd/snap-confine//mount-namespace-capture-helper" pid=701 comm="apparmor_parser"
juil. 19 17:07:17 oem-desktop audit[709]: AVC apparmor="STATUS" operation="profile_load" profile="unconfined" name="/snap/core/7270/usr/lib/snapd/snap-confine" pid=709 comm="apparmor_parser"
juil. 19 17:07:17 oem-desktop audit[709]: AVC apparmor="STATUS" operation="profile_load" profile="unconfined" name="/snap/core/7270/usr/lib/snapd/snap-confine//mount-namespace-capture-helper" pid=709 comm="apparmor_parser"
juil. 19 17:07:19 oem-desktop snapd[1094]: AppArmor status: apparmor is enabled and all features are available
juil. 19 17:07:19 oem-desktop snapd[1094]: AppArmor status: apparmor is enabled and all features are available
juil. 19 17:07:19 oem-desktop snapd[1094]: snapmgr.go:258: cannot read snap info of snap "snapd" at revision 3646: cannot find installed snap "snapd" at revision 3646: missing file /snap/snapd/3646/meta/snap.yaml
juil. 19 17:07:19 oem-desktop snapd[1094]: panic: assignment to entry in nil map
juil. 19 17:07:19 oem-desktop snapd[1094]: goroutine 1 [running]:
juil. 19 17:07:19 oem-desktop snapd[1094]: github.com/snapcore/snapd/overlord/ifacestate.addImplicitSlots(0xc4202ce380, 0xc420366000, 0x0, 0x0)
juil. 19 17:07:19 oem-desktop snapd[1094]:         /build/snapd-ghjK3c/snapd-2.39.3/_build/src/github.com/snapcore/snapd/overlord/ifacestate/implicit.go:68 +0x291
juil. 19 17:07:19 oem-desktop snapd[1094]: github.com/snapcore/snapd/overlord/ifacestate.(*InterfaceManager).addSnaps(0xc42022ef00, 0xc420332540, 0x5, 0x8, 0x0, 0x0)
juil. 19 17:07:19 oem-desktop snapd[1094]:         /build/snapd-ghjK3c/snapd-2.39.3/_build/src/github.com/snapcore/snapd/overlord/ifacestate/helpers.go:133 +0x7e
juil. 19 17:07:19 oem-desktop snapd[1094]: github.com/snapcore/snapd/overlord/ifacestate.(*InterfaceManager).initialize(0xc42022ef00, 0x0, 0x0, 0x0, 0x0, 0x0, 0x0, 0x5606d60c8f40, 0xc42026de60, 0x0, ...)
juil. 19 17:07:19 oem-desktop snapd[1094]:         /build/snapd-ghjK3c/snapd-2.39.3/_build/src/github.com/snapcore/snapd/overlord/ifacestate/helpers.go:68 +0x172
juil. 19 17:07:19 oem-desktop snapd[1094]: github.com/snapcore/snapd/overlord/ifacestate.Manager(0xc4202ce380, 0xc4202325a0, 0xc4202c7b20, 0x0, 0x0, 0x0, 0x0, 0x0, 0x0, 0xf, ...)
juil. 19 17:07:19 oem-desktop snapd[1094]:         /build/snapd-ghjK3c/snapd-2.39.3/_build/src/github.com/snapcore/snapd/overlord/ifacestate/ifacemgr.go:79 +0x2b4
juil. 19 17:07:19 oem-desktop snapd[1094]: github.com/snapcore/snapd/overlord.New(0x0, 0x0, 0x0)
juil. 19 17:07:19 oem-desktop snapd[1094]:         /build/snapd-ghjK3c/snapd-2.39.3/_build/src/github.com/snapcore/snapd/overlord/overlord.go:135 +0x438
juil. 19 17:07:19 oem-desktop snapd[1094]: github.com/snapcore/snapd/daemon.New(0x5606d5b1d6e5, 0x6, 0x0)
juil. 19 17:07:19 oem-desktop snapd[1094]:         /build/snapd-ghjK3c/snapd-2.39.3/_build/src/github.com/snapcore/snapd/daemon/daemon.go:704 +0x28
juil. 19 17:07:19 oem-desktop snapd[1094]: main.run(0xc42022e9c0, 0x0, 0x0)
juil. 19 17:07:19 oem-desktop snapd[1094]:         /build/snapd-ghjK3c/snapd-2.39.3/_build/src/github.com/snapcore/snapd/cmd/snapd/main.go:108 +0xa5
juil. 19 17:07:19 oem-desktop snapd[1094]: main.main()
juil. 19 17:07:19 oem-desktop snapd[1094]:         /build/snapd-ghjK3c/snapd-2.39.3/_build/src/github.com/snapcore/snapd/cmd/snapd/main.go:58 +0xd7
juil. 19 17:07:19 oem-desktop systemd[1]: snapd.service: Main process exited, code=exited, status=2/INVALIDARGUMENT


---

### Post by dino99 on 2019-08-06
Broken again:

chromium_chromium.desktop[1698]: cannot create cgroup hierarchy /sys/fs/cgroup/devices/snap.chromium.chromium/: No such file or directory
chromium_chromium.desktop[1700]: LaunchProcess: failed to execvp:

---

