---
title: "Horizon Vmware Viewer: Not rendering desktop?"
date: 2016-06-13
forum: Virtualisation
---

### Post by eddiefiggie on 2016-06-13
I'm trying to connect to a school PC so to use the lab containing the Office 2013 environment.  I have 16.04 installed on my laptop.

I got the client configured doing this (because I couldn't find a better source):

[https://ubuntu-mate.community/t/how-to-install-vmware-horizon-view-client-3-5-x64/2222](https://ubuntu-mate.community/t/how-to-install-vmware-horizon-view-client-3-5-x64/2222)

I'm able to connect and see the virtual machines.  When I select the VM I want, my screen goes black with the typical frame you'd expect....then it kicks me back out.

Here's what the terminal is reading in the background:


```
username@mysystem:~$ /usr/bin/vmware-view
Using log file /tmp/vmware-username/vmware-horizon-client-9325.log
2016-06-13 20:28:05.486-07:00: vmware-view 9325| Spawn of vmware-view-usb failed: Failed to execute child process "vmware-view-usb" (No such file or directory)
2016-06-13 20:28:05.486-07:00: vmware-view 9325| ViewUsblib: mmfw_RegisterClient: error opening connection: error 2 (No such file or directory)
2016-06-13 20:28:05.486-07:00: vmware-view 9325| ViewUsblib: ViewUsb_InitLib: cannot connect to vmware-view-usbd: mmfw_ret=1
2016-06-13 20:28:05.486-07:00: vmware-view 9325| CdkViewUsb_Init: ViewUsb_InitLib returned ViewUsbStatus_UsbdCommsFailure
2016-06-13 20:28:05.486-07:00: vmware-view 9325| CdkViewUsb_Init: (is vmware-view-usbd running?)
2016-06-13 20:28:05.862-07:00: vmware-view 9325| rmksContainer(9355): Using LogFile VChan-Client.log
2016-06-13 20:28:05.862-07:00: vmware-view 9325| rmksContainer(9355): VMW_RDPVC_BRIDGE_LOG_ENABLED is not defined.                        Logs are disabled.
2016-06-13 20:28:05.981-07:00: vmware-view 9325| rmksContainer(9355): CreateMKSInterface: forcing mount, Remote MKS already present
2016-06-13 20:28:05.981-07:00: vmware-view 9325| rmksContainer(9355): OnMountUnmount: (0, 0) 1024 X 576.
2016-06-13 20:28:12.161-07:00: vmware-view 9325| rmksContainer(9355): Remote MKS network connection status changed: DISCONNECTED
2016-06-13 20:28:12.163-07:00: vmware-view 9325| rmksContainer(9355): OnMountUnmount: remote MKS not present!


```

Why is it trying to use a USB?  I confused by the log in the terminal.

Where do I go from here?  =(

I desperately want to NOT have to use a windows setup to do these assignments.

---

### Post by eddiefiggie on 2016-06-14
I just downgraded back to 14.04 LTS.  I have the client installed from the Ubuntu Software Center.

I run the same connection to my school Windows/Office 2013 VM...  It seems to try to connect (as before).... then it kicks me off and send my back to the pool menu with the option to choose which VM I want....like before.


Here's the log file:

```
2016-06-13T23:51:21.799-08:00| main| I120: Log for VMware Remote MKS Container pid=2637 version=e.x.p build=build-1331430 option=Release
2016-06-13T23:51:21.799-08:00| main| I120: The process is 32-bit.
2016-06-13T23:51:21.799-08:00| main| I120: Host codepage=UTF-8 encoding=UTF-8
2016-06-13T23:51:21.799-08:00| main| I120: Host is Linux 4.2.0-38-generic Ubuntu 14.04.4 LTS
2016-06-13T23:51:21.745-08:00| main| I120: VTHREAD initialize main thread 0 "main" pid 2637
2016-06-13T23:51:21.747-08:00| main| I120: LOCALE en_US.UTF-8 -> NULL
2016-06-13T23:51:21.747-08:00| main| I120: Msg_SetLocaleEx: HostLocale=UTF-8 UserLocale=NULL
2016-06-13T23:51:21.748-08:00| main| I120: Msg_Reset:
2016-06-13T23:51:21.748-08:00| main| I120: [msg.dictionary.load.openFailed] Cannot open file "/etc/vmware/config": No such file or directory.
2016-06-13T23:51:21.748-08:00| main| I120: ----------------------------------------
2016-06-13T23:51:21.748-08:00| main| I120: PREF Optional preferences file not found at /etc/vmware/config. Using default values.
2016-06-13T23:51:21.748-08:00| main| I120: Msg_Reset:
2016-06-13T23:51:21.748-08:00| main| I120: [msg.dictionary.load.openFailed] Cannot open file "/usr/lib/vmware/settings": No such file or directory.
2016-06-13T23:51:21.748-08:00| main| I120: ----------------------------------------
2016-06-13T23:51:21.748-08:00| main| I120: PREF Optional preferences file not found at /usr/lib/vmware/settings. Using default values.
2016-06-13T23:51:21.748-08:00| main| I120: Msg_Reset:
2016-06-13T23:51:21.748-08:00| main| I120: [msg.dictionary.load.openFailed] Cannot open file "/usr/lib/vmware/config": No such file or directory.
2016-06-13T23:51:21.748-08:00| main| I120: ----------------------------------------
2016-06-13T23:51:21.748-08:00| main| I120: PREF Optional preferences file not found at /usr/lib/vmware/config. Using default values.
2016-06-13T23:51:21.748-08:00| main| I120: Msg_Reset:
2016-06-13T23:51:21.748-08:00| main| I120: [msg.dictionary.load.openFailed] Cannot open file "/home/eddiefiggie/.vmware/config": No such file or directory.
2016-06-13T23:51:21.748-08:00| main| I120: ----------------------------------------
2016-06-13T23:51:21.748-08:00| main| I120: PREF Optional preferences file not found at /home/eddiefiggie/.vmware/config. Using default values.
2016-06-13T23:51:21.748-08:00| main| I120: PREF Disabling user preferences because disableUserPreferences is set.
2016-06-13T23:51:21.748-08:00| main| I120: PREF Failed to load user preferences.
2016-06-13T23:51:21.799-08:00| main| I120: MKSRoleMain: Initializing...
2016-06-13T23:51:21.799-08:00| main| I120: DICT --- USER PREFERENCES
2016-06-13T23:51:21.799-08:00| main| I120: DICT --- USER DEFAULTS /home/eddiefiggie/.vmware/config 
2016-06-13T23:51:21.799-08:00| main| I120: DICT --- HOST DEFAULTS /etc/vmware/config 
2016-06-13T23:51:21.799-08:00| main| I120: DICT --- SITE DEFAULTS /usr/lib/vmware/config 
2016-06-13T23:51:21.799-08:00| main| I120: Msg_SetLocaleEx: HostLocale=UTF-8 UserLocale=NULL
2016-06-13T23:51:21.799-08:00| main| I120: MKSRoleMain: Initializing Sig
2016-06-13T23:51:21.800-08:00| main| I120: MKSRoleMain: Initializing WorkerLib
2016-06-13T23:51:21.801-08:00| vthread-3| I120: VTHREAD start thread 3 "vthread-3" pid 2640
2016-06-13T23:51:21.801-08:00| main| I120: MKSRoleMain: Initializing MKS
2016-06-13T23:51:21.842-08:00| main| I120: VmdbAddConnection: cnxPath=/db/connection/#1/, cnxIx=1
2016-06-13T23:51:21.844-08:00| main| W110: VDPUnityVmdb: failed to open plugin file libvdpservice.so: libvdpservice.so: cannot open shared object file: No such file or directory
2016-06-13T23:51:21.845-08:00| main| I120: MKSXlib: Initialized thread-safe Xlib
2016-06-13T23:51:21.857-08:00| main| I120: VDPPLUGIN: pcoip_client: initializing
2016-06-13T23:51:21.879-08:00| main| W110: PulseBackendOpenLib: Failed opening Pulse Audio library: libpulse.so.0: cannot open shared object file: No such file or directory.
2016-06-13T23:51:21.879-08:00| main| W110: PulseBackendCloseLib: Pulse Audio library has not been loaded.
2016-06-13T23:51:21.879-08:00| main| I120: SoundBackend_Create: Pulse backend creation: failure.
2016-06-13T23:51:21.879-08:00| main| W110: AlsaBackendOpenLib: Failed opening Alsa library: libasound.so.2: cannot open shared object file: No such file or directory
2016-06-13T23:51:21.879-08:00| main| I120: SoundBackend_Create: ALSA backend creation: failure.
2016-06-13T23:51:21.879-08:00| main| I120: SoundBackend_Create: OSS backend creation: success.
2016-06-13T23:51:21.879-08:00| main| W110: OSSBackendInitStream: Invalid sound file name: /dev/dsp.
2016-06-13T23:51:21.890-08:00| main| I120: MKSVchan_Init
2016-06-13T23:51:21.890-08:00| main| I120: Registering connect callback function
2016-06-13T23:51:21.895-08:00| main| W110: VDPPluginHostLoadMKSVchanClientLib: loading mksvchanclient
2016-06-13T23:51:21.895-08:00| main| I120: VDPPLUGIN: mksvchanclient: initializing
2016-06-13T23:51:21.895-08:00| main| I120: MKSVchanClient_Init
2016-06-13T23:51:21.895-08:00| main| I120: REMOTEMKS: Protocol is VDP.
2016-06-13T23:51:21.895-08:00| main| W110: VDPOverlayHostPluginGetPluginListLinux: Failed to open config file [/etc/vmware/vdp/host_overlay_plugins/config].
2016-06-13T23:51:21.895-08:00| main| I120: VDPOverlayHostPlugin_Init(): loading overlay plugins
2016-06-13T23:51:21.895-08:00| main| I120: MKSRoleMain: Powering on.
2016-06-13T23:51:21.895-08:00| main| I120: MKSRoleMain: Powering on SigMKS
2016-06-13T23:51:21.895-08:00| main| I120: MKSRoleMain: Powering on MKS
2016-06-13T23:51:21.895-08:00| main| I120: MKS PowerOn
2016-06-13T23:51:21.896-08:00| mks| I120: VTHREAD start thread 1 "mks" pid 2697
2016-06-13T23:51:21.896-08:00| mks| I120: MKS thread is alive
2016-06-13T23:51:21.897-08:00| mksInput| I120: VTHREAD start thread 4 "mksInput" pid 2698
2016-06-13T23:51:21.898-08:00| mks| W110: VDPUnityVmdb: powerOn skipped due to inactive plugin
2016-06-13T23:51:21.898-08:00| mks| I120: DLSym: Error opening shared library "libGL.so.1" (libGL.so.1: cannot open shared object file: No such file or directory)
2016-06-13T23:51:21.898-08:00| mks| I120: MKS-RenderMux: Collecting RenderOps caps...
2016-06-13T23:51:21.899-08:00| mks| I120: KHBKL: Unable to parse keystring at: ''
2016-06-13T23:51:21.899-08:00| main| I120: REMOTEMKS: Powering on VDP Plugin
2016-06-13T23:51:21.899-08:00| main| I120: VDPPLUGIN: pcoip_client: connecting to target 
2016-06-13T23:51:21.900-08:00| main| I120: Peer reported input preferences 0x1.
2016-06-13T23:51:21.900-08:00| main| I120: Peer has no preferred mouse mode.
2016-06-13T23:51:21.900-08:00| main| I120: Peer reported input capabilities 0x2.
2016-06-13T23:51:21.907-08:00| mks| W110: VDPPLUGIN: pcoip_client: set display topology while CONNECTING. Deferring.
2016-06-13T23:51:21.909-08:00| mks| I120: X11-Backend: successfully started by HWinMux to do window composition.
2016-06-13T23:51:21.911-08:00| mks| I120: MKS-X: XI major version 2, minor version 3
2016-06-13T23:51:21.912-08:00| mks| I120: X11-Backend: XINFO SHM available, version 1.2, shared pixmaps
2016-06-13T23:51:21.912-08:00| mks| I120: X11-Backend: Error selecting parent input: (1)
2016-06-13T23:51:21.912-08:00| mks| I120: X11-Backend: Error selecting input: (1)
2016-06-13T23:51:21.912-08:00| mks| I120: X11-Backend: Error lowering window: (1)
2016-06-13T23:51:21.912-08:00| mks| I120: X11-Backend: Error selecting root input: (1)
2016-06-13T23:51:21.912-08:00| mks| I120: X11-Backend: Error changing attributes: (1)
2016-06-13T23:51:21.912-08:00| mks| I120: X11-Backend: Error mapping window: (1)
2016-06-13T23:51:21.912-08:00| mks| I120: XINFO X fd is 16
2016-06-13T23:51:21.912-08:00| mks| I120: XINFO depth 24 bpp 32 class 4
2016-06-13T23:51:21.913-08:00| mks| I120: XINFO  ServerVendor: "The X.Org Foundation"
2016-06-13T23:51:21.913-08:00| mks| I120: XINFO VendorRelease: 11702000
2016-06-13T23:51:21.913-08:00| mks| I120: XINFO XKB available, version 1.0
2016-06-13T23:51:21.914-08:00| mks| I120: XINFO XTEST available, version 2.2
2016-06-13T23:51:21.914-08:00| mks| I120: XINFO Xinerama available
2016-06-13T23:51:21.914-08:00| mks| I120: XKeymap_PowerOn: use evdev keycode mapping.
2016-06-13T23:51:21.914-08:00| mks| I120: MKS-SWB: Number of MKSWindows changed: 1 rendering MKSWindow(s) of total 1.
2016-06-13T23:51:21.923-08:00| mks| W110: VDPPLUGIN: pcoip_client: ignoring mouse event while CONNECTING
2016-06-13T23:51:21.927-08:00| mks| I120: KHBKL: Unable to parse keystring at: ''
2016-06-13T23:51:22.153-08:00| vthread-5| I120: VTHREAD initialize thread 5 "vthread-5" pid 2665
2016-06-13T23:51:22.153-08:00| vthread-5| I120: PCOIP_VCHAN_CONNECT_EVENT_CONN
2016-06-13T23:51:22.153-08:00| vthread-5| I120: mksvchanplugin CONNECTED.
2016-06-13T23:51:22.153-08:00| vthread-5| I120: MKSVchanPluginHandleConnect: Opening legacy channel with capability 0x00000000.
2016-06-13T23:51:22.154-08:00| vthread-5| I120: pcoip_vchan_open succeeded.
2016-06-13T23:51:22.154-08:00| vthread-6| I120: VTHREAD initialize thread 6 "vthread-6" pid 2695
2016-06-13T23:51:22.154-08:00| vthread-6| I120: Peer reported input capabilities 0x2.
2016-06-13T23:51:22.154-08:00| mks| I120: VDPPLUGIN: pcoip_client: successfully connected
2016-06-13T23:51:22.177-08:00| vthread-5| I120: MKSVchanPluginHandleOpened: Legacy channel opened with capability 0x00000000.
2016-06-13T23:51:22.177-08:00| vthread-5| I120: MKSVchanPluginHandleOpened: MKSVchanPlugin is active. Negotiated capability is 0x00000000
2016-06-13T23:51:22.177-08:00| vthread-5| I120: MKSVchanPluginHandleOpened: Queueing clipboard send that we may have missed.
2016-06-13T23:51:22.177-08:00| vthread-7| I120: VTHREAD initialize thread 7 "vthread-7" pid 2642
2016-06-13T23:51:22.177-08:00| vthread-7| I120: mksvchan: clipboard from host requested.
2016-06-13T23:51:22.183-08:00| vthread-7| I120: MKSVchanPlugin_Send: sent data of len: 8, remaining: 0
2016-06-13T23:51:22.183-08:00| vthread-7| I120: MKSVchanPlugin_SendClipboardData: sending packet data of len 9
2016-06-13T23:51:22.183-08:00| vthread-7| I120: MKSVchanPlugin_SendClipboardData: Sending packet header took 0 seconds
2016-06-13T23:51:22.183-08:00| vthread-7| I120: MKSVchanPlugin_Send: sent data of len: 9, remaining: 0
2016-06-13T23:51:22.183-08:00| vthread-7| I120: MKSVchanPlugin_SendClipboardData: Clipboard packet sent
2016-06-13T23:51:22.183-08:00| vthread-7| I120: MKSVchanPlugin_SendClipboardData: Sending 9-byte payload took 0 seconds
2016-06-13T23:51:22.679-08:00| mks| I120: Begin gathering input Locale Identifiers for the user.
2016-06-13T23:51:22.681-08:00| mks| I120: Number of installed Input Locale Identifiers for the user 1
2016-06-13T23:51:22.681-08:00| mks| I120: 1. Language 0x409 Layout unique id 0x0
2016-06-13T23:51:22.681-08:00| mks| I120: Finished gathering input Locale Identifiers for the user.
2016-06-13T23:51:28.455-08:00| vthread-5| I120: PCOIP_VCHAN_CONNECT_EVENT_CONN
2016-06-13T23:51:28.455-08:00| vthread-5| I120: mksvchanplugin DISCONNECTED.
2016-06-13T23:51:28.455-08:00| vthread-5| I120: MKSVchanPlugin_Cleanup: exiting 0
2016-06-13T23:51:28.455-08:00| vthread-5| I120: MKSVchanPlugin_Cleanup: Closing legacy virtual channel now.
2016-06-13T23:51:28.456-08:00| mks| W110: VDPPLUGIN: pcoip_client: disconnect reason code 6: VDPCONNECT_SERVER_DISCONNECTED
2016-06-13T23:51:28.456-08:00| mks| I120: MKSRoleMain: Disconnected from server.
2016-06-13T23:51:28.456-08:00| mks| I120: MKSRoleMain: Disconnected from server with error code 6.
2016-06-13T23:51:28.467-08:00| mks| I120: X11-Backend: stopped by HWinMux to do window composition.
2016-06-13T23:51:28.467-08:00| mks| I120: MKS-SWB: Number of MKSWindows changed: 0 rendering MKSWindow(s) of total 0.
2016-06-13T23:51:28.467-08:00| main| I120: REMOTEMKS: Powering off VDP Plugin
2016-06-13T23:51:28.467-08:00| main| I120: VDPOverlayHostPlugin_Exit(): unloading overlay plugins
2016-06-13T23:51:28.467-08:00| main| W110: VDPPLUGIN pcoip_client: disconnect request while already disconnected.MKSVchanClient_Exit
2016-06-13T23:51:28.467-08:00| main| I120: VDPPLUGIN: pcoip_client: exiting...
2016-06-13T23:51:28.468-08:00| main| I120: MKSVchanPlugin_Cleanup: exiting 1
2016-06-13T23:51:28.468-08:00| main| I120: MKSVchanPlugin_Cleanup: Closing legacy virtual channel now.
2016-06-13T23:51:28.468-08:00| main| I120: MKSVchan_Exit
2016-06-13T23:51:28.468-08:00| vthread-7| I120: mksvchan: clipboard shutdown requested.
2016-06-13T23:51:28.471-08:00| main| I120: VDPPLUGIN: pcoip_client: exited.
2016-06-13T23:51:28.471-08:00| main| I120: MKSRoleMain: Powering off.
2016-06-13T23:51:28.471-08:00| main| I120: MKSRoleMain: Powering off MKS
2016-06-13T23:51:28.474-08:00| mks| W110: VDPUnityVmdb: powerOff skipped due to inactive plugin.
2016-06-13T23:51:28.474-08:00| mks| I120: MKS PowerOff
2016-06-13T23:51:28.474-08:00| mks| I120: MKS thread is exiting
2016-06-13T23:51:28.474-08:00| main| I120: MKSRoleMain: Powering off SigMKS
2016-06-13T23:51:28.474-08:00| main| I120: MKSRoleMain: Exiting...
2016-06-13T23:51:28.474-08:00| main| I120: MKSRoleMain: Exiting MKS
2016-06-13T23:51:28.475-08:00| main| I120: MKSRoleMain: Exiting WorkerLib
2016-06-13T23:51:28.475-08:00| main| I120: WORKER: asyncOps=0 maxActiveOps=0 maxPending=0 maxCompleted=0
2016-06-13T23:51:28.475-08:00| main| I120: MKSRoleMain: Exiting Sig
2016-06-13T23:51:28.475-08:00| main| I120: MKSRoleMain: Skipping SSL (already exited)
2016-06-13T23:51:28.475-08:00| main| I120: MKSRoleMain: Exiting Poll
2016-06-13T23:51:28.475-08:00| main| I120: MKSRoleMain: Exiting Log
```

---

### Post by MAFoElffen on 2016-06-15
I search over on the VMware Forums and found that others had this same problem. It pointed to an installation problem of Horizon Client vmware-view. There was two solutions that worked for users:

[http://askubuntu.com/questions/271719/vmware-view-install](http://askubuntu.com/questions/271719/vmware-view-install)

[https://communities.vmware.com/thread/499473](https://communities.vmware.com/thread/499473)

Hope that helps.

---

### Post by eddiefiggie on 2016-06-23
I followed the 1st link to get up to the point where I made the OP.

The second link was new...  I read through that one and employed the recommendations.  It seems there are far fewer errors.  Still a few however.

I can see using a USB drive through VM will likely continue to give me heartburn.  here's what the Terminal is reading when I try and connect:

```

Jun 23 13:33:07.936: vmware-view.bin 6437| Spawn of vmware-view-usb failed: Failed to execute child process "vmware-view-usb" (No such file or directory)
Jun 23 13:33:07.936: vmware-view.bin 6437| ViewUsblib: mmfw_RegisterClient: error opening connection: error 2 (No such file or directory)
Jun 23 13:33:07.936: vmware-view.bin 6437| ViewUsblib: ViewUsb_InitLib: cannot connect to vmware-view-usbd: mmfw_ret=1
Jun 23 13:33:07.936: vmware-view.bin 6437| CdkViewUsb_Init: ViewUsb_InitLib returned ViewUsbStatus_UsbdCommsFailure
Jun 23 13:33:07.936: vmware-view.bin 6437| CdkViewUsb_Init: (is vmware-view-usbd running?)
Jun 23 13:33:07.959: vmware-view.bin 6437| PCoIP Client(6443): Gtk-Message: Failed to load module "overlay-scrollbar"
Jun 23 13:33:07.959: vmware-view.bin 6437| PCoIP Client(6443): Gtk-Message: Failed to load module "unity-gtk-module"
Jun 23 13:33:07.982: vmware-view.bin 6437| PCoIP Client(6443): Gtk-Message: Failed to load module "canberra-gtk-module"
Jun 23 13:33:08.269: vmware-view.bin 6437| PCoIP Client(6443): Gtk-Message: Failed to load module "overlay-scrollbar"
Jun 23 13:33:08.269: vmware-view.bin 6437| PCoIP Client(6443): Gtk-Message: Failed to load module "unity-gtk-module"
Jun 23 13:33:08.277: vmware-view.bin 6437| PCoIP Client(6443): CreateMKSInterface: forcing mount, Remote MKS already present
Jun 23 13:33:08.278: vmware-view.bin 6437| PCoIP Client(6443): OnMountUnmount: (0, 0) 1024 X 576.
Jun 23 13:33:08.283: vmware-view.bin 6437| PCoIP Client(6443): Gtk-Message: Failed to load module "canberra-gtk-module"
Jun 23 13:33:14.278: vmware-view.bin 6437| PCoIP Client(6443): Remote MKS network connection status changed: DISCONNECTED
Jun 23 13:33:14.278: vmware-view.bin 6437| PCoIP Client(6443): OnMountUnmount: remote MKS not present!


```

---

### Post by MAFoElffen on 2016-06-24
One thing I wonder, even when I use vShere guests, I know if I am using USB from a client, I have to use VMware Tools. Some use opn-vmware-tools instead (which has problems with current versions). It I use USB from a guest to use usb from the host, I have to do a pass-through.

What "is" the remote host? What is the client? Is it tunneled through a VNC? (What is the VNC client?)

Are you using VMware Tools or open-vmware-tools?

I am just trying to figure out and picture all the pieces that are trying to connect to each other ... and that figures in to the context of the errors. For instance. trying to connect to something that is not there as an agent or protocol.

---

