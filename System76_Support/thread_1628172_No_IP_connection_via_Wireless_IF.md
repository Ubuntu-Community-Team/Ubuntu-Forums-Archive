---
title: "No IP connection via Wireless I/F"
date: 2010-11-22
forum: System76 Support
---

### Post by 130s on 2010-11-22
Just sharing the problem I worked around by my own. I'm not sure what was the cause but it worked. 

_Problem phenomenon: _
Even though wireless connection indicator on the top bar of Ubuntu desktop shows it connects to the router, any network connections that use IP doesn't work which includes:
- ping to { the nearest router, google.com } becomes "DESTINATION UNREACHABLE"

[U]What I did before the problem occurred:
[/U]I bought star3, did clean install of Ubuntu 10.04 Netbook edition from LiveUSB which I created by UNetBootin. Set wireless router configuration.

_Workaround_
Connect ethernet cable which enabled IP communication. Then on "Update Manager", do "check" and update software. Then on "setting" panel, added 
deb [http://planet76.com/repositories/](http://planet76.com/repositories/) ./to "Other Software" and apply all available updates.
During adding planet76 repository, I encountered a trouble described [here]("http://ubuntuforums.org/showthread.php?t=1587466") (solution is available as well).


PC: Starling star3
OS: Ubuntu 10.04

Isaac

PS. Looks like [someone in this thread]("http://ubuntuforums.org/showthread.php?t=1593267&page=2") had a similar/same problem.

---

