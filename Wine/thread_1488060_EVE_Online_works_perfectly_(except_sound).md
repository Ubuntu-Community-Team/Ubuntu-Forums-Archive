---
title: "EVE Online works perfectly (except sound)"
date: 2010-05-19
forum: Wine
---

### Post by miickEe on 2010-05-19
I have recently upgraded to Ubuntu 10.04 and I love it, great release. I am running wine1.2, and installed the latest EVE Online client in there. It runs perfectly, although without sound. The sound worked the first time I ran the game, then somewhere during gameplay it stopped. The sound works in all other applications, and in the winecfg sound test.

Here is the output of the command I use to run the game.

```

mike@mike:~$ ine explorer /desktop=0,1280x1024 "C:\Program Files\CCP\EVE\eve.exe"
No command 'ine' found, did you mean:
 Command 'ipe' from package 'ipe' (universe)
 Command 'xine' from package 'xine-ui' (universe)
 Command 'ifne' from package 'moreutils' (universe)
 Command 'one' from package 'opennebula' (universe)
 Command 'line' from package 'util-linux' (main)
 Command 'ink' from package 'ink' (universe)
 Command 'inc' from package 'nmh' (universe)
 Command 'inc' from package 'mailutils-mh' (universe)
 Command 'ne' from package 'ne' (universe)
 Command 'wine' from package 'wine1.2' (universe)
ine: command not found
mike@mike:~$ wine explorer /desktop=0,1280x1024 "C:\Program Files\CCP\EVE\eve.exe"
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:win:RegisterDeviceNotificationA (hwnd=0x124168, filter=0x73e9d4,flags=0x00000001) returns a fake device notification handle!
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:heap:HeapSetInformation 0x8d9000 0 0x33fc6c 4
fixme:win:EnumDisplayDevicesW ((null),0,0x338d7c,0x00000000), stub!
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x20074 0x00000000
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0xf39ca50,0xf39c970): stub
fixme:imm:ImmDisableTextFrameService Stub
fixme:imm:ImmReleaseContext (0x20074, 0x1381c8): stub
fixme:reg:GetNativeSystemInfo (0x33b718) using GetSystemInfo()
fixme:d3d:buffer_PreLoad Too many full buffer conversions, stopping converting

```

What could be causing this? Suggestions would be greatly appreciated.

Please note this was posted some time before, but it was deleted (searches do not find it). I would be grateful if this post was not deleted, as I don't think there is any reason for it.

---

### Post by ELD on 2010-05-19
We have a WINE forum, seriously we do.

---

### Post by miickEe on 2010-05-19
Well this seems a good a place as any to put such a topic, seeing as it's gaming in Ubuntu.

---

### Post by ELD on 2010-05-19
I'm not going to argue over a fact. It is in fact a windows game, you are in fact working with wine. We in fact do have a wine forum for exactly this.

=

Wine forum, all other threads get moved, so will yours.

I don't mean to be rude, but the tiniest amount of searching will have told you this. It also shows you haven't read the guidlines for this forum, to quote *sigh*
> 
[COLOR=Red]Wine and Windows related games on linux, please post  them [in our wine forum]("http://ubuntuforums.org/forumdisplay.php?f=313").
If not they will be deleted or closed.
[/COLOR][COLOR=Red]
[/COLOR]

---

### Post by miickEe on 2010-05-19
I have recently upgraded to Ubuntu 10.04 and I love it, great release. I am running wine1.2, and installed the latest EVE Online client in there. It runs perfectly, although without sound. The sound worked the first time I ran the game, then somewhere during gameplay it stopped. The sound works in all other applications, and in the winecfg sound test.

Here is the output of the command I use to run the game.


```

mike@mike:~$ ine explorer /desktop=0,1280x1024 "C:\Program Files\CCP\EVE\eve.exe"
No command 'ine' found, did you mean:
 Command 'ipe' from package 'ipe' (universe)
 Command 'xine' from package 'xine-ui' (universe)
 Command 'ifne' from package 'moreutils' (universe)
 Command 'one' from package 'opennebula' (universe)
 Command 'line' from package 'util-linux' (main)
 Command 'ink' from package 'ink' (universe)
 Command 'inc' from package 'nmh' (universe)
 Command 'inc' from package 'mailutils-mh' (universe)
 Command 'ne' from package 'ne' (universe)
 Command 'wine' from package 'wine1.2' (universe)
ine: command not found
mike@mike:~$ wine explorer /desktop=0,1280x1024 "C:\Program Files\CCP\EVE\eve.exe"
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:win:RegisterDeviceNotificationA (hwnd=0x124168, filter=0x73e9d4,flags=0x00000001) returns a fake device notification handle!
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:heap:HeapSetInformation 0x8d9000 0 0x33fc6c 4
fixme:win:EnumDisplayDevicesW ((null),0,0x338d7c,0x00000000), stub!
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x20074 0x00000000
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0xf39ca50,0xf39c970): stub
fixme:imm:ImmDisableTextFrameService Stub
fixme:imm:ImmReleaseContext (0x20074, 0x1381c8): stub
fixme:reg:GetNativeSystemInfo (0x33b718) using GetSystemInfo()
fixme:d3d:buffer_PreLoad Too many full buffer conversions, stopping converting

```
I am running on board sound on a Gigabye MA74GMT-S2 motherboard. What could be causing this? Suggestions would be greatly appreciated.

---

### Post by miickEe on 2010-05-19
I have made a thread in the wine forum as you requested, you can delete this thread now.

---

### Post by cariboo on 2010-05-19
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by Rikeshar on 2011-05-23
Sorry to bring up an old topic, but I"m having the same problem... after a while the sound in EVE cuts out, but stays on for all the other programs on the computer. I'm using the ALSA drivers. I tried OSS, but I get no sound at all that way. Any ideas?

---

