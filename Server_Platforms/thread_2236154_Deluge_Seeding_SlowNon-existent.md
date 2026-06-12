---
title: "Deluge Seeding Slow/Non-existent"
date: 2014-07-24
forum: Server Platforms
---

### Post by nuttboxer2 on 2014-07-24
Environment:
Trusty 14.04 headless server
libtorrent 0.16.16.0
Deluge 1.3.6

My torrents seed ok during download, but not at all, or barely once download completes.  I had an issue before where they wouldn't seed at all, and fixed it by upgrading libtorrent, but this time I believe I have the latest version.  I am running a VPN and proxy, not sure if that could be causing an issue with the upload ports?  I use random for the port numbers, and never needed to port forward using deluge before.

---

### Post by sandyd on 2014-07-26
> **nuttboxer2 said:**
> Environment:
Trusty 14.04 headless server
libtorrent 0.16.16.0
Deluge 1.3.6

My torrents seed ok during download, but not at all, or barely once download completes.  I had an issue before where they wouldn't seed at all, and fixed it by upgrading libtorrent, but this time I believe I have the latest version.  I am running a VPN and proxy, not sure if that could be causing an issue with the upload ports?  I use random for the port numbers, and never needed to port forward using deluge before.

Go to deluge preferences (I assume you are using deluged + deluge client). Click on the 'Network' tab, and choose 'Test Active Port'.
If that returns an error, it means that your incoming ports are blocked. Normally, the ports should be opened automatically using UPnP and should not require manual port forwarding.

---

### Post by nuttboxer2 on 2014-07-27
I haven't seen that button in the webui the past few releases, maybe because I'm using random ports?
[ATTACH=CONFIG]255092[/ATTACH]

---

### Post by sandyd on 2014-07-27
> **nuttboxer2 said:**
> I haven't seen that button in the webui the past few releases, maybe because I'm using random ports?

Oh, assumed you were using the deluge client, not the webui, I have never used the webui so I dont know where that button is.

EDIT:
Removed a base64 image from your post, please use the manage attachments button instead of dragging and dropping an image

---

### Post by nuttboxer2 on 2014-07-27
Added the image correctly(?), though it doesn't display full size.

I've always used webui, and that button was in previous versions, but doesn't seem to be there anymore.  As the issue was libtorrent last time, thinking maybe that bug has been re-introduced in 16.16...

---

### Post by sandyd on 2014-07-28
Try using [http://www.canyouseeme.org/](http://www.canyouseeme.org/) to see if your ports are open.

---

### Post by nuttboxer2 on 2014-07-30
will that work from command line?  I assume I'd have to run it on the seedbox, which doesn't have any UI.

---

