---
title: "U1 Plugin Crashing Rhythmbox"
date: 2010-11-11
forum: Ubuntu One (CLOSED)
---

### Post by migs73 on 2010-11-11
As you can se from the title, when I open Rhythmbox, it crashes and shutsdown after a few seconds. If I disable the U1 Plugin Rhythmbox works fine. I also noticed if I login to U1 music store on the web all my music downloads are greyed out and showing as 0mb downloaded although they have all been downloaded in full, they also show up fine via the U1 web login.

Here is the response from terminal when opened that way;

```
mike@dell-laptop:~$ rhythmbox
/home/mike/.gtkrc-2.0:8: Unable to find include file: ".themes/nautilus/nautilus.rc"

(rhythmbox:1904): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** Message: pygobject_register_sinkfunc is deprecated (GstObject)
** (rhythmbox:1904): DEBUG: Syncdaemon not running, waiting for it to start in NameOwnerChanged
** (rhythmbox:1904): DEBUG: Loading the real store page

liboauth: data to sign='GET&https%3A%2F%2Fone.ubuntu.com%2Fmusic%2Flogin&oauth_callback%3DNone%26oauth_consumer_key%3Dubuntuone%26oauth_nonce%3DruPBxW4umduPZAc05mXdj%26oauth_signature_method%3DHMAC-SHA1%26oauth_timestamp%3D1289427066%26oauth_token%3DZWtjmdQjl6HzX8bKnwHP%26oauth_verifier%3DNone%26oauth_version%3D1.0'


liboauth: key='hammertime&DnH666MmVBbRwC4g46fld79l42gMnSk4BHqDfVrwHXKtLQblgLdNfGc7l9DXLKtfHggkrrzlNZX6FcQg'

** (rhythmbox:1904): DEBUG: navigation requested to https://one.ubuntu.com/music/login?oauth_callback=None&oauth_consumer_key=ubuntuone&oauth_nonce=ruPBxW4umduPZAc05mXdj&oauth_signature_method=HMAC-SHA1&oauth_timestamp=1289427066&oauth_token=ZWtjmdQjl6HzX8bKnwHP&oauth_verifier=None&oauth_version=1.0&oauth_signature=x1XSeXpNhWddTMKYMOWYawxBrj0%3D
Segmentation fault
```

another user on a previous thread of mine on the subject ([http://ubuntuforums.org/showthread.php?t=1618454](http://ubuntuforums.org/showthread.php?t=1618454)) could also replicate this problem, but suggested when he connected t U1 first the problem did not occur. I did not find this to be the case, I connected, synched okay and then tried to open Rhythmbox, but it still crashed.

Many Thanks

Mike

---

### Post by migs73 on 2010-11-12
Bump

---

### Post by cor2y on 2010-11-12
Still no solutions except to remove ubuntu one music store plugin.
Even connecting to ubuntu one then laucnhing rhythmbox solved nothing.
Then i tried to purge all local rhythmbox data so it would start fresh still crashes on launch.
It looks like canonical's decision to switch to banshee next release is a good/smart one.

Edit
I was finally able to fix this. 
For music on your system/harddrive/usb key etc but when i insert a music cd it crashes with segmentation fault again.

1) Remove ubuntu one music store plugin from synaptic
2) Delete/clear all local rhythmbox references with
```

rm ~/.local/share/rhythmbox/ ~/.cache/rhythmbox/ ~/.gconf/apps/rhythmbox/ -r
```
3) Launch Rhythmbox and disable all music store/fm rhythmbox plugins, then quit rhythmbox
4) Reinstall ubuntuone music store plugin
5) Launch Rhythmbox again and now it shouldnt crash, renable all the plugins you disabled.

For me everything was working fine until i decided to insert a cd to rip to harddrive then the segmentation fault/crash came back.

---

### Post by migs73 on 2010-11-13
Thanks for your help Cor2y, but mine went straight back to the seg fault.

I think I'll launch it as a bug, but should that be with Ubuntu one or Rhythmbox?

---

### Post by migs73 on 2010-11-15
Hi all

Reported this as a bug;

