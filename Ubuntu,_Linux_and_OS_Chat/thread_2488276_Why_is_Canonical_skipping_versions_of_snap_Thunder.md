---
title: "Why is Canonical skipping versions of snap Thunderbird and Chromium?"
date: 2023-06-29
forum: Ubuntu, Linux and OS Chat
---

### Post by donald187 on 2023-06-29
I've seen this happen twice with snap Thunderbird.  They're not just  late.  They skip an entire version.  Now apparently the same is  happening with snap Chromium.

```

$ snap info chromium
name:      chromium
summary:   Chromium web browser, open-source version of Chrome
publisher: Canonical&#10003;
store-url: https://snapcraft.io/chromium
contact:   https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bugs?field.tag=snap
license:   unset
description: |
  An open-source browser project that aims to build a safer, faster, and more
  stable way for all Internet users to experience the web.
commands:
  - chromium.chromedriver
  - chromium
snap-id:      XKEcBqPM06H1Z7zGOdG5fbICuf8NWK5R
tracking:     latest/stable
refresh-date: yesterday at 12:31 PDT
channels:
  latest/stable:    114.0.5735.106 2023-06-09 (2497) 157MB -
  latest/candidate: 114.0.5735.198 2023-06-27 (2529) 156MB -
  latest/beta:      115.0.5790.40  2023-06-22 (2523) 157MB -
  latest/edge:      116.0.5845.4   2023-06-26 (2527) 158MB -
installed:          114.0.5735.106            (2497) 157MB -

```

Chrome 114.0.5735.133 came out on June 13 and snap Chromium is still on 114.0.5735.106.

Google has now come out with Chrome 114.0.5735.198 on June 26th.  So apparently Canonical is skipping the version 114.0.5735.133.[COLOR=#666666][FONT=arial]

[https://chromereleases.googleblog.com/](https://chromereleases.googleblog.com/)

[https://chromereleases.googleblog.com/search?updated-max=2023-06-14T14:43:00-07:00&max-results=7&start=14&by-date=false](https://chromereleases.googleblog.com/search?updated-max=2023-06-14T14:43:00-07:00&max-results=7&start=14&by-date=false)

I believe that these versions had fixed cves.  Certainly Chrome 114.0.5735.133 has.
[/FONT][/COLOR]

---

### Post by ian-weisser on 2023-06-29
Your output clearly shows newer snaps in the candidate, beta, and edge channels.

---

### Post by donald187 on 2023-06-29
Indeed.  And this was the case for Thunderbird as well if I recall.  So of course I'm asking about the stable channel.

---

### Post by exploder on 2023-07-03
I wonder if perhaps they skip point releases that address issues with other platforms that do not effect Linux users? Just guessing....

---

### Post by donald187 on 2023-07-03
> **exploder said:**
> I wonder if perhaps they skip point releases that address issues with other platforms that do not effect Linux users? Just guessing....

I appreciate the guess. :)

---

### Post by grahammechanical on 2023-07-03
A lot depends upon who is maintaining the snap packaged app. I do believe that Mozilla developers maintain the snap versions of Firefox and Thunderbird. So, the decision is nothing to do with Canonical. 

[https://blog.mozilla.org/futurereleases/2016/04/21/firefox-default-browser-for-linux-users-ubuntu-new-snap-format-coming-soon/](https://blog.mozilla.org/futurereleases/2016/04/21/firefox-default-browser-for-linux-users-ubuntu-new-snap-format-coming-soon/)

Regards

---

### Post by donald187 on 2023-07-03
> **grahammechanical said:**
> A lot depends upon who is maintaining the snap packaged app. I do believe that Mozilla developers maintain the snap versions of Firefox and Thunderbird. So, the decision is nothing to do with Canonical. 

[https://blog.mozilla.org/futurereleases/2016/04/21/firefox-default-browser-for-linux-users-ubuntu-new-snap-format-coming-soon/](https://blog.mozilla.org/futurereleases/2016/04/21/firefox-default-browser-for-linux-users-ubuntu-new-snap-format-coming-soon/)

Regards

Canonical seems to maintain Thunderbird and Chromium.  But I'm aware that Mozilla packages Firefox.

[https://snapcraft.io/thunderbird](https://snapcraft.io/thunderbird)

[https://snapcraft.io/chromium](https://snapcraft.io/chromium)

---

### Post by deadflowr on 2023-07-03
Might be because they are switching core versions that will be used for chromium moving forward:
[https://discourse.ubuntu.com/t/request-for-testing-chromium-moving-from-core20-to-core22/36591]("https://discourse.ubuntu.com/t/request-for-testing-chromium-moving-from-core20-to-core22/36591")

---

### Post by donald187 on 2023-07-03
> **deadflowr said:**
> Might be because they are switching core versions that will be used for chromium moving forward:
[https://discourse.ubuntu.com/t/request-for-testing-chromium-moving-from-core20-to-core22/36591](https://discourse.ubuntu.com/t/request-for-testing-chromium-moving-from-core20-to-core22/36591)

Thanks. :)

---

### Post by donald187 on 2023-07-04
And version 114.0.5735.133 has been skipped.  The stable channel is now on 114.0.5735.198.

```

$ snap info chromium
name:      chromium
summary:   Chromium web browser, open-source version of Chrome
publisher: Canonical&#10003;
store-url: https://snapcraft.io/chromium
contact:   https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bugs?field.tag=snap
license:   Apache-2.0 AND BSD-3-Clause AND LGPL-2.0 AND LGPL-2.1 AND MIT AND MS-PL AND (GPL-2.0+ OR LGPL-2.1+ OR MPL-1.1)
description: |
  An open-source browser project that aims to build a safer, faster, and more
  stable way for all Internet users to experience the web.
snap-id: XKEcBqPM06H1Z7zGOdG5fbICuf8NWK5R
channels:
  latest/stable:    114.0.5735.198 2023-07-04 (2529) 156MB -
  latest/candidate: 114.0.5735.198 2023-06-27 (2529) 156MB -
  latest/beta:      115.0.5790.56  2023-06-29 (2534) 157MB -
  latest/edge:      116.0.5845.4   2023-06-26 (2527) 158MB -

```

(I'm currently on Debian so using the live cd to be able to post terminal output.)

---

### Post by donald187 on 2023-07-06
> **deadflowr said:**
> Might be because they are switching core versions that will be used for chromium moving forward:
[https://discourse.ubuntu.com/t/request-for-testing-chromium-moving-from-core20-to-core22/36591](https://discourse.ubuntu.com/t/request-for-testing-chromium-moving-from-core20-to-core22/36591)

And the new version of Chromium uses core 22 now so maybe that was it.  Leastways core 22 was downloaded prior to downloading Chromium.

---

