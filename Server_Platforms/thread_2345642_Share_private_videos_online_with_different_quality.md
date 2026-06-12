---
title: "Share private videos online with different quality settings"
date: 2016-12-06
forum: Server Platforms
---

### Post by dudumomo on 2016-12-06
Hi there,

I got some family videos I used to compress and then share to some family member by either email or in the cloud (Owncloud or Pydio).
But some of them have a very different connection (one member is on weak 3G connection, because no ADSL available for example....still in 56k)
Or some will have fiber...

I'm looking for something like Youtube where the system will detect the bandwidth and adapt the video quality accordingly.
Ideally, if I could host myself the software, it would be great !

Any suggestion?

Thank you !

---

### Post by TheFu on 2016-12-06
Plex Media Server - it isn't F/LOSS, but it is free.  The easy way is for everyone to use plex-pass, but you don't need to do that.  You can create ssh keys, setup a SOCKS proxy for them and they can use a web browser as the interface.  People on dialup - just mail them a DVD.

No idea how to do this on Windows, but on Linux ...
Setup the tunnel to the Plex Server - you run ssh on public-ip-to-your-house-ssh.com. They can be the same machine or not. Mine are not.

```
# They start an ssh session that forwards the plex server port 32400 (putty should be able to do this on Windows)
$ ssh -f -L 32400:plex:32400 [email]userid-you-setup@public-ip-to-your-house-ssh.com[/email] -NT

```
Then they open a browser and visit [http://localhost:32400/web/](http://localhost:32400/web/) to access plex web GUI.  There's a transcode setting they'd set in the upper right-hand corner. For WAN, the 480 resolution is probably best.

Simple. Free. Secure. No 3rd parties except whatever you do about DNS.  Clearly, you'd need to open whatever ssh port you use. Probably best NOT to use 22/tcp ... but anything over 60K would be fine.  Would be smart to use ssh-keys for authentication, never passwords.  Secure the ssh server and you might want to prevent actual shell logins. I've never needed to provide a tunnel without a login allowed, but I bet it is possible.

There are probably other methods too.

Or just use talky.io using screen sharing live.

If you use owncloud/nextcloud, you'll need to transcode the videos to a size/quality for each viewer and teach them which file to grab.  Personally, I only use nextcloud with a SOCKS proxy setup via ssh. I don't consider HTTPS secure enough, though I use it for nextcloud too even though it isn't available to the internet.

---

### Post by dudumomo on 2016-12-06
Thanks TheFu,
I never thought about Plex,,, I'll give it a try.
Thank you

---

### Post by gordintoronto on 2016-12-06
Why not just use Youtube? It supports private videos.

---