[https://bugs.launchpad.net/rhythmbox-ubuntuone-music-store/+bug/675315](https://bugs.launchpad.net/rhythmbox-ubuntuone-music-store/+bug/675315)

If this also affects you please login in to launchpad and visit the bug page above, click on the 'does this bug affect you?' near the top and select 'yes'.

Many thanks

Mike

---

### Post by fermin on 2010-11-19
I too have this problem. As suggested, I unistalled the ubuntu one music store plugin for rhythmbox through synaptic, removed all references to rhythmbox from local directory through

```
rm ~/.local/share/rhythmbox/ ~/.cache/rhythmbox/ ~/.gconf/apps/rhythmbox/ -r
```

Also, I do use an ubuntu One account for file syncing so I deactivated syncing from my machine through the 'me-menu'->Ubuntu One->Devices->Disconnect. Then restarted Rhythmbox from the terminal with debugging symbols as

```
rhythmbox -d
```

and it seemed to work for a few minutes, it started to rescan my whole music collection, I suppose it was rebuilding the database; the plugins where also deactivated so I went to active them again (the ones I use but the Ubuntu One Music store I had already uninstalled), and bam! it crashed again ](*,). The terminal showed (last few lines)


```
(04:01:14) [0x9d61068] [rb_metadata_gst_load_tag] rb-metadata-gst.c:388: no metadata field for tag "mode"
(04:01:14) [0x9d61068] [rb_metadata_gst_load_tag] rb-metadata-gst.c:388: no metadata field for tag "emphasis"
(04:01:14) [0x9d61068] [rb_metadata_gst_load_tag] rb-metadata-gst.c:459: processed bitrate value: 128
(04:01:14) [0x9d61068] [rb_metadata_bus_handler] rb-metadata-gst.c:676: message of type state-changed from fakesink
(04:01:14) [0x9d61068] [rb_metadata_bus_handler] rb-metadata-gst.c:676: message of type state-changed from pipeline
(04:01:14) [0x9d61068] [rb_metadata_bus_handler] rb-metadata-gst.c:676: message of type async-done from pipeline
(04:01:14) [0x9d61068] [rb_metadata_load] rb-metadata-gst.c:812: gone to PAUSED for file:///home/fermin/M%C3%BAsica/A%20Perfect%20Circle/Emotive/12%20-%20Fiddle%20and%20the%20Drum.mp3
(04:01:14) [0x9d61068] [rb_metadata_load] rb-metadata-gst.c:864: successfully read metadata for file:///home/fermin/M%C3%BAsica/A%20Perfect%20Circle/Emotive/12%20-%20Fiddle%20and%20the%20Drum.mp3
(04:01:14) [0x9d61068] [rb_metadata_dbus_load] rb-metadata-dbus-service.c:128: metadata load finished (type application/x-id3)
(04:01:14) [0x9d61068] [rb_metadata_dbus_add_to_message] rb-metadata-dbus.c:132: opening container type {uv}
Fallo de segmentación
```

the last of which is spanish for 'segmentation fault', which is the same error I've been having all along.

I suspect the problem isn't then about the Ubuntu One plugin/syncing daemon, but either about Rhythmbox itself, or **a combination of it running with the newest Linux kernel**, which I just installed (and rebooted) before the problem with rhythmbox appeared.

I'm using Ubuntu 10.04, Linux kernel 2.6.32-26 (the one I just upgraded to), Gnome 2.30.2, Rhythmbox 0.12.8.

Maybe trying to go back to previous kernel version?

EDIT: I tryed to mark the bug in launchpad as occurring to me also, but I got the message 'Not allowed here. Sorry, you don't have permission to access this page. You are logged in as ferminfm.' Why would that be? Comes without saying I couldn't mark it.

EDIT2: Going back to previous Linux kernel (2.6.32-25) did not work. I keep getting the segmentation fault error. Also, I recurringly get this while running rhythmbox through the terminal (without the -d option this looks more clearly):

```
(rhythmbox:2719): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(rhythmbox:2719): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
```

Maybe this gives some hints for someone that understands what those messages say.

---

### Post by cor2y on 2010-11-19
Mine continued to work then mysteriously stopped working again.
So i removed rhythmbox completely, deleted all references/rhythmbox settings once again and installed 
banshee and all its plugins/extra packages.
So far no problems, banshee is the new default audio player next ubuntu release so might as well get used to it from now.

---

