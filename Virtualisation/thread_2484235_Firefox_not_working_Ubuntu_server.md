---
title: "Firefox not working Ubuntu server"
date: 2023-02-20
forum: Virtualisation
---

### Post by valgrif on 2023-02-20
Hello, I have a Ubuntu Server 22.04.1 arm64 virtual machine created in the UTM program and running on a MacBook Pro M1. When I install the desktop, the applications work correctly (Thunderbird, LibreOffice, etc.), but Firefox does not run. It appears as if it's open, but a transparent window keeps reappearing in a loop. I have tried updating it, uninstalling and reinstalling it, and even creating new virtual machines, but the problem persists. Can anyone help me? Thank you.

---

### Post by DuckHook on 2023-02-20
Firefox is now a snap. I don't know if that is the source of the problem, but it could very well be.

There are a number of ways to work around the snap issue. The easiest is to download the standalone version of FF from Mozilla's site and install it. It will keep itself automatically updated by alerting you to new releases and allowing you to just install them.

Another technique is to add the Mozilla Team's PPA to your install and use the ESR version of FF. ESR is several versions behind the latest and greatest, but it is secure and has the benefit of stability and long term support.

This is a common topic on these forums. You can search for threads that solve this issue. Post back for additional help if you need us to direct you.

---

