---
title: "build ltsp root folder NOT using ltsp-build-client"
date: 2013-07-08
forum: Server Platforms
---

### Post by xris_xcess on 2013-07-08
Hi:

I'm running a lab in a school with ubuntu server 12.04 and fat-clients with xubuntu-desktop. Instead of building a fat-client directly I let ltsp-build-client build a thin client and then installed a minimal xfce4 in that.

In an effort to make the clients lighter and faster, I wanted to know how to build a ltsp root folder with debootstrap and chroot, and maybe get a "slimmer" final image.

I tried to compare a standard root folder with mine and installed the ldm, nbd and lstp-client packages... but I didn't get very far.

I also tried looking in the LTSP official docs (ubuntu and ltsp project pages) but I didn't get concrete information about any special configs. AND also in the /usr/lib/ltsp folder, where are config scripts for ltsp-build-client.

Does anyone have more information, tips or experience doing this? OR am I just being overly picky and will not really get much performance gains from trying to go the "manual way"?

---

