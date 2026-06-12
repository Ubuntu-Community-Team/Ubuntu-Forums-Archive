---
title: "Transmission fails with SSL trackers"
date: 2012-02-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by pressureman on 2012-02-18
In the last couple of weeks I noticed that some existing torrents I had running in Transmission with an SSL tracker, no longer worked. Also any new torrents that I add will no longer start downloading.

Transmission tries to get the list of peers from the tracker, but after 60 seconds fails with "Could not connect to tracker".

I know that the tracker is reachable, as I can open the URL with a browser.

Is anybody else experiencing this problem? SSL trackers are not so common (mostly used by private trackers), and I only have the one example to test with. At this stage I can't say for sure whether it's perhaps a quirk with this particular tracker, or whether it affects Transmission generally.

I've tried other versions of Transmission (2.42, 2.31, 2.50b1), to no avail.

---

### Post by pressureman on 2012-02-18
I should add that the SSL tracker in question works fine with Deluge and rtorrent. It definitely would appear to be something buggy in either Transmission or libcurl-gnutls.

---

### Post by pressureman on 2012-02-21
For anyone interested, I found a workaround that fixes the problem - install libgnutls26 packages from Debian sid.

[https://bugs.launchpad.net/ubuntu/+source/gnutls26/+bug/937537](https://bugs.launchpad.net/ubuntu/+source/gnutls26/+bug/937537)

---

