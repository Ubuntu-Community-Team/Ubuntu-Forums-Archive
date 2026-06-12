---
title: "default Python version for 22.04 jammy?"
date: 2022-02-24
forum: Ubuntu Development Version
---

### Post by dhalbert on 2022-02-24
The release schedule here: [https://discourse.ubuntu.com/t/jammy-jellyfish-release-schedule/23906](https://discourse.ubuntu.com/t/jammy-jellyfish-release-schedule/23906)
lists Python 3.10 on January 13, 2022 in the "Planned and potentially disruptive archive-wide activities" section.

I'm running jammy. /usr/bin/python is still Python 3.9.10 [EDIT: I said 3.9.2 by mistake] but /usr/bin/python3.10 is also installed.

Is it the plan to switch to Python 3.10.x for the final release, or will /usr/bin/python be 3.9.x?

Thanks.

---

### Post by guiverc on 2022-02-24
I'm running *jammy* too, but I get the following

```

guiverc@d960-ubu2:~$   python3 --version
Python 3.9.10

```

I recall a conversation on the topic (*#ubuntu-devel or like room; conversation between Core-Devs*) ; but as python3 version doesn't matter to me I took no notice of it, or the plans & their expected dates.

I'll provide the following, but note this may not be the reason they said  (*this answer seems common sense to me*).

The `apt` and package tools have to deal with python 3.10 properly before python version is changed; otherwise they may stop working if the change occurs first meaning installed systems won't upgrade. Default version will only be changed when everything is ready.

Don't forget Ubuntu* jammy* is still in *alpha*.

---

### Post by dhalbert on 2022-02-24
Sorry, yes, I mean 3.9.10, not 3.9.2 (I had recently looked at an RPi, which was on 3.9.2).

Thanks for the chat recollection, that is exactly what I wanted to hear. I was mostly wondering because the 3.10 change was given as being in January.

---

### Post by dhalbert on 2022-03-02
I just upgraded packages, and /usr/bin/python3 is now python 3.10.2.

---

