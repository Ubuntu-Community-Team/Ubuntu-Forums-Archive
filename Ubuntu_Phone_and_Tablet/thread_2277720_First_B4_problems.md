---
title: "First B4 problems"
date: 2015-05-11
forum: Ubuntu Phone and Tablet
---

### Post by msknight on 2015-05-11
Hi Folks,

I've just taken delivery of my B4 Ubuntu phone and I'm having a few issues that I need help with please.

Firstly, I can't find where to change the bluetooth name of the device.

Second, the Wi-Fi MAC address is needed for Wi-Fi security, but not only was it not presented at set up, it isn't in the "About Phone" either.

Third, I remember in Ubuntu desktop (which is why I changed to Mint) that all search results went to the internet automatically and I had to turn it off after install. Where is the turn-off within the phone please, and is where any guide to the policy on this ... I don't want my data bill to go through the roof as it did with Android once!  - (long story short, in a bad reception area, constant failed packets cause retries but nevertheless, the cost of the failed data packets still counted, so over the course of the weeks my phone bill went skywards ... so data transmission that I can't control is an immediate phone killer.)

---

### Post by lgd on 2015-05-11
1. Doesn't work without deactivating the write protection of the whole system.
2. ifconfig -a
3. system settings > security > dash

Please remember: One thread - one question. So for more details open new ones please.

---

### Post by msknight on 2015-05-11
1. Not in GUI - how do I report this to devs? this is something any customer would expect to handle via the GUI.
2. It popped up after an update ... sounds like default software needs updating and I need to put forward a suggestion to devs that the WiFi Mac is visible during initial set up so that people can program their wifi security
3. Popped up after the update.

Thanks!

---

### Post by slickymaster on 2015-05-11
> **msknight said:**
> 1. Not in GUI - how do I report this to devs? this is something any customer would expect to handle via the GUI.
2. It popped up after an update ... sounds like default software needs updating and I need to put forward a suggestion to devs that the WiFi Mac is visible during initial set up so that people can program their wifi security
3. Popped up after the update.

Thanks!
Information about bug reporting on Ubuntu Touch can be found in here: [https://wiki.ubuntu.com/Avengers](https://wiki.ubuntu.com/Avengers). The Avengers page contains a tabulated list of packages with handy links for where to file bugs.

To file a bug directly on the device use the "ubuntu-bug" program, specifying the package which you'd like to report against. e.g.```
adb shell ubuntu-bug unity8
```

---

