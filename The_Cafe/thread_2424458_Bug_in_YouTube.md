---
title: "Bug in YouTube?"
date: 2019-08-08
forum: The Cafe
---

### Post by Skaperen on 2019-08-08
i set a music video to loop (right click on video area and select "loop" to toggle).  but when a video ad plays, the loop setting is getting turned off.  they are not letting me hear their ads over and over and over and over ... now i truly believe they are just trying to make it more annoying!

---

### Post by Skaperen on 2019-08-11
youtube just did it again, stuck an ad in my music which reset the loop mode.

---

### Post by again? on 2019-08-11
Use ublock origin.
I don't see ads at all.
I block googleads.g.doubleclick.net and doubleclick.net and others.
Trial and error, see what works without affecting functionality.
[https://github.com/gorhill/uBlock/wiki](https://github.com/gorhill/uBlock/wiki)

---

### Post by Skaperen on 2019-08-11
the video ads are coming from a different domain?  what kind of blocking is used?
[LIST]
[*]just drop the query and let it wait for no answer?
[*]drop the answer for a similar effect?
[*]give a false answer of 127.0.0.1 or some IP that will reject ports 443 and 80?
[*]put these names in /etc/hosts with an IP like above?
[*]answer the HTTP/HTTPS request with a 404?
[/LIST]
for HTTPS you'd have to put in a fake CA so a fake cert (signed by the fake CA) will be accepted.

what happens when an ad position is reached?  i've seen it pause and spin the circle for a while for about as long as a network timeout then go back to the video.  that's a long pause and not really a good way to block an ad.

i'm not really opposed.  they need to pay to run the service and are working to make sure artists get compensated.  most radio stations have ads, too.  but ads in the middle of songs and messing with settings, buggy or intentional, is going too far.  so i am seriously considering this now.

how is this thing set up?  can it be installed by a non-root user that has a directory of their own in PATH?

---

### Post by again? on 2019-08-11
It's a browser extension....read the wiki.
On most sites I disable, but works well for youtube.
You can import my attached config.
Open the ublock dashboard from the icon popout and in the settings tab you can restore from file.
The settings affect all sites , so I just disable when I want normal functionality.

---

### Post by PaulW2U on 2019-08-12
> **Skaperen said:**
> how is this thing set up?  can it be installed by a non-root user that has a directory of their own in PATH?
uBlock Origin can be installed as an extension from the [Chrome/Chromium Webstore]("https://chrome.google.com/webstore/detail/ublock-origin/cjpalhdlnbpafiamejdnhcphjbkeiagm") or from [Firefox Add-ons](https://addons.mozilla.org/).

There are also [packages]("https://packages.ubuntu.com/search?keywords=ublock&searchon=names&suite=all&section=all") in the Ubuntu repositories but unfortunately they don't seem to be updated to reflect recent bug fixes and enhancements.

---

